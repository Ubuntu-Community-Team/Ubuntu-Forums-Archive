---
title: "wireless device not ready"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by vivekpandey1991 on 2012-03-20
i have ubuntu 10.10 running on my machine... but the problem is it is not detecting any wifi connection. my friend having same company's laptop with same config is able to  connect it properly .. but when i enable wireless by right click on network manager applet , i could later only see device not ready when i left click the applet ... it just does not detect any wifi connection. pls help

---

### Post by gordintoronto on 2012-03-20
You right-click on Network Manager and then what?

On my system, I select "Edit Connections." I select the Wireless tab. I click on "Add." I enter the SSID of my router. (A simple name that is all lower case.) I click on "Available to all users" and "Connect automatically." I click on Wireless Security, select Security as "WPA and WPA2 Personal", and enter my passphrase. Apply, Close.

---

### Post by card_ace on 2012-03-20
agreed.  on my laptop my wireless doesn't always play nice and I have to manually put in the network information.  Often times it doesn't pick up networks even though I'm surrounded by them in my dorm.  Try to manually put in the network name and security info in the network connections as described above.

---

### Post by wildmanne39 on 2012-03-20
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Bucky Ball on 2012-03-20
Plugged in an ethernet cable, gotten updates and checked 'Additional Drivers'?

---

