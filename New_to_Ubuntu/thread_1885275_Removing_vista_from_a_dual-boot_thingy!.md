---
title: "Removing vista from a dual-boot thingy!"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by ehehlomy on 2011-11-22
So, I just upgraded to 11.10, and I figured it was about time I got rid of Windows Vista, which is doing absolutely nothing but taking up space on my poor laptop. However, I have no idea how to remove it from the Ubuntu end of things! (as that is what I want to keep.)
I googled and such, but the first step involved me getting something I just couldn't seem to find (install gparted from System > Admin > Synaptic
)
Would a kind soul help a near-computer-illiterate person in need of assistance?
Thanks in advance!

---

### Post by pierreyy on 2011-11-22
hey.

the application Gparted can be found in the software center 


ull find a reply that involves a live cd  i strongly recomend that
[https://answers.launchpad.net/ubuntu/+question/7194](https://answers.launchpad.net/ubuntu/+question/7194)

the link for the livecd 

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

good luck!

---

### Post by Miljet on 2011-11-22
If you still have the Live-CD, or Live-USB, that you used to install Ubuntu, it should have gparted on it.  It is better to work from a Live disk when changing partitions anyway.
Be absolutely sure you know which partition contains what before you start. If you have any doubt, run the following code in a terminal ```
sudo fdisk -l
``` That is a small L, not a 1. Post the output here and someone will tell you exactly how to proceed.

---

### Post by LegendaryBibo on 2011-11-22
I would recommend just a wipe. Gparted on the drive now would cause issues.

---

### Post by pierreyy on 2011-11-22
> I would recommend just a wipe. Gparted on the drive now would cause issues.

issues like what?  i think if the user does it properly issues wont arise

---

### Post by lolpenguin on 2011-11-23
> **pierreyy said:**
> issues like what?  i think if the user does it properly issues wont arise

Ummm...not really. Just formatting a partition can sometimes cause it to become corrupted.

---

### Post by Mark Phelps on 2011-11-23
The System --> Admin --> Gparted response was for previous versions of Ubuntu where GParted was installed.  It's not installed by default anymore.

If you just want to remove a partition (one that's not in use) you can do the same using Disk Utility -- which is installed.

Click on the Dash icon on the upper left of the desktop, enter Disk Utility, and launch it.

---

### Post by Ricx94 on 2011-11-23
burn a ubuntu liveCD (just go to ubuntu.com and download the newest version if you don't already have one somewhere).

boot to the cd, and say to run from disc, not install. 
go to the unity launcher (or hit windows key on keyboard), and type "gparted" (no quotes). it will find the program, click on it, and it will open up. heres where some previous knowledge comes in. if you know the size of your vista partition, delete that first. there are some other partitions sitting around, though, some are ubuntu, some are vista. i believe windows likes a partition around 101MB for something, and there may be another one if this is still the original install of vista on the computer, and not a reinstall. that would be the recovery partition for vista. after deleting the right ones (maybe do some research to make sure i am correct which partitions to delete.), then i believe gparted can be used to expand the ubuntu partition to take the whole drive (you'll want to expand the largest ubuntu partition, as this is where everything is stored.).

I would recommend doing a full reinstall instead, though, which would involve putting in the ubuntu disc, getting rid of all partitions with gparted, and installing to take the whole hard drive. do a full backup first of any files you might want to keep. this is a bit safer in my opinion.

whichever you choose, don't forget to apply all changes made with gparted, or they will not be done.

---

### Post by BC59 on 2011-11-23
Well here starts the problem.

When you have deleted the 1 or 2 or 3 NTFS partitions of MS Vista, then the remnants are recognized as unallocated space.

Gparted will help you to expand Linux to occupy that space. Because Windows was installed first (I assume) then it occupies the left part of the drive. Means you have to move your Linux partitions to the left. This is not so easy. Takes time and it's always a risky procedure. Personally I don't recommend it, because there are many possibilities of failure.

---

### Post by roger_1960 on 2011-11-23
Hi

To put it simply:

Back up all your data.

Do a clean install of 11.10 using the whole disk.

Reload your data and reinstall any extra apps you use.

Other methods are more complicated and risky.  Even if you try a different method (deleting MS partitions and moving existing ones), BACKUP anything valuable before you start.

---

### Post by Ricx94 on 2011-11-23
> **roger_1960 said:**
> Even if you try a different method (deleting MS partitions and moving existing ones), BACKUP anything valuable before you start.

I am in complete agreement. whenever doing anything to do with partitions, backup should be step #1...this is VERY IMPORTANT

---

### Post by ehehlomy on 2011-11-24
> **roger_1960 said:**
> Hi

To put it simply:

Back up all your data.

Do a clean install of 11.10 using the whole disk.

Reload your data and reinstall any extra apps you use.

Other methods are more complicated and risky.  Even if you try a different method (deleting MS partitions and moving existing ones), BACKUP anything valuable before you start.

This, for the sake of easiness and simplicity, will probably be what I shall do. I will definitely back up! I don't have much on this old laptop, but it's worth doing. I've learned my lesson with that before, haha...
Thanks to all for your solutions :)

---

### Post by lisati on 2011-11-24
> **domskhel said:**
> This, for the sake of easiness and simplicity, will probably be what I shall do. I will definitely back up! I don't have much on this old laptop, but it's worth doing. I've learned my lesson with that before, haha...
Thanks to all for your solutions :)

Sounds like a plan with potential. Even with the best of care, things *sometimes* (but not always) go wrong, so backups of important data are definitely a good idea. Good luck!

---

