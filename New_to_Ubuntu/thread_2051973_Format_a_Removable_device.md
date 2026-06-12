---
title: "Format a Removable device?"
date: 2012-09-02
forum: New to Ubuntu
---

### Post by nachinew on 2012-09-02
Hi,

New to UBUNTU, what are the method to format in Ubuntu?
 How to format a removable device in Ubuntu...

---

### Post by Bodsda on 2012-09-02
> **nachinew said:**
> Hi,

New to UBUNTU, what are the method to format in Ubuntu?
 How to format a removable device in Ubuntu...

The easiest way is probably with a program called 'gparted'
It may already be installed.

Gparted gives you a graphical interface to disk partitioning. 
[https://help.ubuntu.com/community/GParted](https://help.ubuntu.com/community/GParted)

HTH,
Bodsda

---

### Post by The Cog on 2012-09-02
+1

If gparted is not already installed, then this command on the command line will install it:
```
sudo apt-get install gparted
```

Once you launch the program, there is a drop-down at the top right that lets you choose the drive you are working on. Be careful not to format the wrong drive - it defaults to working on the main drive on your computer.

---

### Post by coffeecat on 2012-09-02
There's also Disk Utility which is already installed.

But if you want to format a USB device without creating more than one partition and you are using Ubuntu 12.04, simply right-click on the mounted device icon in the launcher and choose "Format". You can open Disk Utility from the format window if you want more control.

---

### Post by nachinew on 2012-09-03
Thanks All. 
So the Option are gparted and Disk Utility right.
Any other option to mount and demount the external devices.
:p

---

### Post by Paqman on 2012-09-03
Removable devices will be mounted automatically when you plug them in. To unmount a device you can right click on it's icon on the launcher (left of screen) and select the option from there.

---

### Post by nachinew on 2012-09-03
> **Paqman said:**
> Removable devices will be mounted automatically when you plug them in. To unmount a device you can right click on it's icon on the launcher (left of screen) and select the option from there.

ok, If again i want to Remount means what should i do, I will not plug out the device???;)

---

### Post by Paqman on 2012-09-03
> **nachinew said:**
> ok, If again i want to Remount means what should i do, I will not plug out the device???;)

Good question; I have no idea. I just pull it out and plug it back in.

---

### Post by nachinew on 2012-09-03
Any one have an idea, Please share here.....:D

---

### Post by Bartender on 2012-09-03
Well, that's all I do if I've unmounted and want to remount.  Unplug the USB cord and plug it back in.  Are you saying you don't want to do that?

I'm still using 10.04.  I plugged in a USB thumb drive just now to double-check.  An icon appears on the desktop.  If I right-click and Eject, or Safely Remove, the icon disappears and I don't know how you'd get it back.  

There's probably some Ubuntu geek-fu way to reacquire it, but I just unplug it & plug it back in.

---

### Post by nachinew on 2012-09-03
> **Bartender said:**
> Well, that's all I do if I've unmounted and want to remount. Unplug the USB cord and plug it back in. Are you saying you don't want to do that?
 
I'm still using 10.04. I plugged in a USB thumb drive just now to double-check. An icon appears on the desktop. If I right-click and Eject, or Safely Remove, the icon disappears and I don't know how you'd get it back. 
 
There's probably some Ubuntu geek-fu way to reacquire it, but I just unplug it & plug it back in.
 
Lets see I will make this question in another post may i will get the answer.....thanks any ways:lolflag:

---

### Post by Couture2010 on 2012-09-04
just pull it out and plug it back in.

---

### Post by marlow59 on 2012-09-04
I think even if you unmount a flash drive, it still can be seen in Gparted and remounted from there.

---

