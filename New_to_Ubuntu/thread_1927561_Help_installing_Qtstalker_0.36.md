---
title: "Help installing Qtstalker 0.36"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by kainreaver on 2012-02-18
Hello Everybody,

First of all I am new to linux and have been using Ubuntu 11.10 livecd for 4 months now and loving it.  I am
interested in loading qtstalker 0.36 using livecd for a test before completely saying goodbye to windows 7.
I have followed the instructions as in installing qtstalker 0.36 and have loaded the following:-

1.  QT3 Designer
2.  build-essential
3.  libdb4.8 dev
4.  qt3-dev-tools
5.   libqt3-mt-dev

Followed the instructions for loading ta-lib as following:-

1.  ./configure
2.  make
3.  sudo make install

Followed the instruction for loading qtstalker as following:-

1.  export QTDIR=/usr/share/qt3
2.  ./configure
3.  make
4.  sudo make install

After all this I am still not getting any qtstalker directory other then the downloaded file.  Where am I going wrong?  I still do not have qtstalker working.  I have read other forums on installation help but I am unable to get anything going with qtstalker.  Could anybody please me.

Regards

---

### Post by Ms. Daisy on 2012-02-19
You didn't list the [TA-lib]("http://ta-lib.org/") shown in [this documentation]("http://qtstalker.sourceforge.net/install.html"), is it installed?

---

### Post by kainreaver on 2012-02-19
Thanks for your reply Ms. Daisy.

I download TA-lib into Downloads folder and changed directory into it and did the following:-

1.  ./configure
2.  make
3.  sudo make install

After this I tried typing ta into the console and i did get ta-lib-config.  But locate ta-lib-config returns nothing.

Where am I going wrong?

Thanks and Regards

---

### Post by Ms. Daisy on 2012-02-20
I have to say that the directions on the [Qtstalker: Basic Installation]("http://qtstalker.sourceforge.net/install.html") page are intimidating to me.  It appears that there is an order in which things must be installed.  It looks like you need to install TA-lib _before _you install qtstalker.  If you've got everything already installed and you're trying to add TA-lib afterwards then it probably won't work.

You may consider starting over. Purge qtstalker and then follow the guide letter-for-letter.  (The guide has a Debian Package that you may want to look at, I glanced at it and it says they're for testing/unstable. I don't know if you're up for that, but it puts me off.)  It's probably possible to fix your broken installation but frankly I don't have the slightest idea how to do that.

---

### Post by kainreaver on 2012-02-21
Thanks for your reply Ms. Daisy

It would seem that when I type make in qtstalker, I get error messages saying that 
system is not recognized in UpgradeMessage.cpp.  I believe the error is something to do
with system.  I am unable to locate function system in the files.

It would seem that when I type make in qtstalker, I get error messages saying that 
system is not recognized in UpgradeMessage.cpp.  I believe the error is something to do
with system.  I am unable to locate function system in the files.

So I decided to plunge even further by downloading the cvs qtstalker and tried to install it.  I got as
far as make in qtstalker which says qwt_plot.h is not found.  The files are in qwt folders under
/usr/share/qwt.  But the qtstalker.pro file is looking for qwt-qt4 folder which is based on QWT5.0 
version.  Ubuntu 11.10 uses QWT 6.0 version and the folders are named qwt.

I have no idea as to how to proceed further.  Thinking of giving up on qtstalker and Ubuntu completely.

Will try for another 1 week before I run out of ideas or patience.

Once again thanks for your help.

Regards.

---

### Post by kainreaver on 2012-02-22
Ms. Daisy,

I finally installed qtstalker 0.36 using ubuntu 11.10 livecd.  The problem was system was part of
stdlib.h library and I included that in UpgradeMessage.h and IndicatorPage.h and ran the program.
Also I need to include /usr/local/lib in ld.so.conf file for the program.

I even tried 0.37 version on Ubuntu 11.10 livecd unfortunately it uses QWT 6.0 version which has 
different files to 5.2.2 version.  I only managed to get it to work on Debin livecd since it uses
libqwt5-qt4-dev.  I manage to start up the application but as to actually using it is another task.

Anyway I think I will be sticking to Ubuntu 11.10 after all.

Thanks for you help and regards.

Bye.

---

### Post by Ms. Daisy on 2012-02-22
Glad it worked out.

Please mark your thread as solved by clicking on "Thread Tools" at the top of the page and choosing "mark as solved."

---

### Post by kainreaver on 2012-02-22
Thanks for that Ms. Daisy,

I was wondering how to do that.

Regards.

---

