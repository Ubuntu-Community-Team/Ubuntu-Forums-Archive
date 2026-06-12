---
title: "what libs do I need to make a program"
date: 2006-07-11
forum: Programming Talk
---

### Post by markpalinux on 2006-07-11
I saw this math program on digg (or was it freshmeat) the other day.
[http://home.swipnet.se/ump/](http://home.swipnet.se/ump/)

when I tried to make it, I had to go and install gcc then g++, now when I try make it looks like some libs are needed (for gl and X11).

Is there a good way for me to findout what libs I need to make the program other then trial and error.

Thanks,
Mark

---

### Post by digby on 2006-07-11
Have you installed the build-essential package?

---

### Post by markpalinux on 2006-07-12
Thanks - after I got the tools, I ran make again. 

I was then missing some headers – I used [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to search for which package included the files and added them manually with an apt-get install.

Some of the files I had to search for were:
gl.h
glu.h

I later found that checkinstall and auto-apt
Would have helped me.
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

:)

---

