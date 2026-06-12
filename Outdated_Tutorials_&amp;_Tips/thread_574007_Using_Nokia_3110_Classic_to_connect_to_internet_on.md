---
title: "Using Nokia 3110 Classic to connect to internet on Smart network in Philippines."
date: 2007-10-12
forum: Outdated Tutorials &amp; Tips
---

### Post by prototypex3 on 2007-10-12
Process
Step 1. Check all the setting of your phone. All settings must already be set-up prior to connection to your computer. Check the following settings:

1. Menu>Web>Settings>Configuration Settings
Configuration - Smart
Account - Smart
2. Menu>Settings>Configuration Settings
Default configuration settings - Smart
Preferred access point - SmartInternet
	3. Menu>Settings>Connectivity>Packet Data>Packet data settings>Edit active access point
		Alias for access point – edit Access point 1 to SmartInternet
		Packet data access point – edit to internet

Item 3 is not set when you download the settings nor set by Smart customer service agents. I just edited it by myself.

Step 2. Connect the phone using your mini-usb cable. Your phone will prompt you for mode. Choose Nokia Mode.

Check your phone if it can be detected using System Log. You can find it under System>Administration>System Log

It will show something like this:

localhost kernel: [ 1359.371931] usb 2-6: new full speed USB device using ohci_hcd and address 2

localhost kernel: [ 1359.585977] usb 2-6: configuration #1 chosen from 1 choice

localhost kernel: [ 1361.509319] cdc_acm 2-6:1.1: ttyACM0: USB ACM device

localhost kernel: [ 1361.514963] usbcore: registered new interface driver cdc_acm

localhost kernel: [ 1361.515060] drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters

localhost kernel: [ 1361.559314] usbcore: registered new interface driver cdc_ether

localhost kernel: [ 1361.713961] usbcore: registered new interface driver rndis_host

If your computer cannot recognize your phone. You may have to download the latest kernel. 

Step 3. You may have to download ppp which handles modems and dialing. Assuming that you don't have any means of downloading direct to your computer using synaptic or add/remove program, you can download it in [http://packages.ubuntu.com](http://packages.ubuntu.com) and search the package gnome-ppp and download it.
Install it under the terminal under Applications>Accessories>Terminal and type the following command

sudo dpkg -i /”package location”/gnome-ppp.deb

It will prompt you to use your password.
Step 4. You can now configure Ubuntu to connect to the internet. In the terminal, type

sudo gedit /etc/ppp/peers/smart

Edit and enter the following:

debug

noauth

connect "/usr/sbin/chat -v -f /etc/chatscripts/smart"

usepeerdns

/dev/ttyACM0 115200

defaultroute

crtscts

lcp-echo-failure 0

Save the file. After this type:

sudo gedit /etc/chatscripts/smart

Edit and enter the following:

TIMEOUT 35
ECHO    ON
ABORT   '\nBUSY\r'
ABORT   '\nERROR\r'
ABORT   '\nNO ANSWER\r'
ABORT   '\nNO CARRIER\r'
ABORT   '\nNO DIALTONE\r'
ABORT   '\nRINGING\r\n\r\nRINGING\r'
''      \rAT
OK      'AT+CGDCONT=1,"IP","internet"'
OK      ATD*99#
CONNECT ""

Save the file.

Step 5. Now you can connect to the internet using this command:

	sudo pon smart

To end internet session. You can type

	sudo pof smart

Enjoy and I hope this will help. By the way, Smart can support 117 kbps in its GPRS/EDGE network.

---

