---
title: "Bluetooth isn't working properly!"
date: 2016-05-30
forum: New to Ubuntu
---

### Post by salehbozeed on 2016-05-30
My bluetooth headset is connected fine but the sound keeps stuttering, and when i open an app the sound completely disappears! it works quite well with windows 10.

I'm using Ubuntu 16.04 LTS
any thoughts?

---

### Post by jeremy31 on 2016-05-30
Are you using wifi while listening on bluetooth?  If so please post result of ```
lspci -nnk | grep -iA2 net
```

Also run ```
bluetoothctl
``` and post the results from opening an app when the sound quits

Welcome to the forum

---

### Post by salehbozeed on 2016-05-30
Yes, I'm using wifi while listening on bluetooth...here's the results of ```
lspci -nnk | grep -iA2 net
```

03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: XAVi Technologies Corp. BCM43142 802.11b/g/n [1b9a:3002]
	Kernel driver in use: wl
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Toshiba America Info Systems RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1179:f920]
	Kernel driver in use: r8169
	Kernel modules: r8169

-And of ```
bluetoothctl
```

[NEW] Controller 64:5A:04:D1:A9:0F ChromeLinux_D81C [default]
[NEW] Device 00:1D:86:20:02:AC BH-501
[CHG] Device 00:1D:86:20:02:AC Connected: no
[CHG] Device 00:1D:86:20:02:AC Connected: yes

And after the sound disappeared it showed

[CHG] Device 00:1D:86:20:02:AC Connected: no

---

### Post by jeremy31 on 2016-05-31
See if ```
systemctl status bluetooth
```
Shows anything after the audio is disconnected

---

### Post by salehbozeed on 2016-05-31
```
systemctl status bluetooth
```

&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset
   Active: active (running) since Tue 2016-05-31 10:24:25 EET; 13h ago
     Docs: man:bluetoothd(8)
 Main PID: 815 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;815 /usr/lib/bluetooth/bluetoothd


