---
title: "trouble with SDL/openGL"
date: 2009-02-06
forum: Programming Talk
---

### Post by tneva82 on 2009-02-06
I'm trying to set up SDL and openGL for coding. I followed guide I found here:

[http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development](http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development)

SDL example code compiled and ran without errors. Huray! I then proceeded to openGL. Unpacked it, ran configure executable without errors, compiled and then tried to run. Here's error messages that popped up.

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15

I'll take it it's something to do with my settings but where should I be looking?

---

### Post by Ferrat on 2009-02-06
that problem is not in your dev files but with your graphic driver I think, had a similar problem a while back, try purging and reinstalling the graphic driver and see if that helps

---

### Post by tneva82 on 2009-02-06
> **Ferrat said:**
> that problem is not in your dev files but with your graphic driver I think, had a similar problem a while back, try purging and reinstalling the graphic driver and see if that helps

Hum. I did reinstal drivers I downloaded from AMD webpage. Didn't help though :( Nor did rebooting linux.

Edit: Activating drivers from system->administration->hardware drivers did though. Now back to looking how to get that damn WoW running :D

---

