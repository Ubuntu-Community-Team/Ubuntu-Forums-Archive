---
title: "How To Configure The Netopia TER/GUSB-N USB Wireless Adapter"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by hugoBOSS81 on 2012-12-10
> **chili555 said:**
> Awesome!Even more awesome! 

Your device is claimed by rt73usb as *modinfo* tells us:```
chili@LAPTOP60:~$ modinfo rt73usb | grep 9021
alias:          usb:v0EB0p9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]9021[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```*modinfo* also says that firmware is required:You can check for its existence with:```
ls /lib/firmware | grep rt7
```If it's not there, drag the server back to the ethernet cable and do:```
sudo rmmod -f rt73usb
sudo apt-get install linux-firmware
sudo modprobe rt73usb
iwconfig
```Did the wireless come to life?

If the firmware is present and the wireless doesn't work, there is another problem. Diagnose with:```
dmesg | grep -i rt7
lsmod | grep rt
```Please post any suspicious readings.

OMG !!! you are the man !! I've been searching the net for 3 days, several hrs a day for this solution and gone through more than 3 dozen articles with how-to instructions and none of them worked. i read your post once and tried it and BAM! My wifi network was up instantly I had eth0 and wlan0 connect properly simultaneously at that so i tested them individually to ensure they worked properly. You saved me from going back to windows 8 lol 7 was the most I'd use anyway. :lolflag: Best part is I've managed to build a stable desktop on an MSI K8NGM-V board with built-in graphics with full hardware acceleration using the NVIDIA-Linux proprietary drivers 304.64, 2GB RAM, PCI HSUSB, Crystal Soundfusion audio, 120GB "C" drive, 1TB SATA, & 20 inch flat-screen using Ubuntu 12.04 with kernel 3.4.0.xxx-generic upgrade and numerous goodies. THANKS A MILLION !!! Now to make my custom Remastersys DVD. :guitar:

---

### Post by chili555 on 2012-12-10
I'm very glad to have helped. I usually encourage posters who have solved the issue to have fun, but it sounds like you are having lots of fun already!

---

### Post by hugoBOSS81 on 2012-12-10
> **chili555 said:**
> I'm very glad to have helped. I usually encourage posters who have solved the issue to have fun, but it sounds like you are having lots of fun already!

Interestingly enough, I removed the Ethernet connection, rebooted and now i have WiFi working (it's detected but not connected), but it won't connect to my network. i don't have any need for a password on my WiFi as i don't have any neighbors within a 50 ft radius to pick it up lol so it's just an open network but the network manager sees it as a hidden network but won't establish the connection now. any clues?

---

### Post by chili555 on 2012-12-10
Any clues here?```
nm-tool
sudo iwlist wlan0 scan
```

---

### Post by sandyd on 2012-12-10
**moved to own thread**

Please do not post in threads more than one year old

Thanks!

---

### Post by hugoBOSS81 on 2012-12-10
> **chili555 said:**
> Any clues here?```
nm-tool
sudo iwlist wlan0 scan
```

```
nm-tool
```
State: disconnected
--------------------
Device: eth0
Type: wired
Driver: forcedeth
state: unavailable
Default: no
HW address: 00:13: D3:E2:C1:81

Capabilties:
Carrier Detect: yes
Wired Properties:
Carrier: off

Device: wlan0
Type: 802.11 wifi
Driver: ndiswrapper
State: disconnected
Default: no
HW Address: 00: D0:41:C0:B7:39

Capabilties:
-Wireless Properties:
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes

Wireless Access Point

```
sudo iwlist wlan0 scan
```
wlan0 No scan results

Odd thing is it worked fine at first when i had the clean install of 12.04 precise. I didn't know upgrading the kernel would affect the wifi drivers from what I've read online. I'm almost to the point of taking on the task of recomiling the kernel to include the drivers from either the original 12.04 or the ones off the install cd from the USB adapter even though they are windows drivers. I used the "windows wireless drivers" tool app if that helps any.

---

### Post by hugoBOSS81 on 2012-12-10
> **sandyd said:**
> **moved to own thread**

Please do not post in threads more than one year old

Thanks!

Sorry about that, this was an issue I just now came across and i stumbled upon this thread in the forum search i did plus chili555 answered right away.

---

