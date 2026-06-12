---
title: "How can i tell if i have load count problem??"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by lellyville on 2008-09-28
really worried about my hdd dieing on me...

when i entered 
sudo smartctl -a /dev/sda | grep Load_Cycle_Count

i get 63747 for the last number
then it increased after like 10 minutes to 63748
do i have this problem? Also does vista also have this problem? or is it just linux exclusive thing? because i only used ubuntu about 30 hours and vista about like a year.

---

### Post by bobnutfield on 2008-09-28
I have never had an issue with smartctl, but there is an article here on understand the diagnostics.  

[http://www.linuxjournal.com/article/6983]("http://www.linuxjournal.com/article/6983")

---

### Post by mc4100 on 2008-09-28
> **lellyville said:**
> really worried about my hdd dieing on me...

when i entered 
sudo smartctl -a /dev/sda | grep Load_Cycle_Count

i get 63747 for the last number
then it increased after like 10 minutes to 63748
do i have this problem? Also does vista also have this problem? or is it just linux exclusive thing? because i only used ubuntu about 30 hours and vista about like a year.
I'd say you were unaffected, but I'm no expert; this might be useful if you determine you are affected:
[http://www.linux-hero.com/rant/ubuntu-hard-drive-explosions](http://www.linux-hero.com/rant/ubuntu-hard-drive-explosions)

---

### Post by t0p on 2008-09-28
*Grrr*... why is it that when I enter that *smartctl* command, I don't get that kind of output?

```
t0p@ubunty:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
sudo: smartctl: command not found
t0p@ubunty:~$ sudo apt-get install smartctl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package smartctl
t0p@ubunty:~$ 

```

So what's that all about?

---

### Post by mc4100 on 2008-09-28
I installed the package a while ago, thus can't remember what it's called, but this looks promising: 
```
sudo apt-get install smartmontools
```

---

### Post by t0p on 2008-09-28
Okay, I've got *smartmontools*.  So now, smartctl doesn't seem to do anything except this ouptut:
```

t0p@ubunty:~$ sudo smartctl -a /dev/sdd
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

```

So doing
```
sudo smartctl -a /dev/sda | grep Load_Cycle_Count

```

obviously returns no output...

:confused:

**PS:** sorry to the OP for hijacking your thread. :)

---

