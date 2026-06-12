---
title: "Can I downgrade xorg?"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by blueshead on 2012-06-08
The update in 12.04 has messed up my mouse in some games (scroll wheel).

How would I downgrade xorg?

---

### Post by stmiller on 2012-06-08
Unfortunately it's not possible to downgrade without major breakage. :/

---

### Post by anewguy on 2012-06-08
+1.  Many things have some fairly tight ties to X windows, and trying to go backward could prove to be a challenge at best.

dave ;)

---

### Post by RikoW on 2012-06-09
Hi,

I did downgrades of the xorg drivers a few time. I posted some instructions earlier:

[http://ubuntuforums.org/showpost.php?p=10165272&postcount=4]("http://ubuntuforums.org/showpost.php?p=10165272&postcount=4")

(adjust to the Ubuntu releases you need)

Use at your own risk, though. You may break things seriously and might end up re-installing your system.

Good luck, if you intend to try.

                 Riko

---

### Post by anewguy on 2012-06-11
Drivers - yes, though as you mentioned they can also be problematic.  But trying to downgrade X itself?  That's just asking for problems.  ;)

Dave ;) or

---

### Post by blueshead on 2012-06-11
I'd like to thank everyone for their answers.

I guess the safest thing to do is make an 11.10 bootable partition on an exterior h/d? My games ran just fine in that..

---

### Post by bodhi.zazen on 2012-06-11
> **blueshead said:**
> I'd like to thank everyone for their answers.

I guess the safest thing to do is make an 11.10 bootable partition on an exterior h/d? My games ran just fine in that..

That and file a bug report. Without a bug report, how would your problem get addressed ?

---

### Post by blueshead on 2012-06-11
> **bodhi.zazen said:**
> That and file a bug report. Without a bug report, how would your problem get addressed ?


A bug report was filed..

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/989811]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/989811")

---

### Post by bodhi.zazen on 2012-06-11
> **blueshead said:**
> A bug report was filed..

And there was much rejoicing ...

---

### Post by anewguy on 2012-06-12
I noticed the bug report is in how some games handle things like the mouse.  I don't think we ever got a reason why you want to do what you were asking, so I'm going to assume for the gaming.  I would suggest you go to the [ubuntu games and leasure forum ]("http://ubuntuforums.org/forumdisplay.php?f=93")and check there for help specific to the game(s) you are trying to get to work.

If it's not for a game, then please post back the reason why you are wanting to do this.

Dave

---

### Post by blueshead on 2012-06-12
> **anewguy said:**
> I noticed the bug report is in how some games handle things like the mouse.  I don't think we ever got a reason why you want to do what you were asking, so I'm going to assume for the gaming.  I would suggest you go to the [ubuntu games and leasure forum ]("http://ubuntuforums.org/forumdisplay.php?f=93")and check there for help specific to the game(s) you are trying to get to work.

If it's not for a game, then please post back the reason why you are wanting to do this.

Dave


Basically as stated in the bug report.. Upgrading to ubuntu 12.04 broke scrolling in some games. It seems some people fixed this by downgrading xorg.

Howsoever ,After the warnings here about trying that.. I will concede and leave xorg alone.  I will this weekend just make an 11.10 partition for my games. Problem for me at least solved.

At this point..Thank you everyone for your help and advice and can a mod close this thread.? 

As the scrollwheel problem has not been solved in 12.04 I cannot check this off as solved.=;

---

### Post by anewguy on 2012-06-12
Does your scroll wheel work in such thing as Firefox when just scrolling a normal page?  I have a scroll wheel mouse and it works fine, but I also am not a gamer.  Wondering if it works otherwise because if it doesn't perhaps there is something more we can look at - like how the system sees the mouse.

Dave ;)

---

### Post by blueshead on 2012-06-12
> **anewguy said:**
> Does your scroll wheel work in such thing as Firefox when just scrolling a normal page?  I have a scroll wheel mouse and it works fine, but I also am not a gamer.  Wondering if it works otherwise because if it doesn't perhaps there is something more we can look at - like how the system sees the mouse.

Dave ;)


It works just fine except in games powered by the Quake 3 engine. It was fine until upgrade from 11.10 to 12.04.

---

### Post by idoitprone on 2012-06-13
> **blueshead said:**
> It works just fine except in games powered by the Quake 3 engine. It was fine until upgrade from 11.10 to 12.04.

ohh, the quake 3 engine is kidda old.

Do you know what's older than Quake 3, Xorg. You have to realize xorg is a different beast of problems. Graphic cards, gui tool kits, editors, networking, virtual space drivers, graphic libraries are all connected to the Xorg. Trying to make Xorg compatible with itself is already hard. In fact, common complaint of Xorg developers is that they practically gave up keep binary compatibility when they release new a version of Xorg. There is a reason why Wayland is gaining momentum. Xorg is holding back the Linux desktop and making things worse. That breaking of scrolling is one of many things Xorg is known to do.

So, unless you want to deal with Xorg, which believe is a giant pain in the ***. I can keep rant forever, but it does not matter. I want Wayland to succeed but sacrificing network transparency is probably is harsh compromise

---

### Post by anewguy on 2012-06-13
I thought that was going to be the case - works fine except in your game.  I don't believe that would be any type of Ubuntu issue, but rather an issue with the game, as mentioned above by idoitprone.

Dave ;)

---

### Post by blueshead on 2012-06-13
> **anewguy said:**
> I thought that was going to be the case - works fine except in your game.  I don't believe that would be any type of Ubuntu issue, but rather an issue with the game, as mentioned above by idoitprone.

Dave ;)

I would thimk it is an Ubuntu issue..as this happened from upgrading from 11.10 to 12.04? xorg or maybe openGL?

---

### Post by anewguy on 2012-06-13
Even if you leave this post here, do check/post the gamin and leisure forum.  They don't just answer questions on playing a game, but cover installation, issues with running - like you are experiencing - problems after an OS update, etc., for the game.
<snip - I accidently pasted something here that wasn't relevant!>
Just an idea that might get you better responses.

Dave ;)

---

