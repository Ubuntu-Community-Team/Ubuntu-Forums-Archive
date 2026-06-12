---
title: "wd external drive issue"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by chastaind3 on 2013-09-15
i have a western digital passport 1TB. i password protected it on my tower which currently runs win7. i'm making the the move to linux so this is all new to me. i will always use windows from time to time but i really need to become fluent in linux. so far learned that setting up the password while in windows installs drivers for that OS. what confuses me is that i have been told and from what i know of linux is that "linux will talk with other OS's but other OS's have trouble talking to linux" this being the case why is linux having trouble useing a driver for a win7 OS to open my external drive so i can enter PW and use this drive? does anyone have a solution for the driver issue or know of a program that will COMPLETELY!! wipe this drive. i have tryed numerous formats with numerous partition managers and wiping software. i have i a feeling its just me being a noob is the issue......PLEASE HELP!!!!!!

---

### Post by 3rdalbum on 2013-09-15
When people say "Linux talks to Windows but Windows doesn't talk to Linux", they are saying that Linux can access NTFS hard disks, but Windows doesn't access any Linux-formatted disks.

Your password-protected hard disk is definitely an exception, because it requires a special filesystem driver. Linux can't use Windows 7 drivers, they are two completely different operating systems. Code that runs on one, can't be understood by the other. It's the same reason why Macintosh programs can't run on Windows, and vice-versa.

I don't know the specifics of your hard disk, but Gparted should be able to format it. There's no encryption scheme for hard disks that is cross-platform unfortunately.

---

### Post by CeejRab on 2013-09-15
Hello [**[COLOR=#000000]chastaind3[/COLOR]**]("http://ubuntuforums.org/member.php?u=1860786"),

I had a similar problem with my western Digital 120GB HD. The preoloaded software for encryption and backup purposes can be a real pain when trying to use the drive between OS's. 

I wiped my drive using a Low Level Format which completely overwrites the data. When you delete a file, it just tells the drive that that information can be written over. All computing data is written in 0's and 1's, so your files need to be written over with several layers of 01010101101001010101 type information in order for it to be truly deleted and non recoverable. This is why we format our drives now and then to get a fresh clean start. 

I recommend this tool:
[http://download.cnet.com/HDD-Low-Level-Format-Tool/3000-2094_4-75544788.html](http://download.cnet.com/HDD-Low-Level-Format-Tool/3000-2094_4-75544788.html)

You must run this program from a windows machine to format the external drive. Then you can open GParted or another program and give it a quick format of the filesystem you prefer. I Recommend FAT-32 for external drives that are being used cross-platform because it is recognized by all operating systems. As long as you dont deal with files larger than 4 GB, you will be fine. A single file larger than 4GB is not supported on FAT-32 filesystems. If this is a problem for you and you need to be able to have a single file larger than 4GB, perhaps ex-FAT would be best for you. 

Hope this helps! All the Best,

-Christian

---

