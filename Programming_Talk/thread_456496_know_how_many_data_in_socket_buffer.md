---
title: "know how many data in socket buffer"
date: 2007-05-27
forum: Programming Talk
---

### Post by angustia on 2007-05-27
hi

there is some way to know how many bytes are in the receiving buffer of a socket?

i have some sockets and i make poll on them for many events but hangup events are received as read events (POLLIN) with 0 bytes; so right now i have to test POLLIN events with a false read (recv(s, buffer, buffer_size, MSG_PEEK)) to know if it is an incomming packet or a hang up. There's another more elegant way to know that?

thanks in advance

excuse my english.

---

### Post by gradedcheese on 2007-05-27
For what it's worth, your way is how I would have done it too.  It would be interesting to know if there are better approaches though.

---

