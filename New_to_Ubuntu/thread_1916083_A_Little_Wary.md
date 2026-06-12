---
title: "A Little Wary"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by dnoonan on 2012-01-27
I have tried dual boot Ubuntu/Windows XP previously twice, on two separate machines...and both times loved it, UNTIL I suddenly couldn't boot into either Windows or Ubuntu...it appears that the small program that lets you make the choice (can you tell I'm a nooby? :-) ) became corrupt. Is this a common problem, and if so, is there anyway to avoid it? I really like running both, actually prefer Ubuntu, but needed to have Windows available.
 
I just bought a Windows 7 machine, and I'm tempted to try again, but I hate to have to re-install everything like I did when it when kafluie last time.
 
All support and hand holding is most appreciated.

---

### Post by cespinal on 2012-01-27
I had experiences with that some years ago. But I have been dual booting for 3 years with no problems... 

I would suggest installing ubuntu from a USB stick rather than a CD first. 

The other option would be running ubuntu on virtualbox...

---

### Post by arochester on 2012-01-27
> the small program that lets you make the choice That's Grub or Grub2.

Nixie Pixel has some videos about fixing this.E.g.  [http://www.youtube.com/watch?v=8lod8sRb_6I](http://www.youtube.com/watch?v=8lod8sRb_6I) [http://www.youtube.com/watch?v=gl8mfpZuDiM](http://www.youtube.com/watch?v=gl8mfpZuDiM)

---

### Post by mastablasta on 2012-01-27
it is not a common problem. if you installed a dual boot via Wubi there was this issue that came ou tduring updates. I believe this was sorted out. 
if you instaleld a propper side by side dual boot then there was no such issue. at least not that i am aware of. and even if Grub (the boot loader) would get corrupted for some reason, the repair is a live disk and an grub update away. (boot from liveCD/USB and update/repair grub).

since you have a new computer, i suggest you use the latest version for better drivers support (if you don't like the interface, then use on o fother Ubuntu flavours - Kubuntu, Xubuntu etc). And don't forget to boot from a live media first and *try it* to make sure that computer's hardware is actually linux compatible (not a windows only maschine).

---

### Post by dnoonan on 2012-01-27
I am impressed.  13 minutes and 3 replies...thanks so much.  I'll be around, I'm sure. (I did remember Grub right after I posted the original...duh!)

---

