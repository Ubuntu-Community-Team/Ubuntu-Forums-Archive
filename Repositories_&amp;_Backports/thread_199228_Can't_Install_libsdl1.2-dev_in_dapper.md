---
title: "Can't Install libsdl1.2-dev in dapper"
date: 2006-06-18
forum: Repositories &amp; Backports
---

### Post by josephfley on 2006-06-18
Hi there,

I was trying to install libsdl1.2-dev in my dapper, but I got some dep problems:

libsdl1.2-dev:
 Depends: libartsc0-dev but it is not going to be installed

libartsc0-dev:
 Depends: libglib2.0-dev but it is not going to be installed

libglib2.0-dev:
  Depends: libglib2.0-0 (=2.10.2-1ubuntu3) but 2.10.3-0ubuntu1 is to be installed

What can I do?

Thanks for your time

---

### Post by l0th on 2006-06-20
[QUOTE=josephfley]Hi there,

I was trying to install libsdl1.2-dev in my dapper, but I got some dep problems:

libsdl1.2-dev:
 Depends: libartsc0-dev but it is not going to be installed

libartsc0-dev:
 Depends: libglib2.0-dev but it is not going to be installed

libglib2.0-dev:
  Depends: libglib2.0-0 (=2.10.2-1ubuntu3) but 2.10.3-0ubuntu1 is to be installed

What can I do?

Thanks for your time[/QUOTE]

Completely new to Ubuntu and I ended up at the same point while trying to compile superkaramba. Is there anyway I can change the way ./config operates so that it'll be happy with 2.10.3-0ubuntu1? If not, how can I install 20.10.2-1ubuntu3 instead?

---

### Post by filip on 2006-06-30
I have exactly the same problem as you guys. I asked someone else to check their packages, and they have the other (correct, apparently) version of libglib2.0-0 

The only weird thing I've done to this system, is use the EasyUbuntu script. How about you guys?

---

### Post by filip on 2006-06-30
I've found the correct file here:
[http://mirror.switch.ch/ftp/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.10.2-1ubuntu3_i386.deb](http://mirror.switch.ch/ftp/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.10.2-1ubuntu3_i386.deb)

After you download the file, you use the following command in the directory you downloaded it too:

sudo dpkg --install libglib2.0-0_2.10.2-1ubuntu3_i386.deb

I still don't know how this has happened. Please ask me, if there is anything unclear.

---

### Post by NunoCorreia on 2006-07-04
filip: that doesn't want to work since apparently I've installed a more recent version of the package.

I've read the [bug reports at Launchpad](https://launchpad.net/distros/ubuntu/+source/base-config/+bug/10183) but I didn't come around to any conclusion. I need to install libsdl1.2-dev as well but I don't want to break my packages' consistency...

---

### Post by rlgc79 on 2006-07-14
I had the same problem... I solved this issue by changing my /etc/apt/sources.list to the one in [http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

---

### Post by Epimetheus on 2006-07-21
In synaptics you can degrade packages, anyone tried this? After i installed the .deb of glib i got a broken dependencie which i fixed by degrading it one version.

---

### Post by YanalAlHasan on 2006-09-20
hello all, I had the same problem in dapper 6.06 and fixed it by
(please perform all the steps you may think some are not neccessary but they will configure apt-get -f install in step 4)
1)sudo apt-get install libsdl1.2-dev (but it fails)
2)sudo dpkg --force-depends -r  libglib2.0-0(this will remove libglib)
3)downloaded libglib2.0-dev([http://packages.ubuntu.com/dapper/libdevel/libglib2.0-dev](http://packages.ubuntu.com/dapper/libdevel/libglib2.0-dev)) and tried to install it(but it failed)
4)apt-get -f install(it will do everything and remove the package which was causing the problem which is libglib2.0-data or something like that and install the downloaded libglib and download libartsc0-dev from the net and at last download libsdl1.2-dev and install it)
Hope it helps and plz do all the steps for it to work.

---

### Post by keithjr on 2006-10-01
> **YanalAlHasan said:**
> hello all, I had the same problem in dapper 6.06 and fixed it by
(please perform all the steps you may think some are not neccessary but they will configure apt-get -f install in step 4)
1)sudo apt-get install libsdl1.2-dev (but it fails)
2)sudo dpkg --force-depends -r  libglib2.0-0(this will remove libglib)
3)downloaded libglib2.0-dev([http://packages.ubuntu.com/dapper/libdevel/libglib2.0-dev](http://packages.ubuntu.com/dapper/libdevel/libglib2.0-dev)) and tried to install it(but it failed)
4)apt-get -f install(it will do everything and remove the package which was causing the problem which is libglib2.0-data or something like that and install the downloaded libglib and download libartsc0-dev from the net and at last download libsdl1.2-dev and install it)
Hope it helps and plz do all the steps for it to work.



It works for me too.  I also used EasyUbutu, so I imagine that might have something to do with it.  Try disabling the easyubuntu and plf repos that it created and try to re-install it... that might be a solution.  But yes indeed, Yanal's also works fine!

Thanks!  :mrgreen:

---

