---
title: "Skype 4.0"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by Old-un on 2012-07-14
I got really fed up with Skype and since i have been running Ubuntu 12.04 haven't bothered at all. But just by chance i noticed an article about Skype 4.0 and was hoping that someone could tell me if this new version is easier to install and use before i actually attempt an install myself. Thanks

---

### Post by Pilot6 on 2012-07-14
What do you mean by "easier to install"?
Previous version could be installed either from repo using Software Manager or apt-get. Or e.g. by double-clicking the deb file and pressing install.
4.0 can be downloaded as a deb file. Just double-click it and press install. What can be easier?

---

### Post by Old-un on 2012-07-14
Yes you are correct Pilot6. What i meant to say was did Skype users find the new version 4.0 did away with the sound problems that were always a pain in the old 2.2 version?

---

### Post by drpjkurian on 2012-07-14
I've been using skype version 4 for the past few weeks, No issues at all. Go ahead and install

---

### Post by Old-un on 2012-07-14
I installed Skype version 4 and everything even my old Logitech webcam worked great except the sound.

When i tried to make a test call all i got back was static? Plus the following: To change sound settings you need to use your Desktop Manager volume control or PulseAudio volume control.

I was tempted to open a terminal and type:
```

sudo apt-get purge PulseAudio

```

But was afraid that by doing so would affect other software on my computer?

---

### Post by markbl on 2012-07-14
I use skype chat + calls + video quite a bit. There are a number of good improvements and fixes in skype 4.

---

### Post by hakermania on 2012-07-14
> **drpjkurian said:**
> I've been using skype version 4 for the past few weeks, No issues at all. Go ahead and install

I can confirm this.

---

### Post by NikTh on 2012-07-14
> **Old-un said:**
> I installed Skype version 4 and everything even my old Logitech webcam worked great except the sound.
Hi ,
Try these two commands as workaround.. one at time , and see if sound work 

```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
``````
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so  skype
```Skype 4.0 works very well for me too.

Thanks

---

