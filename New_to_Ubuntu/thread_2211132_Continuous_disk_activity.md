---
title: "Continuous disk activity?"
date: 2014-03-14
forum: New to Ubuntu
---

### Post by schmitta on 2014-03-14
My disk is being continuously hit. My process numbers run from 1 to 
schmitta 21320  0.0  0.1   4944  1172 pts/0    R+   09:13   0:00 ps auxww
and it seems like there are too many processes cause delays of minutes for the system to respond to mouse clicks (denial of service?). Any ideas?

---

### Post by Vladlenin5000 on 2014-03-14
My sincere apologies if I sound rude or unfair but I've to ask this: Are you for real or just someone payed to spread FUD or doing it for fun?
Have you red this (your own thread), especially post #9? [http://ubuntuforums.org/showthread.php?t=2184758](http://ubuntuforums.org/showthread.php?t=2184758) 
Perhaps you should actually read and make an effort to understand the points in contention there before we go any further...

---

### Post by buzzingrobot on 2014-03-14
This ([http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)) sticky thread always linked at the top of this forum might be useful reading.

What process is "continuously" hitting your drive and what happens when you terminate that process?

The chances of this being caused by an errant process, or a legitimate process (say, a new Dropbox/Ubuntu One install in the process of synchronizing) are great.

---

### Post by 3rdalbum on 2014-03-14
If you could write a virus to run on somebody's computer and do anything, what would you do?

a. Steal their internet banking details and take their money
b. Post funny things on Facebook under their name as a laugh
c. Make their computer really slow

Why on earth would somebody go to all the trouble of writing a virus and distributing it... for the sole purpose of making your computer slow?

Just because (you think) something is unexpected behaviour, does not mean that your computer has viruses. As was mentioned in the thread that Vladlenin linked to, Windows users get paranoid about viruses, almost as though they are biological super-organisms that spread through the air and cause random mayhem to any piece of electronics they encounter. There are NO VIRUSES THAT WORK ON UBUNTU. Full-stop. Some day there may be. Today, there are none. You are more likely to be killed by a shark than to get a Linux virus.

Now if you're actually interested in solving your problem, I suggest it's probably a buggy program at fault. The command 'top' will help you identify a single process or a couple of processes that are individually using a lot of CPU power, so you can either kill them or take some other kind of action to prevent them from causing problems.

The command "ps aux" will show you all the processes running on your system. If you do indeed have tens of thousands of programs running - possibly one of them is spawning itself when it shouldn't - then you can use "ps aux | less" to look through them. You'll quickly identify which one is running when it shouldn't. Then use the "killall" command, e.g. if Apport is the command that's respawning itself continuously, "killall apport" should stop this from happening. Then you can remove the program or disable it for good.

---

### Post by oldos2er on 2014-03-14
I've changed the thread title to better reflect the problem.

---

### Post by bapoumba on 2014-03-15
Is this an older computer or a recent one ?
I've moved to lubuntu for some time now on this older laptop, because of similar symptoms. My own interpretation on my own machine : unity was too resource hungry for this older gear. Sometimes the cursor would hang in there for two minutes and then slowly move where I had placed it. No possible action in the meantime. My CPU was always up, I could hear the disks cry their accesses out.

---

### Post by buzzingrobot on 2014-03-15
> **bapoumba said:**
> Is this an older computer or a recent one ?
I've moved to lubuntu for some time now on this older laptop, because of similar symptoms. My own interpretation on my own machine : unity was too resource hungry for this older gear. Sometimes the cursor would hang in there for two minutes and then slowly move where I had placed it. No possible action in the meantime. My CPU was always up, I could hear the disks cry their accesses out.

If the system begins to swap because installed RAM is too small to support the active processes, then the disk(s) will be accessed much, much more, perhaps constantly, and that will generate heat, etc. Elements on the display can stall during swapping because code and data is being written to, and read from, the drives instead of being manipulated in memory. If the code, for example, needed to move the cursor is swapped out, the cursor won't move until the code is read from the drive, after something else is written out to make room.

