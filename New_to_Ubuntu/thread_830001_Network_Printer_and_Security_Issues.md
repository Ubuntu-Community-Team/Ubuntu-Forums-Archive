---
title: "Network Printer and Security Issues?"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by isaacj87 on 2008-06-15
Hey all,

Let me tell you guys my set-up first before I ask my question(s). I have a [HP Photosmart 2575 All-in-one]("http://h10025.www1.hp.com/ewfrf/wc/product?product=441240&lc=en&cc=us&dlc=") printer that I've recently hooked up to my wireless router so all my PCs in my house can use it (Windows and Linux PCs). My guess is it simply puts out a local IP address that we all can connect to and print.

My question is does this create any potential security issues? If so, how might I go about making my situation a little bit more secure?

Thanks in advance for responses! I, unfortunately, know little on the matter...

---

### Post by brian_p on 2008-06-17
> **isaacj87 said:**
> Hey all,

Let me tell you guys my set-up first before I ask my question(s). I have a [HP Photosmart 2575 All-in-one]("http://h10025.www1.hp.com/ewfrf/wc/product?product=441240&lc=en&cc=us&dlc=") printer that I've recently hooked up to my wireless router so all my PCs in my house can use it (Windows and Linux PCs). My guess is it simply puts out a local IP address that we all can connect to and print.

My question is does this create any potential security issues? If so, how might I go about making my situation a little bit more secure?

That printer has an ethernet port so I suppose you are using it with the router. I guess DHCP will get it an address like 192.168.x.x, just like all other devices on the network. If you're thinking of security in terms of what could come from the internet you are ok because the printer's address is not contactable from a remote host (unless you set up the router to make it so).

---

