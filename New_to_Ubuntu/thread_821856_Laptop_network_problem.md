---
title: "Laptop network problem"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by GreenfieldMark on 2008-06-07
So I'm attempting to move a large file from one computer to another via a wireless network. Both computers are using Ubuntu 8.04, but the laptop is having some problems. Every so often, during the transfer, everything on the laptop will freeze. The progress bar will stop moving, the system info applet will stop moving, and altogether it looks as though the computer has frozen up. 

Everything seems to start up again when I move the mouse though, implying there's some program taking over when the computer is idle. However all network activity stops. The laptop is still connected to the network and the signal is still coming in strong, but the file transfer has stopped completely and has to be restarted. This also happens when downloading large amounts of update, though it seemed fine when I upgraded from 7.10 to 8.04. To me, this points to a problem with 8.04 that wasn't in 7.10. 

The only thing I could think of was the search/tracker program, but the problem keeps cropping up even now that I've stopped it. I've also checked the power management settings, but there was nothing there that could cause a problem. Has anyone else had any similar issues? Any ideas on how to fix this? 

I could have just been really unlucky these past couple of days, but it seems to me that networking is a place where Ubuntu fails miserable to be usable by the average computer user.

---

### Post by spiderbatdad on 2008-06-07
Take a look at the syslog file System>>Administration>>System Log>>SysLog
Maybe the wireless connection is dropping.

Run a couple of terminals during the transfer like: sudo netstat -catnup and another terminal with Htop or ps aux to try to see what is happening. Also maybe run your file transfer through the terminal.

---

### Post by GreenfieldMark on 2008-06-07
So I tried it again using your suggestions and discovered the touchpad lost synchronization at about the same time the transfer stopped. Since I didn't see anything out of the ordinary with HTOP or sudo netstat -catnup and since it appears to have happened before according the system log, I'm betting this is the problem. 

So any idea on what to do about it?

Edit: Upon running it again and checking the syslog, not just the messages, I discovered this message: > Microcode SW error. Restarting 0x82000008

This appears to be what led to the touchpad losing synchronization.

---

### Post by spiderbatdad on 2008-06-07
Several bugs reported regarding that error:[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/226134](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/226134)
Google the error may lead to a fix. The above link looks promising.  Or may be related to the method used to configure wireless card driver.

---

