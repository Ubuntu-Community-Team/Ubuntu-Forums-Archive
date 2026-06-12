---
title: "No Sound"
date: 2014-01-31
forum: New to Ubuntu
---

### Post by Leagh_Raven on 2014-01-31
Hey, so I decided to finally switch away from Windows. Everything is great, except the lack of sound. I don't seem to have a volume control even. Help?

---

### Post by jshanks24 on 2014-02-01
Here is a guide for [Troubleshooting Linux Sound Issues]("http://www.troubleshooters.com/linux/sound/sound_troubleshooting.htm"). Let me know if it helps.

---

### Post by Gone fishing on 2014-02-01
I think you may have problems with divers and hardware starting in the middle of the guide given above what happens if you run ```
alsamixer
``` and ```
sudo lshw | grep Audio 
```or ```
sudo lspci | grep Audio
``` from a terminal?

---

