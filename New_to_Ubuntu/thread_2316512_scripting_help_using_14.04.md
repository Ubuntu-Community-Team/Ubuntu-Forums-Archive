---
title: "scripting help using 14.04"
date: 2016-03-08
forum: New to Ubuntu
---

### Post by rburkartjo on 2016-03-08
take a look at this script. it hibernates for 60 sec then reboots to the boot menu and when i reboot it loads to what i had before i ran the script. it is only suspose to suspend for 60 secons;

#1/bin/bash
echo xxx | sudo rtcwake -m disk -s 60

/tlks

---

