---
title: "wireless issues on Acer Aspire 5538G AMD Athlon 64 x2 Processor"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by Newbeatontheblock on 2011-12-02
Hi everyone,

a few days ago i kicked windows and installed Ubuntu on my Acer Aspire Laptop.
Lovin it but only i m having issues with my wireless passwords which i need to enter  each time when i reboot my pc and do a logon or logoff ...Also the connection gets kicked all the time when i m in a session...
Sadly enough i have to admit that wireless was working great under windows 7
Don t wanna get back on the track with bill but i need to have my wireless working functioning properly .....
Hopefully anyone here has any suggestions 

When i checked  my terminal via [SIZE=3][COLOR=#0000FF]gksudo gedit  /etc/modprobe.d/blacklist.conf  [/COLOR][/SIZE] i saw that  my wireless is actived

Thanks in advance for all the tips provided 
[SIZE=3][COLOR=#0000FF]
[/COLOR][/SIZE]

---

### Post by nothingspecial on 2011-12-02
That command will show you which modules (drivers) are not loaded. Any way, you could do with posting your wireless card.

```
sudo lshw -C network
```

Put the out put of that command in a new post here and please put it code tags. Simply highlight the text and click the # in the formatting options at the top of the posting box.

---

### Post by Newbeatontheblock on 2012-06-10
Problem is fixed thanks very much

---

