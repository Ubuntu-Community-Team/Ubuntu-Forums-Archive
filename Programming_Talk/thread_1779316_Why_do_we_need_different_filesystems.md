---
title: "Why do we need different filesystems?"
date: 2011-06-10
forum: Programming Talk
---

### Post by lalitpratap on 2011-06-10
Is anybody having idea...
Why we uses different file system for different devices?
Ex. filesytem for CD-Rom, for Hard-Disk, for Network drive etc
 
Since i have seen that there are lot of filesystems available in the market.
 
!! I am not talking about filesystem differing in implementation strategy...since different filesystem implemet uses different strategy of implementation...I am talking about Why do we need different filestsem for different hardware devices.
 
Can we use filesystem written for hard-disk e.g ext2,ext3 for CD-Rom?

---

### Post by simeon87 on 2011-06-10
I'm not aware of a technical reason why, it's just that new file systems are being developed and they gradually replace previous ones. We're mostly stuck with the current file systems due to decisions in the past: everyone has to use the same system otherwise my DVD wouldn't work on your computer, etc.

---

### Post by nvteighen on 2011-06-10
Such a question is like asking why there are several ways to implement any well-known algorithm or concept: because people come up with different solutions for a problem, but with attention placed in different aspects.

Sometimes there might be material restrictions to overcome, sometimes it's just because you implement what you need (using ext4 in a DVD-R would be silly), sometimes it's to optimize disk I/O, sometimes to avoid fragmentations, etc. Different filesystems are created to address different subproblems concerning storing information in a device.

And sometimes, it's because patents can give you money and money moves the world.

---

### Post by slavik on 2011-06-10
> **lalitpratap said:**
> Is anybody having idea...
Why we uses different file system for different devices?
Ex. filesytem for CD-Rom, for Hard-Disk, for Network drive etc
 
Since i have seen that there are lot of filesystems available in the market.
 
!! I am not talking about filesystem differing in implementation strategy...since different filesystem implemet uses different strategy of implementation...I am talking about Why do we need different filestsem for different hardware devices.
 
Can we use filesystem written for hard-disk e.g ext2,ext3 for CD-Rom?
because a cd-rom is a not a hard disk drive, because an sd card which degrades over time is not a tape.

the point is that different file systems are developed for different hardware.

a CD was not really meant to be re-writable, that's why there are no inodes.

Some file systems (reiserfs) deal better with smaller files than other filesystems which deal better with larger files (JSF).

---

