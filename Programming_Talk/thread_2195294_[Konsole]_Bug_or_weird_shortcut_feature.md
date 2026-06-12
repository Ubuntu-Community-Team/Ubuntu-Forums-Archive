---
title: "[Konsole] Bug or weird shortcut feature?"
date: 2013-12-23
forum: Programming Talk
---

### Post by kangaba on 2013-12-23
Hi,
Using Kubuntu, and hence Konsole to compile stuff.
While keeping the window$ key pressed I hit Enter and it prints out this:

> 
$ (keep window$ key pressed & hit Enter)
::1                      fox-System-Product-Name  ip6-loopback
fe00::0                  ip6-allnodes             ip6-mcastprefix
ff00::0                  ip6-allrouters           localhost
ff02::1                  ip6-localhost
ff02::2                  ip6-localnet
~$ s
s: command not found
~$


Tested on Gnome terminal too - doesn't print anything. Is it a bug in Konsole or some special shortcut?


Using Kubuntu 13.10 amd64.

---

### Post by ofnuts on 2013-12-23
Same here.... seems to print the hosts listed in /etc/hosts

---

