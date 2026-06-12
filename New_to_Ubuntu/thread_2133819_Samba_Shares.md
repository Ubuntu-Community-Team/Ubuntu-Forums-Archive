---
title: "Samba Shares"
date: 2013-04-09
forum: New to Ubuntu
---

### Post by Habanero101 on 2013-04-09
Hi guys, I have a problem where I shared some drives using Samba on Ubuntu Release 12.10 (quantal) 32-bit; but the shared pc and its drives drop out of the Windows' PC network, the drop outs I think is random, thought it did happen twice in the middle of transfer some very large video files from one pc (Ubuntu) to the other PC (Windows), but I also notice that some other times windows will be unable to find the Ubuntu pc and a few minutes later it will. 

When the Ubuntu pc dropped out, I did a ping test from windows and it couldn't transfer any packets, when the windows pc was connected to the Ubuntu pc in networks, the ping test time was average 1ms.

Any ideas on what could be causing this erratic behavior and how to remedy it?

---

### Post by jeSah8ci on 2013-04-09
It seems that some user reported it on the SuperUser forums... the [answer that claimed to solve the issue]("http://superuser.com/a/262598") had also tried two other things before, so it may have been a combination of those three.

But the most important one seems to be the one I'm linking to:

> [LIST=1]
[*]Disconnect any existing mapped drives
[*]Map a new drive; check the boxes for "Reconnect" and "Use different credentials"
[*]When you are prompted, enter SERVER\USERNAME for the user name. For example, if your server's name is SHIRE, and the user name is Baggins, enter SHIRE\Baggins for the user name.
[*]Enter the password as usual.
[*]Check the "remember credentials" box.
[/LIST]


---

### Post by Habanero101 on 2013-04-09
Thanks, I read the thread you posted; but with my problem, I don't have to re-enter credentials, the windows pc automatically reconnects afterwards. And when I reboot, it is automatically connected. My problem is with somehow automatically disconnecting at random points for a period of time of I estimate, 10 minutes or so.

---

### Post by Habanero101 on 2013-04-11
Anyone else think they can help me out here?

---

