---
title: "Odd! PSFTP is suddenly not working..."
date: 2008-07-19
forum: New to Ubuntu
---

### Post by bvanpelt on 2008-07-19
I'm having an odd problem. I've been using PuTTY and PSFTP for a year or so, now. Putty works fine, and continues to work. I can connect to my remote production server and my local QA server just fine.

On the other hand, PSFTP has suddenly stopped working! Using a DOS window to run it I see "Fatal: Network error: Connection refused".

I haven't changed anything! Possibly someone has been playing with my desktop PC? Its odd that suddenly I can't FTP to either machine, yet I can PuTTY to both.

Any thoughts?

---

### Post by cariboo on 2008-07-19
Has something changed with the ftp services on both machines? Have you done an upgrade of some sort? Are the ftp ports open?

To find out if the ports are open use some sort of portmapping program like nmap. You can download it here:

[http://nmap.org/download.html](http://nmap.org/download.html)

Jim

---

### Post by bvanpelt on 2008-07-19
I forgot to mention, I'm using SSH. I believe (rightly?) that the ssh port is used for both SSH xterm & ssh ftp...

---

### Post by bvanpelt on 2008-07-20
Oh, sheesh! Two separate problems!
1) Original domain-name has expired on prod server; the shortcut used this old domain-name.
2) I had moved the SSH port on QA but had not modified the shortcut.

Duh!

---

