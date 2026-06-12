---
title: "XP to Ubuntu w/serial cable"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by tomcatdad on 2008-09-27
I have connected a PC w/ Ubuntu to a PC with XP using a serial cable (performance is not an issue, and I have a cable). I have zip experience with Ubuntu, studied Unix using Linux back in collage (have B.S. in C.S.)need to expand my computing knowledge base. So, to start, how do I ping the two PCs? thanks

---

### Post by nsche on 2008-09-28
First you need a "null modem" cable.  You can make it with a cable having pin 2 on one end connected to pin 3 on the other and vice versa.  Set up communications using ppp (point to point protocol).  I don't know if it is included with XP but the Ubuntu end should be easy to set up using "network settings" (System->Administration->Network) to configure a Point to Point connection.

---

