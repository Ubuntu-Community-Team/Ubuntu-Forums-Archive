---
title: "[SOLVED] Update Manager problems"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by getut on 2008-05-11
I have a fresh install of Hardy 32 bit and am having a problem of the Update Manager constantly giving the error message "The update information is outdated. This may be caused by network problems. Please update manually by clicking on this icon and then selecting 'Check'.

I have clicked on the icon and it updates from the repos and the icon will go away for 30 minutes or so then its back.

sudo apt-get update and sudo apt-get upgrade work just fine... it even gets updates like it is supposed to with no errors.

It all started when I changed from main usa repos to Duke University a day or two after release day for hardy. The Duke repos worked great then stopped working when the error started so I switched back to main usa repos and got lots of updates but the error remained. I finally switched to main canonical repos and got even more updates but the error won't go away.

---

### Post by diablo75 on 2008-05-11
Try going to System>Administration>Software Sources.

From the first window that you are shown, it will tell you what server it is currently going to for updates.  Click on that button and it will expand open a little bit.  Then click on "Other..."

A new window will appear with a very large selection of mirrors to pick from.  Try clicking on the "Select Best Server" button.  It will go through and ping them all, and the one with the fastest response time will be selected for you.  Alternatively, you could go through the listing and select the one you believe is closest to you and try that instead.  Then click close, reload, and then try your Updates again.  Don't click on the "revert" button by accident, it'll just put your previous server selection back, which isn't what you really want...

---

### Post by nilarimogard on 2008-05-11
I'm having the same issue, and that thingy with best servers... it says no server found :))

although apt-get update works just fine... except the outdated error in systray

---

### Post by getut on 2008-05-12
> **diablo75 said:**
> Try going to System>Administration>Software Sources.

From the first window that you are shown, it will tell you what server it is currently going to for updates.  Click on that button and it will expand open a little bit.  Then click on "Other..."

A new window will appear with a very large selection of mirrors to pick from.  Try clicking on the "Select Best Server" button.  It will go through and ping them all, and the one with the fastest response time will be selected for you.  Alternatively, you could go through the listing and select the one you believe is closest to you and try that instead.  Then click close, reload, and then try your Updates again.  Don't click on the "revert" button by accident, it'll just put your previous server selection back, which isn't what you really want...

That is actually what I think got me into this pickle. I was using the Duke University repos (the fastest and the closest to me). but they got out of sync with canonicals or something. Dukes just plain stopped working. I found it out because my machine at work running Hardy got some updates, but after about 4 days my home machine still hadn't offered them to me. I switched to the main repos at home and it got all of those updates also. Right about the same time that happened, my error message started and hasn't cleared up since.

---

### Post by b9k9kiwi on 2008-07-06
I have been experiencing Manager Update problems for three or four days now - none of the solutions or processes pointed to in this thread make any difference on my Hardy Heron system.What's the fix - a re-install?

---

### Post by getut on 2008-07-06
I finally found the problem.

My wife uses Scribus for desktop publishing and I always configure my Ubuntu to go to the Scribus repositories to get the latest/greatest rather than the one in the Ubuntu repositories.

Well when I upgraded to Hardy, there was no Hardy version of the Scribus repositories yet so I just used the Gutsy repos and changed the name to Hardy with the idea that whenever they came online it would just start working and the newest version would show up as an upgrade.

The end result is that the hardy scribus repo always failed. This failure caused the update manager to think it was out of date. When it really wasn't. It was just that one of the repos was unreachable... not out of date.

I found the issue when I was browsing through the Hardy bugs list and someone had reported a bug with update manager showing as out of date if any repo was unreachable. Clear any bad repos from your apt sources.list file and the problem should go away if it was the same problem as mine.

---

### Post by b9k9kiwi on 2008-07-06
Okay - Update Manager tells me "Failed to fetch [http://ppa.launchpad.net/banshee-team/ubuntu/dists/Hardy/Main/binary-i386/Packages.gz](http://ppa.launchpad.net/banshee-team/ubuntu/dists/Hardy/Main/binary-i386/Packages.gz)  404 Not Found".

I guess if I remove the address from my list of repositories, then all will be well - but how do i do that?

---

### Post by b9k9kiwi on 2008-07-07
> **b9k9kiwi said:**
> Okay - Update Manager tells me "Failed to fetch [http://ppa.launchpad.net/banshee-team/ubuntu/dists/Hardy/Main/binary-i386/Packages.gz](http://ppa.launchpad.net/banshee-team/ubuntu/dists/Hardy/Main/binary-i386/Packages.gz)  404 Not Found".

I guess if I remove the address from my list of repositories, then all will be well - but how do i do that?

In reply to my own message - there were two locations in Software Sources pointing to Banshee sources - I unchecked those and now all seems okay.

Not exactly intuitive as the source titles didn't match the error message to any great extent all part of the learning curve it would seem.

---

