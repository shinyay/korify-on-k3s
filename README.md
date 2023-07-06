# Getting started with Korify on K3s

Cloud Foundry Korifi is the familiar Cloud Foundry abstraction ported over to Kubernetes clusters. It brings a multitenant experience to Kubernetes and helps app developers consume clusters with ease.

- [Cloud Foundry Korifi](https://www.cloudfoundry.org/technology/korifi/)

## Description

In this tutorial I will try to install Korify on K3s.

- [K3s](https://k3s.io/)
  - Lightweight Kubernetes. Production ready, easy to install, half the memory, all in a binary less than 100 MB.

## Installation

### 0. Multipass

K3s does not support MacOS. So you have to we need to setup a Linux layer on top of MacOS.

**Multipass** is a lightweight VM manager for Linux, Windows and macOS. It's designed for developers who want a fresh Ubuntu environment with a single command.

- [Multipass](https://github.com/canonical/multipass)

```shell
brew install --cask multipass
```

Then spin up a new VM by specifying memory and disk space.

```shell
multipass launch --name k3s --memory 4G --disk 40G
```

Check the VM details.

```shell
multipass info k3s
```

```shell
Name:           k3s
State:          Running
IPv4:           192.168.64.6
Release:        Ubuntu 22.04.2 LTS
Image hash:     fe102bfb3d3d (Ubuntu 22.04 LTS)
CPU(s):         1
Load:           0.51 0.33 0.13
Disk usage:     1.4GiB out of 38.7GiB
Memory usage:   189.5MiB out of 3.8GiB
Mounts:         --
```

Mount the VM

```shell
mkidr vm
multipass mount (pwd)/vm k3s:~/k8s
```

Open a shell prompt on the instance

```shell
multipass shell k3s
```

### 1. Install K3s

Run the following command inside of Multipass VM:

```shell
ubuntu@k3s:~$ curl -sfL https://get.k3s.io | sh -s - --disable traefik --write-kubeconfig-mode 644
```

- `--disable traefik`
  - The `–-disable traefik` argument is passed to the installation script to disable the installation of the Traefik ingress controller. This is because we will install Contour for ingress control at a later step and the two will conflict with each other.
- `–-write-kubeconfig-mode 644`
  - This sets the file permission mode of the generated kubeconfig file to 644 which means the owner will have read and write access, while others have only read access

## Demo

## Features

- feature:1
- feature:2

## Requirement

## Usage

## References

## Licence

Released under the [MIT license](https://gist.githubusercontent.com/shinyay/56e54ee4c0e22db8211e05e70a63247e/raw/34c6fdd50d54aa8e23560c296424aeb61599aa71/LICENSE)

## Author

- github: <https://github.com/shinyay>
- twitter: <https://twitter.com/yanashin18618>
- mastodon: <https://mastodon.social/@yanashin>
