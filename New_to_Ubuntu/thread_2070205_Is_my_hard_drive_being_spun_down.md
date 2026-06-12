---
title: "Is my hard drive being spun down?"
date: 2012-10-12
forum: New to Ubuntu
---

### Post by andperry on 2012-10-12
I've got a computer running Ubuntu Server 12.04. The main Linux system along with all files requiring frequent access are on the original IDE hard drive. I've just added a 320GB Western Digital SATA drive for use as a second disc (the motherboard being sufficiently modern to have built-in SATA ports). The purpose of this is to store files that will not require constant access, so I am interested in being able to spin down the drive on idle in order to save power. There is currently no data on the drive but I have mapped it to a folder in fstab.

I have included the following lines in hdparm.conf in order to spin the disc down after 20 minutes:-

```
command_line {
    hdparm -S 240 /dev/sdb
}

```My main question is how can I prove whether or not the disc is being spun down? Tried doing a directory listing of the disc after it should be idle, wondering if there might be a slight delay, but it was instant. Tried it again with someone listening to the computer to see if spin-up could be heard - heard a slight noise but far from certain - wasn't a distinctive whirring sound. 

Everything may be working fine, but I just need to be able to prove it for certain. Any ideas?

Thanks,

Andrew.

---

### Post by jingaling on 2012-10-12
Hi Andrew,

Once of the guest writers on my blog has literally just had an article published on power management including disks being spun down. He used a utiliy called TLC to achieve this. There is loads of info on their website. Maybe this article will help you:

[http://ow.ly/eq9Pp](http://ow.ly/eq9Pp)

---

### Post by sandyd on 2012-10-12
> **andperry said:**
> I've got a computer running Ubuntu Server 12.04. The main Linux system along with all files requiring frequent access are on the original IDE hard drive. I've just added a 320GB Western Digital SATA drive for use as a second disc (the motherboard being sufficiently modern to have built-in SATA ports). The purpose of this is to store files that will not require constant access, so I am interested in being able to spin down the drive on idle in order to save power. There is currently no data on the drive but I have mapped it to a folder in fstab.

I have included the following lines in hdparm.conf in order to spin the disc down after 20 minutes:-

```
command_line {
    hdparm -S 240 /dev/sdb
}

```My main question is how can I prove whether or not the disc is being spun down? Tried doing a directory listing of the disc after it should be idle, wondering if there might be a slight delay, but it was instant. Tried it again with someone listening to the computer to see if spin-up could be heard - heard a slight noise but far from certain - wasn't a distinctive whirring sound. 

Everything may be working fine, but I just need to be able to prove it for certain. Any ideas?

Thanks,

Andrew.

```

sudo hdparm -C /dev/sdb

```

will show the drive status.

Active drives should show up as active/idle

---

### Post by audiomick on 2012-10-12
> **andperry said:**
> ...Tried it again with someone listening to the computer to see if spin-up could be heard - heard a slight noise but far from certain - 

As far as your problem goes, take the advice of the last couple of posters. 

As far as listening to a specific component goes, you can improvise a stethoscope using a screwdriver or a pen or something. Choose something fairly hard, preferably with one end larger and nicely rounded. Using something that is too big to accidently slip into your ear is good. Place the larger end on the soft spot in front of your ear-hole.

DO NOT STICK ANYTHING IN YOUR EAR. EVER. Not even cotton buds...

Anyway, one end on the spot in front of the ear-hole so that the ear-hole closes, and the other end on what ever it is you want to hear. If that isn't enough, try closing the other ear with your finger as well.

---

