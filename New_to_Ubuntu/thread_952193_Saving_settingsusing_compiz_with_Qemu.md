---
title: "Saving settings/using compiz with Qemu"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by crimlaw on 2008-10-18
About two weeks ago, I downloaded and installed Ubuntu 8.04 using the "install within windows" option. I have been using both OS's and loving Ubuntu. However, getting back and forth between the two is a little annoying because it requires the full restart. So, I did some google searching and found Qemu. Following this tutorial:
[http://www.pendrivelinux.com/2008/06...shared-folder/](http://www.pendrivelinux.com/2008/06...shared-folder/)

I got Ubuntu 8.04 onto my portable harddrive, and it appears to run just fine (a little slow though). However, I am not sure how to "install" Ubuntu from this point. In other words, I still want to install the OS so I can change it and use programs like compiz, but then I love the ability to flip back and forth between the Os's. Is this possible?

Also, what are the drawbacks to using ubuntu this way?

Thanks!!!

---

### Post by Ptero-4 on 2008-10-18
You might want to use virtualbox instead of qemu for this. VirtualBox is faster since it virtualizes (pass the instructions through without conversion, which is good since you're gonna be doing an x86-on-x86-compatible) instead of emulating (which converts the instructions from the host to the guest CPU, redundant since you're on a x86-compatible CPU), also virtualbox is far easier to set up (entirelly graphical) and is also OSS. To do the install you create a virtual HD using the wizard that appears when you make the "virtual PC", you can also make virtual HD's using the disk manager. BTW, no one of the known non-M$ PC emulators (vmware, virtualbox, qemu, parallels and bochs) emulate a graphics adapter good enough to use compiz, so compiz is a no-no under a VM.

---

### Post by crimlaw on 2008-10-18
yeah, I figured it was too good to be true thinking I could use compiz.  But, thanks for the response.  Looks like I am just going to have to continue to restart all the time. 

Thanks for the help

---

