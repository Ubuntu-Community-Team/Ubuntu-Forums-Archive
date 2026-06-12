---
title: "Installing 8.04 without wiping 7.10"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by metafractal on 2008-04-27
I currently run gutsy on my laptop and it runs well (albeit after a lot of fiddling). I'm keen do a fresh install when I install the new release of Ubuntu, Hardy Herron. However, I don't want to wipe off gutsy until I am sure that I can get everything working in hardy. For this reason I intend to install hardy on a new partition without touching the gutsy partition. (My home folder is on a separate partition to the operating system.) 

My questions are:
(a) Does this sound like a good idea?
(b) Will I be able to wipe the gutsy partition and merge it with my home partition when I am satisfied that I have got hardy working?
(c) I don't want to have to manually install all my packages again. Is there a way to save a list of my installed packages under gutsy and have synaptic install them automatically under hardy? 

Thanks for your help!

---

### Post by kk0sse54 on 2008-04-27
Why don't you just run Hardy off the liveCD for a week or so to see if everything works?

---

### Post by metafractal on 2008-04-27
Because some things (such as wireless modem) took some major fiddling to get working, so I'm not expecting everything to work out of the box, but I'm hoping that everything will work after some playing around. It would be awkward to play around with drivers and things that require restarts whilst running off the live CD, wouldn't it? Correct me if I'm wrong.

---

### Post by obidose on 2008-04-27
> **C!oud said:**
> Why don't you just run Hardy off the liveCD for a week or so to see if everything works?

I'm guessing he wants drivers / extra packages sorted rather than just things on the live cd.

Depending on where you place the new partition (so long as it is next to you current ubuntu partition on the disk) it think it should be doable. Otherwise you can allways still format the old ubuntu partition afterwards and use it as extra storage even if its not combined with 8.04 directory (this way has the added advantage of being able to do the same thing next update without re partitioning)

---

### Post by Oldsoldier2003 on 2008-04-27
> **metafractal said:**
> I currently run gutsy on my laptop and it runs well (albeit after a lot of fiddling). I'm keen do a fresh install when I install the new release of Ubuntu, Hardy Herron. However, I don't want to wipe off gutsy until I am sure that I can get everything working in hardy. For this reason I intend to install hardy on a new partition without touching the gutsy partition. (My home folder is on a separate partition to the operating system.) 

My questions are:
(a) Does this sound like a good idea?
(b) Will I be able to wipe the gutsy partition and merge it with my home partition when I am satisfied that I have got hardy working?
(c) I don't want to have to manually install all my packages again. Is there a way to save a list of my installed packages under gutsy and have synaptic install them automatically under hardy? 

Thanks for your help!
a) yes
b)yes if you are willing to play around with gparted live cd and the partitions are adjacent (otherwise its a lot of delete create and restoring backups)
c)dkpg -l > mypkgs.txt

---

### Post by daberger on 2008-04-27
u should be able to dual boot with wubi.

---

### Post by Paqman on 2008-04-27
> **metafractal said:**
> 
My questions are:
(a) Does this sound like a good idea?

Yep. It's a perfectly reasonable thing to do.
> 
(b) Will I be able to wipe the gutsy partition and merge it with my home partition when I am satisfied that I have got hardy working?

Yes, if you want. Just run Gparted from a LiveCD, delete your Gutsy partition, and expand the other partitions.

Personally i'd keep it though. Having a spare partition can be handy. You could use it to try out other distros, for example. 
> 
(c) I don't want to have to manually install all my packages again. Is there a way to save a list of my installed packages under gutsy and have synaptic install them automatically under hardy? 

[There sure is](http://ubuntuforums.org/showthread.php?t=261366)

Btw, it'd be best to use different user accounts on Gutsy and Hardy. Since they'd be sharing the same /home you might corrupt your user settings if you tried sharing a single user name.

---

### Post by obidose on 2008-04-27
> **daberger said:**
> u should be able to dual boot with wubi.

I thought wubi only worked in windows? Plus he would still have to remove it afterwards to upgrade fully, then have to fiddle with drivers again.

---

### Post by kk0sse54 on 2008-04-27
You should be able to run Hardy off the liveCD without making any changes to your computer so you would be able to change drivers but yes you are right that it would get a little annoying every time you reboot because it pops the CD out again and you have to pop it back in before the computer loads. So if you want to install Hardy under a new partition and then later on delete the gutsy partition you will need to boot up a live CD and use G parted from there to delete that partition and you should be able to resize the hardy partition. Yes there is a way to save all the packages I had a link somewhere here but i can't seem to find it :|

---

### Post by metafractal on 2008-04-27
Thanks for all your exceptionally speedy help! Thanks also for the advice about different user accounts - I hadn't considered that.

---

### Post by kk0sse54 on 2008-04-27
There is a version of wubi for linux called lubi

---

### Post by daberger on 2008-04-30
> **obidose said:**
> I thought wubi only worked in windows? Plus he would still have to remove it afterwards to upgrade fully, then have to fiddle with drivers again.

im not sure. lubi then?

---

