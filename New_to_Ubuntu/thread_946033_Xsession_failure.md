---
title: "Xsession failure"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by bolwarra_ on 2008-10-12
Hi,
I can't seem to boot into X. 
The last time my machine was running i was tweaking the boot splash with startup-manager.

After login I have the following XSession error.

----
gdm[24133]: WARNING: GDM file gdm-daemon-config.c: line 2033 (): Cannot run seteuid to 0: Operation not permitted.
GDM file gdm-daemon-config.c: line 2033 (): Cannot run seteuid to 0: Operation not permitted.
----

startx in terminal give me this... 

----
xauth: /home./blah/.Xauthority not writable, changes will be ignored
xauth: error in locking authority file /home/blah/.Xauthority
xauth: error in locking authority file /home/blah/.Xauthority
xauth: error in locking authority file /home/blah/.Xauthority

Fatal sever error:
Server is already active for display 0
	If the server is no longer running, remove /tmp/.X0-lock
	and start again

No protocol specified
giving up.
xinit: Resource temporarily unavailable (errno 11): unable to connect to X server
xinit: No such process (errno 3): Server error
xauth: error in locking authority file /home/blah/.Xauthority
---

I really need some help with this, so if anyone can help me correct the problem that would be great.
I can still access the internet with lynx et all

Cheers,
Tristan

---

