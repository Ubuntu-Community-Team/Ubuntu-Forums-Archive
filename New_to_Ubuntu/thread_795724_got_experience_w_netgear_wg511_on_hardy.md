---
title: "got experience w/ netgear wg511 on hardy?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by scholzilla on 2008-05-15
I need to buy a wireless card for my gateway mt-series laptop and am looking at the netgear wg511 wireless G PC card. Of course, it doesn't say it's linux compatible and I wanted to find out if others have found this to work out of the box with the windows driver that comes with the cd. I wiped windows off my machine in a moment of glory, but am not sure about driver install and configuration problems w/linux. I can't just try it and return it without paying the odious "restock charge" (yet I can return underwear without a restock charge--go figure). 

Other card suggestions are welcome, but I'm most interested in this one cause i can get it quick and cheap.

thanks

---

### Post by tad1073 on 2008-05-15
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)

---

### Post by scotartt on 2008-05-22
Hello

I already have a WG511 "made in taiwan" card which worked perfectly in the older v 7 ubuntu which i just upgraded to 8.10. However it now, nothing, it's not even there as /dev/eth1

lshw -C network
# produces the following for it


 *-network UNCLAIMED
       description: Network controller
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=28 mingnt=10


Which on the wireless networking page says 'UNCLAIMED' means, the driver is not installed correctly.

However the hardware support page linked to in the post above appears to infer that support is 'built-in' which clearly it isn't in this case. Previously the wireless card "just worked" apart from the actual network configuration. 

I tried a simple 'sudo modprobe -r prism54' followed by 'sudo modprobe prism54' and the thing came to life, and is installed and the 'UNCLAIMED' above goes away. I will try a reboot in a minute and see if it survives that.

[UPDATE] ; Nope. everytime a reboot is done, I have to 'sudo modprobe prism54' to make it load the driver.

---

### Post by scholzilla on 2008-05-22
thanks. I get a similar UNCLAIMED output and also suspect the driver. I have a 64bit architecture and I think the available drivers don't fit. It would be nice if someone would come up with a strategy to make wifi simpler on ubuntu, but apparently it's not an easy thing to do.

---

### Post by stchman on 2008-05-22
> **scholzilla said:**
> I need to buy a wireless card for my gateway mt-series laptop and am looking at the netgear wg511 wireless G PC card. Of course, it doesn't say it's linux compatible and I wanted to find out if others have found this to work out of the box with the windows driver that comes with the cd. I wiped windows off my machine in a moment of glory, but am not sure about driver install and configuration problems w/linux. I can't just try it and return it without paying the odious "restock charge" (yet I can return underwear without a restock charge--go figure). 

Other card suggestions are welcome, but I'm most interested in this one cause i can get it quick and cheap.

thanks

The problem is that the SAME card could have multiple chipsets.  One chipset can be very Linux friendly while another can be very Linux un-friendly.

---

### Post by chili555 on 2008-05-25
There are indeed several chipsets in the WG511; the Taiwan has the Prism54 chipset.

scotartt, the reason your modprobe won't survive a reboot is hidden in */etc/modprobe.d/blacklist:*> # replaced by p54pci
blacklist prism54Does your card come to life if you *sudo modprobe p54pci?* Does it survive a reboot? If not, you can add *p54pci* to */etc/modules.*

---

### Post by scholzilla on 2008-05-26
> **stchman said:**
> The problem is that the SAME card could have multiple chipsets.  One chipset can be very Linux friendly while another can be very Linux un-friendly.

Is there a way to tell which chipsets are present and which are problematic? Thanks.

---

### Post by jimrz on 2008-05-26
I have a Netgear WG511T (the "T" is important) that works outs "out of the box" in 8.04. A freind has the same card and same results, also. It has the Atheros 5212 chipset which is supported by the madwifi drivers. This model is still pretty readily available, but ships with firmware that does not support WPA encryption. If you need WPA, upraded firmware that does WPA is available for download on the Netgear support site. Installation of the upgrade is simple, straightforward and, once completed, works perfectly.

---

### Post by scholzilla on 2008-05-27
unfortunately, i bought the 511 without a T. I can't seem to find a 64bit windows driver for this, so if you know where to get one, please let me know.

---

