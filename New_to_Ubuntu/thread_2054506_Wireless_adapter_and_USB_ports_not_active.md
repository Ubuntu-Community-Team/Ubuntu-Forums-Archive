---
title: "Wireless adapter and USB ports not active"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by zuren on 2012-09-07
I am searching and muddling my way through a new install.  A friend has an old Gateway laptop that was running Vista and had some major issues within Windows that reinstalls and recovery points solved for a bit but never completely.  He wanted to revive it for simple word processing and surfing, so I suggested Lubuntu.

Install went okay; I had to use "acpi=off".

The 2 issues I have are:
1.  Realtek RTL-8185 wireless adapter is not connecting
2.  USB ports are not working

I've done searches and it seems that the RTL-8185 adapter has a history of installing incorrectly.  I'm still combing through and trying things.  I did as suggested in post #10 of this thread with no luck:

[http://ubuntuforums.org/showthread.php?t=1830220&highlight=rtl-8185](http://ubuntuforums.org/showthread.php?t=1830220&highlight=rtl-8185)

I have run ```
iwconfig
``` and ```
lspci
```.  It is getting power and is seen by the system.  But when I mouse over the network icon in the tray it says: Wireless Networks - disconnected.

Hard-wiring to the router works fine.

I found a Linux driver for this card at the Realtek [website]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true") and saved it to the desktop, but I'm having a heck of a time trying to install it.  My hope is that is the issue but feel I may need more guidance than what I'm finding.

As for the 3 USB ports, I haven't tackled that yet so any direction/suggestions would be appreciated.  It's probably another driver issue as they worked in Windows.

Thanks!

Computer:

GatewayW340UI laptop
Celeron M 1.6GHz
441MB RAM
Realtek RTL-8185 wireless adapter (not working)

---

