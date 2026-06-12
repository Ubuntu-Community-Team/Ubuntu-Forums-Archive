---
title: "It's official!!"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by at2smithjason on 2008-07-26
Well it's official, I have started to use Ubuntu and I am a convert.  I like it alot.  and I want to make the full switch.  But when i tried to do the install and use the full disc drive it said that I couldn't because of a partition that needs to get closed.  Can I get an assist here so that I can get Linux fully installed on my computer.  Thanks guys!

---

### Post by billgoldberg on 2008-07-26
> **at2smithjason said:**
> Well it's official, I have started to use Ubuntu and I am a convert.  I like it alot.  and I want to make the full switch.  But when i tried to do the install and use the full disc drive it said that I couldn't because of a partition that needs to get closed.  Can I get an assist here so that I can get Linux fully installed on my computer.  Thanks guys!

If you are running windows. Make sure you shut it down properly.

---

### Post by at2smithjason on 2008-07-26
> **billgoldberg said:**
> If you are running windows. Make sure you shut it down properly.

i am using the live session right now.  Is that whats causing me to not be able to get the full install?

---

### Post by damis648 on 2008-07-26
No. Boot up Windows, then make sure you properly shut it down. That should fix it.

---

### Post by foxmulder881 on 2008-07-26
> **at2smithjason said:**
> i am using the live session right now.  Is that whats causing me to not be able to get the full install?

If you're running in Live CD mode, just click on the **Install** icon on desktop. The installed should guide you through the rest of it.

---

### Post by aktiwers on 2008-07-26
As Damis said, if Windows was not shutdown correctly it leaves the disc "still being used". Therefore the LiveCD cant format it.

So you need to boot up into Windows one last time and shut it down correctly.

Welcome to Ubuntu and the forums! Make sure to ask here if you need more help :)

---

### Post by RiceMonster on 2008-07-26
Welcome to the wonderful world of Linux, I hope everything goes smoothly for you once you get it installed :).

---

### Post by Paqman on 2008-07-26
> **damis648 said:**
> No. Boot up Windows, then make sure you properly shut it down. That should fix it.

The reason you might need to do this is that if an NTFS partition isn't shut down properly it gets flagged as being a bit dodgy, btw.

As damis and billgoldberg suggest, a quick boot up and shut down of Windows should clear the flag and allow you to proceed. Once you no longer have the NTFS partition you won't run into this problem again.

---

### Post by at2smithjason on 2008-07-26
Well, I have Ubuntu installed 100% and I am using it right now.  I am liking it alot and I am glad that i made the switch.  Thanks for all of your help and support.  I will be sure to come back here if I need help and I wil send everyone here that is thinking of making the switch from windows to Linux. Thanks again guys/gals!

---

### Post by foxmulder881 on 2008-07-29
Good to see you got it installed ok. Cheers mate.

---

### Post by steveneddy on 2008-07-29
Welcome to Ubuntu.

---

### Post by at2smithjason on 2008-07-30
I like using Linux, but I am thinking abot going back to windows just for gaming.  I want to do a dual boot, how would I switch between Windows and Linux?  Will it ask me what I want to start up in like when I used the CD for the Live session before I installed Ubuntu?

---

### Post by sharks on 2008-07-30
yes it will show up a menu for booting windows or ubuntu.
screenshot:[http://images.howtoforge.com/images/unetbootin_windows_linux/big/38.png](http://images.howtoforge.com/images/unetbootin_windows_linux/big/38.png)

Now install Window$ and now u will not be able to see ubuntu.
put the live cd and boot it and restore GRUB.

For restoring GRUB:
[www.sorgonet.com/linux/grubrestore/](www.sorgonet.com/linux/grubrestore/)
[www.ubuntuforums.org/showthread.php?t=224351](www.ubuntuforums.org/showthread.php?t=224351)
[www.linuxquestions.org/questions/general-10/how-to-restore-grub-after-win-xp-install-446952/](www.linuxquestions.org/questions/general-10/how-to-restore-grub-after-win-xp-install-446952/)

---

### Post by JoneYee on 2008-07-30
One thing that hasn't been mentioned.  In my opinion it is beneficial to install Ubuntu to the entire disk instead of a smaller partition on the disk.  To that end, make sure you backup whatever you deem important prior to proceeding with an install (as you should do before any major upgrade or migration)

---

### Post by Vorian Grey on 2008-07-30
Dual boot is easy. Install Windows first, then Ubuntu. Ubuntu will set up Grub, a boot manager for you and it will include Windows as an option for you. Personally, when I set up a computer to dual boot I partition the disks before I install any OS.

---

### Post by linux6994 on 2008-07-30
Welcome to Ubuntu!

Ubuntu offers many things stability, customization, and incredible support in this forum. You can not beat the price. Being a recent convert from the MS world you might feel the need for a Windoze fix every now and then, this will subside as time goes by. One of the many wonderful features of Linux is that you can run Windoze virtually to satisfy that ancient need. XP or any other OS can be run virtually via virtualbox or wmware. 

Just query the forum or the net for help. I have attached what it will look like.

---

### Post by markjensen on 2008-07-30
> **linux6994 said:**
> ... 
One of the many wonderful features of Linux is that you can run Windoze virtually to satisfy that ancient need. XP or any other OS can be run virtually via virtualbox or wmware.
Hardly a valid solution for the thread starter who was wanting to keep Windows as a dual-boot for gaming.    You can't game in a VM Windows install. ;)

---

### Post by linux6994 on 2008-07-30
You are correct. Not enough coffee this morning.

---

### Post by markjensen on 2008-07-30
> **linux6994 said:**
> You are correct. Not enough coffee this morning.Off-topic, but have actually been successful at an XP install in Virtualbox?   I only tried it once, some time ago, and it had some error that stopped me.   I didn't search for a solution, since I was just trying it for kicks.   But if you just popped in an XP CD and Virtualbox had no hiccups, I would be interested in the improvement in status since my attempt.

---

