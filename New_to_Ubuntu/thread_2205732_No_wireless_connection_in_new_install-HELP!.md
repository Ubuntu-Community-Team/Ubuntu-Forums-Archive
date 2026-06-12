---
title: "No wireless connection in new install-HELP!"
date: 2014-02-15
forum: New to Ubuntu
---

### Post by Bugscuffle on 2014-02-15
I'm the new guy that doesn't know scratch about computers and especially ubuntu. I loaded ubuntu onto the second H.D on my computer. O.K. good it appears to be working except that I have no connection to the internet. O have Windows 7 on the other H.D. and it is connected to my WiFi router and works fine. How do I, and remember, I don't know scratch, get this ubuntu to work with my WiFi? Thanks in advance.

---

### Post by Vladlenin5000 on 2014-02-15
Assuming you have a standard Ubuntu, in the top bar at right you'll find the network-manager 'icon' and if your WiFi device has been correctly recognized and installed you should see a list of wireless networks (or at least yours). Click it, enter the password if required and you should be good to go.
If not please post back and inform which WiFi device you computer has.

---

### Post by Frogs Hair on 2014-02-15
You also may need to install a wireless driver from additional drivers. In 12.04 search for Additional Drivers and in 13.10 it is located in Software & Updates > Additional Drivers.

---

### Post by Bugscuffle on 2014-02-15
O.K. I found the Additional Drivers icon in Network Settings, but how do I get there if I don't have a network connection and what I am trying to get is that network connection? Am I trying to download something that will enable me to download it? I have the original installation disc. Is it on there?

---

### Post by Vladlenin5000 on 2014-02-15
You need an internet connection to do that indeed. Try Ethernet if available.

---

### Post by wildmanne39 on 2014-02-15
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

