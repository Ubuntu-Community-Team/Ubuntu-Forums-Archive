---
title: "Time Synchronization (NTP) is ~45 seconds ahead than it supposed to be"
date: 2016-06-07
forum: New to Ubuntu
---

### Post by simba4 on 2016-06-07
[LEFT]
Ubuntu 14.04, 64bit,


Hi all,


I noticed that the computer's time is about 45 seconds ahead of the cellular time (that is the correct time locally).


I checked using _[this page]("http://blogging.dragon.org.uk/setting-up-ntp-on-ubuntu-14-04/")_ and my settings seem to be identicle.
Don't really know what to do next.


_My servers are_:
server 0.ubuntu.pool.ntp.org
server 1.ubuntu.pool.ntp.org
server 2.ubuntu.pool.ntp.org
server 3.ubuntu.pool.ntp.org
# Use Ubuntu's ntp server as a fallback.
server ntp.ubuntu.com


Someone gave me his local time server:  **Israel-IX.iix.net.il**

Is it possible that there is such a gap between the servers?


What do you think I should do about that?


Thank you,

James
[/LEFT]

---

### Post by TheFu on 2016-06-07
Don't trust cellular networks to be perfectly correct. Perfect time isn't a priority for them and isn't a requirement for their security to work. They just need to be *close enough* for the encryption to work correctly.

Check against a government time server for your location.  In the USA, that is [http://time.gov/](http://time.gov/). I'm seeing times accurate to within my ability to tell - so within 0.2 sec ... that that's inside a VM, running a remote desktop client.

I've never used more than 3 NTP servers, BTW.

Saw this warning about Israel on the ntp.org site.
> There are not enough servers in this zone, so we recommend you use the Asia zone

---

### Post by mastablasta on 2016-06-09
moving slightly to the east will make the time correct :D

---

