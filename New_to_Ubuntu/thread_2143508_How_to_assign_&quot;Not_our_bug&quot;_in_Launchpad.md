---
title: "How to assign &quot;Not our bug&quot; in Launchpad?"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by abcuser on 2013-05-09
Hi,
I use several bug tracking systems (also Launchpad). Sometimes there is a situation that end-user reports a bug that is not directly associated with a program that bug is reported against. For example end-user report a bug that program is not working, but the source of the problem is some upstream library that has bugs or there is a bug in Ubuntu itself that influences the program end-user is reporting bug against. So program maintainer can't do much in this case, he/she can report a bug to upstream and wait for an upstream fix. In this case this is classical upstream bug. For this purpose bug tracking system BugZilla has a bug STATUS of "Not our bug". I can't see anything similar in Launchpad, is it? What is recommended status to set in this case?

P.S. Can someone point me to the system where bugs are reported for Lauchpad, to check if there is some wish already reported to add "not our bug" or something similar for bug status.
Thanks

---

### Post by Cheesehead on 2013-05-09
Add the proper package or project.
Change the status on yours to "Invalid"
Explain the change in comments.

---

### Post by abcuser on 2013-05-09
If setting status=Invalid, then bug is closed and if multiple users are having the same problem, then there is bug chance any other user will open a new bug with the same problem. IMHO, Invalid status is not the best one... I was thinking of setting some tag or something to know bug is upstream bug. Also if bug is set to Invalid (so bug closed down) and this bug is reported for development version of program, that final stable release can be released without checking if upstream bug was fixed, so there should be no stable release of program released if upstream bug is not fixed, because your stable release is actually non-stable.

---

### Post by Cheesehead on 2013-05-10
If it's an upstream bug, leave it open and use the "Remote Bug Watch" feature. Launchpad will monitor the upstream bug if it uses any common tracker, and automatically update the status based on the upstream bug. It's usually in the right-hand column, at the bottom.

Example bug with a Remote Bug Watch: [https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/535517](https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/535517)

Coincidentally, the same bug shows how a bug can be assigned to more than one package/project/upstream, and can have a different status in each, to prevent the duplication problem you describe. The example shows how Invalid can be used properly, yet the bug remains open.

---

