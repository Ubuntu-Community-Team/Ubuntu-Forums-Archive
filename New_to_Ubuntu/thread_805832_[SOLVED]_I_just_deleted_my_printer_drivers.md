---
title: "[SOLVED] I just deleted my printer drivers"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by phread59 on 2008-05-24
I was trying to update my printer driver it's an HP 5140.  I went to hp's web site and installed the drivers as reccomended.  One dependancy asked if the kernel driver should be deleted and new driver installed.  It deleted the kernel driver but bombed the new driver install.  Now printer is dead.  It did work before but had a few glitches.  I tried to get a better driver.  I failed yet again.  Any suggestions on where to get a driver and install it or reinstate kernel driver?

Mark Shuman

And feeling dumb for deleting anything from the kernel.

---

### Post by Bruce M. on 2008-05-24
Search for "HP Printer Driver" in Synaptic Package Manager

---

### Post by HotShotDJ on 2008-05-24
> **phread59 said:**
>  I went to hp's web site and installed the drivers as reccomended.Hi, Mark.

For future reference, the "Windows Way" of going to all the hardware manufacturer's web sites, then downloading and installing their drivers usually doesn't work for Linux.  There are exceptions to this, of course, but they are very rare.  The same holds true for most software.  We don't go to vendor web sites to get our software, we use trusted software repositories.  Again, there are exceptions, but they are rare.

(P.S.  Don't feel dumb.  What you did was follow the way of doing things that you were taught in the Windows World.  I promise you, this is not the last mistake you will make. :)  That is why this forum is here.)

---

### Post by perce on 2008-05-24
try typing the following command on a terminal:

sudo apt-get install --reinstall hplip

if you wonder what it means: 
sudo = execute the command with administrator rights

apt-get install = command for installing programs. Looks scary at first, but is one of the best programs ever.

--reinstall = install the program even if it is already installed

hplip = Linux driver for HP printers

Sure there is a graphic way to do the same, but I'm not familiar with it.

---

### Post by phread59 on 2008-05-25
I got it fixed.  I tried to get back in but for some reason there was a server error coming up.  I had a lot to do last night so I'm just getting back.  I just restarted in recovery mode.  It reinstalled the printer driver just fine and I'm good to go.  I was just trying to get the extra functions of the printer up.  These include the camera card reader and the scanner functions.  I have it done as best as is possible with Linux.  I reinstalled Windows yesterday.  God  I now realize just how stupid and obnoxious Windows is.  I payed for it so I am going to keep it up and running.  I just don't have to use it anymore.

As Hot Shot said I gotta get the Windows mentality pounded out of me.  I'm learning Linux more and more each day.  I've gone so far as to download Fedora 9, 8.04 server and am going to install 8.04 64 bit later on Monday.  I have my dual boot working and have figured out how I'm going to configure the other Distro's in Grub.  I am all set to either have a sucessful multiboot set up or a real nightmare.  But damn the torpedo's and full speed ahead.

Mark Shuman

PS: The Server Edition is for the file server I am setting up on an old Pentium 3 machine I was given.

---

