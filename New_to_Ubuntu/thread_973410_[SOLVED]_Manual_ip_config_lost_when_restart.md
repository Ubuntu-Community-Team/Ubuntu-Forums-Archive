---
title: "[SOLVED] Manual ip config lost when restart"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by drakeman007 on 2008-11-06
Hello, guys, anyone have the problem that every time i restart ubuntu it resets my ip configuration to dhcp and i have to set the config again, and i do this everytime i restart! anyone have any info or solution for this?  :confused::confused::confused:
thanks in advance.
Ubuntu version : Intrepid IBEX

---

### Post by Iowan on 2008-11-06
[Other threads]("http://ubuntuforums.org/showthread.php?p=6119911") suggest Network Manager has a bug that doesn't allow saving settings.  Advice there was to remove NM and manually edit */etc/network/interfaces*.

---

### Post by drakeman007 on 2008-11-06
> **Iowan said:**
> [Other threads]("http://ubuntuforums.org/showthread.php?p=6119911") suggest Network Manager has a bug that doesn't allow saving settings.  Advice there was to remove NM and manually edit */etc/network/interfaces*.

Im going to try that iowan, thanks ,i write back to you if this works.... Awesome!!!!:popcorn:

---

### Post by drakeman007 on 2008-11-07
> **Iowan said:**
> [Other threads]("http://ubuntuforums.org/showthread.php?p=6119911") suggest Network Manager has a bug that doesn't allow saving settings.  Advice there was to remove NM and manually edit */etc/network/interfaces*.

Thanks, it works, just removed and edit the files and done... for future references o question about this

1st i removed network manager
```
sudo apt-get remove network-manager
```

2nd I edit the file 
```
sudo gedit /etc/network/interfaces
```
with my ip settings....

3rd
```
sudo gedit /etc/resolv.conf
```
and i add the DNS
nameserver 200.75.200.2 example.!
you can add more than one if you wnat

4 Restart the interface file
```
sudo /etc/init.d/networking restart
```



regards.

---

### Post by iponeverything on 2008-11-07
Its not necessary to remove NM -- it will just ignore any interface that is configured via /etc/network/interfaces

---

### Post by Iowan on 2008-11-12
Although this thread is tagged [SOLVED], [this]("http://ubuntuforums.org/showthread.php?t=974382") How-To proposes a solution.

---

### Post by drakeman007 on 2008-11-12
> **Iowan said:**
> Although this thread is tagged [SOLVED], [this]("http://ubuntuforums.org/showthread.php?t=974382") How-To proposes a solution.

Thanks awesome guide iowan... really appreciate

---

### Post by kelargo on 2008-11-14
> **iponeverything said:**
> Its not necessary to remove NM -- it will just ignore any interface that is configured via /etc/network/interfaces

Network Manager seemed to ignore the entries and the system did not have any IP Address.

---

