---
title: "Ubuntu wiped out by chkdsk / winxp"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by wknight022 on 2008-07-26
Heard the computer rebooting the other night, got up to see - and lo and behold, WinXP had updated (a new Maicious Software Removal Tool) and was rebooting. Well, it seems chkdsk had been called in to scan my drive because windows detected an error, and I got there about the time I saw "deleting grub"...
I read lots of the threads on here and tried various methods to re-establish grub, but there was actually only one partition showing using either super grub, or when I tried the re-install via installation CD...so I went back into Windoze and uninstalled WUBI et al. 
Truth is this machine is a little old, and probably is given to disk errors. So when I do rebuild I am going to try partitioning the disk before installation of Ubuntu or windoze.
What file system is recommended with Ubuntu, FAT32 or NTFS?

I love the Ubuntu interface and file update system, so it will definitely be my everyday system, only booting into Windoze when required.

Thanks ahead for any recommendations or suggestions.

---

### Post by SunnyRabbiera on 2008-07-26
Ubuntu can work with ntfs or fat 32.
I am suspecting this issue stems from using wubi, as its not really a proper installer.

---

### Post by wknight022 on 2008-07-26
Yes, that was my feeling also, but at least it got me going in the right direction...over the learning hump a little, so to speak.

I am definitely getting more used to the Linux setup and enjoy the robust performance and relative security compared with Windoze with OFFICE, which to me seems more and more like Swiss cheese. Full of holes.

I am proselytizing my compatriots at work about the benefits of Open Source. So let me just read some, and step back and listen.

Lots of good knowledge on these pages.

---

### Post by SunnyRabbiera on 2008-07-26
Well dont get me wrong, wubi is a good idea though yes it needs work.
Wubi is still experimental but its getting much better.

---

### Post by BGFG on 2008-07-26
Sounds like you're on the right track already, I agree with a dedicated partition... thought i'd throw in my opinion of chkdisk. It actually wrecked my vista installation once and i had just popped in the stupid xp cd as a test to see if vista would allow it to install. I ended up having to run a series of disk repairs to recover quite a few missing media files.

---

### Post by hyper_ch on 2008-07-26
if you reinstall everything or so... you don't need to choose filesystem beforehand... yuo can chose it upon installtion.

WinXP will offer you ntfs and fat32

Ubuntu will offer you a whole lot more - generally stick to ext3 if you have no good reasons to select differently.

But this is done DURING the install process.

---

### Post by caljohnsmith on 2008-07-26
> **wknight022 said:**
> ...I am going to try partitioning the disk before installation of Ubuntu or windoze.
What file system is recommended with Ubuntu, FAT32 or NTFS?

I'm not quite clear on whether you mean what other file systems can Ubuntu work with or what should Ubuntu's file system actually be? For the former case, as was all ready pointed out, Ubuntu doesn't have any problem dealing with FAT or NTFS; for the latter case, Ubuntu typically uses the ext3 file system.

---

### Post by Old_Grey_Wolf on 2008-07-26
> **BGFG said:**
> Sounds like you're on the right track already, I agree with a dedicated partition... thought i'd throw in my opinion of chkdisk. It actually wrecked my vista installation once and i had just popped in the stupid xp cd as a test to see if vista would allow it to install. I ended up having to run a series of disk repairs to recover quite a few missing media files.

I agree he is on track. I use the ext3 format for GNU/Linux.

I am grateful for chkdisk. chkdisk is the reason I'm using GNU/Linux. chkdisk destroyed my XP installation. Since I was reinstalling I thought I may as well try dual booting with this thing called Linux. I couldn't make anything worse. :)

---

### Post by BGFG on 2008-07-27
Thanks for a great laugh Wolf :)
On another note... really looking forward to ext4

---

### Post by SoftwareExplorer on 2008-07-27
I would say use ext3 for Ubuntu and ntfs for windows. Ubuntu supports ntfs just fine. You can't install Ubuntu on a ntfs or fat32 partition without using wubi and therefore windows. I would use the Ubuntu live CD with gparted and ntfs support to set up the partitions first (sudo apt-get install gparted ntfsprogs e2fsprogs), then install windows and then Ubuntu, so that you end up with GRUB. The Ubuntu installer will even auto detect the windows and add it to the GRUB list.

Also, it might be a good idea to get the [Super Grub Disk]("http://supergrubdisk.org") and make a CD of it so you can install grub and get to linux if windows writes over grub. It sure has saved the day a few times for me.

---

