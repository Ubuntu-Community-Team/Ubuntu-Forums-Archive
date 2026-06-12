---
title: "nVidia Graphics Driver - Flickering"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by BarfBag on 2012-06-20
Hello, all.  I'm currently running Xubuntu 12.04, but I have also had this problem in Ubuntu 12.04 and Linux Mint 13.  My screen flickers.  It only flickers when doing things that have to do with graphics, though.  Full screen YouTube, watching full screen DVD's, and even simply grabbing a window and moving it around produces it.  I wish I could provide a screen shot, but it happens so quickly, I am unable.  The problem isn't too serious - it's usually just a line down the center with a half second delay in the second half, and it goes away after a second.  It always comes back, though, and it is extremely annoying.  I'm not sure what other information to provide, so if I am missing anything, please advise me and I will post it.

---

### Post by Autodave on 2012-06-20
> **BarfBag said:**
> Hello, all.  I'm currently running Xubuntu 12.04, but I have also had this problem in Ubuntu 12.04 and Linux Mint 13.  My screen flickers.  It only flickers when doing things that have to do with graphics, though.  Full screen YouTube, watching full screen DVD's, and even simply grabbing a window and moving it around produces it.  I wish I could provide a screen shot, but it happens so quickly, I am unable.  The problem isn't too serious - it's usually just a line down the center with a half second delay in the second half, and it goes away after a second.  It always comes back, though, and it is extremely annoying.  I'm not sure what other information to provide, so if I am missing anything, please advise me and I will post it.

Have you looked for other Nvidia drivers?

---

### Post by Johnny3 on 2012-06-20
[http://www.youtube.com/watch?v=QtPAJ9BR1W8&feature=g-user-u](http://www.youtube.com/watch?v=QtPAJ9BR1W8&feature=g-user-u)

This young man helps me a lot.
Good Luck and God Bless Johnny3 65+++

---

### Post by DingusFett on 2012-06-20
I've got issues with my Nvidia card at the moment, and had the screen flickering. To stop the flickering I opened the NVidia X Server Settings program, at set the refresh rate to 60Hz instead of Auto, which at least stopped the flickering. My problem is that the graphics card isn't reading the EDID from the monitor, so wasn't using the correct refresh rate.

---

### Post by StormForge on 2012-07-19
I had a similar problem and it was cured by disabling the powermizer option in the nvidia settings (set it to "prefer maximum performance").

-Bill

---

