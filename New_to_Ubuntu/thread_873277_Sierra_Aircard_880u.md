---
title: "Sierra Aircard 880u"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by stolks on 2008-07-28
Hi, I have been trialling Ubuntu and I am very surprised at how the whole Linux desktop has progressed over the past couple of years.  I am really hopeful that I can finally get rid of Vista and XP.

I am currently trying to install a Sierra Aircard 880U on an ASUS Laptop F3J Series.  I have gone through various iterations of ppp and kppp installations, setups, etc and I now have the card working; well sort of.


The modem connects, cause I can see the details panel with assined IP and the graph ticks over etc.  I also see the modem in 'Network Tools' with  assigned IP address.  

My problem is that I cant get a network connection on the modem. That is I cant see the internet via the modem?  Can anyone help?

I should add that when is use pppd I get the following:
IPCP: timeout sending Config-Requests
sent [LCP TermReq id=0x2 "No network protocols running"]
sent [LCP TermReq id=0x3 "No network protocols running"]
Connection terminated.
Modem hangup

Which is why I went to kppp - which seems to work, but I am doubtful about the network protocol.

I'd appreciate if some could help.

Regards

Steve

---

### Post by charliedontserf on 2008-08-23
Hi Steve,

I´d be interested to know how you got it working at all.

I´m using a PC, ubuntu and an 880U.

I can´t seem to get it going in ppd or kppp.

Any help appreciated.

Cheers,

AC

---

### Post by WombatOfDoom on 2008-10-08
I have it working well on my laptop. Currently, I have 8.10 (Intrepid), but I was using 8.04 (Hardy) with the same setup.

Ubuntu recognises the device automatically, and creates /dev/ttyUSB0, /dev/ttyUSB1, /dev/ttyUSB2.

I downloaded and installed the (GPL) Vodafone mobile connect software from Betavine.net. I'm currently running version 2.0beta3 ( [https://forge.betavine.net/projects/vodafonemobilec/](https://forge.betavine.net/projects/vodafonemobilec/) )

DON'T start the software until you have done the next step!

Drop the text at the bottom of this post into a the file /usr/share/vodafone-mobile-connect-card-driver-for-linux/sierrawireless_880.py .The directory should already exist.

Start the VMC software, via Applications->Internet->Vodafone Mobile Connect, it should recognise your 880U and you should be able to configure your APN by hand. I didn't have to do much configuration, but I'm a Vodafone customer. YMMV

I can connect to the internet, and send/receive text messages. The only downside is that in 8.04, interaction with Network Manager is pretty poor, so you have to tell Firefox that you are online manually.

There are rumours the Network Manager in 8.10 will support WWAN, but I've not got that working yet.

```
"""
DevicePlugin for the Sierra Wireless 880 datacard. Mostly copied from
the 875 card code. Licensed under the GPL.
"""

from vmc.common.exceptions import DeviceLacksExtractInfo
from vmc.common.plugin import DBusDevicePlugin

from vmc.common.hardware.sierra import SierraWirelessCustomizer

class SierraWireless880(DBusDevicePlugin):
    """L{vmc.common.plugin.DBusDevicePlugin} for SierraWireless 880"""
    name = "SierraWireless 880"
    version = "0.1"
    author = "James Radley"
    custom = SierraWirelessCustomizer
    
    __remote_name__ = "MC8780"   #response from AT+CGMM

    __properties__ = {
        'usb_device.vendor_id' : [0x1199],
        'usb_device.product_id': [0x6855],
    }

    def extract_info(self, children):
        # Sierra Wireless uses ttyUSB0 for the connection, ttyUSB2 for control
        for device in children:
            try:
                if device['serial.port'] == 0: # data port
                    self.dport = device['serial.device'].encode('utf8')
                elif device['serial.port'] == 2: 
                    self.cport = device['serial.device'].encode('utf8')
            except KeyError:
                pass
        
        if not self.dport or not self.cport:
            raise DeviceLacksExtractInfo(self)

    
sierrawireless880 = SierraWireless880()[/FONT]
```

---

### Post by crutch on 2008-11-05
Hi,
I followed the instructions that you gave, including dropping the text into the specified file, but when I start the program it fails to detect my modem (Sierra aircard 880U) Anything I might have missed?

---

