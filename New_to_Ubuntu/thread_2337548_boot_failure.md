---
title: "boot failure"
date: 2016-09-19
forum: New to Ubuntu
---

### Post by Timothy_Cota on 2016-09-19
I have used 3 different versions of ubuntu in the last couple of weeks,  14:04.5  16:04, and finally 12:04.5.  In  each case It boots up fine for the first few boots,  then I get this message:


    Gave up waiting for root device.   Common problems:
- boot args (cat/process/command line)
-check rootdelay=( did the system wait long enough?)
-check root= (did the ystem wait for the right device?)
-missing modules (cat/modules /modules; ls/dev)
-Alert! /dev/disc/by-uuid/7654343f-b9D4-466E-9BD2-3D39F4C774A4 does not exist.
    dropping to a shell(ash)
Enter help for a list of built-in commands.
        After I entered help:    
(intramfs) HELP
/bin/sh: HELP: not found                      [ When this occurs I have to do a hard shutdown, then select recovery mode from the boot menu an then I can boot up.]
                unktim
 Toshiba Tecra M10 s1001 
intel duo-core processor 32 bit:
2.53 ghz
RAM: 4g
sshd 250g split   ubuntu 12:04.5/win 7

---

### Post by Bashing-om on 2016-09-19
Timothy_Cota; Yuk !

With 3 failed successful installs of 'buntus, I would question the hardware .
Before reinstalling,- again - I recommend running diagnostics to check your ram (memtest) and hard drive (smartmontools).
See: 
[https://www.smartmontools.org/](https://www.smartmontools.org/)
[http://ubuntuforums.org/showthread.php?t=2192335](http://ubuntuforums.org/showthread.php?t=2192335) <-How to read output of smartctl

Nothing last forever, and hard drives are going to fail.

[INDENT][INDENT]hope for the best
[/INDENT][/INDENT]

---

### Post by oldfred on 2016-09-19
If core2 duo, it is 64 bit and you probably should be using 64 bit Ubuntu. 

Since older full Ubuntu may be slow as Unity needs better graphics. You can install fallback or one of the lighter weight flavors like Xubuntu or Lubuntu.

Do you have a larger hard drive? Do you have AHCI on in BIOS for hard drives? Not RAID nor IDE.
Some with IDE cannot boot beyond 137GB on a drive, so a default install of just / & swap can have boot files after update beyond the 137GB point and cause issues. It that is the case better to use Something Else and use 25GB for / (root) at beginning of drive, 2GB for swap at end of drive and everything in middle for /home or other data partition(s).

---

### Post by Timothy_Cota on 2016-09-19
Bashing -om and old Fred:  thank you for your responses.  Unfortunately I am a newbie so most of it is way over my head.  I did do a memtest before installing 12:04.5 and it passed with no errors.  As far as the hard drive is concerned I replaced the original with a ssd 3 months ago.  All this has become moot  because I have another problem that is apparently insurmountable.   When I installed 12:04 the first thing I did was to set up backups.  I then tried to do a manual backup which was blocked by ubuntu1.  I later learned that ubuntu1 is defunct.  I tried to delete my subscription but was warned that if I did everything I signed into would be orphaned and I could never access them again.  At this point I feel that I should go back to 14:04.5.
                                                                                                  unktim (age 74)

---

### Post by Bashing-om on 2016-09-20
Timothy_Cota; Hey ;

The important thing is that you are up and running .
We learn from our efforts and move on.

This old man has a passion for computers in general and ubuntu in particular .
Many reasons why ubuntu is my operating system of choice.

Mainly:
[INDENT][INDENT]because together we can
[/INDENT][/INDENT]

---

### Post by Timothy_Cota on 2016-09-21
Thanks bashing-om.  I was 68 when I tried linux so you have a leg up on me but I know what you mean.  I think linux is incurable for people with a thirst for learning.  There are brief periods of remission but no lasting cure.   unktim

---

### Post by oldrocker99 on 2016-09-21
> **Timothy_Cota said:**
> Thanks bashing-om.  I was 68 when I tried linux so you have a leg up on me but I know what you mean.  I think linux is incurable for people with a thirst for learning.  There are brief periods of remission but no lasting cure.   unktim

I'm 68, too, my friend. I started with 8.04 lo these many years ago (ZERO malware, BTW). I **still** have a ton to learn, and it's such a pleasure to work with the community. Welcome to the forums, and remember, the only stupid question is one that doesn't get asked.

---

### Post by #&amp;thj^% on 2016-09-21
> **oldrocker99 said:**
> I'm 68, too, my friend. I started with 8.04 lo these many years ago (ZERO malware, BTW). I **still** have a ton to learn, and it's such a pleasure to work with the community. Welcome to the forums, and remember, the only stupid question is one that doesn't get asked.

Ahh come on now you guys are all still young lads...:)
Sorry Off Topic

---

