---
title: "Virtualization"
date: 2015-12-27
forum: New to Ubuntu
---

### Post by seabird22 on 2015-12-27
Hello to all,


I know that there is a virtualization forum, however, I figured I would ask here since I have been out of the scene for a while, and my question is not specific to any virtualization platform.

Does the latest version of Ubuntu desktop come with virtualization software or do I have to install one separately? 

Thanks in advance.

---

### Post by Vladlenin5000 on 2015-12-27
You have to install the one you want.

---

### Post by Herdo on 2015-12-27
I don't think so.  I believe Ubuntu Server comes with KVM preinstalled, but as far as I know you would have to install the software yourself for Ubuntu Desktop.  Virtualbox is a good choice and can be found on the Ubuntu Software Center.

---

### Post by seabird22 on 2015-12-27
got it,

I need to be able to run windows 10 for work purposes. 


Thanks for the replies.

---

### Post by deadflowr on 2015-12-27
> **Herdo said:**
> I don't think so.  I believe Ubuntu Server comes with KVM preinstalled, but as far as I know you would have to install the software yourself for Ubuntu Desktop.  Virtualbox is a good choice and can be found on the Ubuntu Software Center.

Ubuntu Server comes with nothing but the base system.
However during installation you can install the extra packages you need, including virtualisation packages.

---

### Post by HermanAB on 2015-12-27
I'd recommend that you download Virtualbox from the Oracle web site.  The version that is in the repos cannot handle USB devices.

---

### Post by sandyd on 2015-12-27
> **Herdo said:**
> I don't think so.  I believe Ubuntu Server comes with KVM preinstalled, but as far as I know you would have to install the software yourself for Ubuntu Desktop.  Virtualbox is a good choice and can be found on the Ubuntu Software Center.

The KVM hypervisor is built into the kernel and is included in both desktop and server edition, though the tools to run the virtual machine (i.e. qemu-kvm/libvirt/etc) are not on the system.

there are a  few issues with KVM/Win10, mainly -> [http://ubuntuforums.org/showthread.php?t=2289210](http://ubuntuforums.org/showthread.php?t=2289210) / [https://me.m01.eu/blog/2015/03/windows-10-kvm-and-iscsi/](https://me.m01.eu/blog/2015/03/windows-10-kvm-and-iscsi/)

Not sure if they are fixed yet, still running Win7 under kvm

---

### Post by seabird22 on 2015-12-27
> **HermanAB said:**
> I'd recommend that you download Virtualbox from the Oracle web site.  The version that is in the repos cannot handle USB devices.

Is virtual box free of charge?

---

### Post by Vladlenin5000 on 2015-12-27
Yes, it is.

---

### Post by QIII on 2015-12-27
It is free for personal use.

If you need Win10 for graphics-heavy applications, then VirtualBox may not be suitable for you.  The hardware abstraction layer does not provide robust graphics performance.

However, if what you need is limited to office productivity apps, VirtualBox is a great choice.

---

### Post by kevdog on 2015-12-27
I'm just curious what you guys recommend for virtualization software.  I've run virtual box for years for many different linux installs and it seems OK. Albeit I admit these are graphically intensive applications.

---

### Post by sandyd on 2015-12-27
> **kevdog said:**
> I'm just curious what you guys recommend for virtualization software.  I've run virtual box for years for many different linux installs and it seems OK. Albeit I admit these are graphically intensive applications.

KVM. So far, I haven't found anything that doesn't run on it, except for when Windows 10 was first released.

Xen is good too, though I mainly prefer it in a XenServer setup. Even then, there are a few odd things. For example, installing Ubuntu 14.04 (not server) requires a bit of tweaking in the latest edition of XenServer 6.5

Vmware is good, but license support is highly restrictive if using ESXi and not Player. The fact that VSphere Client doesn't support the latest features in the latest ESXi release is one thing. Requiring the web interface (which is part of VCenter I think) to have all the VM features is another, simply because VCenter needs another license :p

Edit:
Windows 10 seems to work without issues with KVM on Ubuntu 15.10. You might want to choose that for better performance if you have virtualization extensions on your computer CPU.

When installing, just set OS to Windows 7, after installation, use the Fedora Windows Drivers from [https://fedoraproject.org/wiki/Windows_Virtio_Drivers](https://fedoraproject.org/wiki/Windows_Virtio_Drivers). They didn't have Windows 10  in the downloaded driver iso, so I chose Windows 8.1. Restarted and set everything to virtio and it seems to work/


Unfortunately, I don't have Ubuntu 14.04 LTS to test.

---

