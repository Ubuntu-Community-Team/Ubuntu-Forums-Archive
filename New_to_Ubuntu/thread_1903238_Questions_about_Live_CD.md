---
title: "Questions about Live CD"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by eastwocs on 2012-01-02
What should/shouldn't work? Are there any restrictions on what will work under Live CD?
 
I am about to take the plunge and try 10.04LTS on my oldish Atom Acer Aspire One.
 
Being a total noob, and not having high confidence, I thought I would first play around with the Live CD before taking the plunge and doing a proper install. Live CD loaded fine and I was able to play with the desktop, except for 2 things:
- could not change screen resolution
- wireless did not work
 
For both these items I assume I will just need to find and install the correct drivers.
However, am I right to assume that since the cd is read-only, you can't actually update any drivers in live mode? So I shouldn't really be worried it didn't work out of the box? All the user doco about installation says to "try it out", but is short on details about what to expect.
 
If I connect to wired LAN, should I expect that to work in Live mode out of the box?
 
Sorry for the total noob post - I'm already asking questions and haven't even installed anything yet! Thanks in advance.

---

### Post by hansdown on 2012-01-02
Welcome to the forum, eastwocs.

You are right,to a point.

If you install with a wired connection. the odds are better, that the wireless will work.

This holds true,with other things, as well.

Wired connection is best.

---

### Post by eastwocs on 2012-01-02
Is it important/preferred to install whilst wired?
 
i.e. will it find and install drivers during install? Or do you always need to do that manually afterwards?

---

### Post by hansdown on 2012-01-02
> **eastwocs said:**
> Is it important/preferred to install whilst wired?
 
i.e. will it find and install drivers during install? Or do you always need to do that manually afterwards?

Sorry for the cryptic response, eastwocs.

A wired connection is always best, whether you are using a live disc, or trying to install.

Hope this sounds a little brighter, than my first response.

:)

---

### Post by 3rdalbum on 2012-01-02
Try a more recent Ubuntu, preferably 11.10. The software is more recent and there are more drivers available. More people use the latet Ubuntu so they can give the most accurate and recent instructions.

Atom netbooks work well with Ubuntu 11.10.

---

### Post by I2k4 on 2012-01-02
I'm using on an Acer One, after testing many version via Live USB.  The netbook can boot from USB (need to check / reset BIOS) and you're much better off on Live USB with Persistence than Live CD without Persistence, since you can read/write to the USB drive using the "Persistence" memory and save all your settings between boots.  Use the USB instructions here, but note at Step 2 that the Pendrive installer permits Persistence, which I set for the USB space over 1.5GB:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

I've had absolutely no problem with drivers or wi-fi installing on the USB drive this way, and in fact find the same USB drive can boot the OS on either my Acer netbook or main Dell laptop with no change in functionality.  

The Persistent Live USB is not a full substitute for installing on the hard drive, because in my experience it is slower than a regular full install and tends to "break" after several weeks, but it is a lot better and more configurable than Live CD and a much better test of one version against others.

You'll also see from the drop down menu on the installer that there are lots of lighter weight versions to try on the little netbook.  I quite like Lubuntu, but didn't like its preinstalled software and spent time replacing it - use the trial and error on Live USB to evaluate different interfaces and the available software from several versions of Ubuntu, Lubuntu, Xubuntu, Puppy, Mint, etc. - they all have .ISO downloads that the Pendrive installer will create with Persistence, and shopping distros is half the fun.

---

### Post by Basher101 on 2012-01-02
> **I2k4 said:**
> I'm using on an Acer One, after testing many version via Live USB.  The netbook can boot from USB (need to check / reset BIOS) and you're much better off on Live USB with Persistence than Live CD without Persistence, since you can read/write to the USB drive using the "Persistence" memory and save all your settings between boots.  Use the USB instructions here, but note at Step 2 that the Pendrive installer permits Persistence, which I set for the USB space over 1.5GB:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

I've had absolutely no problem with drivers or wi-fi installing on the USB drive this way, and in fact find the same USB drive can boot the OS on either my Acer netbook or main Dell laptop with no change in functionality.  

