---
title: "Virtual Machine of existing OS on separate partition?"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by bigcat42 on 2008-11-24
My laptop has Ubuntu 8.10 and Windows Vista installed on separate partitions. While I prefer using Ubuntu, I occasionally need to access certain programs through Vista. What I would like to do is be able to start up Vista without rebooting the computer (and then rebooting back to Ubuntu when I'm done).

In other words, I would like to use a virtual machine (or something similar) to boot up an OS from an existing partition. I want to retain my existing dual-boot setup, but gain the benefits of using a virtual machine. Is such a thing possible?

---

### Post by grazed on 2008-11-24
It is possible. Though it requires a bunch of work from the terminal and modification to your MBR. 

Make sure you image your HDD before starting (there's a chance you can bork your MBR and not be able to boot past grub) and have a look at VMware.

[http://blogs.vmware.com/vmtn/2007/01/running_a_physi.html](http://blogs.vmware.com/vmtn/2007/01/running_a_physi.html)

A much easier solution is just to do a virtualbox/vmware/parallels install from within linux and import your files and settings.

---

### Post by gunga-din on 2008-11-24
Or you could use the vmware converter and convert your vista machine to to a vmware virtual machine, this way you only ever need to boot in to ubuntu and just fire up the vista VM whenever you need it, the only drawback at the moment is that the graphics adapter in vmware doesnt support 3D.

I currently have Ubuntu as my base OS and have 2xp boxes and one vista all running happily together in a completely virtual network environment.

---

### Post by hyper_ch on 2008-11-24
vmware supports now directx 9.0c

---

