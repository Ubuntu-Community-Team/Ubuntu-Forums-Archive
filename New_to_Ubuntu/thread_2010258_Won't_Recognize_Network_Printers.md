---
title: "Won't Recognize Network Printers"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by rmason9 on 2012-06-25
I can't get Ubuntu 12.04 to recognize my network printers.  I read through several threads addressing this issue but none of the solutions worked.  I am connecting wired, not wireless at this point.  Here is what I've done:

[LIST]
[*]Printer is HP PSC 1400.  I downloaded and installed hplip software from the HP website and installed, replacing existing file that came with Ubuntu install. I  also have a Samsung ML-2010 connected to the network via the host computer (desktop).
[*]I dont' know the host names of the printers but have entered the host computer name, host computer IP address, and router IP address in the Host field of the dialog box to no avail.  I can't find the IP addresses of the printers themselves.
[/LIST]
Additionally, although my computer running Ubuntu can access the internet via the network, it does not appear as a computer on the the network on my Host desktop computer running Win7.  Shouldn't it show up?


Any helpful comments will be appreciated...Thanks!!!

---

### Post by cmcanulty on 2012-06-25
Install a linux driver for the printer and install samba

---

### Post by NikTh on 2012-06-25
> **rmason9 said:**
> I can't get Ubuntu 12.04 to recognize my network printers.  I read through several threads addressing this issue but none of the solutions worked.  I am connecting wired, not wireless at this point.  Here is what I've done:

[LIST]
[*]Printer is HP PSC 1400.  I downloaded and installed hplip software from the HP website and installed, replacing existing file that came with Ubuntu install. I  also have a Samsung ML-2010 connected to the network via the host computer (desktop).
[*]I dont' know the host names of the printers but have entered the host computer name, host computer IP address, and router IP address in the Host field of the dialog box to no avail.  I can't find the IP addresses of the printers themselves.
[/LIST]
Additionally, although my computer running Ubuntu can access the internet via the network, it does not appear as a computer on the the network on my Host desktop computer running Win7.  Shouldn't it show up?


Any helpful comments will be appreciated...Thanks!!!

Install smbclient 
```
sudo apt-get install smbclient
```
then 
Make sure that your Windows host system has enabled printer sharing. 
Then from Ubuntu go to printing > add > Network printer > windows printer via samba and click browse to search.

---

### Post by cmcanulty on 2012-06-25
If the printer is not attached to a windows machine does it still need to be shared on windows and need samba? Our lib has a brother MFC cabled to wall via ethernet.

---

### Post by Lyfang on 2012-06-25
I have a similar problem but with a wireless printer.

Wireless printer "Processing - Unable to locate printer." [https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/987212](https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/987212)

---

