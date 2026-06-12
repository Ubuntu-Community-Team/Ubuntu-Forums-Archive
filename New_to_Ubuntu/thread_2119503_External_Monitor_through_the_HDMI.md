---
title: "External Monitor through the HDMI"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by kronomia on 2013-02-24
**Part I - The Problem:**
My Dell laptop is not detecting my Samsung external monitor through the  HDMI cable on Ubuntu 12.04. The same computer with the same monitor is  working perfectly under my Windows 7 operating system. 



  **Part II - The Computer Specifications:**
Please visit the below link for the computer specifications:
[http://pastebin.com/ZdMVsaAQ](http://pastebin.com/ZdMVsaAQ)
[URL="http://pastebin.com/ZdMVsaAQ"]
[/URL]
  **Part III - The Operating System:**
The operating system i am using now is Ubuntu 12.04 - Updated daily from the official main servers. 



  **Part IV - The External Monitor Specifications:**
- Brand: Samsung
- Model Number: S23A950D
- Model Code: LS23A950DSL/XM
- Link: [http://www.samsung.com/my/consumer/pc-peripherals-printer/monitor/led-monitor/LS23A950DS/XY](http://www.samsung.com/my/consumer/pc-peripherals-printer/monitor/led-monitor/LS23A950DS/XY)
[URL="http://www.samsung.com/my/consumer/pc-peripherals-printer/monitor/led-monitor/LS23A950DS/XY"]
[/URL]                      
  Thanks in advance for your help!

---

### Post by Bodsda on 2013-02-24
> **kronomia said:**
> **Part I - The Problem:**
My Dell laptop is not detecting my Samsung external monitor through the  HDMI cable on Ubuntu 12.04. The same computer with the same monitor is  working perfectly under my Windows 7 operating system. 



  **Part II - The Computer Specifications:**
Please visit the below link for the computer specifications:
[http://pastebin.com/ZdMVsaAQ](http://pastebin.com/ZdMVsaAQ)
[URL="http://pastebin.com/ZdMVsaAQ"]
[/URL]
  **Part III - The Operating System:**
The operating system i am using now is Ubuntu 12.04 - Updated daily from the official main servers. 



  **Part IV - The External Monitor Specifications:**
- Brand: Samsung
- Model Number: S23A950D
- Model Code: LS23A950DSL/XM
- Link: [http://www.samsung.com/my/consumer/pc-peripherals-printer/monitor/led-monitor/LS23A950DS/XY](http://www.samsung.com/my/consumer/pc-peripherals-printer/monitor/led-monitor/LS23A950DS/XY)
[URL="http://www.samsung.com/my/consumer/pc-peripherals-printer/monitor/led-monitor/LS23A950DS/XY"]
[/URL]                      
  Thanks in advance for your help!

Hi,

Can you paste the output of the following command please.
```

lspci | grep -i vga

```

This will help us identify which graphics card driver you need and which tools to use to configure the additional monitor.

Thanks,
Bodsda

---

### Post by kronomia on 2013-02-24
[Updated]

The output of ```
lspci | grep -i vga
``` is:

```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)
```

---

