---
title: "How to prevent screenshots from being taken..?"
date: 2013-04-02
forum: Programming Talk
---

### Post by KingNeil on 2013-04-02
Is there any modification I can make to the Ubuntu operating system, or program I can install.. to prevent screenshots from being taken..? Like, not just with PRINT SCREEN or any particular program... but just, prevent it from working, period..?

It's probably not possible, because the pixels are rendered, and thus, I assume they could be captured... but still, I thought I would ask...

Here is a StackOverflow thread on the topic, but I think it's Windows oriented

[http://stackoverflow.com/questions/455623/how-can-i-prevent-users-from-taking-screenshots-of-my-application-window](http://stackoverflow.com/questions/455623/how-can-i-prevent-users-from-taking-screenshots-of-my-application-window)

---

### Post by Stonecold1995 on 2013-04-03
That's not currently possible.  While technically a process needs to run as root to access things like the screen, buttons, etc, Xorg instead makes it so that programs can be run as any user and gain access.  This is because Xorg itself runs as root, and so has access to the screen.  Processes themselves can then get information from the hardware simply by "asking" Xorg.  This is why you don't need root to keylog, record the screen, etc.

IIRC, SELinux has something that can run processes in an separate virtual X server (or something like that) to make keylogging harder, so I assume it would work with screenshots as well, but it is poorly implimented and difficult to use.

If you really don't want a program to be able to take screenshots, there's a way to remove executable permissions from all of /home (this involves modifying /etc/fstab) so that no scripts or programs can run from that location.  This way only programs in places like /usr/bin can execute, meaning it would need to be installed by root in order to even start.  However I think this breaks some scripts that are in /home, so it probably wouldn't be a good idea.

---

