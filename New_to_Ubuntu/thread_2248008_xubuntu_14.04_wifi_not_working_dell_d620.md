---
title: "xubuntu 14.04 wifi not working dell d620"
date: 2014-10-11
forum: New to Ubuntu
---

### Post by klein5366 on 2014-10-11
i'm working on a dell d620 laptop, I'm trying to up grade it from ubuntu 10.04 32bit to xubuntu 14.04 32bit. 10.04 worked perfectly well until adobe decided to not support flash in Linux, thus my journey begins! i first installed xubuntu 14.04, the wireless did not show at all like it doesn't have a wifi card in it. i tried every thing i could find with google, finally i triple booted it with ubuntu 10.04 32bit, xubuntu 12.04 32bit and xubuntu 14.04 32bit and found a wireless_script to run for de-tales. it is interesting to look at each script all coming from the same laptop but different versions of ubuntu. 

also i have noticed on this laptop there is a wifi led under the screen by the right hinge, when you boot 10.04 that led comes on and when you are booting 12.04 or 14.04 it never comes on. so xubuntu 12.04 and 14.04 isn't turning on the wifi card ?  

wireless-info_10_04.txt = wifi works out of the box  just had to install the sta driver 

wireless-info_12_04.txt = it had me install the driver, but it doesn't show anything to do with wifi in network manager  

wireless-info_14_04.txt = never asked me to install a driver, and it doesn't show anything to do with wifi in network manager

---

### Post by moropeza28 on 2014-10-12
I had the same problem a while ago. I follwed the instructions posted here and it always helped me  [http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

---

### Post by klein5366 on 2014-10-12
moropeza28 thanks

worked great on xubuntu 12.04 i went through the hole page but finally sudo apt-get install firmware-b43-installer installed the driver, i rebooted and the wifi led came on and wifi worked.

on xubuntu 14.04 i just did sudo apt-get install firmware-b43-installer i rebooted and the wifi led came on and wifi worked.

thank you can you mark this solved

---

