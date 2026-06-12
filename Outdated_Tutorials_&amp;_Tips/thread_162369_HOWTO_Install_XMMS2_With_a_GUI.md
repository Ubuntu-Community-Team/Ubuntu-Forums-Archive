---
title: "HOWTO: Install XMMS2 With a GUI"
date: 2006-04-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Toxicity999 on 2006-04-18
If you followed the other guide on installing XMMS2 alone just pick up where that left off and you'll be fine.

Add the following to your /etc/apt/sources.list:

Dapper:
deb [http://exodus.xmms.se/debian](http://exodus.xmms.se/debian) drapper main

Breezy:
deb [http://exodus.xmms.se/debian](http://exodus.xmms.se/debian) stable main

sudo apt-get install python2.4 python2.4-gtk2 python2.4-xmms2client   xmms2-decoder-mad  xmms2-decoder-vorbis

Download Shellac:
[http://hem.bredband.net/b298027/shellac-20060412.tar.gz](http://hem.bredband.net/b298027/shellac-20060412.tar.gz)

Extract your download

cd To it

sudo python setup.py install

xmms2-launcher

shellac.py

there you go!

It's not perfect... no docking... but it's better then playing by command line.

There are plenty of Clients available for XMMS2 just look around if this isnt good enough for yeh!

---

### Post by sargate on 2006-11-11
i can not use dr cox aka rxmms2 (is a client writen in ruby), i already try everything, neither XMMS2Musica, not even shellac, in the FAQ of xmms2 they say you have to reinstall with a diferent configuration, but you can not do that whit deb's.
Any suggestions?

Update: i can use python clients but not ruby clients

---

### Post by fridaythe14th on 2007-05-24
I tried to install Shellac (in Feisty a year after this topic was written). It complained about not finding a module named xmmsclient. It also loitered my file system with files in various folders. Not sure I was able to find and delete all of them (not that I really had to).

Also shellac hasn't been updated in a a year.

Does anyone know a better GUI to use? (Sorry if you're the author of Shellac)

---

