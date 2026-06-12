---
title: "upgraded my ubuntu 9.10 to 10.4LTS"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by BT56 on 2011-09-30
i need a help, my computer is P4 2.8 processor and 1GB ram and 500GB HDD i upgraded my ubuntu 9.10 to 10.4LTS and now my computer is slow, mainly i cnt open more than three tabs in fire fox its getting slow and stuck. and i cant watch MP4 and mkv files, they wont play normally,  those files are freezing wen they are playing. pls help me.

---

### Post by overdrank on 2011-09-30
Hi and welcome, moved to Absolute Beginner Talk

---

### Post by garvinrick4 on 2011-09-30
> **BT56 said:**
> i need a help, my computer is P4 2.8 processor and 1GB ram and 500GB HDD i upgraded my ubuntu 9.10 to 10.4LTS and now my computer is slow, mainly i cnt open more than three tabs in fire fox its getting slow and stuck. and i cant watch MP4 and mkv files, they wont play normally,  those files are freezing wen they are playing. pls help me.
Open system monitor and see what your cpu usage is during certain functions. Ram is fine
I do not know exactly how old the processor. But not running compiz, running videos not in
HD or 720 in YouTube. See what is eating you up????
gnome-system-monitor is the package.
```
sudo apt-get install gnome-system-monitor
```or 
```
top
```Will let you see in terminal.

---

### Post by BT56 on 2011-10-01
> **garvinrick4 said:**
> Open system monitor and see what your cpu usage is during certain functions. Ram is fine
I do not know exactly how old the processor. But not running compiz, running videos not in
HD or 720 in YouTube. See what is eating you up????
gnome-system-monitor is the package.
```
sudo apt-get install gnome-system-monitor
```or 
```
top
```Will let you see in terminal.

my processor is 3years old, videos in my hard drive wont play well they are freezing, i checkd with system monitor, it is not showing nything only the chart is moving all programs are sleeping.. :(

---

### Post by mörgæs on 2011-10-01
How does 10.04 work in a live boot?

---

### Post by garvinrick4 on 2011-10-01
> my processor is 3years old, videos in my hard drive wont play well they  are freezing, i checkd with system monitor, it is not showing nything  only the chart is moving all programs are sleeping.. :sad: Is it just in one app like Movie Player or in more
than one application? If it is movie player than give this a go. 
```
sudo apt-get clean
``````
sudo apt-get install --reinstall totem
```

---

### Post by Linux_junkie on 2011-10-01
> **BT56 said:**
> i need a help, my computer is P4 2.8 processor and 1GB ram and 500GB HDD i upgraded my ubuntu 9.10 to 10.4LTS and now my computer is slow, mainly i cnt open more than three tabs in fire fox its getting slow and stuck. and i cant watch MP4 and mkv files, they wont play normally,  those files are freezing wen they are playing. pls help me.

How did you upgrade to 10.04? Unless you have done it already I would always recommend a fresh install Ubuntu and not to upgrade from a previous version.  Fresh installs usually work without (many) problems.

---

