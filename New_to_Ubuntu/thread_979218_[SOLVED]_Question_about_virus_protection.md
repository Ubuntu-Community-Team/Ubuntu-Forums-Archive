---
title: "[SOLVED] Question about virus protection"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-11-11
I was just curious if there was a virus scanning program that can be run from Ubuntu LiveCD and scan a Windows XP machine for viruses?

---

### Post by waffleturd on 2008-11-11
ubuntu is generally safe from viruses

---

### Post by UbuntuNerd on 2008-11-11
I think you could use a Linux live CD and ClamAV to scan it but Im not 100 percent sure.

---

### Post by slughappy1 on 2008-11-11
That is not my question. My question is, can I scan a WINDOWS XP drive for viruses. My friends computer is an XP machine that has a virus I think. But his computer can't do really anything because of it.

---

### Post by lisati on 2008-11-11
My own preference on Windows is for the free version of AVG. There is a Linux-friendly version but I had heard that support for it is likely to end.
[http://ubuntuforums.org/showthread.php?t=889552](http://ubuntuforums.org/showthread.php?t=889552)

---

### Post by inxygnuu on 2008-11-11
No, to answer your question, Ubuntu comes with very little virus protection, because uUbuntu gets very little viruses. I can tell you some good programs If you are only scannng your windows because it wont start. Personally, i would simply back everything up, and at that point, just wipe the drive if it wont start.

---

### Post by slughappy1 on 2008-11-11
Well see I don't know where the virus is. So I don't want to take the chance of keeping it around when I back up the computer. I plan on backing it up tomorrow and re-installing everything. But I was hoping to be able to scan it first and make sure it doesn't come along for the ride.

---

### Post by Crafty Kisses on 2008-11-11
Ubuntu ships with no open ports on public interfaces. In other words, a "port scan" would show all closed ports, nothing open. As a result, putting up a firewall would provide no more security than not putting one up, so it really doesn't matter.

If you must have some Anti-Virus program though, you might want to try "AVG" or something to that nature.

---

### Post by lisati on 2008-11-11
Am I missing something here? I think the original poster wants to use an Ubuntu CD with suitable AV software on it to help fix a Windows machine. If so, one option would be to create a custom CD with some kind of AV software added.

---

### Post by Matt26 on 2008-11-11
> **lisati said:**
> Am I missing something here? I think the original poster wants to use an Ubuntu CD with suitable AV software on it to help fix a Windows machine. If so, one option would be to create a custom CD with some kind of AV software added.

my thoughts exactly- my guess would be that you can't use a live disc to scan a windows installation, as they are two different operating systems by design and a linux-based antivirus software will look for infections on a linux-based installation- provided this understanding of how antivirus software operates at the root level is in any way accurate.

can you even boot into safe mode in XP?  if you are able to do this, you might want to try downloading and installing MalwareByte's AntiMalware... this is one of the most thorough and effective antivirus software programs i have used recently, and it has resolved a number of nasty infections for me that other prorgams such as AVG could not take care of (or even detect).

---

### Post by ghost_ryder35 on 2008-11-11
> **slughappy1 said:**
> I was just curious if there was a virus scanning program that can be run from Ubuntu LiveCD and scan a Windows XP machine for viruses?
I understand wanting to use linux for this but UBCD4WIN was created just for this.
[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

---

### Post by handydan918 on 2008-11-11
> **inxygnuu said:**
> No, to answer your question, Ubuntu comes with very little virus protection, because uUbuntu gets very little viruses. I can tell you some good programs If you are only scannng your windows because it wont start. Personally, i would simply back everything up, and at that point, just wipe the drive if it wont start.

And to correct your answer to his question, yes , it can be done. Maybe not with an Ubu disk, if it doesn't ship with clamav, but for pete's sake, it isn't impossible.


Practically speaking tho, the best way to repair a virus issue is to backup and hose the system. Windows is just sooo fragile...

---

