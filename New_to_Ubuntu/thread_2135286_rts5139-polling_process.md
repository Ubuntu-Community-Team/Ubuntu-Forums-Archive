---
title: "rts5139-polling process"
date: 2013-04-13
forum: New to Ubuntu
---

### Post by putStrLnNick on 2013-04-13
Simple question, but google searches caught mostly real-time-strategy-related pages. The pages I did find on the other "rts" seemed to assume the reader knew what it was. It seems to be some kind remote connection protocol, but I'm not sure and would appreciate an explanation. I'm concerned (perhaps a bit paranoid) given the difficult I had finding any info on this and because I keep seeing a process called rts5139-polling show up when I run quantal. In particular, I'm not sure whether this means it's my computer that's being "polled" or I'm the one doing the polling. Any form of explanation is appreciated. Thanks!

---

### Post by zrdc28 on 2013-04-13
That is your card reader polling, if you don't use it just remove it, an easy way to try it is, open terminal  sudo nano "/etc/rc.local " type in "rmmod rts5139"  ctrl x and save. reboot and you it will be gone.

---

