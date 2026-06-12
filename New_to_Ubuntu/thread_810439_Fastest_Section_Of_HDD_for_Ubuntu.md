---
title: "Fastest Section Of HDD for Ubuntu"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by skymera on 2008-05-28
Hi,

I have a 10,000RPM drive for optimum performance for when using Ubuntu.

What section of the hard drive is fastest to read/write to and also to boot from?

I read the outer tracks of a HDD are th fastest, would this be the best place to put Ubuntu?

Thanks

---

### Post by gali98 on 2008-05-28
The fastest place is the primary partition on the primary drive. (i.e. sda1)
(I don't know physically where that is located, but probably on the outside.)
Kory

---

### Post by skymera on 2008-05-28
Thanks for quick reply.

Currently i have it as the first partition on the inner most track.

I'll re-arrange tonight and hopefully get a small speed boost.

---

### Post by gali98 on 2008-05-28
I hope it helps! I'm not sure how much of a performance boost you will get, but I hope it will help you out.
Kory

---

### Post by skymera on 2008-05-28
How safe is it to resize + move NTFS partitions in an extended partition using gParted?

---

### Post by gali98 on 2008-05-28
ooo.... Not my department I'm afraid. I think it is relatively safe, but I would research it on the gparted site, or wait till someone else answers...
Kory

---

### Post by LeoSolaris on 2008-05-28
I've resized and moved around my NTFS partition several times using gparted. Just make sure you do it with a LiveCD, otherwise all bets are off.

You're speed boost will most likely be very small, but I'll not say that it doesn't exist.

Leo

---

### Post by H.Callahan on 2008-05-28
> **skymera said:**
> How safe is it to resize + move NTFS partitions in an extended partition using gParted?
Should be relatively safe as long as there are absolutely no interruptions like power, or an inadvertent reboot while the process (which can be long) is taking place.

With that said, it is always recommended to backup everything before you start something like that if the slightest possibility of losing data is something that would ruin your day.

---

