---
title: "Chrome hogging CPU."
date: 2011-09-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by seattle vic on 2011-09-10
For about 5 days now, Chrome has been unusable.  After about 10 seconds or so it starts using up to 100% of the CPU.  When I look at the system monitor there are many instances of Chromium-browser with the waiting channel saying futex-wait-queue-me.  Eventually it just stalls and I have to close it using the kill command.

---

### Post by JonM33 on 2011-09-10
> **seattle vic said:**
> For about 5 days now, Chrome has been unusable.  After about 10 seconds or so it starts using up to 100% of the CPU.  When I look at the system monitor there are many instances of Chromium-browser with the waiting channel saying futex-wait-queue-me.  Eventually it just stalls and I have to close it using the kill command.

I use Chromium with 11.10 and have no problems at all.

---

### Post by fjgaude on 2011-09-10
I have no issue with Chromium browser. If you do report as a bug to launchpad.

---

### Post by P-I H on 2011-09-10
In my installation I have had problems with Chromium since Alpha 1. When I close a tab the cpu load goes up to 100% on one of the cores and it takes several seconds before I am able to use the next tab.
However this happens just with Ubuntu and Ubuntu 2D login. With Gnome login Chromium behaves as usual.

---

### Post by JonM33 on 2011-09-10
> **P-I H said:**
> In my installation I have had problems with Chromium since Alpha 1. When I close a tab the cpu load goes up to 100% on one of the cores and it takes several seconds before I am able to use the next tab.
However this happens just with Ubuntu and Ubuntu 2D login. With Gnome login Chromium behaves as usual.

Just tried to reproduce and I do not get that problem. I have a 1.66GHz Core Duo on my IBM ThinkPad X60s.

---

### Post by dmoconnell on 2011-09-10
> **seattle vic said:**
> For about 5 days now, Chrome has been unusable.  After about 10 seconds or so it starts using up to 100% of the CPU.  When I look at the system monitor there are many instances of Chromium-browser with the waiting channel saying futex-wait-queue-me.  Eventually it just stalls and I have to close it using the kill command.

Ok stupid question time. Their is Chrome Browser, maintained by Google, and the Chromium Browser, the open source sister to Chrome. Some would say their is no real difference between the two, I maintain that their is small (under the hood) difference between the too. On one line you are talking about Google Chrome. but then when you talk about the system monitor you call it Chromium. My question is which one do you have installed, Chrome or Chromium. this would help to replicate the problem (and also to know where to file the bug report)   

I maybe asking a very stupid question, but as I said I feel their is a difference between the two and it may only be effecting one of them.

Dm

---

### Post by seattle vic on 2011-09-10
I downloaded it from the Ubuntu archives using synaptic, so I guess it's chromium-browser.

---

### Post by effenberg0x0 on 2011-09-11
In my case it was the Flash Plugin, not Chromium, which was taking 100% of CPU. That is discussed in another recent thread ([http://ubuntuforums.org/showthread.php?t=1840667](http://ubuntuforums.org/showthread.php?t=1840667)). 

Using the command /usr/bin/top, see if you have npviewer.bin eating your resources. Kill it (something like sudo killall -s KILL npviewer.bin, or any other way you are used to doing it).  See how Chrome/Chromium perform without the Flash Plugin.

For the record: I am a Chrome user in all my PCs, but I have been using Firefox in Oneiric right now. I think that it currently integrates better with the Flash Plugin, Unity and the GUI changes, gives me a better performance in the 64 bits platform, etc. 

Regards,
Effenberg

--------------------
Ubuntu Oneiric is Beta 1. It is expected to not work 100% and is  not what I would personally recommend for anyone that just needs to get  the job done. It's aimed at beta testers and people that can afford to  have a broken PC right now. So PLEASE: DO NOT attempt any of the  mentioned procedures if you're working on a server / production machine,  if you don't have backup of your data or if you don't have the habit of  performing fixes in Ubuntu / Linux distros. You can end up having to do  a new install from scratch. I can't be held responsible for any damage,  ok? :smile:

---

