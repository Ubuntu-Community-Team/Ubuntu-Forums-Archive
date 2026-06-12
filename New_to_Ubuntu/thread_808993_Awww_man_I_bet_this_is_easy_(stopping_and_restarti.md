---
title: "Awww man I bet this is easy (stopping and restarting)"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by cackles on 2008-05-27
I just tried 4 times to stop azureus on a remote connection (PuTTY) but it wont, instead it has stopped showing downloads on the HTML remote connection and started adding more downloads (unknown what because I cant get in).

Ive tried azureus halt and stop.

I get 'command not found'.

All I wanted to do was stop it and enter via XMING/GUI on an XP machine, my Azureus install is on a headless.

Ive rebooted and instead of 'resetting' itself and restarting I just keep getting errors and a blank webgui download screen, the other pages for it appear to work.

This is its favourite error:

```
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-6-openjdk/jre/bin/java
[GUI] StartServer ERROR: unable to bind to 127.0.0.1:6880 listening for passed torrent info: Address already in use
StartSocket: passing startup args to already-running Azureus java process listening on [127.0.0.1: 6880]
```

Now I cant remember how to kill it completely and start it off again and its never listened on port 6880 cus I changed that at install :/

---

### Post by stueng on 2008-05-27
If you want to kill a process just type sudo killall processname..i.e

sudo killall azureus

If you want to see a list of processes running you can type ps -x to limit the output to one page at a time type px -x | more and to show processes that match a certain string type ps -x | grep azureus for example

to kill a specific PID type kill -9 PID (where PID is a number)

Stu

---

### Post by cackles on 2008-05-27
Thanks stu, that helped indirectly. What I had to do was take it out my startup and use that, though after a reboot it shouldnt have still been running with it removed from rc.local.

I had to restart, go in through the gui and what did I find there? All the stop commands I used as 'torrents'. I then deleted them all off and the html side on my client machine came up, not a great thing I admit :( Must be a bug, like it shouldnt have froze up like that, it should have given me errors on the HTML page.

All it took was 'azureus <command>' and it was broke, where be the 'invalid torrent location/name message'? Cant max it out again though. Was downloading a torrent @ 800-900 and now its barely breaking 400 ... gonna have to check that out because even on that machine it maxes out at 2.2MBish, max from my top machine is 2.85MB/sec.

All in all ... not mellow, but I guess its just as well its only a 30GB HDD for the master, or whatever its called in linux :) and this is all practice! I'm past reinstalling now, I have reinstalled around 40 times in the 2 weeks or so Ive had Ubuntu to 'try and perfect it'. Im glad I got it working again.

Again, stu, thanks for the swift reply.

---

