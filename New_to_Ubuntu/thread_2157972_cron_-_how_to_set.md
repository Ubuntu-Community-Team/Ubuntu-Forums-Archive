---
title: "cron - how to set?"
date: 2013-06-27
forum: New to Ubuntu
---

### Post by elementX on 2013-06-27
Hi,

I need to set a script to run every 4 hours.
I have it like this at the moment:
*               */4             *               *               *               /path/to/script

I am not sure about minutes - should it be '0' or '*' ? Is the rest of it OK?

---

### Post by Kujua on 2013-06-27
Minute should be 0. If you put * it will run your script once every minute in the matching hour, ie 60 times. If you put it 0 your script will be run only once at the start of the hour.
Rest look okay.

---

