---
title: "I can't start the X after a forced shutdown"
date: 2013-09-25
forum: New to Ubuntu
---

### Post by herbert tamayo on 2013-09-25
Hi, I was downloading some files but I forgot to connect my laptop to the AC, so when it ran out of battery it turned off, when I tried to turn it on I got the log in welcome page ( where I can select the desired user account), but after type the password, ubuntu tries to load the X but after 2 or 3 minutes I returned to the log in page, so maybe it's a problem related with the forced shutdown.

my questions are:
1. where shall I check what error is?
2. how can I reload the x?

I'm using ubuntu 12.04

thank you and best regards

---

### Post by dshgna on 2013-09-25
I think it may be an issue with the password. I had a complication once where the correct password would not be accepted by the login screen but would get accepted in the login that appears after clicking switch user. You could try it.

If it does not work, try going to recovery mode from the boot menu and start start x from the commandline with startx.

---

