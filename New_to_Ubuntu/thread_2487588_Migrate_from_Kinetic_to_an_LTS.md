---
title: "Migrate from Kinetic to an LTS"
date: 2023-06-09
forum: New to Ubuntu
---

### Post by seso532 on 2023-06-09
Hey all, I accidentally installed Ubuntu kinetic and just found out it's coming to EOL in Jul.

I had not considered a higher version would have different LTS support, another got'cha for me ](*,)! 

I read downgrading to LTS 22.04 can be painful and I need to migrate before EOL. 

Next option, Lunar EOL is also short, can I expect maybe a version after Lunar may give an LTS option, is that how release cycles work? Guidance how to migrate to LTS smoothly and without reinstalling much appreciated!

---

### Post by guiverc on 2023-06-09
You didn't say if your install was a Desktop or Server install (*in my opinion that makes a  difference*).

Just FYI:   Many of us can fall into that trap, eg. a little over a decade ago I came into that same hurdle; didn't like Ubuntu 11.10 so returned to 11.04 (GNOME 2 for *classic* and not GNOME 3) which was when I first really learnt about non-LTS with Ubuntu (I was still new to Ubuntu then, having mostly used Debian or OpenSuSE at that time).

**Firstly I'll provide your upgrade options**

- Ubuntu offers two upgrade paths

(1) from LTS to LTS, ie. 22.04 will offer an upgrade to the next LTS **after **the release of Ubuntu 24.04.1 which won't be until August 2024.  LTS releases are the *first* release on an *even* year, thus 20.04, 22.04 are currently supported LTS releases, the next will be 24.04 or 2024-April.

(2)  upgrade via all releases, ie. 22.04 will upgrade to 22.10, then to 23.04, then to 23.10 before finally returning to the next LTS which is 24.04 in April 2024.

ie. you can continue upgrading every 6-9 months and you'll get to 24.04, with your upgrade opening **before **its opened from prior LTS users (ie. 23.10 upgrades to 24.04 months before 22.04 -> 24.04 upgrades are offered).

Ubuntu's LTS *development* occurs over two years, starting end of April 2022 and completing with the release of Ubuntu 24.04 LTS.  Three non-LTS releases are released providing users an option of using that *development* work, being 22.10 (*where you are now*), 23.04 (*your next jump*) and currently the work is towards 23.10 (*which is actually close to the final 24.04 in most respects*). 
[B]
Secondly - Re-install options[/B]

On desktop systems, you can perform a non-destructive install to re-install your system to fix package problems etc as an easy fix. As no release checks are made, you can also use this method to install a different release, thus achieving what I think of as an *Upgrade via re-install*, but it also can be used to *downgrade* an install too.

There can be risks with going backwards... ie. I mentioned I went back from Ubuntu 11.10 to 11.04 (the GNOME 2 desktop I loved was gone with 11.04, but thanks to the GNOME-CLASSIC login option I actually still liked 11.04 as it was still GNOME2 when using CLASSIC.. it didn't feel the same to me at 11.10, and after a few weeks I wanted to go back to 11.04).  I just used the re-install/repair option (*something I love about Ubuntu*) to return to 11.04; ie. non-destructive reinstall of the prior release & I was back on 11.04 I preferred, at least until 11.04 reached EOL (*non-LTS had 15 months then, its now only 9 months*).  Anyway I soon discovered the first issue going backwards... During the few weeks I was using the newer software, I started exploring the newer options GNOME software allowed, decided I liked some of those features so started using them (here I'm talking about evolution or the GNOME Mail app & its new capacity to sort/tag incoming mail) ...

When I returned to the prior release; any email that had been touched by the new rules was suddenly *invisible* to the older evolution version I had on the older 11.04 I was then using. No error appeared, the mail program just didn't show any of those emails. I didn't notice it, though a few phone calls later I slowly became aware that I wasn't dealing with all emails due to some no longer appearing in my inbox. I got around the issue by reading my email at terminal & forming the reply on an editor (*since they wouldn't show in the mail app*) and then sending replies normally in the GUI app.. When I upgraded to 12.04 I could return to normal operation.

In most cases, returning to an earlier release of Ubuntu via re-install will not be a problem, but I've had problems like this more than once in using it. It's not release specific, but APP/package specific (ie. in this example I'm referring to evolution or the [GNOME Mail MUA]("https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=evolution") as QA tests are only performed by Ubuntu & GNOME on moving to later releases, no checks on going backwards.  I've also had issues with Liferea & some other apps too on different backwards jumps.  Result is you need to do some homework (*checking what changed in packages where data matters to you*) if re-install an older release of Ubuntu.

Having problems with going backwards are not the norm; in my GNOME Evolution MUA example; the problem I experienced was only because I used the newer features in the later version; if I'd not touched that feature I'm sure I would not have had an issue. In the Liferea case however, the database was altered during the *release-upgrade* which created a problem when the older release was returned to (*as data wasn't in the format it was expected to be in for the version of liferea then in use*). 


For some more details on non-destructive re-installs, I'll provide
- [https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743](https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743)  (refer the *Install using existing partition* testcase
- [https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533)


You can also clean install (*usually default if you've got a server install*), then restore your data from backups... however you can still have issues like I did with the *non-destructive re-install* where data was modified by later versions of apps.

---

### Post by ActionParsnip on 2023-06-09
If you keep updating to the next release until you hit 24.04 then you will have an LTS install. Alternatively, wipe the installation off and do a clean install of 22.04 and restore your user data from your backups

---

### Post by #&amp;thj^% on 2023-06-09
> **seso532 said:**
> 
I read downgrading to LTS 22.04 can be painful and I need to migrate before EOL. 
It is for sure, and will test every linux skill in the book, I've done it a few times but it is quicker to do a clean fresh install, no cruft left behind.
> **seso532 said:**
> 
Next option, Lunar EOL is also short, can I expect maybe a version after Lunar may give an LTS option, is that how release cycles work? Guidance how to migrate to LTS smoothly and without reinstalling much appreciated!
That's not something I would recommend (downgrading). You will have another point release (Not a LTS) in Mantic 23.10, before reaching a true LTS 24.02.
That kind of helps in choosing your route you wil take I hope. :)
Best of luck with ever route you take.

---

