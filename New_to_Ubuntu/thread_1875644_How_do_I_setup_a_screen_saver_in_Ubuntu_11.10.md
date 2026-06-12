---
title: "How do I setup a screen saver in Ubuntu 11.10?"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by Qu0ll on 2011-11-05
I have gone through all the System Settings but can't see anything for a screen saver.  How can I configure one?

---

### Post by orange2k on 2011-11-05
try:

```
sudo apt-get install xscreensaver
```

---

### Post by Qu0ll on 2011-11-05
OK thanks, I have done that but how do I turn it on or configure the screen saver?

---

### Post by owenll on 2011-11-05
> **Qu0ll said:**
> OK thanks, I have done that but how do I turn it on or configure the screen saver?


I used the instructions here to enable screensaver in 11.10: [http://www.liberiangeek.net/2011/10/enable-screensavers-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/10/enable-screensavers-in-ubuntu-11-10-oneiric-ocelot/)

---

### Post by brothersman on 2011-11-05
I typed in 
sudo apt-get install xscreensaver

and this is whats returns


Reading package lists... Done
Building dependency tree       
Reading state information... DoneReading package lists... Done
Building dependency tree       
Reading state information... Done
Package xscreensaver is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  xscreensaver-data

E: Package 'xscreensaver' has no installation candidate

So I typed sudo apt-get install xscreensaver-data

Same things returns

---

### Post by brothersman on 2011-11-05
Never mind I figured it out, changed my software sources to different server!

---

### Post by Qu0ll on 2011-11-05
> **owenll said:**
> I used the instructions here to enable screensaver in 11.10: [http://www.liberiangeek.net/2011/10/enable-screensavers-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/10/enable-screensavers-in-ubuntu-11-10-oneiric-ocelot/)

Thanks, that worked nicely :p

---

