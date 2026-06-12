---
title: "Should/can I run some distro of linux?"
date: 2014-10-18
forum: New to Ubuntu
---

### Post by dogfiresmith on 2014-10-18
Maybe I went into this the wrong way. Installing Ubuntu  14.04 and assuming everything would work. (See my other
threads for those discussions.) Let me tell you what I have,what I want, and what I don't want.  And then people can
tell me if I should/can run linux.

Have: Lenovo R61, 4Megs of RAM

Want: Good looking desktop (lubuntu is an example of one I would consider not good looking), everything works after the
install.  Connect to the internet, to the wireless printer, to the wireless mouse, to the external harddrive, ...

Don't want: Needing to know about chipsets, video cards/drivers, any drivers, doing things on the command line.

If at this point you are going to recommend I do run linux please give me details, a web page with instructions would be even better.

Thanks

---

### Post by QIII on 2014-10-18
In a world where OEMs starve if they do not make sure their hardware does not work with Windows, they spend all of their time making sure it does or they starve.'

Not so with Linux.  Linux often gets short shrift.

Many people thing that Windows supports their hardware.  It is, in fact, the other way around -- Microsoft does absolutely nothing at all to make sure the drivers for XYZ Corp's video driver works.  They don't care.  It's XYZ Corp's job to make sure their driver is compatible with Windows.

That is how the world works.

In the Linux world, we are often left to our own devices.  If the OEMs don't make sure their drivers work with Linux, we have to find work arounds and kludges.  People spend a lot of unpaid time writing open source drivers for devices for which the OEMs do not provide design information.  They peer as deeply as they can into black boxes and make educated guesses.  Sometimes things do not work well.

If you are expecting Linux to be a drop-in replacement for Windows, you will be disappointed.  If you are willing to roll up your sleeves, you will find great satisfaction.  You will need to learn about your hardware and you will sometimes need to use the terminal.  That is the way it is.

This is what life is like in a world that bends to the will of Microsoft.

---

### Post by sammiev on 2014-10-18
It seems command equipment works right out of the box except some video cards and wireless modems. I'm one of the lucky folks where I have 5 laptops that all worked straighted out of the box from the day I bought them. Wish you luck with yours. :popcorn:

---

### Post by Vladlenin5000 on 2014-10-18
With most Lenovo models everything usually works out of the box as well but the R61 has been sold with different graphics cards/chips, some good, others not so much. And perhaps half of a dozen of different WiFi cards, again, some supported out of the box, other not quite...

(This has been commented before a few times already)

---

### Post by fantab on 2014-10-18
> If you are expecting Linux to be a drop-in replacement for Windows, you  will be disappointed.  If you are willing to roll up your sleeves, you  will find great satisfaction.  You will need to learn about your  hardware and you will sometimes need to use the terminal.  That is the  way it is.

+1.

[Bodhilinux]("http://www.bodhilinux.com/") is better looking IMO, give it a try if you want something similar to lubuntu in performance.

---

