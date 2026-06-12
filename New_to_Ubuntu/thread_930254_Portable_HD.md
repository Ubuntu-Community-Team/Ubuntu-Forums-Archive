---
title: "Portable HD"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by Enigma52809 on 2008-09-25
Hi,
I have a question. I'm sorta new to Linux. I had it for about a month before but I had to change back to Windows. The reason I had to change back was because my 160 GB Seagate External HD was losing its file structure and wasn't able to open any of the files it contained. So with that drive pretty much dead, I now have a new drive, a Simple Tech 250 GB external, and I'm considering switching, or at least temporarily trying (using Wubi to install it on Windows) Ubuntu again. However, I need to make sure that this time the files won't all be erased like last time. 
How can I know for sure that this WILL NOT happen? Thanks in advance for the help.

---

### Post by dhtseany on 2008-09-25
I don't think that Ubuntu was the cause of your previous problems; rather the use of cheap hard drive. 

I think you'll be just fine.

Peace
Sean

---

### Post by luckis on 2008-09-25
Something like that happened to me too, with a seagate external 320GB, as i figured out was the hard drives factory format to fat32 that did the damage, i reformatted the hd when i noticed weird behaviour in 260GB ext3 and about 50GB ntfs and now works great! 
When you format the disk for ubuntu install pay attention to the device it 's going to be installed into. 
So the way to ensure its well being, just re-format it and always unmount before eject.

---

### Post by Enigma52809 on 2008-09-25
Okay, I'll have to do a bit more research to make sure. I was just suspicious because it only started to fall apart right when I switched to Ubuntu. Is this once considered a "cheap hard drive" too?

---

### Post by luckis on 2008-09-25
I don't think that any of the disks are concidered cheap in a low quality way, just small capacity! My external st320 seagate still works awesome after about 3 years of use. 
Enigma if there is a way that Ubuntu caused the problem that would be manual configuration... like bogus /etc/fstab or tune2fs etc. 
Cheers

---

### Post by pi.boy.travis on 2008-09-25
I have always used Seagate external hard drives.  I even have the really old one that looks like a doughnut!

I would recommend against Wubi.  I used it to install Ubuntu on a couple of my friends laptops, and it didn't work after the third boot. . .  You are better off just repartitioning.  Just make sure you backup first!

---

### Post by Tatty on 2008-09-25
I dont see how Ubuntu could have been causing files on your hard disk to disappear or become corrupt.  Its very hard to imagine how a bug that serious would slip through undetected for so long.

Were you unmounting the drive correctly?  If you were then its more likely to just be a coincidence that your HDD was failing at the same time as your first use of ubuntu.

---

### Post by Enigma52809 on 2008-09-25
> **pi.boy.travis said:**
> I have always used Seagate external hard drives.  I even have the really old one that looks like a doughnut!

I would recommend against Wubi.  I used it to install Ubuntu on a couple of my friends laptops, and it didn't work after the third boot. . .  You are better off just repartitioning.  Just make sure you backup first!

I considered that, but I'm kinda uncomftorable partitioning it myself and stuff. I'm pretty computer literate but I'd rather not risk losing everything. This time I'll make sure that I mount the drive correctly (or try to at least) so hopefully I won't have any problems.

---

### Post by Tatty on 2008-09-26
> **Enigma52809 said:**
> I considered that, but I'm kinda uncomftorable partitioning it myself and stuff. I'm pretty computer literate but I'd rather not risk losing everything. This time I'll make sure that I mount the drive correctly (or try to at least) so hopefully I won't have any problems.

Really you should be backing up all your valuable data before installing or upgrading any OS.  These are major things to do to a computer and there is always the chance of things going wrong.

---

### Post by Enigma52809 on 2008-09-26
> **Tatty said:**
> Really you should be backing up all your valuable data before installing or upgrading any OS.  These are major things to do to a computer and there is always the chance of things going wrong.

I do, and when I do this I back it all up on my external hard drive. Which is why the drive crashing has caused me such a problem and why I'm a bit reluctant to try anything again.

---

### Post by pi.boy.travis on 2008-09-26
I think that you will find that Ubuntu is far more stable than Windows.  It also has this community to help you out!  I would encourage you to give it a go.  You can always delete Ubuntu if need be.

I have never had a problem with partitioning when installing Ubuntu, and I have installed it many times on many computers.  I also always make sure that the user's essential data is backed up first.

Have you considered using CDs or DVDs as a backup medium?

---

