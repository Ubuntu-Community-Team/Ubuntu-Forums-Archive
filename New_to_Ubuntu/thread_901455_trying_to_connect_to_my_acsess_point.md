---
title: "trying to connect to my acsess point"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by determinedblkman on 2008-08-26
i installed my wireless adapter card Via ndiswrapper, the power light comes on but not the link light. when i put in:
 david:~> /sbin/iwconfig
 lo       no wireless extentions.
 
 wmaster0 no wireless extentions.

 wlan0    IEEE 802.11g ESSID:""
          Mode:Managed Channel:0 Access point: Not-associated
          Tx-Power=0 dBm
          Retry min limit:7  RTS thr:off  fragment thr=2346 B
          Link Quality:0 Signal level:0 Noise level:0
          Rx invalid rwid:0 RX invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0
-----------------------------------------------------------------
 i'm running absolute linux (slackware): my wireless card adapter is linksys wpc54g ver.3: 
 if there's any other info i need supply, tell me. 
 i'm extremely new at linux, so i'm kindly asking for some help here. thank you

---

### Post by phidia on 2008-08-26
What does ndiswrapper -l output? In other words is the windows driver loaded?
You may need to configure the connection to your access point and I don't know what tools absolute linux provides for that.

---

### Post by determinedblkman on 2008-08-26
> **phidia said:**
> What does ndiswrapper -l output? In other words is the windows driver loaded?
You may need to configure the connection to your access point and I don't know what tools absolute linux provides for that.

ndiswrapper -l
 driver present hardware present

---

### Post by jgrabham on 2008-08-26
try this - [http://unintelligible.org/blog/2007/06/06/wpa-using-the-wpc54g-v3-pcmcia-card-in-ubuntu-feisty/](http://unintelligible.org/blog/2007/06/06/wpa-using-the-wpc54g-v3-pcmcia-card-in-ubuntu-feisty/)

---

### Post by phidia on 2008-08-26
> **jgrabham said:**
> try this - [http://unintelligible.org/blog/2007/06/06/wpa-using-the-wpc54g-v3-pcmcia-card-in-ubuntu-feisty/](http://unintelligible.org/blog/2007/06/06/wpa-using-the-wpc54g-v3-pcmcia-card-in-ubuntu-feisty/)

I'm not sure how much that will help with a system that's NOT debian based, but what the hey have a go.

---

### Post by jgrabham on 2008-08-26
> **phidia said:**
> I'm not sure how much that will help with a system that's NOT debian based, but what the hey have a go.

Oops, didn't read the slack bit, just log in to root before you start, ignore the sudo, and swap the apt-get for however you install things with slackwares package manager.

---

