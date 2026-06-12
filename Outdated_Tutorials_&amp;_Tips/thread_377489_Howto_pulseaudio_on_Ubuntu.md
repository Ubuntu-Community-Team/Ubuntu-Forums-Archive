---
title: "Howto: pulseaudio on Ubuntu"
date: 2007-03-06
forum: Outdated Tutorials &amp; Tips
---

### Post by zasf on 2007-03-06
Since I coulnd't find any howtos for this on ubuntuforums.org, I point you to this on [debian forums]("http://forums.debian.net/viewtopic.php?t=12497"), credits to Mrbigshot08

---

### Post by zasf on 2007-11-27
As of today, pulseaudio works very well on gutsy, provided that you fix a couple of things.

You can find more details in the bug reports below:

[LIST]
[*][ pulseaudio esd wrapper is not working with gnome](https://bugs.edge.launchpad.net/ubuntu/+source/pulseaudio/+bug/108577)
[*][ module-esound-protocol-unix and ownership of /tmp/.esd directory](https://bugs.edge.launchpad.net/ubuntu/+source/pulseaudio/+bug/91494)
[*][ non-free Flash 9 doesn't work with pulseaudio](https://bugs.edge.launchpad.net/ubuntu/+source/pulseaudio/+bug/94233)
[/LIST]

Matteo

---

### Post by mrashley on 2007-11-27
Is pulseaudio automatically included (installed etc) with Gutsy?

I ask because I recall having read an article on it a while back but I don't think I installed it. But maybe I'm mistaken.

In either case it's on my system and I hate it. I hate it like stepping in dog poo on the way to a job interview when you're already late. I also heard pulseaudio eats babies.

Every day I have three or four applications that won't run unless I kill the pulseaudio program(daemon?). Then the program runs. A while later it seems pulseaudio always auto-magically starts up again. I assume that some **other** programs require it, like totem or something built in.

Anyway, it's really annoying. Did I do this to myself - and so I frankly deserve it - or should I be making placards to protest against my community for making my day bad when it should have beta tested first? Or involving myself and helping make better decisions.

Or is pulseaudio actually [SIZE="3"]really cool[/SIZE] and I'm just missing the boat?

---