May 31 10:24:53 Satellite-C55-B bluetoothd[815]: Endpoint registered: sender=:1.
May 31 10:24:53 Satellite-C55-B bluetoothd[815]: RFCOMM server failed for Headse
May 31 10:25:07 Satellite-C55-B bluetoothd[815]: Endpoint unregistered: sender=:
May 31 10:25:07 Satellite-C55-B bluetoothd[815]: Endpoint unregistered: sender=:
May 31 23:38:14 Satellite-C55-B bluetoothd[815]: /org/bluez/hci0/dev_00_1D_86_20
May 31 23:38:25 Satellite-C55-B bluetoothd[815]: Suspend: Connection timed out (
May 31 23:38:27 Satellite-C55-B bluetoothd[815]: Abort: Connection timed out (11
May 31 23:38:45 Satellite-C55-B bluetoothd[815]: /org/bluez/hci0/dev_00_1D_86_20
May 31 23:40:42 Satellite-C55-B bluetoothd[815]: /org/bluez/hci0/dev_00_1D_86_20
May 31 23:43:38 Satellite-C55-B bluetoothd[815]: /org/bluez/hci0/dev_00_1D_86_20

---

### Post by salehbozeed on 2016-05-31
> **jeremy31 said:**
> See if ```
systemctl status bluetooth
```
Shows anything after the audio is disconnected

It's like it disconnects and connects!

---

### Post by jeremy31 on 2016-05-31
And you have no issues with wifi?  I have viewed a lot of issues with that chipset lately on the 4.4 kernel

You may want to delete the pairing with the headset and then pair it again

---

### Post by salehbozeed on 2016-05-31
> **jeremy31 said:**
> And you have no issues with wifi?  I have viewed a lot of issues with that chipset lately on the 4.4 kernel

You may want to delete the pairing with the headset and then pair it again


Actually i do! occasionally the wifi[COLOR=#111111][FONT=Ubuntu] disconnects and i have to turn it off then back on again to reconnect!

i tried to delete the pairing but it didn't solve the problem! should i upgrade the kernel?[/FONT][/COLOR]

---

### Post by jeremy31 on 2016-06-01
Can you try a 14.04 ISO?  See if you can get the original and not 14.04.1 or newer to see if everything is stable then

---

### Post by salehbozeed on 2016-06-01
> **jeremy31 said:**
> Can you try a 14.04 ISO?  See if you can get the original and not 14.04.1 or newer to see if everything is stable then

alright!

btw i'm facing another problem! the screen keeps flickering, but i noticed that it occurs only while browsing on Chrome or Opera!

---

### Post by salehbozeed on 2016-06-02
> **jeremy31 said:**
> Can you try a 14.04 ISO?  See if you can get the original and not 14.04.1 or newer to see if everything is stable then

I installed 14.04 ISO and i couldn't even enable bluetooth :confused:

I tried different solution but it remained disabled! now i've returned to 16.04

---

### Post by jeremy31 on 2016-06-02
Anything in ```
dmesg | egrep -i 'blue|firm'
```

I guess it could be a newer bluetooth device that doesn't have the firmware available to function properly

---

### Post by salehbozeed on 2016-06-02
> **jeremy31 said:**
> Anything in ```
dmesg | egrep -i 'blue|firm'
```

I guess it could be a newer bluetooth device that doesn't have the firmware available to function properly


[   10.192833] toshiba_bluetooth: Toshiba ACPI Bluetooth device driver
[   12.606261] Bluetooth: Core ver 2.21
[   12.606287] Bluetooth: HCI device and connection manager initialized
[   12.606293] Bluetooth: HCI socket layer initialized
[   12.606297] Bluetooth: L2CAP socket layer initialized
[   12.606306] Bluetooth: SCO socket layer initialized
[   18.261425] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.261432] Bluetooth: BNEP filters: protocol multicast
[   18.261441] Bluetooth: BNEP socket layer initialized
[ 1446.370849] [Firmware Bug]: battery: (dis)charge rate invalid.
[40575.564912] Bluetooth: hci0: BCM: chip id 70
[40575.581030] Bluetooth: hci0: BCM43142A
[40575.581037] Bluetooth: hci0: BCM (001.001.011) build 0000
[40575.613054] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[40575.613075] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[40575.691334] Bluetooth: RFCOMM TTY layer initialized
[40575.691345] Bluetooth: RFCOMM socket layer initialized
[40575.691354] Bluetooth: RFCOMM ver 1.11
[40590.353582] Bluetooth: hci0 command 0x1003 tx timeout

---

### Post by jeremy31 on 2016-06-02
Post results for ```
lsusb
```

---

### Post by salehbozeed on 2016-06-02
> **jeremy31 said:**
> Post results for ```
lsusb
```

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b446 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0930:0225 Toshiba Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by jeremy31 on 2016-06-02
There is a generic guide to finding the firmware [here](http://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working-on-ubuntu/632348#632348)
You will want to search the bcbtums.inf for 0225 until you find a RAMUSB0225.copy list with a .hex file listed below.  Then use Jesse Sung's hex2hcd to convert the hex file to BCM.hcd and finally copy it into /lib/firmware/brcm  then reboot and see if it makes an improvement

---

### Post by salehbozeed on 2016-06-02
> **jeremy31 said:**
> There is a generic guide to finding the firmware [here]("http://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working-on-ubuntu/632348#632348")
You will want to search the bcbtums.inf for 0225 until you find a RAMUSB0225.copy list with a .hex file listed below.  Then use Jesse Sung's hex2hcd to convert the hex file to BCM.hcd and finally copy it into /lib/firmware/brcm  then reboot and see if it makes an improvement

I'll check it out! do you have any idea regarding the screen flickering?

---

### Post by salehbozeed on 2016-06-04
> **jeremy31 said:**
> There is a generic guide to finding the firmware [here]("http://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working-on-ubuntu/632348#632348")
You will want to search the bcbtums.inf for 0225 until you find a RAMUSB0225.copy list with a .hex file listed below.  Then use Jesse Sung's hex2hcd to convert the hex file to BCM.hcd and finally copy it into /lib/firmware/brcm  then reboot and see if it makes an improvement

Unfortunately that didn't solve the problem!

I noticed that when i disable wifi, bluetooth works flawlessly! so it could be an interference between them.

---

### Post by jeremy31 on 2016-06-04
If can change the router settings, see if setting to a different channel helps

---

### Post by Geoffrey_Arndt on 2016-06-04
As a last resort, here is _another approach_ so that you can use your main hardware by attaching linux friendly adapters:

Available via Amazon or similar vendors.   I have several Panda products, and all have worked without need to compile drivers.

Then, next time you buy a new system (laptop or desktop), just get one with Linux preinstalled so these components are tested ahead of deployment to the public.
[URL="http://www.pandawireless.com/Products%20|%20Panda%20Wireless.html"]
http://www.pandawireless.com/Products%20|%20Panda%20Wireless.html[/URL]

---

### Post by beaucoder2 on 2016-06-04
Hi all, FWIW - 14.04.4  Bluetooth setup on Gateway laptop.

In UBSoftware Center install all Bluetooth but NOT Blueman.

Plug in usb bluetooth adapter. In Bluetooth go to devices and REMOVE the audio device. Then use the "+" to add it again and immediately hit the find/reset button on the audio receiver (Amazon Audio in this case). Ubuntu 14.04.4 now found the correct audio device AND it now shows up in the Sound Settings below Speakers, Built-in Audio. Select the audio receiver and run the sound test. Be sure the speaker green plug is all the way in the audio receiver (or only the left channel will play.) Pick a tune from Youtube and play it. Enjoy!

The trick is to remove the newly found Amazon Audio (or what you have) that got discovered on boot up. While it is discovered it is NOT properly installed. Remove it from Bluetooth devices popup and then add it in again and immediately hit the find/reset button on the receiver. The receiver should now properly appear in sound settings. It should also remain stable there. Select the Amazon Audio or what you have in the sound settings. Worked like charm for me after hours & hours without any sound out of the Bluetooth speakers just tons of link-up attempt beeps. Sheesh!

HTH.  Ken Wagner

---

### Post by jeremy31 on 2016-06-04
> **beaucoder2 said:**
> Hi all, FWIW - 14.04.4  Bluetooth setup on Gateway laptop.

In UBSoftware Center install all Bluetooth but NOT Blueman.

Plug in usb bluetooth adapter. In Bluetooth go to devices and REMOVE the audio device. Then use the "+" to add it again and immediately hit the find/reset button on the audio receiver (Amazon Audio in this case). Ubuntu 14.04.4 now found the correct audio device AND it now shows up in the Sound Settings below Speakers, Built-in Audio. Select the audio receiver and run the sound test. Be sure the speaker green plug is all the way in the audio receiver (or only the left channel will play.) Pick a tune from Youtube and play it. Enjoy!

The trick is to remove the newly found Amazon Audio (or what you have) that got discovered on boot up. While it is discovered it is NOT properly installed. Remove it from Bluetooth devices popup and then add it in again and immediately hit the find/reset button on the receiver. The receiver should now properly appear in sound settings. It should also remain stable there. Select the Amazon Audio or what you have in the sound settings. Worked like charm for me after hours & hours without any sound out of the Bluetooth speakers just tons of link-up attempt beeps. Sheesh!

HTH.  Ken Wagner

Unfortunately this will not work for this one as the bluetooth device ```
Bus 001 Device 003: ID 0930:0225 Toshiba Corp. 
``` wasn't supported until December 2015.  Ubuntu only patched the 3.19.0-56 and newer kernels for Vivid and 4.2.0-30 for Wily.

I use an Atheros AR5B225 wifi/bluetooth combo card in my Lenovo and haven't had any major issues for the past year when they figured out a timing issue with xhci and the firmware upload

---

### Post by salehbozeed on 2016-06-16
> **jeremy31 said:**
> If can change the router settings, see if setting to a different channel helps

That didn't work either! Thanks for your time Jeremy.

---

### Post by jeremy31 on 2016-06-16
I have good luck with the Atheros wifi/bt card in my Lenovo, it is an AR5B225.  I hate to recommend something as there is always a way for something to go wrong as if I put it into my Toshiba P875, no bluetooth is found but I have put other cards in that laptop and not had any luck until I tried an older Atheros card an AR5B195

---

### Post by drm200 on 2016-06-19
This does not work for me.  Ubuntu 14.04 finds the USB device .. but it does not show up in the sound settings so I am unable to get sound out of the device.

---

### Post by jeremy31 on 2016-06-19
drm200
So you can pair with your audio device?  Check ```
pactl list short | grep bluetooth
```

---

