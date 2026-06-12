---
title: "Windows (like browser window) is bugged at startup"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by hansnn on 2012-10-31
When i boot Ubuntu 12.04 and try and open a web browser (chromium) it appears very small. like the size of this window i am writing in to make this thread.
But the window is in fact normal size, i just cannot see it.
I can right click anywhere on the screen and get the chromium menu, inspect element etc.

I am using cinnamon, could this be the problem?


Also my boot has become unreasonably slow. The purple screen (after i selected 'boot mode' (recovery, normal, etc.) but before the ubuntu logo with the dots 'loading bar') is what takes too long.

Why could this be happening?
Could it be something with Daemon? I looked at the syslog and it seems to be what takes up most of the boot time.
Here you can see the syslow (scroll down to the bottom and watch timestamps)

[http://pastebin.com/jyv2rvgj](http://pastebin.com/jyv2rvgj)

Thank you

---

### Post by MG&amp;TL on 2012-11-01
Try using Unity (because it's installed by default-feel free to use any other DE) and see if it's the same. It sounds like a window manager issue (and it therefore cinnamon's fault).

If it is fixed in another DE, I think it's bug report time.

---

### Post by hansnn on 2012-11-05
I am now using Gnome Classic, and have not experienced the bugged windows any more.

But the boot is still slow at the purple screen.

---

### Post by hansnn on 2012-11-08
I noticed that one of my partitions was off by 2000kb and figured this was why the boot was slow, so I re installed and made an entirely new partition table.
Now all is working as smooth as it can. (I think)

---

