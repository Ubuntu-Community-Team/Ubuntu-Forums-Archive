---
title: "Ethernet setup basics"
date: 2017-10-22
forum: New to Ubuntu
---

### Post by chootsmagoots on 2017-10-22
Hello, 

I'm a super-n00b when it comes to OSs and particularly linux, so forgive me for being completely lost on how to setup my ethernet connection from a terminal.  I got lubuntu installed and started trying to work, but my first sudo apt-get update failed, and after a little work, it seems to be that I am not connected to my LAN.  any help is appreciated.

Maybe part of the issue is that I'm only opening a terminal window... I really only need terminal, but lububtu seems to have more than that, which is something I had not realized... currently debugging that

---

### Post by The Cog on 2017-10-22
Is it a wired LAN or wireless?
Please post the output of these commands that print info:
```
ifconfig
route -n
```
and this one that will try to use dhcp to get an address (may take a minute to complete)
```
sudo dhclient
```

---

