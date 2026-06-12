---
title: "Which velocity is good when you need to transfer a big data between pc"
date: 2017-05-14
forum: New to Ubuntu
---

### Post by sed_faster on 2017-05-14
Hello everybody,

I use scp to copy a large amount of data between pc linux. On this networking I only use Linux, Ubuntu server and Lubuntu. The network it is build like this:

PC (ubuntu server)
Switch tp-link TL-SF1008D - ([https://www.amazon.com/TP-Link-8-Port-Ethernet-Desktop-TL-SF1008D/dp/B0034CL3MA](https://www.amazon.com/TP-Link-8-Port-Ethernet-Desktop-TL-SF1008D/dp/B0034CL3MA))
PC (Lubuntu 16.04)

The result, verbose, of the command scp are: [http://imgur.com/a/qqg0d](http://imgur.com/a/qqg0d)

In green box you can see the velocity of download to each file, right? Altogether I copy between pc 55GB, and this task delayed more and less 2 hours and 3o minutes. You can see the time about transference on third line to be cut from the end "in 8618.2 seconds".
I think that speed is bad! What do you think about this performance?

**Note:** While the pc did transference I don't use any pc and on Ubuntu Server I have 2GB Ram and on Lubuntu I have 4GB ram.

Thanks

---

### Post by The Cog on 2017-05-14
That works out at abut 49 Mbit/Sec, and the switch is a 100M switch. So at the very best, you will be able to achieve double that speed. It may well be worth trying to use rsync rather than scp to see if that goes any faster. Rsync can operate over ssh so there is no extra configuration required as you already have ssh working.

---

