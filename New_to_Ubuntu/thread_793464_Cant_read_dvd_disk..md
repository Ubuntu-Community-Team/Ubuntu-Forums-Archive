---
title: "Cant read dvd disk."
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Dissident85 on 2008-05-13
Hi all, i have a dvd that i want to watch on my laptop but i think it must have some form of protection on it.. it works in dvd players, but not in computers... i have tried in ubuntu, and windows and i get the same thing. 

any ideas on how i may be able to play this movie on my comp???

---

### Post by macaholic on 2008-05-13
Do any other DVDs work in either of the operating systems?

---

### Post by Dissident85 on 2008-05-13
> **macaholic said:**
> Do any other DVDs work in either of the operating systems?

yes, i have tried a few different ones...

---

### Post by Dissident85 on 2008-05-13
I just tried it on a xp media center pc and it worked. could i be missing a codec? do some dvds use different codecs?

---

### Post by SunnyRabbiera on 2008-05-13
hmm, is this something you got from a store or something someone burnt for you?

---

### Post by Dissident85 on 2008-05-13
> **SunnyRabbiera said:**
> hmm, is this something you got from a store or something someone burnt for you?

Its Underbelly(tv series) which i purchased from a store

---

### Post by SunnyRabbiera on 2008-05-13
and you did install libdvdcss in ubuntu right?
are you sure its in the right region?

---

### Post by Dissident85 on 2008-05-13
> **SunnyRabbiera said:**
> and you did install libdvdcss in ubuntu right?
are you sure its in the right region?

yes i have libdvdcss2 installed. and i didnt think regions mattered with computers, i have never had any problems with that before.. 

but i know the dvd is for australia, how do i check what my computer is set to? if there is such a setting?

---

### Post by Dissident85 on 2008-05-13
Don't know if this will help, but when i tried to make a backup copy of the dvd i got the fallowing error
```
Command exits with failure code:
Command: execflow tccat -i /dev/scd0 -T 1 | dvdrip-progress -m 25 -i 1 | head -c 25m > /tmp/dvdrip.audioprobe.22354.vob && tcprobe -i /tmp/dvdrip.audioprobe.22354.vob && echo EXECFLOW_OK; rm -f /tmp/dvdrip.audioprobe.22354.vob

Output: libdvdread: Invalid title IFO (VTS_01_0.IFO).
libdvdread: Invalid title IFO (VTS_01_0.IFO).
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00017b97)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00017c02)!!
Read failed for block 0
25/25
[fileinfo.c:118] file read error: Success
[tcprobe] unknown file type
[tcprobe] filetype/codec not yet supported by 'transcode'
```

---

### Post by mc4man on 2008-05-13
> could i be missing a codec? do some dvds use different codecs?
probably not and no
Considering the history and very limited release it wouldn't be surprising if it had some real garbage structure protection. You could run vlc from a terminal and post output. Seeing as though it plays on xp it would be interesting (and narrow the possibilities) to see if you get playback in xp on an open source player vs. the closed source your probably using. Vlc would work or MPC also.

