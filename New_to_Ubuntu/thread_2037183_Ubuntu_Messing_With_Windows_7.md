---
title: "Ubuntu Messing With Windows 7"
date: 2012-08-03
forum: New to Ubuntu
---

### Post by Lefaid on 2012-08-03
Hey, this might be more of a Windows 7 problem, but I wanted some opinions from around here before I take my next step in fixing my computer.  

I dual boot Windows 7 and Ubuntu on my laptop, same drive.  I have been having a lot of issues with my Windows Partition on my computer for a while now, especially since March.  I got a blue screen on my Windows 7 partition any time I try to start it.  Since then I have reinstalled Windows and Ubuntu on my computer yet no matter how many times I reinstall Windows, I would get random blue screens in Windows.  It had gotten to the point that it will not start up in Windows after I installed it again about a month ago.  There was nothing special about the last time I got it running.  It was just a "normal" blue screen with a different message and now it will not start again.

I bring this up here because a lot my friends think that my Windows 7 problems are related to me dual booting it with Ubuntu.  Based on my research I do not understand how this could be, considering that blue screens use to come up at random in Windows 7, after it had started up.  I am not expert however.  Is this a reasonable claim or is there something else going on in Windows?

---

### Post by QIII on 2012-08-03
In general, this is unexpected behavior.  Many, many of us dual boot.

But that doesn't mean that nothing is wrong in your particular case.

Can you describe a little more fully what you see?  Is this a real dual boot or WUBI?

---

### Post by robtygart on 2012-08-03
How much space have you allowed for your Windows & Linux partitions..

If you don't know type

```
sudo fdisk -l
```

Post the output please..

Someone I am sure will post here with better info.

---

### Post by Lefaid on 2012-08-03
I think it is a real dual boot, using grub when I press the power button to select Ubuntu or Windows 7.  If I select Ubuntu, it will boot.  Sometimes the Ubuntu logo will come up, other times it will not, but it always gets to the login screen in about 30 seconds or something like that.  I have never timed it.  When I have selected Windows 7 in the last week, it shows the Starting Windows screen then blue screen with a "Cannot find disk image"-esque error.  It use to start no problem and the blue screens messages that would show up at random suggested something to do with the CPU or memory.

Edit:  Found the exact message, UNMOUNTABLE_BOOT_VOLUME

Technical Information:

STOP!  0x000000ED (0xFFFFFA8004, 0xFFFFFFFC0000285, 0x00000000000000, 0x00000000000000)

---

### Post by Lefaid on 2012-08-03
> **robtygart said:**
> How much space have you allowed for your Windows & Linux partitions..

If you don't know type

```
sudo fdisk -l
```

Post the output please..

Someone I am sure will post here with better info.

I do not have the computer with me right now.  I gave Windows 7 about 200 GB and Ubuntu 110 GB with 5 GB of swap space.

Edit: Corrected sizes

---

### Post by QIII on 2012-08-03
Ok.  Without the computer and some specific data, all we can do is speculate.

Will you have access to it soon?

---

### Post by Lefaid on 2012-08-03
> **QIII said:**
> Ok.  Without the computer and some specific data, all we can do is speculate.

Will you have access to it soon?

I might be back with it tomorrow, if not then, then I wlll by Wednesday.  I will revive the thread when I have it again.

---

### Post by Mark Phelps on 2012-08-03
I have multi-boot PCs sharing Ubuntu and Win7 and have no problems -- but I make a point of NOT doing either of the following:
1) Mounting the Win7 partition from inside Ubuntu and writing to it.
2) Using Hibernation with Win7

Either of these can corrupt the Win7 filesystem -- and they can produce the very problems you're experiencing.

---

### Post by Lefaid on 2012-08-08
Mark thanks for the advice there.  I do not think I had hibernated this install of Windows with Ubuntu at any point but I had in past lives of this computer, say 2 or 3 reinstalls ago.  I will keep that in mind.

Someone asked for me to post my space allotted.  Here it is

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00dc0a83

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    15743699     7871818+   7  HPFS/NTFS/exFAT
/dev/sda2   *    15745024   425345023   204800000    7  HPFS/NTFS/exFAT
/dev/sda3       425347070   625141759    99897345    5  Extended
/dev/sda5       425347072   616751103    95702016   83  Linux
/dev/sda6       616753152   625141759     4194304   82  Linux swap / Solaris


