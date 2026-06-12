---
title: "port 22: Connection refused"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by know-it-some on 2008-08-14
Here's an odd one.  I believe that I have completely disabled the firewall on my new ubuntu server, yet I still get the following when I try to ssh to it:

port 22: Connection refused

The method I used for disabling the firewall was to isse the following:
lokkit --disabled

That did not work so now I tried:
ufw disable

and then: 
ufw status

Which yeilded:
Firewall not loaded

So if it were indeed a problem with the firewall blocking port 22 despite my efforts to turn it off, how would I determine that?  What log would I look in?  Thanks!

---

### Post by Gannon8 on 2008-08-14
For some reason, trying to use vncviewer from the terminal gave me the same problem, but gnome's Remote Desktop program worked. I do not get it either.

---

### Post by spiderbatdad on 2008-08-14
did you sudo apt-get install openssh-server?

---

### Post by know-it-some on 2008-08-15
I did now :0

I am not used to that not being installed with the base system. How does the saying go? "A server with ssh is like a fish without a bicycle"?

---

