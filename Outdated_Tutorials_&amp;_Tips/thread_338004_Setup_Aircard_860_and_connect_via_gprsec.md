---
title: "Setup Aircard 860 and connect via gprsec"
date: 2007-01-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Darrena on 2007-01-13
This post is also available from:
[http://darrenalbers.com/gprsec/aircard.html](http://darrenalbers.com/gprsec/aircard.html)


Here are some quick and dirty install instructions for an Aircard 860 on Ubuntu.

    * Download the firmware from: 
[http://www.sierrawireless.com/resources/faq/PC_Card/AirCard850_860/Aircard_Linux.tar](http://www.sierrawireless.com/resources/faq/PC_Card/AirCard850_860/Aircard_Linux.tar)
[http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=118](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=118)

    * Extract SW_8xx_SER.dat and rename it to SW_7xx_SER.cis  (This tip found at: [http://ubuntuforums.org/showthread.php?t=154092](http://ubuntuforums.org/showthread.php?t=154092))
    * Copy the SW_7xx_SER.cis to /lib/firmware
    * Insert your card
    * use dmesg to determine what serial port the device is on.  For example:

[17609860.104000] pccard: PCMCIA card inserted into slot 0
[17609860.104000] pcmcia: registering new device pcmcia0.0
[17609860.148000] 0.0: ttyS0 at I/O 0x3f8 (irq = 3) is a 16550A

    * Install GPRSEC from [http://darrenalbers.com/gprsec/](http://darrenalbers.com/gprsec/)
    * Run gprsec, select preferences and select the serial port you determined from dmesg.
    * Save the settings and click connect

---

### Post by magicfab on 2007-01-27
Hi

Thanks for the info. I am trying to get a AC850 card to work in 6.06.1, i have gathered all the info I could here:
[https://wiki.ubuntu.com/AirCard8X0](https://wiki.ubuntu.com/AirCard8X0)

I invite you to proofread/add anything you may find useful.

---

### Post by pcailey1 on 2007-04-24
Thanks You are the greatest. I can now finally get rid of windblows forever.

I've looked and looked and tried many things but this is the first thing that ever worked. When , I first ran gprsec i had to remove the card and reinsert it, Then rerun gprsec to get connected. Thanks again you've made my day. I Just installed Unbuntu fiesty yesterday.
,
I'll be here for a long time now Thanks again. !!!

---

### Post by sheaton319 on 2007-05-07
I have an 860 card with the latest firmware. Ubuntu 7.04 and gprsec 3.0. I have gotten my card to be recognized on Linux on ttys0 and gprsec recognizes that its there, but when i try to connect, it says "Interrupted by User" and "Flat Battery". Does anyone know what this means? Or how to fix it?

Thanks much in advance.

---

### Post by b4thatsunday on 2007-05-07
Try configuring it using the LiveCD to make sure it works...

I'm going through something right now where my card ONLY works on the LIVE CD...
I get a connection time out when trying with my installed OS

*shrug*

---

### Post by bomanizer on 2007-07-01
Similar problems here. I'm trying to connect with my gprs phone, using gprsec. I get the "flat battery"- error also. Feisty & gprsec & Samsung sgh-z540. The connection is ok with kmobiletools....go figure...

---

### Post by frefly on 2007-07-25
I did as you, but the dmesg just output the following:

[17180499.452000] pcmcia: registering new device pcmcia0.0

There was no the last string,

Can you tell me why?

---

### Post by wareagle on 2007-10-26
=D>

THANK YOU for the file renaming tip.  Works great!  (Using Kubuntu Gutsy)

---

### Post by wareagle on 2007-10-26
Here is some of the info I needed to connect to Cingular (pasted from [this site](http://www.nowsms.com/framer.htm?http://www.nowsms.com/discus/messages/1/21562.html)):

Server Address - [http://mmsc.cingular.com/](http://mmsc.cingular.com/)

Network Connection: Modem:Sierra Wireless Aicard 3G Modem.
WAP Gateway IP Address - 66.209.11.61

GPRS APN - wap.cingular
Login Name - [email]WAP@CINGULARGPRS.COM[/email]
Password - CINGULAR1
Modem Used - Sierra Wireless Aircard 3G Modem

---

### Post by Horndog on 2008-05-07
I have been a Sierra AirCard 860 and followed the howto.
I get this:

```
horndog@horndog-laptop:~$ pon ac850
/etc/chatscripts/ac850chat: 1: : Permission denied
/etc/chatscripts/ac850chat: 3: TIMEOUT: not found
/etc/chatscripts/ac850chat: 5: OK: not found
/etc/chatscripts/ac850chat: 7: CONNECT: not found
Connect script failed 
```

Any suggestions? 
BTW I don't have any internet without this connection.

Thanks

EDIT for more info

```

May  8 02:52:59 horndog-laptop dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
May  8 02:53:01 horndog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May  8 02:53:09 horndog-laptop dhclient: No DHCPOFFERS received.
May  8 02:53:09 horndog-laptop dhclient: No working leases in persistent database - sleeping.
May  8 02:53:09 horndog-laptop dhclient: No DHCPOFFERS received.
May  8 02:53:09 horndog-laptop dhclient: No working leases in persistent database - sleeping.
May  8 02:55:52 horndog-laptop pppd[7635]: pppd 2.4.4 started by horndog, uid 1000
May  8 02:55:53 horndog-laptop pppd[7635]: Connect script failed
May  8 02:55:54 horndog-laptop pppd[7635]: Exit.
May  8 02:57:47 horndog-laptop dhclient: DHCPDISCOVER on ath0 to 255.255.255.255

```

```

horndog@horndog-laptop:~$ ls /dev/um*
/dev/umts

```

```

horndog@horndog-laptop:~$ pccardctl ident
Socket 0:
  product info: "Sierra Wireless", "AC850", "3G Network Adapter", "R1"
  manfid: 0x0192, 0x0710
  function: [color=red]2 (serial)[/color]
Socket 1:
  no product info available

```

---

### Post by wareagle on 2008-05-07
> **Horndog said:**
> I have been a Sierra AirCard 860 and followed the howto.
I get this:

```
horndog@horndog-laptop:~$ pon ac850
/etc/chatscripts/ac850chat: 1: : Permission denied
/etc/chatscripts/ac850chat: 3: TIMEOUT: not found
/etc/chatscripts/ac850chat: 5: OK: not found
/etc/chatscripts/ac850chat: 7: CONNECT: not found
Connect script failed 
```

Any suggestions? 
BTW I don't have any internet without this connection.

Thanks

Try running that as root.

---

### Post by Horndog on 2008-05-08
> **wareagle said:**
> Try running that as root.

I did and also google and found this which didn't work:

```


horndog@horndog-laptop:~$ sudo pon ac850


```

No joy

```

sudo apt-get remove network-manager network-manager-gnome

```

Thanks for your reply

[color=red] I started a new thread[/color]

---

