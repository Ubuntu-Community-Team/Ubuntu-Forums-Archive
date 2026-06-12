---
title: "Setting up UTC time"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-04-25
How would I go about setting up the clock to display UTC time instead of 12 or 24 hour local time?

---

### Post by ajmorris on 2008-04-25
if you are using gnome, you can just right click on the clock in the taskbar, and click adjust date and time, and select UTC as the TimeZone, if you are not using gnome, there are other methods :)

AJ

---

### Post by alienexplorers on 2008-04-25
In Hardy I checked under time zones and there is no listing for UTC time.  Where else can I go to have my time changed to UTC?

---

### Post by ajmorris on 2008-04-25
you can go to /etc/default/ and edit the file rcS by changing the line UTC=no to UTC=yes. Then invoke tzconfig, which will ask if you want to change the time zone. On getting the answer "y" it will ask you to choose from among geographical regions 1) through 11) or "12) None of the above." Answer 12, then select either UTC or Zulu. 

The effect is immediate and survives subsequent reboots.

---

### Post by alienexplorers on 2008-04-25
I can't seem to find tzconfig.  where is it located so I can run it?

---

### Post by kpkeerthi on 2008-04-25
See [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

### Post by ajmorris on 2008-04-25
> **alienexplorers said:**
> I can't seem to find tzconfig.  where is it located so I can run it?

you may have to install tzconfig first... (tzdata is the package name iirc)

AJ

---

### Post by alienexplorers on 2008-04-25
Got it running Thanks.

---

### Post by trmentry on 2008-05-15
I'm having a bit of a problem

I have xubuntu installed.  

I did a tselect and chose None for the option then entered.
UTC+0 
for my zone. 

But the clock still shows up as London in the GUI.  

The Hardware clock is set to UTC.  And I have /etc/default/rcS UTC=yes

What am I missing?

Thanks

---

