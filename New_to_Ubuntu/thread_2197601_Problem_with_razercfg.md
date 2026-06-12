---
title: "Problem with razercfg"
date: 2014-01-04
forum: New to Ubuntu
---

### Post by sliddex on 2014-01-04
Hi guys! I have problem with razercfg. I've runned these commands in console
```

sudo apt-get install python
sudo apt-get install libusb-1.0-0-dev
sudo apt-get install python-qt4
sudo apt-get install cmake

```
and I have this error "Could not find library "libusb-1.0" with header libusb.h". Im using HDD for home folder, and other part of OS is on my SSD. Is it possible this to be problem?

---

### Post by Menthu_Rae on 2014-07-04
Hey mate,

6 months on... but if you (or anyone else) still need the program - this is probably the issue:

[http://ubuntuforums.org/showthread.php?t=1729300&p=10692447#post10692447](http://ubuntuforums.org/showthread.php?t=1729300&p=10692447#post10692447)

So make sure you:

```
rm CMakeCache.txt
```

Once that's done - this is how I set it up in 14.04 [on KUbuntu] (with help from README and googling errors as they came up):

First make sure you have all of your dependencies - I found I needed pyside to make qrazercfg run...

```
sudo apt-get install libusb-1.0-0 libusb-1.0-0-dev cmake python-qt4 python3-pyside
```

Now, from the directory you git-cloned or unzipped into...

```
cmake .
make
```

```
sudo su
```

```
make install
cp ./razerd.initscript /etc/init.d/razerd
ln -s /etc/init.d/razerd /etc/rc2.d/S99razerd
ln -s /etc/init.d/razerd /etc/rc5.d/S99razerd
ln -s /etc/init.d/razerd /etc/rc0.d/K01razerd
ln -s /etc/init.d/razerd /etc/rc6.d/K01razerd
```

Now, according to the README:

> If you don't have an xorg.conf, you don't have to do anything and it
should work out-of-the-box.

If you do... then reference the README for what you need to do, the section is:

> X11-WINDOW (X.ORG) CONFIGURATION
================================

Make sure you run the service... either as su if still carrying on from above or sudo if you opened a new shell:

```
service razerd start
```

Then you should just be able to run either:

```
razercfg
```

or

```
qrazercfg
```

If you chose qrazercfg - you should get a nice GUI like this:

[ATTACH=CONFIG]254450[/ATTACH]

---

### Post by Bucky Ball on 2014-07-04
And with that, we'll bid this until recently dormant and unanswered old thread good night. Thanks for sharing your fix and hopefully it will help future travellers. 
[I]
Thread closed. [/I]

;)

---

