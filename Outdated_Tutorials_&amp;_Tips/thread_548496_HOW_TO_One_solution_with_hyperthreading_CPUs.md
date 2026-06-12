---
title: "HOW TO: One solution with hyperthreading CPUs"
date: 2007-09-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Lylepalooza on 2007-09-11
I have read in several places about some people having issues with hyper threading in Ubuntu 7.04 Feisty Fawn. Many people have stated that although:
[LIST]
[*]Their CPU/Motherboard are both capable of hyper threading
[*]They have the i686 SMP kernel
[*]They have hyperthreading switched on
[/LIST]

There CPU still isn't recognised as being Hyperthreaded IE:

[LIST]
[*]It doesn't appear as two CPU's in system monitor
[*]It doesn't appear as two CPUs if you use the Top command (followed by pressing 1) in terminal
[*]It doesn't appear as two CPUs under the command cat /proc/cpuinfo in terminal
[/LIST]

I struggled with the same issue attempting to get my CPU's hyper-threading to work. Eventually the solution was to remove "nopic nolapic" from one of the options in the grub boot menu. In my case, I can't remember why I needed to disable apic in the first place and removing these two words didn't affect my setup at all. However, there may be a very good reason why you did and removing these two words may have undesirable affects on your setup, so be warned.

The grub boot menu can be edited via:

Sudo gedit /boot/grub/menu.lst

The lines you're looking for are similar to:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash noapic nolapic

After editing this, hit save, and in terminal type:

Sudo update-grub

After a restart, you should be in business.

For me, this worked perfectly and now I am enjoying the speed boost of hyper-threading. 

Now I know the above would seem obvious to some, but to me (a noob) it wasn't. So as you want users to help other users, I thought I would put this short How To together. Moderators, feel free to move it to where ever it should go if it doesn't belong in this category.

Lylepalooza

---

### Post by abhilash82 on 2007-09-14
My System Spec. is Intel 865GBF, 2.4 GHz with HT, 256 MB RAM and in my system monitor, the usage of 2 processors can be observed. I haven't made any changes for Ubuntu to detect my HT core.:guitar:

---

