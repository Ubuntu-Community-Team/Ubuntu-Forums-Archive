---
title: "Removing windows from a wubi install and/or adding more room to a wubi install"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by HomesteadMommy on 2012-03-05
I've been running linux for a few weeks and just love it.  I'm short on hard drive room and I'm thinking of removing vista from my pc.  When I installed Ubuntu I used the Wubi installer so the searching I've done seems to show I need to compleatly reinstall Ubuntu. [http://askubuntu.com/questions/784/how-to-i-remove-windows-but-keep-ubuntu](http://askubuntu.com/questions/784/how-to-i-remove-windows-but-keep-ubuntu)

That artical only had a few lines on wubi.  But it did say to copy your home folder.  How much of my settings will this save?  Will it keep the software that I've installed?  Does it keep the ppa's that I've set up already?  I'm just wondering how much I'll have to redo. ;) 

One other question, for a short term solution.  When I installed Ubuntu with wubi I went with the 17 gig that it recomended.  I have just over 1 gig of space left in Ubuntu.  How could I take space from the widows side and add it to Ubuntu.  Any info I've been able to find talked about doing this by shrinking partions.  But since I used wubi, it's not in a partion separet from windows right?

Thanks!

---

### Post by seawolf167 on 2012-03-05
You can move your Ubuntu Wubi install to its own dedicated partition following the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=1519354"). Once you have done so, you can simply delete the Windows partition and use a tool like GParted to resize your Ubuntu partition into the newly created free space. 

All your settings/configurations will be saved, though I still highly recommend creating a backup image of your disk just in case something happens. [Clonezilla]("http://clonezilla.org/") is my recommendation for software to accomplish this.

To install gparted:
```
sudo apt-get install gparted
```The WubiGuide is located [here]("https://wiki.ubuntu.com/WubiGuide") for more information.

---

### Post by HomesteadMommy on 2012-03-05
Thanks!  I didn't find that one when I was searching.  I was wondering, if i use gparted to make a new partion can this be done safley when I'm in my main ubuntu system?  From what I can tell Ubuntu doesn't include GParted in it's set up so it would not be on a live cd.  If I boot from a live cd, can you install GParted from the software center on that?  
Sorry, I haven't used the cd start up before for ubuntu.

---

### Post by seawolf167 on 2012-03-05
The [LiveCD should have GParted installed ]("https://help.ubuntu.com/community/LiveCD")- it just isn't included when installed to disk. You can install it with

```
sudo apt-get install gparted
```

---

### Post by HomesteadMommy on 2012-03-05
Ah ok!  Sorry I assumed the setups were the same.

---

### Post by Elfy on 2012-03-05
> if i use gparted to make a new partion can this be done safley when I'm in my main ubuntu systemNot sure you can do this untill your main ubuntu is not wubi.

Until then you are working in a virtual disk.

If you are just looking to increase the space for wubi - [https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F)

---

### Post by HomesteadMommy on 2012-03-05
Thanks everyone!  I've been reading over the info and I think I understand what I'm doing now. lol  I hope to give it a try tomorrow after I've backed everything up. :)

---

### Post by HomesteadMommy on 2012-03-14
Just wanted to update.  Before I could try this vista went belly up on me.  Sooooo I decided to just install everything from scratch.  I now have just Ubuntu on the laptop and it's working great!  Took me a few days to get everything set up the way I like it.

---

### Post by Mark Phelps on 2012-03-15
> Just wanted to update.

I hope you're NOT talking about updating to 12.04.  That only recently entered Beta status and still has issues preventing its more general use.

Also, if you DO want to update to 12.04 down the road, strongly suggest to transition out of your Wubi setup before you do that.

---

### Post by HomesteadMommy on 2012-03-15
> **Mark Phelps said:**
> I hope you're NOT talking about updating to 12.04.  That only recently entered Beta status and still has issues preventing its more general use.

Also, if you DO want to update to 12.04 down the road, strongly suggest to transition out of your Wubi setup before you do that.

Nope I'm using 11.10. :) When I said "I wanted to update" I just wanted to respond to the replies that had been given to me.  I don't like to ask for help then go AWOL.  Eventually I'll be able to try moving a wubi install though.  My dh has it installed on his lap top to.

---

### Post by UnknownFearNG on 2012-03-16
If Vista went belly up (why would it not ;)), why not just install Ubuntu from scratch instead of using Wubi? Wubi is easy to use, but definitely not the preferred way of installation. I wouldn't recommend it to anyone starting anyway, but that's just my opinion.

---

### Post by HomesteadMommy on 2012-03-16
> **UnknownFearNG said:**
> If Vista went belly up (why would it not ;)), why not just install Ubuntu from scratch instead of using Wubi? Wubi is easy to use, but definitely not the preferred way of installation. I wouldn't recommend it to anyone starting anyway, but that's just my opinion.

I had already installed Ubuntu with Wubi about a month ago.  I wanted to move it to it's own partition, so I could get rid of M$ with out having to reinstall everything I had already set up in Ubuntu.
Vista crashed grr lol not a surprise. :rolleyes: I booted from a cd to try Gparted, but it would not let me resize the main hard drive that had both systems on it.  It was giving error messages with the partition.  I couldn't get it to fix it, so I decided to just start fresh. :)

---

### Post by UnknownFearNG on 2012-03-17
> **HomesteadMommy said:**
> It was giving error messages with the partition.  I couldn't get it to fix it, so I decided to just start fresh. :)

Sounds great :)

---

