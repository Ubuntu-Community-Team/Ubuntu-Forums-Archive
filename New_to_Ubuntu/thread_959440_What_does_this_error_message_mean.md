---
title: "What does this error message mean?"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by suomalainen on 2008-10-26
Ubunteros,

What does this error message mean?

Thank you.

pa@pa-desktop:~$ cd Desktop
pa@pa-desktop:~/Desktop$ chmod a+x GoogleEarthLinux.bin
chmod: cannot access `GoogleEarthLinux.bin': No such file or directory
pa@pa-desktop:~/Desktop$ chmod a+x GoogleEarthLinux.bin
pa@pa-desktop:~/Desktop$ sudo ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.3.7284.3916..............................................................
loki_setup: Suspect size value for option option


(setup.gtk2:8759): Gtk-WARNING **: Error loading theme icon 'gtk-cancel' for stock: Unable to load image-loading module: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: cannot open shared object file: No such file or directory
loki_setup: Suspect size value for option option

loki_setup: Suspect size value for option option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...

---

### Post by Xiong Chiamiov on 2008-10-26
Are you running 64-bit?  And, more importantly, does Google Earth run?

---

### Post by suomalainen on 2008-10-26
Yes I'm running 64 bit Ubuntu 7.10, But Google Earth does not launch.

Are you able to help me?

---

### Post by Xiong Chiamiov on 2008-10-26
> **suomalainen said:**
> Yes I'm running 64 bit Ubuntu 7.10, But Google Earth does not launch.

Are you able to help me?
Well, [it looks like]("https://bugs.launchpad.net/ubuntu/+bug/195928") you need a few files from a 32-bit install.  If you don't have one or know anyone who does, you could I suppose download the 32-bit live cd and grab them off of there.

---

### Post by oldsoundguy on 2008-10-26
OR .. you could un-install it and load the 32 bit version which works fine on my 32 bit machines, and my one 64 bit machine.

---

### Post by forger on 2008-10-26
medibuntu has a **googleearth** package
- Add medibuntu repositories:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```
- Install google earth:
```
sudo apt-get install googleearth
```

If this doesn't work:
- You haven't set up your repositories properly.
- I would really recommend to upgrade to a newer Ubuntu release :)

---

### Post by forger on 2008-10-26
By the way, you didn't have to start another thread ( [http://ubuntuforums.org/showthread.php?t=959347](http://ubuntuforums.org/showthread.php?t=959347) )

---

### Post by suomalainen on 2008-10-26
No this information doesn't work either and repositories are indeed set up correctly.

---

### Post by forger on 2008-10-26
hardy 64-bit has ia32-libs, the required libs for this ;)
hardy + medibuntu is the easiest way to go

---

### Post by suomalainen on 2008-10-26
I's sorry this is a bit too cryptic for me to understand you. :(

If I understand you correctly :> I have the repositories correctly installed and yes, I am using 7.10.

---

### Post by suomalainen on 2008-10-26
Can someone kindly help or advise me on this? I've been on it all day to no avail.

I tried to install Google Earth through both Synaptic Program manager and Google's web site and the installation appears to go accordingly but then when I try to launch the application the splash screen appears and everything freezes. 

I'm not a wizard with Ubuntu and high tech terms but do rely on this application.

I have been using Google Earth for almost a year now on my Ubuntu 7.10 64 bit machine with no problems until today...

All assistance appreciate.

---

### Post by forger on 2008-10-26
What I mean is to upgrade from ubuntu 7.10 (gutsy) to ubuntu 8.04.1 (hardy):
[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)
[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

Also install medibuntu repositories, but for ubuntu 8.04.1 (hardy heron):
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Ubuntu 8.04.1 64-bit which you will install contains a package named **ia32-libs**, which installed by default. That package is the one that Google Earth needs.

You can easily install it from medibuntu if you upgrade to 8.04.1:
```
sudo apt-get install googleearth
```

---

