---
title: "kernel debugging with netconsole"
date: 2007-03-18
forum: Programming Talk
---

### Post by oboontoo on 2007-03-18
For some reason my ubuntu just freezes from time to time and I was hoping I'd see some kernel messages if I installed netconsole, but I'm not having any luck getting any messages sent.

I've added the following as kernel boot params ```
netconsole=4444@192.168.0.10/eth1,6666@192.168.0.100/00:0D:87:AA:C9:00
```

Where:
192.168.0.10 is the IP of my Ubuntu box I'm trying to 'debug'.
eth1 is the network interface on my Ubuntu box.
192.168.0.100 is the IP of my WinXP PC where I'm running NetCat on port 6666.
00:0D:87:AA:C9:00 is the mac address of the network card on my WinXP PC.

On my WinXP I'm running
```
nc -l -p  6666 -u

```
But nothing seems to get sent to it.

Any ideas what might be wrong? The two boxes can ping each other just fine.

---

