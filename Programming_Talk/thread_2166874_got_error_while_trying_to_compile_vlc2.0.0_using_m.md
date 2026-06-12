---
title: "got error while trying to compile vlc2.0.0 using make command"
date: 2013-08-11
forum: Programming Talk
---

### Post by Rahul04789 on 2013-08-11
Hi friends,

I installed the vlc2.0.0 source code from the url:   **[http://download.videolan.org/vlc/2.0.0/](http://download.videolan.org/vlc/2.0.0/)**
While compiling it using make command, I got the following error:

Making all in share
make[2]: Entering directory `/home/rahul/Gstreamer/vlc-2.0.0/share'
  LUAC   lua/playlist/appletrailers.luac
/usr/local/bin/luac: lua/playlist/appletrailers.lua:70: invalid escape sequence near '\.'
make[2]: *** [lua/playlist/appletrailers.luac] Error 1
make[2]: Leaving directory `/home/rahul/Gstreamer/vlc-2.0.0/share'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rahul/Gstreamer/vlc-2.0.0'
make: *** [all] Error 2


I checked further for lua, which was installed in my system
rahul@rahul-VPCEG28FN:~$ lua -v
Lua 5.2.2  Copyright (C) 1994-2013 Lua.org, PUC-Rio

I even installed liblua5.2-dev package by using "Synaptic Package manager", but was not able to remove my error.

Please someone tell me what shoul I do?

Thanks & Regards

---

### Post by sanderj on 2013-08-11
I would start by using the most recent VLC: [http://download.videolan.org/vlc/last/](http://download.videolan.org/vlc/last/)

---

### Post by Rahul04789 on 2013-08-11
@sanderj:

I did the same but gor error whulr execution:

rahul@rahul-VPCEG28FN:~$ vlc ABC.webm 
VLC media player 2.0.5 Twoflower (revision 2.0.5-0-g1661b7d)
[0x9273908] main libvlc error: No plugins found! Check your VLC installation.



Please tell me how to resolvde it..

---

### Post by sanderj on 2013-08-11
why do you want to compile VLC yourself? Why not install it using "sudo apt-get install vlc"?

---

### Post by nathan-b on 2013-08-11
> **sanderj said:**
> why do you want to compile VLC yourself? Why not install it using "sudo apt-get install vlc"?

People always answer these type of threads by saying something like this. I think the answer is, "because we can". :cool:

Personally, I've learned a lot about the system by compiling things for some crazy reason and then trying to fix dependency errors or whatnot. Granted, the most important lesson was that the package manager is there for a reason, but it was fun at the time. And there's always the odd package that wasn't compiled with some option that I want. I think on an old Debian or something GtkPod wasn't compiled with mp3 support for licensing reasons so I compiled it myself. It happens.

---

### Post by Bachstelze on 2013-08-12
> **nathan-b said:**
> People always answer these type of threads by saying something like this. I think the answer is, "because we can". :cool:

Well, this OP obviously can't. :)

---

### Post by ofnuts on 2013-08-12
Have you at least got a look at line 70 of lua/playlist/appletrailers.lua?

---

