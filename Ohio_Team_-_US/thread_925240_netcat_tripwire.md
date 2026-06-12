---
title: "netcat tripwire"
date: 2008-09-20
forum: Ohio Team - US
---

### Post by zerhacke on 2008-09-20
Been working on a tripwire through netcat for some time.  All it does is fakes a ssh server prompt, and when the person connecting to it inputs anything it gets dumped to a text file along with their complete hostname.

It's done through a perl script and makes heavy use both WHILE statements and a perl implementation of getch I found on the net.

It's pretty fun, really.  All those southeast Asian bot networks usually have ssh set up on their system and you wouldn't believe the amount of dumb scans the crackers use with their own username and password first off the bat.

---

