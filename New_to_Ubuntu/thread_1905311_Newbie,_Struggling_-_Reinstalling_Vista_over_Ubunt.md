---
title: "Newbie, Struggling - Reinstalling Vista over Ubuntu"
date: 2012-01-06
forum: New to Ubuntu
---

### Post by idde on 2012-01-06
Hello everyone,

I'm sorry if this has been posted before, I've looked around, but none of the other threads on this issue seem to correspond with my specific situation. Although please do point me in the right direction if there's a thread I've overlooked.

About two years ago I installed Ubuntu on a computer (shared between me and a brother) that was originally running Windows Vista. I'm now about to leave for University, and my brother has asked me to return the computer to its original state.

I've done this kind of thing plenty of times before, but I seem to have hit a roadblock this time. I have a Vista installation CD (the computer either didn't come with a recovery CD or has been lost). I partitioned up the disk in Ubuntu using gparted - there's now one big, empty NTFS partition which I was planning to install Vista on.

So... when I use the Vista CD, the Windows installer shows up three partitions:

Disk 0 Partition 1 Primary
Disk 0 Partition 2 Primary
Disk 0 Partition 3 Logical

Partition 1 is formatted as NTFS. Though when I come to install, I get the dialogue 'Windows is unable to find a system volume that meets its criteria for installation'. This is where I'm stuck.

To make matters worse, when I boot into Ubuntu... well, I can't. I get 'error: unknown filesystem. grub rescue>'. I'm assuming I can just use a Live CD to repartition stuff from 

Some help would be wonderful. I'm leaving for University soon and I've been told to fix this before I leave, on penalty of death. Could do with either a complete installation of Vista on the whole drive or some sort of Dual Boot arrangement. Whichever is easier quite frankly.

---

### Post by freacert on 2012-01-06
hey, shame you cannot convince your brother, but try to make in gparted a primary disk bootable. Flag it as boot. hope this helps you

---

### Post by HeroOfCanton on 2012-01-06
Since you are trying to put Windows back on (booooo ;)) have you tried using the Windows CD to manually delete and recreate all partitions? I would delete all 3, rebuild as one, and start your install from there.

---

### Post by QIII on 2012-01-06
From the Vista install disk, are you offered an option to run fixmbr?

---

### Post by idde on 2012-01-06
Thanks for the quick responses everyone! Yes, it is indeed a shame that he wants Vista back on it, of all things.

@Heroofcanton I've not tried that yet, I'll give it a go. Hang on. 

@fixmbr I'm not sure what fixmbr is, but I don't see any option for it. I can pull up a terminal thing by pressing shift + f10 though, I imagine I can do it from there. What would I have to do with that?

---

### Post by idde on 2012-01-06
> **QIII said:**
> From the Vista install disk, are you offered an option to run fixmbr?
I am not given the option to fixmbr, I've tried it in the console too. Command not recognised.

---

### Post by QIII on 2012-01-06
Can you pop the Live CD in, get to the terminal and post the results of

```
sudo fdisk -l
```

That's an "ell" not a "one".

---

### Post by idde on 2012-01-06
> **QIII said:**
> Can you pop the Live CD in, get to the terminal and post the results of

```
sudo fdisk -l
```

That's an "ell" not a "one".
Right, here goes.

Disk /dev/sda: 1000.2 GB, 1000204886106 bytes
255 heads, 63 sectors/track, 121601 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes

device boot          start          end           blocks     id     system
/dev/sda1                1        96629       776168448    6         FAT16
/dev/sda2 *          96629        120485     191621120     83        linux
/dev/sda3            120485       121602     8970241       5      extended
/dev/sda5            120485       121602     8970240       82    linuxswap

disk /dev/sdc: 3965 mb
49 heads, 48 sectors/track, 3292 cylinders
units = cylinders of 2352 * 512 = 1204224 bytes
disk identifier: 0x00000000

device boot          start          end           blocks     id     system
/dev/sdc1             4              3293       3868160      b   w95 fat32

---

### Post by mastablasta on 2012-01-06
> **idde said:**
> I am not given the option to fixmbr, I've tried it in the console too. Command not recognised.

fixmbr is a windows command run from Windows recovery console to restore master boot record for windows (linux replaced it with GRUB). fixmrb command did the job in winXP i am not sure about Vista. 

too bad you didn't get him win7 instead. 

anyway as it was advised boot the windows CD, delete all partitions, reformat it and create new ones. that should solve the problem

Or fix the main boot record like this: [http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)
or here: [http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

---

### Post by QIII on 2012-01-06
From the looks of it, /sda is not formatted as NTFS as you think.
 
 I'm with mastablasta.
 
 Use your Windows install disk to reformat the entire drive to NTFS if it will  let you.  If not, try Gparted again, because something did not work.

---

### Post by idde on 2012-01-06
Wahey! That seems to be working. Yeah, I was surprised to see it wasn't formatted as ntfs too, bit odd. Anyway, it's doing its thing, I'll let you all know how it goes.

---

### Post by idde on 2012-01-07
Worked perfectly guys, thanks QIII, heroofcanton and mastablasta for the advice! :)

---

### Post by matza55 on 2012-01-07
I have the same problem. My wifes pc, had Vista installed from factory. No cd come with. Think I used a XP Pro cd to solve the problem. Then I removed XP, then installed Vista again. (puh)
Now she also use Ubuntu, and are happy with 11.10!

---

