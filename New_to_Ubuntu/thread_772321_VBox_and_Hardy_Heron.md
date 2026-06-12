---
title: "VBox and Hardy Heron"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by almabeck on 2008-04-28
I upgraded to Hardy but now can't get VBox to start. I get the message below when I try. [Don't know if it's related, but I also have lost sound upon upgrade. When I test sound, it looks like the computer thinks I'm hearing something, as the test indicators seem to be working normally--no error message or anything, just no sound. Sorry, I'm a newbie and don't know the proper terms.]

VBox error message:


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by hyper_ch on 2008-04-28
I did download the 7.10 .deb from the vbox site and that works like a charm. You might want to try that.

---

### Post by GavinZac on 2008-04-28
you open a terminal and run this:

sudo apt-get install virtualbox-ose-modules-generic

or just do a search for "virtualbox-ose-modules-generic" in Synaptic Package Manager (System->Admin->Synaptic) and install that. It will automatically add the proper driver you need then.

---

### Post by almabeck on 2008-04-28
> **GavinZac said:**
> you open a terminal and run this:

sudo apt-get install virtualbox-ose-modules-generic

or just do a search for "virtualbox-ose-modules-generic" in Synaptic Package Manager (System->Admin->Synaptic) and install that. It will automatically add the proper driver you need then.

Awesome! Your suggestion worked like a charm. Now I can use my knitting program again. Many thanks for taking the time to help.
Alma

---

### Post by hyper_ch on 2008-04-28
> **almabeck said:**
> my knitting program

Got some pics of your works (knittings)?

---

