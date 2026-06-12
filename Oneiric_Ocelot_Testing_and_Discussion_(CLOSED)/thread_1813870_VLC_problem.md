---
title: "VLC problem"
date: 2011-07-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by 23dornot23d on 2011-07-28
When choosing 

**advanced open file .... **

is any body else getting strange results .....

I did a reinstall too of VLC  ..... but it creates a [[COLOR=Blue]_***window right across the screen ***_[/COLOR]]("http://img808.imageshack.us/img808/3899/screenshotat20110728191.jpg")then refuses to close down
the application ....

---

### Post by mc4man on 2011-07-28
To prevent till fixed - 
you need to install qt4-qtconf, run it and switch the default gui to anything other than gtk+, cleanlooks is good choice.
exit and save

After above before restarting vlc you should open your home folder and delete if there
.config/vlc
.cache/vlc

(this has been going on for quite some time - 
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/805303](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/805303)

---

### Post by 23dornot23d on 2011-07-28
Thank you .... that solved it for now ..... and I also added myself to the bug report you posted

Cheers ... ;)

---

### Post by mc4man on 2011-07-28
On a tester I keep the 1.11 vlc but for own use only use the 1.2+ version
There is a ppa for that but they've had build(packaging) issues for quite some time
Far superior even though a few glitch's from time to time

In O the 1.2 integrates into the soundmenu - screen in link, if inclined Andrew's how-to. will do you well (remove repo vlc first

[http://ubuntuforums.org/showthread.php?p=11077188#post11077188](http://ubuntuforums.org/showthread.php?p=11077188#post11077188)

---

### Post by lucazade on 2011-07-28
@mc4man
do you know if vlc 1.2 comes with vaapi or vdpau support out of the box,
or it is still necessary to manual patching and compiling?

---

### Post by mc4man on 2011-07-28
> **lucazade said:**
> @mc4man
do you know if vlc 1.2 comes with vaapi or vdpau support out of the box,
or it is still necessary to manual patching and compiling?

!.2 should provide vaapi, whether it works depending on hardware is another story
(actually if you ck. the chanelogs vaapi was added to vlc-1.1.3-2

I haven't bothered in quite some time - with my nvidia hardware vaapi in vlc performed quite poorly

There are some threads on, for starters you need vainfo to return a positive result which it;s likely NOT to with default vdpau-va driver

On the flip side - vlc thru ffmpeg (libavcodec) does support mt decoding now, at least here that is better than vaapi

On nvidia nothing works better than mplayer/mplayer2 w/ vdpau

Edit: one thread
[http://ubuntuforums.org/showthread.php?t=1588465](http://ubuntuforums.org/showthread.php?t=1588465)

Ex. of mt decoding - core2/duo

> 0x9cb5590] avcodec decoder debug: trying to use direct rendering
[0x9cb5590] avcodec decoder debug: allowing 2 thread(s) for decoding
[0x9cb5590] avcodec decoder debug: ffmpeg codec (H264 - MPEG-4 AVC (part 10)) started
[0x9cb5590] avcodec decoder debug: using frame thread mode with 2 threads


---

### Post by lucazade on 2011-07-28
> **mc4man said:**
> !.2 should provide vaapi, whether it works depending on hardware is another story
(actually if you ck. the chanelogs vaapi was added to vlc-1.1.3-2

I haven't bothered in quite some time - with my nvidia hardware vaapi in vlc performed quite poorly

There are some threads on, for starters you need vainfo to return a positive result which it;s likely NOT to with default vdpau-va driver

On the flip side - vlc thru ffmpeg (libavcodec) does support mt decoding now, at least here that is better than vaapi

On nvidia nothing works better than mplayer/mplayer2 w/ vdpau

Edit: one thread
[http://ubuntuforums.org/showthread.php?t=1588465](http://ubuntuforums.org/showthread.php?t=1588465)

interesting, thanks.
I'll give it a shot with both nvidia/vdpau and gma500/vaapi :) 
yep, mplayer with vaapi  works quite well here but never tried with vdpau.

well i'm not in a hurry for this, mostly was curiosity.

EDIT: Oh, thanks for the links, really useful! :)

---

### Post by mc4man on 2011-07-28
> **lucazade said:**
> 
yep, mplayer with vaapi  works quite well here but never tried with vdpau.

vdpau in mplayer can work extremely well but as always it comes down to hardware - newer cards have far greater levels of vdpau support

(what the deal is come 12.04+ w/ ubuntu/nvidia/wayland will be interesting

---

### Post by lucazade on 2011-07-28
> **mc4man said:**
> vdpau in mplayer can work extremely well but as always it comes down to hardware - newer cards have far greater levels of vdpau support

(what the deal is come 12.04+ w/ ubuntu/nvidia/wayland will be interesting

agree, how wayland and nvidia will work together will be interesting, for sure won't be an easy transition for binary drivers w/o KMS.

---

### Post by Yes_It's_Me on 2011-07-31
Oh thank you thank you thank you. I have been having this issue for weeks now, not only with VLC but with a PyQt app I wrote (A guitar synthesiser). I haven't had a look at that bug report but I will add myself to it and take a look. This has to be a larger issue with qt/gtk and not just VLC.

My app, without that little workaround would flip out just like VLC and not let me exit, additionally, X would start using 100% of CPU, it would crash compiz/unity and result in having to kill it via a virtual terminal and logging in again.

---

