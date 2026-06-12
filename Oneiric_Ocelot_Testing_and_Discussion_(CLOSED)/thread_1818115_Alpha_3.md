---
title: "Alpha 3"
date: 2011-08-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-08-04
Any idea when it will be available for download?

---

### Post by MacUntu on 2011-08-04
When it's announced by Kate Stewart on the [ubuntu-devel-announce mailing list](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2011-August/thread.html).

---

### Post by madjr on 2011-08-04
i hate waiting lol

---

### Post by aka120 on 2011-08-04
> **madjr said:**
> i hate waiting lol

Wait no more :D
[http://cdimage.ubuntu.com/releases/oneiric/alpha-3/](http://cdimage.ubuntu.com/releases/oneiric/alpha-3/)

---

### Post by sgage on 2011-08-04
> **aka120 said:**
> Wait no more :D
[http://cdimage.ubuntu.com/releases/oneiric/alpha-3/](http://cdimage.ubuntu.com/releases/oneiric/alpha-3/)

Hurrah!

---

### Post by fjgaude on 2011-08-04
Well, Alpha3 is released but I've tried two different ways to get it to install on my Dell 10n, dd and Startup Disk Creator. Neither got me to an install GUI.

Any ideas?

---

### Post by cariboo on 2011-08-04
A few more details would help, where does it stop in the process?

---

### Post by fjgaude on 2011-08-04
It gets to saying Welcome to Ubuntu and then to a command line. Not sure what to do next. I tried startx but I knew wouldn't work. Install?

---

### Post by jerrylamos on 2011-08-04
Alpha 3 "No Screens Found".

It thinks lightdm has started but there is no desktop.

Tried sudo apt-get update, sudo apt-get upgrade and there were 500 packages to be upgraded!! and 15 held back!!  O.K., tried it, no luck.

Tried xorg.conf with vesa no screens found.

Tried startx no screens found.

Tried ubuntu-bug xorg but of course everything has to be running including X to file the report.  If it was all running I wouldn't have a need for ubuntu-bug.  I've tried saving the report and sending it to launchpad, but the people on launchpad said they couldn't use the report.  Catch 22.

This is ati radeon Xpress 200 running Alpha 2.

Alpha 3, dead on arrival.

Jerry

---

### Post by mc4man on 2011-08-04
> **jerrylamos said:**
> 

Tried sudo apt-get update, sudo apt-get upgrade and there were 500 packages to be upgraded!! and 15 held back!!  O.K., tried it, no luck.

Jerry

Seems quite suspect for an A3 iso if that's what you're actually  using 
(only 27 here, nothing held

---

### Post by fjgaude on 2011-08-04
I was attempting a fresh install of Alpha 3 and couldn't get to a desktop... just a command line. Seemed like it was ready for the try/install screen but never made it.

Any ideas?

---

### Post by cariboo on 2011-08-05
Did you try setting nomodeset?

---

### Post by fjgaude on 2011-08-05
No, but do tell me how to do that.

---

### Post by drs305 on 2011-08-05
> **fjgaude said:**
> No, but do tell me how to do that.

You should be able to invoke the 'nomodeset' option during a LiveCD boot by pressing F6 to display various options, although I've not tried it on the Oneiric CD.

Here is the community doc:
[LiveCDBootOptions]("https://help.ubuntu.com/community/LiveCDBootOptions")
Reference the "Changing the CD's Default Boot Options" section. 

No guarantee that 'nomodeset' is the answer to your problems, but this will tell you how to add it or other kernel switches to the CD boot options.

---

### Post by jerrylamos on 2011-08-05
Alpha 3 Dead On Arrival.

I've tried a bunch of tricks but still no desktop at all.

Now if I do a startx, I do get a GUI which says there is no gnome, but only gives me the choice of Logout, which works.  Back to square one.

ati radeon Xpress 200 runs most everything on Alpha 2, only command line on Alpha 3.  That's even with the August 5 daily build.

Jerry

---

### Post by fjgaude on 2011-08-05
I gave up on Alpha 3 as I am now working with my Dell 10n and the new video driver, EMGD... it works fine with Alpha 2 updated for today, in Unity 2D mode and almost in 3D, close... I'm sure Luca and Sista will get it there soon. <smile>

---

### Post by VinDSL on 2011-08-05
Don't mean to muddy the waters, but...

I updated my Live USB Image to Alpha 3 this morning, booted it, looked around, ran a few tests from CLI - and couldn't see any difference between it and my fully patched and updated Alpha 2 install.

Are we talking about fresh A3 installs being DOA - images not booting - wash, rinse and restyle failing - or what?!?!?

I didn't bother installing A3 but the image booted/ran just fine.

Any ISO testers following this thread?  I can't imagine this slipping by them.

---

### Post by fjgaude on 2011-08-05
The lack in Alpha 3 likely has to do with the video aspects. Jerry and I have quiet different machines. I run Intel Poulsbo mini and she is with an Ati. The drivers in Alpha 2 worked for both of us but not in the .iso Alpha 3. That's the way it is.

---

### Post by jerrylamos on 2011-08-06
> **fjgaude said:**
> The lack in Alpha 3 likely has to do with the video aspects. Jerry and I have quiet different machines. I run Intel Poulsbo mini and she is with an Ati. The drivers in Alpha 2 worked for both of us but not in the .iso Alpha 3. That's the way it is.

Lightdm downlevel is the culprit for me. On live Alpha 3, real hardware, I tried: 
sudo apt-get install lightdm
nothing updated. No help.

With command line I noticed /etc/apt/sources.list was only a few lines long.  Whoa, it's usually a couple pages long!

I copied in sources.list from Alpha 2:
sudo mkdir /media/temp
sudo mount /dev/sdb8 /media/temp
sudo cp /media/temp/etc/apt/sources.list /etc/apt/sources.list 
sudo apt-get update 
sudo apt-get install lightdm
Actually did some updates.

Voila!  desktop came up!
Now ps2 mouse didn't move cursor, so forums to the rescue, plugged in a USB mouse.  I don't know the package for ps2 mouse which runs fine on Alpha 2 and previous levels of Ubuntu.

Briefly running Alpha 3 pretty rough.  I suspect a whole lot more packages in Alpha 3 are way way down level.  Very very strange in a brand new build.  No way I'm going to install that mess.

Jerry

---

### Post by fjgaude on 2011-08-07
I ran the latest daily build as grub iso without issue... it looked good, showing all the other partitions on the box, x64, cool! Fast! It's getting there but the live version of Alpha 3 is something else.

I have the updated Unity 2D running fine on my mini 10 using EMGD driver and Luca's script. We wait and see how things go at release time in mid-October.

---

### Post by jerrylamos on 2011-08-08
> **jerrylamos said:**
> Alpha 3 Dead On Arrival.

I've tried a bunch of tricks but still no desktop at all.

Now if I do a startx, I do get a GUI which says there is no gnome, but only gives me the choice of Logout, which works.  Back to square one.

ati radeon Xpress 200 runs most everything on Alpha 2, only command line on Alpha 3.  That's even with the August 5 daily build.

Jerry

Found the problem, installed & up and running.

I've got two hard drives, 

An IDE that boots and the Narwhal and LucidLTS installations on the IDE calls /dev/sda.

A SATA that is 2nd drive and also has a Meerkat partition on it usually used for TV viewer.

Now Oneiric installation also on the IDE calls the boot IDE /dev/sdb instead of /dev/sda like it should.  

No idea why.  Wound up causing Live Ubuntu and me no end of confusion.

?

Jerry

---

### Post by x-shaney-x on 2011-08-08
Alpha 3 (both an upgraded alpha 2 and a fresh 3 install) had been working pretty well.
A few minor bugs but nothing too major until now...

In unity 3D, I have discovered I cannot use 3 finger touchpad taps as middle-clicks, thanks to the evil compiz and have been unable to find a workaround.
That alone is the show stopper as far as unity 3D is concerned.

Unity 2D DOES allow me to use the touchpad this way but has a couple of show stoppers of it's own:
I can't make the launcher icons any smaller and I use a lot of launchers.
Indicator power does not work in unity 2D for some reason.
And finally, not such a big deal but the options to keep dash maximized don't work.

---

