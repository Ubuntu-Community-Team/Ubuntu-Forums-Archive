---
title: "Installing Netgear router Ubuntu 10.10"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by Brianret on 2011-10-31
[SIZE=2]I have purchased a Netgear WNR 3500 router which I have installed in windows 7 and I would now like it to work with my Ubuntu 10.10 set up on the same pc. Could anyone point me in the direction of[/SIZE] instructions how to do this?

---

### Post by Diametric on 2011-10-31
Does your Ubuntu machine "see" the signal?

---

### Post by quadproc on 2011-10-31
> **Brianret said:**
> [SIZE=2]I have purchased a Netgear WNR 3500 router which I have installed in windows 7 and I would now like it to work with my Ubuntu 10.10 set up on the same pc.[/SIZE]

The router is (or should be) independent of the computer so the same setup should work for both computers.  BTW, the ipconfig command in Windows is very similar to the ifconfig command in Ubuntu.

You might run into issues regarding drivers if you are using USB to connect from the Ubuntu system to the router, but if you are using 10/100 base T then the standard drivers should work fine.

I am running a Netgear FVS318 and I had no problems setting it up.  I use Ubuntu 10.10 with Firefox, so I just connected to 192.168.0.1 and when it wanted a user and password I gave it the default _admin_ and _password_.  Then I could set up things in the router.

Depending on your router and modem, you may need to set up the modem with the router removed from the system.  Once the modem is set to transparent bridge mode then the router can be reinserted.

If I have missed something in your question then please ask again, with more detail.

quadproc

---

### Post by gandaran on 2011-10-31
> **Brianret said:**
> [SIZE=2]I have purchased a Netgear WNR 3500 router which I have installed in windows 7 and I would now like it to work with my Ubuntu 10.10 set up on the same pc. Could anyone point me in the direction of[/SIZE] instructions how to do this?
can you provide details on how the router was setup in windows?
a router is an independet device you just setup once on any OS by accessing the router configuration page (router IP) in any web browser then it works for any computer whether using cable or wireless.
but you can also set up the router (if the router has built in modem) with a pppoe connection on windows where the actual dial-up is done from the computer not the router so if you have gone this way then you have to do the same on ubuntu or every other computer OS.

---

### Post by M!K3_$ on 2011-10-31
[ftp://downloads.netgear.com/files/WNR3500v2_SM_19Feb09.pdf]("ftp://downloads.netgear.com/files/WNR3500v2_SM_19Feb09.pdf")

If you follow the manual setup instructions you will arrive at the desired result.

---

