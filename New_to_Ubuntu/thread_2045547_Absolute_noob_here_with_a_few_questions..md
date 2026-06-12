---
title: "Absolute noob here with a few questions."
date: 2012-08-21
forum: New to Ubuntu
---

### Post by Darkenmal on 2012-08-21
Hey guys, literally installing Ubuntu onto my 8gb drive as we speak! Its pretty exciting times. :P

But I have a few questions for you all.

1. When I turn on my computer, can I just choose between Ubuntu and Windows? Thats it?

2. Considering its only a 8gb drive how could play games that work on it? Would I have to install games onto the drive or could I use my 1.5 tb thats just plugged into my computer?

Any other helpful advice would be awesome. Thanks guys!

---

### Post by kemtnbkr on 2012-08-21
> **Darkenmal said:**
> Hey guys, literally installing Ubuntu onto my 8gb drive as we speak! Its pretty exciting times. :P

But I have a few questions for you all.

1. When I turn on my computer, can I just choose between Ubuntu and Windows? Thats it?

2. Considering its only a 8gb drive how could play games that work on it? Would I have to install games onto the drive or could I use my 1.5 tb thats just plugged into my computer?

Any other helpful advice would be awesome. Thanks guys!

Welcome to Ubuntu/ Linux in general. 

I assume you mean a flash USB drive?  but if you install Ubuntu to a flash USB drive, you can just select your boot device from your BIOS and boot either from your internal HDD (Windows) or a USB device (Ubuntu).  

Generally, if you plan on using ubuntu regularly, it is better to install to your internal hard drive- faster read/write and more space available.  If you are installing to a partition on your hard drive, when you first boot your computer the GRUB 2.0 menu will appear; you can pick Ubuntu (or another installed distro) or windows at this point.

As far as games go, playing off of a flash drive probably wouldn't work the greatest as it would have poor read/write speeds, not to mention the space restrictions.  If you are intent on using a flash drive, you also may want to look up a lighter-weight distro, for example Lubuntu or Xubuntu.  These lightweight distros generally take up less space than the full-on Ubuntu, plus load more quickly on slower hardware.

Hope my (somewhat meandering) reply was helpful.  Good luck, and whatever path you choose, don't be afraid to ask.

---

### Post by cbanakis on 2012-08-21
If you have windows installed, and select side by side install during ubuntu setup, you should be able to choose an os on boot.

8GB is probably not enough to have windows and ubuntu installed.
(Not sure what version of windows you have, but Vista & 7 are very large installed)
Ubuntu is under 2GB.  (I think)

I'm sure there is a way you can have Ubuntu apps/games install to your 1.5TB, but I have never tried it.  Someone here will know.  (Might be easier to just use the 1.5TB for everything)

I recommend installing from a CD instead of a flash drive.
(there are plenty of benefits to a flash drive install, but it can sometimes cause problems)

Look around in the Ubuntu Software Center, after your install is complete.
Not sure if you have ever heard of it, but its kinda like the appstore on your smart phone, except nearly everything is free.

If you cant find what your looking for, there is a program called wine, which allows you to run windows software in linux.

Hope all this helps.

Edit (Somehow I did not even consider that you were talking about an 8GB flash drive)
Best to install on the 1.5TB.  (You can keep windows, just by selecting "install Ubuntu beside windows" during install)

---

### Post by Bufeu on 2012-08-21
1. Yes, simple as that.
2. That's a tricky question. Linux doesn't install an app/a program to a specific ("fixed") place. Instead the file are "spead" over the disk, eg. binaries to /bin and configuration files to ~ (your home folder).
You can move /bin to an other storage device, yes. There's several threads about this topic here on ubuntu forums, and via Google you'll find even more, foe example [this]("http://www.overclock.net/t/728823/make-ubuntu-install-programs-to-another-drive-d").

---

### Post by Darkenmal on 2012-08-21
> **cbanakis said:**
> If you have windows installed, and select side by side install during ubuntu setup, you should be able to choose an os on boot.

8GB is probably not enough to have windows and ubuntu installed.
(Not sure what version of windows you have, but Vista & 7 are very large installed)
Ubuntu is under 2GB.  (I think)

I'm sure there is a way you can have Ubuntu apps/games install to your 1.5TB, but I have never tried it.  Someone here will know.  (Might be easier to just use the 1.5TB for everything)

I recommend installing from a CD instead of a flash drive.
(there are plenty of benefits to a flash drive install, but it can sometimes cause problems)

