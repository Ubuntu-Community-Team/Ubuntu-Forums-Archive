---
title: "clock/calendar disappeared from Unity panel"
date: 2011-09-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jcphil on 2011-09-07
I don't see any way to get it back. Any ideas?

---

### Post by MacUntu on 2011-09-07
I'm sure I'm missing some evolution package or so, but I have no idea which one. I do see the clock in the panel, but I don't get a nice calendar on opening it.

---

### Post by tychocity on 2011-09-07
same problem

---

### Post by cariboo on 2011-09-07
I noticed that I didn't have a calendar the other day to, I thought is was because I set the clock to show month/day/time, but checking again to day under Time & Date Settings that the Monthly Calendar was unticked. Enabling the calendar worked for me

---

### Post by cariboo on 2011-09-07
merged two threads on the same subject.

---

### Post by jcphil on 2011-09-07
Hmm! I don't have "Date & Time" anywhere in System Settings. I tried a search and it took me to an unrelated screen.

> **cariboo907 said:**
> I noticed that I didn't have a calendar the other day to, I thought is was because I set the clock to show month/day/time, but checking again to day under Time & Date Settings that the Monthly Calendar was unticked. Enabling the calendar worked for me

---

### Post by cariboo on 2011-09-07
Click on the clock on the panel.

---

### Post by jcphil on 2011-09-07
The reason I posted was because there is no clock on my panel.

---

### Post by Hreinsi on 2011-09-07
> **cariboo907 said:**
> I noticed that I didn't have a calendar the other day to, I thought is was because I set the clock to show month/day/time, but checking again to day under Time & Date Settings that the Monthly Calendar was unticked. Enabling the calendar worked for me

Missing calander too Time and date settings are set to calander 
Clock is still there

---

### Post by Johnb0y on 2011-09-07
could try: [https://wiki.ubuntu.com/TimeAndDate](https://wiki.ubuntu.com/TimeAndDate)

---

### Post by Hreinsi on 2011-09-07
Unity --restore did it again calander is back

---

### Post by MacUntu on 2011-09-07
> **cariboo907 said:**
> merged two threads on the same subject.

Not the same subject. :P

But thanks, the calendar item was unchecked, now it's back again!

:guitar::guitar::guitar:

---

### Post by mc4man on 2011-09-07
> **jcphil said:**
> Hmm! I don't have "Date & Time" anywhere in System Settings. I tried a search and it took me to an unrelated screen.
Check if indicator-datetime is installed

---

### Post by jcphil on 2011-09-07
> **mc4man said:**
> Check if indicator-datetime is installed

It was not. Don't know how it got uninstalled. But it's back now!

---

### Post by Johnb0y on 2011-09-08
please remember to put this issue as solved. thanks.

---

### Post by VinDSL on 2011-09-08
Late to the party...

On my install, sometimes the calendar appears - sometimes it doesn't.

Once it disappears, it won't reappear until I reboot.

This is the only indicator that quits working for me, during a session.  All the rest, work all the time...

---

### Post by VinDSL on 2011-09-08
> **cariboo907 said:**
> I noticed that I didn't have a calendar the other day to, I thought is was because I set the clock to show month/day/time, but checking again to day under Time & Date Settings that the Monthly Calendar was unticked. Enabling the calendar worked for me
I'll check that, next time it happens - probably in a few minutes.  :)

Thanks!

---

### Post by pmanski on 2011-09-09
> **jcphil said:**
> It was not. Don't know how it got uninstalled. But it's back now!

It's not a solution.

indicator-datetime wants to install evolution-data-server-common. 
In this version Ubuntu - Thunderbird is replacing the Evolution.

---

### Post by cariboo on 2011-09-09
> **pmanski said:**
> It's not a solution.

indicator-datetime wants to install evolution-data-server-common. 
In this version Ubuntu - Thunderbird is replacing the Evolution.

Create a bug report, with relevant logs.

---

