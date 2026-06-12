---
title: "HOWTO: Compile CSpace on Ubuntu"
date: 2008-03-13
forum: Outdated Tutorials &amp; Tips
---

### Post by yrufset on 2008-03-13
HOWTO: compile CSpace (private p2p) on Ubuntu
Hello all.
i've been trying to send my sister (xp user) some files over the net.
i heard about this app called CSpace, which is a private decentrelized p2p program, available for both Win32 and Linux.

but only source for linux, and i was a newbie.
i searched the forums and the web for some guidence, and found nothing.

i decided to bravely try to compile it myself, and..... VOUUaLLLA!
i made it.
so i thought why not post it up as HOWTO.

a few notes:
this was tested on Xubuntu Gutsy Gibon (7.10) only. Though it should work flawlessly on any other 
Gutsy version (Ubuntu, Kubuntu Etc...)

1. first step, installing all of the dependencies:
```

sudo apt-get install python2.4 python-qt4 python-ctypes python-pycurl python-ncrypt

```

2. download CSpace source code from CSpace's web page: [www.cspace.in](www.cspace.in) (just in case the direct-link is broken)
or
use wget or any other download tool to grab: 
[http://www.cspace.in/srcdist/CSpaceSrc126.zip](http://www.cspace.in/srcdist/CSpaceSrc126.zip)

3. extarct the source code to whatever folder you wish (i did it in /home/yourname/CSpace) using your favorite extraction app.
newbies: just double click the downloaded file, choose extarct, and put it in /home/yourname/CSpace.

4. open up terminal where you extracted the source, and launch the app:
```

sudo python CSpace.pyw

```

or you can just add a launcher to desktop using that command.


using the app is very easy. you need to get a public ID key, and start adding contacts by using their keys....

feel free to post correcttions, questions, etc....

Happy-Private-P2P'ing!

---

### Post by skipf on 2008-03-15
It takes LONGER to READ about the installation than it does to install it.
 THANKS!!!

---

### Post by yrufset on 2008-03-16
Well,
there's almost no documentation about that wonderful app on the web.
i thought it might be nice to add some...

you welcome ;)

---

### Post by garba on 2009-07-14
thanks for your post, tried this on jaunty but it can't seem to go through the "connecting" stage... an open source program, based on open source stuff, working flawlessly on windows and not working at all on a linux distro oh well ps fyi yes im kind of pissed off

---

