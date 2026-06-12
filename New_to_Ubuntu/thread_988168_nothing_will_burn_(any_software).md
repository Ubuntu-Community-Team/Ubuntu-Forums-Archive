---
title: "nothing will burn (any software)"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by muted1987 on 2008-11-20
i have this tiny lil problem with my dvd-rw drive and ubuntu and i cant work out whats wrong. 

i have put in a blank dvd rom disc as this is what it shows on the desktop when it comes up but when i try to use nautilus (in-built) cd creator i cant selct my drive or write speed same with brasero says there is no medium there please insert one. gnomebaker does the same thing. 

i did see a post on here about going to system preferences removable drives and ticking a box about burning a disc when inserted but there is nothing in there and i dont know where to start looking for my dvd drive in the filesystem so i cant check it.

if anybody can help would be appreciated.

---

### Post by LowSky on 2008-11-20
does the same thing happen with other mediums, like CD-R's?
Are you sure you can burn a DVD-R, some computers can read DVDs but only burn regular CDs

---

### Post by muted1987 on 2008-11-20
hi thx for replying yes i can burn dvds normally with windows but i cant in ubuntu

not to sure about cd-rs as i have none at hand

---

### Post by LowSky on 2008-11-20
Try running ```
df -h
``` in a terminal and see if you have a least 3GB Avail on / (root)

---

### Post by muted1987 on 2008-11-20
by the looks of things i have 31gig left

---

### Post by SamNSane on 2008-11-20
It will be best, I'm sure, if you can get a "native" burner application to work for you.

However, if you just want something to work for you, you have an alternative that won't cost you much time or effort to try.

If you install wine from the repositories, and then download and install ImgBurn, I suspect that you'll be able to use that drive.

The site is [http://www.imgburn.com/]("http://www.imgburn.com/").

That software, in my experience, is the best all-around burning software written. It's Windows software, but it works perfectly under the new version of wine in Ubuntu 8.04 for me.

I don't know why, but in Ubuntu Hardy and Intrepid none of my three different burners (1 modular bay drive and 2 external USB-connected) would work on either of my Ubuntu systems. But they worked in Windows, and they work with ImgBurn/WINE under Ubuntu.

In the end, I got tired of struggling with gnomebaker, cd creator, serpentine, k3b, and brasero. I just installed a Windows burner and haven't had a failed burn or verification since then. Weird. But true.

PS: Any luck?

---

