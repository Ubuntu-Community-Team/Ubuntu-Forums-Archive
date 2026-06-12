---
title: "How to obtain source code for gnomine?"
date: 2013-05-07
forum: Programming Talk
---

### Post by scruffyeagle on 2013-05-07
I know this might seem like an elementary thing to most of you, but it's something I haven't been able to figure out in the past hour of searching online. I need to obtain some specific source code.

I want to take one of the existing programs (gnomine as it was in Lucid), and tweak it. I'm not trying to start a "project". I simply want a version for my own use that behaves differently than the one I have. I wouldn't want to tweak the latest (gnome3) version, because I don't like what they've done with the color scheme, or the changes of controls, etc. I prefer the earlier version. It should be less work & better result, starting from that. But,  step #1 is to obtain the correct source code. I won't even know what language it was written in, until I've done that.

Can anybody walk me through this?

---

### Post by schragge on 2013-05-07
The source package for *gnomine* is [gnome-games](https://launchpad.net/ubuntu/+source/gnome-games/1:2.30.0-0ubuntu6).

---

### Post by tgalati4 on 2013-05-07
There is some info in this thread:  [http://ubuntuforums.org/showthread.php?t=2113307&highlight=gnomine](http://ubuntuforums.org/showthread.php?t=2113307&highlight=gnomine)

My last suggestion was to simply copy the binary code from the old version to your new system and run it to see if it works.  If you get errors that libraries are missing, then copy those older libraries as well.  You can have older and newer libraries sitting next to each other on your disk, without messing up the package manager.

Recompiling from source is instructive, but it will take some time for you to put together the tool chain to build it and even then, there may be bugs running it in your current environment.

---

### Post by schragge on 2013-05-07
Just installed gnomine from Lucid on current Debian sid. The only other Ubuntu packages needed were gnome-games-common from Lucid and liblaunchpad-intergration1/liblaunchpad-integration-common that I took from Quantal, but you probably already have installed working versions of them on Precise.  All the other GTK+2.0 stuff was in Debian sid repository.

---

### Post by scruffyeagle on 2013-05-26
> **schragge said:**
> The source package for *gnomine* is [gnome-games](https://launchpad.net/ubuntu/+source/gnome-games/1:2.30.0-0ubuntu6).

Got it. Thank you!

---

### Post by scruffyeagle on 2013-05-28
I intended on marking this thread as "solved" today - but, I'm not getting that as an option on the drop-down list from "Thread tools".

---

### Post by BlinkinCat on 2013-05-28
> **scruffyeagle said:**
> I intended on marking this thread as "solved" today - but, I'm not getting that as an option on the drop-down list from "Thread tools".

Hi,

Here's how to mark your first post as solved -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by scruffyeagle on 2013-06-10
Great!  Got it.  Did it.  Thanks for the guidance.

---

