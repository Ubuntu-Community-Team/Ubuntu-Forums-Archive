---
title: "Network and Sharing"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by linuxaspirer on 2011-09-18
In win 7 and Lion X  , it shows automatically on the side pane what are the network connections that are available,
does the same thing shows up on the ubuntu.
Can I connect my laptop to my wife lion xs mac using network sharing.

thanks
sastry

---

### Post by Lisiano on 2011-09-19
If you mean WiFi then just "Create new Wireless Connection" under Network Manager. If you mean a cable then you need to manually set it. Click Network Manager -> Edit Connections -> Wired -> Add -> (Give it a name if you wish) untick Connect automatically -> IPv4 Settings -> Method: Shared to other computers -> Save. Now you can "connect" to this connection using Network Manager by just clicking on it's name. When you are done, click the name again or click some other connection.

---

### Post by nerdse on 2011-09-19
> **Lisiano said:**
> If you mean WiFi then just "Create new Wireless Connection" under Network Manager. If you mean a cable then you need to manually set it. Click Network Manager -> Edit Connections -> Wired -> Add -> (Give it a name if you wish) untick Connect automatically -> IPv4 Settings -> Method: Shared to other computers -> Save. Now you can "connect" to this connection using Network Manager by just clicking on it's name. When you are done, click the name again or click some other connection.

We have 2 PCs & a laptop attached to a Verizon FiOS router. The laptop & one PC run Ubuntu 11.04 (the Ubuntu PC was supposed to be dual boot, but no matter how many times we try to put the appropriate drivers in, they won't install, making Windows even more useless than usual). The 3rd PC runs 4 bit XP at present. 

The printer is attached to the wannabe dual boot PC. Despite its being shared under admin on the Ubuntu side (& even on the Windows side in desperation), neither the laptop nor the Windows PC can attach to the printer as we could with older versions of Ubuntu. We tried attaching all 3 computers to the printer via a USB 3 way port, but we still can't get it to share, so we have to wait until my husband's not using his PC (the wannabe dual boot one) to print anything. We've tried CUPS with & without the USB hub, no luck. 

I tried going to the various types of network options in 11.04; it recognizes a Windows network but says it can't find shares even though they're there. On 11.04, there is no "Network Manager." There is "Network Connections" & "Network Proxy" under the "preferences" menu in the admin logon; there is "Network Tools" under the Administration menu. Under "Places" there is a "Network" option & under that, "connect to server..." which takes me to the icon for the Windows network. From there, however, I can't connect.

Does anyone have the 11.04 instructions? The manual wasn't any more enlightening to me...not even sure what I missed. Any help would be appreciated.

---

### Post by anewguy on 2011-09-19
nerdse - if you are not the OP of a thread, in this case it's linuxaspirer, then you need to open your own thread for your problem.

trying to respond to 2 peoples separate problems in the same thread leads to nothing but confusion (and usually aggravation) for all involved.

Dave ;)

---

### Post by Lisiano on 2011-09-19
I agree with anewguy. nerdse please start a new thread with your problem as it does not sound similar to this problem.
Also the network manager is the icon that looks like 2 arrows going Up and Down, a WiFi logo, or a Ethernet port. Just click on all the icons until you find it.
Btw.
> The 3rd PC runs 4 bit XP at present.
4-bit XP... I need to get me one of those!!!

---

