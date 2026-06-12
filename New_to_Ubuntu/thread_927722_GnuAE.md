---
title: "GnuAE"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by GSands on 2008-09-23
I am looking for some assistance in installing GnuAE in Hardy anybody up to helping?  Yes I am a convert from the "other" OS, and I will never go back.:KS

---

### Post by Mornedhel on 2008-09-23
This one looks like it hasn't been maintained for the last three years (from their CVS repository). It's not on the GNU FTP either. You'll have to :

1. Install CVS from the 'cvs' package
2. Using CVS, get the sources of gnuae (link : [http://savannah.gnu.org/cvs/?group=gnuae](http://savannah.gnu.org/cvs/?group=gnuae))
3. From there it looks like the standard configure/make/make install applies :
3. a. Get the 'build-essential' package
3. b. In the source folder, do : ./configure
3. c. Then do : make
3. d. Finally do : sudo make install
4. With a little luck everything works. You can now type gnuae at a terminal to start the software.

At 3. c. you will probably run into errors depending on what libraries gnuae relies on. Make will warn you accordingly. You will have to get those libraries from the Ubuntu repository (same place you got cvs and build-essential from).

Note that this is not the standard method for installations, but this particular program is not maintained and never was packaged properly for Debian or Ubuntu.

---

