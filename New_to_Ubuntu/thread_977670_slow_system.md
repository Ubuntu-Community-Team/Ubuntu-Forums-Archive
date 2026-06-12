---
title: "slow system"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-11-10
hi everyone,i am using hardy on my desktop that has 2 gigs of RAM,a core2duo processor,and nvidia Geforce 6200(256 MB).But,the system seems to be somewhat slow and inresponsive to me.how can i boost the system speed without having to part from all the eyecandy,compiz,themes,emerald,etc.

---

### Post by sirebral on 2008-11-10
Right Click on your panel and add the CPU Frequency Scaling Monitor.  Then Left click on that and choose performance. 

Does that help?

---

### Post by Carl Hamlin on 2008-11-10
> **stonecoldjha said:**
> hi everyone,i am using hardy on my desktop that has 2 gigs of RAM,a core2duo processor,and nvidia Geforce 6200(256 MB).But,the system seems to be somewhat slow and inresponsive to me.how can i boost the system speed without having to part from all the eyecandy,compiz,themes,emerald,etc.

I've had many of my systems improve their performance by orders of magnitude after removing trackerd.

---

### Post by JKBurton on 2008-11-10
Try running System/Administration/System Monitor, when to your knowledge the system should be idle. On the resources tab, let it settle (no mouse or kbd use) for a minute, and then look at how much CPU is being consumed. If it's over 10%, switch to the processes tab, click on the %CPU column until it says "%CPU ^", which sorts the running processes so the ones consuming CPU are at the top.

Again, let it settle for a minute, then note which processes are showing %CPU above 0.  It'll keep changing, but over a few changes the same few processes should keep showing up.

Post that list, and I'll see if I can help.

Best of luck,
Keith

---

### Post by oldos2er on 2008-11-10
> **stonecoldjha said:**
> hi everyone,i am using hardy on my desktop that has 2 gigs of RAM,a core2duo processor,and nvidia Geforce 6200(256 MB).But,the system seems to be somewhat slow and inresponsive to me.how can i boost the system speed without having to part from all the eyecandy,compiz,themes,emerald,etc.

 Which version of Ubuntu are you running?

 I agree with the suggestion to disable or uninstall tracker. I generally remove all services I don't use or need, including bluetooth, brltty, laptop-mo$, pcmciauti$, wpa-ifup, etc. I use CONCURRENCY=shell (only speeds up boot process), have vm.swappiness set to 5, and I have writeback enabled in the filesystem (note writeback increases risk of losing data if there's an unexpected shutdown). Use Google to find many more examples of steps you can take to speed up your system, just use caution. I make a backup copy of any file I alter; and be sure to use "gksu" (if you're a Gnome user) to call gedit instead of "sudo" as so many sites recommend.

 I have a similar system to yours (2GB RAM, Core2Duo, 512MB Nvidia Geforce 7300), and it's very snappy. I'm on 8.04.1.

---

### Post by Carl Hamlin on 2008-11-10
> **oldos2er said:**
> and be sure to use "gksu" (if you're a Gnome user) to call gedit instead of "sudo" as so many sites recommend.

Why gksu over sudo?

---

### Post by oldos2er on 2008-11-10
> **Carl Hamlin said:**
> Why gksu over sudo?

 Because it has the potential to bork .ICEauthority. See [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by Carl Hamlin on 2008-11-10
> **oldos2er said:**
> Because it has the potential to bork .ICEauthority. See [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

Gotcha. Thanks for the tip!

---

### Post by stonecoldjha on 2008-11-10
how do i disable all that?

---

### Post by Carl Hamlin on 2008-11-10
> **stonecoldjha said:**
> how do i disable all that?

You'll get a number of answers to this question. I like to use 'apt' to do it. Apt has a fairly comprehensive man page, and works pretty well in my experience for loading and unloading packages.

---

