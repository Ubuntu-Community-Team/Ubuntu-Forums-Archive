---
title: "GStreamermm"
date: 2009-06-07
forum: Programming Talk
---

### Post by poisonkiller on 2009-06-07
Hello there!
I'm trying to create a program in C++ (running Karmic alpha), which uses GStreamermm to play a music file. So I found an example: [http://svn.gnome.org/viewvc/gnomemm/gstreamermm/trunk/examples/media_player_gtkmm/](http://svn.gnome.org/viewvc/gnomemm/gstreamermm/trunk/examples/media_player_gtkmm/)
When I try to compile it, I get an error, that playbin2.h and ximagesink.h are missing. So I go to /usr/include/gstreamermm-0.10/gstreamermm to look for them, and they aren't there. So, why aren't they there? I have gstreamer base, good, bad and ugly plugins all installed and libgstreamermm-0.10-dev too. Any suggesions what to do?

---

### Post by SledgeHammer_999 on 2009-06-07
I think you need **libgstreamermm-plugins-base0.10-dev**
And I hope you are using pkg-config to output the correct includes for g++.

---

### Post by poisonkiller on 2009-06-07
Unfortunately such package doesn't exist... I checked Ubuntu Packages, Karmic repositorys etc. And I rechecked the source code, those headers really do exist. :P

---

### Post by SledgeHammer_999 on 2009-06-07
how about **libgstreamer-plugins-base0.10-dev**? This surely exists but I don't know if it makes your program compile.

---

### Post by poisonkiller on 2009-06-08
I have that package installed and included, but my program still isn't compiling.

---

### Post by SledgeHammer_999 on 2009-06-08
I don't know, I am using Jaunty, and there isn't a package that provides playbin2.h here.

What command line do you use to compile? Are you using pkg-config?

---

### Post by poisonkiller on 2009-06-08
Yes, I am using pkg-config. I'm pretty sure I have everything correctly configured. The only problem is, that playbin2.h doesn't exist in /usr/include/gstreamermm-0.10/gstreamermm, but it should exist, since it does exist in the source code ([http://ftp.gnome.org/pub/GNOME/sources/gstreamermm/0.10/](http://ftp.gnome.org/pub/GNOME/sources/gstreamermm/0.10/)).

---

### Post by poisonkiller on 2009-06-08
Well... I finally solved it. :D
I compiled it from source and I accidentally noticed, that all the header files weren't created in /usr/include/gstreamermm... but instead /usr/local/gstreamermm... Now everything is working perfectly. :)

---

### Post by SledgeHammer_999 on 2009-06-08
good to hear. Keep on hacking on gstreamer. I am too :p

---

