---
title: "Installing"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by Drezard on 2008-10-04
Trying to install apache 1.3.14 from source. (I need this version for a certain reason). I've downloaded it from: [http://archive.apache.org/dist/httpd/](http://archive.apache.org/dist/httpd/)

How do i compile it from source? I cant find a make file for it!

Daniel

---

### Post by rsambuca on 2008-10-04
Download the tarball and extract it.  The instructions on how to install are inside.

---

### Post by Drezard on 2008-10-04
I never worked that out. I feel so stupid now :S

---

### Post by rsambuca on 2008-10-04
Nothing to feel stupid about.  We all live and learn...  I think there should be a configure file in there somewhere, if I recall correctly.  Let us know how it goes.

---

### Post by rsambuca on 2008-10-04
I haven't read the file, but the usual method for installing from source would be something like this...```
tar -xzf apache-1.3.14.tar.gz
cd apache-1.3.14
./configure
make
sudo make install
```
Instead of the last line, you could use 'checkinstall' to make a deb so that it will be removable via synaptic in the future.

---

### Post by Drezard on 2008-10-04
Sudo make, make install, make config all didn't work. I tried cd'ing to /src and it didnt work either :S The only thing the install said was "run make install". Didnt work :S

Daniel

---

### Post by rsambuca on 2008-10-04
Try those commands I gave you in my last post.

---

### Post by Drezard on 2008-10-04
Going to google a few of the errors its giving me but if you know whats wrong please help.

When I run everything up to ./configure, it all works fine. ./configure works great, but make and sudo make install, throws these errors:

> 
===> src
make[2] *** No rule to make target 'all'. Stop.
make[1] *** [build-std] Error 2 


Daniel

---

### Post by rsambuca on 2008-10-05
You probably don't have the required packages that are required to install packages from source code.  Try installing the build-essential package and then try again.

You can install the build-essential packages from Synaptic Package Manager, or via command line:
```
sudo apt-get install build-essential
```

---

