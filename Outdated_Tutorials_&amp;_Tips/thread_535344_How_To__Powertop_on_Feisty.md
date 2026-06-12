---
title: "How To:  Powertop on Feisty"
date: 2007-08-26
forum: Outdated Tutorials &amp; Tips
---

### Post by shof2k on 2007-08-26
This is a summary of installing Intels powertop tool as discussed [ **_here_** ]("http://ubuntuforums.org/showthread.php?p=3089596").  This is source based, so you will need to be familiar with a terminal beforehand.

This only applies to Feisty, since Gutsy will have this in the repos.  I can't comment for any previous version however.  Also note that you need kernel 2.6.21 or above.

1) Install the following prerequisites:
```
sudo apt-get install build-essential libncurses5-dev libncursesw5-dev 
```

2) Download the latest powertop source from [ **_here_** ]("http://www.linuxpowertop.org/download.php").  I've used version 1.8, but some have stuck to version 1.2

3) Put the source in /usr/src and unpack using ```
sudo tar -xvf powertop-1.8.tar.gz 
```

5) Compile using: ```

cd powertop-1.8
sudo make
sudo make install
```
You can also use "checkinstall" instead of "make install" to create a simple .deb for easier removal.

6) Run with 
```
sudo powertop 
```

I don't pretend to know a lot about this, but it appears a useful tool so I'm hoping this thread will be a focus of useful discussion.  So far, my usage is limited since it complains I don't have certain kernel parameters.

---

### Post by aqcohen on 2007-08-30
The  step five (5) is mistyped.

cd powertop-1.7 must be cd powertop-1.8 

:) 
newbe users may confuse that.

---

### Post by shof2k on 2007-08-30
> **aqcohen said:**
> The  step five (5) is mistyped.

cd powertop-1.7 must be cd powertop-1.8 

:) 
newbe users may confuse that.

Fixed.  Thanks

---

### Post by fmo on 2008-02-19
Hi,

I had to do this for the compilation of 1.9 to complete without errors:
```

 sudo apt-get install libgettext-ruby-util

```

---

