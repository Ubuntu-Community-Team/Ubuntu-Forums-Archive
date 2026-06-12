---
title: "Hard shutdown instead of restart."
date: 2017-06-08
forum: New to Ubuntu
---

### Post by crip720 on 2017-06-08
Running 16.04 with intel baytrail.( I have the work around)  On rare times need to do a hard shutdown when ubuntu wants a restart after update.  Restart and shutdown not related, just bad timing.  Just wanted to know what happens to do the update?  Does the update operation finish if a hard shutdown is done instead of a restart or soft shutdown?  Thank you.

---

### Post by ian-weisser on 2017-06-08
Debian, by default, installs upgrades in the background while you are working - unlike Windows which installs at shutdown. Everything is *already installed* before you get the restart prompt. The purpose of the restart is to reload the (new) kernel at boot. Restarting vs shutdown should make no difference at all.

One exception: There's a little-known, almost-never-used setting in /etc/apt/apt.conf.d/50unattended-upgrades that WILL change install-in-the-background to install-at-shutdown. If you happen to discover and change that setting, then a 'hard shutdown' at the wrong time may corrupt your system quite badly. Don't do that.

---

### Post by crip720 on 2017-06-08
Thank you, knew that restart or soft shutdown did not make a difference, did not know if hard shutdown would.  System has needed two hard shutdowns when restart was required, but system seems to be okay.  Will mark as solved.

---

