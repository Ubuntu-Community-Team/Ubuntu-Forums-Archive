---
title: "No Wireless Connection"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by Crocodileofdoom on 2011-10-27
Hello

I have a Dell 1464 and I just downloaded Ubuntu, everything went smooth, but I have no WiFi, when I click in the signal icon it says the following:

> Wireless Networks device no ready (firmware missing)

What must I do to configure it?

---

### Post by Silent Warrior on 2011-10-27
Step 1: Find out what hardware you're trying to use - it helps. :) Looking through the online documentation, I found nothing that mentions the Dell 1520 WLAN card specifically, but several of Dell's earlier WLAN cards appear to have worked with Broadcom drivers. I assume this means wireless connections don't work - so get connected by wire, or download the packages from a public computer, or whatever. Make sure you have linux-firmware installed. It doesn't look like linux-firmware-nonfree will help you, but I'll mention it all the same. There are also a whole ton of different Broadcom firmwares in the repository, though they won't help you unless your card actually uses those chipsets. Good luck finding that out... I'm coming up dry.

[http://www.laptops-drivers.com/dell-laptop/dell-inspiron-1464-lan-wifi-and-bluetooth-driver.html](http://www.laptops-drivers.com/dell-laptop/dell-inspiron-1464-lan-wifi-and-bluetooth-driver.html) <- You could MAYBE get the driver pack from here to work through Ndiswrapper - assuming this is the driver for your card.

Oh, waitwaitwait, just stumbled across this: [http://www.backtrack-linux.org/forums/beginners-forum/1723-bt4-boot-cd-dell-1764-dell-1520-wireless-card.html](http://www.backtrack-linux.org/forums/beginners-forum/1723-bt4-boot-cd-dell-1764-dell-1520-wireless-card.html) Have a look here FIRST OF ALL, mkay?

---

### Post by Crocodileofdoom on 2011-10-27
> Step 1: Find out what hardware you're trying to use - it helps. :smile: Looking through the online documentation, I found nothing that mentions the Dell 1520 WLAN card specifically, but several of Dell's earlier WLAN cards appear to have worked with Broadcom drivers. I assume this means wireless connections don't work - so get connected by wire, or download the packages from a public computer, or whatever. Make sure you have linux-firmware installed. It doesn't look like linux-firmware-nonfree will help you, but I'll mention it all the same. There are also a whole ton of different Broadcom firmwares in the repository, though they won't help you unless your card actually uses those chipsets. Good luck finding that out... I'm coming up dry.

[[COLOR=#444444]http://www.laptops-drivers.com/dell-...th-driver.html[/COLOR]]("http://www.laptops-drivers.com/dell-laptop/dell-inspiron-1464-lan-wifi-and-bluetooth-driver.html") <- You could MAYBE get the driver pack from here to work through Ndiswrapper - assuming this is the driver for your card.

Oh, waitwaitwait, just stumbled across this: [[COLOR=#444444]http://www.backtrack-linux.org/forum...less-card.html[/COLOR]]("http://www.backtrack-linux.org/forums/beginners-forum/1723-bt4-boot-cd-dell-1764-dell-1520-wireless-card.html") Have a look here FIRST OF ALL, mkay
 
Thanks i'll check that

---

### Post by varunendra on 2011-10-28
Hello *Crocodileofdoom*, and welcome to the forums:) (nice username by the way ;)),

To let us know the hardware details of your network interface, and whether or not a driver/firmware is associated with it, please open a terminal, enter the following command and post back the output here:
```
sudo lshw -C network
```Please wrap the output in 'code' tags (like I did above) by selecting (only) the pasted output text, and clicking on the **#** symbol at the top of the edit box in which you write your posts. Doing so preserves the formatting and makes it more readable.

---

### Post by computerandu on 2011-10-28
> **Crocodileofdoom said:**
> Hello

I have a Dell 1464 and I just downloaded Ubuntu, everything went smooth, but I have no WiFi, when I click in the signal icon it says the following:



What must I do to configure it?

Dell 1464...may be a Broadcom adapter. What is the output of following ciommands:

iwconfig

sudo rfkill list all

---

### Post by Crocodileofdoom on 2011-10-28
First of all thanks for the warm wellcome (*Varunendra*) and for the replies(*Computerandu, Varunendra and Silent Warrior*).

Secondly I'll what you told me.

When I insert the code provided by *Varunendra*:

```
sudo lshw -C network
```

This is the output:

```
*-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0400000-f0403fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: b8:ac:6f:5b:36:67
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.103 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:2000(size=256) memory:f0810000-f0810fff memory:f0800000-f080ffff memory:f0820000-f083ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 4
       logical name: wlan0
       serial: f0:7b:cb:67:67:d9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

```


And with the ones that *Computerandu* gave:

With the first one:

```
iwconfig
```

The output is:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

```



And with the last code:

```
sudo rfkill list all
```

The output is:

```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```


Silent Warrior: I appreciate your help but unforutnately it didn't work :)
THANKSSSSS!!!!!! :D

---

### Post by gandaran on 2011-10-28
> description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
look first in additional drivers to activate broadcom driver or check out here what you need to install
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by TBABill on 2011-10-28
With the BCM4312 (same adapter I have in 3 machines) you will have the easiest time with the STA driver. Sometimes Ubuntu will offer both b43 and STA. Choose the STA and follow the prompts, reboot and enjoy. You'll need to be connected via ethernet first.
 
As a side note, on future installs just go into the live session and enable the driver via additional drivers. However, when it says to restart to make the change work, DON'T! Just open a terminal and ```
sudo modprobe wl
``` and then wait a minute or so. You should then be able to connect during the live session AND you will have a permanent wireless configuration up and working when the install finishes.

---

### Post by varunendra on 2011-10-28
So you indeed have a broadcom chip. Please try this first:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```Let the command finish its task, then-
```
sudo apt-get install firmware-b43-installer b43-fwcutter
```If this doesn't help, post outputs of:
```
lsmod
cat /etc/modprobe.d/blacklist.conf
ls /etc/modprobe.d/blacklist*
```

**Edit:**
Looks like I need to increase my responding speed :)

**PS:**
Assuming OP has 11.10 installed, I think "Additional Drivers" option will only offer sta drivers which do not seem to work with 11.10. Accordingly, I recommend to try the b43 drivers first as I posted above, and make sure it is not blacklisted by any previous attempts with sta drivers.

---

### Post by computerandu on 2011-10-28
Follow the instructions in this post and do erevrt back if it solves:

[http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

---

### Post by AvalonSpirit on 2011-10-28
Ok, so you have a broadcom BCM43xx wireles card:

Check this help page: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") (it actually took me a while to find when I was having a similar problem)

If you can connect to a wired network check [Step 3.1]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_Internet_access")
If you can't get online you can use either the live CD or the live USB you installed from by following [Step 3.2]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access").

If you use your live session, you dont have to boot it, just use it to get the drivers.

Hope this helps!

---

### Post by Crocodileofdoom on 2011-10-28
Thaaaaanks!!!!!!!!!!!

It worked!!!!!!!!!

I really but really appreciate this help!!!!

Thanks to you all!!!!!!!!

[I]Silent Warrior
Varunendra
Computerandu
AvalonSpirit
Gandaran
TBABill[/I]

:popcorn:

---

### Post by varunendra on 2011-10-28
> **Crocodileofdoom said:**
> Thaaaaanks!!!!!!!!!!!

It worked!!!!!!!!!

I really but really appreciate this help!!!!

Thank you all!!!!!!!!

:popcorn:
We'd really appreciate your feed back on 'which one worked'? The sta driver or the b43? If not sure, just tell us the method you tried.
Thank you.

---

### Post by Crocodileofdoom on 2011-10-28
Sorry I forgot to post it I was too happy :)

For me the one proposed by Gandaran was the one that worked for me, but thanks again I tried every single one!!!!!! :D

---

