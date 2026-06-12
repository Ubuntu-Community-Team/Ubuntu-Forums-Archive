---
title: "Start a program at a certain time"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by mishathegoat on 2008-09-09
Hello everyone,

I have (legal) torrents that can only be started late at night when my roommates are asleep so that it does not interfere with their internet usage. I was wondering if it there is some application that will allow me to open/close my torrent program at a set time.

Please, any help is appreciated.

MishaTheGoat

---

### Post by iaculallad on 2008-09-09
> **mishathegoat said:**
> Hello everyone,

I have (legal) torrents that can only be started late at night when my roommates are asleep so that it does not interfere with their internet usage. I was wondering if it there is some application that will allow me to open/close my torrent program at a set time.

Please, any help is appreciated.

MishaTheGoat

If you want, you could install ktorrent as it has a good scheduler plugin. You can configure it to run only on specified time and turn it off on internet usage peak hours.

---

### Post by Greyed on 2008-09-09
Yes, cron, it comes standard with any unix.

Though personally I manage my torrent speeds with the clients that I use.  So far all clients that I have used in the past few years allow you to rate limit the speed at which they download and upload.  In fact the 2 clients I used recently, Azureus and KTorrent, both had schedulers that would allow you to slow-down, or stop, your up/download speeds during peak usage hours and ramp it up later on when noone is apt to be using the network.

---

### Post by t0p on 2008-09-09
**cron** will be able to do what you want.

```
man cron
``` for info on usage

---

### Post by mishathegoat on 2008-09-09
The scheduler plugin for ktorrent is perfect thats exactly what I was looking for thank you. And thank you everyone else for your quick responses.

---

### Post by vishzilla on 2008-09-09
Just in case for future

There are two scheduling options
1. at (for one time)
2. cron (for recurring)

Refer the man pages they are helpful
```
man at
man cron
```

---

