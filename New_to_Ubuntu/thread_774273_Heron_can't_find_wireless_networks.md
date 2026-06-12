---
title: "Heron can't find wireless networks"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by MockY on 2008-04-29
My laptop scanned wireless networks just fine with Edgy and Feisty. iwlist scan worked flawlessly and so did network manager. However, in Heron it's not working right at all. Iwlist scan does not find anyting and in order to connect to my LAN, I have to manually enter all the information, including the SSID, in order to be able to connect. This presents a problem beacuse I don't always know what network I am going to connect to.

So I wonder if anyone else got issues with wireless after jumping onto Heron, and why this got worse.

---

### Post by superprash2003 on 2008-04-29
have you tried restricted drivers? system->administration->restricted drivers .. enable if any(wireless)

---

### Post by MockY on 2008-04-29
The card works just fine once you know what network that exist in the area. Intel restricted drivers are already enables. And why would it get worse with a newer version of Ubuntu. It just does not make sense.

---

### Post by Iago1989 on 2008-04-29
There are a few good "radar" 3rd party things like "wicd" (what I use, cuz it remembers ASCII passwords)

then there's Wifi Radar, find it in the add/remove search tool under "Internet"

---

### Post by MockY on 2008-04-29
Since WiFi-Radar relies on iwlist scan, it does not pick up anything at all either.

---

### Post by unMourned on 2008-04-29
This solved my wireless woes, 100%.


[url]http://ubuntuforums.org/showpost.php?p=4805938&postcount=1[/url

> **sbrbot said:**
> Ubuntu 8.04 has new b43 driver for Broadcom wireless cards. Ndiswrapper is not needed anymore. b43 driver (module) uses Broadcom card firmware for running wireless card. Problem with Broadcom cards is that Broadcom company copyrighted its wlan firmware and it is not distributed with Ubuntu. Wireless card (b43 module) will not work without this firmware. Here is one way how one can easily install Broadcom firmware:

1) connect your computer to Internet using ethernet connection

2) using Synaptic Package Manager install b43-fwcutter tool

This tool is used for extracting Broadcom firmware that b43 module needs.

At the end of b43-fwcutter installation procedure Configuration of b43-fwcutter will be initiated where you will be asked whether to "Fetch and extract firmware" - answer Yes, of course.

PICTURE#1

After installing b43-fwcutter tool, in background a script will start which will from internet (that's why you need ethernet connection) automatically download Broadcom libraries containing needed firmwares, b43-fwcutter will extract firmwares in /lib/firmwares directory and finally you should only restart you computer.

PICTURE#2

3) you should blacklist ndiswrapper and old bcm43xx drivers if they were not blacklisted already in /etc/modprobe.d/blacklist file.

4) in Network-Manager (icon with two screens in upper right corner) setup needed connection data in order to connect to your Access Point

PICTURE#3 and PICTUR#4

That's it folks!

HTH

---

### Post by MockY on 2008-04-29
Awesome that you solved your issue. However, my Intel card is not Broadcom and would therefore not work.

Again, the card works just fine. It is correctly installed from the get go, but it does not scan for wireless connections. I have to manually enter the network information in order for it to connect (ssid and security). Once that is done, wireless with dhcp works just fine.

If this doesn't work, then I have no other option than go back to Feisty.

---

