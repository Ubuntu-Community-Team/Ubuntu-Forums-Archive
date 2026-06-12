---
title: "[SOLVED] No Desktop After Installation"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by anachronon on 2008-05-19
I am new to Umbutu and Linux, though I have been working with computers, on and off, since the days of punch cards.  I have been trying to get an installation of Linux going for the past month, trying different things, but always with problems.

     I suppose I should start with one of the first and more basic problems.  I downloaded a copy of Ubuntu Studio 8.04 from Canonical (as I want to do graphics work).  However, after an 1100 MB download, DVD burn, and long installation process, all I got was the terminal command prompt, no desktop.

     After fighting it for a week, I finally stumbled upon and apt-get command, "download ubuntu desktop".  After another 1100MB download, etc, it worked, I had a desktop.

     My question is: Did I do the right thing?  Or, did I atually download a different version of 8.04?  If so, does it make a difference?  If anyone is familiar with Ubuntu Studio, please let me know.

     Thanks.

---

### Post by tamoneya on 2008-05-19
it almost sounds as if you downloaded the server edition instead of the desktop edition.  The server edition does not have a desktop since it isnt necessary for servers and will just use resources.  all of the desktop editions (ubuntu, kubuntu ,edubuntu, ubuntu studio) should all have a desktop environment of some sort.

---

### Post by anachronon on 2008-05-20
> **tamoneya said:**
> it almost sounds as if you downloaded the server edition instead of the desktop edition.  The server edition does not have a desktop since it isnt necessary for servers and will just use resources.  all of the desktop editions (ubuntu, kubuntu ,edubuntu, ubuntu studio) should all have a desktop environment of some sort.
Thanks.  Unfortunately, I don't see how I could have come up with a server edition.  Here is the download page from the Ubuntu Studio website:

     [http://cdimage.ubuntu.com/ubuntustudio/releases/hardy/release/](http://cdimage.ubuntu.com/ubuntustudio/releases/hardy/release/)

     I am using a P4 processor in that machine, so I chose the download marked "ubuntustudio-8.04-alternate-i386.iso", using the bit-torrent option.  After downloading I ran a check on the disk for errors, before burning the disk.  It checked fine.

     I guess my question is:  Do I need to re-do the download and installation?  If so, do I need to burn a new disk, reformat the HD again, etc?  Or, is there an easier way?

     Thanks.

---

### Post by tamoneya on 2008-05-20
it doesnt seem to me like you need to do anything.  You said you found apt-get and install a desktop and it works.  How is this broken?

---

### Post by jimv on 2008-05-20
I believe that when you do the install with the alternate CD, there's a section that gives you a choice of what to install...like server/desktop/etc.  I ran into this issue with a class I was helping with.  Everyone but one person got the desktop installed, and the one person that didn't get the desktop had used the alternate CD.  We went back through the install and saw an option for selecting Desktop.  Once we did that, it installed OK.

---

### Post by dstew on 2008-05-20
I think on the Alternate Install CD you have a menu that asks what software to install, and it is possible you did not check (or unchecked) something that led to the desktop being left off. But, as far as I know, once you do apt-get install ubuntu-desktop you have the whole system. I often install that way when I do a network install, that is, get the server (base) install first, then get the desktop over the internet later.

---

### Post by anachronon on 2008-05-20
Thanks everyone.  It looks like I don't really have to do anything more.  I just wasn't sure though; needed to make certain that I didn't end up with two competing installations, or something similarly problematic.

---

### Post by Drunky on 2008-05-21
[IMG]http://img153.imageshack.us/img153/7651/ubuntustudiodesktopoptimq7.png[/IMG]

If 'Ubuntu Studio desktop' option is not checked then it will not install and leave you at the command line when booted.

Good job on finding out that apt-get will load your desktop for you.

I hope you have fewer problems as you progress in your Linux travels.  Or at least the problems are quickly solved.

---

### Post by anachronon on 2008-05-21
> **Drunky said:**
> [IMG]http://img153.imageshack.us/img153/7651/ubuntustudiodesktopoptimq7.png[/IMG]

If 'Ubuntu Studio desktop' option is not checked then it will not install and leave you at the command line when booted.

Good job on finding out that apt-get will load your desktop for you.

I hope you have fewer problems as you progress in your Linux travels.  Or at least the problems are quickly solved.
Thanks.  I remember that screen.  I will try to reinstall by checking that option, as it may cure some other problems.

---

### Post by anachronon on 2008-05-21
One last note:  On reinstalling, I discovered that I wasn't properly selecting the package.  On my screen, the part with "<space> selects; <enter> activates" was cut off.  No wonder I couldn't get it to work.

    Thanks.

---

