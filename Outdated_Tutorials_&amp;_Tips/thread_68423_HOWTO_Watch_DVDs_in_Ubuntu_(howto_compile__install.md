---
title: "HOWTO: Watch DVDs in Ubuntu (howto compile / install xine)"
date: 2005-09-23
forum: Outdated Tutorials &amp; Tips
---

### Post by jworr on 2005-09-23
This is my first howto so be gentle :) 

Here is what I do to watch encrypted dvds and other video codexes on Ubuntu

This is howto install xine on your system, it works with tons of codexes and plays encrypted dvds

download the latest xine-lib, libdvdcss, and xine-ui

xine-lib & xine-ui
[http://xinehq.de/index.php/releases](http://xinehq.de/index.php/releases)

libdvdcss
[http://www.fr.linuxfromscratch.org/view/blfs-5.0/multimedia/libdvdcss.html](http://www.fr.linuxfromscratch.org/view/blfs-5.0/multimedia/libdvdcss.html)

extract all the gzip folders and open a terminal window

install these packages through synaptic
gcc
g++
autoconf
zlib1g-dev
x-window-system-dev
libpng12-dev
libpng10-dev

next do this 
sudo gedit /etc/ld.so.conf

add this line to the file and save it:
/usr/local/lib

now compile the source:

cd /path/to/libdvdcss-1.28
sudo ./configure
sudo make
sudo make install

cd /path/to/xine-lib-1.1.0
sudo ./configure
sudo make
sudo make install

cd /path/to/xine-ui-0.99.4
sudo ./configure
sudo make
sudo make install

hope this helps someone  :)

---

### Post by pinoyskull on 2005-09-23
what's the difference between your guide and and installing thru apt

---

### Post by jworr on 2005-09-24
When I installed Xine through apt it wouldn't play dvds for me maybe I was doing something wrong but it definatly didn't work

---

### Post by Goober on 2005-09-25
Hrm.  Xine never worked for me, when I installed with the apt.  Maybe this method might work . . . 

Of course, I can play DVDs in VLC, so I won't try this, I have too many needless programs floating around in my Ubuntu installation anyway, but the apt definitely does not work with DVDs.  Or I don't know how to get it working anyway.

---

### Post by Tralobyte on 2005-09-25
Apt worked for me.
sudo apt-get install xine libdvdcss2

---

### Post by Swoop on 2005-09-25
Apt get worked fine for me too.. not probelms.

---

