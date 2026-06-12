---
title: "asterisk and ubuntu 12.04"
date: 2013-08-13
forum: New to Ubuntu
---

### Post by sebabatso on 2013-08-13
HI 

I have followed a tutorial on [http://ubuntuforums.org/showthread.php?t=1780326](http://ubuntuforums.org/showthread.php?t=1780326) ([SIZE=2][ Asterisk 1.8 with MySQL Realtime Support]("http://ubuntuforums.org/showthread.php?t=1780326")[/SIZE] ) trying to setup asterisk 1.8.10 with realtime. the whole idea is to get a2billing runninng. However i have a problem, after following the tutorial and doing everything there, i am not sure of how to test if asterisk is really connected to mysql realtime database. can any one please help me out with the command or technique to use to ensure that asterisk really see the database. I tryed "realtime mysql status" on the asterisk CLI and it is not recognised.

---

### Post by slickymaster on 2013-08-13
You can edit your **logger.conf** file to enable debug output so that debug info is written to [B]/var/log/asterisk/ 
[/B]See [Collecting Debug Information]("https://wiki.asterisk.org/wiki/display/AST/Collecting+Debug+Information")

---