just read latest post ck. here also
[http://ubuntuforums.org/showthread.php?p=4946867#post4946867](http://ubuntuforums.org/showthread.php?p=4946867#post4946867)
stuff about regions earlier in thread

---

### Post by Dissident85 on 2008-05-13
ok, so i tried to open it in open vlc
and here is what i got... 
```
VLC media player 0.8.6e Janus
libdvdread: Invalid title IFO (VTS_01_0.IFO).
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00017b97)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00017c02)!!
[00000287] dvdread demuxer error: read failed for block 0
[00000280] main playlist: nothing to play
```

---

### Post by mc4man on 2008-05-14
I'd try the dvdnav patch, you could ck. region though doesn't seem to be an issue. If that doesn't work and you _can't playback with vlc in xp_, than it's likely you won't in linux. (possible exception of lindvd) If you can then than a solution may be possible.

edit: do ck. the region - some structure protections combined with no region or region mismatch might cause above error (your region 4 i assume)

---

### Post by Dissident85 on 2008-05-14
> **mc4man said:**
> I'd try the dvdnav patch, you could ck. region though doesn't seem to be an issue. If that doesn't work and you _can't playback with vlc in xp_, than it's likely you won't in linux. (possible exception of lindvd) If you can then than a solution may be possible.

i have libdvdnav4 installed. what is the dvdnav patch? 

i also tried playing the dvd in vlc in windows xp, and it didnt work. just got the men....


> **mc4man said:**
> 
edit: do ck. the region - some structure protections combined with no region or region mismatch might cause above error (your region 4 i assume)
ay??? :S

---

### Post by mc4man on 2008-05-14
> what is the dvdnav patch
it doing what's in the link from 2 posts back
[http://ubuntuforums.org/showthread.php?p=4946867#post4946867](http://ubuntuforums.org/showthread.php?p=4946867#post4946867)
Just follow the instr.exactly.  After installing dvdnav4-ifo (the 'patch') go into home dir., find .dvdcss and delete the folder for Underbelly. (if you can't find the right folder then delete all the folders inside .dvdcss, don't worry they are recreated the next time you play any particular title)
If it doesn't work post back and there's one other way.

---

### Post by Dissident85 on 2008-05-14
> **mc4man said:**
> it doing what's in the link from 2 posts back
[http://ubuntuforums.org/showthread.php?p=4946867#post4946867](http://ubuntuforums.org/showthread.php?p=4946867#post4946867)
Just follow the instr.exactly.  After installing dvdnav4-ifo (the 'patch') go into home dir., find .dvdcss and delete the folder for Underbelly. (if you can't find the right folder then delete all the folders inside .dvdcss, don't worry they are recreated the next time you play any particular title)
If it doesn't work post back and there's one other way.

it didnt work. same thing
```
VLC media player 0.8.6e Janus
libdvdread: Invalid title IFO (VTS_01_0.IFO).
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00017b97)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00017c02)!!
[00000287] dvdread demuxer error: read failed for block 0
[00000280] main playlist: nothing to play
```

---

### Post by Gone fishing on 2008-05-14
Have you got libdvdcss installed? you can get it from the medibuntu repositories.

---

### Post by SunnyRabbiera on 2008-05-14
> **Gone fishing said:**
> Have you got libdvdcss installed? you can get it from the medibuntu repositories.

no I asked that one, hes got it.

---

### Post by mc4man on 2008-05-14
While it's not meant for this situation you could try opening vlc with 
```
export DVDCSS_METHOD=title && vlc dvd://
``` (with dvd in drive)
The odds are you won't be able to watch this title on linux. What i'd do is    rip it to hdd. If you want a method that should work let me know

---

### Post by nicedude on 2008-05-14
This sounds like a region problem to me so you need to make sure you are set to use region for your location

The geographical regions are as follows:

REGION 1 -- USA, Canada
REGION 2 -- Japan, Europe, South Africa, Middle East, Greenland
REGION 3 -- S.Korea, Taiwan, Hong Kong, Parts of South East Asia
REGION 4 -- Australia, New Zealand, Latin America (including Mexico)
REGION 5 -- Eastern Europe, Russia, India, Africa
REGION 6 -- China
REGION 7 -- Reserved for Unspecified Special Use
REGION 8 -- Reserved for Cruise Ships, Airlines, etc...
REGION 0 or REGION ALL -- Discs are uncoded and can be played Worldwide, 

Since you are in Sydney you need region 4 setting do this by installing a package from the Ubuntu Universal repositories called "regionset"

here is the command to insert in a terminal to acomplish this
sudo apt-get install regionset

then use that to set your DVD drives region to region 4 for down-under DVD's :-)

Hope that get your playback going

---

### Post by Gone fishing on 2008-05-14
>  	
Re: Cant read dvd disk.
This sounds like a region problem to me so you need to make sure you are set to use region for your location


I forgot that problem I've region freed all my drives by flashing them Samsung and Lite-on drives are usually good for this.

---

### Post by Tomatz on 2008-05-14
In a terminal:


```
sudo apt-get install regionset
```


Then try ;)

---

### Post by Dissident85 on 2008-05-14
ok, so i installed regionset and i tried to play it in vlc (launching it from a terminal) and this is what i get now :S 
```

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1573 ***
*** for c_adt->cell_adr_table[i].cell_id > 0 ***

```

and that is just a small part, it went on for a bit. :S :(

---

### Post by mc4man on 2008-05-14
@ Dissident85
as per the pm i'll post the ripping method here later but I'm thinking there may be some miscommunications here. _Checking_ your region setting has been mentioned from the beginning, and i gave you a link to a thread that told you how. In any event you should really resolve this first.
With a _dvd in your drive_ run regionset from the terminal
If it shows 5 _user_ changes left the drive hasn't been set, set it to region 4.
If it shows that a region has been set make sure it's region 4, if not you'll need it to be set at 4 for this title. (best setting anyway)
Warning - setting/changing regions should not be done to play specific titles, you'll quickly run out of resets. The best thing is to have it set to your region.
_If_ your region had not been set or set to anything other than 4 you may still be able to play this title. If this is the case (_region not set, or wrong setting_) then after setting/changing try vlc again. Make sure you again go into .dvdcss and remove the titles folder before trying vlc again.
If still no playback and your region _had or recently has been set to 4_ then you'll have to rip _Unless you haven't removed the titles folder from .dvdcss first_ (edited)

edit; ex.  - only need to specify drive if you have 2 drives
```
doug@doug-desktop:~$ regionset /dev/scd0
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET    [COLOR="Red"] <-[/COLOR]
vendor resets available: 4
user controlled changes resets available: 4 [COLOR="Red"]<-[/COLOR]
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]: n
```

---

### Post by mc4man on 2008-05-14
If you still can't play after 
confirming region set to 4
having an installed dvdnav4-ifo
clearing .dvdcss
Then possibly it can't be played in linx. i've only seen 1 title that won't - reservation road - recent universal release
if no linux ripper can handle the protection (k9copy and modified vobcopy best choices) then you can do this (forgive baby steps)
Install wine
Run winecfg  (from terminal or app menu)
If you see a preloader error go here and fix, then rerun winecfg
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)
In winecfg set windows version to windows nt.4.0 or xp
In drives tab click autodetect,  if you want to set audio do so though irrelevant to this  exit winecfg
download dvdfab hd decrypter 5.0.2.0 from here (first dl shown) [http://www.dvdfab.com/free.htm](http://www.dvdfab.com/free.htm)
If this is the 1st. time using wine install from terminal, after that a right click open with wine or d. clicking will become available for .exe's
Browse to drive_c (path shown below or from wine menu in apps)
Put the dl.'ed DVDFab5020.exe in drive_c
From terminal run (adjust for user name)
 ```
wine /home/doug/.wine/drive_c/DVDFab5020.exe

```
follow the install as in win. though uncheck install vso burning engine and  create quick launch icon. Don't worry about vso error box, click ok
This is the free version with the paid included as a trial, what you want is the free - with your dvd in the drive click on Start DVDFab HD Decrypter (middle panel)
The app should start scanning the disk, the rest is evident. Saves to home dir. under DVDFAB. Note the free version will rip full title and movie only

Quirks
when it starts ablue smear will appear in upper left panel - click on desktop or start to rotate desktops and it will disappear
Don't minimize defab
If you want to go into settings (no real need to ) it accessed from green arrow. Once it opens you'll be unable to navigate, to fix - 
with mouse cursor in left panel push arrow down followed by arrow left on your keyboard and wait a few seconds. That will give you control and also change lang. to finnish - adjust to suit

---

### Post by smellydog on 2008-05-17
I had the same problem.  My drive was not set to a region.  I installed regionset and had no regions set for my drive.  I changed it and emptied my .dvdcss folder and all is well.  I bought the computer without it ever being tainted by windowz, it came pre-installed with linux.

---

