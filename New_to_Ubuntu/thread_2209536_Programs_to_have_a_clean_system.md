---
title: "Program/s to have a clean system"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by sdvf on 2014-03-06
Hi guys, i'd like to have a clean and fast system as i've got now. Programs for linux like ccleaner for windows.
Is there any one?

---

### Post by arochester on 2014-03-06
[https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean)

---

### Post by Lars Noodén on 2014-03-06
The EXT file system doesn't fragment like NTFS does.  Nor does the rest of the system suffer from bit rot likethe other OS does.  So there is relatively little that can be done to change the performance of your system.  It's already well-tuned by default.

---

### Post by vanadium on 2014-03-06
I concur fully. Linux is boring in that respect. You do not need to spend time to clean the system in order to keep it fast and responsive. The file system does not significantly fragment (except when near full), there is no central registry that gets bloated and that may become corrupt, taking down the entire system. Cleaning only serves to recover a little disk space (in the order of megabytes only) caused by unused programmes, downloaded installation archives or unused libraries. Your effort will not be rewarded with better performance, though.

---

### Post by ibjsb4 on 2014-03-06
> **sdvf said:**
> Hi guys, i'd like to have a clean and fast system as i've got now. Programs for linux like ccleaner for windows.

Not like ccleaner, but does a nice job

[https://apps.ubuntu.com/cat/applications/saucy/bleachbit/](https://apps.ubuntu.com/cat/applications/saucy/bleachbit/)

First time you use it, be sure about what your removing :)

---

### Post by nunecas123 on 2014-03-06
> **ibjsb4 said:**
> Not like ccleaner, but does a nice job

[https://apps.ubuntu.com/cat/applications/saucy/bleachbit/](https://apps.ubuntu.com/cat/applications/saucy/bleachbit/)

First time you use it, be sure about what your removing :)

I'm pretty sure he doesn't even need that. If he wants a faster system, he should do an upgrade to his hardware ;). But still, well thought.

---

### Post by oldrocker99 on 2014-03-06
A hardware upgrade is almost certainly the best way to improve GNU/Linux performance. In other words, what he said^.

---

### Post by ibjsb4 on 2014-03-06
Wow, thats good  ..

Hardware upgrade recommended; I would of had to ask what the computer specs are first :)

---

### Post by nunecas123 on 2014-03-06
We all forgot that :p.

So, can you simply please tell us the computer specs?
Thanks!

---

### Post by Rob Sayer on 2014-03-09
CCleaner can remove cookies and such, but so can you browser if you set it up right and/or use the right plugins ...

The main semi useful thing for ccleaner in windows I've seen is to fix the windows registry, but I have trouble trusting windows programs for that.

In linux, you don't actually need anything like a windows registry cleaner.  There really isn't anything quite like a 'registry'.

Windows programs install themselves.  And, since windows permission levels completely and utterly *stink*, it's quite easy for a program installer to remap your system through the windows registry.  Windows media programs are notorious for that.  And the stupid OS gives no indication of this whatsoever.

In linux, the OS installs all programs.  It's impossible for a program install to remove codecs et al and put in new ones without big red flags going up.

Before I installed linux I actually switched to windows programs that were linux ports because they virtually always won't mess up the windows registry when you install them.  This made the switch to linux a lot easier BTW.

---

### Post by oldos2er on 2014-03-09
> **sdvf said:**
> Hi guys, i'd like to have a clean and fast system as i've got now. Programs for linux like ccleaner for windows.
Is there any one?

This seems to be a FAQ asked by Windows users, but they never explain what exactly ccleaner does. What specifically do you want to "clean"? Someone mentioned bleachbit, just take care you understand what it's going to do so nothing is deleted that you don't want deleted (good backups are a must, need I say?). Personally I think programs like that are unnecessary, but that's just me.

---

