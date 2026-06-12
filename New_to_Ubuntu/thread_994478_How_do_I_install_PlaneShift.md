---
title: "How do I install PlaneShift?"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by RadiationHazard on 2008-11-26
I just downloaded the bin and I tried this
```
jordan@jordan-laptop:~$ cd ~/Desktop
jordan@jordan-laptop:~/Desktop$ sudo su
[sudo] password for jordan: 
root@jordan-laptop:/home/jordan/Desktop# ./PlaneShift-v0.4.02-x86.bin
bash: ./PlaneShift-v0.4.02-x86.bin: Permission denied
root@jordan-laptop:/home/jordan/Desktop# 

```

but as you can see it didn't do anything. :confused:

---

### Post by wirelessmonkey on 2008-11-26
try:
sudo chmod +x ~/Desktop/PlanesShift-v0.4.02-x86.bin
sudo sh ~/Desktop/PlanesShift-v0.4.02-x86.bin

---

### Post by RadiationHazard on 2008-11-26
Solved!

[http://gaming.gwos.org/doku.php/guides:32bit:planeshift]("http://gaming.gwos.org/doku.php/guides:32bit:planeshift")

---

