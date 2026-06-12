---
title: "sound was working, now not"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by cgkades on 2008-09-07
I had my sound working, now it stopped. i'm lost

```

brett@you-bunt-who:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

---

### Post by chrismcb on 2008-09-07
maybe you need to reinstall a driver.  im not sure though

---

### Post by cgkades on 2008-09-07
> **chrismcb said:**
> maybe you need to reinstall a driver.  im not sure though

how it was automaticly set up?

---

### Post by chrismcb on 2008-09-07
it could have automaticly set it up right when you installed ubuntu, then somehow stoped working or something.  This is just a guess, but i think re-installing the driver would be something to try.

---

### Post by cgkades on 2008-09-07
> **chrismcb said:**
> it could have automaticly set it up right when you installed ubuntu, then somehow stoped working or something.  This is just a guess, but i think re-installing the driver would be something to try.

any hints on how?

---

### Post by chrismcb on 2008-09-07
> **cgkades said:**
> any hints on how?

hmmmm..... i looked it up, I couldnt find a driver, but apparently it is a problem on that type of sound card  :(   but it seems that some people have found some luck

[http://www.linuxforums.org/forum/gentoo-linux-help/99291-intel-82801g-ich7-family-high-definition-audio-controller-microphone-problem.html](http://www.linuxforums.org/forum/gentoo-linux-help/99291-intel-82801g-ich7-family-high-definition-audio-controller-microphone-problem.html)

[http://forums.fedoraforum.org/showthread.php?t=195804&mode=linear](http://forums.fedoraforum.org/showthread.php?t=195804&mode=linear)

apparently they a package or two, and it works for some of them.  some of the names are alsa and atrpms.

---

### Post by cgkades on 2008-09-07
> **chrismcb said:**
> hmmmm..... i looked it up, I couldnt find a driver, but apparently it is a problem on that type of sound card  :(   but it seems that some people have found some luck

[http://www.linuxforums.org/forum/gentoo-linux-help/99291-intel-82801g-ich7-family-high-definition-audio-controller-microphone-problem.html](http://www.linuxforums.org/forum/gentoo-linux-help/99291-intel-82801g-ich7-family-high-definition-audio-controller-microphone-problem.html)

[http://forums.fedoraforum.org/showthread.php?t=195804&mode=linear](http://forums.fedoraforum.org/showthread.php?t=195804&mode=linear)

apparently they a package or two, and it works for some of them.  some of the names are alsa and atrpms.


the first link is for microphone problems, but i'll look into it a little more, and the second one is for fedora. i DID however reinstall alsa. still not working

---

### Post by cgkades on 2008-09-07
none of the info from the links seemed to work

---

### Post by chrismcb on 2008-09-08
man, im really sorry, but i have  no idea.  maybe if anyone else has any ideas?

---

### Post by bobnutfield on 2008-09-08
Try opening a terminal and typing:

> aplay -l

This will list all devices that are available to the system.  If your card is shown, try:

> /etc/init.d/alsa-utils reset

---

