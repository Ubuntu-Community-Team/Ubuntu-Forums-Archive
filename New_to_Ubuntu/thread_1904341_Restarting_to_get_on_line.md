---
title: "Restarting to get on line"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by dowkeith on 2012-01-04
This is a problem that has persisted for years -- probably since Hardy Heron. When I sign on, I can't go online (either through Firefox or to update on root) without doing a restart. I was wondering if this is because I had to change the boot order to going to the hard drive first in order to install Ubuntu from a disc. What can I do to fix this? Every time without fail I am signing on and then doing a restart in order to get online. My notebook computer is connected by an ethernet cable to a Webtell router. My service is high speed from Verizon. This problem does not exist with two other computers on this router.

---

### Post by Anstice on 2012-01-04
Go to System > Administration > Additional Drivers and see if there are other drivers available for your ethernet card.

---

### Post by dowkeith on 2012-01-05
Thanks for getting back to me. There were no drivers listed when I went to the menu you suggested. I redid the boot order, but that made no difference. I noted that during the first sign on a line came up several times saying something like "message killed, no connection." This doesn't happen on the restart. I can live with this as I have for a long time, but it is annoying.

---

### Post by sandyd on 2012-01-05
> **dowkeith said:**
> This is a problem that has persisted for years -- probably since Hardy Heron. When I sign on, I can't go online (either through Firefox or to update on root) without doing a restart. I was wondering if this is because I had to change the boot order to going to the hard drive first in order to install Ubuntu from a disc. What can I do to fix this? Every time without fail I am signing on and then doing a restart in order to get online. My notebook computer is connected by an ethernet cable to a Webtell router. My service is high speed from Verizon. This problem does not exist with two other computers on this router.
Can you post the output of
```

sudo ifconfig

```
while you can't connect to the net?

---

### Post by jtarin on 2012-01-05
> **sandyd said:**
> Can you post the output of
```

sudo ifconfig

```
while you can't connect to the net?
Sudo is not required with the "ifconfig" command.
Are you using network manager to connect?

---

### Post by dowkeith on 2012-01-06
Thanks sandyd,

I will tell you what came up, but tonight I got online on the first try. It has become more random since I returned to the notebook's original boot order. I don't think I am using network manager to connect. I go through a router Verizon supplied with my high speed. I will post the results if I have trouble tomorrow.

---

### Post by dowkeith on 2012-01-08
> **sandyd said:**
> Can you post the output of
```

sudo ifconfig

```
while you can't connect to the net?
Hi Sandy,

Sorry about the delay. I was in New York. Here is what the ifconfig command gave me,

   duke@duke-laptop:~$ ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B) 

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:75:d4:ff  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by dowkeith on 2012-01-13
I'd like to thank everyone who offered suggestions on my restart problem.
I finally went to Geek Squad. It wasn't a linux problem. Everything worked fine in the store. I seem to have had an old router that was working fine with Windows machines but not with Linux. I bought a new Westell router and everything is fine as long as I use an Ethernet connection.

I went with Westell because the original Belkin router blew out my phones. My question is how I can make a wireless connection between my linux notebook and the Westel 7500. Linux asks for a user name and password. When I enter the ESSID and then the WEP key I get rejected. Is there something I have to do in linux to fix this?

---

