---
title: "[SOLVED] How do you know if it installed?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by melbs on 2008-08-11
As I am learning how to get software and updates through apt-get I was wondering if there was a way to tell if what I wanted to install was installed and updated. For instance if I installed LAMP or some other software or package is there somewhere or something I can type to see if it installed? Or to see all of what I have installed? Either through command line or GUI. Thanks :)

---

### Post by rockerphil on 2008-08-11
the easiest way for me is to simply run the apt-get install again, if it did indeed install the terminal will tell you that the latest version is already installed. hope this helps,

Phil

---

### Post by mc4100 on 2008-08-11
I think this might be what you're looking for
```
dpkg -s **package name**
```
> **melbs said:**
> [Can I] see all of what I have installed? 
Sure, in Synaptic Package Manager (first, you must be in the "status" part, in the bottom left corner), there is a "installed" section on the left side which shows you only installed packages...
Also, this is related, you want to have a look at /var/lib/dpkg/status

---

### Post by melbs on 2008-08-11
Makes sense, that would work a lot of the time but I just did a tasksel and installed LAMP - I'm almost positive it installed okay would there be anywhere to "go" to see it was installed. Or a place to "go" and see a list of apps installed?

---

### Post by melbs on 2008-08-11
> **mc4100 said:**
> I think this might be what you're looking for
```
dpkg -s **package name**
```

Sure, in Synaptic Package Manager (first, you must be in the "status" part, in the bottom left corner), there is a "installed" section on the right side which shows you only installed packages...
Also, this is related, you want to have a look at /var/lib/dpkg/status


What does "dpkg" stand for? I've seen this command around. What is it? Thanks for the info. it helped out.

---

### Post by mc4100 on 2008-08-11
```
man dpkg
``` is your friend. :)
>        dpkg - package manager for Debian

> DESCRIPTION
       dpkg  is  a  tool to install, build, remove and manage Debian packages.
       The primary and more user-friendly front-end for  dpkg  is  dselect(1).
       dpkg  itself  is controlled entirely via command line parameters, which
       consist of exactly one action and zero or  more  options.  The  action-
       parameter tells dpkg what to do and options control the behavior of the
       action in some way.

---

### Post by cariboo on 2008-08-12
Try System-->Administration-->Synaptic Package Manager-->File-->History
this will list everything you have installed, removed and updated since your initial installation.

Jim

---

### Post by tinker312 on 2008-08-12
After I install something . . . like xine or something I just pop open a terminal and type xine . . . I think your environment path among other places points to /usr/bin so if the program installed to /usr/bin and you have permissions to run said program . . . it will give some indication that it is installed when you type it's name.

FYI if you want to know if something is running type ps|aux :)

---

### Post by 3rdalbum on 2008-08-12
In Synaptic, go to the package that was installed. Right-click it, go to Properties. Under the "Installed Files" tab, you'll find a list of files and locations that were installed by the package. In Nautilus, if you look for those files in the filepath, then the package has been installed.

But really, if you install a package in your package manager, it *has* installed; you don't need to check up on it.

---

### Post by nicedude on 2008-08-12
Try copying and pasting the following command ( without the quotes ) in a terminal and you will get a nice text file on your desktop that lists all the packages you have installed. I prefer doing this sometimes since its easy to use the search function to look through the text file and find whether something is present or not.


"dpkg --get-selections > ~/Desktop/WhatsInstalled.txt"


just my 2 cents

---

### Post by melbs on 2008-08-12
Thanks for all of the answers!!!

---

