---
title: "Network printer issue"
date: 2012-07-02
forum: New to Ubuntu
---

### Post by VoReason on 2012-07-02
Hi everyone.  I'm loving my Ubuntu experience (I'm a previous long-time Windows user).  My wife and I both have Ubuntu 12.04 installed on our netbooks.  She is more "tethered" (uses hers like a desktop, with a larger screen, wireless keyboard and printer hooked to it).  I would like to print through her computer, rather than unplug the USB from hers and plug it into mine.  We have a wireless network, so it shouldn't be a problem (it wasn't for Windows).

We have gone as far as enabling print sharing, etc.  I've searched (and found) the printer connected to her computer.  She "published" the printer and everything appears ready to print.  By the way, the Printer is an HP p2015d.  It works great for both of us when we plug into it (USB cable).  The printer status says, "idle - Ready to print."  The drivers all installed from the printer list, and it appears everything is peachy.  The only problem is, nothing happens when I try to print something (uncluding the "test page").  It appears to send the job, processes it, and yet the printer just sits there like a bump on a log.  Yes, there is paper in the printer, and the printer is working fine otherwise.  When I look in the print queue, it shows the job as "completed" (liar... I wish!).  I've gone under the menue bar "printer -> server -> connect -> and it seems to connect fine.

I'm just about there, I can feel it... just one more little step I'm missing, maybe?

Any thoughts would be appreciated,
:KS
VoReason

---

### Post by mapes12 on 2012-07-02
> The drivers all installed from the printer listI think you have the HPLIP driver that installs by default with Ubu. This is out of date. On the machine that hosts the printer (your wife's I think) go to the HPLIP website (Google will find it) and follow their instructions to download and install the latest driver.

---

### Post by Bucky Ball on 2012-07-02
Welcome.

As this is a network printer I am assuming it is connected to the router and so is your wife. The printer has a static IP? Your computer is connected to the router/network wirelessly? Then you and the printer are on the same LAN and you should be able to find the printer automatically using System>Printing, but you need to install HPLip first. This way you by-pass going through your wife's computer completely. ;)

If you are running a cable into the router (that your wife and the printer are plugged into) you should be able to find the printer easily. Just copy the setup your wife has. ;)

---

### Post by Bucky Ball on 2012-07-02
If not already installed you will need to install HPLip from here:

[http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)

Go Printing>Add Printer>Network Printer. Give it a few seconds to find the printer on the network. It should pop up in the screen on the left with the IP address next to it.

---

### Post by VoReason on 2012-07-02
> **Bucky Ball said:**
> Welcome.

As this is a network printer I am assuming it is connected to the router and so is your wife. The printer has a static IP? Your computer is connected to the router/network wirelessly? Then you and the printer are on the same LAN and you should be able to find the printer automatically using System>Printing, but you need to install HPLip first. This way you by-pass going through your wife's computer completely. ;)

If you are running a cable into the router (that your wife and the printer are plugged into) you should be able to find the printer easily. Just copy the setup your wife has. ;)

Thanks for the tip.  Once I found the right IP it worked!  It had me going through her PC and the USB port before (port 9100) somehow.  Our network is complex (it is one wireless hub of a whole string of building that are hooked to a VSAT with a Network Attached Storage and a bunch of switches).  It turned out the IP address for the wireless system we are using is  10.10.105.162 (not the usual IP address that it gives you when you ping the computer online, like the website "whatismyipaddress.com" (which is 119.something-or-other).  Anyway, it is SOLVED!  Thanks!
):P

---

### Post by VoReason on 2012-07-02
> **Bucky Ball said:**
> If not already installed you will need to install HPLip from here:

[http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)

Go Printing>Add Printer>Network Printer. Give it a few seconds to find the printer on the network. It should pop up in the screen on the left with the IP address next to it.


Thanks for pointing this out...  I guess I already had the newest one.

---

### Post by Bucky Ball on 2012-07-02
Great news! Enjoy and please mark thread as 'Solved' from 'Thread Tools' to help others. ;)

---

