---
title: "xubuntu screen savers"
date: 2015-04-26
forum: New to Ubuntu
---

### Post by Lee_Henderson on 2015-04-26
Hello all, I am using xubuntu 15.0.4. How do you install screen savers?? Everything else running fine, just no screen savers

---

### Post by kerry_s on 2015-04-26
it's the same as 14.04

[http://xubuntu.org/news/screen-locking-in-xubuntu-14-04/](http://xubuntu.org/news/screen-locking-in-xubuntu-14-04/)

basically you install xscreensaver & remove light-locker

---

### Post by Dennis N on 2015-04-26
About xscreensaver:

To have all the screensavers, you need to install these packages:

xscreensaver
xscreensaver-data
xscreensaver-data-extra
xscreensaver-gl
xscreensaver-gl-extra
rss-glx

xscreensaver-data comes with xscreensaver, but the others are installed separately and will provide many additional screensavers. rss-glx requires some extra steps, and contains some of the best screensavers. Read the file /usr/share/doc/rss-glx/README.xscreensaver.

Add **xscreensaver** to the startup applications: command to use is **xscreensaver -no-splash**

note: best to turn off (remove from startup applications) existing screensavers (gnome-screensaver, light-locker, mate-screensaver) if you want to use this.

Setup and choose screensaver to use: **Settings > Screensaver**

---

### Post by Bashing-om on 2015-04-26
Lee_Henderson; Hello;

In addition ^^ :
[http://www.jwz.org/xscreensaver/man1.html](http://www.jwz.org/xscreensaver/man1.html)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Lee_Henderson on 2015-04-27
Thanks for your help, yep I was being daft lol.  Removed Light Locker, installed Xscreensaver, made it a startup item, job done

---

### Post by Bashing-om on 2015-04-27
Lee_Henderson; Great !

Help is what we do :)

If this matter is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]and happy trails to you
[/INDENT][/INDENT]

---

### Post by beblasl on 2016-01-18
Trying out Linux Lite (no relation to Miller Lite) on an old Compaq Evo N 610C ( Ubuntu 14.04.3) Only have a 20 GB HDD and the screws are frozen in the HDD caddie preventing me from adding a larger one, hence the Linux Lite. I'm impressed so far, only one more bug to work out with the wifi. Thanks for your post, I really need my Bouncing Cow!

---

