---
title: "Random open ports"
date: 2014-07-30
forum: New to Ubuntu
---

### Post by geir765 on 2014-07-30
Hi! I just installed ubuntu 14. But when i do "sudo nmap -n -r -v -p1-65535 -sT 192.168.1.155". (scanning myself) I get random open ports. Like

PORT      STATE SERVICE
44554/tcp open  unknown
48523/tcp open  unknown

They don't show up in netstat -l. And idea what this might be??

---

### Post by TheFu on 2014-07-30
On my box, using **lsof** - some of these trace back to alsa and pulseaudio stuff.

---

