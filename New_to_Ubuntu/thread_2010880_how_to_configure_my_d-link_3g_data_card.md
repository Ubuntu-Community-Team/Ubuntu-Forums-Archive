---
title: "how to configure my d-link 3g data card"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by shafeeqahd on 2012-06-26
Hi friends,

I am new to ubuntu 12.04 and linux. I'm having difficulty configuring my d-link 3g data card in the new ubuntu 12.04 os. When I plug my 3g data card in usb port, the device only blinks and there is nothing happening on the screen so that I can install the driver for the data card.

Please help me proceed further so that I can have a great ubuntu experience.

Looking forward for all your reply.

With Regards,
Shafeeq

---

### Post by Cheesemill on 2012-06-26
You may not have to install a driver, it might already be included with Ubuntu.

You might just have to activate the card by clicking on the network icon in the top right corner of the screen.

---

### Post by audiomick on 2012-06-26
Cheesemill is right: you should not have to install a driver. 

Those things are very often a Huawei device. You can check that by doing
```
lsusb
```

with it plugged in. You should get something like this

```
mick@ubuntu-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c317 Logitech, Inc. Wave Corded Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c046 Logitech, Inc. RX1000 Laser Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The second last entry is my Deutsche Telekom 3G stick.

Does the device show up as a drive in your file manager? There is usually some storage space on those things that also shows up when you plug them in.

You could also check to make sure a package called "usb-modeswitch" is installed. I believe it is installed by default these days on Ubuntu. Just search for it in the software centre and see if it is on there. It probably is, but you never know.

I should probably mention that when I plug my 3G stick in, the system asks me for the password to connect as soon as it has found the stick. I honestly can't remember if I had to manually point to the stick the first time or not, and I don't have an install any more where it hasn't been plugged in already, so I can't check.

---

### Post by shafeeqahd on 2012-06-26
Thank you for your reply.

I tried with the code  
> lsusbI was able to find the my dlink 3g link shown up below

> cheeka@cheeka-ProBook:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 138a:003c Validity Sensors, Inc. VFS471 Fingerprint Reader
Bus 002 Device 003: ID 04f2:b230 Chicony Electronics Co., Ltd Integrated HP HD Webcam
Bus 002 Device 005: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 006: ID 2001:a80b D-Link Corp. I also made sure that 'usb-modeswitch' is installed. But after plugging my 3g dongle I am not getting any pop up so that I can enter my password.

Please help!!!

---

### Post by audiomick on 2012-06-26
Ok, maybe you need to go to the network manager icon and manually set up a new mobile broad band connection. Wait a few minutes. I have to re-boot into another install to see how that works in Unity.

---

### Post by audiomick on 2012-06-26
Ok,it is all coming back to me. ;)

Note: I checked this out on an 11.10 install. It is Unity, but I haven't seen 12.04 yet. I assume it is the same.

There are 4 screen shots attached. 
The first one shows the network applet with no connection. Looks like a triangular segment of a circle.

The second one shows the network applet with a wired connection. Looks like two arrows pointing in opposite directions.

If you left click on that icon, you get the menu seen in the third screenshot. Mine is in German, but the principle is the same. The menu entry you are looking for is the "Verbindungen verarbeiten" one. It is a reasonable assumption that it is the bottom one in the English version too. "Verbindungen verarbeiten" means "Change connections". It might be called something like "connection settings" or "add connection". You'll have to use your common sense there.

When you click on the appropriate entry, you get the window that is shown in the fourth screenshot. Choose the tab called "mobile broadband", and choose "add". That is the "hinzufügen" button that the mouse is pointing to in the screenshot. 

The first page after the intro asks you for your country, then you are asked for the provider's name, then there is a question about the modality of payment. I think you can just go ahead with the default there if you don't have any specific info. I did, at any rate, with my Deutsche Telekom Dongle, and I know of a couple of blokes who used the default settings for an Australian provider, and a couple who used the default settings for U.S. American providers. If in doubt, use the default.

After you have done all this, you should get a pop-up when you plug the thing in asking for the password, and it should then connect. Mine did.

---

### Post by jijunarayan on 2012-11-27
> **shafeeqahd said:**
> Hi friends,

I am new to ubuntu 12.04 and linux. I'm having difficulty configuring my d-link 3g data card in the new ubuntu 12.04 os. When I plug my 3g data card in usb port, the device only blinks and there is nothing happening on the screen so that I can install the driver for the data card.

Please help me proceed further so that I can have a great ubuntu experience.

Looking forward for all your reply.

With Regards,
Shafeeq
goto and download

[http://www.mmnt.net/db/0/0/support.dlink.co.in/firmware/DWM-156](http://www.mmnt.net/db/0/0/support.dlink.co.in/firmware/DWM-156)

1.	Uninstall The previous  D-Link connection Manger.
 
2. Plug the dongle into USB port of the computer.
3. Cancel The AutoRun.
 
4. Double click on the New Firmware EXE and wait until prompt came as “Press any Key to Continue..” 
 

 
5. Then  remove the dongle and connect it again . Install the connection manger from the dongle.
 

6. Open the connection Manger and verify the you have Software version 6.0.1IN.
 
 




Pls and update d-link DWM156 firmware, after that you can see driver files in that. please install i386.deb or amd64.deb(driver files in d-link modem).then unplug d-link modem. After that plug d-link modem
then type in terminal
[COLOR="Red"]$ sudo su
enter password
$ modprobe option[/COLOR]

then in nework icon you can see new GSM/GPRS connection click in that and edit apn and all

---

### Post by mailatabhishekd90 on 2013-03-06
hello...i jst cmplt th creation of connection through the mobile broadband connection manager, also get the password .....nw i can't see th "connet" button....how i connect to the internet.....hlp me pllllzzzz

---

### Post by milankantony on 2014-02-11
[http://wp.me/pHXl3-mt](http://wp.me/pHXl3-mt)

[COLOR=#666666][FONT=Lucida Grande]First install 3g_modem_connect_D300_i386.deb which is inside usb adapter to pc.Just mount usb adapter as a CD drive or copy using Windows 7 OS[/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande]meelogs@meelogs-desktop ~ $ lsusb
Bus 001 Device 003: ID [COLOR=#FF0000][FONT=inherit]2001:a706[/FONT][/COLOR] D-Link Corp.        [COLOR=#0000FF][FONT=inherit]#notice the product ID [/FONT][/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
meelogs@meelogs-desktop ~ $ sudo 3g_
3g_connect.sh 3g_modem_switch
meelogs@meelogs-desktop ~ $ sudo 3g_modem_switch -v2001 pa706
No default vendor/product ID given. Aborting.         [COLOR=#0000FF][FONT=inherit]#if this fails as it happened here type next line(tab completion)[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande]meelogs@meelogs-desktop ~ $ sudo 3g_modem_switch -c /etc/3g_modem_connection/switch_2001_7d01.conf[/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande]Looking for target devices …
No devices in target mode or class found
Looking for default devices …
found matching product ID
adding device
Found device in default mode, class or configuration (1)
Accessing device 003 on bus 001 …
Getting the current device configuration …
OK, got current device configuration (1)
Using first interface: 0×00
Using endpoints 0×01 (out) and 0×81 (in)
Inquiring device details; driver will be detached …
Looking for active driver …
OK, driver found (“usb-storage”)
OK, driver “usb-storage” detached[/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande]SCSI inquiry data (for identification)
————————-
Vendor String: HSPA USB
Model String: SCSI CD-ROM
Revision String: 6225
————————-[/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande]USB description data (for identification)
————————-
Manufacturer: D-Link,Inc
Product: D-Link DWM-156
Serial No.: 536591501550760
————————-
Setting up communication with interface 0
Using endpoint 0×01 for message sending …
Trying to send message 1 to endpoint 0×01 …
OK, message successfully sent
Resetting response endpoint 0×81
Resetting message endpoint 0×01
-> Run lsusb to note any changes. Bye.[/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande]meelogs@meelogs-desktop ~ $ lsusb
Bus 001 Device 004: [COLOR=#FF0000][FONT=inherit]ID 2001:7d01[/FONT][/COLOR] D-Link Corp.           [COLOR=#0000FF][FONT=inherit] #on successful mode switcting ie from normal data card to 3G Modem[/FONT][/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
meelogs@meelogs-desktop ~ $ ifconfig
eth0 Link encap:Ethernet HWaddr 00:e0:4c:36:25:f9
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)[/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande]lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:31 errors:0 dropped:0 overruns:0 frame:0
TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:3244 (3.2 KB) TX bytes:3244 (3.2 KB)[/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande]ppp0 Link encap:Point-to-Point Protocol
inet addr:223.187.3.58 P-t-P:10.64.64.64 Mask:255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1500 Metric:1
RX packets:90 errors:0 dropped:0 overruns:0 frame:0
TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:3
RX bytes:774 (774.0 B) TX bytes:2200 (2.2 KB)[/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande]meelogs@meelogs-desktop ~ $ ping google.com
PING google.com (74.125.236.163) 56(84) bytes of data.
64 bytes from maa03s16-in-f3.1e100.net (74.125.236.163): icmp_req=1 ttl=55 time=281 ms
64 bytes from maa03s16-in-f3.1e100.net (74.125.236.163): icmp_req=2 ttl=55 time=378 ms
^C64 bytes from maa03s16-in-f3.1e100.net (74.125.236.163): icmp_req=3 ttl=55 time=240 ms[/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande]— google.com ping statistics —
3 packets transmitted, 3 received, 0% packet loss, time 6982ms
rtt min/avg/max/mdev = 240.521/299.948/378.119/57.719 ms
meelogs@meelogs-desktop ~ $[/FONT][/COLOR]

[COLOR=#666666][FONT=Lucida Grande]next time simply plug in and wait for a few seconds untill green led blinks for a few second.[/FONT][/COLOR]

---

