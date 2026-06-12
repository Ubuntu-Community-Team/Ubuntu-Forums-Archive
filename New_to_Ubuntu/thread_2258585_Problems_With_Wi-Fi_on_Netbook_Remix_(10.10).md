---
title: "Problems With Wi-Fi on Netbook Remix (10.10)"
date: 2014-12-28
forum: New to Ubuntu
---

### Post by Sir_Ernest_Vines on 2014-12-28
Woo Hoo! First post!!! :-D
Anyways, I installed ubuntu netbook remix for version 10.10 onto my Toshiba NB505 without problems. So I thought. I tried to get connected to wifi, but it just says something about a wired connection is disconnected. I apparently have Realtek RTL8188CE. is there a later version of netbook remix? id est what would be the latest version? on another note, is the multi-touch trackpad is not supported in this version? how can I get that feature if it is available?
Thanks in advance! :-D

---

### Post by grahammechanical on 2014-12-28
And a Woo Hoo! To you too! :)

Welcome to the forums. There is good news and there is bad news. First, the good news. Wikipedia assures me that with the release of Ubuntu netbook remix 10.10 in October 2010, the Unity interface was used. That is good news because six months later Ubuntu desktop got the Unity user interface. So, here I am using Ubuntu 14.10 (released October 2014) and just may be I can give instructions that fit your user interface.

Now for the bad news. Ubuntu 10.10 whether desktop or netbook remix only had 18 months support. The software repositories for that version have long since been closed and relocated to the old releases servers. That means that you cannot update the system or install any software and that includes WiFi drivers.

There might be some more good news. Is this your model?

[http://www.cnet.com/products/toshiba-nb505-n500bl-10-1-atom-n455-windows-7-starter-1-gb-ram-250-gb-hdd/specs/](http://www.cnet.com/products/toshiba-nb505-n500bl-10-1-atom-n455-windows-7-starter-1-gb-ram-250-gb-hdd/specs/)

If it runs windows 7 it should run the latest version of Ubuntu and that is 14.04.1. Can you download Ubuntu 14.04.1 and run a live session to see if it works?

WiFi drivers are usually installed by default. Otherwise we go to the Additional Drivers utility and run that to see if it can offer a WiFi driver but we need to be connected to the internet in order for the driver to be downloaded. This is most likely why you got that message about a wired connection.

This wiki page will explain how to change the URLs of the software sources that are currently pointing to the closed repositories to the URLs that point to the old-releases repositories. You will need to do that if you want to install software, including a WiFi driver. You will also have to do that if you want to upgrade to the next version of Ubuntu. In fact you will have to repeat the process to get from 10.10 to 11.04 and then from 11.04 to 11.10 and from 11.10 to 12.04, which by the way, is still supported.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

It is a Iot of work, which why I suggested downloading 14.04.1 and installing that. It has 5 years support counting from April 2014.

Regards.

---

