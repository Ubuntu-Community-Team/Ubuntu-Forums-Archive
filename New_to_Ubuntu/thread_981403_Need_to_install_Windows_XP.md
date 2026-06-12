---
title: "Need to install Windows XP"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by pretone on 2008-11-13
I need to install XP (:() on a system that is running Ubuntu 8.04.

It won't recognize the .exe file on the install disc, how can I make it work?

---

### Post by oilchangeguy on 2008-11-13
> **pretone said:**
> I need to install XP (:() on a system that is running Ubuntu 8.04.

It won't recognize the .exe file on the install disc, how can I make it work?

first, what is "it"? are you trying to install xp in ubuntu? more details please.

---

### Post by pretone on 2008-11-13
Yes I am trying to install Windows Xp in Ubuntu.

---

### Post by redbob on 2008-11-13
There are two alternatives:
1) Install Virtualbox, so you must install XP within it;
2) Install wine, so you may run several windows apps.

---

### Post by pretone on 2008-11-13
Alright when I try to install Wine it says it depends on binfmt-support
Where can I get that?

---

### Post by kansasnoob on 2008-11-13
If you're looking to dual-boot look here:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by pretone on 2008-11-13
> **kansasnoob said:**
> If you're looking to dual-boot look here:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

I get stuck at step four.
Ubuntu will not recognize/ play the XP install disc.

---

### Post by oilchangeguy on 2008-11-13
> **pretone said:**
> I get stuck at step four.
Ubuntu will not recognize/ play the XP install disc.

it seems you're doing this wrong. you have to boot the computer from the windows xp cd. not try to install xp inside of ubuntu. read step four again.

---

### Post by kansasnoob on 2008-11-13
> **oilchangeguy said:**
> it seems you're doing this wrong. you have to boot the computer from the windows xp cd. not try to install xp inside of ubuntu. read step four again.

That's right.

You have to restart the computer and then it's all up to you, and the Windows detection thing.

If the Win XP disc won't run when you restart the puter then either your disc or your drive is bad, or something is NOT set right in BIOS.

BIOS must be set to boot from CD first!

---

### Post by pretone on 2008-11-13
> **oilchangeguy said:**
> it seems you're doing this wrong. you have to boot the computer from the windows xp cd. not try to install xp inside of ubuntu. read step four again.

Okay I've been trying that, but it won't work. I'm not sure if I have a boot disc, but it is an install disc. I tried it on another computer and it opens up fine


How do I get a binfmt-support file that I need to install Wine?

---

### Post by kansasnoob on 2008-11-13
> **pretone said:**
> Okay I've been trying that, but it won't work. I'm not sure if I have a boot disc, but it is an install disc. I tried it on another computer and it opens up fine


How do I get a binfmt-support file that I need to install Wine?

I honestly don't understand much of what you're saying!

You can install wine from synaptic or:

```
sudo apt-get install wine
```

I really think you need to do some studying. Maybe start here:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by handydan918 on 2008-11-13
First of all, see if there is as linux users group in your area. You really don't seem to have any idea about what you are trying to undertake, and while setting up a dual-boot system isn't rocket science, it IS computer science.  You might benefit from some hands-on help.

---

### Post by johnhouk on 2008-11-13
> **pretone said:**
> I get stuck at step four.
Ubuntu will not recognize/ play the XP install disc.

This guys got a nonbootable (Probobly mis-burnt) disc, ... or maybe an iso file, or just the install files in a folder.

Any I stumbled here looking for similar only i do have a bootable disc, just no way to boot from it. My laptops Hard Drive AND Floppy drive are no good. my bios dosn't support the usb port, but does have a network boot option.

I couln't get a windows installation going because the "FreeDOS" behind the "OSdeploy" software i was using would fail in the manipulation of it all* But I could get an ubuntu installation to go. ...PXE over TFTP and all.

ANYWAY now i'm here and i'm still looking for windows options.

What I want to know if is there a way to copy the files inplace to where windows setup is run on the next boot!

Thataway I could either follow those dual boot instructions or reinstall alltogeather.

I'll try and see if wine will allow me to run the setup.exe (win32 app). 
If not ill have to adapt to this kernel and virtualize the rest.

Please don't reply to my problem here. I'm starting a new thread for that. I'll call it. BootSector 



*It hits an an error conserning the himem, I forget what it was exactly.

---

### Post by medley on 2008-11-13
> **pretone said:**
> I need to install XP (:() on a system that is running Ubuntu 8.04.

It won't recognize the .exe file on the install disc, how can I make it work?

A good option for you might be to install VirtualBox in Ubuntu, then install XP as a virtual machine. I've done this before and it works well as long as you have sufficient ram. In fact right now I'm using Ubuntu in a virtual machine on Vista using VirtualBox. You'll need a gig of memory to get satisfactory results. You can just launch XP from within Ubuntu when you need it.

Good luck.

---

