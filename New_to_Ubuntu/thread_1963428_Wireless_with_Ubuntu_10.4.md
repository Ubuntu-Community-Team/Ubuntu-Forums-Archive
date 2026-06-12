---
title: "Wireless with Ubuntu 10.4"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by jagdefalke on 2012-04-22
Hey ya'll.    I just got an acer netbook for wireless because the hubby always has to take our internet with him (truck driver) for business purposes.     this is my very first experience really with anything resembling a portable pc with wireless, I've always been on desktops with ethernet so I feel like I'm pretty much starting from rock bottom.    I've partitioned it with the win 7 loader on one half and 10.4 on the other from the startup disk creator on my desktop, and I can easily find all kinds of signals in town with the win7 but I really have no idea how to get 10.4 to pick anything up.   I know I still have some basic lib packages to download and stuff and I'm gonna have to go hook up at the inlaws to do that, I'm just not sure what exactly i need to get wireless working.    So I was just hoping someone would be willing to give up a little list of what I need?   ;)   Maybe some drivers or something?

---

### Post by wildmanne39 on 2012-04-22
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by IWantFroyo on 2012-04-22
Does the netbook have an Ethernet port? If so, run "gtk-jockey", or find "Additional Drivers" in the System menu.

What model netbook do you have?

---

### Post by cogier on 2012-04-22
I have found that Acers work well with 10.04. Have you run  **System>Administration>Hardware drivers**. You will need to be connected to the internet. This may find and install the drivers you need.

---

### Post by jagdefalke on 2012-04-22
Excellent, thankyou!   I just now hooked up to the inlaws ethernet and will check all those out and let you know what happens.   :)
It's an Aspire One d270, the standard wallyworld special.  hehe..OK




added:
OK, so I found the broadcom wireless driver and installed that along with the standard libdvdcss2, and Wi-Fi Radar.   Reloaded my packages, checked for updates and just for giggles restarted the system and it seems to be picking up the local neighborhood signals...   so I guess all I need to do now is head back into town and test it on a public signal.   Wish me luck!   
Thanks everyone!  :)

---

### Post by jagdefalke on 2012-04-25
Seems to be working now.  :)

---

