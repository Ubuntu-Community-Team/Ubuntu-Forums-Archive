---
title: "Dial Up Connection Setup/test"
date: 2017-02-08
forum: New to Ubuntu
---

### Post by dusty1980 on 2017-02-08
I'm setting an old Gateway laptop for my Mom to use to dial-in and get her Juno email.  How do I test if the dialup connection is working?

---

### Post by Autodave on 2017-02-08
If that is an internal modem and a Windows software run modem, you are in for a fight that you may not win. IF it is going to be possible to get dial-up working, you are probably going to have to get an external modem. (If you decide to go that route, Ebay is a good place to find a good, used one.  I included a link that I found: not sure if it will help or not.


[https://ubuntuforums.org/showthread.php?t=2221574&highlight=dial+modem](https://ubuntuforums.org/showthread.php?t=2221574&highlight=dial+modem)

---

### Post by alanthelinuxguy on 2017-02-08
> **dusty1980 said:**
> I'm setting an old Gateway laptop for my Mom to use to dial-in and get her Juno email.  How do I test if the dialup connection is working?

I would try using wvdial (see [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)).  This will let you test the modem's configuration and, in particular, will check if your laptop will talk to it.  As noted by AutoDave, so-called Winmodems don't normally work well under Linux; however, there are reports of exceptions to this "rule".  Even using an external modem with a laptop can be problematic since older modems need a serial cable and laptops generally don't have a serial port.  There are some web-based reports of success using a serial to USB adapter cable to make the connection.  Personally, using such a setup, I was able to get a USR modem to dial out and handshake with a dial-up service but couldn't establish any data transfer (the modem didn't see the request for a userid and password).  I ended up using an old desktop computer which had a serial port to connect to the external modem and successfully establish a dial-up connection.  If it turns out that you need an external modem, another possible route is to purchase one that connects through a USB port; however, I have no experience with these units.

> **dusty1980 said:**
> ...Juno email.  How do I test if the dialup connection is working?

Another somewhat obvious thing to do is to try to dial-up Juno using your setup as, I assume, they will provide such a potential connection.

---

### Post by dusty1980 on 2017-02-08
Thanks for the replies.  As of now, I'm trying to contact Juno regarding email software I can download for use on a linux OS.  They have not replied to date.

---

