---
title: "SSH File Transfers Slow To Crawl"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by KevinD_Atl on 2008-05-06
[FONT="Georgia"]So I have a SSH server setup on Ubuntu 7.04.  I connect to it via Windows WinSCP and connect fine.  WHen I start transfering files, it starts strong; 250KBS+ but then slows down to 45Kbs or even slower.  Anything to look at why this just starts slowing down? The connection where the server sits is cable, and download from a 20+ MB pipe, so I don't think it's bandwidth. I have the port forwarded for both UDP and TCP...[/FONT]

---

### Post by Cypher on 2008-05-06
So you are connecting to your Linux server externally with a cable link? If that's the case, then it's normal for it to start off at a high rate and then slow down and stabalize at a slower rate as the transfer continues. 

That's basically how cable is going to work..it's not sustained speed. If you're on Comcast or something, their speedboost technology will burst for a short period and then sit at the slower rate..

Realize that it's your upload pipe from the server that is the limiting factor and cable is fast at download, but slower at upload..

---

### Post by KevinD_Atl on 2008-05-06
Yep, I am on Comcast.  This makes total sense, the total speed overall is good anyway, just wondering why it would slow like that.

---

### Post by Cypher on 2008-05-06
The slowdown really becomes noticable with large files as you'll see it start off with great haste only to slow down to a number significantly less than what it started at. :)

However, on smaller files the bursting technology does it's thing and the files get transferred faster.

---

