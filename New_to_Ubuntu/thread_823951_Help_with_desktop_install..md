---
title: "Help with desktop install."
date: 2008-06-09
forum: New to Ubuntu
---

### Post by patrick0605 on 2008-06-09
I'm trying to isntall 8.04 on my desktop machine, in hopes of turning it into a DVR.  Anyway, it's proving to be more difficult than when I did it on my laptop.

I'm running the live CD, and no matter which way I try, either running from the CD or actually installing it on the HD, I can't get it to work.

After the splash screen does its thing, it'll start the boost process.  It'll hang on "running local boot scripts" even though it says [OK], it will try this three times before the screen becomes garbled with what looks like the Ubuntu splash screen again.  After this, I get a "Low graphics mode" warning.  I try to configure my monitor, which isn't listed, and my video card, but it accomplishes nothing.

After this, the resolution is so off that I cannot see what I'm typing so it gets a bit difficult.

I hit alt+f1 and bring up the command line, and here is where I have no idea what needs to be done.  When I installed 7.10 on my laptop, it was so simple no problems what so ever, this is posing to be a real pain in the ***.


If it matters, system specs:

AMD 3700+ clawhammer S754
Epox nForce 250gb mobo
1GB Mushkin DDR400 ram
ATi X800XT PE VGA card.
Seagate 500GB Sata
WD 36GB Raptor
WD 200GB IDE drive

Thanks in advance, this is really starting to annoy me.

---

### Post by quelx on 2008-06-09
try using the **alternate** install CD.

---

### Post by Rocket2DMn on 2008-06-09
You can obtain the alternate install cd from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom.  The alternate install cd uses a text based installer rather than a live session, but it is still intuitive and easy to use.

---

### Post by inportb on 2008-06-09
> **quelx said:**
> try using the **alternate** install CD.

But of course, that would not fix the video issue, which I'm pretty sure is what's going on here. ATi's pretty messed up.

See if you can fix the video drivers on the live session. If you can, just do an alternative install and fix it the same way:

1) get the fglrx driver:
sudo apt-get install xorg-driver-fglrx

2) open up /etc/X11/xorg.conf as superuser and modify your "Device" section to say:
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fglrx"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
EndSection

3) start the X server:
startx

---

### Post by Rocket2DMn on 2008-06-09
A good number of video cards just don't work with the LiveCD, but usually work after installation (they can only fit so much into the Live session on the cd).  Using the alternate install disc allows you to skip the graphics stuff which will normally work OK after installing (even if they didn't work on the LiveCD).  If for some reason they don't work after install, it is much easier to troubleshoot then rather than on the LiveCD.

---

### Post by patrick0605 on 2008-06-09
I'm going to try using the alternative CD now and I'll report back with my findings.

I love this forum, both times I had issues with my installs, within minutes someone was there to offer a helping hand.

---

### Post by inportb on 2008-06-09
> **Rocket2DMn said:**
> A good number of video cards just don't work with the LiveCD, but usually work after installation (they can only fit so much into the Live session on the cd).

Of course, we all know that the bulk of the software lives online. As long as you have enough RAM, there's nothing wrong with tweaking the live session (installing the video driver and stuff). It'll give you a reasonable estimate of how responsive your system would be to tweaking, post-installation.

---

### Post by patrick0605 on 2008-06-10
Well, I didn't really figure out my problem, but I guess 8.04 doesn't like my desktop, but 7.10 works just fine.  

I'm actually installing it now as I'm typing this.

Thanks for your help guys.

---

### Post by patrick0605 on 2008-06-11
Now I have another question.

I got Gutsy running just fine right now...still trying to rearrange things how I like them.  Anyway, my question is, if upgrade to Hardy through the update manager, will I run into the issues before when I tried installing it off the LiveCD, or will I be ok?

Thanks in advance.

---

### Post by Rocket2DMn on 2008-06-11
The only way to really know is to try, though you *should* be ok.  Some people have graphics troubles in Hardy, but not as many as with Gutsy and other previous versions.  The LiveCD just isn't a good indicator of whether your card will work with the installation since most cards that don't work with the LiveCD do work after installing.

---

### Post by patrick0605 on 2008-06-11
Ok, thanks.  I'll try it out and see what happens.  Worst comes to worst, I stick with 7.10 for a while.

---

