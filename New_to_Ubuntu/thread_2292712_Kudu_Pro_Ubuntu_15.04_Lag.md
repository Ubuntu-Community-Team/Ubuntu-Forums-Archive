---
title: "Kudu Pro Ubuntu 15.04 Lag"
date: 2015-08-30
forum: New to Ubuntu
---

### Post by darksim2 on 2015-08-30
EDIT: Very new to Ubuntu. Only experience so far has been getting my wifi to work better.

I've had this laptop for about a week and just yesterday started noticing severe lag spikes happening for no apparent reason. With Gnome System Monitor open, I see several CPUs being used more heavily than I would expect considering GSM and one tab in Opera are the only things I have open. Even with nothing open though I still experience the same symptoms (typing freezes then either does nothing or duplicates the pressed key dozens of times, for example). When I go to the "processes" tab everything under "CPU" reads 0.

---

### Post by ajgreeny on 2015-08-30
You might do better with an open terminal running the command **top** which will list the processes running, and which you can sort by CPU% by typing an upper case C.

Set that window to always be on top (by right clicking in the top titlebar of the terminal), then drag it down so you can see just the first four or five processes.  Now you can continue your work and open other applications with the terminal still visible to keep an eye on what process is using all your CPU cycles.

When we know that we can try to sort out why, and hopefully how to stop it happening.

---

### Post by darksim2 on 2015-08-31
Thanks! That's showing things much better.

I'm seeing a lot of watchdog/4, kworker/4:0, ksoftirqd/4, and migration/4. dnsmasq has shown up once. They're all in the 80%+ range. While I've been observing this, they haven't been causing the same issues consistently. I only notice the lag spikes on occasion and sometimes there will only be one of the processes I mentioned and other times I'll notice compiz and/or Xorg at 30%+ in addition to one of the others at 80%+.

Overall it hasn't been as bad (yet) today. Rebooting has fixed the problem in the past, but sometimes it'll pop up right on startup and others it won't show up until I've been working for a few hours.

I'm also starting to notice Opera showing up with around 30% and sometimes one or two additional processes in the 10s and 20s during these spikes. I was about to say watchdog appeared to be a major culprit, but then another spike happened with kworker and migration but no watchdog so I'm kind of at a loss.

---

### Post by ajgreeny on 2015-08-31
I've no experience of watchdog, but do you really need it?

---

### Post by darksim2 on 2015-08-31
It must have just been on here by default, but from what I've been reading about it I'd say no.

This is what I've found: [http://askubuntu.com/questions/134899/watchdog-0-process-using-all-my-cpu-suddenly](http://askubuntu.com/questions/134899/watchdog-0-process-using-all-my-cpu-suddenly)

---

### Post by mc4man on 2015-08-31
Everyone that runs Ubuntu with Ubuntu supplied kernels has watchdog. It should not be using a lot of cpu.
Seeing as though you just bought this laptop from System76 I'd contact their tech support & have them fix these " lag" issues. The laptop is under warranty & also within the 30 day return period.

As an aside you got it with 15.04 which will be end of life in Feb. At that point you'd need to upgrade or fresh instal 15.10 or install 14.04.x. The newer or older kernel may treat you better...
In any event I'd get Sys76 to square this up, you should not be getting these issues out of the box.

---

### Post by QIII on 2015-08-31
There have been bug reports from time to time regarding issues with watchdog and certain kernels.

But I agree System76 should be called to task on a new machine.

---

### Post by darksim2 on 2015-08-31
I opened a support ticket with them so we'll see how that goes. If there's a good fix, I'll be sure to post it here.

---

### Post by ajgreeny on 2015-09-01
There is no watchdog on my Xubuntu 14.04 and never has been to my knowledge.  Is it just in Ubuntu, not necessarily the others?

---

