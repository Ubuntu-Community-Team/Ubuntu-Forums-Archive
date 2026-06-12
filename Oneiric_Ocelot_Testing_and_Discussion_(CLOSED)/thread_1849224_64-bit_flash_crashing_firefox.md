---
title: "64-bit flash crashing firefox"
date: 2011-09-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2011-09-24
With beta 2 I have decided once again to try the 64-bit version.
I normally use 32-bit these days, mainly because of flash problems.

So anyway, although flash content plays fine, I find firefox crashes EVERY time I close a tab with flash content.

The whole app just freezes up completely and I have to terminate it.
This doesn't happen with chromium though.

---

### Post by x-shaney-x on 2011-09-24
Just to add, I have since tried running firefox in safe mode and it still has the problem.

---

### Post by sammiev on 2011-09-24
Use [Flash_aid]("http://www.webgapps.org/download/add-ons/firefox") and your problems will likely be over. :)

---

### Post by x-shaney-x on 2011-09-24
Ok, I admit I ignored the reference to flash aid before.
For some time I have been striving to avoid fiddling in any way.  I want as close as possible to a desktop that suits me WITHOUT adding PPAs or compiling software or using scripts to install things.  Mainly for ease of initial setup but in frustration I went ahead and tried it.

Needless to say, flash works perfectly now and no crashing so thanks for that tip :)
Just wonder if anyone knows how this affects other browsers?

I have tried chromium and it is picking up the same flashplayer but will it also have the enhancements that flash-aid is meant to give firefox (more efficient, better full-screen compatibility etc)?

---

### Post by ratcheer on 2011-09-24
Again, I just do the simple manual installation of 64-bit Flash and I have had no problems at all. I use the Firefox 7 Beta that is current for Oneiric.

I recommend that you uninstall any Flash that is currently on your system, download the current 64-bit Flash for Linux directly from Adobe, extract the files, and copy file libflashplayer.so to directory /usr/lib/mozilla/plugins. The copy should be done under sudo.

Tim

---

### Post by Paddy Landau on 2011-09-24
Surely one should not have to fiddle to get something as basic as Flash working? This is *not* going to leave newcomers with a good impression!

---

### Post by x-shaney-x on 2011-09-24
I must agree.  I'm certainly not a newcomer but I still don't want to start extracting and copying files or editing config files to get the most basic things working.

---

### Post by lovinglinux on 2011-09-26
> **x-shaney-x said:**
> Ok, I admit I ignored the reference to flash aid before.
For some time I have been striving to avoid fiddling in any way.  I want as close as possible to a desktop that suits me WITHOUT adding PPAs or compiling software or using scripts to install things.  Mainly for ease of initial setup but in frustration I went ahead and tried it.

Needless to say, flash works perfectly now and no crashing so thanks for that tip :)
Just wonder if anyone knows how this affects other browsers?

I have tried chromium and it is picking up the same flashplayer but will it also have the enhancements that flash-aid is meant to give firefox (more efficient, better full-screen compatibility etc)?

Flash-Aid only works in Firefox. However, the changes it makes affects other browser as well.

---

