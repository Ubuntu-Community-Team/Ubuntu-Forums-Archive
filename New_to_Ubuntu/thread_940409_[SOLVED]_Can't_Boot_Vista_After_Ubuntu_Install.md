---
title: "[SOLVED] Can't Boot Vista After Ubuntu Install"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by WhyCantEveryOSBePerfect on 2008-10-07
HELP!  I cannot boot into windows vista anymore.  I get to the screen where I have a couple options to boot (vista and ubuntu) and ubuntu boots fine.  However, if I select vista the microsoft screen comes up like usual, then instead of starting windows I get a big screen that says GATEWAY on it (my laptop manufacturer) and a system recovery tool opens up.  HELP!

---

### Post by drowner on 2008-10-07
Hi.

You should start by posting the output of
```

sudo fdisk -l

```
and 
```

cat /boot/grub/menu.lst
```

This will tell us what partitions you have and what grub thinks they are.

---

### Post by WhyCantEveryOSBePerfect on 2008-10-07
sudo fdisk -l won't help because I have a raid0 setup
it just returns:  Unable to seek on /dev/sda



## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-21-generic root=/dev/mapper/isw_diihdeefba_RAID06 ro splash vga=795
initrd		/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-21-generic root=/dev/mapper/isw_diihdeefba_RAID06 ro single
initrd		/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=/dev/mapper/isw_diihdeefba_RAID06 ro splash vga=795
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=/dev/mapper/isw_diihdeefba_RAID06 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin


Those are the respective results.  However, when I start my computer it detects Windows Vista as an option.  It starts to load and then brings me to my system recovery options.  I think this means something within vista got screwed up?  Does ubuntu/grub overwrite anything in Vista?

---

### Post by tangibleorange on 2008-10-07
grub shouldn't touch vista but if you resized your vista partition with GParted (in the installer) it might have affected the vista settings. it's possible GRUB is trying to boot to the recovery partition rather than the real Vista partition. unfortunately without some kind of partition list, i can't really say...

---

### Post by ostamp on 2008-10-07
sounds to me like grub is not recognizing the correct startup file for windows and probably installed somewhere strange. here's a thread to reinstall grub > [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351). besides that, i would check the grub menu file with > sudo gedit /boot/grub/menu.lst in terminal and post up what the file has on your windows install. hope this starts to help.

---

### Post by Dark_Stang on 2008-10-07
It sounds like you're booting to the recovery partition on the laptop and not the main OS partition.

---

### Post by kansasnoob on 2008-10-07
That's not a grub problem folks!

That happens when Vista gets corrupted by resizing with anything other than it's own partitioning tools.

This may work:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

If not there are two people that frequent this site that know how to fix it:
meierfra and caljohnsmith. Maybe others but I know they can.

---

### Post by davidryder on 2008-10-07
Add this to your menu.lst file:

```
title Windows Vista (1)
root (hd0,0)
makeactive
chainloader +1
boot

title Windows Vista (2)
root (hd0,1)
makeactive
chainloader +1
boot
```

The first entry will try to boot from the 1st partition of the 1st disk, and the second will try to boot from the 2nd partition of the 1st disk. It's a little trial & error, but logic follows that if Ubuntu is on your 3rd partition, Vista is on the 1st or 2nd. 

Your error is likely being caused by GRUB incorrectly identifying your recovery partition as Vista's partition. Once you identify which of those options boots to Windows you can just delete the other one.

---

### Post by klytu on 2008-10-07
> **WhyCantEveryOSBePerfect said:**
> sudo fdisk -l won't help because I have a raid0 setup
it just returns:  Unable to seek on /dev/sda



## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-21-generic root=/dev/mapper/isw_diihdeefba_RAID06 ro splash vga=795
initrd		/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-21-generic root=/dev/mapper/isw_diihdeefba_RAID06 ro single
initrd		/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=/dev/mapper/isw_diihdeefba_RAID06 ro splash vga=795
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=/dev/mapper/isw_diihdeefba_RAID06 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin


Those are the respective results.  However, when I start my computer it detects Windows Vista as an option.  It starts to load and then brings me to my system recovery options.  I think this means something within vista got screwed up?  Does ubuntu/grub overwrite anything in Vista?

Vista is not listed in your GRUB menu ... When you say "it detects Windows Vista as an option." What does "it" refer to? How are you trying to start Vista if not from the GRUB menu?

---

### Post by WhyCantEveryOSBePerfect on 2008-10-07
Vista was originally resized with its own tools before ubuntu was installed.  It sounds like what you said, that it's booting the wrong partition could be right, I sure hope so.  Here's the data from
sudo fdisk /dev/mapper/isw_diihdeefba_RAID0
                            Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_diihdeefba_RAID0p1               1        1786    14346013+   7  HPFS/NTFS
/dev/mapper/isw_diihdeefba_RAID0p2   *        1787       46031   355391264    7  HPFS/NTFS
/dev/mapper/isw_diihdeefba_RAID0p3   *       46031       46093      504713+  83  Linux
/dev/mapper/isw_diihdeefba_RAID0p4           46094       48641    20466810    5  Extended
/dev/mapper/isw_diihdeefba_RAID0p5           46094       46580     3911796   82  Linux swap / Solaris
/dev/mapper/isw_diihdeefba_RAID0p6           46581       48641    16554951   83  Linux

Command (m for help): 


So I think it does look like the first partition there is my backup partition.  I guess that's what grub is booting into?

When I said "it" in my earlier posts I guess I mean grub.  On the menu where I select which OS to boot looks something like this

Windows Vista
Ubuntu 8.04.1 blah blah blah
Ubuntu 8.04.1 (recovery)
Ubuntu 8.04.1 blah blah blah
Ubuntu 8.04.1 (memtest)
The highlighted option will boot in 15 seconds.

---

### Post by WhyCantEveryOSBePerfect on 2008-10-07
Thanks Guys!  The code listed above to edit the menu.lst worked!!!  Thanks a bunch!

---

### Post by davidryder on 2008-10-07
> **WhyCantEveryOSBePerfect said:**
> Thanks Guys!  The code listed above to edit the menu.lst worked!!!  Thanks a bunch!

Anytime!! :D :guitar: :KS

---

