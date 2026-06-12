---
title: "Virtual machine running Ubuntu LTS 14 and KDE"
date: 2014-04-20
forum: New to Ubuntu
---

### Post by jon80 on 2014-04-20
I have just installed Ubuntu 14 LTS on Virtualbox, however, there seems to be no way of accessing a desktop which includes the possibility of installing or using applications and a desktop is of no use to me.

The problem with trying to use keyboard shortcuts is that I am afraid that they are not supported by VirtualBox v4.3.10 r93012
See article at [http://www.zdnet.com/hands-on-with-ubuntu-14-04-the-best-ubuntu-desktop-ever-7000028578/](http://www.zdnet.com/hands-on-with-ubuntu-14-04-the-best-ubuntu-desktop-ever-7000028578/).
There seems to be some issue with keyboard capture on the guest OS however it is feeling too complicated, can you help please?

It seems that Ubuntu 13, and, Virtual Box installed on top of a guest that runs Windows Server 2008 had a few problems as well see attachment.  Anyone had similar problems?

I am also reading news of Ubuntu One being shutdown on 1st June 2014, does this mean that this forum is planned to disappear, or just hosted data that needs to be downloaded by existing users?

I will give up and use another enviornment within two days.
:confused:

---

### Post by SeijiSensei on 2014-04-20
> Virtual Box installed on top of a guest that runs Windows Server 2008 had a few problems as well see attachment.

What do you mean by this?  Is Windows Server 2008 the "host" into which you installed Ubuntu, or are you trying to install Ubuntu into a VM inside Server 2008 which is itself a guest?  I sincerely doubt you can nest VirtualBox installations that way.

Why don't you start by installing [Ubuntu Server]("http://cdimage.ubuntu.com/ubuntu-server/daily/current/")?  It comes with no gui at all.  If you get that to work, you can install a desktop with a command like "sudo apt-get install kubuntu-desktop" or the appropriate flavor based on your desktop preference.

I've encountered the error shown in the second screen when installing to a machine with either an ATI or NVIDIA adapter (I forget which).  It appears to be associated with the open-source drivers; installing the appropriate proprietary driver for the graphics card made the error disappear.

---

