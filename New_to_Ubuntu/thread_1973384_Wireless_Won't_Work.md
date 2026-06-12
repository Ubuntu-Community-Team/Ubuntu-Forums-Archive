---
title: "Wireless Won't Work"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by WacoOne on 2012-05-04
Warning: I'm a newbie and have no geek skills. I installed Lubuntu on an old XP machine and it works beautifully. When I plug in an ethernet cord, it goes online right away. 

However, I can't get wireless to work. I've activated the Broadcom STA wireless driver, rebooted, unplugged ethernet ... no luck. 

What do I need to do?

---

### Post by bobman321123 on 2012-05-04
Have you downloaded the driver from this link: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
and compiled it?

---

### Post by TBABill on 2012-05-04
Are you sure which driver you need? Some models do not setup properly with the STA driver while the b43 works well for them. If you open a terminal and enter ```
lspci | grep Network
```and paste the output here we can help further.

---

### Post by WacoOne on 2012-05-04
I simply went into system tools and activated the additional drivers. Now the light is green, but still no luck. To answer your q Bobman, I have not downloaded and compiled the driver from that site you referenced.

Here's the info you requested, TBABill. Thanks!


eric@ubuntu:~$ lspci | grep Network
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by TBABill on 2012-05-05
Easy fix. Connect via ethernet, then ```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

---

### Post by NikTh on 2012-05-05
Hi , 
if you want give these commands to terminal and see if works
```
sudo rfkill unblock wifi 
sudo rfkill unblock all
``` 
Thanks

---

### Post by WacoOne on 2012-05-07
TBAbill, et al. Still no luck. I put in the code as you all suggested, nada. 

Any other ideas? 

(Thanks for the help, by the way.)

---

### Post by westie457 on 2012-05-07
Have you de-activated the STA driver? If not that can be done through 'Additional drivers' and as a check reinstall the packages suggested earlier```
sudo apt-get install --reinstall b43-fwcutter && sudo apt-get install --reinstall firmware-b43-installer
``` then reboot.

Your wireless should now be working.

---

### Post by WacoOne on 2012-05-07
Westie,

That got it! It's working now. Wow, I really appreciate the help. (I'm talking to you from the wireless connection now :-)

---

### Post by westie457 on 2012-05-07
Glad its working for you. 

Have got the same chip so was relatively easy.

When you get chance can you mark this as '[COLOR="Red"]Solved[/COLOR][COLOR="Black"]' using 'Thread Tools' at the top of the message pane[/COLOR]

---

### Post by WacoOne on 2012-05-07
Done. Thanks again.

---

