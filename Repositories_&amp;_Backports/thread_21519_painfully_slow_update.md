---
title: "painfully slow update"
date: 2005-03-22
forum: Repositories &amp; Backports
---

### Post by wbeck85 on 2005-03-22
THis afternoon, the default hoary repositories are being painfully slow. THey ahve been updating for about 1/2 an hr now. Usually, i download from there at about 400-600 KB/s so this is a little weird. Anyone else experiencing this problem? Are the repositories being updated or something? what is wrong here?
I hope apt-get isnt broken....

---

### Post by kperkins on 2005-03-22
Same deal here. Real Slow updating.

---

### Post by wbeck85 on 2005-03-22
[QUOTE=kperkins]Same deal here. Real Slow updating.[/QUOTE]
 must be a server problem, glad the troubles not on my end. Hopefully it wont take to long to speed up again

---

### Post by wixtech on 2005-03-22
[QUOTE=wbeck85]THis afternoon, the default hoary repositories are being painfully slow. THey ahve been updating for about 1/2 an hr now. Usually, i download from there at about 400-600 KB/s so this is a little weird. Anyone else experiencing this problem? Are the repositories being updated or something? what is wrong here?
I hope apt-get isnt broken....[/QUOTE]
 I had the same problem today (@ 3:00pm CST) and I "solved" it by changing my sources from "us.archive.ubuntu.com" to just "archive.ubuntu.com" as listed in /etc/apt/sources.list.  Then just run an apt-get update and you're on your way to good transfer rates.  I will probably change back in a few days.  I hope this helps you out!

---

### Post by wbeck85 on 2005-03-22
[QUOTE=wixtech]I had the same problem today (@ 3:00pm CST) and I "solved" it by changing my sources from "us.archive.ubuntu.com" to just "archive.ubuntu.com" as listed in /etc/apt/sources.list.  Then just run an apt-get update and you're on your way to good transfer rates.  I will probably change back in a few days.  I hope this helps you out![/QUOTE]
 Awesome, thanks that worked. I wonder whats up?

---

### Post by micro_cz on 2008-04-25
having same problem on archive.ubuntu.com too .. all downloads are terrible slow, in 90 percent of attemps server refuses the connection

---

### Post by Strifer on 2008-04-28
I'm experiencing the same problem...I'm updating my ubuntu to 8.04 just right now...and god damn...the transfer is REALLY slow..

and seems that I can't stop the process..something about data losing and that stuff...=/

---

### Post by sjv123 on 2008-11-27
I have been having the same problems. Is it due to high traffic volume? 

I would be interested in using a torrent for updates, if traffic is the issue.

---

### Post by zloy on 2008-11-27
my 8.04 update download was slow today until I changed the repository server to "Main server" from "Server for Canada".
now it's flying up to 1MB/sec...

---

### Post by JabberWalkie on 2009-02-11
Ive been having this problem lately as well. This fixed it! Thanks guys! I'm not sure what is wrong with the Canadian mirrors by they all seem slow as molases.

---

### Post by unixeducation on 2009-02-11
I gave up on Canadian mirrors a long while back, after consistently getting 12 Kbps download rates on a cable connection.

---

