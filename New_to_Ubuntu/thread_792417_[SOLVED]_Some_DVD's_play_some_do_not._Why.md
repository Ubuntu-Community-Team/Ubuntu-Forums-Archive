---
title: "[SOLVED] Some DVD's play some do not. Why?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by ocean223 on 2008-05-12
How come some DVD's play and others don't in VLC? Example is ELF and WIZARD of OZ do not play. These are legit discs that I own. I've been through every tutorial or thread that's available. They play on my Mac and on a Windows machine.:confused:

---

### Post by SunnyRabbiera on 2008-05-12
Its probably because you dont have libdvdcss, its not installed by default in ubuntu because of various legal issues.
Dont worry though, this is easy to remedy...
you can easily get a package for it with this link:
[here]("http://download.videolan.org/pub/libdvdcss/1.2.9/deb/")

---

### Post by HotShotDJ on 2008-05-12
> **ocean223 said:**
> How come some DVD's play and others don't
Follow the instructions [HERE]("https://help.ubuntu.com/community/Medibuntu") and then install libdvdcss

---

### Post by ocean223 on 2008-05-12
Libdcss2 is installed through the Medibuntu repos. What else could I be in need of? I just tried to play "The Castaway" No go.

---

### Post by SunnyRabbiera on 2008-05-12
are you running the 32 bit version of ubuntu or the 64bit one?

---

### Post by mc4man on 2008-05-12
The one thing those titles may have in common is rce protection. Do you know if the dvd region has been set on your drive? 
Opening vlc from a terminal and posting errors is also useful

---

### Post by ocean223 on 2008-05-12
I'm running 32 bit.
Here is the VLC terminal stuff"
ocean223@ocean223-laptop:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: CASTAWAY
libdvdnav: DVD Serial Number: 2C4D79C9
libdvdnav: DVD Title (Alternative): CASTAWAY
libdvdnav: Unable to find map file '/home/ocean223/.dvdnav/CASTAWAY.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000145
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000048e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000056e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00000586
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000005f2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00002d31
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000155f3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003e6c4a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003e6cba
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003e7a63
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003e7ad3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003e8a04
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003e8a74
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003ea409
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.
Aborted
ocean223@ocean223-laptop:~$

---

### Post by SunnyRabbiera on 2008-05-12
did you try to play these titles in another player?
like totem (movie player)?

---

### Post by mc4man on 2008-05-12
> libdvdnav: Suspected RCE Region Protection!!!
Still need to know about if drive has been set to a region, if you don't know 
install regionset and with a dvd in the drive run regionset. If you see 5 user changes left then drive has never been set. 4 or less and it has been set in which case answer no and post back.

---

### Post by ocean223 on 2008-05-12
Okayfine. Will do.

---

### Post by ocean223 on 2008-05-12
Uh oh! What do I do now? Installed regionset and got this:

ocean223@ocean223-laptop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:

---

### Post by mc4man on 2008-05-12
answer yes, choose region 1
then go into your home dir.(show hidden files), find the .dvdcss folder and delete everything _inside_. then try vlc again.

---

### Post by ocean223 on 2008-05-13
Did all that, still know movie though. Older movies work fine though.

There must be a solution somewhere.........:(

---

### Post by ocean223 on 2008-05-13
Hey I got Elf to play, Castaway gives gibberage.  Must be on to something

---

### Post by mc4man on 2008-05-13
just to double ck. did you delete all the folders in .dvdcss ?

edit post terminal output for castaways

---

### Post by ocean223 on 2008-05-13
Thanks! All seems to be working well' I appears that 



regionset was the culprit. I Had know idea! Thanks Again

---

### Post by mc4man on 2008-05-13
What may come up is some recent titles may not play. They would have a structure protection x protect or something similar. Many can be played using a dvdnav4 patch. Some can't be at all. <I forget> Road - universal release is one. 
Page here - [http://tobias.rautenkranz.ch/libdvdread_ifo.html](http://tobias.rautenkranz.ch/libdvdread_ifo.html)

Easiest method
paste into 3rd. party software in system -> software sources -> add
```
deb http://tobias.rautenkranz.ch/debian stable/
```
run in teminal
```
wget -qO - http://tobias.rautenkranz.ch/tobias.rautenkranz.asc | sudo apt-key add -
```
then ```
sudo apt-get update
``` and 
```
sudo apt-get install libdvdnav-ifo4
```

That'll take care of playback in vlc of anything that actually can be played

---

### Post by ocean223 on 2008-05-13
Many thanks again mc4man, you are da best!!:guitar:

---

### Post by kenfeyl on 2008-06-01
Hi mc4man, you're the bomb but I have a problem. My DVD throws the IFO error shown below when attempting to view it in vlc. I have wiped out .dvdcss/, checked that my region is set to 4 and have libdvdcss installed. I suspect I need the libdvdnav-ifo4 patch, but unfortunately I have amd64 and the patch is only available for powerpc and i386. Any tips?

```
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: CASEFORCHRIST
libdvdnav: DVD Serial Number: 36C44CA0
libdvdnav: DVD Title (Alternative): CASEFORCHRIST
libdvdnav: Unable to find map file '/home/ken/.dvdnav/CASEFORCHRIST.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014b
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000eb2d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000cc103
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000cc13c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00106601
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0010663a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0010dd41
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0010dd7a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00112795
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001127ce
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0011fd8a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0011fdc3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00138b1b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00138b54
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 4
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdnav: ifoOpenVTSI failed - CRASHING!!!
vlc: vm.c:198: ifoOpenNewVTSI: Assertion `0' failed.

```

---

### Post by cariboo on 2008-06-01
If you are actually in region 4 (Oceania; Latin America, Caribbean) then you are going to have to modify your dvd drive to play dvd's from region 1. Here is a guide on how to make your dvd drive region free:

[http://www.dvdexploder.com/compdvd.htm](http://www.dvdexploder.com/compdvd.htm)

Jim

---

