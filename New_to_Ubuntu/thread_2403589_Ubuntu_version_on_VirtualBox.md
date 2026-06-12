---
title: "Ubuntu version on VirtualBox"
date: 2018-10-13
forum: New to Ubuntu
---

### Post by az-dev on 2018-10-13
Hi, I am new to Ubuntu and to virtual machine in that matter.  I am trying to create a virtual machine with Ubuntu OS on it.  Can I ask whether I can install (make an ISO image) from the 'main' Ubuntu desktop version here: [https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop), or do i need a 'special' version, download link, for the virtual machine iso?

Thank you

---

### Post by TheFu on 2018-10-13
It is best to run a non-GPU intensive flavor of Ubuntu for use in VMs.  The default, main, release wants direct access to the GPU which is non-trivial under virtualization.  

So, a few questions and options.

Which hypervisor are you hoping to use? KVM, qemu, Xen, and virtualbox are popular options. Each has pros/cons.

Which non-GPU intensive flavor of Ubuntu will be used? Lubuntu, Xubuntu, Ubuntu-mate are popular options. There are others.

The special virtual machine version of Ubuntu server is a tiny, server. It lacks any desktop, no GUI, and is limited in the shell programs provided to be as light as possible.  This isn't what a desktop user needs. All the ISOs for Ubuntu can be used directly by a hypervisor to boot and install into a virtual machine.

---

### Post by az-dev on 2018-10-13
Thanks for your reply.  Oh my, I didn't know about the other Ubuntu versions even existed.  

In terms of which hypervisor to use, I have both, windows 10 hyper-v and VirtualBox installed.  I think I will be using VirtualBox.

I am now even more confused which version of Ubuntu to use.  One thing I understood is that on vm best to use one of the lighter versions.  But there so many.  

I will be using for some programming by installing java jdk, node.js, maybe android sdk etc.  These are all for my uni course subjects.  Perhaps I can just try the light versions one-by-one and see which is best suited for my needs?

Thanks

---

### Post by TheFu on 2018-10-13
It is NOT a good idea to have 2 hypervisors installed at the same time. Remove the one you don't use to prevent conflicts.  Might need to remove both, then reinstall the one you want.  In these forums, you'll get more help with virtualbox. As you can imagine, hyper-v isn't used much by linux people.

Doing java development is a hog regardless of which OS you use.  I'm afraid you'll be disappointed with the performance regardless because that is the nature of Java programming. You don't have enough CPU or RAM, regardless of your physical machine.  Java makes a $1,000 Core i7 CPU seem slow and wants 32G of RAM.  I consider 8G of RAM the minimum for java development. 

I got so frustrated with java development that I stopped and switched to a different language.  I was lucky and had the choice, since I'd already been a professional programmer 15 yrs. Java can teach some important lessons, but it can also lead new programmers into believing that the physical hardware isn't important, which is false.  Never forget that code runs on real hardware as some point and poorly written code will run poorly.

As for picking a flavor, installing into a new VM is about 10-20 minutes and you can wipe them afterwards.  That isn't much of a commitment and every new install does teach some new lessons. The better you get at installing now, the better you will be when it is important and you don't have time for mistakes. Learn the VM settings that help make performance better.  Search for "virtualbox tuning" for some articles about that.  The default VM settings are better than they were, but still lacking.  You can't please everyone all the time and server settings need to be different from desktop settings.

You can have 25 different VMs installed if you have the storage for them.  10G is enough for a test VM and 25G is enough for a full desktop VM.  My main desktop uses ... 
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        20G   17G  1.8G  91% /
```
17G right now.  This machine was first installed in 2010 and has gone from 10.04 --> 12.04 --> 14.04 --> 16.04 Ubuntu updates.  If I need more storage for home, next time I'll add another virtual disk file.  I do ruby and perl development on this VM.  My HOME used 7.2G, so the OS really used under 10G currently.  With Java, you'll need more - bloat.  But that should be added as a separate virtual disk for a number of reasons.  That way you can use that HOME with the different flavors, if you like.  Just make certain the storage is only used by 1 running VM at a time. It would be bad otherwise.

So ... if you have 250G available, temporarily, you can test out 25 flavors of Linux.  ;)  Have the appropriate amount of fun!

---

### Post by az-dev on 2018-10-13
Thank you for your detailed explanation and suggestions - much appreciated.  As suggested I will try to create several VMs and learn in the process.  

I do understand your disappointment about the Java, but I have no choice but to do it as part of my study module.  

Thanks

---

### Post by SeijiSensei on 2018-10-14
Meanwhile, if you're shopping for distributions, use [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/).  

For starters you might try Lubuntu or Xubuntu as they are more "light-weight" than standard Ubuntu of Kubuntu.

Just download these ISOs to your hard disk, then point to them as the installation medum when setting up a new VM in VirtualBox.

Lubuntu: [http://cdimage.ubuntu.com/lubuntu/bionic/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/bionic/daily-live/current/)
Xubuntu: [http://cdimage.ubuntu.com/xubuntu/bionic/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/bionic/daily-live/current/)

Use an "LTS" version like 18.04 (named "Bionic Beaver") since it will be supported for five years.  All other releases are transitory and will only be supported for nine months.  Details here: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

