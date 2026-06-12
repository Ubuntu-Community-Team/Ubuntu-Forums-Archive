---
title: "Bluetooth not working on ubuntu 14.04"
date: 2016-03-24
forum: New to Ubuntu
---

### Post by xavier-senra on 2016-03-24
Hello,
Bluetooth is not working on my ubuntu 14.04 (in a asus N751JX-T7024H laptop).

I've installed Bluetooth Manager and I have alto tried with installing bluetooth driver packages:  
sudo apt-get install bluez bluez-alsa bluez-audio bluez-btsco bluez-compat bluez-cups bluez-dbg bluez-gstreamer bluez-hcidump bluez-pcmcia-support bluez-tools bluez-utils python-bluez bluewho indicator-bluetooth libbluetooth-dev libgnome-bluetooth11 libbluetooth3 python-gobject python-dbus

as suggested on the post [http://askubuntu.com/questions/490346/bluetooth-not-working-in-ubuntu-14-04-lts](http://askubuntu.com/questions/490346/bluetooth-not-working-in-ubuntu-14-04-lts)

But no success...

Any idea?

Thank you.

---

### Post by jeremy31 on 2016-03-24
Post the result of ```
lsusb; uname -a; lspci -nnk | grep -iA2 net; rfkill list all
```

---

### Post by xavier-senra on 2016-03-29
The result to that command is:

$ lsusb; uname -a; lspci -nnk | grep -iA2 net; rfkill list all
Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 04f2:b3fd Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 13d3:3480 IMC Networks 
Bus 001 Device 004: ID 046d:c050 Logitech, Inc. RX 250 Optical Mouse
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Linux Xavi-portatil-gris 3.19.0-56-generic #62~14.04.1-Ubuntu SMP Fri Mar 11 11:03:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
03:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: AzureWave Device [1a3b:211f]
    Kernel driver in use: ath9k
--
04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by jeremy31 on 2016-03-29
[COLOR=#333333][FONT=monospace]Post
```
usb-devices | awk '/3480/' RS=
```

I suspect the 13d3:3480 is the bluetooth device and it isn't supported in that kernel

I would file a bug report also, start at [/FONT][/COLOR]https://bugs.launchpad.net/ubuntu/+source/linux/+filebug

---

### Post by mörgæs on 2016-03-30
No, don't file bugs against old software like 14.04. If the problem also appears in 16.04 then we *might *need to file a bug.

---

### Post by Geoffrey_Arndt on 2016-03-30
Another solution - get a supported bluetooth dongle from Panda (works great - - plug & play)

[http://www.pandawireless.com/](http://www.pandawireless.com/)

---

### Post by jeremy31 on 2016-03-31
If the 13d3:3480 device is the bluetooth the issue remains in bluetooth-next.git

I see no reason to buy another bluetooth when the patch is only 3 or 4 lines

---

### Post by Geoffrey_Arndt on 2016-03-31
Never hurts to have options . . .

---

### Post by xavier-senra on 2016-04-02
Finally I will wait until I update to ubuntu 16.04 and see what happens...

Thank you for the options.

---

### Post by jeremy31 on 2016-04-02
Nothing will change unless a bug report is filed.  Ubuntu won't even know about this device existing

This is a list of Atheros ID from bluetooth-next
```
[COLOR=#000000]{[/COLOR][COLOR=#000000] [/COLOR][COLOR=#010181]USB_DEVICE[/COLOR][COLOR=#000000]([/COLOR][COLOR=#2928FF]0x0489[/COLOR][COLOR=#000000],[/COLOR][COLOR=#000000] [/COLOR][COLOR=#2928FF]0xe04d[/COLOR][COLOR=#000000]) },[/COLOR]	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0489[/COLOR], [COLOR=#2928FF]0xe04e[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0489[/COLOR], [COLOR=#2928FF]0xe057[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0489[/COLOR], [COLOR=#2928FF]0xe056[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0489[/COLOR], [COLOR=#2928FF]0xe05f[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0489[/COLOR], [COLOR=#2928FF]0xe076[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0489[/COLOR], [COLOR=#2928FF]0xe078[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0489[/COLOR], [COLOR=#2928FF]0xe095[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x04c5[/COLOR], [COLOR=#2928FF]0x1330[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x04CA[/COLOR], [COLOR=#2928FF]0x3004[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x04CA[/COLOR], [COLOR=#2928FF]0x3005[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x04CA[/COLOR], [COLOR=#2928FF]0x3006[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x04CA[/COLOR], [COLOR=#2928FF]0x3007[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x04CA[/COLOR], [COLOR=#2928FF]0x3008[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x04CA[/COLOR], [COLOR=#2928FF]0x300b[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x04CA[/COLOR], [COLOR=#2928FF]0x300d[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x04CA[/COLOR], [COLOR=#2928FF]0x300f[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x04CA[/COLOR], [COLOR=#2928FF]0x3010[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x04CA[/COLOR], [COLOR=#2928FF]0x3014[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0930[/COLOR], [COLOR=#2928FF]0x0219[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0930[/COLOR], [COLOR=#2928FF]0x021c[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0930[/COLOR], [COLOR=#2928FF]0x0220[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0930[/COLOR], [COLOR=#2928FF]0x0227[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0b05[/COLOR], [COLOR=#2928FF]0x17d0[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0CF3[/COLOR], [COLOR=#2928FF]0x0036[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0CF3[/COLOR], [COLOR=#2928FF]0x3004[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0CF3[/COLOR], [COLOR=#2928FF]0x3008[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0CF3[/COLOR], [COLOR=#2928FF]0x311D[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0CF3[/COLOR], [COLOR=#2928FF]0x311E[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0CF3[/COLOR], [COLOR=#2928FF]0x311F[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0cf3[/COLOR], [COLOR=#2928FF]0x3121[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0CF3[/COLOR], [COLOR=#2928FF]0x817a[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0CF3[/COLOR], [COLOR=#2928FF]0x817b[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0cf3[/COLOR], [COLOR=#2928FF]0xe003[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0CF3[/COLOR], [COLOR=#2928FF]0xE004[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0CF3[/COLOR], [COLOR=#2928FF]0xE005[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x0CF3[/COLOR], [COLOR=#2928FF]0xE006[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x13d3[/COLOR], [COLOR=#2928FF]0x3362[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x13d3[/COLOR], [COLOR=#2928FF]0x3375[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x13d3[/COLOR], [COLOR=#2928FF]0x3393[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x13d3[/COLOR], [COLOR=#2928FF]0x3395[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x13d3[/COLOR], [COLOR=#2928FF]0x3402[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x13d3[/COLOR], [COLOR=#2928FF]0x3408[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x13d3[/COLOR], [COLOR=#2928FF]0x3423[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x13d3[/COLOR], [COLOR=#2928FF]0x3432[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x13d3[/COLOR], [COLOR=#2928FF]0x3472[/COLOR]) },
	{ [COLOR=#010181]USB_DEVICE[/COLOR]([COLOR=#2928FF]0x13d3[/COLOR], [COLOR=#2928FF]0x3474[/COLOR]) },
```
No 13d3,3480 in the list

---

### Post by mörgæs on 2016-04-02
From which release does the list come?

---

### Post by jeremy31 on 2016-04-02
That is from the bluetooth dev's git [http://git.kernel.org/cgit/linux/kernel/git/bluetooth/bluetooth-next.git/tree/](http://git.kernel.org/cgit/linux/kernel/git/bluetooth/bluetooth-next.git/tree/)

The last new device added was 13d3:3472 on March 10

---

### Post by drm200 on 2016-06-19
> **mörgæs said:**
> No, don't file bugs against old software like 14.04. If the problem also appears in 16.04 then we *might *need to file a bug.

I am using Ubuntu 14.04 LTS because it is supported until 2019.

Your moniker "Staff Emeritus" seems to tell me that you are an official Ubuntu mouthpiece.  So, it seems that this is official notice that Ubuntu that 14.04 is not supported til 2019 but its end of life is now.  

Is that correct?  It is important to me to know the real picture.  Release 16 is too buggy for me to go to (I've already tried it) ... And if 14.04 LTS is not going to be properly supported by Ubuntu, then I give up.

Please clarify your comment and let us know if this is official Ubuntu speak.

---

### Post by coffeecat on 2016-06-19
> **drm200 said:**
> Your moniker "Staff Emeritus" seems to tell me that you are an official Ubuntu mouthpiece.  So, it seems that this is official notice that Ubuntu that 14.04 is not supported til 2019 but its end of life is now.  

Let me correct you. **No one** on this forum is an "official Ubuntu mouthpiece". We are all - forum staff included - volunteers, mostly ordinary users such as yourself. But this is the official forum, recognised by Canonical, for Ubuntu, just one of several [community support venues for Ubuntu](http://community.ubuntu.com/help-information/). The word emeritus in mörgæs' user title means what emeritus always means - retired. 

As far as Ubuntu 14.04 is concerned, it is supported until 2019 - see here: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by mörgæs on 2016-06-25
14.04 is supported in the sense that security related bugs are fixed, not bugs in general. That's why people should as a rule of thumb install the latest Buntu when they encounter a non-security bug in old software. 

How did Bluetooth work in 16.04?

If you tell which other bugs are present in 16.04 we might be able to show a solution.

---

