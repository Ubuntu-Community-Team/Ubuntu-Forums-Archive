---
title: "Ubuntu 12.04 screen goes to sleep after 10 min"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by DHinton on 2012-04-24
I am running Ubuntu 12.04 on a Compaq NC2400, the screen goes to sleep after 10 minutes.  I found some post on some commands to run in the terminal that seem to disable the feature, but after I reboot the computer it goes back to going to sleep after 10 minutes.  Is there anyway so that the screen never goes to sleep?

thanks

---

### Post by anewguy on 2012-04-24
system settings, brightness and lock, change the timer at the top.

---

### Post by Curtis6767 on 2012-04-24
System Settings

Brightness and Lock

---

### Post by DHinton on 2012-04-25
> **anewguy said:**
> system settings, brightness and lock, change the timer at the top.

Tried that changed the time to never, also changed the power settings to don't suspend, yet it still sleeps after 10 minutes.  Any other ideas?

---

### Post by z3nhakr on 2012-04-25
12.04 is still in beta so your best bet is to wait for the final release and then update

---

### Post by wojox on 2012-04-25
Was this the terminal command?
```
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
```

---

### Post by DHinton on 2012-04-25
> **wojox said:**
> Was this the terminal command?
```
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
```
yes

---

### Post by DHinton on 2012-04-25
> **z3nhakr said:**
> 12.04 is still in beta so your best bet is to wait for the final release and then update

Was thinking maybe the same thing, I have a copy of Mint that I could use I guess.

---

### Post by wojox on 2012-04-25
> **DHinton said:**
> Was thinking maybe the same thing, I have a copy of Mint that I could use I guess.

Release is < 24 hours. 

Do you have dcon-tools installed. If so open dconf-editor and check it there.

---

### Post by DHinton on 2012-04-25
> **wojox said:**
> Release is < 24 hours. 

Do you have dcon-tools installed. If so open dconf-editor and check it there.

yes I do have that installed, what am looking for in dcon-tools?

---

### Post by wojox on 2012-04-25
> **DHinton said:**
> yes I do have that installed, what am looking for in dcon-tools?

Look in org -> gnome -> desktop -> screensaver

---

### Post by DHinton on 2012-04-25
> **DHinton said:**
> yes I do have that installed, what am looking for in dcon-tools?

So I used a a live cd of Ubuntu 11.10, changed the power settings and Screen setting to never, it seems to be working.  So it looks like a 12.04 issue.  Not a huge deal on this project to go back to 11.10. I will try to use 12.04 on the next project.

---

### Post by DHinton on 2012-04-25
> **wojox said:**
> Look in org -> gnome -> desktop -> screensaver

the is no entry for screensaver under desktop

---

### Post by wojox on 2012-04-25
No?

---

### Post by DHinton on 2012-04-25
[attach]216572[/attach]> **wojox said:**
> no?

---

### Post by wojox on 2012-04-25
> **DHinton said:**
> [attach]216572[/attach]

lol your in the wrong path. Look in org -> gnome -> desktop -> screensaver

That's cool though the Live CD did the trick. :lolflag:

---

### Post by DHinton on 2012-04-25
> **wojox said:**
> lol your in the wrong path. Look in org -> gnome -> desktop -> screensaver

That's cool though the Live CD did the trick. :lolflag:

if at first you don't succeed, try, try again :) but is still goes dark after 10 minutes... starting the install of 11.10.  At least I learned some more about ubuntu / linux.

---

### Post by codingman on 2012-04-25
There was a new update in update manager that fixed this, so try updating.

---

### Post by c1823a on 2012-12-05
The exact same thing just started happening with my system, around December 4, 2012.  It did not have a problem before this.  After exactly 10 minutes, the system goes into suspend mode (or at least that's what it appears to be doing) and it will wake up after a keyboard input.  I use this system for streaming video to my TV and I have had the suspend timer set at 1 hour. It worked great until now.  Are there any new ideas on this?

---

### Post by verzx on 2012-12-05
Maybe this is the problem you're having, unless you've not changed power settings so the monitor doesn't turn off to save power because you're idle for 10 minutes. (This is in the power settings)

[http://ubuntuforums.org/showthread.php?t=2059551](http://ubuntuforums.org/showthread.php?t=2059551)

---

### Post by c1823a on 2012-12-05
Thanks for that!!!  I'll give it a try tonight.  Yes, power settings have been checked multiple times.

---

### Post by c1823a on 2012-12-08
The installation of Caffeine works great!!  Thank you!!

---

### Post by Plorkz on 2012-12-08
I have this same problem!!! terminal commands do nothing... brightness and lock do nothing hoping that dcon thing works!!!

---

