---
title: "This is pretty much a general computer question"
date: 2016-03-26
forum: New to Ubuntu
---

### Post by desolation2 on 2016-03-26
[ATTACH=CONFIG]267992[/ATTACH]
But it has to do with Ubuntu because I don't really know what I'm looking at, I've recently switched to Ubuntu and I was having issues with another harddrive the disk percentage in windows kept going up to 100% randomly, and it lagged the hell out of my computer.  Anyways, I got a new harddrive plugged it in and I booted Ubuntu on it and have been using it, no problems so far, however when I do some tasks I make sure to check my hardware monitor to make sure nothings going on like I had before.  While I'm doing this I see this on my hardware monitor, this obviously has a lot more information than the basic windows version so I was wondering if someone could dumb it down for me.  Should my cpu% every be 102%?  I don't think so, but I honestly don't know was wondering if someone could help.

---

### Post by grahammechanical on 2016-03-26
Is that HTOP? It helps to know.

Actually, the utility is reporting CPU = 43.2%. Twice it records that. The process that is showing the 103.1% is --enable-offline-auto-reload and that is a command related to a setting in Google Chrome (I guess). Why it is showing 103.1% I do not know. Why it is even showing at all, I do not know. I do not see that entry when I load Chrome and check with HTOP.

Regards

---

### Post by yetimon_64 on 2016-03-26
> **grahammechanical said:**
> ...Why it is showing 103.1% I do not know...

The OPs screenshot indicates a 4 core cpu from the details of the "Sensors" info. A process running on 2 cores (or more) can often read over 100 % as apps like htop can add up all the core values to get a display like that. 

I suspect it only applies to multithreaded capable applications when used with such utilities. I have pesonally had some utilities (like htop) show my ffmpeg video encoding jobs displaying up to 400 % cpu usage when transcoding dvd video to h264 mp4 files on a quad core machine in the past (4 cores in use at very near 100 % each on a water-cooled quad core desktop unit :-)).

Edit: @ OP, going by the sensors info your cpu core temps look fine, I wouldn't worry about apps like htop adding up the values on a multicore machine. Yeti.

---

### Post by coldraven on 2016-03-27
In the advanced Chrome settings there a check box that says something like "Continue running in background when Chrome is closed". I always disable it, I don't trust that they are not switching on my microphone just in case I want to order Pizza or something. In other words Google is snoopy enough already.

---

### Post by mcduck on 2016-03-28
> **yetimon_64 said:**
> The OPs screenshot indicates a 4 core cpu from the details of the "Sensors" info. A process running on 2 cores (or more) can often read over 100 % as apps like htop can add up all the core values to get a display like that. 

I suspect it only applies to multithreaded capable applications when used with such utilities. I have pesonally had some utilities (like htop) show my ffmpeg video encoding jobs displaying up to 400 % cpu usage when transcoding dvd video to h264 mp4 files on a quad core machine in the past (4 cores in use at very near 100 % each on a water-cooled quad core desktop unit :-)).

Edit: @ OP, going by the sensors info your cpu core temps look fine, I wouldn't worry about apps like htop adding up the values on a multicore machine. Yeti.

yep, for a multicore CPU many programs see 100% as "100% of single core", so for 4 cores the max would be 400% (or 800% for 4-core CPU with hyperthreading).

Same goes for [load]("https://en.wikipedia.org/wiki/Load_%28computing%29") value, on a 4-core CPU "full" load would be 4.0 rather than 1.0. (of course in case of load, that can always go above the "full" use, while in case of cpu utilization percentage you'll only get the 100%*number of cores)

---

