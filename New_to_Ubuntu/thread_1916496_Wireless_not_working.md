---
title: "Wireless not working"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by bertybert on 2012-01-28
My wireless internet is not working at all. I have a very simple wireless router, without any ethernet ports-just wireless. The internet icon in the top bar says no wireless devices were found. A possible problem might be my /etc/network/interfaces file.

---

### Post by anewguy on 2012-01-28
Let's start with more information:

Do the following, 1 line at a time in a terminal window:

echo "***  lspci  ***" > ~/dwetest.txt
lspci >> ~/dwetest.txt 
echo "***  lsusb  ***" >> ~/dwetest.txt
lsusb >> ~/dwetest.txt
echo "***  lshw  ***" >> ~/dwetest.txt
lshw -C network >> ~/dwetest.txt
echo "***  ifconfig  ***" >> ~/dwetest.txt
ifconfig >> ~/dwetest.txt
echo "***  iwconfig  ***" >> ~/dwetest.txt
iwconfig >> ~/dwetest.txt
echo "***  lsmod  ***" >> ~/dwetest.txt
lsmod >> ~/dwetest.txt
echo "*** network interfaces  ***" >> ~/dwetest.txt
cat /etc/network/interfaces >> ~/dwetest.txt

Now use a USB stick or some other media and copy the dwetest.txt file from your home folder to the media.

Take the media to the PC you are using to post here and reply back, attaching that file to the post.

Dave ;)

---

### Post by bertybert on 2012-01-28
I guess I should mention I'm running ubuntu 10. Does that change anything?

---

### Post by bertybert on 2012-01-28
also, heres the file.

---

### Post by SuaSwe on 2012-01-28
I could be blind but I'm not seeing a wireless device in there. Do you know what kind of wireless card/dongle you have, built-in or USB? Have you taken a look in Additional Drivers to see if one is available to install?

---

### Post by electrojustin on 2012-01-28
Yes, Ubuntu 10.04 or 10.10 for that matter does change things a bit. There is a possibility that the kernel you are running doesn't have support for your network card. I had a similar problem when downgrading to 10.04 for certain 11.10 issues I won't go into. Perhaps try upgrading to a newer version if there's no reason in particular that you are using 10.

---

### Post by bertybert on 2012-01-28
the reason i didnt install 11 is because when i did the 64-bit version (i have an intel i7 cpu) it totally crashed and gave me a shell, and when i did the 32-bit version it said my install cd couldnt be mounted

---

### Post by bertybert on 2012-01-28
also, heres my wi-fi info, copied from the system information app:
  Software Versions:
  CoreWLAN:	2.1.1 (211.3)
  CoreWLANKit:	1.0.1 (101.1)
  Menu Extra:	7.0.1 (701.2)
  configd plug-in:	7.1.1 (711.1)
  System Profiler:	7.0 (700.3)
  IO80211 Family:	4.1.1 (411.1)
  WiFi Diagnostics:	1.0.1 (101.1)
  AirPort Utility:	5.5.3 (553.20)
  Interfaces:
en1:
  Card Type:	AirPort Extreme  (0x14E4, 0xD6)
  Firmware Version:	Broadcom BCM43xx 1.0 (5.100.98.75.18 )
  MAC Address:	b8:8d:12:35:76:2a
  Locale:	FCC
  Country Code:	US
  Supported PHY Modes:	802.11 a/b/g/n
  Supported Channels:	1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165
  Wake On Wireless:	Supported
  AirDrop:	Supported
  Status:	Connected
  Current Network Information:
7HMN2:
  PHY Mode:	802.11g
  BSSID:	00:26:62:44:13:90
  Channel:	11
  Country Code:	US
  Network Type:	Infrastructure
  Security:	WEP
  Signal / Noise:	-53 dBm / -71 dBm
  Transmit Rate:	54

---

### Post by anewguy on 2012-01-28
Your wireless should be:

03:00.0 Network controller: Broadcom Corporation Device 4331 (rev 02)

That's also going to be the unclaimed network that shows in the list.

I would try first:

- hard wire a connection between the PC and the router

- open a terminal window and type:

sudo apt-get update <press enter>

sudo apt-get upgrade <press enter>

- close the terminal window

- In 10.xx, I believe you would next go to System, then Administration, then Restricted Drivers (I've been away from 10.xx for a long time so just trying to remember).  This should search the net for any available drivers.  If it finds something, it should come up with a driver (or perhaps more than 1).  

- disconnect the hard wire to the router

- check your wireless again.


In the mean time, it also wouldn't hurt to do a Google/Yahoo!/Bing/whoever search using:

ubuntu 10. bcm4331

as the search string and see what turns up.  That would be my next step anyway.

Dave ;)

---

### Post by westie457 on 2012-01-28
[http://ubuntuforums.org/showpost.php?p=11630052&postcount=5](http://ubuntuforums.org/showpost.php?p=11630052&postcount=5)

Hello, if the procedure in the above link does not work for you  then try navigating to pool > restricted > b and install the bcmwl package. Then while the Software Centre window is open find the b43-fwcutter package and remove it and reboot.

Either of these should get the wireless working, if not there is another option to try. However we shall look into that if both of the above fails to work.

Hope this helps.

---

### Post by Miljet on 2012-01-28
> I have a very simple wireless router, without any ethernet ports-just wireless.
This presents an interesting dilemma, you need to connect to the internet to download and install drivers, but your wireless doesn't work so you can't connect.

Is your modem and router separate units? If so, can you temporarily bypass the router and plug directly into the modem?

---

