---
title: "How to Extend Windows Partition"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by nolanread on 2012-05-07
Hello all,

When I installed Ubuntu onto my computer, I wanted to dual boot with Windows (which I did).  However I partitioned too much space for Linux and not enough for Windows to meet my needs.  Using GParted I was able to reduce my Linux partition in size, but I can't seem to figure out how to extend the size of my Windows [XP] partition.  I have tried using both GParted in Linux and the Disk Management utility in Windows.  I have been able to make a new, separate Windows partition, but I would rather have it all as one partition.  Right now I have reduced the size of my Linux partition to what I want it to be and have unallocated space on my hard drive that I would like to extend my Windows partition to fill.  How do I go about doing this?  Since I have virtually no files on either Windows or Linux at this point I am not worried about losing any data.

---

### Post by oldfred on 2012-05-07
Welcome to the forums.

It typically becomes like that old slide puzzle where you have to move 3 things to get the one you want in the right place.

Post a screen shot of gparted. You can use the screen shot tool and upload using the paper clip icon on the edit panel above your message.

As long as you have no critical data you can do this. Normally you should backup everything as moving partitions around is higher risk. Any power failure or interruption (of what may be a long process) will damage file structure and force a new install.

I also typically suggest a separate NTFS shared data partition as writing into the Windows system partition from Ubuntu is not recommended. Windows does not like it. 

For my XP I put both my Firefox & Thunderbird profiles in the shared and had the same bookmarks and email in both XP & Ubuntu. My wife also wanted pictures in the shared to use with Picasa. I installed the Windows version of Picasa in Ubuntu and had the same Firefox, Thunderbird, & Picasa apps in each with all data in a common location.

---

### Post by nolanread on 2012-05-09
Silly question, but I'm still a beginner.  How do I take a screenshot in Ubuntu?

---

### Post by jerome1232 on 2012-05-09
> **nolanread said:**
> Silly question, but I'm still a beginner.  How do I take a screenshot in Ubuntu?

press the prtscn button on your keyboard. On US keyboards it's usually to the right of of the function keys. If your on laptop, squint at the keys, it's on there somewhere. You can also open the dash with the "windows" key, and type screenshot, the screenshot utility will pop up.

---

### Post by Shadius on 2012-05-09
> **nolanread said:**
> Silly question, but I'm still a beginner.  How do I take a screenshot in Ubuntu?

Use the **PrtSc** key on your keyboard. You should hear a shutter sound like a camera taking a picture and the screenshot should appear on your desktop.

---

### Post by GuelphNewbie on 2012-05-12
Boot to Windows and install Minitool's Partition Manager ```
 http://www.partitionwizard.com/free-partition-manager.html 
``` which should do the job nicely. As always, back up your system before messing with partitions.

---

