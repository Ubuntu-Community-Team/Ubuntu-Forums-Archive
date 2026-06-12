---
title: "[SOLVED] setting wireless card to monitor mode."
date: 2008-05-29
forum: New to Ubuntu
---

### Post by untermensch on 2008-05-29
I have a bcm4318 wireless chip, and I wanted to know how to set it to monitor mode and to take it out of monitor mode. Can anyone help?

---

### Post by quelx on 2008-05-29
[http://ubuntuforums.org/showthread.php?t=539385](http://ubuntuforums.org/showthread.php?t=539385)

---

### Post by cdtech on 2008-05-29
```
sudo iwconfig wlan0 mode monitor ## monitor all packets on the frequency
or iwconfig wlan0 mode managed ## connects to a network
```

If wlan0 is your wireless.

---

### Post by untermensch on 2008-05-29
ok, so I got it to work. However, now I can't get my wireless card to pick up networks when it's not in monitor mode. How can I fix that?

---

### Post by untermensch on 2008-06-29
Never mind. [SOLVED]

---

