---
title: "WMII 3 with Ruby configs"
date: 2006-06-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Gandalf on 2006-06-24
Hi,

WMII ( [Window Manager Improved 2](http://www.wmii.de) )  is a dynamic window manager for X11. It supports classic and dynamic window management with extended keyboard, mouse, and filesystem based remote control. It replaces the workspace paradigm with a new tagging approach. 

Its minimalist philosophy attempts to not exceed 10.000 lines of code (including all shipped utilities and libraries), to enforce simplicity and clarity.

It's very lightweight, easy to use, it's the best choice for those who love simplicity, well-organized highly customizable desktop, it's not the best choice for KDE-like lovers (Sorry but I said KDE coz KDE is very bloated).

Anyway wmii support confguration code can be written in any script language, bash, python, perl and of course the best is Ruby.

Mauricio Fernandez. wrote the whole configuration file in Ruby, which makes it faster and lot easier to maintain, check out [http://eigenclass.org/hiki.rb?scripting+wmii+with+ruby](http://eigenclass.org/hiki.rb?scripting+wmii+with+ruby) for more information.

Dapper does not provide WMII 3 but WMII 2, so you have to install it from edgy, so go to [http://packages.ubuntu.com/edgy/x11/wmii](http://packages.ubuntu.com/edgy/x11/wmii) and download your version and install it
```

wget http://archive.ubuntu.com/ubuntu/pool/universe/w/wmii/wmii_3.1-1_i386.deb
dpkg -i wmii_3.1-1_i386.deb

```
same goes for powerpc and amd64 get the links from [http://archive.ubuntu.com/ubuntu/pool/universe/w/wmii/](http://archive.ubuntu.com/ubuntu/pool/universe/w/wmii/)

Now you need configurations, so either use original code from [http://eigenclass.org/hiki.rb?wmii+ruby](http://eigenclass.org/hiki.rb?wmii+ruby)

or use my modified one
```

apt-get install subversion
cd /tmp
svn export svn://wael.nasreddine.com/wael/trunk/personal/config/home/wael/.wmii-3 wmii-3 --username config
# Password is config too
cp -a wmii-3 ~/.wmii-3

```

you can also get my configs from [http://wael.nasreddine.com/files/config/home/wael/.wmii-3/](http://wael.nasreddine.com/files/config/home/wael/.wmii-3/) (always up-to-date)

Finally here's some screenshots...
- [_Gandalf_](http://bbs.archlinux.org/profile.php?mode=viewprofile&u=5095)
[[IMG]http://Serv1.imagehigh.com/imgs//ih000001/13275_1.th.png[/IMG]](http://Serv1.imagehigh.com/view.php?id=13275_1.png&path=/imgs//ih000001)[[IMG]http://Serv1.imagehigh.com/imgs//ih000001/32495_2.th.png[/IMG]](http://Serv1.imagehigh.com/view.php?id=32495_2.png&path=/imgs//ih000001)
[[IMG]http://Serv3.imagehigh.com/imgs/04/13890_22_06_2006.th.png[/IMG]](http://Serv3.imagehigh.com/view.php?id=13890_22_06_2006.png&path=/imgs/04)[[IMG]http://Serv3.imagehigh.com/imgs/04/4708_22_06_2006_2.th.png[/IMG]](http://Serv3.imagehigh.com/view.php?id=4708_22_06_2006_2.png&path=/imgs/04)
[[IMG]http://Serv1.imagehigh.com/imgs//ih000001/15919_mess.th.png[/IMG]](http://Serv1.imagehigh.com/view.php?id=15919_mess.png&path=/imgs//ih000001)[[IMG]http://Serv1.imagehigh.com/imgs//ih000001/14444_screenshot000.th.png[/IMG]](http://Serv1.imagehigh.com/view.php?id=14444_screenshot000.png&path=/imgs//ih000001)

- [codemac](http://bbs.archlinux.org/profile.php?mode=viewprofile&u=3725)
[[img]http://people.cs.vt.edu/~codemac/shots/screen2006.06.22_00.54t.png[/img]](http://people.cs.vt.edu/~codemac/shots/screen2006.06.22_00.54.png)

---

### Post by Scio on 2006-07-14
I have a problem with dpkg:

dpkg: dependency problems prevent configuration of wmii:
 wmii depends on libc6 (>= 2.4-1); however:

Any ideas how to fix this?

---

### Post by Gandalf on 2006-07-14
Can you try
```

dpkg --ignore-depends=libc6 -i wmii_3.1-1_i386.deb

```

---

### Post by Scio on 2006-07-14
> **Gandalf said:**
> Can you try
```

dpkg --ignore-depends=libc6 -i wmii_3.1-1_i386.deb

```

Now I had it installed, but it won't start and just goes back to login manager. Maybe it just needs libc6 version 2.4 to work.

Edit:
Ok, now it works, I just compiled it from the sources:
[http://www.wmii.de/index.php?page=repos](http://www.wmii.de/index.php?page=repos)

---

### Post by Gandalf on 2006-07-14
> **Scio said:**
> Now I had it installed, but it won't start and just goes back to login manager. Maybe it just needs libc6 version 2.4 to work.

Edit:
Ok, now it works, I just compiled it from the sources:
[http://www.wmii.de/index.php?page=repos](http://www.wmii.de/index.php?page=repos)
Can someone get the package via apt-get source,build the deb file against libc6 >= 2.3.6, and post it please ??? I don't have Ubuntu installed ATM :)

---

### Post by SuperSlickNick2000 on 2006-07-20
I've been wanting to try out wmii myself, but I'm kinda dumb. I downloaded, made, made installed the wmii (I got the sources from the wmii.de site) and then what? In particular where do I find the .xinitrc appropriate file? I tried writing the line "exec wmii" in a bunch of different places and restarting X but nothing seems to work. What should I do?

---

### Post by beppu on 2006-07-24
> **Gandalf said:**
> Can someone get the package via apt-get source,build the deb file against libc6 >= 2.3.6, and post it please ??? I don't have Ubuntu installed ATM :)


[http://beppu.lbox.org/articles/2006/07/23/wmii-3-package-for-ubuntu-dapper](http://beppu.lbox.org/articles/2006/07/23/wmii-3-package-for-ubuntu-dapper) <=- the blog entry detailing the procedure

[http://linuxmovies.lbox.org/wmii_3.1-2_i386.deb](http://linuxmovies.lbox.org/wmii_3.1-2_i386.deb) <=- this is the .deb I built for Dapper


:cool:

---

### Post by pgmario on 2006-09-20
Thanks for the how-to!
I had to build it from source for PPC since the Edgy .deb didn't work (see attachment, use at your own risk, for PPC Dapper).
But wmii is really useful on laptops for advanced users. I won't use it on my desktop machine, but I really like to not having to use the trackpad on my ibook.
One question, though. Did they remove tabbed windows in version 3? alt+u to open a frame and add a client with alt+a doesn't work anymore.

---

### Post by singamayya on 2007-01-24
> **SuperSlickNick2000 said:**
> I've been wanting to try out wmii myself, but I'm kinda dumb. I downloaded, made, made installed the wmii (I got the sources from the wmii.de site) and then what?

Run these commands:

$ cp ~/.xinitrc{,.bak} # make backup if possible
$ echo "exec wmii" > ~/.xinitrc # make new .xinitrc file
$ startx # run wmii

> In particular where do I find the .xinitrc appropriate file?

It should be in your home directory. If it is not there, then just make one.

> I tried writing the line "exec wmii" in a bunch of different places and restarting X but nothing seems to work. What should I do?

See above.

---

### Post by coe on 2007-02-27
I too compiled the latest wmii (3.5.1) from source, put "exec wmii" in ~/.xinitrc, and eigenclass.org's ruby configs in directories ~/.wmii-3 and even ~/.wmii-3.5 (just to make sure that wasn't the problem), but when I re-login or restart X, I get the same gnome window manager as always... and when I try to run wmii myself, I get a message saying that another window manager is already running.... ("oh really?"). What am I missing (besides a brain)?

Also, don't the wmii key bindings wreak havoc with those of other apps, like say emacs? always wondered about that.
thanks for whatever clue you guys may have...
c.

---

### Post by Altarbo on 2007-05-17
EDIT: Nevermind, I get it.

---

