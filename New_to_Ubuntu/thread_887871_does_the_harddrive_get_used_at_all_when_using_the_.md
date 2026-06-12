---
title: "does the harddrive get used at all when using the live disk?"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by muteXe on 2008-08-12
i would think not, but i want to make sure that even straight after you boot up it doesn't spin the HD.

Thanks,

mute

---

### Post by cmnorton on 2008-08-12
If you are using "spinning" to mean mounted, then I believe you have to request the hard drive be mounted with a live CD, and it probably depends on the distro of the live CD. 

On Knoppix, you not only have to mount the drive, but if you want to delete the files off an old laptop, you have to change the permissions on the drive to write.

I've used the Ubuntu live CD once, and cannot remember if my drives were already mounted or not.

---

### Post by theyranos on 2008-08-12
I haven't used Ubunutu's livecd recently, but most livecds do spin up the drive to read the partition table. It then uses that information to give you the option to read files from your system if you want.

Unless you explicitly tell it to, though, it won't change anything.

---

### Post by snowpine on 2008-08-12
Does the Live CD use an existing Linux swap partition?

---

### Post by Steveway on 2008-08-12
> **snowpine said:**
> Does the Live CD use an existing Linux swap partition?

Yes, it does.

---

### Post by muteXe on 2008-08-12
I am trying to find out what's wrong with my brother's laptop.  Sometimes it switches on, sometimes it doesn't. If it does get to the desktop (it's windows btw), then pressing the start button will make the start menu appear in about 15 minutes (yes, that's minutes).
I put in xubuntu live cd, thinking if it worked it would probably mean the hard drive is buggered as a live cd will use the laptop RAM but not the HD memory.  I just wanted to confirm that really.

I have ran memtest for about 1.5 hours and it kept passing. then insterestingly when i pressed escape to reboot, i got a huge flood of memory errors.

I just dont know what's up it.  Thanks for your answers anyway.  I have had to do a hard reboot on the machine, i'm now going to see what happens if i actually boot off the xubuntu disk now.

Thanks again,

mute

---

### Post by LowSky on 2008-08-12
How old is the computer in Question? If its sorta new and still has a warrenty I would get it looked at.
> **muteXe said:**
>   Sometimes it switches on, sometimes it doesn't.  That sound like a power supply issue, or a bad motherboard

> **muteXe said:**
>  If it does get to the desktop (it's windows btw), then pressing the start button will make the start menu appear in about 15 minutes (yes, that's minutes).
This could be a bad hard drive, motherboard, or processor.

 I would think its a bad power supply or motherboard as it seems that the computer is not supplying enough voltage. the best thing to do is make sure every screw is as tight as it should be. As it could be just something loose causing a short.

---

### Post by muteXe on 2008-08-12
yea, it's bad alright.  just glad it's my brother's :)

However, i've been browsing the internet happily using the live cd.  At first it wouldnt boot his windows partition but i stuck a "-f" at the end of the mount command to force it then it was fine.  I can explore his windows files fine.  So weird.

i cannot unmount it tho.  say's "device busy"...

---

