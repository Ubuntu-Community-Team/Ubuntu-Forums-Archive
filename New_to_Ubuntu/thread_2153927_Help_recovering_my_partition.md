---
title: "Help recovering my partition"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by FloydianX on 2013-06-12
Hello, I'm in a bit of a crisis I'm afraid.

A few days ago I decided to try Ubuntu again after a few years of using Windows 7. So I installed Ubuntu 12.04 on a separate partition. A few minutes ago I decided to try a different distro to see what it was like, so I decided to try installing Linux Mint. 

Now unfortunately, the Linux Mint installer crashed during installation, more precisely, it crashed on the part where it was partitioning. Now when I start up my computer I can't load anything, neither Windows 7 or Ubuntu. All that happens is I'm brought to a command line type screen called Grub Rescue. 

Now I'm feeling a bit panicky. I'm currently using the Ubuntu CD. 

Would someone be able to walk me through how to recover the partitions without losing windows 7? I'm hoping it's possible. For me my main priority is the windows partition, the ubuntu install was only a couple days old so nothing of value wil be lost if it's not recoverable, not so much with the windows side...

Please bear in mind that I'm completely new to linux, so you may have to talk to me like I'm a 4 year old :)

Thanks for your help :)

---

### Post by kindafunnylookin on 2013-06-12
Have you tried shutting down and rebooting? Sometimes grub does not install properly and freezes on loading. A hard shut down and restart will probably do the trick.

---

### Post by FloydianX on 2013-06-12
Yes I've tried that. It just goes to the Grub Rescue command line

---

### Post by FMFCorpsman on 2013-06-12
I am relatively new, but I might be able to point you in the right direction. If you can get on another computer with internet access you can download [Boot-Repair]("https://sourceforge.net/p/boot-repair-cd"). Once thats done you can extract the ISO to a USB using [Unetbootin]("http://unetbootin.sourceforge.net/"). Just boot off of the USB and see if those tools can help with your issue. There might be an easier way I don't know of, but just giving you what I have learned so far.

---

### Post by Bucky Ball on 2013-06-12
Boot Repair. Boot from and install disk, get online with a cable, install Boot Repair, run it, reboot (yes, Boot Repair will install while you are running from disk). You can also run off the details of your grub and setup. If this fix doesn't work, run that option and post a link to the results here.

---

### Post by FMFCorpsman on 2013-06-12
I am relatively new, but I might be able to point you in the right direction. If you can get on another computer with internet access you can download [Boot-Repair]("https://sourceforge.net/p/boot-repair-cd"). Once thats done you can extract the ISO to a USB using [Unetbootin]("http://unetbootin.sourceforge.net/"). Just boot off of the USB and see if those tools can help with your issue. There might be an easier way I don't know of, but just giving you what I have learned so far.


sorry for repeat post

---

### Post by Bucky Ball on 2013-06-12
> **FMFCorpsman said:**
> I am relatively new, but I might be able to point you in the right direction. If you can get on another computer with internet access you can download [Boot-Repair]("https://sourceforge.net/p/boot-repair-cd"). 

As previously mentioned in the post directly before yours; you can install Boot Repair while running from the LiveCD/DVD, you don't need to boot from a disk made on another computer. Just plug an ethernet cable into the one that needs fixing and boot from CD/DVD.  

Please read other posts, not just the first. ;)

---

### Post by FMFCorpsman on 2013-06-13
BuckyBall if you notice my post was before yours. I just mistakenly made a repeat post. Please read other posts, not just the first. :wink: LOL!

---

### Post by Bucky Ball on 2013-06-13
> **FMFCorpsman said:**
> BuckyBall if you notice my post was before yours. I just mistakenly made a repeat post. Please read other posts, not just the first. :wink: LOL!

Apologies, strange laggy mix up. Carry on ... ;)

PS: I have deleted your duplicate post.

---

### Post by FMFCorpsman on 2013-06-13
> **Bucky Ball said:**
> Apologies, strange laggy mix up. Carry on ... ;)

PS: I have deleted your duplicate post.

No Worries Mate! Thanks for handling the second post.

---

### Post by FloydianX on 2013-06-13
Hey guys, thank you all very much for your help!
I used boot repair from the live CD and it seemed to work! :D Panic over

Thanks again guys, you're awesome.

---

