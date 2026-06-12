---
title: "Error on Boot up recovering journal."
date: 2019-10-03
forum: New to Ubuntu
---

### Post by igcd on 2019-10-03
Hello,

I have a server running Ubuntu 16.04 and it runs fine for a day or two but then all of a sudden with no warning it powers off and this message shows up (i have attached a picture)


I power down the server and start it again. Then it is back to normal for another day or so and then back to the same error.

I have never come across this issue before. What could be causing this?

---

### Post by Skaperen on 2019-10-04
if it powers down, how does it show those messages?  do you power it back up and then get those?  are you plugging a 5 or 6 pin round keyboard connector?

---

### Post by Holger_Gehrke on 2019-10-04
Those messages sadly won't help you in diagnosing the problem. It's just the results of a forced fsck after an uncontrolled shutdown. The journal mentioned in the first message is the filesystem journal (not the system wide journal of messages you'd access using 'journalctl'; same name, very different things). Basically some inodes are marked as "in use" but there's no filename associated with them. You should check the logs (/var/logs/syslog) and the journal ('journalctl -b -1' to look at entries from the previous boot). Look for unusual messages towards the end of either

Holger

---

