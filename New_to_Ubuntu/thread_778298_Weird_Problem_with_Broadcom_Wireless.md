---
title: "Weird Problem with Broadcom Wireless"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by amir1979 on 2008-05-01
hi all, i have just done a fresh install of ubuntu and have upgraded to the 8.04  but i have a problem with my broadcom wireless 4328   i had this problem before the upgrade to the new version.

my wireless works when i type sudo modprobe ndiswrapper in the terminal commands but everytime i reboot this command needs to be typed otherwise the wireless wont function.... can someone help or anyone else with a similar problem?

---

### Post by zxscooby on 2008-05-02
```
sudo ndiswrapper -m
```
will  load ndiswrapper automatically when the wlan0 interface is used


You may have to manually put ndiswrapper in the /etc/modules folder.



```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```

---

### Post by encompass on 2008-05-02
If your wireless works after that command then put the line ndiswrapper at the end of this file...
```

sudo nano /etc/modules
```
reboot and report back. :D

---

### Post by amir1979 on 2008-05-11
Hi all thank you for the replies, im sorry i havent been able to get back online been having problems with the pc :(     

unfortunatley none of the steps or codes are working for this at the moment...

the only thing that works is if i type the code

sudo modprobe ndiswrapper  

once i type this command in the konsole my wifi lights up and i have full function, i have no problem establishing connections with wpa or wep   the problem is i need to perform this command each time i boot up...    

any thoughts or suggestions?

---

### Post by encompass on 2008-05-11
Could you run this command please?
```

cat /etc/modules

```
and send me the output from that command.

---

### Post by amir1979 on 2008-05-15
Encompass   thank you for the help  the wireless seems to be working i dont know it mayhave started working based on earlier things but i hadnt noticed...    here is the output that i received when i entered that command that you requested


# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
sbp2
fuse
ndiswrapper

again the wireless is now working so far... :)   again thank you for all your help!!!

---

### Post by encompass on 2008-05-15
glad it's working... remember to check your wireless when ever there is a kernel upgrade.  It may need to be reinstalled, just don't remember. :/

---

### Post by anewguy on 2008-05-15
Yes, it was the addition of ndiswrapper to the /etc/modules file that made this work for you.  It used to be you could sudo modprobe ndiswrapper (which just tells Linux to load that particular kernel module) followed by sudo ndiswrapper -m (which was supposed to make ndiswrapper run at boot).  For some reason, the sudo ndiswrapper -m sort of quit doing it's thing so you have to add ndiswrapper to the /etc/modules file.  That file tells Linux at boot what extra kernel modules to load.

:)

---

