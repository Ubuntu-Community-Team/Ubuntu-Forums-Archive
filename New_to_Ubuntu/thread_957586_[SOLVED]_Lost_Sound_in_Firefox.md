---
title: "[SOLVED] Lost Sound in Firefox"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by Chrissd on 2008-10-24
Hi, last week everything was running perfectly on my computer. This week I've come back to my computer, and I can't hear sound in videos (e.g youtube videos, but not just youtube). They used to work fine!

When Ubuntu starts up, it plays the start sound, Rhythembox still works fine, and videos outside of Firefox work fine. I'm at loss!

Thanks in advance! :)

---

### Post by LowSky on 2008-10-24
There is a known bug that when trying to play flash based media that the sound will not work while also trying to use a multimedia player like rythmbox or banshee. I think its an easy fix

---

### Post by LowSky on 2008-10-24
sudo apt-get install libflashsupport
then restart firefox browser

---

### Post by Chrissd on 2008-10-24
Fantastic, works again!

Is there a simple explanation for this?

---

### Post by LowSky on 2008-10-24
yeah the explanation is that flash is horribly built for linux...lol

---

