---
title: "Dual-Boot from LINUX TO Windows"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Stabilityonitsown on 2008-05-26
I have been searching EVERYWHERE. And all I can find is tutorials for people that want to dual-boot from windows to linux. Can you guys plzzzz help me?:(:( How do I dual-boot from linux to windows?

---

### Post by Inxsible on 2008-05-26
Install XP on a partition on your drive. Make sure its a primary partition. XP won't install in a logical partition.

Then use [Supergrub]("http://www.supergrubdisk.org/") disk to restore the grub.

That's all that you need to do.

---

### Post by iaculallad on 2008-05-26
> **Stabilityonitsown said:**
> I have been searching EVERYWHERE. And all I can find is tutorials for people that want to dual-boot from windows to linux. Can you guys plzzzz help me?:(:( How do I dual-boot from linux to windows?

The reason why you see many tutorials on dual booting from windoze to Linux (Ubuntu) is that windoze is too much too handle, it wants to be the first to load its MBR, unlike Ubuntu that it could re-configure/adjust itself if it finds other OS's installed prior to itself.
In your case of installing Ubuntu first then windoze, you could always use this [guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-68342fc2e30d51fa0aa6f5bf16c911dd8d3663c6") to fix any mess caused after windoze installation.

---

### Post by King_Critter on 2008-05-26
It's pretty simple. First you have to manually partition your hard drive, since Windows can't do that. Check out the GParted Live-CD -- just Google it. You'll also need Super Grub (again, Google it) for restoring the Grub bootloader. 

After you have those two tools downloaded and burned to CDs, the first step is to partition your hard drive. Restart your computer with the Gparted disc in your CD drive, and it should boot into a graphical environment displaying GParted. Just shrink your Linux partition and hit apply. Wait a few minutes while it does its stuff. After it's done, install Windows. While installing, be sure to tell it to install in the unpartitioned space you freed up. After that finishes, you'll notice that you can only boot into Windows. To fix this, reboot your computer with the Super Grub disc in your drive, and look for an option that say something like "restore grub." Select that, choose the correct file (there should only be one) hit enter, and try rebooting your computer again. It should display Grub, allowing you to select your operating system. If windows doesn't show up on the list, then you may need to manually add it. Search Google for guides to modifying grub/menu.lst. :)

---

### Post by jlandaw on 2008-05-26
> **Inxsible said:**
> Install XP on a partition on your drive. Make sure its a primary partition. XP won't install in a logical partition.

Then use [Supergrub]("http://www.supergrubdisk.org/") disk to restore the grub.

That's all that you need to do.

I agree with Inxsible, but I dont know f you need to use another program to do that in Denian.

To duel boot with the grub menu, you need to have windows still on a primary partition. Grub will find the "Longhorn/Windows bootloader and you can load windows from it... 

The best thing is to have windows installed and working, then install linux or reinstall the grub bootloader..

You may have to use the methods in theos other tutorials at firs to get to Linux - duel boot form windows to set up the duel boot in grub

---

### Post by cdtech on 2008-05-26
Do you have Ubuntu installed? Are you using one drive or two?

---

### Post by cdtech on 2008-05-26
It's pretty easy really:

With the live Ubuntu cd.

When you get to the desktop open a terminal and enter.

sudo grub

This will put you into a "grub>" shell (i.e. the grub prompt). At grub>. enter these commands

grub >find /boot/grub/stage1

Whatever was returned for the find command use it in the next step (you are still at grub>.

grub >root (hd?,?)

Again use the value from the find command i.e. if find returned (hd1,5) then you would enter root (hd1,5)

Next enter the command to install grub to the mbr

grub >setup (hd0)

Then exit the grub shell

grub> quit

Then reboot without the CD.

---

