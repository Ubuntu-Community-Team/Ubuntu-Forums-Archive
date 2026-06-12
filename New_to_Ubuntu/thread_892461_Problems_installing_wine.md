---
title: "Problems installing wine"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by viergeame on 2008-08-17
I just installed Xubuntu 6.06 on a friend's computer and I can't seem to get wine to install.  I downloaded the appropriate .deb package and put it on a usb flash drive to get it on his computer since he doesn't have an internet connection yet.  I got the file to his computer, right clicked it and told it to run with the deb package installer.  The installer window popped up for a second, showed a loading bar then disappeared.  I assumed that it just installed rather quickly, but it doesn't show up anywhere and none of his .exe files will run.  I have installed .deb packages on my own system like this before with no problems, so I'm not sure what I'm missing here.  Also, I'm having a bit of sleep deprivation, so maybe I am forgetting something painfully obvious.  Any help would be greatly appreciated, as my friend may go insane without his games. lol

---

### Post by Paqman on 2008-08-17
If you look at [Wine's entry in the repos](http://packages.ubuntu.com/hardy/wine) you can see that there's a ton of dependencies. If any of these are missing on your friend's machine, it won't install.

Normally the package manager would just download the required dependencies, but without an internet connection it can't do that. You'd need to have all the required packages (and all *their* dependencies)

One way to solve this would be to burn a copy of the [Ubuntu DVD](http://cdimage.ubuntu.com/releases/hardy/release/) and use it as a repo in his machine. The DVD contains the Universe and Multiverse repos, and should satisfy all the dependencies without needing the net.

---

### Post by viergeame on 2008-08-17
Wow, I can't believe I forgot about dependencies... Lack of sleep is really getting to me I guess.

There is a slight problem with that solution, I am doing this installing on a rather old computer that doesn't have a DVD drive.  I chose to install Dapper on it because it is so old.  Actually it barely meets the minimum specs for it.  It's a sad computer, but it was free.

---

### Post by dje on 2008-08-17
have a look [here]("http://ubuntuforums.org/showthread.php?t=887904"), that should be of some help

dje

---

### Post by viergeame on 2008-08-17
Awesome, thanks.  That is now one of my favorite websites.  I'll get that installed and make my friend sane again.  :)

---

### Post by audioAl on 2008-08-17
I too want to install wine, I am new to this O.S. so be patient with me, hope it works out for you, audioAl over and out:guitar:

---

### Post by dje on 2008-08-17
> **audioAl said:**
> I too want to install wine, I am new to this O.S. so be patient with me, hope it works out for you, audioAl over and out:guitar:

sorry if i misunderstand but are you asking for help installing wine?

dje

---

