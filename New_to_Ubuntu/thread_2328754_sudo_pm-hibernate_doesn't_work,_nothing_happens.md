---
title: "sudo pm-hibernate doesn't work, nothing happens"
date: 2016-06-24
forum: New to Ubuntu
---

### Post by andy181 on 2016-06-24
Hi, everyone! I am trying to get my newly switched to Ubuntu 16.04 LTS, installed on a HP 15-f039wm to hibernate but I have not had success. I have a 500GB HDD and 8GB RAM. I tried creating a swap file which I think is enabled, but still when I type "sudo pm-hibernate" nothing happens, I had even tried command lines from similar threads, still nothing. I just switched from Windows, I feel awkward but intrigued at the same time, I have seen pretty Linux savvy people in this forum, please help. :( Thank you.

---

### Post by Geoffrey_Arndt on 2016-06-24
So, are you saying if you leave your laptop on for certain amount of time, it won't automatically go into suspend (light sleep) and then hibernation (deep sleep)?    What power settings are you using? (System Settings>Power . . . the settings are for two states (battery power, AC power)).

About swap file, . . . there is no such thing as enabled or not.   Either the swap file is present (it exists), or it doesn't . . . simple as that.    You can tell by running gparted (preferably from a Live DVD or USB Flash-Stick).   The visual display will show if your swap file is there . . . (or use the "Disks" program as an alternative).   Depending on how much RAM you have, allocate the same or slightly more for swap.

---

