---
title: "Printer Connection to Microsoft XP from Ubunto 8.10"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by Jim Rimedio on 2008-10-14
[FONT="Georgia"]On one box I am running Ubuntu 8.10 connected to a Microsoft Windows XP box with a [FONT="Georgia"][/FONT]wired network. When I first installed this distribution, I could print from the Ubuntu box to a printer connected to the XP box.  Then one day, it stopped printing from the Ubuntu box.  After searching, I found the following: 


"log.blackcomputer

[2008/05/30 13:41:34, 0] lib/util_sock.c:read_data(534)
  read_data: read failure for 4 bytes to client 192.168.1.101. Error = Connection reset by peer"

What does the message mean and what do I do to correct the error?[/FONT]

---

### Post by dhtseany on 2008-10-14
When you installed the printer, you needed to tell Ubuntu where the printer was located. When you specified the XP box did you say "xp-box" (DNS driven name) or IP address? If it was the IP address then maybe the address on the XP box changed?

Just a thought

Peace
Sean

---

