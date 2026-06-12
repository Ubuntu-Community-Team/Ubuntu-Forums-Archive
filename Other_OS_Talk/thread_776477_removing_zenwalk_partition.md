---
title: "removing zenwalk partition?"
date: 2008-04-30
forum: Other OS Talk
---

### Post by marquee moon on 2008-04-30
I'd like to remove a partition that currently contains zenwalk. 

Using Gparted, I delete the partition, which gparted states is succesfull. 
When I try to re-format as ext2 (or ext3, I've tried both..) an error occurs and gparted then states that the partition is of unkown format. If I then unmount and re-mount this partition, it returns as a un-deleted partition, with the full zenwalk file structure. 

So...how do I remove it and re-format this part of my disk?

---

### Post by smoker on 2008-04-30
you will have to unmount the partition before you can format it

what version of gparted are you using?

---

### Post by marquee moon on 2008-05-01
I'll try again with un-mounting first. I'm sure I did this the same way that I've previously deleted partitions. Then again, it was late at night....

Not sure which version of Gparted it was: I downloaded it maybe 6 months ago from the 7.04 repositories. 

I'm considering trying the same with Gparted on Puppy. That seems to be able to zap anything.

---

### Post by smoker on 2008-05-01
i've always had trouble with the gparted in the repos (possibly just down to me!), but gparted on puppy has always worked well with me in the past, though now i have the 'gparted live-cd' which is excellent, and handy to have:
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by marquee moon on 2008-05-01
something very strange is now happening...

I unmounted the partition, deleted, then (to check if things were working OK...)reformatted as ext3 and it worked fine, as you suggested. 

I then unmounted this partition, deleted this it & created a logical partition within which I created 3 sub partitions - root, home & swap to install vector linux onto. 

At this point I had the same problem as before: I couldnt create the home ext2 partition. 

After clicking out of the error message, it indicated *my entire hard drive* as unallocated. I went to my 'home' directory in ubuntu & found my documents (still there), backed these up onto USB memory, then booted up Puppy. 

Puppy's Gparted *also* shows my entire hard drive as a great big gray unallocated block. 

So I turned off the computer, turned it back on, rebooted,  grub worked fine, Ubuntu boots up fine, all my files are still here, all my partitions are still intact. 

.....So what on earth is going on?? 

I've got a feeling this is more a gparted thing than a different OS thing

---

### Post by smoker on 2008-05-01
> & created a logical partition within which I created 3 sub partitions - root, home & swap to install vector linux onto

just a suggestion here, but i'm pretty sure a root/boot partition has to be on a 'primary and active' partition. you can have a max of four primary partitions, or three, and a logical partition (and as many sub-partitions as you want within).

just for peace of mind, it might be as well to check the integrity of the hard drive, you can usually download an app for this purpose from the drive manufacturers support page, or one i use quite a lot is 'drive fitness test', info here:
[http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)

---

### Post by marquee moon on 2008-05-02
Well I’m not entirely sure what exactly happened here…..

I downloaded a fresh install of Ubuntu live & ran gparted from within this, and it *also* indicated that my entire disk was unallocated and had no data on it. By now I’d backed up all my files, (except for some copies of old LP’s I’d made), and checked the integrity of these backups on a separate computer. So I started a full install of Ubuntu.

Following the ‘partitioning’ splash-screen, it gave me only the options of “guided- use entire disk” or “manual” (normally, I free up the relevant bit of space, then use the option “guided- use largest available free space”). 

So the installation wiped my whole HDD and built it again from scratch. Now everything works fine, as if there’d never been a problem.  

I then went on to install Vector linux (…the reason why I was trying to get rid of the Zen Linux partition in the first place).  

The Vector Linux install went very smoothly and I must say I *really* like it. Whilst the installation is a little more heavy on configuration than Ubuntu’s “Sit back and watch it install” method, the result is extremely good. Very fast on a recent laptop, so should work well on older hardware.  
The install process would definitely scare a newbie, which is unfortunate, because this OS is ideal for windows users who have old PC’s & want to move away from Win-98 or Win-ME. It comes with a good selection of packages too.

---

### Post by smoker on 2008-05-02
hi, glad you are up and running again.perhaps it was something to do with logical partitions. ubuntu would have installed on a primary, and so would vector.

i may have a look at vector, i have an old p3 550, 128 ram laptop looking for an os!

---

