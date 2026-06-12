---
title: "No network devices"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by S@nctus on 2008-04-24
I am so excited to have Hardy Heron installed -- this was exactly what I have been waiting for to dive in and use Ubuntu (because I don't know anything at all about it, how to compile something, how to install things or use commands....)

But when I am in it, there is no network detection, and when I go to network settings there seems no place for me to do anything like enable DHCP...it wants only to deal with the modem.  In Windows, no problem.  THere was no problem before either when I used to play with Ubuntu from the live CD of the previous version last month.

My Gateway laptop uses at RealTek 8185 Extensible thingy for wireless -- (wireless card)  Now I have read some threads where people say "Find the windows driver and install it in Ubuntu"...but that doesn't help me because I have no idea how to do that -- such as where could I download it to that I could browse to it from Ubuntu?  Hm...it seems very confusing, but I am here to learn.

THanks for any helpful help for a VERY NEWbee

---

### Post by riven0 on 2008-04-24
Have you tried following this guide to installing the driver. You're probably missing the driver:

[Installing - Realtek Linux wireless driver]("http://rtl-wifi.sourceforge.net/wiki/Installing")

---

### Post by Khalis7 on 2008-04-25
> **S@nctus said:**
> I am so excited to have Hardy Heron installed -- this was exactly what I have been waiting for to dive in and use Ubuntu (because I don't know anything at all about it, how to compile something, how to install things or use commands....)

But when I am in it, there is no network detection, and when I go to network settings there seems no place for me to do anything like enable DHCP...it wants only to deal with the modem.  In Windows, no problem.  THere was no problem before either when I used to play with Ubuntu from the live CD of the previous version last month.

My Gateway laptop uses at RealTek 8185 Extensible thingy for wireless -- (wireless card)  Now I have read some threads where people say "Find the windows driver and install it in Ubuntu"...but that doesn't help me because I have no idea how to do that -- such as where could I download it to that I could browse to it from Ubuntu?  Hm...it seems very confusing, but I am here to learn.

THanks for any helpful help for a VERY NEWbee

> **riven0 said:**
> Have you tried following this guide to installing the driver. You're probably missing the driver:

[Installing - Realtek Linux wireless driver]("http://rtl-wifi.sourceforge.net/wiki/Installing")

Hi. After download the wireless driver you may reload the networking interfaces by running up this command from terminal:
```
sudo /etc/init.d/networking restart
```

You may need to wait for few minutes to let the wireless network to find the network connection.
If nothing happens, you may run this command:
```
sudo /etc/init.d/networking force-reload
```

Try this and see what happens afterwards.

---

### Post by S@nctus on 2008-04-25
Thanks for the links,but I had seen that page before and I don't understand it.  I have gone to terminal and typed commands as it said, I don't get how to download and run the drivers.  I can't obviously do that in Ubuntu because it will not connect to the Internet to let me.  

I can't install anything.  Subversion isn't on my computer and I can't get it online.  I seem to be stuck.

---

### Post by lorienjohnson on 2008-04-28
Bump! I'm having the exact same problem. I, too, am using the Realtek Install tutorial. However, it requires:
 apt-get install build-essential subversion module-assistant

... for which we need the internet. Awkward.

---

