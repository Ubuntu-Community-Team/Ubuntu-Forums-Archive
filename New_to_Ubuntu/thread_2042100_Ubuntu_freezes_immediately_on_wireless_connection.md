---
title: "Ubuntu freezes immediately on wireless connection"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by subtlebreath on 2012-08-14
I'm running an Acer Aspire One AO722-0022, and the latest version of Ubuntu. So long as I have wireless disabled everything runs fine, however as soon as I connect to a wireless network Ubuntu completely locks up.

---

### Post by 2F4U on 2012-08-14
You should at least give details about your hardware, since else I guess that you won't get much response.

---

### Post by subtlebreath on 2012-08-14
Hardware details:
[http://us.acer.com/ac/en/US/content/model/LU.SFT02.176](http://us.acer.com/ac/en/US/content/model/LU.SFT02.176)

---

### Post by NikTh on 2012-08-14
Hi , 
please open a terminal (ctrl+alt+t)  to provide more useful info ... copy-paste below commands one at time and post here the results 
```
cat /etc/lsb-release && uname -r 
lspci -nnk | grep -iA2 net 
rfkill list all 
sudo lshw -C network
dmesg | egrep 'wlan|eth|Network|ath'
cat .xession-errors 
cat /var/log/Xorg.0.log | egrep 'WW|EE'
```_Put the results inside [CODE] tags so can be readable. Highlighting the text and click the [SIZE=3]**#**[/SIZE] symbol on top of message pane._

Thanks

---

### Post by centaurusa on 2012-08-14
> **subtlebreath said:**
> I'm running an Acer Aspire One AO722-0022, and the latest version of Ubuntu. So long as I have wireless disabled everything runs fine, however as soon as I connect to a wireless network Ubuntu completely locks up.

The solution may be to disable the Ethernet controller an rely solely on the wireless connection.  See:

[http://linuxnorth.wordpress.com/2011/10/23/wireless-less/](http://linuxnorth.wordpress.com/2011/10/23/wireless-less/)

---

### Post by cortman on 2012-08-14
I have an Aspire One 722 as well; the solution is to set network boot first in the BIOS boot order. Did that and it works perfectly every time.

---

### Post by subtlebreath on 2012-08-14
> **cortman said:**
> I have an Aspire One 722 as well; the solution is to set network boot first in the BIOS boot order. Did that and it works perfectly every time.

Awesome. That fixed it. Thank you so much - you have no idea how much time I spent trying to fix this.

And, thank you everyone else for helping as well.

---

### Post by cortman on 2012-08-14
> **subtlebreath said:**
> Awesome. That fixed it. Thank you so much - you have no idea how much time I spent trying to fix this.

And, thank you everyone else for helping as well.

I spent hours trying to fix mine too. :) Glad to help.

Mark the thread [SOLVED], using the thread tools in the upper right, if you would.
Good luck!

---

