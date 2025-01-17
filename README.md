# Oracle VirtualBox Ubuntu Setting Docs

This repo is a document with Ubuntu servers installed in Oracle Virtualbox.

## Contents

### [1. Install Tools.](#install)

### [2. Settings Ubuntu.](#settings)

<a name='install'></a>

## 1. Install Tools.

### Install Oracle VirtualBox

### [Download Link 👈](https://www.virtualbox.org/)

### Install Ubuntu 22.04 LTS Server

![Static Badge](https://img.shields.io/badge/ubuntu-22.04-%23ffffff?style=flat-square&logo=Ubuntu&logoColor=white&labelColor=%23E95420)

### [Download Link 👈](https://releases.ubuntu.com/jammy/)

When the installation is complete, turn on the `Oracle virtualbox` and create a new virtual machine. At this time, insert the downloaded `Ubuntu ISO image` and create it.

<a name='install'></a>

## 2. Settings ubuntu.

Download the required Linux package. If you install `net-tools`, you can use the `ifconfig` command.

```bash
$ sudo apt install net-tools
$ ifconfig
# Show your IP Addresses and Adapter Names
```

I will fix my VM(virtual machine) IP Addresses.

```bash
$ sudo vi /etc/netplan/50-cloud-init.yaml
# File name can be difference. ex) 00-installer-config.yaml
```

And typing like this..

```yaml
network:
  ethernets:
    enp0s3:
      addresses:
        - 192.168.1.10/24 # Input the IP Address you want.
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
      routes:
        - to: default
          via: 192.168.1.1
  version: 2
```

```bash
# Apply command
$ sudo netplan apply
# Check Ip address.
$ ifconfig
```

But it is not done. because we can `Port Fowarding`.

Open Oracle VirtualBox Manager. And Click `Tools -> Network`.

![Image](https://github.com/user-attachments/assets/06c43986-a8ce-48ce-94ba-52b94bb2fdc9)

Create, Typing General Options, Typing Port Forwarding. Like This..

![Image](https://github.com/user-attachments/assets/b7c225c0-cdea-4228-a6b9-40b66909a615)

Finally, Fix Master VM Network.

![Image](https://github.com/user-attachments/assets/d8b73876-7cc4-43ac-8cf9-162bd15243f0)

We Are Done!!

### If you want intall Hadoop Cluster and Kubernetes Cluster?

[Hadoop Settings Link 👈](https://github.com/seunggihong/hadoop-install-guide)

[Kubernetes Settings Link 👈](https://github.com/seunggihong/k8s-cluster-setting)
