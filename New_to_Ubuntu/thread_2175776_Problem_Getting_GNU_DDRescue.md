---
title: "Problem Getting GNU DDRescue"
date: 2013-09-20
forum: New to Ubuntu
---

### Post by adam16 on 2013-09-20
I'm trying to recover data from a corrupted hard drive and have run into problem after problem after problem ect.  I've heard gnu ddrescue and testdisk are great programs for this, but I'm not experienced with Ubuntu and I normally only use it to recover data from Windows computers that won't boot into windows.

My problem is, I am running the Ubuntu 12.04.3 LTS live CD, and when I enable the universe and multiverse, the Software Center still cannot find "gnu ddrescue" "ddrescue" or "gddrescue".  So if someone could help walk me through this method it would help.  I have also tried the command "sudo apt-get install gddrescue" in the terminal and it responds with the first 3 lines being successful and the 4th line says "E: Unable to locate package gddrescue".  What am I doing wrong here?

I have also tried booting from Ubuntu Rescue Remix 12.04 Live Cd, but it won't work on my computer for some reason... I verified the MD5 Checksum on the file I downloaded, also verified that the image burnt correctly, and Image Burn said it was correct...  I don't know what I'm doing wrong here either... But when I tried to boot off of this CD, I just got a blank screen, solid black, no cursor, but the LCD screen was on, just black...

If some one could offer me some support on what I'm doing wrong here it would be greatly appreciated... Thanks in advance!!!

---

### Post by slooksterpsv on 2013-09-21
Have you ran the following:

sudo apt-get update

You can also just install TestDisk via sudo apt-get install testdisk

Test Disk will recover the mbr so that it is bootable (by looking at the backup). Is the system connected to the internet?

---

### Post by adam16 on 2013-09-22
I've tried "sudo apt-get install testdisk" and it gave me the same error as it did with the same command for "gddrescue."  I'm about to try sudo apt-get update in just a moment and I will post back my results.

I also wanted to point out that I've gotten the Ubuntu Rescue Remix disc to work on a different computer, but either Ubuntu or that system does not recognize this hard drive.  I have plugged the HDD into many different systems using various operating systems, and the only system/OS combination that will even recognize that the HDD is plugged in is using an Ubuntu 12.04 live cd (NOT the rescue remix version).  So I have to figure out how to do this on the Ubuntu 12.04 live cd...  Also, the only system that will recognize the HDD is a laptop, and the HDD has to be installed internally for the system to even see its there, and not all programs even see it's there (I have to use GParted to scan for the disk to find it's label)...

I'm still about to try "sudo apt-get update" but I really think this error may have something to do with running Ubuntu from a Live CD without having a hard drive to save "test disk" and "gddrescue" to.  That's why I think I get the error "E: Unable to locate package gddrescue."  It seems like it's trying to look for the package on the CD, but I don't know how to get it to look in the universe repositories instead... But I'm about to try "sudo apt-get update".

---

### Post by slooksterpsv on 2013-09-22
The live cd is essentially the same as installing it to the hard drive, the difference is it takes a set amount of memory (usually 512MB) and uses that as a temporary hard disk. The sudo apt-get update should query the packages from the servers to update what's installable. Now if the computer IS NOT connected to the internet, none of this will work. Generally if you just try sudo apt-get install ____ right after booting from the live cd it looks for said package on the live cd not from the internet. You can also look for a deb to download from a site online as well

---