The Persistent Live USB is not a full substitute for installing on the hard drive, because in my experience it is slower than a regular full install and tends to "break" after several weeks, but it is a lot better and more configurable than Live CD and a much better test of one version against others.

You'll also see from the drop down menu on the installer that there are lots of lighter weight versions to try on the little netbook.  I quite like Lubuntu, but didn't like its preinstalled software and spent time replacing it - use the trial and error on Live USB to evaluate different interfaces and the available software from several versions of Ubuntu, Lubuntu, Xubuntu, Puppy, Mint, etc. - they all have .ISO downloads that the Pendrive installer will create with Persistence, and shopping distros is half the fun.

+1 Using live USBs and persistence is the safest way imo to NOT mess with your system in any way and still check out linux distros.

---

### Post by Zill on 2012-01-02
> **3rdalbum said:**
> Try a more recent Ubuntu, preferably 11.10. The software is more recent and there are more drivers available. More people use the latet Ubuntu so they can give the most accurate and recent instructions...
10.04 (Lucid) is the current LTS release though and [will be supported until April 2013]("https://wiki.ubuntu.com/Releases").

As many of us are still happily using 10.04 the OP should be aware that plenty of support for this release will continue to be available. :-)

---

### Post by grahammechanical on 2012-01-02
Ubuntu does not use proprietary software on the live CD neither does it install such software. We have to install it ourselves if we chose to use it.

You may need proprietary drivers to get the full use of your video card and to get wireless working. It all depends on the hardware that you have.

For example, the other year I was able to run the live CD on my older sister's Vista laptop and connect wirelessly to her router without any problem. It might have been 10.04 or 10.10 that I was using - cannot now remember. If your wireless adapter was not recognised by the Live CD you may need a driver. Check out this link and prepare yourself.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Of course one of the reasons for using the latest version of Ubuntu is that it will have the latest drivers in the Linux kernel and that just might include one for your wireless and a better open source video driver.  At least try 11.10 as a live CD. It is better to have the OS younger than the hardware.

Another point, it is true that support for 10.04 desktop lasts until April 2013 but so does support for 11.10.

You could try to install the drivers while in the Live CD mode. The OS runs in memory so you might succeed but any settings will not be saved for the next session. At least you will find out how difficult it will be to get wireless working.

The reason why it is recommended that the computer be connected to the Internet during the installation is so that the install process can update the OS with the latest security fixes and libraries as part of the install. Otherwise, you will have to do it after the install is complete. It makes the whole process seem quicker.

Regards.

---

### Post by morhin on 2012-01-02
I'm on an Acer Aspire 5250. Got it a couple of months ago so I could play with linux. 

I started with Mepis but never could get it to connect. 
I did get PCLinuxOS to connect but had another issue and went to the library for help and found ***Ubuntu for Non-geeks by Rickford Grant and Phil Bull.***
It came with a live cd so I gave it a try and it has been me and the Lucid Lynx (version 10.04) ever since.
I wiped out windows 7 and am running 10.04 full time.
I've still got a lot to learn but the book I mentioned has helped me tremendously as I'm a new noobie.
I just checked and it explains about hooking up wirelessly. I'm sure some other books do too, but I've found this one is great to get started. It does talk a bit about setting up older systems.

By the way.... with my newer laptop I haven't had to do a thing but turn it on and follow the setup procedure Now it seems to find everything in range.

morhin

my wife tells me I'm wrong so often I'm thinking about becoming a weatherman

---

### Post by waynefoutz on 2012-01-02
My suggestion if you are new and want to go wth 10.04, try the "SuperOS" Ubuntu respin. It's Ubuntu, but on a DVD instead of CD. All the wireless drivers are on the disk, so you won't have to plug a hard wire into a router to get your wireless working. Flash, Java, and all he multimedia codecs are installed out of the box. It's a great time saver. They haven't come out with an 11.10 version yet, but the 10.04 iso works fantastic.

[http://hacktolive.org/wiki/Super_OS#Download]("http://hacktolive.org/wiki/Super_OS#Download")

---

