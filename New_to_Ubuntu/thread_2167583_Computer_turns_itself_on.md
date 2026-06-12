---
title: "Computer turns itself on"
date: 2013-08-14
forum: New to Ubuntu
---

### Post by Scott_Green on 2013-08-14
I have had a problem with my computer that i got from work (it had the hard drive wiped so I installed Ubuntu). 
I turn it off before i go to bed and then when i wake up in the morning it is back on!
I caught it in the act last night - it literally started up itself at 3am(GMT).
Does anyone know what might be causing this?

:KS

---

### Post by TheFu on 2013-08-14
Are you certain it isn't in hibernate or standby mode and a mouse move didn't wake it?
Are you certain nobody is sending WoL - Wake On LAN - packets to it?
Are you certain the BIOS is not setup to wake up for backups overnight?
Are you certain there isn't an electrical short in the power button?

Anyway - those are things that I'd check.

---

### Post by matt_symes on 2013-08-14
Hi

In relation to WOL, try unpluging the network cable,  if it is a wired connection, or disable WOL in the BIOS. 

Does it still wake up ?

Kind regards

---

### Post by Scott_Green on 2013-08-14
Thanks for the suggestions,

I shall try disabling the WOL when I get home.
The computer is not connected to the internet just now (it was connected via network cable) but last night there was no connection. Not sure if that makes a difference or not...

---

