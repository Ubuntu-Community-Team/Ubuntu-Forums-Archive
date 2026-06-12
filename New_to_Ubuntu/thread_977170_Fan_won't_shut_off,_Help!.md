---
title: "Fan won't shut off, Help!"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Boondock5 on 2008-11-09
Hey guys!

I've got a Dell lattitude (640) and am running 8.04, the fan runs constantly, doing anything music, video, internet anything, even just typing my homework in Open office. What the Hell? Is there some way to shut this fan off without shutting down the computer?

---

### Post by Ng Oon-Ee on 2008-11-10
Have you checked whether your CPU is actually doing anything? If your fan is on that's normally because your temperature warrants it, I wouldn't want to shut the fan down to save on noise only to have the system melt-down an hour later.

Try running gnome-system-monitor from the terminal:-

```
gnome-system-monitor
```

---

### Post by Boondock5 on 2008-11-10
Thanks, I did that and it showed close to 100% CPU usage, WTH? I'm only running 2 pages from the internet running with no video or music or anything. Plus now my interweb pages are showing signs of lag when it refreshes. UGH!

---

### Post by jamesrl on 2008-11-10
From a terminal type 
```
top
```
and it should explain what is consuming your CPU cycles.

In the future it may be helpful to install htop (has color, better interface) by ```
sudo apt-get install htop
```
and then you type htop

---

### Post by Boondock5 on 2008-11-10
Thanks! I did all that it showed a bunch of stuff running, but I don't know what 99% of it is so I ain't touching it. (this computer with all it's little goodies has to make it till May when I graduate)


Thanks again!

---

