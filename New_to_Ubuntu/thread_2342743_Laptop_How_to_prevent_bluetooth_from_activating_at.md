---
title: "Laptop: How to prevent bluetooth from activating at startup?"
date: 2016-11-09
forum: New to Ubuntu
---

### Post by isolated-thinker on 2016-11-09
Greetings!

I am running 16.04 LTS on my Dell laptop. When I boot up Ubuntu, sometimes the Bluetooth will be activated and I have to manually turn it off. But, once and a while, Ubuntu will boot with Bluetooth turned off.

I am unable to find in the settings where I am able to set it up so the Bluetooth is always turned off when Ubuntu boots.

I was curious to know if anyone knows of a setting that I might be overlooking to keep Bluetooth turned off by default at boot?

Thanks!

---

### Post by oldrocker99 on 2016-11-09
In Startup Applications, there should be a Bluetooth program (probably called blueman) which you can uncheck and get rid of the annoyance.

---

### Post by Qew on 2016-11-09
The way I did it is as follows:

Edit the file /etc/rc.local, adding above the line that has "exit 0" the following:

```
rfkill block bluetooth
```

This will stop bluetooth from being loaded up on startup, but will allow you to start it if you ever want to use it. I originally got this answer from this [Ask Ubuntu page]("http://askubuntu.com/questions/67758/how-can-i-deactivate-bluetooth-on-system-startup"), which will give you further info about the issue and this fix.

---

### Post by isolated-thinker on 2016-11-10
Thank you guys! 
I didn't see Blueman in startup applications, so I had to do rfkill. 
Got it working (or not working, technically, lol)! My battery thinks you!

---

### Post by oldrocker99 on 2016-11-10
Since your problem appears to have been solved, please use the Thread Tools to mark this thread as [SOLVED].

---

