---
title: "Can cutting power damage PC"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by janerik on 2008-06-11
Hi, I wanted to save some electric energi, and turned off the power to my Ubuntu PC, ( after shutting it down in normal way).  Now I can not start it again, it seems to be confused about some mounting points.  I run memory check - turned that off after 3 hours, it was still checking memory. 
Any suggestions anyone. Must point out that Ubuntu worked just fine until this.
Regards janerik

---

### Post by decoherence on 2008-06-11
> Now I can not start it again, it seems to be confused about some mounting points

there are different ways it can get confused over mount points. specifically what is it telling you?

If you simply shut it down and didn't make any drastic changes (like a dist-upgrade) and memory checked out then I'd immediately start suspecting the hard drive (and preying it isn't the motherboard)

the actual output may give us a better idea, though.

---

### Post by LowSky on 2008-06-11
So let me get this straight you turn off the computer by clicking on turn off, it then did so, and then you turned off the power from the power supply/outlet?

The only thing this would effect is the CMOS battery, which powers the Memory that hold the BIOS information like boot order and motherboard settings. If that battery cannot hold a charge or dies, it can mess up a computer that boot more than one hard drive and may give them a new order, which could mess up your mount points.

Now if you just pulled the plug or did a hard shutdown (holding the power button until it turns off), then it is a possiblity that the hard drive coiuld have been effected.

---

### Post by ukripper on 2008-06-11
> **janerik said:**
> Hi, I wanted to save some electric energi, and turned off the power to my Ubuntu PC, ( after shutting it down in normal way).  Now I can not start it again, it seems to be confused about some mounting points.  I run memory check - turned that off after 3 hours, it was still checking memory. 
Any suggestions anyone. Must point out that Ubuntu worked just fine until this.
Regards janerik


As ext3 is journaling system an abrupt shutdown of system through power button may lock the mounted partitions. Which means system still thinks these partitions are already mounted and therefore, it fails to mount next you boot your OS.

Can you post the exact error you are getting?

---

### Post by Cypher on 2008-06-11
If you chose the "Shutdown" option, or hit the power button and saw the familiar progress bar going in reverse and the power went off, this is the normal way of turning the PC off.

This should have absolutely no issue with starting the PC up again, the ONLY thing might be that depending on when the last time your partitions were checked, they might have to be checked. But apart from that this shouldn't cause any problems..

---

### Post by tbrminsanity on 2008-06-11
I don't know of any system that if shutdown properly would result in damage to your system.  If anything letting your computer rest when your not around will increase the longevity of your system.

---

### Post by Achetar on 2008-06-11
Another thing to check would be if you resized any partitions, the UUIDs in /etc/fstab would be invalid and need to be changed. The easy way to fix that problem is just to put path the /dev/ file for it in place of UUID=xxxxxxxxxxxxxxxxxxxxxxxxxx

/dev/hda1 is usually the first partition on a non-SCSI HDD
/dev/sda1 is usually the first partition on a SCSI HDD

---

### Post by decoherence on 2008-06-11
> **tbrminsanity said:**
> I don't know of any system that if shutdown properly would result in damage to your system.  If anything letting your computer rest when your not around will increase the longevity of your system.

But what about the thermal expansion/contraction?

*prepares for religious war* :lolflag:

---

### Post by tbrminsanity on 2008-06-11
> **decoherence said:**
> *prepares for religious war* :lolflag:

:roll:

---

### Post by anderskitson on 2008-06-11
I would be more worried about the hard drive spinning up and down if you are turning off an on all the time, I highly doubt expansion/contranction from heat will make a difference from what I have heard anyways. It's better to keep it on if you know your going to be using consistently, but you should turn it off if you are going to be away from it for a while.

---

