---
title: "Quanta Plus installed on 12.04"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-06-11
Hi all

I am wanting to install Quanta plus, a web design package. Its a KDE package, and my question is, is it possible to install kde packages on a system running Ubuntu 12.04.

Im asking because I ran configure and it wanted kde-config. Is it safe to install or will it screw my system up?

---

### Post by Irihapeti on 2012-06-11
No problem at all in having KDE libraries on an Ubuntu system. They are only used by the programs that need them and don't affect other stuff.

Is this a package you need to compile? If so, you'll need to install the -dev versions of libraries as well.

---

### Post by Senior_Buckethead on 2012-06-11
Thank you, 

How do I get the Dev versions of the necessary libraries?

---

### Post by Irihapeti on 2012-06-11
The -dev versions are in the repositories. I prefer to use Synaptic to find them (haven't worked out how to do that with the Software Centre).

They are needed _in addition to_ the normal libraries. E.g. you might have libreadline6 installed already but you'd need to add libreadline6-dev if a program needs libreadline6 in order to compile. Sometimes, the -dev versions are named a little differently from the base libraries, and it's a case of trial and error to find the right one.

Don't be surprised if you end up doing a little hair-tearing when trying to compile something. It's been a year or two since I compiled anything, but I certainly remember cursing when trying to figure out what I hadn't installed.

But I think it's worth it in the end. :)

---

### Post by finni on 2012-06-12
How exactly and what packages needed to be installed to get quanta running? I can't find quanta package from standard repos??


I'm defaulting to kdevelop (with php) before I get quanta running on 12.04...



EDIT: Nevermind I'm going back to 11.04.

---

### Post by buzzingrobot on 2012-06-13
I remember Quanta.  I don't believe it was upgraded to the Qt4 libraries when KDE went from version 3 to version 4.  A version from 2008 is at kde-apps.org, but I suspect you will need to install the KDE3 libraries to use it.  You will find neither Quanta or the KDE3 libraries in Ubuntu's repositories.  I saw a few scattered references to an attempt to revive it but I have no idea of its status. 

As for KDE on Ubuntu, it's quite nice.  Installing a single KDE program is likely to bring in a good number of KDE files as dependencies.  You might notice some KDE entries in your menus, but that's all.  (If you install all of KDE -- the "kde-full" package, you will see many KDE menu entries.)

---

