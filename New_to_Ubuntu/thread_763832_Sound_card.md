---
title: "Sound card"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by pariksakurikar on 2008-04-23
well i installed ubuntu and the codecs required for mp3 n all...but i dont hear sound and i dunno how to manage my sound card...can someone pls help?

---

### Post by sayakb on 2008-04-23
Open a terminal and type :
```
sudo apt-get install linux-backports-modules
```
Then reboot your computer.

---

### Post by aeiah on 2008-04-23
in the menu you should be able to go to audio / video and select 'sound' for mixer settings. what soundcard do you have, and do you also have onboard sound? ubuntu may be using your onboard soundcard, or perhaps your soundcard isnt supported (x-fi isnt supported very well right now but almost all others are)

---

