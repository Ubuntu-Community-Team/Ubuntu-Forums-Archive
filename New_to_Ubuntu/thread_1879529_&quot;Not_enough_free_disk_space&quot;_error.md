---
title: "&quot;Not enough free disk space&quot; error"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by aidan9629 on 2011-11-11
Running Ubuntu 11.10.

I'm pretty new to linux, so bear with..  I recently installed many OS updates through the update manager, and later upon booting up, I started running into some bugs... 

#1. On the settings dock across the top of the screen, a new icon appears; a red circle with a horizontal white bar through the middle.  When I click it, it gives me the following message:
[INDENT]*"An error occurred, please run Package Manager from the right-click menu or apt-get  in a terminal to see what is wrong. The error message was: 'Error: BrokenCount > 0'. This usually means that your installed packages have unmet dependencies."*[/INDENT]

I'm not quite sure how to run Package Manager, but I opened Update Manager, thinking their names may be synonymous. When I opened it, it had one update ready (already downloaded, ready to install). It was not a system update, but rather an update for an application I'd installed recently. Anyway, I clicked "Install Updates", but was met with *another* error message, saying that I didn't have enough disk space (a matter of a few hundred megabytes). I went into the filesystem, and viewed the top directory's properties. It said that it only had 539.8 MB of free space, yet in the "Contents" section, it said that the total contents of the ubuntu drive totalled 140.8 terabytes. This makes no sense, as my hard drive totals only 640 gigabytes...

Thanks in advance,
Aidan

---

### Post by JayKay3OOO on 2011-11-11
open the terminal.

Type this:

sudo apt-get install -f

or sudo apt-get install --fix-broken

(both do the same thing)

This should fix any broken packages or dependencies if any exist.

BTW the space problem is odd. Use disk utility to check your partition sizes so you can eradicate some partition mess up during install (ain't that a stab in the dark).

---

### Post by jtarin on 2011-11-11
Issue the command df -h in a terminal to see how much disk space you actually have. You should know your partition your Ubuntu installation resides on.

---

