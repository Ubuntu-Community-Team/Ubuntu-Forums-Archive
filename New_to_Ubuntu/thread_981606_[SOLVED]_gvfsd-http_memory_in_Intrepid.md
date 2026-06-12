---
title: "[SOLVED] gvfsd-http memory in Intrepid"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by rotwang888 on 2008-11-13
Hello.  From time to time since switching from hardy to intrepid I've noticed process gvfsd-http using a lot of memory, more than firefox at times.  So...what exactly is it and can I safely kill it?  I haven't noticed any bad results from doing so before, but it must be running for a reason, yes?  Thanks for any info.

---

### Post by talsemgeest on 2008-11-13
Well gvfs stands for Gnome Virtual File System, which controls file operations etc... So it is probably better not to kill it unless you absolutely have to.

---

### Post by rotwang888 on 2008-11-13
Ok then, sounds like I should ignore it.  Just seemed odd it was using so much.  With Intrepid I've been using Deluge instead of utorrent with wine.  Maybe that's related?  What with the "http" and all...just a thought.  Thanks for the info.

---

### Post by talsemgeest on 2008-11-13
It seems to be that downloads get temporarily stored in memory, so that is probably your problem.

---

### Post by rotwang888 on 2008-11-14
A-ha.  Found the problem.  It's not torrents, it's podcasts downloaded with Rhythmbox which has been acting funky. No need to keep that stuff sitting in RAM.  Good to know.  Marking as solved then.  Thanks!

---

### Post by talsemgeest on 2008-11-14
> **rotwang888 said:**
> A-ha.  Found the problem.  It's not torrents, it's podcasts downloaded with Rhythmbox which has been acting funky. No need to keep that stuff sitting in RAM.  Good to know.  Marking as solved then.  Thanks!
Awesome, glad you got it working!

---

### Post by Naugh on 2008-12-03
Same Problem, 
Podcasts are for some reason being saved to my music folder and taking up RAM space, which leads to Rhythmbox Crash.   Instead of "kill Process" i shutdown and restarted my computer and it was removed from RAM. 

It sucks b/c that limits the amout of Podcasts you can download in a single session...not like restarting takes a lot of time, just impractical 

Thanks to Rotwang888 for the help

---

### Post by talsemgeest on 2008-12-03
Has it been reported as a bug? If not, maybe you should do so.

---

### Post by rotwang888 on 2008-12-04
Ok, since at least one other person has looked at this thread, and I did mark it "solved", maybe I should add a couple things.  You shouldn't have to reboot to free up the ram used by the podcasts.  I went into system manager and killed process "gvfsd-http".  By "solved" I just meant that now I know what was causing the high memory usage of that process, not that Rhythmbox is behaving now.  It still crashes regularly.  I've seen a few threads about the problem, and there is one of those "brainstorm" things to get Rhythmbox replaced by something else as Ubuntu's default music player.  Not sure if there is an official bug report...maybe I should figure out how to look that up.

---

### Post by oysterpog on 2008-12-14
i'm getting this problem as well with gvfsd-smb, after i've been downloading stuff off our local server... my processor usage stays at 100% after downloading anything

---

### Post by mrynit on 2008-12-18
Today I started downloading about 10 podcasts with rhythembox. I noticed my memory usage jumped to 88% and I have 2GB. I am running ```
Ubuntu 8.04, 2.6.27-10-generic, Rhythmbox 0.11.6
``` After killing rhythembox RAM usage dropped to a normal level. 
[[IMG]http://img72.imageshack.us/img72/7029/96955341hf7.th.png[/IMG]](http://img72.imageshack.us/my.php?image=96955341hf7.png)

---

### Post by talsemgeest on 2008-12-18
> **mrynit said:**
> Today I started downloading about 10 podcasts with rhythembox. I noticed my memory usage jumped to 88% and I have 2GB. I am running ```
Ubuntu 8.04, 2.6.27-10-generic, Rhythmbox 0.11.6
``` After killing rhythembox RAM usage dropped to a normal level. 
[[IMG]http://img72.imageshack.us/img72/7029/96955341hf7.th.png[/IMG]](http://img72.imageshack.us/my.php?image=96955341hf7.png)
You will probably be better off starting a new thread, as this one has already been marked as [solved].

---

### Post by mrynit on 2008-12-21
it's not solved. the problem is identified.

---

### Post by talsemgeest on 2008-12-21
No, look at the title of this thread. Notice the little [solved] at the beginning? That means the original poster has marked it as solved.

Most people who are trying to help on these forums skip these threads as they believe someone else has already solved it. So, if you want to be helped, I would suggest you create a new thread.

But, as this is obviously a bug, please file a bug report. That way the people who can will fix it. There is a very good page on how to file a bug report [here](http://ubuntuforums.org/showthread.php?t=1011078).

---

### Post by jamesisin on 2009-01-21
Was that bug report ever filed (by anyone)?

Is there another thread that was started for this problem?

I am seeing something similar and I am trying to research the issue (gvfsd-smb using 50% of my proc for no apparent reason).

Links anybody?

---

### Post by zytzagoo on 2009-03-31
> **jamesisin said:**
> Was that bug report ever filed (by anyone)?

Is there another thread that was started for this problem?

I am seeing something similar and I am trying to research the issue (gvfsd-smb using 50% of my proc for no apparent reason).

Links anybody?
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/225615](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/225615)

---

### Post by robdashu on 2010-08-27
I had a severe problem with gvfsd [vanilla].  I'm not collecting podcasts.

I started up update-manager, and my entire 1Gig of RAM and almost my entire swap space (1.3G) were used up.  System Monitor reported gvfsd the largest memory user at 400MB.  When I ended the process, everything reverted back to normal operating state...

gvfsd restarted and is using only ~ 60MB

Seems unrelated to Rhythmbox bug

---

