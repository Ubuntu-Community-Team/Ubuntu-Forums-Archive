---
title: "Ubuntu 10.04.3 LTS Alternate i386 won't boot after fresh (but troubled) installation"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by bronzenose on 2012-01-20
I am new to linux and Ubuntu but not to PCs and the bugs they harbor.   My unix is very weak and rusty (15 years rusty) but I can read man pages  and pipe to more.

I installed on my desktop dell from an Ubuntu 10.04.3 LTS Alternate i386 CD with  "nomodeset".  Normal installation of 10.04 LTS from CD and from USB stick  failed repeatedly despite trying combinations (including all) of  nomodeset BOOT_DEBUG=3 DEBIAN_FRONTEND=text fb=false video=vga16:off  mem=512m priority=medium snd-dummy.  Installation from 10.04 standard CD or  USB would hang with a blank screen or after a message about "checking battery state".

My current installation has never booted.  Dual boot to windows works.   GRUB offers 2 linux options which end in PC restarting (see below)  memory tests and windows vista (which boots as well as vista ever  booted).

With the latest Ubuntu version (11.x) I have been able to get all the  way to a working desktop when installing from a USB stick but I must end  up with 10.04LTS because that's the only version supported by the app  that I just have to have (EMC2).  Installing 11.10 is an option only if  there is a downgrade path from a clean new 11.10 installation to a  never-successfully-installed 10.04LTS.

Presently when I try to boot from my hard drive (all cds ejected and mass storage USB removed):
Boot from GRUB option  "Ubuntu, with Linux 2.6.32-33-generic" yields  blank screen followed by a reboot or "uncompression error -- system  halted"
Boot from GRUB option "Ubuntu, with Linux 2.6.32-33-generic (recovery mode)" yields "uncompression error -- system halted"

Possible coincidence: this is after trying "startx" from recovery  shell.  Previously I had consistently received errors when booting  related to (this is from my memory, the symptom seems to have changed)  Kernel panic -- VFS not syncing -- no filesystem can mount

I can boot from the "alternate" cd in "Rescue a broken system" mode  mounting "/dev/sdc5" and executing a shell there but I am not sure what  to do after that.  From the shell I can see a /target and i can cd there  and list files.  dmesg doesn't seem to end with any errors to report --  it ends with "EXT-fs (sdc5): mounted filesystem with ordered data mode"  but I imagine dmesg is only telling me about the recent successful boot  from the CD and not the failed boot beforehand.

I have read of problems with drives changing names depending on the  order in which they respond so I have tried booting many times to see if  they answer in the expected order but it does not seem to help.

I'd very much appreciate help either to fix the problem or on how to find more  details on what's happening.  Two weeks and dozens of hours ago I'd have  liked to understand what was going on but now I just want to fix it and  move on.  Thank you in advance.
 
My hardware:
Older (Windows Vista was brand new) Dell XPS720 with 4GB ram
three SATA hard drives: the 500GB or so drive with windows vista on it  and two Western Digital 2TB drives, the second of which has a half TB  partition for Ubuntu (sdc5) and a swap partition (sdc6).
[SIZE=-1]NVIDIA nForce®  680i SLITM  Chipset for Intel[/SIZE][SIZE=-1] with nVidia®  GeForce®  8800 set up for a large single monitor (2560x1600 pixels)
two internal optical drives (dvd CDRW etc.)

      [/SIZE]

---

### Post by mastablasta on 2012-01-20
Have you tried ACPI=off parameter? or xforcevesa?
 
you need proprietary drivers for the graphics cards. 
 
also is this a notebook?

---

### Post by bronzenose on 2012-01-20
this is a desktop not a laptop.

I'm not totally sure how to "try" those parameters.  I booted and pressed "e" in BRUB menu on the recovery mode option, added those parameters (one at a time and then both together) to the end of what looks like the kernel's boot parameters in the line

    linux /boot/vmlinuz-2.6.33-generic root=UUID=ca31cc91-[etc.]0de1555 ro single nomodeset
so it reads
    linux /boot/vmlinuz-2.6.33-generic root=UUID=ca31cc91-[etc.]0de1555 ro single nomodeset ACPI=off xforcevesa

after typing the change i press ctrl-X to boot, as indicated in the help message under the editor.

If i have tried your parameters correctly then they do not seem to help -- i get a blank screen (no blinking cursor) and then after a while (a minute or so?) a reboot.

---

### Post by bronzenose on 2012-01-22
I am beginning to suspect that the problem is the combination of my nVidia nForce 680i motherboard and a 2TB hard drive. Vista crashed 54% through formatting the 2TB until i installed new drivers.

Can someone tell me how to install fresh with the right SATA drivers? nVidia's site offers little more than a file to download and i think i need to know how to get that into my installation media and have it installed.

---

### Post by bogan on 2012-01-22
Hi!, **bronzenose**,

Please confirm you are not using two nvidia 8800 cards as SLI, if you are take one out and try again. You may need to take one out to install the driver, in any case.

First:
You Posted the Grubmenu line you were editing:> linux /boot/vmlinuz-2.6.33-generic root=UUID=ca31cc91-[etc.]0de1555 ro [COLOR=Red]single [/COLOR]nomodeset The "single" enforces a recovery boot, and should not be there if this is from the normal boot line.

Second:
Try adding [as you have described]   '--verbose text', which should show how far things get, error messages or/and where it hangs.
 If it ends on "Checking battery state", that probably confirms a video driver problem as most of your other symptoms suggest.
 Ctrl>Alt>F1; F2 & F7 may give you more details.
If all is well it will end in a Text Terminal login, and you can check the graphics with ```
sudo service gdm start
 # or
sudo service lightdm start 
```--- lightdm instead of gdm if using 11.10. 
You can also fix the video driver from there, [ See below ] though there are clearly other problems as well causing a 'Time out'.
**Edit**: If it does not end in a login prompt, Ctrl>Alt.>F2 should give you a tty2 login prompt, even if the system has hung-up.

Third:
You also posted: > nVidia's site offers little more than a file to download and i think i need to know how to get that into my installation media and have it installed. Sorry, that is just not true!

Go to their Download Drivers page and enter GeForce>8 series>Search and it recommends the 290.10 driver - I use it myself and had no trouble learning how to use it - followed by a simple instruction for installing it, plus a Link to a ReadMe file that is most comprehensive.

In addition, if you download the file "NVIDIA-Linux-x86-290.10.run" and decompress it, you will find another ReadMe file that even includes an elementary tutorial on using Ubuntu Terminal Commands as affects installing drivers. [ "x86" if 32bit.]

I am not familiar with the differences between an Alternate and Standard Iso/CD/Usb installation, nor your suspected Motherboard and SATA driver problems: hopefully someone who is will contribute.

Chao!,  **bogan**.

---

### Post by mastablasta on 2012-01-22
additional Sata drivers are not needed in linux.

---

### Post by bronzenose on 2012-01-23
Thank you for your help.  I have tried reinstalling a few more times  (different versions too) and my problem is now different enough that i'm going to close this thread.  nVidia's site is very helpful with the video cards as you say but I was under the apparently mistaken impression that I might need new motherboard drivers for linux (as I had had to do with microsoft windows) and it was the motherboards that seemed not to offer a great deal of help.  Perhaps I am mistaken there too.  Thank you again.

---

