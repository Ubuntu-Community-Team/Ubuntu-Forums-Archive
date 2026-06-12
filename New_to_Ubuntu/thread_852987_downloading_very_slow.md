---
title: "downloading very slow"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by japephillips on 2008-07-08
In recent times I have had a lot of slooooooow dialup connections after a couple of months of all well. My ISP reckon something is downloading in the background but I cannot see anything (using Firestarter), they insist I do a TCP dump on PPP as their end shows all well (of course!). I don't have any idea how to do that and a web search made no sense to me. I am using Ubuntu 7.10 and have also a partition set up to use 8.04 but with same slow results. I use Fireworks and it often freezes during opening of tags, downloading web pages, general stuff that used to be OK. I have to hard switch off.
Any ideas please?

---

### Post by ChameleonDave on 2008-07-08
Fireworks?  Isn't that a Windows app?

---

### Post by japephillips on 2008-07-08
firefox

---

### Post by ChameleonDave on 2008-07-08
> **japephillips said:**
> firefox

OK.  People sometimes report that, sadly, there are more bugs in Firefox for Linux than for Firefox for Windows.

To see whether this is a Firefox problem or an Internet connection problem, try using another browser.

The GNOME desktop has Epiphany, and KDE has Konqueror.  Opera is also a very good browser.  Install them if necessary, and see how it works.

---

### Post by jordanmthomas on 2008-07-08
Well, although it's unlikely you have background downloads you don't know about, have you done a tcpdump?
```
sudo tcpdump
```
It will show all the connections you're making.  If you see anything you don't recognize, it's something you should perhaps investigate.

---

### Post by iaculallad on 2008-07-08
You could try the procedures in this [page]("http://forevergeek.com/open_source/make_firefox_faster.php") to tweak your Firefox for faster access.

---

### Post by japephillips on 2008-07-08
> **jordanmthomas said:**
> Well, although it's unlikely you have background downloads you don't know about, have you done a tcpdump?
```
sudo tcpdump
```
It will show all the connections you're making.  If you see anything you don't recognize, it's something you should perhaps investigate.

Thank you, that was what I was asking for. A Google search gave me pages of stuff I didn't understand and no simple command. 
unfortunately the terminal response is:

tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes

I tried sudo tcpdump -v and it didn't do anything.

---

### Post by jordanmthomas on 2008-07-09
I have never used dialup with linux, but I don't think it would be using eth0, but some other connection name.

What do you get when you type
```
ifconfig
```
My output:
```
[COLOR="Red"]eth1[/COLOR]      Link encap:Ethernet  HWaddr 00:12:F0:43:FF:E6  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe43:ffe6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:241592 errors:0 dropped:11 overruns:0 frame:0
          TX packets:262611 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:119312398 (113.7 Mb)  TX bytes:28413630 (27.0 Mb)
          Interrupt:17 Base address:0xc000 Memory:dfdfd000-dfdfdfff 

[COLOR="Red"]lo[/COLOR]        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:571426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:571426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55499159 (52.9 Mb)  TX bytes:55499159 (52.9 Mb)

```

The parts in red are my network interfaces.  As you can see, eth1 is connected.  lo is always connected and is just there so your computer can connect to itself (in simplified terms)

Yours may be something like **ppp0** or something (again, I don't know for sure and this is just a guess.  Don't worry if it's called something else)

Try running 
```
sudo tcpdump -i **ppp0**
```
where ppp0 is the name of the interface you found with ifconfig.

Hope this helps.

---

