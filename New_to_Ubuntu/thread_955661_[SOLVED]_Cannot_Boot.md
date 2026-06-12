---
title: "[SOLVED] Cannot Boot???"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Meskarune on 2008-10-22
Currently when I try to Boot into Xubuntu 8.04 I see the xubuntu logo and progress bar for about 5 seconds. Then the screen goes to the command line and stops at

```
*Starting MTA                 ..._
```

The screen stays there and I cannot type anything and have to shutdown manually.

I can boot into recovery mode. 

The only things I've done to my system in the last week:
linux kernel updates
installed i2p
installed real player 11
Used Commandline to try and get permissions changed on my USB hard drive. (chmod)

otherwise I've just done the regular updates. 

I tried using the recovery mode to repair packages and the x server...but that didn't help. 

I am semi-familiar with the commandline. Is there logs I can look at to figure out whats going on?

---

### Post by Het Irv on 2008-10-22
Since Ubuntu is Debian Based this might help:
[http://datenroulette.de/blog/index.php?blog=4&title=starting_mta_takes_a_long_time&more=1&c=1&tb=1&pb=1](http://datenroulette.de/blog/index.php?blog=4&title=starting_mta_takes_a_long_time&more=1&c=1&tb=1&pb=1)

---

### Post by Crandom on 2008-10-22
MTA stands for Mail Transport Agent. If you can access the command line, try these commands:

tail /var/log/Xorg.0.log
tail /var/log/messages

you can load up a livecd and look at those logs if you can't get to a terminal.

---

### Post by Meskarune on 2008-10-22
Thanks so much! I typed in dpkg-reconfigure exim4-config and a TUI opened up with a mail server configurator. I told it I used internet mail and didn't need the local host to recieve stuff and then rebooted. 



While I was at the start up screen the progress bar got nearly to the end before crashing to the commandline. It stopped at *starting MTA again. But after about 30 seconds booted up. I then got the error :


"Could not look up internet address for Coconut. This could prevent XFCE from operating correctly. It may be possible to correct the problem by adding Coconut to the file /etc/hosts"



But Coconut (my computer) is already in /etc/hosts...



127.0.1.1 Coconut.meskarune Coconut.meskarune



I'll mess with my computer some more to try and figure out the weird boot sequence and the hosts file.



Thanks soooo much for your help! It was sooooooo painful booting into windows to post this thread...I'm happy to be back in linux. :)

---

### Post by Het Irv on 2008-10-22
> **Meskarune said:**
> 

Thanks soooo much for your help! It was sooooooo painful booting into windows to post this thread...I'm happy to be back in linux. :)

:lolflag:
Been there, had that pain.

---

### Post by Sarmacid on 2008-10-22
> **Meskarune said:**
> 
But Coconut (my computer) is already in /etc/hosts...



127.0.1.1 Coconut.meskarune Coconut.meskarune


Your hosts file should read
```
127.0.1.1 Coconut
```

---

