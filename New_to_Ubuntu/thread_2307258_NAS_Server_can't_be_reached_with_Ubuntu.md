---
title: "NAS Server can't be reached with Ubuntu"
date: 2015-12-23
forum: New to Ubuntu
---

### Post by Sky_Dog on 2015-12-23
Hi,

I have a NAS QNAP Server.  

I can find the server with QNAP Finder in windows, but my Ubuntu is not able to find it in the network.

Where can I start searching for the problem? I have no idea why Ubuntu doesn't find the NAS Server.

Thanks in advance and ... merry Christmas!
SkyDog

---

### Post by gordintoronto on 2015-12-23
People need more information than "my Ubuntu is not able to find it in the network." Tell us what you did, and what results you observed.

For example: "I ran Nautilus, I clicked on "browse network," but the NAS did not appear.

I have found that my NAS goes to sleep, and then it doesn't appear. It's not a wonderful NAS.

---

### Post by sandyd on 2015-12-23
> **Sky_Dog said:**
> Hi,

I have a NAS QNAP Server.  

I can find the server with QNAP Finder in windows, but my Ubuntu is not able to find it in the network.

Where can I start searching for the problem? I have no idea why Ubuntu doesn't find the NAS Server.

Thanks in advance and ... merry Christmas!
SkyDog
Hi, Qfinder is available for Linux. See [https://www.qnap.com/i/useng/utility/](https://www.qnap.com/i/useng/utility/), however its not useful since qSync is missing.

Instead, setup[ NFS on the NAS]("http://docs.qnap.com/nas/4.0/en/index.html?win_mac_nfs.htm").
You can then mount it from Linux using the commands at the bottom of the page

---

### Post by Sky_Dog on 2016-01-21
Thanks a lot, you are right!

---

