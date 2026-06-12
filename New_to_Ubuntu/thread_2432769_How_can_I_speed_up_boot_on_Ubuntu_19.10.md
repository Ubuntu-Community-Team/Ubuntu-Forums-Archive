---
title: "How can I speed up boot on Ubuntu 19.10?"
date: 2019-12-08
forum: New to Ubuntu
---

### Post by bjohas on 2019-12-08
Edit: The boot on Ubuntu 19.04 was super-fast, but with 19.10 the boot is taking around 2 minutes.

systemd-analyze gives
```
Startup finished in 9.736s (kernel) + 1min 36.475s (userspace) = 1min 46.211s 
graphical.target reached after 1min 36.225s in userspace
```
When I time the startup, it takes about 15 secs to get to the hang:
```
Started update utmp about system runlevel changes
```
(This suggests perhaps that utmp is not the problem - as the start of it is complete?) The screen then pauses for around 90 secs before arriving at the login, in line with the above values.

The recent ubuntu update (2019-12-08) claims to have improved things (?)
```
 systemd-analyze 
 Startup finished in 14.590s (kernel) + 4.267s (userspace) = 18.857s 
 graphical.target reached after 4.252s in userspace
```
However, despite these different values, the overall boot time of nearly 2 minus is not changed. So not sure why systemd-analyze reports it like that.

Changes I have tried: At the top of the list was NetworkManager-wait-online.service, so I did:
```
 sudo systemctl mask NetworkManager-wait-online.service
```
(see [https://forums.linuxmint.com/viewtopic.php?t=282437](https://forums.linuxmint.com/viewtopic.php?t=282437)).  While that removes time from NetworkManager-wait-online.service, it doesn't lead to a speedup overall.

Crossposted here: [https://unix.stackexchange.com/questions/556189/how-can-i-speed-up-boot-on-ubuntu-19-10](https://unix.stackexchange.com/questions/556189/how-can-i-speed-up-boot-on-ubuntu-19-10)

---

### Post by crip720 on 2019-12-08
Might have to use the 'disable' line also.  Should use [COLOR=#6A6A6A][FONT=Roboto]**systemd**[/FONT][/COLOR][COLOR=#545454][FONT=Roboto]-[/FONT][/COLOR][COLOR=#6A6A6A][FONT=Roboto]**analyze blame to see what is taking time.  Can usually google the stuff taking long time to see if safe to disable.**[/FONT][/COLOR]

---

### Post by Dennis N on 2019-12-08
There is also the hardware side of things. Especially, what type of disk(s) are you using? HDD? SATA SSD? NVMe SSD? Move up the ladder if you can.

---

### Post by bjohas on 2019-12-09
Thanks for comments - the boot is much slower than 19.04. The boot on 19.04 was super-fast, so it's not a hardware issue (am on SSD). Have updated post accordingly.

---

### Post by bjohas on 2019-12-22
With recent updates (as of 2019-12-22), the problem has gone away. The stats reported by systemd-analyze are
```
Startup finished in 11.021s (kernel) + 4.453s (userspace) = 15.474s 
graphical.target reached after 4.438s in userspace
```
and they are now accurate.

---

