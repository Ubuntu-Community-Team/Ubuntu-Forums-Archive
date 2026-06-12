---
title: "Asus n-13 wireless card install problems"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by McKage on 2011-10-08
Hi guys,
So I am very new to ubuntu linux. I have the ubuntu 11.04 install and I picked up this wireless card because it specifically had linux support. Upon browsing the files on the cd, it appears that there are instructions on how to install this driver but it is much too far above my head for me to be able to execute them properly. Does anyone know how to get this driver installed, any help would be much appreciated :) I have worked on a basic level in the terminal but i do not have a really well-versed knowledge in it. Thank you!

McKage

---

### Post by Redblade20XX on 2011-10-08
Usually there is included in the driver a README. That's where you should start. You'll have to compile the driver your self (getting the full linux experience ;)) or use the search function on this site to see if anyone has watered down the build instructions for beginners. :p

- Red

---

### Post by McKage on 2011-10-08
Yes but my particular question is how do i compile the driver. These instructions give me some code but i don't know what i need to replace with machine specific numbers and what to type in at face value. Can you help?

---

### Post by thefasterblueone on 2011-10-08
I have this adapter using 11.04 with no problems.

[https://help.ubuntu.com/community/WifiDocs/Device/Asus%20USB-N13_Natty%2011.04]("https://help.ubuntu.com/community/WifiDocs/Device/Asus%20USB-N13_Natty%2011.04")

---

### Post by Redblade20XX on 2011-10-08
_*****NOTE*****_ : Make sure to back up your important stuff. Compiling and installing stuff manually has the potential to break the system if done incorrectly.


Go here and download the most recent driver for RT3070 : [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

Open a terminal and type: ```
sudo apt-get install build-essential
``` This installs the complier and useful tools.

Move the downloaded file into your destop and follow these instructions: 

_*****NOTE*****_ : Some of these instructions might need some time to complete so don't just mass copy and paste. Enter each instruction and wait till the terminal tells you it's complete. Also for the make part, make sure that at the end of the instruction the terminal tells you it's successful in compiling or else you'll have a broken system if you continue on.

> **chili555 said:**
> 

Open a terminal and do:```
cd Desktop/
tar xvjf DPO_RT3070*
cd DPO_RT3070_LinuxSTA_V2.3.0.2_20100412
gedit os/linux/config.mk
```Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.

Proofread, save and close gedit. Now do:```
sudo su
cp RT2870STA.dat RT3070STA.dat
rm /etc/udev/rules.d/network_drivers.rules
rm /etc/modprobe.d/network_drivers.conf
make
make install
rmmod -f rt2870sta
modprobe rt3070sta
exit
```Detach the ethernet cable, if any and click the Network Manager icon.

Now is your card working? We may need to tweak RT3070STA.dat, if not.

Hopefully it all works out correctly! ;)

-Red

---

### Post by Redblade20XX on 2011-10-08
:lolflag: since there was an easier way to do this! I'll leave this for anyone who needs it for lower buntu distributions. :tongue:

-Red

---

### Post by McKage on 2011-10-08
Thanks to thefasterblueone this is like not a problem anymore :) thanks guys for your responses.

---

