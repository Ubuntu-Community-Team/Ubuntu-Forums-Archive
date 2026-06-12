---
title: "removing old shortcuts from app menu"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by voxmortem on 2012-09-25
Hello,

I've been using ubuntu 12.04 for some time now, however, I still fail on removing applications shortcuts after unninstalling software. 

I'm using gnome desktop (3.42) and problem occurs only in games tab so far- I have some broken shortcuts there from games I already uninstalled. I've tried using alacarte to delete those entries, but it crashes whenever I try to remove something from menu list. Unticking apps doesn't hide those empty shortcuts either, and I couldn't find anything to solve the problem. Is there a way to get rid of those shortcuts, is it a bug or did I messed something up in my system? :)

I'll appreciate any help- while it's not something critical, it's definately something I don't like about my system.

Cheers!

---

### Post by daslinkard on 2012-09-25
These launchers should be located in one of the following directories....

[LIST]
[*]/usr/share/applications
[*]/usr/local/share/applications
[*]~/.local/share/applications
[/LIST]
If your launcher file is in any of the first two directories, you will require root permissions to remove it.

---

