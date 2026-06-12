---
title: "i can not log in to my user"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by HazKO on 2012-01-18
error: unknown filesystem.
grub rescue>
 
what does this mean, i cant start my laptop without seeing this on the screen.. plz help

---

### Post by HazKO on 2012-01-18
error: unknown filesystem.
grub rescue>
 
whats the deal with my laptop????
 
 ive never had any problems with the system its jus recently it started doing this, the screen is all black and this error on the blank black screen..

---

### Post by Lars Noodén on 2012-01-18
Can you use the rescue CD to boot and then mount the hard disk still?

---

### Post by HazKO on 2012-01-18
error: unknown filesystem.
grub rescue>

whats the deal with my laptop????

ive never had any problems with the system its jus recently it started doing this, the screen is all black and this error on the blank black screen..

---

### Post by HazKO on 2012-01-18
yhh i can use the CD, now that you mentioned this, is it possible to insert my ubunto installation cd and format the system same way microsoft formats?

---

### Post by cariboo on 2012-01-18
We are going to need a little more information. Is this a fresh install? What type of install is it, wubi, or to a partition?

---

### Post by QIII on 2012-01-18
As a real quick look (there is a much more detailed script that you might need to run), could you pop the Live CD in, go to the terminal, type

```
sudo fdisk -l
```

(that's an "ell" not a "one") and post the results back here?

This will give us a brief look at the partitions on your drives.

---

### Post by WorMzy on 2012-01-18
Looks like your hard disk, or one of the file systems on your hard disk, has gotten itself into a bit of a state.

First things first, we need to know which of those is the problem, the disk or the filesystem. Filesystems are (usually) easy enough to fix, but if your hard disk is dying, then it's time to buy a new one.

Do you have a Ubuntu LiveCD/USB?

If you do, boot it up and "Try" Ubuntu. That'll get you a graphical desktop which you can then run the disk utility from (normally under System -> Administration -> Disk Utility). From there, click the icon for your hard drive (assuming it shows up!), and then click on SMART data. Check out the list of assessments, and post any that have failed here. (The images on [this]("http://www.rawcomputing.co.uk/linux/linuxtips36.html") webpage should give you a bit more of a visual representation of what I mean, if my directions don't apply to your Live version of Ubuntu, you'll have to find your own way to the disk utility and the SMART data).

If all of the assessments check out ok, then your disk is fine (probably), and your filesystem is the bad cog in the machine. That being the case, open a terminal and post the output of the following command:

```
sudo blkid -c /dev/null
```

---

### Post by lisati on 2012-01-18
*Threads merged and moved to **Absolute Beginner Talk**.* 
Please do not start multiple threads for the same problem, it dilutes the community's ability to help.

---

### Post by HazKO on 2012-01-18
guyz i think there is a problem with the file system, anyways im gonna try to get the cd and just re install.. the lap top is fresh i gt it december times i dont know why bt one of my inlaws decided i should forget about microsoft and try ubuntu.. 
 
thank you very much 4 the replies and i will let you know of the outcome..

---

