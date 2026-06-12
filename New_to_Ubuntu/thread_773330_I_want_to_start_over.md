---
title: "I want to start over"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by drrwhistle3 on 2008-04-28
This is what I recieved from previous post

[COLOR="Red"]Quote:Originally Posted by Zaneyard  
You need to boot into the CD
Restart your computer with the disk in. Most likely it will do it automatically, if you see the GRUB screen you are too far. If you do see GRUB, go into your BIOS settings and allow boot from a CD. Or depending on your specific BIOS, hit F12 or something like that (you should see labeled, 'boot selection, or the like' on the screen as soon as you turn on your computer) and select CD Drive from the list.[/COLOR]

Ok I tried this. I first downloaded 8.04 hardy from the Ubuntu site. Extract it in Windows xp with power ISO. Then burn 1 bootable disk in nero and 1 with just the files copied. Brought them both home from work and set my computer's bios to start from CD. The bootable disk started up DOS and stopped there and froze. The non bootable disk just said not recognised. 

Is there a way to format the Ubuntu partition and leave windows xp alone then reinsatll the Ubuntu on the formmatted area? I really have nothing to lose in my Ubuntu side because all important files are on external. If this is possible is there a way to repartition so my Ubuntu side is larger?

Desperatly waiting instructions!!!!

---

### Post by sasquatch74 on 2008-04-28
Hi and welcome to Ubuntu.
The short answer to your question is yes.  There are several options for you.  Some of the best instructions I have seen about getting started in Ubuntu are [here]("http://www.psychocats.net/ubuntu/index").  Hardy Heron is really a great linux distribution for beginners, but there is still a bit of a learning curve for linux in general.  Don't fret, we'll get you there...

---

### Post by Anduu on 2008-04-28
If I understand you correctly you didn't burn the Hardy disk correctly.

There is no need to extract the iso and burn a bootable cd.

All you need to do is burn the iso directly to disk.I makes the cd bootable on its own.

Once you get it up and running it will give you the option to reformat your Ubuntu partition/s and reinstall.

---

### Post by green hornet1 on 2008-04-28
I have ran ubuntu and windows xp dual boot 1 i suggest partition you hard i 2 partition put xp load xp first load ubuntu 2econd when come to the screen that says take over entire hard disk you select partition manually. then you can select set-up petition ubuntu i crest 2 partition 1 large about out double what the size of ram for swap partition. that the way i done mine. i have have reload ubuntu several times xp is till there.

I hope you can make seance of this GOOD LUCK

---

### Post by Jammin80503 on 2008-04-28
I might well be wrong, but I would think you could boot to the existing ubuntu, sudo rm -f it, and install hardy like a brand new install.
(disclaimer - Get more info before doing this, I dont know that it will work)

---

### Post by findspiderweb on 2008-04-28
I think your install disk was incorrectly burned. I burned my iso using InfraRecorder:

[http://infrarecorder.sourceforge.net/]("http://infrarecorder.sourceforge.net/")


To modify your partitions, use GPartEd:

[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

This is a great graphical tool if you want to delete, resize or move partitions. I used it without any problems. (But you should back up data just in case).

---

