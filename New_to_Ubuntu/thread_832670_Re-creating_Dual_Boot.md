---
title: "Re-creating Dual Boot"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by adobrakic on 2008-06-17
Okay, well I'm sick of trying to use Wine to play games, so I wanna re-create dual boot with windows on it. I've found a download of Windows Essential (stripped down version of windows). How would I go about re-creating a dual boot so I can put Windows Essential on my computer, alongside linux?

---

### Post by f37u5g0d on 2008-06-17
I don't know what you mean when you say stripped down version of windows.  I don't really understand how anybody could strip it down.  Does it just not have a lot of free trail software on it or something?

Anyway  I don't think it is possible to install windows on a partition after you have already installed linux on another partition.  Windows will almost certianly recognize the entire harddisk and it certainly won't be content installing in a partition.  I have read countless times on these and other forums that it is just easier to save your files, install windows (it will reformat the whole disk) and then install linux / partition the drive how you want it.

---

### Post by adobrakic on 2008-06-17
It's just windows with barely any any programs on it. But okay, I guess i'll just have to format again. Thanks

---

### Post by kansasnoob on 2008-06-17
Well, I thought essential was purely an office thing, but regardless Win is Win. About 5 months ago I started with these APC guides and everything always worked:

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

Since then I've figured out much better and sometimes much easier ways of doing things reading this guide:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

You certainly can install Win after Linux, I've done it, you just need to do a bit of GRUB rebuilding afterwards, and that's well explained in the APC guides.

---

### Post by adobrakic on 2008-06-17
Was the whole re-installing windows an easy process?
If not, i'll just format.

---

### Post by kansasnoob on 2008-06-17
I just happened to think, one of the biggest problems I had installing win after Ubuntu was that win doesn't see itself as "Drive: C" so you might end up with some win software that doesn't want to install to drive: F, etc.

Still, that can be fixed, not by me, but I paid a friend a modest sum to make some changes to the downloaded software so it would install to the proper "drive".

---

### Post by kansasnoob on 2008-06-17
Following the APC guides it was very easy .............. really, just follow the guide.

---

### Post by adobrakic on 2008-06-17
Alright, i'll try this.
Thanks a lot.

---

### Post by kansasnoob on 2008-06-17
But, it's always easier to install win first!

---

