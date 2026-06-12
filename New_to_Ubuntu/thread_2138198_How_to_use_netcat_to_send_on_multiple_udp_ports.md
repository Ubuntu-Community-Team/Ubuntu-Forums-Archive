---
title: "How to use netcat to send on multiple udp ports?"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by makmuzy on 2013-04-23
Hi,

i want to use netcat to send serial port /dev/ttyS0 to any UDP ports.

i use "nc -u 10.0.6.2 222 < /dev/ttyS0 9600 8N1" and it works! :p

but i need to send to many others ports on same host eg: 222-230 if possible (i use ubuntu server without desktop).

i try "nc -u 10.0.6.2 222-230 < /dev/ttyS0 9600 8N1" and "nc -u 10.0.6.2 222 223 < /dev/ttyS0 9600 8N1" but not work.


Thanks,
Max.

---