This might account for the OP's issue.

---

### Post by bapoumba on 2014-03-15
Thanks buzzingrobot for nicely wording my clumsy writing :)
I have to say that a possible hack or something never crossed my mind. I did have a look at the "top" output though, everything looked normal (sort of saying) with unity and chrome eating up all live resources. Moved to lubuntu right away on this 1GB laptop. Now RAM gets 50% used on average, no more heating (yes, it did heat up quite a bit), CPU usage is low most of the time and swap is 90% free.

---

### Post by buzzingrobot on 2014-03-15
I'm on 14.04 with lots of RAM.  Per System Monitor, Firefox is using the most memory (348 Mib), followed by Liferea (the RSS reader) at 151, Evolution at 99, compiz at 57, and the Update-Manager at 46.  There are a number of Unity components, of course.  It's interesting, though, that System Monitor itself is taking more memory than any single component of Unity.

---

### Post by bapoumba on 2014-03-15
14.04 here too. If I choose to look only at active processes, only gnome-system-monitor is active on a continuous basis (8MB), and chromium gets on from time to time. These are the only two applications I'm using right now. Of course, sorting them out by mem usage, chromium gets on top every time it gets active, with 3 to 5 different active processes, 8 total. My mem is 50% used atm, but you probably know this does not mean 50% _is_ used. 50% is either used or reserved by applications.

If I look at the system processes, Xorg wins, then Networkmanager and polkitd, woopsie and dhclient. 

I have 1GB RAM and 1.5GB swap. Swap is 7.3% used atm. Since I've been using lubuntu, I've never had the feeling swap was overwhelmed. I never really checked either :)

---

### Post by lisati on 2014-03-15
My $0.02:
As others have suggested, it's a good idea to investigate what's actually happening. What looks like continuous disk activity can be a result of a number of things. Insufficient RAM to cope with the processes you have running has already been mentioned. Another is when your system is having trouble reading or writing to your disk for some reason, and is being slowed down as it tries to deal with it.

Tools such as *ps*, *top* and *htop* can be useful in tracking down what's using your system's resources.

---

### Post by anewbie on 2015-02-01
Kind of an old thread but I've been investigating this issue on my computer and it is without a doubt chrome (chromium). I set up monitor processes and that little sucker is writing gigs of data a day; then I started looking a threads (chromium bugs) and found several spanning 2 years updated as recently as a month ago indicating chromium loves to clobber the disk. One person suggested disabling malware detection and I'm testing that but so far it doesn't help much - 7 GB of writes by chromium in 12 hours.

---

### Post by bapoumba on 2015-02-01
> **anewbie said:**
> Kind of an old thread but I've been investigating this issue on my computer and it is without a doubt chrome (chromium). I set up monitor processes and that little sucker is writing gigs of data a day; then I started looking a threads (chromium bugs) and found several spanning 2 years updated as recently as a month ago indicating chromium loves to clobber the disk. One person suggested disabling malware detection and I'm testing that but so far it doesn't help much - 7 GB of writes by chromium in 12 hours.

Would you have links to these bug reports ?

---

### Post by anewbie on 2015-02-01
Here's a couple there are more. There are also threads on chromium memory leaks (which eventually lead to swapping). I know my system isnt' swapping as I also monitor that state but after a month or so it will unless i restrt chromium.

[http://code.google.com/p/chromium/issues/detail?id=401391](http://code.google.com/p/chromium/issues/detail?id=401391)

[http://code.google.com/p/chromium/issues/detail?id=439400](http://code.google.com/p/chromium/issues/detail?id=439400)

-
There are also other (non bug reports) such as this thread (one of many):
[https://foldingforum.org/viewtopic.php?f=95&t=26609](https://foldingforum.org/viewtopic.php?f=95&t=26609)

--
There's a couple there are more. There are also threads on chromium memory leaks (which eventually lead to swapping). I know my system isnt' swapping as I also monitor that state but after a month or so it will unless i restrt chromium.

---

