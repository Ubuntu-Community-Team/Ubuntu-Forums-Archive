---
title: "system randomly freezing"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by DavidG24 on 2011-09-21
Hi guys,

I am currently running Ubuntu 10.10 x64 and recently the system seems to freeze up (generally when running a movie/tv show through vlc ..or media player). When I check the System Monitor, the CPU starts to fluctuate between 0 and almost 100% with absolutely no programs running (i.e. after I've killed the media). 

I have no idea as to whether this could be a problem with my version of ubuntu or the hardware I've got (listed below), but I've been running the computer for < 6 months (granted its had its fair share of different distros installed and uninstalled).

I'm not sure if this would have anything to do with it, but a friend was having a similar program after he installed wine1.3 - and so I was curious as to whether anyone had heard of anything like this occuring.

Also, if possible could someone provide the command to complete purge wine from my system, including any config files and menu items I would be very appreciative.

Thanks in Advance.

David

---

### Post by Lisiano on 2011-09-21
1) Where are the hardware specs?
2) Try looking at ```
iotop
``` and ```
top
``` at the same time.
3) I don't think wine could cause this as it's not running when there are not Windows programs open.
4) Just run ```
sudo apt-get purge wine1.3 wine wine1.3-gecko winetricks
``` Or go to System -> Administration -> Synaptic and mark the packages after the word "purge" as "Mark for a complete removal".

---

