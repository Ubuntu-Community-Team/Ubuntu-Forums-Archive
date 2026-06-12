---
title: "Should Apport pop up automatically?"
date: 2011-08-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-08-01
Apport is enabled according to '/etc/default/apport', crash files go to '/var/crash', but Apport is never popping up asking me to report the crashes - should this currently work?

---

### Post by mc4man on 2011-08-01
It works here _for most_ crashes, but I do clean var/crash quite often (usually daily
If the same keeps coming up and nothing new to report I leave the .crash which makes it more likely not to create a pop up.

---

### Post by MacUntu on 2011-08-01
Thanks, I will monitor the crash directory more closely from now on. :-/

---

### Post by MacUntu on 2011-08-02
Four new crashes, no Apport (which should have shown up for at least three of those crashes). :(

---

### Post by mc4man on 2011-08-02
I'm not getting many crashers lately though most pop up
This one always pops up but only occurs occasionally and does cause issues
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/810145](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/810145)

This one is a pita, as long as I leave in /var it doesn't pop up. within 30 min. of removing it does. The thing is nothing seems wrong at all..
 [https://bugs.launchpad.net/ubuntu/+source/libx11/+bug/507062](https://bugs.launchpad.net/ubuntu/+source/libx11/+bug/507062)
I would feel silly asking if apport-gtk is installed so won't

---

### Post by mc4man on 2011-08-05
Not surprisingly, since the other day now never get the apport pop up 'reporting' window.
Just OSD messages (and in unity no <whatever it's called> indicator icon

---

### Post by MacUntu on 2011-08-05
FWIW, I made it a bug report the other day:

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/820391](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/820391)

---

### Post by mc4man on 2011-08-05
> **MacUntu said:**
> FWIW, I made it a bug report the other day:

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/820391](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/820391)

Do you get an OSD message?

---

### Post by Starks on 2011-08-05
i get 50 apport messages in a row

close one, two spawn in its place

---

