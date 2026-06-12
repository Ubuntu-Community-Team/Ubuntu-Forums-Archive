---
title: "[SOLVED] Changing menu.lst"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Sbarton on 2008-06-19
Hi All!, after a large update today including a linux kernel 2.6.24.19 I believe I was presented with the dialogue box with the choice of keeping the current list or choosing another (example: the package maintainer list etc). I chose to keep the current menu list. I notice now that the new kernel is not on the boot menu list and wonder if I should have chosen differently. Having looked at Synaptic I see that the new Kernel is installed.
I have AMD64 with Hardy 64 bit version.
Any info received gratefully.
regards :)

---

### Post by Dedoimedo on 2008-06-19
Hello,

You can manually add the new entry.

Go to /boot and see if it's there. Should be something like vmlinuz-2.6.4.19 or so.

Now, backup grub menu then edit it:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup

Copy the existing entry in the menu, place it above the existing one and then change the letters to reflect the latest kernel version.

Save, reboot, see if it works.

Dedoimedo

---

### Post by stchman on 2008-06-19
> **Sbarton said:**
> Hi All!, after a large update today including a linux kernel 2.6.24.19 I believe I was presented with the dialogue box with the choice of keeping the current list or choosing another (example: the package maintainer list etc). I chose to keep the current menu list. I notice now that the new kernel is not on the boot menu list and wonder if I should have chosen differently. Having looked at Synaptic I see that the new Kernel is installed.
I have AMD64 with Hardy 64 bit version.
Any info received gratefully.
regards :)

DO NOT manually change the menu.lst file.  It can produce unwanted effects.

I find the best way to configure GRUB is to use startup manager.

```
sudo apt-get install startupmanager
```

StartUpManager allows you to change your boot order, timings, display info and color.

Also do not remove kernels manually.  If you remove old kernels via Synaptic it automatically updates your menu.lst file.

---

### Post by phidia on 2008-06-19
There are several ways to do this if you get in trouble there is a [guide here]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+setup")for reinstalling grub.
You should be able to use gksudo gedit to copy your current ubuntu entry in menu.lst and then just edit/replace the kernel version with the updated one.
I posted my ubuntu entry, gutsy, below:

> ## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ea0c02c0-72c0-42e8-ac34-fc3df584affb ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
 The part you want to edit is on the line the starts with "kernel" put in you most recent vmlinuz entry.
Hope that helps.

---

### Post by Victormd on 2008-06-19
Just type
```
sudo update-grub
```
and the new kernel should be automatically included.

---

### Post by Sbarton on 2008-06-20
Thanks to all posters and your suggestions! For just changing menu list the post by Victormd worked great and seemed to be the simplest, thanks! I also found of interest the post by 'stchman'regarding startup manager.Thanks for that!

You know, Ubuntu has become so easy and good with each version I find I am using the terminal less now and forget some of the terminal input I have picked up over the years.:)
 Once again thanks to all!
regards

---

### Post by Victormd on 2008-06-20
Any time... :)
Don't forget to mark the thread as solved... :)

---

### Post by Joeb454 on 2008-06-20
I've always installed the package maintainers version, because after the last kernel entry (where it stops automagically adding them) it doesn't change at all, so it keeps my Windows boot option there :)

---

### Post by Sbarton on 2008-06-20
joeb454, thanks I now know that is what I should have chosen.
regards

---

