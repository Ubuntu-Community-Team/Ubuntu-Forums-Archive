---
title: "anti virus"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by trav9595 on 2014-04-28
are there any newer screeners for Ubuntu that are good to use for virus or similar...???I use Xubuntu and it has worked the best of all the Linux I have tried. 0 crashes in 2 years.

---

### Post by jbaerboc on 2014-04-28
If you're looking for an anti-virus program ClamAV is a rather popular Linux native program. That being said, unless you plan to move filed to a Windows machine and are concerned about infecting it you don't have to worry much about viruses on Ubuntu. It can still happen but it's extremely rare.

---

### Post by grier-devon on 2014-04-29
Always nice of you to run a scan though before transfering data to a friend as we often don't realize what Window based infections we carry that we are immune too. 

The downside to the clamav is 14.04 is carrying a current version of the software but when it updates to something newer you have to use the ppa which in my experience is broken all to often or at least was for 13.10 as I do regular scans being I transfer a lot of data to Windows users.

---

### Post by sandyd on 2014-04-29
Do note that while clamav exists, it does not detect all viruses, and occasionally has false positivies.

If you suspect a file might have a virus, it may be better to test it at a service like VirusTotal ([link]("https://www.virustotal.com/")) which can scan the file using multiple antivirus vendors.

---

### Post by LastDino on 2014-04-29
There aren't any ''really good'' Anti-virus program for home user in Linux. However, if you are using WIne and transferring window files, try to have those scanned with alternatives like scanning those on some windows machine or try using bootable anti-virus solution. But really, you don't need to go that far unless you're doing what I've mentioned quite extensively.

---

### Post by Old_Grey_Wolf on 2014-04-29
In addition to clamav...There are several but they are not open-source. They are free though.

AVG -  [http://free.avg.com/us-en/download.prd-alf](http://free.avg.com/us-en/download.prd-alf) probably what you would use if you choose one of these. It is only a scanner so it doesn't remove the virus.
Comodo - [http://comodo.com/home/internet-security/antivirus-for-linux.php](http://comodo.com/home/internet-security/antivirus-for-linux.php) for 12.04.
Kaspersky - [http://kaspersky.com/product-updates/linux-file-server-antivirus](http://kaspersky.com/product-updates/linux-file-server-antivirus) for Linux file servers.

---

### Post by jbaerboc on 2014-04-29
> **sandyd said:**
> Do note that while clamav exists, it does not detect all viruses, and occasionally has false positivies.

If you suspect a file might have a virus, it may be better to test it at a service like VirusTotal ([link]("https://www.virustotal.com/")) which can scan the file using multiple antivirus vendors.

Huh that's pretty nifty. Thanks for posting :)

---

