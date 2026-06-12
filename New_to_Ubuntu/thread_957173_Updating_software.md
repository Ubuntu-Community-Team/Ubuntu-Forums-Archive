---
title: "Updating software"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by brandoncolorado on 2008-10-24
Hi,

I have a few questions about updating OpenOffice.  I would like to go to version 3.  I have done forum research, and I am confused.

1)  What does it mean to use a PPA to update OpenOffice?  I believe that the PPA is a repository.  If I use this to update, will Ubuntu 'take over' control of the program after the next version is released and OpenOffice 3.0 becomes the standard?  

2)  What are the disadvantages to installing via a .deb file?  Can I just install it from the OpenOffice.org website?  If I do, will the software automatically update itself like all of my other software?  What happens when the system wants to update 2.4 to 3.0?  Won't I have two 3.0 versions on my computer?

3)  What is the best way of doing this without F*%&* things up?

---

### Post by igknighted on 2008-10-24
A 'PPA' is a personal repository that someone has set up.  It has software that is not certified by Ubuntu, but is packaged by users, for users.  It is (usually) safe to use.

You can install via a .deb package, but there are disadvantages.  First, it can be complicated to get all the dependencies when installing a .deb.  Also, you will not get updates via apt/synaptic for a .deb install (where as since a PPA is a repository and will be used by apt, so any updates to the PPA will be passed on).

The .deb's that Ubuntu issues have tweaks to work better in Ubuntu, and integrate (visually mostly) better.  The .deb's from OO.o will not have this.

Also, if you do install 3.0, completely remove 2.4 first (use the --purge option).  Sometimes they can coexist, but sometimes there are issues.  I wouldn't chance it.  You can always apt-get 2.4 again if 3.0 doesn't work out.

---

### Post by fr.theo on 2008-10-24
hi, check out this site or this thread

site: [http://openofficedocs.wordpress.com/2008/10/14/install-openoffice-30-on-ubuntu/](http://openofficedocs.wordpress.com/2008/10/14/install-openoffice-30-on-ubuntu/)

Thread: [http://ubuntuforums.org/showthread.php?t=953065&page=2](http://ubuntuforums.org/showthread.php?t=953065&page=2)


good luck.

---

### Post by em4r1z on 2008-10-24
You'd better play it simple and stick to the version provided in the Ubuntu repositories unless there was a feature you really needed. Try OOo 3 using a LiveCD of Mandriva 2009, Fedora 10 beta or OpenSUSE 11.1 beta 3 and see if it fits your needs.

---

### Post by Hexagoon on 2008-10-24
Here's a tutorial

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

---

