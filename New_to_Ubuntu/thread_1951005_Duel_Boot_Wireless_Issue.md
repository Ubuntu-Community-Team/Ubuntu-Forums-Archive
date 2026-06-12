---
title: "Duel Boot Wireless Issue"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by philberg32 on 2012-04-01
I just downloaded and installed to run this duel boot with W7 (using the Wubi App). I like it so far, and I would like it more if I could connect to the net. It seems that it doesn't recognize any hardware I have for my wireless connection. Is there some kind of update or missing component I need to get?

Any walk through or links to downloads I need and how to get them across to the ubuntu side would be fantastic

Phil

---

### Post by BertN45 on 2012-04-01
you probably need to find the right driver. Try typing lspci (PCI cards) or lsusb (USB dongles) in the Terminal to know what WiFi hardware you are using.

You can use the HW name to google for the driver and any installation prescriptions.

If that does not help, you can come back here and tell us what wifi HW you have. There is a good chance that somebody here has the same wifi and knows what to do.

---

### Post by philberg32 on 2012-04-02
So will ubuntu/Wubi not recognize the current drivers I have installed with Windows 7? I am posting all of this on the laptop I am running the duel boot on (Windows boot of course). This is my first experience with Linux (for a new job), so will I need drivers designed for Linux and if so can I install them from the Windows side into the Ubuntu folder that it needs to be in?

Forgive my lack of knowledge about Ubuntu, hopefully soon I will be providing the answers.

---

### Post by wildmanne39 on 2012-04-02
Hi, ubuntu needs linux drivers, if you do not have a supported wireless device then you can use what is called ndiswrapper but it is the last option you want to try.

Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.

I can help with wireless but depending what card you have you may have to take your computer somewhere you can connect to the internet to install the driver or you could use a cell phone to tether to your computer but I have not personally done this last option but many people have.

EDIT: [COLOR="Red"]Hello westie457[/COLOR]
Thank you

---

### Post by westie457 on 2012-04-02
Hello. Welcome to UF.

You are right in thinking that Ubuntu will not work with Windows drivers and vice-versa, they are in written for different OSes and are incompatible.

If you post the output of ```
lspci -vnn
``` this will let us know which wireless chip you are using and we can then instruct you on how to install the correct drivers.

Installing via Wubi is not meant to be a long term use of Ubuntu it is more of an extended run of using the LiveCD for testing purposes. Sooner or later it is going to break, normally through an update, this is fixable however it is usually better to go the whole hog and dual-boot with separate partitions or even separate hard drives. This last paragraph is advisory only and does not need to be acted on just yet. More like something for you to think about for the future.

Back on topic. Could you also post the output of ```
rfkill list all

lsmod
``` these are separate commands to be run one at a time.

Thank you


PS: Most of my wireless chip knowledge has come from the person who posted immediately before me and yet again he has [COLOR="Red"]NINJAed me[/COLOR]. Hello wildmanne39

---

### Post by philberg32 on 2012-04-02
OK, before I go through all the code analysis, I will tell you I am running a stock Dell Vostro 1500. I am also going to install the full version of ubuntu on this machine, since it is really only for learning ubuntu and getting comfortable with it. I have no real data of files on this machine it was pretty much collecting dust for the past two years.

After I install the full version I will try running the codes you posted.

Thank you both.

---

### Post by Mark Phelps on 2012-04-03
Just so you know ... the Wubi install and a separate install ... are the SAME version.  The Wubi install simply installs from inside MS Windows into a single file.

As far as Ubuntu features are concerned, they are the same.

The same is true regarding Linux drivers.

---

### Post by philberg32 on 2012-04-03
Ok, so I installed the full version of Ubuntu and still can not access any networks. 

Some more specifics....
When I go into setting/network/wireless it says firmware missing.
When I try to access setting/additional drivers it says "Downloading packages indexes failed, please check your network status (no kidding).......

Since I can not access this site from the laptop I am trying to get wireless working on, there will obviously be no cut and paste of terminal info. If you can tell me specifically what data you are looking for from each entry I will type them in a reply.

I did a quick search for vostro 1500 Linux drivers but couldn't find anything real. Of course the dell site only has drivers for Microsoft OS's.

thank you once again.

---

### Post by philberg32 on 2012-04-03
Some of the info from the terminal:

ethernet controller:  Broadcom Corp BCM4401-B0  kernel driver in use: b44
Network Controller:  Broadcom Corp BCM4311 802.11b/g kernel driver in use: b43-pci-bridge

Clicking on the wifi symbol top right of screen shows all greyed out except VPN Connection, Enable Networking (checked), Enable Wireless (checked) and Edit Connections.

Going into edit connections, then wireless, all is blank, so it isn't seeing my wireless network. Such a huge pain just to get familiar with Ubuntu by Monday.

Thanks for the help guys.

---

### Post by philberg32 on 2012-04-03
OK what I did was hook in my wired connection then....

- I removed the STA driver from Additional Drivers
- I opened synaptic and installed b43-fwcutter then firmware-b43-installer
- Reboot

As per an existing post on these forums. Problem solved and I can get to playing with ubuntu.

---

