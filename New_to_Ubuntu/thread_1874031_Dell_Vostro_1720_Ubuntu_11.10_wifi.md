---
title: "Dell Vostro 1720 Ubuntu 11.10 wifi"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by mebomechanicno1 on 2011-11-02
I have tried running 11.10 on a Dell Vostro 1720 using the live CD supplied by Ubuntu User magazine. This required me to use the proprietory driver to access WiFi. It says it has installed but there is still no WiFi, which can be accessed without difficulty using the same machine running Vista Business and using a Sony Vaio using a fully installed 11.10 distro which I had downloaded and turned into a USB, so yes the wifi switch must be on (unless the Ocelot is switching it off and Vista is switching it back on again, which does seem highly unlikely). Any ideas will be greatly appreciated.

---

### Post by mebomechanicno1 on 2011-11-03
Oh well, I guess no one knows the answer?

---

### Post by computerandu on 2011-11-03
Hi,

Try the solution given her and do revert back whether it helps or not:

[http://www.computerandyou.net/2011/10/how-to-solve-no-wireless-network-detected-in-ubuntu-11-10/](http://www.computerandyou.net/2011/10/how-to-solve-no-wireless-network-detected-in-ubuntu-11-10/)

---

### Post by Mikepfive on 2012-01-11
Hi,

I came across this thread as I have a Dell Vostro with apparently the same problems.

So I tried the solution suggested by computerandu above and it solved my problem straight away.

Many thanks

Mike

---

### Post by shuttleworthwannabe on 2012-01-11
That solution assumes that the jockey was unable to detect automatically the card and install (or suggests an driver for installation) broadcom; so the solution should work.

But, I have a Vostro 3700 also has a broadcom wireless card; the problem is the WIFI LED light does not come on at all--but the WiFi works fine--signal is picked up, connects and all is good (jockey did everything for me). But no LED light comes on. Any suggestions to switch this light on?
[Edit]--this Ask Ubuntu [thread]("http://askubuntu.com/questions/75398/dell-vostro-3300-wi-fi-led-not-working") may shed some light to enthusiast!

---

### Post by Mariane on 2012-01-11
I spent a long time fiddling with wireless with my Dell Vostro. 
Once I installed wicd and everything became simple. 

Once you get wicd with your favorite package manager there are 3 commands to type.

WARNING: I quote this from memory, double check! 

wicd
wlan up
wicd-client

And then it just functions... Forever...

---

### Post by deputyjones on 2012-07-04
This worked for me, thanks!

---

