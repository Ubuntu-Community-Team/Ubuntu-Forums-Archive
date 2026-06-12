---
title: "[SOLVED] Install Ubuntu from iPod Classic"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Dahaka14 on 2008-07-07
I have an iPod Classic 80GB, and I am running Vista right now on my laptop.  I was wondering how I could boot from my iPod and install Ubuntu through its USB.  I tried using UnetBootin off the bat, but my laptop freezes when I restart it after changing to boot from USB in the BIOS.  I was wondering if there was a way to clear everything on the iPod (of course not to the point where I can't just reformat it to be an iPod again afterwards)and boot from it.  Thanks.

---

### Post by neurostu on 2008-07-07
Yes you can install ubuntu to your ipod, but it won't work as an ipod anymore.  Boot a liveCD. plug in the ipod, format the ipod with the partition editor under System-->Administration-->Partition Manager. Then run the installer but select the ipod as the destination HDD.

I've never tried it but it should work.... try google i'm sure someone's done it.

---

### Post by falcon61102 on 2008-07-07
Yeah, by formatting the ipod as nerostu suggests you will be able to write to it.  In essence, you will have an 80 gig external HD with a fancy screen after you format it.  Whether it's bootable or not, I have no idea.  To return it to the usual iPod format can be accomplished using iTunes.  Brings up and interesting question as to whether you could use qtparted to resize the iPod partition and add an addition partition to it, therefore allowing to contiue to be an iPod but also act as a normal HD as well.  Anyone?

---

### Post by neurostu on 2008-07-08
I highly doubt that is possible (ok so I'm sure its possible, but certainly difficult)... I think the apple firmware is pretty restrictive... hence you don't have people buying the 30gb ipod and doing a self upgrade to a bigger HDD.  
Also if you could have two partitions on the ipod you certainly wouldn't be able to easily use it as a linux install and a ipod, you'd need to install grub on the mbr and I'm not sure if grub supports booting the apple mbr... 

there are just a lot of issues about trying to dual boot the ipod...

---

### Post by Dahaka14 on 2008-07-08
Ok guys, sorry if you misinterpreted it, but I just meant that I wanted to install the installer to the iPod temporarily so that I could boot it as a live cd, like other people have used their flash drives.  All I need to do is boot it as the live cd, install ubuntu, then reformt it back.  Is this possible?

---

### Post by falcon61102 on 2008-07-09
Your best bet is to either burn the liveCD to a CD or get a flash drive and use that.  iPods were not designed for what you intend to use it for and while it may theoretically be possible with a lot of work, it would be much easier to buy a $20 USB drive than to risk rendering your iPod useless.  IMO.

---