### Post by vasa1 on 2014-10-18
[Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by Rob Sayer on 2014-10-18
I wouldn't recommend any other distro than ubuntu for a linux novice.  As you already seem to have figured out, linux takes more config generally than windows.  

Though it's not fair to compare ubuntu to pre installed windows.  Anyone who's installed windows on a computer can tell you that there's going to be some config there too.  E.g. those windows install discs only come with generic video drivers.

A very good idea before install is to go into windows' system information and find out what your hardware adapters actually are.  Then search "ubuntu [whatever]".  Here and askubuntu.org are the best places for info generally.  Many blogs are out of date or simply aren't written by someone all that knowledgeable in the first place.

The best thing would be to just download the install live CD for all ubuntu DE versions.  Do the md5sum check, burn (preferably to USB stick for speed), boot.  Select Try Ubuntu and see what you think.

Unity is considered the 'default' DE.  I tried it but didn't like it.  YMMV.  It's not that fast though ... it needs 3D hardware acceleration just to run the desktop.  You'd need the same sort of power you need for windows 7 or 8.

KDE is heavy as well but you can speed it up a lot by proper setup, which you can't do with unity.  That's what I mostly use.  You can configure it like crazy, almost to a fault.

XFCE is what I'm using on my 1Gb netbook.  It's pretty lightweight and reasonably fast, and it's pretty easy to config.

LXDE is the lightest and fastest DE, though it's indeed the ugliest.  There's no free lunch.  It's *way* faster than the others though.  I've had lubuntu on my netbook but frankly I had a lot of problems with 14.04.  Frankly it was bug ridden.  Hopefully 14.04.1 is better (14.04.1 or 14.04.2 isn't really different from 14.04 in ubuntu, it just has more bug fixes and needs less updating).  

Actually LXDE is so much faster on my netbook I've downloaded a copy of 14.04.1 but haven't installed it yet.  The thing is, my netbook runs noticeably cooler in lubuntu.  And that's very tempting.

---

### Post by buzzingrobot on 2014-10-18
> **dogfiresmith said:**
> 

Have: Lenovo R61, 4Megs of RAM

Want: Good looking desktop (lubuntu is an example of one I would consider not good looking), everything works after the
install.  Connect to the internet, to the wireless printer, to the wireless mouse, to the external harddrive, ...

Don't want: Needing to know about chipsets, video cards/drivers, any drivers, doing things on the command line.




Some wifi card vendors don't provide Linux drivers, and they don't release enough information about their cards to allow drivers to be written by someone else. 

Using the command line is actually not required to use a functioning Linux distribution. Advice given here and elsewhere on the web invariably includes command line use because it's much simpler to enter a line of text than correctly lead someone through a series of mouse clicks on a GUI interface. Exceptions exist, especially if something breaks, but use of the command line in Linux in that scenario is comparable to registry editing in Windows.  Most Windows users have an inordinate fear of using the command line. 

The best and safest way to experiment is to download, boot and run an install image in the 'try me' to see if all your hardware is recognized and works.  If it does not, post specific questions here.

I've installed Windows only a very few times in the last several years, on Lenovo hardware. Invariably, that meant a post-install trip to a Lenovo site to download and install appropriate drivers.  In the case of Windows 7, I needed to previously download and burn the right ethernet driver to a USB stick because Windows 7 doesn't include the driver in its install image. So, it's not always accurate to say Windows eliminates the headache of tracking down drivers or that it works out of the box, even on thoroughly mainstream hardware like Lenovo.

---

### Post by yancek on 2014-10-18
> Have: Lenovo R61, 4Megs of RAM

That has to be a typo if the computer was manufactured in the last 30 years.

---

### Post by grahammechanical on 2014-10-18
After reading your first post, my advice would be to stick with what came on the machine when it was first purchased.

In Linux we have choice. There are many distributions of LInux with different desktop environments and user interfaces. I am sure that they all come as downloadable ISO images that can be burned to a DVD or a USB memory stick and can then run as a live session without making any changes to the machine. Try out a few live sessions and install the one you like. If you accept someone else's recommendation, you will not be satisfied.

---

### Post by Mark Phelps on 2014-10-18
Using ANY Linux distro is going to involve some learning -- as was already pointed out, Linux is not a drop-in replacement for Windows.

Only YOU can know what UI you like -- so, only YOU can try out the different distros and desktops to see what you like.  A good website to go to download different Linux distros is distrowatch.com.

While knowing about chipsets is not a necessity to use Linux distros, if you end up having to install video drivers, you will at least need to know what video chipset you have on the machine in order to download the proper drivers.

As to command line usage, that lessens more all the time -- but there will always be cases where using a simple command will yield needed information easier than wading through a sea of menus and mouse clicks.

IF you're willing to expend some effort, then you're welcome to stay; but if you want a "shove the disk in the drive, click once any you're done" environment, then using Linux is not the right path for you to take.

---

### Post by richaustin on 2014-10-18
Hi

I've read some things on this thread that I think are pretty negative in terms of helping someone adapt to Linux when they are coming from Windows. It is certainly true that in some respects Linux is, or at least seems to be, more complex than Windows. However, that in no way makes it impossible for a person who just wants it to darn well work! I just want a distro to work and I've been a professional in IT for 30 years!

First off, a distro is what you will generally see different flavours, or brands, of Linux called. In the background it is all the same but they each have their own way of working. This is, trust me, a good thing because it gives you choice. However, a user coming from Windows, which is, well, just Windows, is not going to get the concept straightaway and I can see how it is bewildering to say the least. I found it very confusing when I first started off with Linux.

A real problem is what do you recommend to a new user coming from Windows. It isn't easy to say, and you will get people who are anti-this, pro-that, and they aren't really looking at what you require. As has been mentioned in this thread as a great choice is Ubuntu, which to be honest isn't a bad choice at all. It tends to "just work", you can make it look great (personally I hate the purple colour scheme but it's better than the dreadful brown it used to be - very marginally) but you can fairly easily change it. Given that you said you think Ubuntu is ugly, although I think you should look at how you can change it to suit you (can't do that in Windows, but you sure as hell can in Linux) I would recommend PCLinuxOS.

I know that suggestion is likely to get me flamed by various people for suggesting it but it is a solid distro and it works much like Windows. Things are where you expect them to be such as minimise, maximise buttons, a Start button. Things like music and video tend to work well and it is supported by a good community.

I hope you you haven't been put off trying Linux, it really is a great system and a joy to use. If you stick with it, ask on the forum's for help, try things out, you will end up with a system that works, and looks, exactly how you want it. You willl never have that with Windows, there are always limits that Microsoft impose, whereas in Linux there are no limits and there isn't a one size fits all, tough if you don't like it, solution.

Richard

---

### Post by newb85 on 2014-10-18
Although it is not an official variant of Ubuntu (and thus not supported on this site other than the other distro section), Linux Mint can be a great place for new users to start.  It has more drivers, codecs, etc. automatically installed.  It is a direct fork of Ubuntu, with each version of Mint based on the latest version of Ubuntu (and released about a month later).  Under-the-hood, everything works the same, but the Desktop Environment (the graphical part of the OS) and some of the default applications are different.  It uses the Ubuntu repositories, so the software selection will be the same.  Most support questions will still be applicable here.

One thing that has not been pointed out yet in this thread is that if you choose the right distro, you will have great community support at your fingertips.  (This won't really apply to the more obscure distros.)

---

### Post by sammiev on 2014-10-18
> **richaustin said:**
> Hi

I've read some things on this thread that I think are pretty negative in terms of helping someone adapt to Linux when they are coming from Windows. It is certainly true that in some respects Linux is, or at least seems to be, more complex than Windows. However, that in no way makes it impossible for a person who just wants it to darn well work! I just want a distro to work and I've been a professional in IT for 30 years!

First off, a distro is what you will generally see different flavours, or brands, of Linux called. In the background it is all the same but they each have their own way of working. This is, trust me, a good thing because it gives you choice. However, a user coming from Windows, which is, well, just Windows, is not going to get the concept straightaway and I can see how it is bewildering to say the least. I found it very confusing when I first started off with Linux.

A real problem is what do you recommend to a new user coming from Windows. It isn't easy to say, and you will get people who are anti-this, pro-that, and they aren't really looking at what you require. As has been mentioned in this thread as a great choice is Ubuntu, which to be honest isn't a bad choice at all. It tends to "just work", you can make it look great (personally I hate the purple colour scheme but it's better than the dreadful brown it used to be - very marginally) but you can fairly easily change it. Given that you said you think Ubuntu is ugly, although I think you should look at how you can change it to suit you (can't do that in Windows, but you sure as hell can in Linux) I would recommend PCLinuxOS.

I know that suggestion is likely to get me flamed by various people for suggesting it but it is a solid distro and it works much like Windows. Things are where you expect them to be such as minimise, maximise buttons, a Start button. Things like music and video tend to work well and it is supported by a good community.

I hope you you haven't been put off trying Linux, it really is a great system and a joy to use. If you stick with it, ask on the forum's for help, try things out, you will end up with a system that works, and looks, exactly how you want it. You willl never have that with Windows, there are always limits that Microsoft impose, whereas in Linux there are no limits and there isn't a one size fits all, tough if you don't like it, solution.

Richard

Great post to say the least and we are here to help, but to just work right of the box is hit or miss. We are here to help but he/she must be willing to help us and be prepared to do some leg work. I do wish the person the best of luck. :)

---

### Post by Topsiho on 2014-10-18
[I]"Don't want: Needing to know about chipsets, video cards/drivers, any drivers, doing things on the command line.
If at this point you are going to recommend I do run linux please give me details, a web page with instructions would be even better."
[/I]

I don't recommend you to use any Linux. If you want to use Linux (or any other) you need to put some effort into it to only just use it.
If you use Linux you're profiting from the work of thousands of people who have put, and are still putting, a lot of work into it ... and love to do so for people who show some appreciation for this.

Sorry for this.

Topsiho

---

