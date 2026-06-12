---
title: "Edimax 7218g RT61 wirless PCI card problems"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by RaptorSW on 2008-05-24
Hi All,

New to this Forum and Ubuntu and look forward to learning lots about Linux.

This leads me on to my first hurdle.

Installed Unbuntu 8.04 on a home built system.  Installation was fine (has some probs with sound but this was a MOBO issue) and all appears fine - except one thing.

I added a Edimax Wireless PCI card which runs the RT61 chipset.  lspci shows that it had identified the card (Network Controller: RaLink RT2561/Rt61 802.11g PCI).  

I then added the relevant details into the Network manager (SSID, WPA key etc).  However, no connection with the router was made (tried pinging but no luck).  I added some lines to /etc/network/interfaces (as detailed in [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)) but still no luck.

Have no idea what to do about this.  I can only assume it has something to do with WPA.

I know that the card is partially working since 'iwlist scan' will show wireless networks (although my networks SSID is not always picked up).

Please could somebody give me some advice - I'm pulling my hair out here and have spent most of the day attempting to fix this. :( 

Thanks in Advance

Simon

---

### Post by nick_h on 2008-05-25
You may have to install another driver.

Have a look at the [hardware support](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax) page for Edimax network cards.

---

### Post by RaptorSW on 2008-05-25
I ended up downloading the driver from the Ralink website and rebuilding.  Now have a wireless connection :guitar:

However, I currently have to manually start the connection everytime I reboot.  I added my SSID and WPA passkey settings to /etc/network/interfaces but it's not being picked up.  The only way I can get it working is via Network Manager (have to re-enter my passkey).  Could it be that Network Manager is causing the problem?

Anyone have any ideas?:confused:

---

