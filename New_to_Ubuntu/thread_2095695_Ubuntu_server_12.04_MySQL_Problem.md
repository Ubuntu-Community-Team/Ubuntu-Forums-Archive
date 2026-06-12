---
title: "Ubuntu server 12.04 MySQL Problem"
date: 2012-12-17
forum: New to Ubuntu
---

### Post by mihajlo92 on 2012-12-17
Got the server up and running, it's working and I got remote control enabled. My Problem is that I can connect from other pc's i tested it and it's working i have access to mysql database, but I also got a website up and running which is not on my server and it doesnt have acces to my databases. Like I said i can connect using remote control with HeidiSQL from any computer but not from a website. I also got php5-mysql installed. What's wrong? :/

---

### Post by GordThompson on 2012-12-18
Is the website hosted by a hosting provider? If so, they may be blocking outbound connections to the port you're trying to use.

---

