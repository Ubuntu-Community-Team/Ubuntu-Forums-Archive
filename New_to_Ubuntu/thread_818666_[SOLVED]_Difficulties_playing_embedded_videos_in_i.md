---
title: "[SOLVED] Difficulties playing embedded videos in in Firefox - Hardy Heron"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by euchrid33 on 2008-06-04
I've just installed Hardy Heron, and I'm having some problems with it.

Embedded videos won't play in Firefox - they either don't play at all, showing a black screen, or play with lots of skips, freezes and stutters.  These videos all play fine in my Windows install.  Youtube videos run fine for some reason.

Before you suggest it, I've installed the VLC plugin, the terminal says that it's already installed and doesn't need to be installed again.  Could it be the plugin which Firefox uses to run them?  I'm not sure how to select the one that it uses.

Any suggestions would be very welcome.

---

### Post by euchrid33 on 2008-06-04
Addendum - now that I look more carefully, a lot of videos are stuttering in Youtube as well.  Downloaded videos play fine, in both VLC and mplayer.

---

### Post by kk0sse54 on 2008-06-04
Are you using firefox 3?

---

### Post by euchrid33 on 2008-06-04
Yes, Firefox 3 Beta 5 to be precise.

---

### Post by euchrid33 on 2008-06-05
Okay, I tested it with Firefox 2.  Same problem.  

This is getting very frustrating, and if I can't work it out it's likely to be a deal-breaker for me.  That would be pretty awful, as I've started to like a lot of other stuff that Ubuntu does.

---

### Post by RSingh on 2008-06-05
Try disabling Compiz Fusion and trying.

Right Click on desktop > Background > Effects

Tick "No Effects"

Also you can check your embedded player is configured correctly:
[URL="http://ubuntuforums.org/showthread.php?t=540412"]
Try here: http://ubuntuforums.org/showthread.php?t=540412[/URL]

---

### Post by worldy on 2008-06-05
Is the Adobe Flash FireFox plugin version 9 installed ?

---

### Post by euchrid33 on 2008-06-05
The Shockwave Flash Firefox plugin is installed, and it's version 9 - I presume that this is the same thing?

I've disabled all effects on the desktop, and it hasn't made a difference.

I've also discovered that embedded MP3s - podcasts and the like - don't work either.  In fact, they cause the browser to freeze and then crash.  Is this likely to be part of the same problem?

---

### Post by avtolle on 2008-06-05
When you installed the VLC plugin, did you remove the default plugin for mplayer? If not, there could be a conflict.

---

### Post by euchrid33 on 2008-06-05
I believe that I did, yes.  I ran a search for mplayer in synaptic, and every entry is unchecked - that means that it's not installed, yes?  It couldn't be lurking somewhere else?

I checked in about:plugins as well, there's two mentions of it - once under Windows Media Player Plugin 10 (compatible; Totem), where is says application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes

It also appears under VLC Multimedia Plugin, in much the same fashion.  Is this an issue?  Should I try to remove these?

---

### Post by Bloch on 2008-06-05
Youtube videos use the Flash format. Many sites now use flash for video, where previously they might have used embedded realplayer vdeos or microsoft technologies.

Far too many websites that hold video media only test their site on windows and perhaps a mac. Some videos will not play on Firefox (on linux); some will play only after a hack, some will play when you change plug-ins and then you find that other video sites now fail to work.

Give the URL of the website with video that failed to play and others can test it.

For example with RTE [http://www.rte.ie/](http://www.rte.ie/) I can only play video when I click to play in an external player. It doesn't bother me now.

The main thing is that embedded videos are problematic, but large well-maintained sites generally pose no problem.

---

### Post by avtolle on 2008-06-05
> **euchrid33 said:**
> I believe that I did, yes.  I ran a search for mplayer in synaptic, and every entry is unchecked - that means that it's not installed, yes?  It couldn't be lurking somewhere else?

I checked in about:plugins as well, there's two mentions of it - once under Windows Media Player Plugin 10 (compatible; Totem), where is says application/x-mplayer2     AVI video     avi, wma, wmv     Yes

It also appears under VLC Multimedia Plugin, in much the same fashion.  Is this an issue?  Should I try to remove these?
OK, you are referring to the Totem plugin there, right? BTW, I meant Totem before, typed mplayer. If you have a separate VLC plugin installed, then I'd remove the Totem plugin that refers to VLC. Not an expert here, just seems that if there are two plugins attempting to do the same thing, there's going to be a conflict.

EDIT: In an attempt to clarify, if you have installed from Synaptic or Add/Remove programs mozilla-plugin-vlc, then there are two plugins trying to handle output to vlc; that one, as well as the Totem one, which is installed by default.

---

### Post by euchrid33 on 2008-06-05
Okay, sorted!

I think that you were on the right track - I found <a href="http://ubuntuforums.org/showthread.php?t=786131"> this thread,</a> which shows the command for installing Adobe Flash and purging everything that might interfere with it.

sudo apt-get purge flashplugin-nonfree gnash gnash-common swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport

Worked like a charm, and I'm loving Ubuntu again.

---

### Post by avtolle on 2008-06-05
Great. Please mark the thread "solved" if you would.

---