Look around in the Ubuntu Software Center, after your install is complete.
Not sure if you have ever heard of it, but its kinda like the appstore on your smart phone, except nearly everything is free.

If you cant find what your looking for, there is a program called wine, which allows you to run windows software in linux.

Hope all this helps.

Edit (Somehow I did not even consider that you were talking about an 8GB flash drive)
Best to install on the 1.5TB.  (You can keep windows, just by selecting "install Ubuntu beside windows" during install)


First off, thanks for the speedy replies guys.

Just zeroing in on this answer, I have a few more questions which arose from your answers.

1. My windows is not installed on my 1.5 tb, but a lot of my stuff is on there is it in danger of being lost? And since Windows is on another harddrive (internal two 500gb, 1tb raid), what happens to that?

2. If I install on my 1.5 tb, how much should I do? (I have 500 gb in space) and using wine, can I access my windows folders with wine and run my games? 

Thanks again.

---

### Post by sandyd on 2012-08-21
> **cbanakis said:**
> If you have windows installed, and select side by side install during ubuntu setup, you should be able to choose an os on boot.

8GB is probably not enough to have windows and ubuntu installed.
(Not sure what version of windows you have, but Vista & 7 are very large installed)
Ubuntu is under 2GB.  (I think)

I'm sure there is a way you can have Ubuntu apps/games install to your 1.5TB, but I have never tried it.  Someone here will know.  (Might be easier to just use the 1.5TB for everything)

I recommend installing from a CD instead of a flash drive.
(there are plenty of benefits to a flash drive install, but it can sometimes cause problems)

Look around in the Ubuntu Software Center, after your install is complete.
Not sure if you have ever heard of it, but its kinda like the appstore on your smart phone, except nearly everything is free.

If you cant find what your looking for, there is a program called wine, which allows you to run windows software in linux.

Hope all this helps.

Edit (Somehow I did not even consider that you were talking about an 8GB flash drive)
Best to install on the 1.5TB.  (You can keep windows, just by selecting **"install Ubuntu beside windows" **during install)
- Just a note
Sometimes, (It has happened), using the Ubuntu installer to resize the Windows partition causes Windows to chkdisk. Sometimes, it never finishes.

The safest way is to use the Windows Disk Manager to create Free space, and then partition that in Ubuntu.

You can access the Windows Disk Manager in 
Control Panel -> Administrative Tools (switch to large icons view if you don't see it) -> Computer Management.

---

### Post by Darkenmal on 2012-08-21
> **sandyd said:**
> - Just a note
Sometimes, (It has happened), using the Ubuntu installer to resize the Windows partition causes Windows to chkdisk. Sometimes, it never finishes.

The safest way is to use the Windows Disk Manager to create Free space, and then partition that in Ubuntu.

You can access the Windows Disk Manager in 
Control Panel -> Administrative Tools (switch to large icons view if you don't see it) -> Computer Management.

Can you explain please? That just went through one ear and out the other lol.

---

### Post by cbanakis on 2012-08-21
> **Darkenmal said:**
> First off, thanks for the speedy replies guys.

Just zeroing in on this answer, I have a few more questions which arose from your answers.

1. My windows is not installed on my 1.5 tb, but a lot of my stuff is on there is it in danger of being lost? And since Windows is on another harddrive (internal two 500gb, 1tb raid), what happens to that?

2. If I install on my 1.5 tb, how much should I do? (I have 500 gb in space) and using wine, can I access my windows folders with wine and run my games? 

Thanks again.

In theory, the partitions will be resized using available free space, so nothing should be lost.
I can't say much about that though, because I never did a dual boot.
(Though I am sure its fine, because Ubuntu is designed to dual boot with windows)

If you can access your Windows programs from an Ubuntu session, small/dinky programs should just work on double click (If you have wine installed)

However, because of registry entries, and dependencies, most programs will probably need to be re-installed in Ubuntu using wine.

And wine is far from perfect.  (Not all Windows programs work)

You can check for compatibility at [http://appdb.winehq.org/](http://appdb.winehq.org/)
(Shows all known programs that have been tested with wine, and the results)

I know MS Office 2010/2007/2003 all run in wine.

Also...
Photoshop CS2
Diablo III
World Of Warcraft
Adobe Audition
(These are programs I have running, so I know they work great)

---

### Post by sandyd on 2012-08-21
> **Darkenmal said:**
> Can you explain please? That just went through one ear and out the other lol.
I mean that if you click the 'install beside windows' option, that can happen.

---

