---
title: "How to format laptop hard drive and start over?"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by Buenadriver on 2014-02-24
How can I format my hard drive and start with a fresh install? Currently have 13.10 installed on top of 12.04 and won't let me install any apts. Thanks.
Ok, but how do I do that parted operation. Step by step, please. Thank you.
Is this drive I am on right now labled the C: drive?

---

### Post by david98 on 2014-02-24
Use the live disk you used to install ubuntu go into gparted and format the drive through there

---

### Post by Buenadriver on 2014-02-24
When we do a reply like this, are we supposed to click on quick reply, or just edit the first post?

---

### Post by david98 on 2014-02-24
Quick reply would be sufficient. Did you manage to format the hdd ?

---

### Post by Buenadriver on 2014-02-24
Still waiting for the how to info.

---

### Post by grahammechanical on 2014-02-24
If Ubuntu is to be the only OS on that drive then use the live session to install Ubuntu and when you get to the page that asks what you want the installer to do, then select Erase Entire Disk and Install Ubuntu.

The installer will take care of the paritioning and the formatting of the drive.

Regards.

---

### Post by newb85 on 2014-02-24
"C:" would be a Windows designation, and ambiguously could refer to a drive or just a partition (part of a drive).  Usually, C: is the drive/partition where the Windows OS is installed.  However, if you were examining the drive or partition from Linux, you wouldn't even see the Windows drive letter.

Is this a Wubi install?  (Put a different way, did you install it from within Windows?)

---

### Post by Buenadriver on 2014-02-24
Ok will give that try. Put install dvd in drive it spun for about 20 secs. but nothing else happened. Thanks for the quick reply.

---

### Post by david98 on 2014-02-24
Get a buntu disk ie cd/dvd or usb boot it up into a live session ie try ubuntu without making any changes to your computer. Once into ubuntu go to unity dash search gparted and open it click on your the hard drive delete all partitions by clicking on them then click on partition click delete. Do this to all partitions you will have to click on the green arrow to start the task. once all the partitions have been deleted click back on it then go to partitions click format then decide what you want to format hdd to then click green arrow to apply action's. Alternatively you could just boot up a buntu disk click install then click erase disk and install buntu.

---

### Post by Mark Phelps on 2014-02-24
> Put install dvd in drive it spun for about 20 secs. but nothing else happened. 

That typically happens if you do not have your BIOS set to boot first from your CD/DVD drive.

---

### Post by Buenadriver on 2014-02-24
Re-installed from CD and erased everthing, was online during install, but now I have no internet connection. How can I set this backup? Wireless would be ok. Thanks again. Upper right hand corner shows no network devices available.

---

### Post by vishnuugopi on 2014-02-24
> **david98 said:**
> Use the live disk you used to install ubuntu go into gparted and format the drive through there
as he said that works

---

### Post by oygle on 2014-02-24
I need to format the HDD and install 13.10 also.  :)

From previous installs, it seems GParted doesn't remove the data, is that correct ? I ask this because even with manually creating the partitions, there is still "old data" left there. I want to completely "wipe" everything and start again (after a full backup of course). Last time I did this, there were old configs and settings still left there.

---

### Post by Buenadriver on 2014-02-24
What I did was put in the install CD and when asked what I wanted to do I choose erase everything and install.

---

### Post by oygle on 2014-02-24
Yes, I'm not convinced that it will erase everything, going on what happened last time I did a clean install. I suppose I can always do a few of the command at [http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326) , to make sure it is all completely "wiped".   :)

---

### Post by newb85 on 2014-02-25
Gparted will remove the data if you choose to format the partition. 

That said, I don't think you've answered whether it's a wubi install.   Did you boot from the DVD, or insert it while Windows was running?

---

### Post by nunecas123 on 2014-02-25
1. Get a USB Drive or a blank DVD
2. Install Ubuntu on the USB drive or burn it on the DVD
3. Reboot your computer and choose the drive you wish to boot from (either the USB or DVD)
4. Click on "Try Ubuntu"
5. Get on the Dash and type *gparted*. You will see your HD there, hopefully... Right-click on the partition or drive that you wish to format and point your mouse over* Format* and choose the filesystem (NTFS, FAT32, ext4, etc.).
6. Done! It's formatted. Then, you can fresh install Ubuntu.

There are many ways to do this, even on the Ubuntu Installer. Well, this is one of them.

---

### Post by Buenadriver on 2014-02-25
Hey thanks, I think I have got it solved. Will give that a try. Thanks again.

---

### Post by nunecas123 on 2014-02-27
No problem.

---

