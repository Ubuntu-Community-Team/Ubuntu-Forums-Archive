---
title: "pppd and PHP"
date: 2012-07-12
forum: Programming Talk
---

### Post by geger on 2012-07-12
Hi

I need to establish a connection with a modem by php and be sure that the connection is good.

I make a pppd script that works well if I launch it from the bash. However, when I had difficulties when I wanted to use PHP. 

I use the exec function exec('/usr/sbin/pppd call script', $result) but PHP doesn't wait for the command to terminate, so I only can try a few second later to manually check if it is ok and I cannot read the return message ($result is empty).

I tried using the updetach option in the pppd script. With it, PHP wait for the function, I can read the return message but the connection close just after being established.
I have no idea what configuration I should use.

If someone can help me it would be very nice.

---

