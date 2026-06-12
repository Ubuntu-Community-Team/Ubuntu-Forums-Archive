---
title: "Resizing Ubuntu partition again"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by TitanTiger on 2008-05-16
Hey guys, I've been using Ubuntu for about a week now and I'm really enjoying it.  What started as something to tinker with on my Windows laptop (I'm mainly a Mac guy) is becoming the main OS I use on this lappy.

When I started, since I thought since it was just to tinker, I only made the Ubuntu partition 20GB and gave the remainder of the 100GB drive to my Windows partition.  But I'm foreseeing using the Ubuntu side a lot more.

Is there a simple way to resize the partitions again without going through a new install and wiping out all the hard work it took to get everything running right?

---

### Post by issih on 2008-05-16
I'll admit, that I haven't tried this myself, so I'd wait for someone who sounds more certain to chime in if I were you, but here is my understanding of things...

You can't resize a mounted partition..., so your best bet is going to be to boot from a live cd, and repartition things from there.

I know that gparted can non destructively resize ntfs partitions (it can go wrong obviously, and you should backup things you value, but it usually works) as I've done that in order to install ubuntu on machines myself. So once you have a live cd in and gparted running, you ought to be able to shrink the windows drive relatively easily.

I have no idea if you can resize an ext2/ext3 partition so easily, This being linux, I'd guess the answer is yes, but I simply have never tried, you'll have to either poke around in the gparted options to find out, google it or wait for someone with more experience :)

Good luck

P.S. just did a quick search on resizing home partitions, it looks like gparted can do it, so you should just go the live cd route

---

### Post by shifty_powers on 2008-05-16
Thats all true, but BACK UP YOUR DATA ;)

the use of a gparted livecd in this way is at your own risk and is not guaranteed to work, although it should.

don't want to scare you off, just to take some sensible precatuions. This is true WHENEVER you mess around with partitions ;)

---

### Post by Ducatiboy Stu on 2008-05-16
I have the same question..

I would like to be able to re-size my existing NTFS  & linux 

Resize my NTFS smaller, and increase my linux without re installing...

---

### Post by lucasl on 2008-05-16
Personally, I would get systemrescuecd from [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) and boot from it. Then run gparted and it should be easy from there.

You could install gparted on your comp with "sudo apt-get install gparted", but partitions can't be mounted if you want to resize them.

In gparted, just select the windows partition, click resize/move, shrink it, then repeat for the linux partition (but make  it larger).

Hope that helps

Lucas

EDIT: Forgot to mention that systemrescuecd has other amazing features like backup, partition table rebuilding and data recovery.

---

