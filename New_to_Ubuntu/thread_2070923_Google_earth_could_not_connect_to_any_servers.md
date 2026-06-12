---
title: "Google earth could not connect to any servers"
date: 2012-10-14
forum: New to Ubuntu
---

### Post by vikotus on 2012-10-14
Hi. I'm using Ubuntu 10.04.4. Yesterday I installed google-earth to it using .deb from earth.google.com. Now when I start google-earth I get couple of messages, all telling about "cannot locate / connect servers to activate your account" so it seems google-earth cannot connect to internet. I have tried both googleearth with apt-get and downloaded .deb from earth.google.com. Same messages at both. Google servers are fine because it runs fine on my other computers (windows 7 and Linux Mint 13 on the other) Anyone here with same problem?

EDIT: Here are the error messages "Google Earth can't contact the imagery server to download new images" and "Google Earth can't contact the login server to activate your account"

My internet connection is fine, also Google Earth is running fine on same computer with Windows 7... so the problem is located here in ubuntu version or even with ubuntu.

---

### Post by waltclay on 2012-10-15
I am also having a problem. u12.04. In my case it was working fine until recently. Works for a while, but then mouse completely freezes and screen blanks periodically: only choice is power off.
My download is only a few days old, but note what "about" says about version:
Google Earth
5.1.3533.1731
Build Date
Nov 11, 2009
Build Time
4:39:12 pm
Renderer
OpenGL
Operating System
Linux (3.2.0.0)
Video Driver
X.Org
Max Texture Size
8192x8192
Server
kh.google.com
[addendum: I just remembered advice I got when I complained about the search engine in these forums: use google. Doing that, I found [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)  
Much more elaborate than I imagined.]

---

### Post by s1baker on 2012-10-15
@ vikotus
I have 12.04.01 and it runs ok


@ waltclay
I just recently installed GE on 12.04.01
I went to the Google website to get the install.
Here is what my about shows:

```
Google Earth
6.2.2.6613
Build Date
4/14/2012
Build Time
1:09:13 am
Renderer
OpenGL
Operating System
Linux (3.2.0.0)
Video Driver
X.Org R300 Project
Max Texture Size
2048x2048
available video memory
information not available
Server
kh.google.com
```

---

### Post by rafmunoz on 2012-11-06
Something similar happens to me, and I couldn't find the solution yet.  In my case, when I go to tools->3d view all options are grey and couldn't change anything.
After reinstalling several times with various methods, I tried "ldd /opt/google/earth/free/googleearth-bin" and found some missing libraries (already in the same folder).  I solved the problem creating links to that libraries in /usr/lib/i386-linus-gnu.  But there is still the same problem.  
It's curious, GE was ok when I was running 10.10, but with 12.04 it did'nt work, neither with 12.10.  And in Windows XP under a virtual machine it works slow but fine.

---

