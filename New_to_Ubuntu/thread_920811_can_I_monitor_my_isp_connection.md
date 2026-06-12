---
title: "can I monitor my isp connection ???"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by mar225 on 2008-09-15
Is there a way to monitor my internet connection with ubuntu 8.04  I have searched but find nothing

Thanks

---

### Post by LowSky on 2008-09-15
Monitor what exactly? Traffic to and from your router, to and from your computer?

i found this very quickly on Google using the search words, "monitor internet connection ubuntu"

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html)

---

### Post by mar225 on 2008-09-15
I have comcast service and it seems like it is very eratic. It doesn't do any good to call them. They send out some high school dropout who can't help. I want to log the connection so I have some proof of whats happening. If they don't respond then I'll let a lawyer explain it for me.

---

### Post by _sAm_ on 2008-09-15
Could you use this?
[http://www.linuxprimetime.com/applications/monitor-you-computers-network-connection-in-linux/](http://www.linuxprimetime.com/applications/monitor-you-computers-network-connection-in-linux/)

---

### Post by mar225 on 2008-09-15
I'm not into computers deep enoug to use something like that.  All I want to know is when the internet connection fails and when it comes back. Preferably in the form of a log file.

---

### Post by nowshining on 2008-09-15
the system log should show u this esp. if ur using dialup - var/log/syslog - have a look at the log viewer that comes with ubuntu.

---

### Post by S.A.A on 2008-09-15
If you are using dial-up try this:

```
sudo apt-get install ppptray
```

it works perfect for me !

---

### Post by nowshining on 2008-09-15
> **S.A.A said:**
> If you are using dial-up try this:

```
sudo apt-get install ppptray
```

it works perfect for me !


hmmm it may be only in hardy in synaptic - i can't find it in gutsy :)

---

### Post by mar225 on 2008-09-15
comcast isn't dialup. supposedly high speed if it works at all. When it is good it is very good. Most of the time you don't know if it works at all.

---

### Post by S.A.A on 2008-09-15
> **nowshining said:**
> hmmm it may be only in hardy in synaptic - i can't find it in gutsy :)

go to this thread:

[http://ubuntuforums.org/showthread.php?p=3252650](http://ubuntuforums.org/showthread.php?p=3252650)

---

### Post by S.A.A on 2008-09-15
> **mar225 said:**
> comcast isn't dialup. supposedly high speed if it works at all. When it is good it is very good. Most of the time you don't know if it works at all.

I found this for you:

add these to /etc/apt/sources.list:
```
deb http://debian-amd64.alioth.debian.org/debian-pure64 sid main contrib non-free
deb-src http://debian-amd64.alioth.debian.org/debian-pure64 sid main contrib non-free

```

then:
```
sudo apt-get update
sudo apt-get install gkrellm
```

---

### Post by S.A.A on 2008-09-15
Hey, forget about my last post, look at this:

[http://www.gnome.org/projects/netspeed/](http://www.gnome.org/projects/netspeed/)

and at this to install:

[http://www.ubuntugeek.com/netspeed-traffic-monitor-applet-for-gnome.html](http://www.ubuntugeek.com/netspeed-traffic-monitor-applet-for-gnome.html)

---

### Post by mar225 on 2008-09-15
Noyhing is ever simple is it.

Thanks anyway  I could care less about speed at this point. Would like to know if a connection is available though

---

### Post by nowshining on 2008-09-15
oh yeah the network monitor applet by defautl should handle this - right click the bottom panel or whatever panel u want and select add - find it - i forgot where to find it, but it should be easy to find.

---

### Post by mar225 on 2008-09-15
Like I said nothing is ever simple

------------------------------------------------------------------------
Please contact your system administrator to resolve the following problem:

SIOCGIFFLAGS error: No such device
-------------------------------------------------------------------------

I guess I don't have an eth0. I wonder what I'm connected with now?

LOL  Thanks everybody for the suggestions. This just isn't worth the effort

---

### Post by GooblyWoobly on 2008-09-15
The best way to detect if you have connectivity is to ping your gateway on the concast's side. However, as someone said, it's not easy.

You can do a rudimentary check by using the following script: Just paste it on a terminal and run it, and it will output date whenever you lose connectivity.

```
while true; do ping -c 1 www.google.com > /dev/null;  if [ $? -ne 0 ]; then echo -n "Connection down at "; date; fi; sleep 5; done
```

To get out, press Ctrl-C.

What it is doing is, in an infinite loop, sending a single ping (a way of checking if the server is alive) to google (You can choose some other server if you want). If the ping fails, it will print out the time. It will stop printing when the connection is back up. It also sleeps 5 secs between each ping.

It can be made fancier, state/gui can be added. But this basic thing gets the job done if you just want to know if your connection is okay.

---

### Post by m42tyger on 2011-10-25
> **GooblyWoobly said:**
> The best way to detect if you have connectivity is to ping your gateway on the concast's side. However, as someone said, it's not easy.

You can do a rudimentary check by using the following script: Just paste it on a terminal and run it, and it will output date whenever you lose connectivity.

```
while true; do ping -c 1 www.google.com > /dev/null;  if [ $? -ne 0 ]; then echo -n "Connection down at "; date; fi; sleep 5; done
```

To get out, press Ctrl-C.

What it is doing is, in an infinite loop, sending a single ping (a way of checking if the server is alive) to google (You can choose some other server if you want). If the ping fails, it will print out the time. It will stop printing when the connection is back up. It also sleeps 5 secs between each ping.

It can be made fancier, state/gui can be added. But this basic thing gets the job done if you just want to know if your connection is okay.

Thanks for this, this is perfect for me! :)

Just set it up in a terminal and carrying on with business, it's good to have a record of these drops. Hopefully will force ISPs to get better.

---

