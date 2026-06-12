---
title: "cant find any networks in ubuntu 11.10"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by JazzPotato on 2011-11-14
Hi all,
 I just did a clean install of 11.10 again after my arch install became dysfunctional. When I installed, I realised I couldn't connect to the internet with eth0, try as I might. The live disc could connect either, and I had to install without installing updates as I went. I thought the install would fix it. 
 I'm 100% sure my network/modem is not to blame, as I connected with another Windows laptop wired and my father is using wireless on it at this very moment, as am I with my phone. Not is the integrity of my Ethernet cable the problem. Ubuntu insists that there is no network cable connected. 
 Curiously, apparently I used "wired connection 1" 23 minutes ago, however I have never accessed the internet from this machine. 

Thanks in advance,
Gary

---

### Post by acrazyplayer on 2011-11-14
Could be a bad Ethernet cable, maybe something bent or popped off. try looking at both ends and seeing if they are the same.

Also you didn't change anything in the BIOS of your computer did you? Because you can disable Ethernet in there sometimes.

Another thing to do would be to remove any of the settings/options from the network manager. You mention a "wired connection 1" remove it. It's safe to do because Ubuntu will just make a new one.

---

### Post by sandyd on 2011-11-14
Do the lights were you plug in the ethernet turn on?

P.S. Get an [ethernet tester]("http://www.newegg.com/Product/Product.aspx?Item=N82E16899997005") . 
Also sometimes, the ethernet crimping might come loose. Test the cable with another computer to make sure. If you want to fix those by yourself, get an [ethernet crimper]("http://www.newegg.com/Product/Product.aspx?Item=N82E16899888401").

Its one of the few things that I like about wireless networks.:rolleyes:

---

### Post by paolo.pani on 2011-11-15
I had the same problem after upgrading to 11.10.

Apparently, for me the following worked:

sudo nano /etc/NetworkManager/NetworkManager.conf
change the line managed=false to managed=true

Save, stop and start network manager:

sudo service network-manager restart

Cheers,

Paolo

---

