---
title: "Installation problem"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by Ketman on 2012-02-22
I've just acquired a re-furbished desktop to use purely offline, to run Windows and Dos apps, and maybe some from other platforms, like Linux. It arrived today ready to go with Windows XP Professional. So this afternoon I ran the Ubuntu 10.04 disc (the version I have on my laptop), which told me to re-boot. It booted back up into Windows, so I tried again using the option called something like "help me boot up". That worked okay, after Ubuntu had made the necessary modifications, but then I get this message on an otherwise black screen:

BusyBox v1.13.3 (Ubunu 1:1.13.3 lubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initranfs) Unable to find a medium containing a live file system

(initranfs) 

 There's a cursor there waiting for me to input something, but I don't want to touch it until I have some idea what goes on. Can anyone enlighten me?

---

### Post by roelforg on 2012-02-22
May i ask to what you  want to run on the XP?

It might be a good idea to use wine on ubuntu and just get rid of XP.
Multiboot is a pain; wouldn't advice novice users to try.
If you must, use wubi; it's safe and easy.

I have Ubuntu as only os on my pc, saves you a lot of trouble.

---

### Post by raja.genupula on 2012-02-22
[http://ubuntuforums.org/showthread.php?t=1855361](http://ubuntuforums.org/showthread.php?t=1855361)


use that link , let us know what you got .
all the best .

---

### Post by Ketman on 2012-02-22
> **roelforg said:**
> May i ask to what you  want to run on the XP?

It might be a good idea to use wine on ubuntu and just get rid of XP.
Multiboot is a pain; wouldn't advice novice users to try.
If you must, use wubi; it's safe and easy.

I have Ubuntu as only os on my pc, saves you a lot of trouble.

I need multi-boot. I've tried DosBox, which is just about usable, but  not very good. And I don't fancy Wine much either. I need a clean DOS  partition, and another Windows partition to install Windows 95 from an  old disk I have. And I need Ubuntu. The refurb machine came with a 360  gb hard drive, so I might as well use it.

---

### Post by roelforg on 2012-02-22
> **Ketman said:**
> I need multi-boot. I've tried DosBox, which is just about usable, but  not very good. And I don't fancy Wine much either. I need a clean DOS  partition, and another Windows partition to install Windows 95 from an  old disk I have. And I need Ubuntu. The refurb machine came with a 360  gb hard drive, so I might as well use it.
Use WUBI; the multiboot option gives more problems than it's worth.

---

### Post by raja.genupula on 2012-02-22
> **roelforg said:**
> Use WUBI; the multiboot option gives more problems than it's worth.

Under the idea i have on multi-boot what i can say is ' installing both Ubuntu and Windows on separate partitions is always a best and safe thing  '

---

### Post by roelforg on 2012-02-22
> **raja.genupula said:**
> Under the idea i have on multi-boot what i can say is ' installing both Ubuntu and Windows on separate partitions is always a best and safe thing  '
You're right, though.
I never succeeded with it though, the bootloader kept breaking.

---

### Post by raja.genupula on 2012-02-22
> **roelforg said:**
> You're right, though.
I never succeeded with it though, the bootloader kept breaking.

Yeah my friend! but some times unsolvable issues we will face , but if we look it more deeply we gonna get solutions to it . depending upon how much we work harder , we will get that thing . some times you will get easily , but sometimes a bit tough . but tough one will gives more knowledge than easier one.  

Sorry for my english , I am not expert , even not good in that . 

cheers 

raja

---

### Post by roelforg on 2012-02-22
> **raja.genupula said:**
> Yeah my friend! but some times unsolvable issues we will face , but if we look it more deeply we gonna get solutions to it . depending upon how much we work harder , we will get that thing . some times you will get easily , but sometimes a bit tough . but tough one will gives more knowledge than easier one.  

Sorry for my english , I am not expert , even not good in that . 

cheers 

raja

My solution: ditch windows.

Ubuntu is better anyway.

(That's my opinion)

---

### Post by raja.genupula on 2012-02-22
> **roelforg said:**
> My solution: ditch windows.

Ubuntu is better anyway.

(That's my opinion)

Yes My friend , i got it from your starting post in this thread .Ubuntu is 100% better than Windows . :D:D

@OP , have you tried the link i have given to you . ?

---

### Post by Ketman on 2012-02-22
> **raja.genupula said:**
> Yes My friend , i got it from your starting post in this thread .Ubuntu is 100% better than Windows . :D:D

@OP , have you tried the link i have given to you . ?

Yes I have, but I can't make sense of all that. I think I'll try a reboot and see what happens...

---

### Post by cortman on 2012-02-22
> **roelforg said:**
> Multiboot is a pain; wouldn't advice novice users to try.


*Ahem. I would disagree here- all my Ubuntu installations to date have been dual boot with Windows, and I haven't had a single boot issue with any of them. Installing alongside Windows, in a separate partition, is as easy as rolling off a log.
Grub is a fine system, and I've never had it break on me yet. It's not as ideal as an Ubuntu-only system, I'll agree, but if you MUST have Windows, I have found dual-boot to be fast and reliable.

---

### Post by Ketman on 2012-02-22
Not entirely clear what the problem was, but I think what was happening was that the disk was being ejected prematurely. Ubuntu was trying to install itself without the disk. Anyway it's fixed now. I've got it installed alongside Windows XP, no problem, though just to be on the safe side I gave it the rest of the disk. Which might be a problem tomorrow....

I'm not sure if I should start a new thread about this, but what I want to do next is shrink the Ubuntu partition a bit and install my old Windows 95 disk (if it's still good). I don't think I'll need more than 5Gb. But I don't know how to go about it. I know it will have to format a partition as FAT32, but should I do that through Ubuntu? If so, how would I do it?

---

### Post by larrypg on 2012-02-22
Hello,

I am not sure how you set up your disc partition's which could be a problem if you already have four set.  I think you might have a problem with an install of win95 because it most likely will want to write over the mbr.  You might want to consider installing ubuntu and run win xp and win 95 in a virtual machine such as virtualbox.

---

