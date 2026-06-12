---
title: "External Drive Not Recognized"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by krissarathi on 2012-08-10
Hi
I have the same problem. my external hard disk not working. usb port is good as the pen drive works fine.
I checked the drive with my TV and it works fine.
here is the output of lsusb
uname -a
tnk@krishnaleela:~$ uname -a
Linux krishnaleela 3.2.0-27-generic-pae #43-Ubuntu SMP Fri Jul 6 15:06:05 UTC 2012 i686 i686 i386 GNU/Linux
tnk@krishnaleela:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 05fe:0011 Chic Technology Corp. Browser Mouse
I am new to Unix and ubuntu. please advice.

Warm Regards
Sarathi
> **Toz said:**
> It might be a hardware problem. 
- Is this a known good drive? 
- Does it work on another computer? 
- Do you have another cable you could try? 
- How is the drive plugged in? Is it going directly to the computer or is it going through some sort of hub?

With the drive plugged in, open a terminal window and type in the following and post back the results:```
uname -a
lsusb
lsmod
```Have you tried unplugging the drive and then plugging it back in? If so, do you get the same error message? This time, after you plug it in, can you run:```
dmesg | grep "usb 1-6.4"
```and post back the results.

---

### Post by wildmanne39 on 2012-08-11
Post moved to it's own thread!

---

