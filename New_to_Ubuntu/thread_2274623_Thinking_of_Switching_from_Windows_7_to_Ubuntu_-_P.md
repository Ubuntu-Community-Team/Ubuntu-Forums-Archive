---
title: "Thinking of Switching from Windows 7 to Ubuntu - Please help with my Queries..."
date: 2015-04-21
forum: New to Ubuntu
---

### Post by darknet2 on 2015-04-21
I am thinking about switching from Windows 7 to Linux due to privacy concerns. But as I am a new to linux I have few doubts. Appretiate any help with my queries...    1. How to run VM's within Ubuntu Linux without Virtualbox or any other type 2 hypervisors? I am planning to move from Windows 7 to Ubuntu as it is free and due to privacy reasons. Is there any way to run VMs from within Ubuntu without any additional software like Virtualbox or any other type 2 hypervisors? I tried VirtualBox and it sucks in my opinion eventhough it is free. I heard that I could do this by installing KVM? Does this come automatically with Linux desktop version or do i have to install it manually? If Ubuntu cant do this any other Linux distros with this ability to run VM's without installing any additional software?   2. Are the privacy issues associated with Ads and data leaks by Ubuntu fixed in the lateast available release? 3. How to disable paging in Ubuntu? 4. How to disable all logs in Ubuntu? 5. Any Free key stroke encryption software available for Ubuntu?  Thanks...

---

### Post by flaymond on 2015-04-21
Talking about software that 'determined' as a tool, are mostly available in Ubuntu repositories (the central of softwares). You can download those easily from command line. I don't think switching from Windows 7 to Ubuntu for regular users will help that much, although it will make your life a bit hard...IF you don't want to explore. Linux give you more control of your OS, and by that, come more responsibility and more task to get done. If you want a real privacy, try not to get connected to Internet, because as soon you did it, you will exposed to harmful things, anywhere you go. I don't think you should disable system and crucial logs,  if you suddenly mess up your OS, the logs can tell the reason of why. Why do you asking if 'free' encryption tool available in Ubuntu? Ubuntu itself is part of the Free Open Source Software. Of course there's a lot of them available, and you can make yourself one by programming in the Terminal. About privacy issues, Dash is still not 'removed' from Unity launcher, it's part of the Unity...you can disable online search and disable file record. There's a ton to tell, but you can Google for them if you need to find solution. 

* Before doing anything, always back up your files before installing Ubuntu.
* Ubuntu can run VM's.
* VirtualBox is not come by default, need to install it manually.
* Be advised, Linux is hard at first, it will be easy if you willing to learn.


If you want to test Ubuntu, simple make it bootable in USB, and boot the PC with USB, and hit try Ubuntu...No need to download any virtualizing software.


Also, using softwares or programs that we don't know how it's worked increasing 'paranoid feeling'. Better to make your own. It's possible for a user that know basics stuff about Linux -
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/).

---

### Post by dino99 on 2015-04-21
if you are not yet ready to move to ubuntu for real, then you can install virtualbox on windows, then install ubuntu inside it. That way you can test it and continue with windows until you decide to switch .
Glance at the link below for more howto/wiki

---

### Post by darknet2 on 2015-04-21
Many Thanks for the replies. 

May I know how to install a virtual machine in Ubuntu WITHOUT virtualbox. Is KVM the only solution?

---

### Post by Vladlenin5000 on 2015-04-21
There are many other solutions, including the well know VMWare but... What is the problem with Virtualbox?

---

### Post by RobGoss on 2015-04-21
LIke you I have also moved from Windows to Linux, best choice I could have ever made. Like anything else as one stated if you're willing to learn then nothing is impossible.
With a group and community like this, it won't be hard because everyone here is willing to help in some shape or form. Best of luck to you and welcome to Ubuntu it's all beans :)

---

### Post by sammiev on 2015-04-21
I use VMware on Ubuntu with no issues.

---

### Post by matt_symes on 2015-04-21
Hi

> **darknet2 said:**
> ..    1. How to run VM's within Ubuntu Linux without Virtualbox or any other type 2 hypervisors?

If you're looking for a type 1 hypervisor then take a look at Proxmox. It's based on KVM and Linux and can also leverage containers.

[https://www.proxmox.com/en/proxmox-ve](https://www.proxmox.com/en/proxmox-ve)

There is also xen if you want to take a look at that.

Kind regards.

---

### Post by grahammechanical on 2015-04-21
You should download the Ubuntu ISO image and burn it to a DVD or USB memory stick and run a live session. Then you can see for yourself. Read the legal notice at System Settings>Details. And also check out System Settings>Security & Privacy>Files & Applications or Search or Diagnostics. Make your own mind up.

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

I doubt very much if it is possible to set up a virtual machine on any OS without installing some program or other. Virtual machine applications are not part of the default set of applications in Ubuntu. You might find a Linux distribution somewhere that just happens to include a VM program as part of its default set of programs. At some point you will have to trust the organisation supplying the OS and the applications or stop using a computer.

Regards.

---

### Post by Geoffrey_Arndt on 2015-04-22
Here is a distro that is already "pre-configured" for enhanced security and privacy:  [http://distrowatch.com/table.php?distribution=tails](http://distrowatch.com/table.php?distribution=tails)

Also, VPN's can be installed (open or prop.) that enhance security and privacy.   But "Tails" is a better choice than just trying VM's (imho).   Tool of choice for many including E. Snowden.

Edit:   you should know though, downloading Tails may actually result in increased scrutiny and monitoring.

---

### Post by haplorrhine on 2015-04-22
They recently configured Dash Home to collect information on your searches, I think for Amazon, but I think you can disable it.

---

### Post by pepsifx357 on 2015-04-23
I use KVM with Virt-Manager to manage it.

```
sudo apt-get install qemu-kvm libvirt-bin ubuntu-vm-builder bridge-utils virt-manager
```

---

### Post by cariboo on 2015-04-23
> **haplorrhine said:**
> They recently configured Dash Home to collect information on your searches, I think for Amazon, but I think you can disable it.

This can easily be turned of in System Setting-> Security & Privacy.

---

### Post by cariboo on 2015-04-23
> **haplorrhine said:**
> They recently configured Dash Home to collect information on your searches, I think for Amazon, but I think you can disable it.

This can easily be turned off in System Setting-> Security & Privacy.

---

