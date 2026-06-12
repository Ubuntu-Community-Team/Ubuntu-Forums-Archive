---
title: "gksudo does not work"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by SomeoneX on 2008-07-13
Whenever I try to use gksudo, it sits there for several minutes, then a frozen application pops up. For instance if I "gksudo gedit" the terminal has a blank line with a blinking cursor, then a few minutes later gedit pops up, but is not responding. The same goes for "gksudo nautilus".
The programs by themselves without gksudo work fine, but without gksudo I do not have root privelages and cannot edit some files.
I have found a workaround using ls and chmod (sudo works just fine), but being new to Linux that isn't exactly the safest route, is probably more error prone, and I would rather be able to gksudo a command.

---

### Post by nikgare on 2008-07-13
I have seen this before and I think it was a hosts problem - can you post your **/etc/hosts** files please

---

### Post by SomeoneX on 2008-07-13
127.0.0.1	localhost
127.0.1.1	someonex-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


hosts.allow and hosts.deny are all commented out if you needed those as well.

---

### Post by OttifantSir on 2008-07-13
I have almost never used gksu, but are you sure you need the last two letters? Try 'gksu gedit' and 'gksu nautilus' instead of 'gksudo ...'

---

### Post by kevmitch on 2008-07-13
Sorry, I don't have any bright ideas, but I was troubled to hear that you're chmoding system files to edit them. You are changing them back to their original permissions right?

---

### Post by SomeoneX on 2008-07-13
> I have almost never used gksu, but are you sure you need the last two letters? Try 'gksu gedit' and 'gksu nautilus' instead of 'gksudo ...'
I just tried using gksu, the same problem occurred. I thought the su commands differed from sudo commands.

> Sorry, I don't have any bright ideas, but I was troubled to hear that you're chmoding system files to edit them. You are changing them back to their original permissions right?
Yes, that's why I'm using ls (-l) on the file before changing the privileges. This has been working, but is much more of a hassle than gksudo gedit/nautilus.

I guess the thread title may be misleading... (woops) it's more like the application that is called with gksudu is failing, because I get the prompt for my password, it just doesn't work after that. The application takes several minutes to load and isn't working right when it finally appears.

---

