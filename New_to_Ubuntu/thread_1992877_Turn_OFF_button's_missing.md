---
title: "Turn OFF button's missing"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by czgirb on 2012-06-01
Today, may **turn OFF** button, which in default setting is placed on the **Monitor's Upper Left** is missing. What can I do for have it back?
Please help

---

### Post by jtarin on 2012-06-01
What desktop are your running? What version of Ubuntu?

---

### Post by anewguy on 2012-06-01
Did the resolution or the alignments in the monitor setup get changed?

Also - I have run into this problem lately and don't know whay - sometime for whatever reason my screen just goes larger than can be displayed on the monitor.  The result is everything pushed off to the left and everything pushed off to the right.  When it does that my power button isn't visible either.  I do have a terminal icon in the center of my desktop, so when this happens it is still available, so I open a terminal and do sudo shutdown -r now to force a reboot.  When it comes back to the login screen, I usually change to Gnome Classic or Gnome Classic no-effects.  This usually fixes it for me.  *IF* you can get it to reset by rebooting, do so.  Then put a terminal icon in the center of your desktop so if worse comes to worse you have an out.  I suspect this is either from some patch (it just started in the last week) or a nVidia driver problem.

Dave ;)

---

### Post by czgirb on 2012-06-01
> **jtarin said:**
> 
What desktop are your running? What version of Ubuntu?

Ubuntu 10.04 Lucid Lynx

> **anewguy said:**
> 
Did the resolution or the alignments in the monitor setup get changed?

I don't know ... the button is missing after log-in
And before that I never changed my monitor's resolution

> **anewguy said:**
> 
Also - I have run into this problem lately and don't know whay - sometime for whatever reason my screen just goes larger than can be displayed on the monitor.  The result is everything pushed off to the left and everything pushed off to the right.  When it does that my power button isn't visible either.  I do have a terminal icon in the center of my desktop, so when this happens it is still available, so I open a terminal and do sudo shutdown -r now to force a reboot.  When it comes back to the login screen, I usually change to Gnome Classic or Gnome Classic no-effects.  This usually fixes it for me.  *IF* you can get it to reset by rebooting, do so.  Then put a terminal icon in the center of your desktop so if worse comes to worse you have an out.  I suspect this is either from some patch (it just started in the last week) or a nVidia driver problem.
Dave ;)

How to change to Gnome Classic or Gnome Classic no-effects

---

### Post by jtarin on 2012-06-01
> **czgirb said:**
> 
How to change to Gnome Classic or Gnome Classic no-effects

10.04 Ubuntu Lucid Default desktop is Gnome Classic. In a terminal type ```
metactity --replace
```to turn off compiz. To turn compiz on ```
compiz --replace
```Check your startup folder to see if either of these commands are there. Eliminate the one not wanted.

---

### Post by czgirb on 2012-06-01
> **jtarin said:**
> 
... Check your startup folder to see if either of these commands are there. Eliminate the one not wanted.


What you means by Startup folder?
**Preferences > Startup Application**?
What command you mean?
And what command to be eliminated?
SORRY ... I'm 100% new to Ubuntu.

Update 16:32:05
Turn OFF the compiz ... but the turn OFF button still do not shown

---

### Post by melrokz on 2012-06-01
Right click > Add to Panel > in the search box, type 'Shut Down' > click it > Add to panel. That's your button, where you want it. Quite simple :)

---

### Post by czgirb on 2012-06-01
> **melrokz said:**
> Right click > Add to Panel > in the search box, type 'Shut Down' > click it > Add to panel. That's your button, where you want it. Quite simple :)

Do you mean the RED color?
No! No! I want my original button back.
Please guide me ....

---

### Post by inashdeen on 2012-06-01
Did it constantly gone or can you get it back by a restart?

---

### Post by czgirb on 2012-06-02
> **inashdeen said:**
> Did it constantly gone or can you get it back by a restart?

[SIZE=3]**Constantly Gone**[/SIZE]

---

### Post by dcsoldschool53 on 2012-06-02
What you need to do is restore your gnome-panel back to manufacture setting. This will remove any customized settings that you have made, and replace your power off button. Here are two sites to show you how you can do it. [http://www.absolutelytech.com/2010/06/20/how-to-reset-panels-settings-to-default-in-ubuntu/ ]("http://www.absolutelytech.com/2010/06/20/how-to-reset-panels-settings-to-default-in-ubuntu/")and [http://www.starryhope.com/restore-the-default-panels-in-ubuntu/ ]("http://www.starryhope.com/restore-the-default-panels-in-ubuntu/")
 I hope this helps!

---

