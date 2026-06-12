---
title: "Tips on stopping blink of LED lights"
date: 2011-06-28
forum: Outdated Tutorials &amp; Tips
---

### Post by imigyjunia on 2011-06-28
When data is being transferred via wireless network,the blinking LED  light indicates the wireless is on.This tutorial shows how to stop this  annoying blinking light,and so that your laptop has a constant on (or  off) LED light when wireless’s working (or not).
 Open up a terminal window from *Applications -> Accessories -> Terminal*,use  following command to edit the “/etc/modprobe.d/wlan.conf” file (if it’s  not existent,the command will create one with blank).
 gksudo gedit /etc/modprobe.d/wlan.conf add this line at the end of the file,and save it.
 [INDENT]options iwlcore led_mode=1
[/INDENT] Now,restart your machine and problem should be fixed !

---

