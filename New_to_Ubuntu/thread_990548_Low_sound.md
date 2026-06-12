---
title: "Low sound"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by r5gtt2k3 on 2008-11-22
Hi, Made a clean install on the laptop (Dell Latitude D830) And i have al the codecs installed, But when i play media (music/video) the sound is very quiet even with the volume max, Is there a way to get it louder ? like it should be 

Thanks

---

### Post by chazn85 on 2008-11-22
give 

```
 
sudo apt-get install alsa-tools

```
a try then 

```

alsamixer

```

adjust them all to max and you should be ok

---

### Post by r5gtt2k3 on 2008-11-22
Thanks that worked after some fiddling around :D

---

### Post by chazn85 on 2008-11-22
no worries glad it worked for you

---

### Post by dromichaetes on 2009-06-26
chazn85,
 
thank you. great help. it worked just fine after installing alsa-tools and running alsamixer. I run Ubuntu Jaunty 9.04 on a Dell D830 and the sound was really poor out-of-the-box. 
 
But your fix worked great. Thanks!

---

