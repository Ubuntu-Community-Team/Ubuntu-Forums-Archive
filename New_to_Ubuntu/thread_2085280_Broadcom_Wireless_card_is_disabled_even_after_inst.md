---
title: "Broadcom Wireless card is disabled even after installation of b43-fwcutter.. etc"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by osu39 on 2012-11-17
Hi, 

I just recently installed Ubuntu 12.04 on my macbook pro (mid-2012) and my wireless card is disabled. Unfortunately, I do not have access to an ethernet cable, which makes the problem very hard for me. The network settings says it is missing firmware. I understand I need b43 stuff and I have downloaded the required packages on my Mac OSX partition. I then used the following commands in terminal to install everything. 

sudo dpkg -i b43-fwcutter_014-9_i386.deb

tar xfvj broadcom-wl-4.150.10.5.tar.bz2 sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o 

sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o. 

None of the above commands returned error codes. Is there anything else I need to do. When I ran sudo lshw -class networt it said the driver was b43, but the firmware "N/A". My network still says it is disabled. Is there anything eles I should do? Thanks.

---

### Post by sidzen on 2012-11-17
you need brcm43xx-0.fw NOT the fwcutter
first uninstall recursively the folder you untarred to, then get on wired internet and download to USB stick the brcm43xx file and bcm43xx_hdr-0.fw then install to /lib/firmware/brcm (or wherever firmware is normally installed on your system).

---

### Post by osu39 on 2012-11-17
Ok I installed one more thing (I forget what it was) then I rebooted my system to check if anyone replied to this thread. After going back to my linux partion the internet worked fine. However, I really appreciate the help.

---

