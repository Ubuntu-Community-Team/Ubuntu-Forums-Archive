---
title: "video dvd play??"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by bkamalnivas on 2008-06-11
unable to play my video dvds...
(cud be a too basic qn to answer...pls help)

---

### Post by ukripper on 2008-06-11
> **bkamalnivas said:**
> unable to play my video dvds...
(cud be a too basic qn to answer...pls help)

check this link
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by SunnyRabbiera on 2008-06-11
right you need to install the DVD playback stuff on your own, but its easy to do.

---

### Post by Tom--d on 2008-06-11
Download this [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/)

and install. (double click it) and then (I think you need to reboot) then you will be able to play dvds :D!!

---

### Post by Sinkingships7 on 2008-06-11
This is the command you need to install DVD playback:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
Post back if you have any problems.

---

### Post by bkamalnivas on 2008-06-15
installed from links above...
drive shows no files..??
any command to be used or something of that sort??

---

### Post by subaruwrc01 on 2008-06-15
[https://help.ubuntu.com/8.04/musicvideophotos/C/video.html](https://help.ubuntu.com/8.04/musicvideophotos/C/video.html)

However the file server for libdvdcss2 is currently down for maintenance so you'll have to wait a bit.

---

### Post by bkamalnivas on 2008-06-19
tried all the above...unable to play both a video dvd and also a data dvd 
containing .wmv ,.mp4 files that i burnt in ubuntu - diaplays "could not read from source"  
(able to read them in XP)

---

### Post by bromix on 2008-06-19
These two commands worked perfect for me today.
> sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3

then

> sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by ukripper on 2008-06-19
> **bkamalnivas said:**
> tried all the above...unable to play both a video dvd and also a data dvd 
containing .wmv ,.mp4 files that i burnt in ubuntu - diaplays "could not read from source"  
(able to read them in XP)

You might want set region as some dvd player has region codes.

in terminal type :
```
sudo apt-get install regionset
```

and then use ```
regionset 
```

to select your region.

---

### Post by bkamalnivas on 2008-06-20
i ve installed the following:

libdvdcss2

libdvdcss2-dev

libdvdread3

-also region has been set...

still unable to read .avi and .wmv files (burnt in ubuntu) from DVD

---

### Post by Tom--d on 2008-06-20
Install all the gstreamer codecs from Add/remove and use the totem gstreamer backend. 

It works for me (with the libdvdcss2 installed)

---

### Post by bkamalnivas on 2008-06-20
i ve installed it already !!

---

### Post by Tom--d on 2008-06-20
> **bkamalnivas said:**
> i ve installed it already !!

But in the screenshot you provided. you are using xine backend. 
Try the gstreamer. Its different.

---

### Post by bkamalnivas on 2008-06-20
> **Tom--d said:**
> But in the screenshot you provided. you are using xine backend. 
Try the gstreamer. Its different.

i ve tried that too..

just cant figure out the problem (unable to copy the contents of dvd... )

---

### Post by Tom--d on 2008-06-20
> **bkamalnivas said:**
> i ve tried that too..

just cant figure out the problem (unable to copy the contents of dvd... )

Post the screen again but while looking at the details.

---

### Post by bkamalnivas on 2008-06-20
> **Tom--d said:**
> Post the screen again but while looking at the details.

it displays "cud not be copied..."
and some "input/output error"

---

### Post by sydbat on 2008-06-20
Which version of Ubuntu are you running - 32-bit or 64-bit? I run both on different machines and have found lots of problems trying to get the DVD working on the 64-bit machine (will play a bit, won't find drive next time, etc). DVD's play without flaws on the 32-bit box.

---

### Post by bkamalnivas on 2008-06-20
> **sydbat said:**
> Which version of Ubuntu are you running - 32-bit or 64-bit? I run both on different machines and have found lots of problems trying to get the DVD working on the 64-bit machine (will play a bit, won't find drive next time, etc). DVD's play without flaws on the 32-bit box.

Ubuntu 8.04 on 64bit

---

### Post by sydbat on 2008-06-20
I just figured out my problem is a hardware issue. DVD's will not play any better in XP (same exact problems), but when I switch out the DVDRW and put the DVDROM from the 32-bit machine, everything works properly. DOH!

Do you have another DVD player you can install? If so, try it and see if that works.

---

