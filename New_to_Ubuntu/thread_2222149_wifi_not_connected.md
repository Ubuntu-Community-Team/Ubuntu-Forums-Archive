---
title: "wifi not connected"
date: 2014-05-05
forum: New to Ubuntu
---

### Post by tom87 on 2014-05-05
just started comcast isp and want to connect to wifi.  did so with dell inspiron using xp but now having trouble doing so with compaq presario using ubuntu.  one thing i would like to do is remove the various wifi networks i tried to connect to, all named HOME-FBFE and appear on the list.  since none work for wifi, do not want to keep trying and have a list of many and the do not know what to choose to connect to wifi.  currently using wired but want to take compaq to library but afraid it will not work there if it does not work at home.  thanks for your help.

---

### Post by windowsfree on 2014-05-05
open up a terminal and do the following.  it will ask you to input your password.

sudo modprobe -r presario-laptop
sudo rfkill unblock all
rfkill list all

---

