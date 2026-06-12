---
title: "Copying Windows files from USB hard drive with 8.04.1 Live CD"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by newlxer on 2008-09-03
Sorry if this issue has been previously discussed, but after a search I could not find a prior discussion which fits my exact question regarding the integrity of Windows (NTFS) data which is copied using Ubuntu 8.04.1. 

I am a business consultant with limited computer experience. I have been experimenting with Linux.

Vista (SP1) is installed on my Dell 620 Lattitude laptop (2 GD RAM). (I also have XP and Windows 2000 on other computers which I use in my consulting practice.) However, I cannot copy/backup my extremely important business files (Word, Excel and PowerPoint documents, pdf, tif, etc) from one external Seagate FreeAgent USB hard drive to another (both NTFS) without a number of Windows error messages which tell me that Vista will not copy certain files. This is a common Vista problem for many Vista users. (My data has been created over the past 15 years in Windows 3.1, Windows 95, Windows 98, Windows 2000, Windows XP and Windows Vista.)

To get around this copying problem I have used the Ubuntu 8.04.1 live CD in my laptop. Using the live CD, I can copy file folders from one external HD to the other without a problem. I get no error messages. (The copying is extremely fast, about 1 GB/minute!)

After using Ubuntu to make the copies, I check the file folder properties. I see that the same number of files in the original folder on the source hard drive are now in the copied folder on the second destination hard drive. 

However, I am concerned about the chances that the copied folder on the second hard drive contains files which are corrupted and therefore no longer readable in Vista. My limited understanding is that NTFS is not a native format of Linux. I am therefore concerned that the method which Ubuntu 8.04.1 uses to copy Windows data from one NTFS drive to another is not entirely reliable. (I understand that FAT could be an option on the USB drives but some of my files are Acronis True Image backup files which are quite large.)

I am making the copies in order to backup my very important business data. I therefore hope that I will always be able to use Vista, XP and Windows 2000 (as well as Ubuntu) to access the destination hard drive on which I have placed the copied data.

As a very basic and simple backup strategy, I generally back up my business data via drag-and-drop onto two separate USB hard drives in case of of hard drive failure on one. I just bought two larger external hard drives so I am now moving my data from the two smaller ones to the two larger ones.

Should I be concerned about the integrity and stability of my Windows NTFS data on the destination hard drive due to my use of Ubuntu 8.04.1 to copy the files?  I am copying about 600 GB of data.

Thanks for your help!

---

### Post by Tatty on 2008-09-03
NTFS support for linux has been around for a long time now, and it is very mature.  Mature enough for ubuntu to include it out of the box.

Generally I would tell people not to worry about the possibility of data corruption due to this, as - although i have no evidence to prove this - i would confidently say that the likelihood of corruption is not much greater than it would be in windows.

However, if you are handling extremely sensitive data which simply cannot be lost (which it sounds like you are) then you should of course not be relying on any one backup method, as computers can always go wrong.

It might be worth trying to find out what is causing these error messages on Vista - a system which is doing something you dont understand is not a system you can trust.

Also perhaps a more sturdy backup process might be worth looking into with regular automated backups - as well as you current system of manual backups.

In short, i would not worry about data loss due to linux handling of ntfs, but look for other backup methods to employ also.

---

### Post by brentoboy on 2008-09-03
> **newlxer said:**
> Should I be concerned about the integrity and stability of my Windows NTFS data on the destination hard drive due to my use of Ubuntu 8.04.1 to copy the files?

In my experience, no.  You dont need to be concerned.  NTFS has been quite stable in linux for a few years now.  I use it for serious operations all the time (because vista has that blasted indexing "service" that tries to index everything while you move it from drive to drive.)

Anyway, if you want to fix the "integrity" of the files, boot up into XP, plug in the drive(s) open up my computer, right click one of the drives, click properties, click the tools tab, check the disk for errors, make sure and check both of the check boxes that say "do you want me to actually do anything worth wild?" and let it go for a while.  This should repair any honest to goodness file integrity errors.  It cant fix missing data but it can unwind clobbered files and eliminate some of the error messages you were seeing.

once the ntfs is good and repaired, you can copy it in either windows or linux, linux will probably be faster and equally reliable, even though it isn't native.

---

### Post by wolfen69 on 2008-09-03
i use linux cd's (live) regularly to recover customer's data. it's not linux that will screw up anything, it's your knowledge (or lack of) of computers that will.

---

### Post by Liviu-Theodor on 2008-09-03
My nephew did that (copying data from two destroyed Windows system, one laptop and one desktop) and managed to do all error-free, using an ubuntu 7.10 Live CD, even though he knows nothing about Linux. It just worked for him. Unfortunately, my sister (and his aunt, too), insisted to still use Windows XP after that. Of course, it is her choice, even I do not agree to her. I believe she will be the last in family to use that.

---

