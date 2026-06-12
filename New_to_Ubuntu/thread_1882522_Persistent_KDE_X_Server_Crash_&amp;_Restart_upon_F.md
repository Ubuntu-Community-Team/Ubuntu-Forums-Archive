---
title: "Persistent KDE X Server Crash &amp; Restart upon FIrefox Startup"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by GregA on 2011-11-17
X server crash and restart will happen consistenly given the following scenario:

1.   Running Kubuntu 11.04 and Kubuntu 11.10.
2.   Runing KDE desktop v4.6 or newer.
3.   Initial session logout.
4.   Subsequent session login.
5.   Executing Firefox causes immediate black screen (x-crash and restart).

After this crash and restart, invoking Firefox again will not cause a further issue (e.g., Firefox will now start normally).

IF there is NO logout from the initial X session, but instead the user initiates the "switch user" operation, the subsequent login and startup of Firefox will not cause the X crash and restart.

IF there is a system "restart" versus "session logout", there is no issue with X crash/restart upon starting up Firefox.

Also, Firefox is the only browser triggering these crashes, . . . . no such issues with Chromium, Opera, or other non-FF browser. 

Am running KDE 4.7x on a Lenovo 410 with integrated Intel graphics, 4 gb ram.  

Any ideas/suggestions are welcome.

---

