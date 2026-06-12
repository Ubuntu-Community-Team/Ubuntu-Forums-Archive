---
title: "Strange g15daemon Behaviour"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by sepz on 2008-10-27
Hello Gents,

Wondering if any of you have experienced any strange behavior from the G15Daemon, the time and date displays without any hitch on the KB itself, but seemingly at random (approx every 5mins) the daemon is sending some sort of "Home" shortcut command.

If i have a browser window open and focused every few minutes the page loads onto Google.
If I'm just sitting at the X desktop it will bring up my /Home folder in Nautilus without any form of input from me. 

As soon as I do a killall g15daemon I don't hear from this bug again until next reboot/restart of the service.

I've done a modest search and couldn't find anyone else with this issue, and given my fairly limited Linux understanding have come here to see if anyone else has experienced this same behavior? Or where could I start to try and diagnose what is going on? Does the daemon have any kind of home command?

Any advise would be greatly appreciated, not mission critical but definitely something I'd like to (try to) understand!

NB: I have disabled the 'home' shortcut key under key bindings to no effect.

Ubuntu 8.10 x64 - 2.6.27
G15 from apt repositories (currently not on my system to check versions sorry, but I assume g15daemon 1.9x)

(All most recent versions per sourceforge)

Thanks in advance, TLDR !! :)

---

### Post by Zector on 2008-12-31
Sorry to bump an old topic. (Found Via Google)
But this started happening to me too and can't seem to figure out a solution. Does anyone have any hints as to why this may be happening?

*edit*
I'm going to try running G15daemon in debug mode. My guess is that it is somehow hitting XF86HomePage which is mapped to G6 without G15macro running. I checked with xev, but it stopped the moment I tried that.

I'm no expert at any of this, I hope I have the right idea.

*edit 2*
Found this thread which seems to be the same issue.
Dunno what to make from it yet.
[http://www.g15tools.com/forum/viewtopic.php?f=9&t=109&start=0&sid=99d9a09da49e1193e6bcc7974c84854a](http://www.g15tools.com/forum/viewtopic.php?f=9&t=109&start=0&sid=99d9a09da49e1193e6bcc7974c84854a)

---

