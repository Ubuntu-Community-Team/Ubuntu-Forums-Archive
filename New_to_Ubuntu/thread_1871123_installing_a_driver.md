---
title: "installing a driver"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by redno302002 on 2011-10-28
I just installed 10.04, my wireless and wired internet are not working. From reading the other threads, I think I need to install a broadcom driver, I have already downloaded the driver and put on a usb drive. My problem comes when attempting to load the driver, I am very new to ubuntu and am not sure how to use the package system.

Any help would be greatly appreciated.

I am using a Dell inspiron mini.

---

### Post by veggis on 2011-10-28
under prefrences there is gone be an enteri that called hardware driver and activate the drive

---

### Post by mike555 on 2011-10-28
You should have downloaded the driver from the software manager, that way it would have installed and get updated automatically.

---

### Post by cavalier911 on 2011-10-28
Open lxterminal
Type this:
```
lspci -nn > dell.mini.txt
```
hit enter
Type this:
```
less dell.mini.txt
```
hit enter,verify your hardware info is in the file.
hit q to quit less
Copy dell.mini.txt to usb stick,transfer stick to your computer with internet.
Post dell.mini.txt as attachment to your reply:
Additional Options/Attach Files/Manage Attachments/Choose file
Browse to dell.mini.txt/Open/Upload

---

### Post by redno302002 on 2011-10-28
Is this what you wanted me to do?

---

### Post by cavalier911 on 2011-10-29
Yes,you did good.
All commands run in lxterminal:
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [**10ec:8136**] (rev 02)
```
 grep 8136 /lib/modules/$(uname -r)/modules.pcimap
**r8169 **               0x000010ec 0x00008136 0xffffffff 0xffffffff 0x00000000 0x00000000 0x0

```
**r8169** is the kernel module driver for your ethernet card

03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [**14e4:4315**] (rev 01)
```
grep **4315 **/lib/modules/$(uname -r)/modules.pcimap
**ssb**                  0x000014e4 0x00004315 0xffffffff 0xffffffff 0x00000000 0x00000000 0x0
```
```
grep **ssb ** /lib/modules/$(uname -r)/modules.dep
kernel/drivers/net/wireless/b43/**b43**.ko: kernel/drivers/ssb/ssb.ko kernel/net/mac80211/mac80211.ko kernel/net/wireless/cfg80211.ko kernel/drivers/leds/led-class.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko: kernel/drivers/ssb/ssb.ko kernel/net/mac80211/mac80211.ko kernel/net/wireless/cfg80211.ko kernel/drivers/leds/led-class.ko
kernel/drivers/net/b44.ko: kernel/drivers/ssb/ssb.ko kernel/drivers/net/mii.ko
kernel/drivers/ssb/ssb.ko:
```
Broadcomm mini-pci chipset connects to PCI bus through Sonics Silicone Backplane(ssb) mini-bus

**b43 **is kernel module driver for your wireless

b43 requires b43-fwcutter to download/extract/cut/install firmware to /lib/firmware but you must have internet connection
```
sudo apt-get install b43-fwcutter
```
Blue/gray screen appears asking for permission to fetch firmware.
Choose yes
To bring up configure b43-fwcutter again:
```
sudo dpkg-reconfigure b43-fwcutter
```

You should try to get the wired ethernet working so b43-fwcutter can fetch the firmware.If you have another computer that runs ubuntu with internet install b43-fwcutter and get the firmware.Copy the b43 folder from /lib/firmware to a usb stick and move it to /lib/firmware 

Run command in lxterminal:
```
ifconfig > ifconfig.txt
```
Enter
```
sudo lshw -c network > network.txt
```
Enter
Please attach to reply.

---

### Post by beew on 2011-10-29
??? Just run Hardware Drivers it will find and install the driver for you. Then restart and that's it.

One thing about Ubuntu is try to avoid downloading drivers from the manufactures as much as possible. It is not like Windows. Install manually is complicated, it doesn't get updated and may screw things up.

---

### Post by redno302002 on 2011-10-30
I am posting this from my dell mini loaded with 10.04! 

Thank you for all your help cavalier911!

---

### Post by anewguy on 2011-10-30
> **beew said:**
> ??? Just run Hardware Drivers it will find and install the driver for you. Then restart and that's it.

In my experience, this doesn't always work, particularly with the 4311 and 4312.  They do require the firmware cutter and extra firmware downloaded from the net.  There is an "all" firmware package out there that usually is used to solve this with no problem.

> One thing about Ubuntu is try to avoid downloading drivers from the manufactures as much as possible. It is not like Windows. Install manually is complicated, it doesn't get updated and may screw things up.

Sometimes it is necessary to download the driver from the manufacturer, so this is still needed.  Indeed, most aren't automatically updated, but for most it is not complicated to install them.

cavalier911:  great job helping the OP!!


Dave ;)

---

