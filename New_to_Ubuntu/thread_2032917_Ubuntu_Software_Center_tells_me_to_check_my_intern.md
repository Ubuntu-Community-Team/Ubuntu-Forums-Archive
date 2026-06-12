---
title: "Ubuntu Software Center tells me to check my internet connection"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by ArlieS on 2012-07-24
I got a system76 machine pre-installed with ubuntu 12.04. I opened the box, put everything together, turned it on, answered its questions, and all seemed well - if a bit strange.

Approximately the next two things I did were to check that my internet connection was working (e.g. by opening up Firefox), and find the "Ubuntu Software Centre" and start trying to install additional programs. 

The first program installed correctly. So did the second. The third gave me some kind of failure report, and told me to check my internet connection. Fortunately it also gave me the URL it was trying to access to fetch the software, and I was able to use Firefox to explore. [I]The version it was trying to install wasn't present on the download site, though several other versions were. 

[/I]If I'd been really new to linux, I'd have been stuck until Monday, when my vendor's support line would have been available. Fortunately I'm only new to *Ubuntu*, so I was able to fix the problem. However, I imagine a bug should be filed for this, and I haven't a clue how to get the needed information to file a decent bug report. So I guess the support help I'm requesting is help filing the bug :biggrin:

1) From the messages, Ubuntu software centre is implemented using apt-get
2) From the behaviour, it failed to issue "apt-get update" to determine that the list of available software had changed between the day the system was installed and the day I opened the box
3) From exploring root's (ana)cron jobs, I see that there's a cron job to do "apt-get update" 

The bug is 
(1) in situations like mine, the new owner isn't going to wait for a daily cron job to run before playing with their new system, and deciding they really need their favourite game/editor/email client/etc.
(2) the error message returned by the "Ubuntu software centre" is misleading and somewhat scary.  My internet connection was fine - and had just been used to download 2 other pieces of software.  

IMNSHO, the software center should, at a minimum, suggest the possibility of an out-of-date table of available applications when it fails to find one. Better yet, it should simply do "apt-get update" routinely, or at least offer to - after all, AFAIK, most experienced system administrators do "apt-get update" at the start of any session of installing software, and usually follow up with "apt-get upgrade" as well.

---

### Post by waynefoutz on 2012-07-25
Try clicking one Edit/Software Sources when Software Center is open, then in the "download from" dialog, choose "other." Then in the next dialog that omes up, choose "select best server, and click "apply."

---

