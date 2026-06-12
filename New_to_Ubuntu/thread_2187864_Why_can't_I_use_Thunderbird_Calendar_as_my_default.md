---
title: "Why can't I use Thunderbird Calendar as my default Calendar application?"
date: 2013-11-14
forum: New to Ubuntu
---

### Post by Lammis on 2013-11-14
Hi
I am using Ubuntu 13.10 [64 bit] and wonder if it is possible to use the Thunderbird Calendar Lightning 2.6.2 as the default calendar application. Today the only option is Evolution.

[ATTACH=CONFIG]247810[/ATTACH]

---

### Post by philinux on 2013-11-14
Is this package installed on your system?

```
sudo apt-get install xul-ext-lightning
```

---

### Post by Lammis on 2013-11-14
> **philinux said:**
> Is this package installed on your system?

```
sudo apt-get install xul-ext-lightning
```

Yes, it is.

---

### Post by philinux on 2013-11-14
Only hit i can find is this. [http://askubuntu.com/questions/76921/how-do-i-set-lightning-as-the-default-calendar-app](http://askubuntu.com/questions/76921/how-do-i-set-lightning-as-the-default-calendar-app)

I use evolution with google calendar since it syncs with my desktop, laptop and smart phone.

---

### Post by philinux on 2013-11-14
Only hit i can find is this. [http://askubuntu.com/questions/76921/how-do-i-set-lightning-as-the-default-calendar-app](http://askubuntu.com/questions/76921/how-do-i-set-lightning-as-the-default-calendar-app)

I use evolution with google calendar since it syncs with my desktop, laptop and smart phone.

---

### Post by vanadium on 2013-11-14
For me, leafpad is indicated as default Calender application in Settings - Details :) It is apparently difficult for the Ubuntu developpers to include Lightning as a default calendar in the system: the calendar even is not installed by default.

As a matter of fact, I do not really know what I am missing by lightning not being the default calendar.

---

### Post by Lammis on 2013-11-14
> **vanadium said:**
> For me, leafpad is indicated as default Calender application in Settings - Details :) It is apparently difficult for the Ubuntu developpers to include Lightning as a default calendar in the system: the calendar even is not installed by default.

As a matter of fact, I do not really know what I am missing by lightning not being the default calendar.

I use Lightning since I had it synch with my Google account and it was available as an add-on to Thunderbird which is my mail client. I don't like Evolution as a mail client and you are not able to only use the Evolution calendar, right?

---

### Post by vanadium on 2013-11-14
I am also using Thunderbird and Lighting. In fact, it was when I moved to Thunderbird that Canonical decided to make it the default email client :lolflag: Evolution is not installed by default, only the backend evolution-data-server is: if it is mentionned in your details, then you must have installed it at one time. But again: what is the added feature of a "default" calendar"? I just load thunderbird when I need my calendar.

---

### Post by mc4man on 2013-11-14
> **vanadium said:**
> For me, leafpad is indicated as default Calender application in Settings - Details :) It is apparently difficult for the Ubuntu developpers to include Lightning as a default calendar in the system: the calendar even is not installed by default.

As a matter of fact, I do not really know what I am missing by lightning not being the default calendar.
The "Defaults" panel is only going to show apps that have a .desktop file (and of those there can't be a "NoDisplay=true" line
So not missing anything

And, at least here, the timedate indicator > 'Add event' option is worthless in a default install

---

### Post by Lammis on 2013-11-15
> **vanadium said:**
> But again: what is the added feature of a "default" calendar"? I just load thunderbird when I need my calendar.

Well it is not like I can't use the calendar to anything I need but it is the satisfaction of having a complete system that is not just for fun but rather thought through and seamlessly integrated. In my upper right corner I have the Ubuntu date and time. If I click that I see a calendar and have an option to add an event. That is the "default calendar" i.e. Evolution. If I get an electronic contact card via e-mail or from a web site it opens up in the default contact list and it happens to be Evolution. Also meeting requests opens up in Evolution.

So it is just me. I want to have one calendar that is used whenever me or the system need a calendar.

---

### Post by mc4man on 2013-11-15
They decided something here but hasn't resulted in any thing yet.( that I can see...
[https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/957779](https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/957779)

The option shouldn't even be there in a default install until either TB support is enabled or evolution is installed 
(in 13.04 the option only shows once evolution is installed, 13.10 i don't know, in 14.04 the option is present by default

---

### Post by Silvernail on 2013-12-11
> **Lammis said:**
> 
So it is just me. I want to have one calendar that is used whenever me or the system need a calendar.
No it it not just you.  I have been using Evolution since I started using Ubuntu. Now all of a sudden, it won't save my new entries.

What all is Evolution linked to in Ubuntu?. Can I just delete everything?

---

