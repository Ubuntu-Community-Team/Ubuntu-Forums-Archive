---
title: "xconfig issue"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by 440corbon on 2012-03-18
I got tired of having to reset my nvidea drivers every boot up so started playing. My start up always gave me a max res. of 1920 by 1200 or so. so somewhere in process I botched my drivers. Can't seem to get my nvidea started now. any help would be appreciated
TIA

---

### Post by 2F4U on 2012-03-18
I really can't identify what your question is. Do you get the wrong resolution, black screen or something else? What configuration have you done after installing the drivers?

---

### Post by NikTh on 2012-03-18
Hi , 
How you botched you drivers ? what did you do ? uninstall them , or did you "play" with xorg.conf ? if you open a terminal and write ```
apt-cache policy nvidia-current
``` what is the output ? and ```
 cat /etc/X11/xorg.conf
``` what is the output ?

---

