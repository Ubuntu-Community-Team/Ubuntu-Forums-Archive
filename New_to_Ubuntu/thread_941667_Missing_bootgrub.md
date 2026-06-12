---
title: "Missing /boot/grub"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by rayboston on 2008-10-08
Hi,

I just installed ubuntu on my dell lattitude d820, but I'm getting the grub error: "Error 21"

Investigating it, I've found that I don't have a /boot/grub directory. 

Do I need to reinstall grub?

Ray

---

### Post by phidia on 2008-10-08
Well if grub is giving that error it's installed. It sounds like you need to set up grub.
Take a look at the guide [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub") from the wiki. You may not need to do all those steps, but that should get you going.

---

### Post by Forbees on 2008-10-08
if that doesn't work (didn't when i had the problem) you need to use the live cd to reinstall linux

but you can still keep all of your files

when installing do a manual configure with the partitioner, tell it which partition is ubuntu/windows(if any) but selcting ex3 or windows/dos

DONT CLICK FORMAT PARTION

continue with the reinstall

this reinstalls the ubuntu kernal, WITH grub

all of your files will still be there, and all of your settings(once you finish updating/installing drivers) should be there too

when i did this, after my updates and restricted graphics card i have my desktop effects and everything back to normal after a reboot



hope that helps

---

### Post by phidia on 2008-10-08
You do not need to do a reinstall of the whole system!

If the guide doesn't work for anyone having this problem get the [Super Grub Disk]("http://www.supergrubdisk.org/") and use that.

---

### Post by philinux on 2008-10-08
Quick fix is to use the supergrub disk. 
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Choose your preferred download from the links on the right.

---

### Post by rayboston on 2008-10-08
I think you're close to the issue.  Currently the partitioner (from live CD install) is saying not to use the  partition on my machine.  Then it gives me a pulldown menu of types of partitions.

I have a big NTFS partition.  What should I choose from the pulldown menu?

Thanks!

---

### Post by Thelasko on 2008-10-08
Don't reinstall, use the supergrub disk if you can.

---

### Post by rayboston on 2008-10-08
I'm having trouble getting the supergrub disk to boot now.

But, I've noticed that the USB I'm using for the superdisk has /boot/grub

But my hard drive does not have /boot/grub

Also my hard drive is not mounted (accoring to the partion manager that runs with the install.)

When I select my hard drive in the installer's partition manager, it says that the drive is not to be used.  I think it should use it, but I don't know what kind of file system to make it or where it should mount it.

Any thoughts on that?

Thanks!

Ray

---

### Post by Thelasko on 2008-10-08
Is your BIOS configured to boot from a USB device?

---

### Post by dryan775 on 2008-10-09
Slightly simmilar problem here:

I have installed ubuntu 7.10 on my system (dual boot with Windows XP).  I've been using it for a couple of months now (LOVE it compared to Windows).   After the OS selector, I get a resolution error and can not see the splash screen (the one with the ubuntu logo and (the LiveCD version had) the orange "cylon eye" animation).  The system works OK once I got to the user logon screen.

I tried to fix it by editing the /boot/grub/menu.lst file and adding the vga= command to the kernel line.  I tried several numbers, each one only seems to change the resolution in the text shells (the Ctr-Alt-F1 through F6), most are not visable except if I leave the vga= portion out of the menu.lst file. 

Any ideas on how to change the video mode for the logo/animation screen (after OS selector and before the user logon) ???  

Thanks for any info !

Daron Ryan
[email]daron@darasdesigns.com[/email]

---

### Post by cardv on 2008-10-09
thanks for tips

---

