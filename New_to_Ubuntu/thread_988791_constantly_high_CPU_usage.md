---
title: "constantly high CPU usage"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Matt26 on 2008-11-20
i have noticed recently when viewing System Monitor that my CPU usage appears to be unusually hight most of the time, regardless of what applications are running- usually in the 60-80% usage range.

is there a way i can determine what exactly is causing this to happen?  i have looked at my active processes lists under the System Monitor and FireFox is usually at the top of the list with between 20-30% usage on average- followed by the System Monitor process at around 20% usage.

i just want to figure out how to light the CPU usage because i have noticed my system being slightly unresponsive at times, which i believe to be a result of this.

thanks.

---

### Post by doas777 on 2008-11-20
well one of the problems is likely GSM itself. there are several bugs about that on launchpad.
[https://bugs.launchpad.net/gnome-system-monitor/+bug/93847](https://bugs.launchpad.net/gnome-system-monitor/+bug/93847)
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383)


try running top in a terminal
```
sudo top
```
and see what you are running at with gsm closed. if it is still high,make note of the process that is taking up the clocktime.

let us know what you find,
Franklin

---

### Post by rev0lv3r on 2008-11-20
Another nice app is htop

Don't use System Monitor to check your cpu load since it's so cpu intensive itself

---

### Post by davidsrsb on 2008-11-20
8.10 on an old Celeron 2.4 Ghz single core settles down to about 2% cpu load when just sitting there
The run away processes that used to affect me on 8.04 are all fixed these days

---

