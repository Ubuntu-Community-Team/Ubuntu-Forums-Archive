---
title: "Make a .deb from source"
date: 2007-06-15
forum: Programming Talk
---

### Post by ThaddeusW on 2007-06-15
Hello, 
Hopefully this is the proper forum to ask this question. Is there a way to create a .deb from any source? For example I always like to install Midnight Commander but there is no Ubuntu package available. After configuring and compiling is there a way to make a .deb? I would rather this method to keep track of all my software through synaptic.

---

### Post by AdamG on 2007-06-15
sudo apt-get install mc

:)

---

### Post by RawMustard on 2007-06-15
sudo apt-get install checkinstall

man checkinstall

---

### Post by avik on 2007-06-16
Like RawMustard said, get checkinstall.

Then, after you've compiled your program, use sudo checkinstall instead of sudo make install.  It's that simple.

---

### Post by vexorian on 2007-06-16
> **avik said:**
> Like RawMustard said, get checkinstall.

Then, after you've compiled your program, use sudo checkinstall instead of sudo make install.  It's that simple.
hey this is great, always wanted to know how are deb packages made.

I got a question , I want to modiffy requirements but if I type 10. nothing happens...

---

### Post by avik on 2007-06-16
> I got a question , I want to modiffy requirements but if I type 10. nothing happens...

Weird.  Does that happen to any of the other choices (such as version, maintainer, etc.)?

---

### Post by vexorian on 2007-06-16
That's the odd thing, all the other ones work, maybe last night my mind was bugged gonna try again.

Edit: tried again no luck:
Typing 10 makes the menu appear again and insist to type a number to modify a field.

And while we are on it, what's "group" supposed to hold?

---

### Post by avik on 2007-06-16
> That's the odd thing, all the other ones work, maybe last night my mind was bugged gonna try again.

That *is* weird.  But I've never used that option anyway.

> And while we are on it, what's "group" supposed to hold?

It doesn't really matter.  Unless I'm going to make a set of packages all related to each other, I leave that field as it is.

I usually only modify maintainer.

---

### Post by g8m on 2007-06-16
hmm, coincedentially I also was looking for a way to make deb files from source.

In my case a qt4-based source which is build with cmake, make, make install.

I tried the "its that easy" sudo checkinstall, answered the questions...

Building Debian package...OK

Installing Debian package... FAILED!

Looking in the package it appears that half of qt4 is installed. Header files. Those belong to qt4
and don't need to be installed.

am I doing something wrong?

---

### Post by danhm on 2007-06-16
> **g8m said:**
> hmm, coincedentially I also was looking for a way to make deb files from source.

In my case a qt4-based source which is build with cmake, make, make install.

I tried the "its that easy" sudo checkinstall, answered the questions...

Building Debian package...OK

Installing Debian package... FAILED!

Looking in the package it appears that half of qt4 is installed. Header files. Those belong to qt4
and don't need to be installed.

am I doing something wrong?

I had the same problem with Pidgin 2.0.2, but checkinstall normally works great.

Does anyone know what's up?

---

### Post by loell on 2007-06-16
when checkinstall's generates an error, it has an error log.

perhaps someone can post the log here on that particular problem.

---

### Post by g8m on 2007-06-16
After some reading (man checkinstall) and some experimenting, I was able to build the deb.

      sudo checkinstall -D --exclude /lib,/usr/include,/usr/lib,/usr/bin


I was able to do this because the app is installed in /usr/local. Eventually I will install it in /usr/bin and will have that problem again.

Should I debianalize. dh-make, dpkg-buildpackage -rfakeroot, or will I get the same problems.

---

### Post by Mickeysofine1972 on 2007-06-16
Hey guys

CheckInstall is fine most of the time but to make a proper deb there a video that will help:

[http://www.showmedo.com](http://www.showmedo.com)

Other than that you will have to wait until my new app is ready [http://ubuntu-utils.wikispaces.com](http://ubuntu-utils.wikispaces.com)

Mike

---

### Post by loell on 2007-06-16
yeah ... ofcourse, checkinstall is never the proper way of making a deb, especially if you intend to distribute it.
checkinstall deb is only usefull when you are installing from source, this way you can uninstall the app easily.

---

