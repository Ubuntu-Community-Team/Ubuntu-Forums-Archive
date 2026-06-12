---
title: "Ubuntu with KDE and KDE4 very slow"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by anewguy on 2008-08-28
I originally installed Ubuntu from the regular LiveCD - gnome, etc..  I later added KDE desktop to try it out, liking that I had the choice to choose what desktop I wanted at loging.  But, I did notice things started to slow down some.  Late last week I added KDE4, and things came to a crawl.  Not just while in either KDE desktop, but also in Gnome.  This week I gave up and removed everything KDE and KDE4.  Now things are a little more back to normal.  SOOOOooooooo.......

Given slow old hardware (PIII-500, 513mb memory, ATI 9250 video card) is the hardware the reason everything slowed down, or is there more going on (perhaps something like layering of desktops if there is such a thing?)?

Thanks in advance! 

Dave :)

---

### Post by Crafty Kisses on 2008-08-28
Post the results of this output > top

---

### Post by nicedude on 2008-08-28
It is more than likely an application behaving badly and the top command mentioned can help you figure out what is using your PC's resources. Only your CPU looks on the weak side to me as your RAM and graphics card look fine. If it continues to be super slow then I would also tell you that with a p3 processor you might get better results with Xubuntu rather than Ubuntu as it uses the XFCE desktop instead of gnome or kde and is really light on resources making it great for older hardware.

---

### Post by tuxxy on 2008-08-28
> **anewguy said:**
> I originally installed Ubuntu from the regular LiveCD - gnome, etc..  I later added KDE desktop to try it out, liking that I had the choice to choose what desktop I wanted at loging.  But, I did notice things started to slow down some.  Late last week I added KDE4, and things came to a crawl.  Not just while in either KDE desktop, but also in Gnome.  This week I gave up and removed everything KDE and KDE4.  Now things are a little more back to normal.  SOOOOooooooo.......

Given slow old hardware (PIII-500, 513mb memory, ATI 9250 video card) is the hardware the reason everything slowed down, or is there more going on (perhaps something like layering of desktops if there is such a thing?)?

Thanks in advance! 

Dave :)

I had exact same issue a while back, I never liked KDE and even one app caused my GNOME serious problems.  

I solved it by removing anything that came up in synaptic when searched for KDE. :lolflag:

---

### Post by Crafty Kisses on 2008-08-28
I want to try KDE 4, my specs are really good, but I guess if I have any problems, I can uninstall it I guess.

---

### Post by anewguy on 2008-08-28
Well, I can't do a top since I already removed everything kde related.  I can tell you I could not for the life of me find the process via top while I had the problem, and that in particular really baffled me.

---

### Post by nicedude on 2008-08-29
top does not need KDE to work or be installed I use it in Gnome. So you should reinstall top or also you could try htop instead as it is a gui type interface, they are both in the repositories. Also you said that your PC is now faster since you have removed KDE but is it the same as it was before or is it still slower than it was before you ever installed KDE ?

---

