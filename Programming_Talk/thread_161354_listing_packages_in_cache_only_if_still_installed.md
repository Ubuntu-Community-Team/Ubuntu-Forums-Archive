---
title: "listing packages in cache only if still installed"
date: 2006-04-16
forum: Programming Talk
---

### Post by adam.tropics on 2006-04-16
Can't figure how to get apt-cache to do it, so tried this

> #!/bin/bash

sortandcompare ()
{
exec dpkg --get-selections > installed.txt &
sleep 2
awk '{print $1}' installed.txt > installedtemp.txt &
exec sort installedtemp.txt >installed.txt &
sleep 2
exec rm installedtemp.txt &
exec ls /var/cache/apt/archives >available.txt &
awk -F_ '{print $1}' available.txt > available1.txt
sleep 2
exec comm -1 -2 available1.txt installed.txt > finallist.txt &
exec rm available.txt &
exec rm available1.txt &
return 0
}

sortandcompare


which seems to work, could someone verify it for me..

---

