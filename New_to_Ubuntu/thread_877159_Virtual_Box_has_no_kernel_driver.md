---
title: "Virtual Box has no kernel driver"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by yoderian on 2008-08-01
Hello all,

I am wanting to run XP on Virtual Box.  I have set up VB for XP but every time I try to start it gives an error that says:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

I have looked through forums and haven't had much luck.  I am not a programmer I am brand spanking new to Ubuntu and Linux, But I'm sick of all of windows problems.

---

### Post by primolarry on 2008-08-01
Well the error message is pointing out the solution ("Please install the virtualbox-ose-modules package for your kernel").

Just find out which kernel do you have:

```
uname -r
```

And install the package, let's suppose you have 2.6.24-18-386 kernel, you would install:

```
apt-get install virtualbox-ose-modules-2.6.24-18-386
```

And run again the installer.

---

### Post by raptor2552 on 2008-08-01
Do not use the OSE version. Uninstall using Synaptic Manger and then follow the How To: [http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)

---

### Post by Thelasko on 2008-08-01
The OSE version works fine.  You simply don't have the right permissions to use virtualbox.  Open the terminal and enter the following:
```
sudo adduser $USER vboxusers
```
Log out and log back in, all should work.

---

### Post by The Cog on 2008-08-01
> sudo apt-get install virtualbox-ose-modules-2.6.24-18-386

That's not quite right - do that and vbox will stop working after the next kernel version update. Instead, do:
> sudo apt-get install virtualbox-ose-modules-generic
or server instead of generic it that's your kernel version. cat /proc/version will tell you whether its generic, server or whatever. Thing is, this un-versioned package always calls in the latest numbered package and therefore gets upgraded along with the kernel. The numbered package doesn't get upgraded automatically, of course.

---

### Post by yoderian on 2008-08-02
> **Thelasko said:**
> The OSE version works fine.  You simply don't have the right permissions to use virtualbox.  Open the terminal and enter the following:
```
sudo adduser $USER vboxusers
```
Log out and log back in, all should work.
I have already changed the permissions to use vbox

---

### Post by yoderian on 2008-08-02
> **raptor2552 said:**
> Do not use the OSE version. Uninstall using Synaptic Manger and then follow the How To: [http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)
getting rid of the OSE version seems to have done the trick.  Am I going to need all my drivers and everything for xp???

---

### Post by Locke_99GS on 2008-08-02
No, virtual machines use virtualized hardware - your nVidia drivers and such won't work within a VM.

---

### Post by primolarry on 2008-08-03
> **The Cog said:**
> That's not quite right - do that and **vbox will stop working after the next kernel version update**. Instead, do:

or server instead of generic it that's your kernel version. cat /proc/version will tell you whether its generic, server or whatever. Thing is, this un-versioned package always calls in the latest numbered package and therefore gets upgraded along with the kernel. The numbered package doesn't get upgraded automatically, of course.

Well that depends, I don't want my kernel to be upgraded except when I specifically want it, so I have installed my kernel pkg (2.6.24-18-386) but I don't have any virtual pkg like kernel-image-generic installed.

Do you guys point usually to the generic pkg?

Regards,

---

