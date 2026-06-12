---
title: "DNS issues."
date: 2008-09-25
forum: New to Ubuntu
---

### Post by Cuthlif on 2008-09-25
Hi, I just installed 8.04 and I'm having some issues resolving DNS. I have onboard LAN as well as a wireless NIC. I can't get either one of them to connect to the internet.


Uhh... yeah... so.. little help?

Please?

---

### Post by Dr Small on 2008-09-25
Please post the output of this command, from the Terminal (Applications > Terminal):
```
cat /etc/resolv.conf
```

Dr Small

---

### Post by jemate18 on 2008-09-25
can you post output of 

```
ifconfig eth0
```

and

can you do a

```
ping www.google.com
```

?

---

### Post by Cuthlif on 2008-09-25
Ok, lets see here.
etc
cat /etc/resolv.conf yeilds
```
cat: /etc/resolv.conf: No such file or directory
```

ifconfig eth0 gets
```
Link encap: Ethernet  HWaddr 00:1c:25:56:5b:47
inet6 addr: fe80::21c:25ff:fe56:5b47/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 METRIC:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:38 Errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes: 5763 (5.6 KN)
Interupt:19
```

And I can not ping anything,

---

### Post by jemate18 on 2008-09-25
> **Cuthlif said:**
> Ok, lets see here.
etc
cat /etc/resolv.conf yeilds
```
cat: /etc/resolv.conf: No such file or directory
```

ifconfig eth0 gets
```
Link encap: Ethernet  HWaddr 00:1c:25:56:5b:47
inet6 addr: fe80::21c:25ff:fe56:5b47/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 METRIC:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:38 Errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes: 5763 (5.6 KN)
Interupt:19
```

And I can not ping anything,

try
```
sudo ifconfig eth0 up
```

---

### Post by Dr Small on 2008-09-25
Have you even configured the network yet?

---

### Post by Cuthlif on 2008-09-25
Should that bring anything up? I entered it in, it asked for my admin password, I gave it then it just went back to username@computer:-$

---

### Post by Cuthlif on 2008-09-25
> **Dr Small said:**
> Have you even configured the network yet?

Could you elaborate on that?

---

### Post by jemate18 on 2008-09-25
to configure your network....


type
```
network-admin
``` in the terminal 

or

System -> Administration -> Network

---

### Post by Cuthlif on 2008-09-25
> **jemate18 said:**
> to configure your network....


type
```
network-admin
``` in the terminal 

or

System -> Administration -> Network

Yeah,  did that.

---

### Post by jemate18 on 2008-09-25
So have you set up already? what did you do after network-admin

---

### Post by nowshining on 2008-09-25
can u get the DNS names of ur isp, if so create a /etc/resolv.conf file - for a tmp solution see if you can use these:

```
 
nameserver 64.136.52.73
nameserver 64.136.44.73

```

just do

sudo gedit, copy and paste those into an open files - save and navigate to /etc/ and name it rexolve.conf - does it work, u may also add these ips:
```

nameserver 65.247.64.21
nameserver 65.247.64.22
```

---

### Post by Cuthlif on 2008-09-25
> **jemate18 said:**
> so have you set up already? What did you do after network-admin

&#65328;&#65362;&#65349;&#65364;&#65364;&#65369;&#12288;&#65357;&#65365;&#65347;&#65352;&#12288;&#65358;&#65359;&#65364;&#65352;&#65353;&#65358;&#65351;&#65294;&#12288;&#65288;&#65353;&#65351;&#65358;&#65359;&#65362;&#65349;&#12288;&#65364;&#65352;&#65349;&#12288;&#65346;&#65356;&#65359;&#65347;&#65355;&#65369;&#12288;&#65364;&#65349;&#65368;&#65364;&#65292;&#12288;&#65353;&#65364;&#12288;&#65348;&#65359;&#65349;&#65363;&#12288;&#65364;&#65352;&#65353;&#65363;&#12288;&#65359;&#65365;&#65364;&#12288;&#65359;&#65350;&#12288;&#65358;&#65359;&#65367;&#65352;&#65349;&#65362;&#65349;&#65289;

---

