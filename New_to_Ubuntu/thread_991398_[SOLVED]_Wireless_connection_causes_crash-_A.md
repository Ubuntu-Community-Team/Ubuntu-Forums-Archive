---
title: "[SOLVED] Wireless connection causes crash- A"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by tjaysus on 2008-11-23
Hi All,

First post and new user so bear with me! 

Just made a fresh install of Intrepid in dual boot with Vista on my desktop. 

My first problem lies with my wireless connection. As soon as a connection is established, the system crashes- no response at all and I have to physically reboot. On the few times that it has not crashed straight away, I have however been able to connect as usual to the web and synaptic. 

Within Vista, I have a connection as usual without problems.

I have a D-Link DWA-547 which uses an Atheros chipset I believe. I know there is a lot of info concerning the use of Madwifi or ath9k/ath5k drivers. Currently, I have no drivers relating to my wireless adapter listed in System>Admin>Hardware Drivers, although lspci -v prints 'Kernel driver in use: ath9k'.

It's a bit vague I know but its probably more useful for me to ask you what information would be most helpful.

Any guidance would be most appreciated. Thanks in advance.

Tim

---

### Post by jimmy the saint on 2008-11-23
Hey, try the solution in this thread.  It seems to me that it is likely a driver issue.  I saw a few bug reports after doing a quick google search, but didn't look into them too deeply.  This thread, on the other hand, seems to have a simple solution to issues with your card.  It is worth a shot.  If it does work, please mark this one as solved and post back to indicate that the link includes the appropriate fix.  That will ensure that others with similar issues can find the fix easily!

Good Luck 
JTS
Oh yeah, the link!
[http://www.uluga.ubuntuforums.org/showthread.php?t=490500](http://www.uluga.ubuntuforums.org/showthread.php?t=490500)

---

### Post by tjaysus on 2008-11-24
Firstly, thanks Jimmy for the help. 

Using ndiswrapper and ndisgtk I have had zero problems. Downloaded the latest driver from the D-Link website, version 1.31_b02 and the connection has been flawless so far. 

Now, I may be being overly inquisitive but...

I actually used the ndiswrapper documentation @ [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) for code guidance rather than the thread, and within this it suggested adding existing drivers(?) to the blacklist

>  /etc/modprobe.d/blacklist file and add blacklist bcm43xx, blacklist b43, blacklist b43legacy and blacklist ssb to the end of the file.) Note: This only effects what is loaded at startup, so you will have to reboot to have the bcm43xx drivers disabled. If you have an atheros based card, remember to blacklist not only ath_pci, but also ath_hal, since ndiswrapper won't work if ath_hal is still loaded. 

I included ath_pci and ath_hal as it is an Atheros chipset. 

Anyhow, using lspci I now recieved the printout

```
03:06.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
	Subsystem: D-Link System Inc Device 3a6b
	Flags: bus master, fast Back2Back, 66MHz, medium devsel, latency 128, IRQ 16
	Memory at effe0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ndiswrapper
	Kernel modules: ath9k

```

ath9k still appears? Is that as expected. Could someone just clarify what I have blacklisted? Are they alternative drivers?

Im really very grateful for the help. Just trying to understand a little better what I have done!

Cheers, Tim

---

