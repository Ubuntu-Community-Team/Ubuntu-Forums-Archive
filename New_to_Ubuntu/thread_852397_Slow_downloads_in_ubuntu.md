---
title: "Slow downloads in ubuntu"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by saratchandra on 2008-07-07
I decided to create one last thread before leaving. Ubuntu is great and has been for the last three years, but I'm really disappointed about how useless this forum has turned into. I'm ******* tired of creating threads asking for help and getting no replies. I hope this problem gets solved at last.

Coming to my problem, downloads in ubuntu are far far slower compared to windows(even in virtualbox). I tested a download from download.com and java.com and the results are horrible compared to windows. I get about 60 KBPS in windows, but only 20-30 in ubuntu. There is no noticeable difference in browsing speed and even the download starts well, but it slows down after some time. I reinstalled ubuntu, but it didn't work.

---

### Post by RequinB4 on 2008-07-07
If no one answers, it's because you have an uncommon problem that no one knows the answer to, not that we aren't willing to help

what is the output of ```
lspci
```

Are you on wired or wireless?  Did your wireless work out of the box?  Are you on a private or a public network?

---

### Post by saratchandra on 2008-07-07
> **RequinB4 said:**
> If no one answers, it's because you have an uncommon problem that no one knows the answer to, not that we aren't willing to help

what is the output of ```
lspci
```

Are you on wired or wireless?  Did your wireless work out of the box?  Are you on a private or a public network?


I'm on a wired connection with a cable modem, but I have to login. Here is the output of lspci

> 00:00.0 Host bridge: nVidia Corporation Unknown device 07c3 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation Unknown device 07d7 (rev a2)
00:03.1 SMBus: nVidia Corporation Unknown device 07d8 (rev a1)
00:03.2 RAM memory: nVidia Corporation Unknown device 07d9 (rev a1)
00:03.3 Co-processor: nVidia Corporation Unknown device 07da (rev a2)
00:03.4 RAM memory: nVidia Corporation Unknown device 07c8 (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:08.0 IDE interface: nVidia Corporation Unknown device 056c (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation Unknown device 056d (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 056e (rev a1)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0e.0 IDE interface: nVidia Corporation Unknown device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)


---

### Post by gandaran on 2008-07-07
it would be help-full if you could post what type of modem/router you use and how the Internet connection is setup

---

### Post by jamesrfla on 2008-07-07
The download servers at download.com really **** bad. If you download something get it from the maker of the product.

---

### Post by saratchandra on 2008-07-07
> **jamesrfla said:**
> The download servers at download.com really **** bad. If you download something get it from the maker of the product.

I tried different websites, but the problem is same:(

---

### Post by saratchandra on 2008-07-07
> **gandaran said:**
> it would be help-full if you could post what type of modem/router you use and how the Internet connection is setup

Thanks for replying, look at my second post for details. I'm connected to a motorola modem through a usb cable.

---

### Post by RequinB4 on 2008-07-07
Some more diagnostic stuff - Try using wget "url" in a terminal instead of firefox.

This may be a new bug, I can't find any problems with boxes with your ethernet controller besides [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189269](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189269) which is completely irrelevent

---

### Post by jamesrfla on 2008-07-07
Try rebooting the modem and router for two min. After two min plug in the modem and then after a min plug the router back in.

---

### Post by saratchandra on 2008-07-07
> **RequinB4 said:**
> Some more diagnostic stuff - Try using wget "url" in a terminal instead of firefox.

This may be a new bug, I can't find any problems with boxes with your ethernet controller besides [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189269](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189269) which is completely irrelevent

I'll try this

> **jamesrfla said:**
> Try rebooting the modem and router for two min. After two min plug in the modem and then after a min plug the router back in.

I don't have a router, just a modem. The problem is only in ubuntu, downloads are fine in windows.

---

### Post by RequinB4 on 2008-07-07
Well, at this point it's either one of two things, since there is nothing like this anywhere, and it's not any of the obvious stuff.

1)  A new kernel bug, in which case could you please post a report?

or

2) Your ISP somehow, whether intentionally or not, is throttling your connection while in ubuntu.  The most likely scenario I can think of is that you're accidently uploading a torrent in ubuntu on startup (still not very likely).  Probably only way to test this is to use someone else's ISP and see if that helps.

That's all i have, but at least this will be a bump.

---

### Post by AnarkistNZ on 2008-07-07
Try a speedtest on speedtest.net

Link us to the image it outputs. Post your Windows result, then your Ubuntu result side by side. Remember to use the same mirror for both tests, and do them one after the other.

e.g.
[img]http://www.speedtest.net/result/293289948.png[/img]

---

