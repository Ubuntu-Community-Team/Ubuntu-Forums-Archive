---
title: "HOWTO: Install &quot;moodbar&quot; for AMAROK"
date: 2008-03-15
forum: Outdated Tutorials &amp; Tips
---

### Post by saadakhtar on 2008-03-15
**[SIZE="5"][COLOR="RoyalBlue"][CENTER]MOODBAR – AMAROK[/CENTER][/COLOR][/SIZE]**

**_System requirements and dependencies:_**

First of all you will need Amarok of course. The best way to do that is through your favorite package manager since it takes care of all required dependencies for you.

You will need to make sure that you have the following dependent libraries installed before we proceed with actual installation.
[COLOR="Blue"]
1._**gcc-4.0**_
2._**build-essential**_
3._**fftw3**_
4._**fftw3-dev**_
5._**libgstreamer0.10**_
6._**libgstreamer0.10-dev**_[/COLOR]

I would suggest installing the above packages using synaptic or your favorite package manager. libgstreamer0.10-dev, fftw3-dev have extra dependencies make sure that you install all of them. Your package manager will tell you that the extra dependency files are required for the main package to be installed.

Once all above packages are installed please follow these steps:

1.start terminal
2.download (to your home directory) moodbar **_wget [http://pwsp.net/~qbob/moodbar-0.1.2.tar.gz](http://pwsp.net/~qbob/moodbar-0.1.2.tar.gz)_**
3.“**cd moodbar-0.1.2/**”
4.assign yourself root privileges by using “sudo -s”, “su” or “su ” (you will need to enter the root password after above command)
5.once you are root you should see “#” after “/home/youhomedirectoryname”
6.now run config:
7.**_./configure --prefix=`pkg-config --variable=prefix gstreamer-0.10` --enable-sse2_**
8.you should see a lot of dependencies and system settings being checked for pre installation schedule
9.make sure that the process ends without any errors (the config returns some kind of error then look for the dependent file its looking for. In my case it could not configure “fftw3” i installed it but had to install the development package too)
10.now run “**_make_**” after make completes without errors
11.run “**_make install_**” and setup will install the plugin in its correct path or location.
12.Enjoy your new moodbar for AMAROK.


Additional help:

	CONFIG:
If you have a Pentium 4 or an Athlon64 or Core2
./configure --prefix=`pkg-config --variable=prefix gstreamer-0.10` --enable-sse2
If you have a Pentium 3
./configure --prefix=`pkg-config --variable=prefix gstreamer-0.10` --enable-sse
If you have an AMD K7, Athlon XP, or a non x64 Sempron
./configure --prefix=`pkg-config --variable=prefix gstreamer-0.10` --enable-k7

Please check out the “INSTALL” file in moodbar directory for more help.

---

