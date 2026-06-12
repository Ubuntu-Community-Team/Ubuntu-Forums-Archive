---
title: "how to reset Ubuntu back on?"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by bilbo.san on 2008-11-11
Hey!

I have WinXP and Ubuntu on different partitions on my machine... but recently Windows crashed (for a change!) and was forced to re-install again. After that it lost that Boot system where you select the operating system to start the PC with... is there a way to get it back on? ... or should I re-install Ubuntu again. Hope not, I have lots of things there.

For any help, Thanks in advanced!!!

b.

---

### Post by overdrank on 2008-11-11
> **bilbo.san said:**
> Hey!

I have WinXP and Ubuntu on different partitions on my machine... but recently Windows crashed (for a change!) and was forced to re-install again. After that it lost that Boot system where you select the operating system to start the PC with... is there a way to get it back on? ... or should I re-install Ubuntu again. Hope not, I have lots of things there.

For any help, Thanks in advanced!!!

b.

Hi and this link may help
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Coreigh on 2008-11-11
Just restore / fix grub ( the boot menu )
[http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")

---

### Post by B34ST1Y on 2008-11-11
as said above, try restoring GRUB, the boot manager that dictates what operating system you can boot into. If you are STILL having trouble after all the above help, visit [http://www.ultimatebootcd.com](http://www.ultimatebootcd.com)  <---download the disc, and boot from it. Load a boot manager that is preloaded onto the disc, and see if that doesn't fix your issue. 


Cheers. :)

---

### Post by Keen101 on 2008-11-11
I recommend the Super Grub Disk. I've used it ton's of times on various computers to restore grub. [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Krupski on 2008-11-11
> **bilbo.san said:**
> Hey!

I have WinXP and Ubuntu on different partitions on my machine... but recently Windows crashed (for a change!) and was forced to re-install again. After that it lost that Boot system where you select the operating system to start the PC with... is there a way to get it back on? ... or should I re-install Ubuntu again. Hope not, I have lots of things there.

For any help, Thanks in advanced!!!

b.

Use a live CD and boot up into Ubuntu. Open a console (command line) shell.

Let's [COLOR="Red"]**ASSUME**[/COLOR] your system is setup like this:

Windows XP - is on /dev/sda1

Ubuntu Linux is on /dev/sdb1

Ubuntu Linux swap is on /dev/sdb5

[COLOR="Red"]**CHECK TO SEE WHAT YOUR DEVICE NAMES ARE FIRST AND ADJUST THE INSTRUCTIONS ACCORDINGLY!**[/COLOR]


First, temporarily mount your Ubuntu partition on a directory:

```

sudo cd /dev/shm
sudo mkdir linux
sudo mount /dev/sdb1 linux
ls -laF linux

```

The commands do the following:

* Change to a temporary ram disk space
* Make a temporary directory
* Mount your Ubuntu Linux system on the temp directory
* LS looks at it to see if it's there (it should look "normal").

Now, run grub-install to update your Ubuntu installation AND re-install the Grub bootloader onto your master hard drive:

```

sudo grub-install --root-directory=/dev/shm/linux --no-floppy --recheck /dev/sda 

```

This command means:

"Install GRUB, the linux root directory is "/dev/shm/linux" which points to your Ubuntu install, and install the boot loader on the Windows drive which is /dev/sda".

NOTE: Use /dev/sda (the first sector of the drive), NOT "/dev/sda1" which is the XP *partition*.


Actually, there is (in my opinion) a nicer way to dual boot... and that is by using Windows NTLDR.

After installing Linux on a secondary drive, I use "dd" to grab the first 512 bytes of the Linux disk (the master boot record). I call the file "linux.bin".

Then I stick it in the root of my Windows C: drive and add it to my BOOT.INI file.

So when I boot up, I get a *Windows* boot selection.

Hopefully, my instructions will get you back up and running.

Good luck.

-- Roger

---