``` 

sda2 should be Windows, not sure what sda3 is and sda5 is Ubuntu

I really want to get to the bottum of this so that I understand what I did wrong and to make sure I do not make the same mistakes again, assuming the issue is related to the Dual-boot configuration.

---

### Post by Lingadharini on 2012-08-08
> **Lefaid said:**
> Hey, this might be more of a Windows 7 problem, but I wanted some opinions from around here before I take my next step in fixing my computer.  

I dual boot Windows 7 and Ubuntu on my laptop, same drive.  I have been having a lot of issues with my Windows Partition on my computer for a while now, especially since March.  I got a blue screen on my Windows 7 partition any time I try to start it.  Since then I have reinstalled Windows and Ubuntu on my computer yet no matter how many times I reinstall Windows, I would get random blue screens in Windows.  It had gotten to the point that it will not start up in Windows after I installed it again about a month ago.  There was nothing special about the last time I got it running.  It was just a "normal" blue screen with a different message and now it will not start again.

I bring this up here because a lot my friends think that my Windows 7 problems are related to me dual booting it with Ubuntu.  Based on my research I do not understand how this could be, considering that blue screens use to come up at random in Windows 7, after it had started up.  I am not expert however.  Is this a reasonable claim or is there something else going on in Windows?


Yeah, this is an unexpected behaviour.
If you see blue screen, it means some hardware has got something wrong. I get this often 'coz my video drivers fail whenever I try to open some game which has heavy graphics content. I found that once when I opened that game on my windows, my display froze and it recovered saying,'Intel media accelator failed and recovered successfully'. 
See if you could find anything like this.
Ubuntu doesnt cross with windows with this thing. 
Try updating your drivers in windows, may be that could help.

---

### Post by Mark Phelps on 2012-08-08
> **Lefaid said:**
> ... sda2 should be Windows, not sure what sda3 is and sda5 is Ubuntu 

sda3 is the "container" for sda5 and sda6 -- an extended partition.

I really want to get to the bottum of this so that I understand what I did wrong and to make sure I do not make the same mistakes again, assuming the issue is related to the Dual-boot configuration.[/QUOTE]
IF you want help in troubleshooting blue screens with Windows 7, you would do better going to a Win7 forum.  Suggest sevenforums.com.

---

### Post by robtygart on 2012-08-08
> **Lefaid said:**
> Hey, this might be more of a Windows 7 problem, but I wanted some opinions from around here before I take my next step in fixing my computer.  

I dual boot Windows 7 and Ubuntu on my laptop, same drive.  I have been having a lot of issues with my Windows Partition on my computer for a while now, especially since March.  I got a blue screen on my Windows 7 partition any time I try to start it.  Since then I have reinstalled Windows and Ubuntu on my computer yet no matter how many times I reinstall Windows, I would get random blue screens in Windows.  It had gotten to the point that it will not start up in Windows after I installed it again about a month ago.  There was nothing special about the last time I got it running.  It was just a "normal" blue screen with a different message and now it will not start again.

I bring this up here because a lot my friends think that my Windows 7 problems are related to me dual booting it with Ubuntu.  Based on my research I do not understand how this could be, considering that blue screens use to come up at random in Windows 7, after it had started up.  I am not expert however.  Is this a reasonable claim or is there something else going on in Windows?


Have you changed any bios settings? Are you over clocking or have you changed any memory timings?

---

### Post by houseworkshy on 2012-08-08
It is a true duel boot, so in theory the two system are seperate.  It sounds very like a driver ( borked graphics ) , or boot loader ( UNMOUNTABLE_BOOT_VOLUME ) issue.  Could the bootable flag on the windows booting volume have somehow got unchecked?   A program called gparted could discover that; *without changing anything* look at 'manage flags' then back out again.  If so the puzzle is,  if it couldn't mount the volume how does windows get as far as it does?  If it is the windows swap which won't mount then the problem will be internal to windows, or it's loader.    
I haven't used windows on a machine I administrated since xp and am still on an older version of ubuntu  so don't know enough to advise.  Can mention some bits which may be useful though.
There is a good program for gaining system specs called sysinfo.  If from the Ubuntu side you installed it, in any of the usual ways, you could run it from the link it will put in your system tools menu.  Choose save to file and bung it somewhere.  Posting that or some of whats in it would be the easiest way to answer questions about your hardware.
There is a guide on the bootloader here [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
I think people would like to see a copy of you loader in order to be able to help; the guide explains, better than I could, how to show it to them.
 Only a bump really, hope it helps.

---

