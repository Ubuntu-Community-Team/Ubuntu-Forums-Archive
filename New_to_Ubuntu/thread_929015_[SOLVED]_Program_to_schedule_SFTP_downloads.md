---
title: "[SOLVED] Program to schedule SFTP downloads?"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by erudite on 2008-09-24
Is there an FTP program for Ubnutu to schedule downloads (needs to have SFTP support)?

If not would anyone like to tell me the best program to use for SFTP if they think they know the best one?  At the moment I use filezilla but i'm open to suggestions.

---

### Post by ProgramErgoSum on 2008-09-24
FTP and sFTP are mutually exclusive. Scheduling can be left to a script controlled by cron.

Couple of links for you :
[how do I...sshd with sftp]("http://ubuntuforums.org/showthread.php?t=322900")
[Ubuntu-How to sFTP]("http://www.funnestra.org/ubuntu/hardy/#sftp")

---

### Post by erudite on 2008-09-24
Yes, I guess that post wasn't well worded.

Thanks for the links i'll take a look.

---

### Post by The Cog on 2008-09-24
**scp** is probably the command you need to schedule.

Use **cron** for regular jobs, or **at** for scheduling a one-off job at a later time.

---

### Post by erudite on 2008-09-24
Ok thanks dude.

---

