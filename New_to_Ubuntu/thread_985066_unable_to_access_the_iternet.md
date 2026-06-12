---
title: "unable to access the iternet"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by jovigeorge on 2008-11-17
Hi, 
I had installed Ubuntu and all went fine till I tried connecting to the internet. I am using a broad band connection and the connection is working fine in windows. I installed Ubutnu as a dual boot. 
Tried sudo pppoe conf. the system has done a scanning and the scanning stops at 100% and after that nothing happens.
Tries sudo pon dsl provider and the system is giving the following error- "file /etc/ppp/peers/dsl does no texist. Please create it or use a command line argument to use another file in the /etc/ppp/peers/directory"
what should I do now?
Please help.

---

### Post by handydan918 on 2008-11-17
Perhaps the output of ```
lspci
``` might allow someone to buy you
 a clue. Is this a wired connection?

---

### Post by jovigeorge on 2008-11-17
its a wired connection

---

### Post by handydan918 on 2008-11-17
Perhaps the output of


```
lspci
```

might allow someone to buy you
a clue.

---

### Post by oilchangeguy on 2008-11-17
> **jovigeorge said:**
> Hi, 
I had installed Ubuntu and all went fine till I tried connecting to the internet. I am using a broad band connection and the connection is working fine in windows. I installed Ubutnu as a dual boot. 
Tried sudo pppoe conf. the system has done a scanning and the scanning stops at 100% and after that nothing happens.
Tries sudo pon dsl provider and the system is giving the following error- "file /etc/ppp/peers/dsl does no texist. Please create it or use a command line argument to use another file in the /etc/ppp/peers/directory"
what should I do now?
Please help.

have you tried powering off the modem? try that, and at the same time reboot the computer.

---

### Post by jovigeorge on 2008-11-18
the following is the output of the lspcl-
jovi@jovi:~$ lspci

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139

---

### Post by jovigeorge on 2008-11-18
the following is the output of the lspcl-
jovi@jovi:~$ lspci

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139

---

### Post by som88 on 2008-11-18
same thing with me too

---

### Post by uarale on 2008-11-18
this might help
[http://ubuntuforums.org/showthread.php?t=963335](http://ubuntuforums.org/showthread.php?t=963335)

---

### Post by iponeverything on 2008-11-18
you could try:

```
mkdir -p /etc/ppp/peers/
```

---

### Post by jovigeorge on 2008-11-19
nothing happens when i type in th command.

---

### Post by jovigeorge on 2008-11-19
nothing happens when i am trying to create the directory.

---

