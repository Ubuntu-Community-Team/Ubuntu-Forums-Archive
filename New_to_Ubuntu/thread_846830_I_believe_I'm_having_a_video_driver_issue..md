---
title: "I believe I'm having a video driver issue."
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Famicommander on 2008-07-01
To make a long story short, Youtube and other such online videos are running very poorly on my computer. I believe it's a result of a video card error, because I know it's nothing with my flash plugin or CPU usage (knowledge obtained through trial and error in other help threads).

So anyway, here is what my xorg.conf looks like:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver       	"trident"
	Option	"Monitor-VGA"	"My Monitor"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	30-70
	VertRefresh	50-120
	Option    "DPMS"
	Modeline	"1024x768"  64.11  1024 1080 1184 1344  768 769 772 795 -HSync +Vsync
	Option	"PreferredMode"	"1024x768" 
EndSection
```

Does it offer any clues as to what may be causing the problem?

I can run DVDs in full screen. Also, do you think adding RAM might help? I've currently got 256 MB on a Xubuntu 8.04 install.

---

### Post by ibuclaw on 2008-07-01
What sort of trial and errors have you tried?

Because my immediate thoughts would be that flash isn't acting well. And I know this is true in my experience.

The smaller the video window, the better the framerate of the flash video, or so it seems.
So fullscreen flash videos will unfortunately look like sin...

Regards
Iain

---

### Post by Famicommander on 2008-07-01
> **tinivole said:**
> What sort of trial and errors have you tried?

Because my immediate thoughts would be that flash isn't acting well. And I know this is true in my experience.

The smaller the video window, the better the framerate of the flash video, or so it seems.
So fullscreen flash videos will unfortunately look like sin...

Regards
Iain
I'm not trying to watch fullscreen flash. I can't watch any flash at all. I tried gnash, I tried Flash 9, and I tried Flash 10 beta. All of them gave the same results.

But I'd still be open to any suggestions.

Here is the saga of threads related to the video issues with this laptop:
[First issue (lots of info about the laptop, ultimately not resolved in this thread)](http://ubuntuforums.org/showthread.php?t=843061)
[First issue finally resolved](http://ubuntuforums.org/showthread.php?t=843124)
[Current issue](http://ubuntuforums.org/showthread.php?t=846596)

I'm sure they're all related somehow.

---

### Post by ibuclaw on 2008-07-01
Hi, sorry for the delayed feedback, I've just been reading your other posts.

Can you post the output of this command for us?
```
sudo lshw -short | sed '/display/p;/mem/p;/proc/p;d'
```
It will just give me a good idea of what memory you have/video driver you are running off.

Also, have a look around at this thread:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Read Part One, and possibly Part Two as well, that covers most the streaming/flash starters for firefox in K/X/Ubuntu.

Regards
Iain

---

