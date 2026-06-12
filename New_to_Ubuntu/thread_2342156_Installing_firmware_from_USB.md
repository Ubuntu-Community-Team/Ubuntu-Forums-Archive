---
title: "Installing firmware from USB"
date: 2016-11-04
forum: New to Ubuntu
---

### Post by m.hoop on 2016-11-04
Morning all - 

Ok, full disclosure - I am a full-on Ubuntu (linux in general) newbie. Way, way green. So, I apologize for silly questions ahead of time. 

I installed Ubuntu on my old XPS laptop last night (Dell M1530) and somehow managed not to melt the thing. Victory #1.

That said, I'm now completely lost, but trying to learn/research in some kind of iterative fashion. I figured a good first step is internet connectivity. Despite the very pleasing Ubuntu interface, I discovered that wireless connections are not available because I believe my wireless card does not have drivers updated. Fine, I can research that. 

Here's where I am:

I found this resource for installing drivers offline: [http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

I followed all instructions and eventually arrived here to retrieve the firmware/drivers: [http://packages.ubuntu.com/yakkety/firmware-b43-installer](http://packages.ubuntu.com/yakkety/firmware-b43-installer)

I downloaded the 'all' package and each macro package that was labeled 'depends' for a total of 4 files. I put them on a USB stick and subsequently plugged them in to the laptop. Now...I'm stuck. 

I don't know what commands to use to install something from the USB stick such that I can proceed with trying to get my wifi active. Any thoughts? (also, please use small words...)

Thanks
hoop.

---

### Post by oldos2er on 2016-11-04
Need to know what wireless device you're using. Can you open a terminal (Ctrl-Alt-t) and enter ```
lspci | grep Wireless
``` and copy/paste the result here?

---

### Post by m.hoop on 2016-11-04
oldos2er - you bet. 

"0b.:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)"

---

### Post by oldos2er on 2016-11-04
See this thread: [https://ubuntuforums.org/showthread.php?t=2306200](https://ubuntuforums.org/showthread.php?t=2306200) regarding the same device. Let us know if it helps.

---

### Post by m.hoop on 2016-11-04
I did it!

Read: You did it, thank you, kindly.

I'm officially connected to the internet from my previously window(ed) computer. Much obliged. If I understand correctly, the most newbie-friendly way to update drivers and install programs is using 'get' and utilizing the Ubuntu repositories. Is this on track?

---

### Post by oldos2er on 2016-11-04
If by "get" you mean apt-get, that is one way to do it. Some newbies do not feel that using the terminal is at all user-friendly, and it's ok if you feel that way. You can do most of the same things graphically if you prefer, see [https://help.ubuntu.com/stable/ubuntu-help/addremove.html](https://help.ubuntu.com/stable/ubuntu-help/addremove.html)

Would you please mark your thread 'Solved' using Thread Tools at the top of this page? It will help others who might have the same question. Thanks!

---

