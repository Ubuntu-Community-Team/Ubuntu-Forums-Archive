---
title: "installing tar.gz files in 12.04"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by lenypl on 2012-06-24
i download qbittorrent from software centre. but it has very low downloading speed. i used utorrent in windows7. it have good speed. so i download utorrent for ubuntu from internet. i got a tar.gz file.i extract it and get another folder. now how can i install it

---

### Post by Fernhill Linux Project on 2012-06-24
Have a look at these links for instructions : 

[http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by Paqman on 2012-06-24
Anything coming packed in a .tar.gz archive should be avoided. You're best off getting all your software through the package manager, as it'll be kept updated and is easily removed.

Your choice of torrent client shouldn't affect your download speed. Did you try a couple of different torrents? There are other torrent clients available in the Ubuntu repos, such as Transmission, Bittorrent and Deluge. Try one of them before you go fiddling about with messy tarballs.

---

### Post by gakon77 on 2012-06-24
As is visible in my profile there isn't much I can say about Ubuntu 12. Although, I would recommend first to try using the same ports that utorrent uses in windows, for any bitTorrent client you would like to use in Linux.

I use Transmission myself and before of that Deluge. Both work nicely as far as you use the right ports.

Sorry I can't be more precise, but doesn't your version of Ubuntu come with a BitTorrent client by default? If it does, try to configure it to work and avoid the hassle of installing new application (not to mention compiling from source as you tried with Utorrent).

---

### Post by Cheesemill on 2012-06-24
Also uTorrent for Linux is nothing like uTorrent for Windows.

uTorrent for Linux is a server application that doesn't have a graphical user interface, you use it either by typing in commands or using the Web front-end.

I would recommend using [deluge]("apt://deluge") instead:

---

### Post by Curtis6767 on 2012-06-24
Transmission works well and depending on your Ubuntu release should either be in the Software Center, Synaptic Package Manager, or my already be installed by default.

I've used Transmission many times with no surprises.

No reason to go the tar.gz route.

---

### Post by lenypl on 2012-06-25
thank you friends. my major problem solved. i download deluge. it has a good downloadspeed like utorrent. now i dont need utorrent

---

