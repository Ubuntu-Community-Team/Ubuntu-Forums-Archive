---
title: "Unable to start virtual box"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by rraj.be on 2008-07-13
When ever i start the virtual box its giving me this error in new window

```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```
Any solution

---

### Post by rcdeacon on 2008-07-13
You have to get the correct kernel from the repos and then it should load. There is already a thread on this issue. Please do a search for "virtualbox" and you should find it easily. I will look for it also and post back.

EDIT: Thought of something else. you may have to reboot once the new kerneal is installed in order for it to work.
[http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)

---

### Post by hyper_ch on 2008-07-13
(1) is your user in the vboxuser group?
(2) if it is, then reinstall vbox... maybe there has been an issue (or kernel update)

---

### Post by ChameleonDave on 2008-07-13
> **rraj.be said:**
> When ever i start the virtual box its giving me this error in new window

Any solution

Have you tried doing what it says to do?

---

### Post by Canis familiaris on 2008-07-13
Search for "vboxdrv" in synaptic and install the virtualbox modules
Also add your user to vboxusers group.

ANother advice:
Use closed source version of VIrtualbox instead of VIrtualbox OSE.

---

