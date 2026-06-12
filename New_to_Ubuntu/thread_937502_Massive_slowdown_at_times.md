---
title: "Massive slowdown at times"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Mr Mac on 2008-10-03
First, I'm new to Ubuntu.  I just trashed Vista yesterday and installed Ubuntu 8.04.  I've installed only a couple of apps: Wine, IEs4Linux (I'd rather not have done this, but I need IE for work purposes) and KTorrent (KDE4).  

My problem is this:  Occasionally, the hard drive starts running and all functionality of my computer goes out the door.  You can move the mouse cursor, but it is choppy in it's movement.  (The mouse cursor will appear, and when you attempt to move it, it won't move again for another 20-30+ seconds).  I am then left with two choices: wait for Ubuntu to finish it's seemingly random reason for playing with my hard drive (I waited 27 minutes for this to cease - Just why would Ubuntu be accessing my HD for 27 minutes??? :confused:) or turn off the computer.  

I'm running a 1.73 Ghz Dual-Core with 1 gig of RAM.  Ubuntu looks pretty nice, but if I can't resolve this issue, my computer is worthless and I may as well go back to Vista, which I would rather avoid having to do.

There doesn't seem to be any rhyme or reason as to this happening.  It's not like it happens every time I do 'X'.  The last time this happened, I finished setting up my printer, then I ran IE and viewed a web page.  The time before that, there were no programs running.

Thanks for any comments.

---

### Post by adult swim on 2008-10-03
do you have the tracker applet running?  it could be indexing your drive.
an easy way to see what is going on is to have a terminal window open, and when it starts acting up, go to the terminal and type in ```
top
```  that will show you what process is eating up your resources.

---

### Post by Frak on 2008-10-03
I too suggest that you may try disabling Trackers indexing via (I think) System -> Preferences -> either Indexing or Tracker

Could also be in Applications -> Accessories -> tracker or indexing

---

### Post by trebor7_1 on 2008-10-04
Hi I have recently had this happen to me a few times now. Last time I had a terminal open and ran top but it was sowing no great cpu use, just 3 items at 3 - 4 % as I remember. The HDD led was on and system totally un responsive. I left it like this for maybe 6 hours, still nothing.Then did "sudo shutdown -h now" and after a while ended up with a black screen with white text scrolling pass err ata ??? Powered down and restarted ok and is working now, but any suggestions welcome...

---

### Post by rax_m on 2008-10-04
I've noticed that in a fresh install tracker can consume quite a bit of CPU. 
But also, I noticed that a process "scrollkeeper-up" (or something similar) will hog my CPU. I usually just kill it and everything is fine. 

As a previous post said, use "top" from the terminal or the System Monitor tool to check which processes are using the CPU.

---

### Post by 3rdalbum on 2008-10-04
Scrollkeeper-update, trackerd, or updatedb can use lots of CPU time; but they shouldn't use as much as you describe.

If you could somehow get to a terminal and run the command "top" while this is happening, it would be of huge help to us to find out what program is on top of that list.

---

