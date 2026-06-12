---
title: "qemu-system-x86 process consuming CPU"
date: 2023-09-16
forum: New to Ubuntu
---

### Post by tthoele89 on 2023-09-16
Greetings-

I have a fresh install of 22.04.3 LTS.  I am working with multipass / LXD for a MAAS experiment, but I have a qemu process that is consuming 25% of cpu.  I have tries sudo apt-get remove of several variations, and it says the package is not installed.  The process is still there.  

Do you have any suggestions on removing this?

Troy

---

### Post by QIII on 2023-09-16
Do you have a virtual machine running?

---

### Post by MAFoElffen on 2023-09-16
Why?

LXC does not use QEMU, nor does it use QEMU/KVM. Virtual Manager, which uses the libvirtd daemon, by defualt does not have any connection to LXC, unless you first install package 'libvirt-daemon-driver-lxc'... When installed you can create a connection in Virt-manager to create LXC Containers... But that is still through the libvirtdaemon, not through anything QEMU.

So, since those are true, what is the output of the following:
```

sudo virsh list --all
sudo lxc list

```
We shoud see output similar to this:
```

mafoelffen@Mikes-ThinkPad-T520:~$ virsh list --all
 Id   Name                          State
----------------------------------------------
 -    android-x86-9.0               shut off
 -    debian11                      shut off
 -    fedora                        shut off
 -    lunar-lander-testbed          shut off
 -    macOS-Simple-KVM              shut off
 -    solaris11                     shut off
 -    ubuntu-2004-aarch64           shut off
 -    ubuntu-2004-aarch64-Desktop   shut off
 -    ubuntu-23.04.1a               shut off
 -    ubuntu-23.04.1b               shut off
 -    ubuntu-aarch64-template       shut off
 -    ubuntu18.04-aarch64           shut off
 -    ubuntu20.04                   shut off
 -    ubuntu20.04-10                shut off
 -    ubuntu20.04-11                shut off
 -    ubuntu20.04-2                 shut off
 -    ubuntu20.04-minx-02           shut off
 -    ubuntu20.04-ZFS               shut off
 -    ubuntu20.04-ZFS-02            shut off
 -    ubuntu20.04-ZFS-tester        shut off
 -    ubuntu22.04                   shut off
 -    ubuntu22.04-2                 shut off
 -    ubuntu22.04-2-R5              shut off
 -    win11                         shut off
 -    windows10                     shut off
 -    windows11-Unsupported         shut off

mafoelffen@Mikes-ThinkPad-T520:~$ sudo lxc list
+------------------+---------+------+------+-----------+-----------+
|       NAME       |  STATE  | IPV4 | IPV6 |   TYPE    | SNAPSHOTS |
+------------------+---------+------+------+-----------+-----------+
| maf1-alpine1     | STOPPED |      |      | CONTAINER | 0         |
+------------------+---------+------+------+-----------+-----------+
| maf1-archlinux1  | STOPPED |      |      | CONTAINER | 0         |
+------------------+---------+------+------+-----------+-----------+
| maf1-centos1     | STOPPED |      |      | CONTAINER | 0         |
+------------------+---------+------+------+-----------+-----------+
| maf1-gentoo1     | STOPPED |      |      | CONTAINER | 0         |
+------------------+---------+------+------+-----------+-----------+
| maf1-jammy1      | STOPPED |      |      | CONTAINER | 0         |
+------------------+---------+------+------+-----------+-----------+
| maf1-oracle1     | STOPPED |      |      | CONTAINER | 0         |
+------------------+---------+------+------+-----------+-----------+
| maf1-tumbleweed1 | STOPPED |      |      | CONTAINER | 0         |
+------------------+---------+------+------+-----------+-----------+

```

---

