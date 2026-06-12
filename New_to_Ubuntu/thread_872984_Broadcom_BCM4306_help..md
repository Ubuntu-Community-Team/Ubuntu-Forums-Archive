---
title: "Broadcom BCM4306 help."
date: 2008-07-28
forum: New to Ubuntu
---

### Post by thegnarlypanda on 2008-07-28
Hi, I'm having a bit of trouble getting my WiFi card to work in Ubuntu. It works fine under Vista, and I tried a USB WiFi dongle as well and that worked fine without any hassle in Ubuntu. 

But I don't always have access to the dongle so I need some help getting my pci card to work. I've had a good old try on my own, I've installed ndisgtk off the Ubuntu disc and loaded a driver but the little icon in the taskbar doesn't see any networks (with the dongle it sees several). I also tried using some firmware python install thing I found whilst looking through the Wiki but that didn't work either.

Any ideas?

Thanks.

---

### Post by stevoo on 2008-07-28
Another shot in the dark .... 

type 
iwconfig

The last result, should return more than the rest
get the id of it.
most probablt eth1

and run this 4 commands
```

sudo iwconfig eth1 ap any
sudo iwconfig eth1 esseid any
sudo iwconfig eth1 mode managed
sudo dhclient eth1

```

let me know if it has done anything

---

### Post by UbuntuNerd on 2008-07-28
this thread is talking about Broadcom BCM4306 and they got it working you should check it out


[http://ubuntuforums.org/showthread.php?t=735444]("http://ubuntuforums.org/showthread.php?t=735444")

---

### Post by thegnarlypanda on 2008-07-28
> **stevoo said:**
> Another shot in the dark .... 

type 
iwconfig

The last result, should return more than the rest
get the id of it.
most probablt eth1

and run this 4 commands
```

sudo iwconfig eth1 ap any
sudo iwconfig eth1 esseid any
sudo iwconfig eth1 mode managed
sudo dhclient eth1

```

let me know if it has done anything

I'll boot into Ubuntu and try this out now.


[quote=jperez78]this thread is talking about Broadcom BCM4306 and they got it working you should check it out


[http://ubuntuforums.org/showthread.php?t=735444](http://ubuntuforums.org/showthread.php?t=735444) [/quote]

The only problem with this is having a connection to the internet already, when I get a chance to use the dongle I'll give it a go.


EDIT: I got it all working, I used the dongle then downloaded b43-fwcutter and it sorted it.

---

