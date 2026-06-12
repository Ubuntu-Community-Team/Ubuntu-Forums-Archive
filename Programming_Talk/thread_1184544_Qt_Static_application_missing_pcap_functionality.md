---
title: "Qt Static application missing pcap functionality"
date: 2009-06-11
forum: Programming Talk
---

### Post by remy06 on 2009-06-11
Hi,

I have a static application that is missing functionality.

I have managed to build and install Qt ( qt-x11-opensource-src-4.5.0.tar.gz ) on ubuntu 8.04 following this tutorial : 
[http://wiki.qtcentre.org/index.php?title=Building_static_Qt_on_Linux]("http://wiki.qtcentre.org/index.php?title=Building_static_Qt_on_Linux")

The application is a simple sniffer that uses libpcap .After i build the application with "qmake" and "make", I tested it on another system but the application doesn't seem to capture anything,other functions seem fine. Therefore suspect the problem lies with libpcap.

The following is the steps i used:
```

1. Install libpcap files with "sudo apt-get install libpcap0.8-dev"
 
2. Building Qt static
 
sudo apt-get install libx11-dev libfreetype6-dev libavahi-gobject-dev libSM-dev libXrender-dev libfontconfig-dev libXext-dev
(* I can only get pass the ./configure step after I've installed the above......)
 
./configure -static -release -nomake demos -nomake examples -nomake tools
make
sudo make install
 
3. Building the application:
 
add to .pro file:
CONFIG += static
LIBS += -L/usr/lib -lpcap
 
export PATH="$PATH:/usr/local/Trolltech/Qt-4.5.0/bin"
qmake
make

```

everything seems fine..no errors noticed...but I can't figure out what went wrong.....

Is there any solution or something that I've missed?

Please advice...

---

