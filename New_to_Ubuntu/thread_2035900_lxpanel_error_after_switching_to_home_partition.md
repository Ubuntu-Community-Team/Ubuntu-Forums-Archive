---
title: "lxpanel error after switching to /home partition"
date: 2012-07-31
forum: New to Ubuntu
---

### Post by barronmo on 2012-07-31
Running Lubuntu 12.04 on AMD Sempron 2500

I just finished switching my home folder to my /home partition by following the directions [here]("http://help.ubuntu.com/community/Partitioning/Home/Moving").  I got error msg "Sorry, Ubuntu 12.04 has exerienced an internal error."  Sorry I can't post the entire msg but here are some relevant parts:

ExecutablePath: /usr/bin/lxpanel
ProblemType: Crash
SegvAnalysis: Skipped: missing required field "Disassembly"

Thanks, Mike

---

### Post by ajgreeny on 2012-07-31
Have you tried logging out and in again to see if all is now OK?

If you can't logout in the usual way because there is now no panel use **Alt Gr+Print Screen+K** to stop the xsession, which does the same thing, but in a less kind manner to any running apps.

---

### Post by barronmo on 2012-07-31
Unfortunately logging out and back in again didn't work.  In case this helps the contents of the /home partition were created using Ubuntu 9.04.

Mike

---

