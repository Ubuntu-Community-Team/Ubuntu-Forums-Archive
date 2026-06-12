---
title: "bluetooth - asus ux301"
date: 2014-09-24
forum: New to Ubuntu
---

### Post by cad2 on 2014-09-24
hello,

can you please help with the following? thank you!

- i have installed Ubuntu 14.04 on an Asus UX301 - everything worked "out of the box", except for Bluetooth;
- "Blueman" is installed;

- the following packages are also installed (though i don't know if I really need them):    
[I]sudo apt-get install bluez bluez-alsa bluez-audio bluez-btsco bluez-compat
bluez-cups bluez-dbg bluez-gstreamer bluez-hcidump
bluez-pcmcia-support bluez-tools bluez-utils python-bluez bluewho
indicator-bluetooth libbluetooth-dev libgnome-bluetooth11
libbluetooth3 python-gobject python-dbus

[/I]- if i go to SystemSettings>Bluetooth>Bluetooth ON>show Bluetooth status in menu bar, nothing happens: no icon appears on the taskbar + if i close the window and re-open it, Bluetooth is back on the OFF position;
- if I repeatedly click on ON and OFF (SystemSettings>Bluetooth), the Bluetooth icon mysteriously appears on the taskbar. At this stage, the following happens: 
a) i click on the icon and activate Bluetooth: the icon remains visible. I then click on the icon again>set up new device. "Searching for devices" appears and nothing more can be done (tried to pair with an android phone), except that my WiFi connection seems somehow to be affected (I tried four or five times - regularly my WiFi Wlan disconnects and reconnects a minute or so later),
b) i click on the icon, activate Bluetooth AND make it visible: the icon disappears from the taskbar...

any idea? thanks!

---

### Post by xc3RnbFO8P on 2014-09-24
I lost the bluetooth icon to day after Kernel update and I got it back by doing:
> sudo apt-get install --reinstall linux-image-$(uname -r) 
and restart

---

### Post by cad2 on 2014-09-24
thanks but that didn't work for me. The icon does now appear on the taskbar, though the issue described at a) and b) remains the same.

---

### Post by xc3RnbFO8P on 2014-09-24
Do you have a bluetooth dongle that you can try?
could be conflict between wifi and bluetooth.

---

### Post by cad2 on 2014-09-25
unfortunately i haven't got any bluetooth dongle...any alternative you could please think of? thanks!

---

### Post by xc3RnbFO8P on 2014-09-25
After last kernel update my onboard bluetooth stop working, but it works with bluetooth dongle.
Your bluetooth is running but not connecting.
Did it work in the past?


> ringi@ringi-Lenovo-Ideapad-Flex-15:~$ inxi -Fxz
System:    Host: ringi-Lenovo-Ideapad-Flex-15 Kernel: 3.13.0-36-generic x86_64 (64 bit, gcc: 4.8.2) 
           Desktop: Xfce 4.11.6 (Gtk 2.24.23) Distro: Ubuntu 14.04 trusty
Machine:   System: LENOVO (portable) product: 20309 version: Lenovo Ideapad Flex 15
           Mobo: LENOVO model: Strawberry 5D version: 31900003Std Bios: LENOVO version: 8ACN07WW date: 07/31/2013
CPU:       Dual core Intel Core i3-4010U CPU (-HT-MCP-) cache: 3072 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 6784.38 
           Clock Speeds: 1: 782.00 MHz 2: 782.00 MHz 3: 782.00 MHz 4: 782.00 MHz
Graphics:  Card: Intel Haswell-ULT Integrated Graphics Controller bus-ID: 00:02.0 
           X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1366x768@60.0hz 
           GLX Renderer: Mesa DRI Intel Haswell Mobile GLX Version: 3.0 Mesa 10.2.2 Direct Rendering: Yes
Audio:     Card-1: Intel Lynx Point-LP HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 
           Card-2: Intel Haswell-ULT HD Audio Controller driver: snd_hda_intel bus-ID: 00:03.0 
           Sound: Advanced Linux Sound Architecture ver: k3.13.0-36-generic
Network:   **Card-1: Qualcomm Atheros AR9485 Wireless Network Adapter driver: ath9k bus-ID: 02:00.0**
           IF: wlan0 state: up mac: <filter>
           Card-2: Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
           driver: r8169 ver: 2.3LK-NAPI port: 3000 bus-ID: 01:00.0
           IF: eth0 state: down mac: <filter>
           Card-3: Atheros usb-ID: 002-005
           IF: N/A state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 500.1GB (4.9% used) 1: id: /dev/sda model: ST500LM000 size: 500.1GB 
Partition: ID: / size: 107G used: 23G (23%) fs: ext4 ID: swap-1 size: 4.00GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 47.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 261 Uptime: 1:24 Memory: 1521.5/3679.5MB Runlevel: 2 Gcc sys: 4.8.2 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 
ringi@ringi-Lenovo-Ideapad-Flex-15:~$ 

---

### Post by xc3RnbFO8P on 2014-09-25
One thing you can try is to turn of Wifi.

Edit: I was abble to start Bluetooth after I turn off Wifi.
        turn off Wifi and restart, connect bluetooth and enable wifi.

---

### Post by cad2 on 2014-09-26
didn't work either...

---

### Post by karsta62 on 2015-09-23
An older thread but still relevant. 
Bluetooth should work when you disable XHCI in the bios, but then USB3 is reverted to USB2. 

Probably a bit off-topic, but anyway: 
I use a BT dongle and XHCI enabled to have USB3 for faster LAN connection, but then comes another issue: 
The wired network, which is through a USB3 adapter, stops working in a few minutes to a few hours. Sometimes disconnect/connect helps, but not always. 
Using wifi or XHCI disabled (=wired network through USB2 adapter), this does not happen.
Anyone else facing this? 

I'm running kubuntu 14.10.

---

### Post by howefield on 2015-09-23
Please start a fresh thread rather than revive an old one.

---

