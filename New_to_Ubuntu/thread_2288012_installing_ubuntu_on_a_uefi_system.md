---
title: "installing ubuntu on a uefi system"
date: 2015-07-23
forum: New to Ubuntu
---

### Post by jjamescbarrow on 2015-07-23
hey guys, not all new to ubuntu, ive played with it a little. my question is, I have a dell inspiron 17 5000 that is running windows 8.1 which sucks. 

I thought about dual booting but i really dont wanna take a chance on screwing up the boot loader if I ever to go uninstall ubuntu

I have a spare drive, can i just slip that drive in, boot off of the usb that I currently am booting off of, and install ubuntu on that computer, will I have any conflicts with the uefi if I go to do it.

If so what issues will I encounter.

---

### Post by grahammechanical on 2015-07-23
The issue with UEFI is simple. If Windows 8.1 is installed in EFI mode then Ubuntu will also have to be installed in EFI mode. And just to be clear, Windows 8.1 if it comes pre-installed will most definitely have been installed in EFI mode.

The Ubuntu installer will let you select which hard drive to install Ubuntu on. You have to choose the Something Else option. The installer will default to installing the Linux boot loasder (Grub) into the MBR of the first hard disk (sda) but there is a panel with a drop-down menu that will let you select the second hard disk (sdb). 

Alternatively, you could disconnect the Windows drive then let the installer use the only drive connected and you could choose the Erase Disk and install Ubuntu option with safety. After the installation is running and you have confirmed that Ubuntu loads correctly you then reconnect the Windows drive, load into Ubuntu by selecting the Ubuntu drive in the UEFI boot system and when Ubuntu is loaded run this command

```
sudo update-grub
```

That should give you a Grub boot menu that lets you load both Ubuntu and Windows. You will still need to load the Ubuntu live session in EFI mode and install Ubuntu in EFI mode.

Regards.

---

### Post by Vladlenin5000 on 2015-07-23
Hi and welcome.

Yes, by doing as you intend you should have no issues installing and using, no more than the specific notebook would have otherwise:
A Dell Inspiron 1501 is almost 10 years old now, no surprise it sucks with Windows 8.1. Windows 7 should run acceptably and Ubuntu likewise (no exotic or known linux unfriendly hardware to speak of).

---

### Post by jjamescbarrow on 2015-07-23
actually the inspiron 17 5000 series is what it is, i was wrong.

---

### Post by Vladlenin5000 on 2015-07-23
> **jjamescbarrow said:**
> actually the inspiron 17 5000 series is what it is, i was wrong.

Yeah, completely different.
Intel Graphics only or Intel+nvidia hybrid? The former should be a breeze to install, the latter not so much.

---

### Post by jjamescbarrow on 2015-07-23
looks like intel graphics only, we currently have it booted off of a usb, running 15.04 and she says its running fine, and a note (she has never ran linux/ubuntu period) and she actually likes it better than windows.

---

### Post by Vladlenin5000 on 2015-07-23
If it runs fine in the live session, go ahead an install. :p
Any problem/issue, start a new thread describing it.

---

