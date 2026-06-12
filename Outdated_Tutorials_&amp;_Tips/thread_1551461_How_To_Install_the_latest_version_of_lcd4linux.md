---
title: "How To Install the latest version of lcd4linux"
date: 2010-08-12
forum: Outdated Tutorials &amp; Tips
---

### Post by prupert on 2010-08-12
This is taken from my more indepth article here:

[http://www.prupert.co.uk/2010/08/12/install-the-latest-version-of-lcd4linux-on-ubuntu/](http://www.prupert.co.uk/2010/08/12/install-the-latest-version-of-lcd4linux-on-ubuntu/)

For some reaon, Lucid only have version 0.10.X in the repos. This lacks some drivers and other features. If you simply try to compile from source, you come across some issues relating to m4. After lots of googling, I found how to fix them, so I'd thought I'd share.

First, download the latest version via svn:
```
svn co https://ssl.bulix.org/svn/lcd4linux/trunk lcd4linux
```

CD in to the new lcd4linux director and then, run ./configure. If you want to include a specific driver, for instance for Pertelian, include it here, like this:
```
./configure --with-drivers=Pertelian
```
Now, if you try to make, it wont work, I am not sure why, but there are some issues with the source and Ubuntu. To fix these, issue the two following commands:
```
mkdir m4
```
```
sudo ln -sf /usr/share/libtool/config/ltmain.sh .
```
Now, you can run:
```
make
```
```
sudo make install
```

And tada, you have version 0.11.0 of lcd4linux.

---

