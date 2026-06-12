---
title: "deleted data recovery"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by Daydark on 2011-10-20
Hi there, I guess this requires a bit of information, I'm trying to recover some image files from a SD 2 gb card, or from the computer, on the card they were simply deleted manually, and on the computer they were lost when I replaced windows XP with Ubuntu, at the time I thought they were safe in a usb, turns out they weren't.

Right now I'm fumbling around with Scalpel, using [this]("http://www.webupd8.org/2009/03/recover-deleted-files-in-ubuntu-debian.html") guide, problem is it wants a specific directory to search, and since this was back in windows, I have no idea where to tell it to look now. It seems unable to search the SD card, because it always searches from home/ and subdirectories of this.

Anyways, does anyone know of a way to recover images lost in a change of OS? or does anyone know how to recover deleted images from a specific device?

Please help me recover my honeymoon photos, so I wont have to die at the hands of my wife.

---

### Post by kemtnbkr on 2011-10-20
As far as where your pics are on the HD, I have no idea where to point you there.

I have no idea if this would work, but could you potentially mount your sd card under your home directory?  

```
man mount
```

should tell you what you need.

However, I wouldn't try this yet if I were you- ANY DATA written to your SD card could completely destroy your pics if they aren't destroyed already.  I'm 95% a n00b, so I'm not sure what would be safe and what wouldn't, and the situation IMO deserves a lot of care.  

So, someone who knows more than me, would this method be safe?  Also, would it even work at all?

Also, what about dd?  Would that be safe?  He could make an image of the SD card, then scan it with Scalpel I think, due to the low-level copying capacity of dd?

---

### Post by ArgusVision on 2011-10-20
Ouch! Your best bet sounds like the card. Chances are Ubuntu overwrote the ones on the comp. I'm not using the Unity interface, but I'm pretty sure there should be a 'places'
option when you click the 'Ubuntu button' at the top left. From there you should be able to mount the SD card. It will should mount it to /media/UUID#
Where UUID# is an incomprehensible string of numbers and letters that identify the device. You should be able to point scalpel at this directory.

---

### Post by Daydark on 2011-10-21
> **ArgusVision said:**
> Ouch! Your best bet sounds like the card. Chances are Ubuntu overwrote the ones on the comp. I'm not using the Unity interface, but I'm pretty sure there should be a 'places'
option when you click the 'Ubuntu button' at the top left. From there you should be able to mount the SD card. It will should mount it to /media/UUID#
Where UUID# is an incomprehensible string of numbers and letters that identify the device. You should be able to point scalpel at this directory.

Thanks, I recovered them with Photorec from the SD card! [-o<:guitar:

I did it via.[ this guide]("http://blog.mypapit.net/2007/10/how-to-recover-photo-files-from-sd-card-mmc-with-photorec.html") to use photorec.

Anyways, thanks for the answers! I also recovered  118GB images from my labtop hard disc unto my external hard disc, so glad I don't have to look through 20000+ images, since they still were on the sd card :D

This is now SOLVED :)

---

### Post by Mark Phelps on 2011-10-21
Glad to hear it ... so please use the Thread Tools and mark your thread as Solved.  thanks

---

### Post by ArgusVision on 2011-10-21
That's great news! I'm not sure I've heard of photorec, but I'm glad it worked.

---

