---
title: "Ubuntu doesnt recognise private part Fon point"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by oggFrogg on 2008-10-22
I have an IBM thinkpad laptop 1,4G 40G HDD 528Mb and installed ubuntu 6.1. Installing was no problem, all works fine. By starting firefox ubuntu found my Fon wireless network. The laptop has an internal wireless card. Only the public part of my Fon point shows up. Via this link I can surf to my own website, so everything works fine. But I want to connect with the private part of my FON point. Which steps do I have to make?

---

### Post by AFarris01 on 2008-10-22
Is the private part of your network broadcasting an SSID?  if not, then you will have to manually connect to it by left-clicking on the network manager icon in your tray, and going to "Connect to Other Wireless Network" and enter all the appropriate information there.  that should connect you if it's a hidden SSID.

other than that, i'm not sure what else to try, unless the network is encrypted or something.  If this doesn't work for you, post back and hopefully somebody else can help, or I'll learn enough about it to help you better :)

Hope this helps!

Andrew

---

### Post by oggFrogg on 2008-10-23
Andrew Tnks,

Looking at the wireless Windhose network connection that works on my other machines, I found the following for the working connection with my FON point:

SSID: ABCDEFG [COLOR="Red"](The name I gave it, better not to mention here)[/COLOR]
[COLOR="Black"]Network verification: WPA-PSK
Code: TKIP
Network key: ......... [COLOR="Red"](Don't mention it here)
[COLOR="Black"]Key index = 1 , the key is automaticaly allotated

Adresstype: awarded by DHCP
IP adres: XXX.XXX.10.101
Subnet mask: 255.255.255.0
Standard gateway: xxx.xxx.10.1
DHCP server: XXX.XXX.10.1
DNS server: XXX.XXX.10.1

The XXX.XXX stand for the same number not mentioned here. [/COLOR][/COLOR][/COLOR]
no IEEE 802.1X-verification
the wireless connection in this windhose laptop shows up as: (ZD 1211B)IEEE 802.11 b+g USB adapter #7 
My IBM laptop with Ubuntu has an internal wireless card. What is the Linux command to show which card this is?

Strange also is that in my windhose laptop my Fon point is shown as two networks one secured (private) and one unsecured (public).

Ubuntu shows only one network: the public part of my laptop.

does this help to find the answer?

Frits

---

### Post by oggFrogg on 2008-10-26
Solved!

On the dutch forum I was advised to put version 8.04 on my laptop. I did and everything works fine now. The whole FON point is recognised automatically now.

Frits

---

