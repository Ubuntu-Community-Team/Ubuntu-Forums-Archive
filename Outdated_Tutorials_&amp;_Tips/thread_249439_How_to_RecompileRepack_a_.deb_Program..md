---
title: "How to Recompile/Repack a .deb Program."
date: 2006-09-02
forum: Outdated Tutorials &amp; Tips
---

### Post by ZebCarnell on 2006-09-02
How to Recompile/Repack a .deb Program.

By: Zeb Carnell

Ok so you have a program you like on your Debian GNU/Linux based system and would like to edit a menu or option or even recompile the .deb source with a new option or config. You may wonder how you can do this. Well here goes.

Build the basic development environment:

*    apt-get install devscripts build-essential fakeroot *

This installs the necessary packages needed for most development builds in GNU/Linux.
Now you need the source code for the package you wish to repack:

*    apt-get source packagename *

This will download the source code for the package into the directory you are currently in. So please Change Directory (cd) to the directory you want to work in. The above command also unpacks the tar file for you into that directory, so now for you to edit the source code you need to cd into the source folder:

*     cd packagename-version *

Now make your changes. You can adjust which flags are passed to the configure script by looking at the file inside the debian/ directory called "rules". This is where "./configure" and "make" are called from.
So once your changes are made we need to setup the dependencies to repack the package:

*     apt-get build-dep packagename *

Now you can actually rebuild the package. You perform a rebuild by using the debuild command. If you are not the maintainer of the package you will need to add two flags to this telling the build process not to sign the package. In most cases -us -uc are the switches you wish to use. (make sure you are in the source main directory of packagename-version):

*     debuild -us -uc *

Now if you look in the parent directory you will find your recompiled .deb file.
You can install it using:

*     dpkg –i packagename.deb *

If you store your packages inside an Apt repository then you can use "pinning" to make your local package have a higher priority than others.
This doesn't work if you're just using "dpkg --install packagename.deb" to install the file though. In that case you can either:
*Put the package "on hold", so it is never upgraded.
*Rebuild your package with a higher version number, e.g: packagename-version.01


Zeb

---

### Post by jlc on 2007-01-27
How to you upgrade the package version?

---

### Post by glennric on 2007-01-27
> **jlc said:**
> How to you upgrade the package version?

You can use debchange (or its alias dch) to do this.  From the directory of the package you are going to install type "dch" and it will open the changelog in an editor.  You might also try "dch -nmu".  This will add a .1 to the version, and then open the changelog in an editor for you to add a comment if you like. nmu stands for non-maintainer upload.  See man dch for more details.

---

### Post by lightenup on 2007-04-10
Zeb,

Thanks for the post! I was searching all over for a good tutorial on how to compile / re-compile a source package.

LiGHTENUP

---

### Post by ashrack on 2007-04-12
This works great. Tnx.

is it possible to recompile again using that command without having to untar the source again? Because if I dont untar the source again it gives me some errors.

---

### Post by blaz_boy on 2008-08-16
ok , tanks for that but how can i want to do somthing
if i installed an application and i want to repackage it from the installed files , i mean to convert all the installed files of the app to a .DEB package.
cause sometimes i set with my friends they admire a program and we can't reach an internet connection right now and we need to install this program on his labtop , how can i make that ?:popcorn:

---

### Post by zaksworld on 2009-10-18
Thanks so much!  Already I've used this about five times since I read it! :D

---

