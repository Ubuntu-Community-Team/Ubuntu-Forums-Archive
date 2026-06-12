---
title: "step by step help needed for wireless"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by smile-its-smiley on 2008-04-29
i have a toshiba a210 19t laptop with a built in realtek rtl8187b wireless card. no matter what i seem to do i cant get it working if this cant get resolved then ill have to move back to shoddy vista:( hope some one has the answer im looking for

---

### Post by skymera on 2008-04-29
ok when you type ```
 iwconfig 
``` does anything appear in the terminal?

You may be able to get wireless working using Ndiswrapper, i use it for my wireless.

---

### Post by renzokuken on 2008-04-29
have a look here
[http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/)

---

### Post by aberry5555 on 2008-04-29
If you have the installation cd for your wireless then copy the drivers folder on to your desktop for a start. Within that folder there should be a .inf file (you'll be looking for the 32bit version I presume) either in the top folder or a subfolder. Say the .inf file is placed like this in the folder:"realtek_wifi_driver/32bit/driver.inf" then you would open up a terminal and do the following:

```
sudo ndiswrapper -i realtek_wifi_driver/32bit/driver.inf
```

Hope this helps :)

---

### Post by smile-its-smiley on 2008-04-29
no wireless extensions.

eth0
no wireless extensions.

wlan0
IEEE 802.11g
ESSID:off/any
Mode:Managed
Frequency:2.457 GHz 
Access Point: Not-Associated   
          
Bit Rate:54 Mb/s   
Tx-Power:20 dBm   
Sensitivity=0/3  
          
RTS thr:off   
Fragment thr:off
          
Power Management:off
          
Link Quality:0  
Signal level:0  
Noise level:0
          
Rx invalid nwid:0  
Rx invalid crypt:0  
Rx invalid frag:0
          
Tx excessive retries:0  
Invalid misc:0   
Missed beacon:0

^^ that appeared after doing  iwconfig in the terminal

---

### Post by smile-its-smiley on 2008-04-29
ive allready tried sudo ndiswrapper -i realtek_wifi_driver/32bit/driver.inf to no avail. does any one know look at my last post if my drivers are installed or not?

---

### Post by renzokuken on 2008-04-29
```
ndiswrapper -l
```

will tell you if the driver has been installed correctly

---

### Post by smile-its-smiley on 2008-04-29
ndiswrapper -l

adminaccount@adminaccount-laptop:~$ ndiswrapper -l
net8187b : driver installed
	device (0BDA:8197) present
adminaccount@adminaccount-laptop:~$ 

im guessing that my drivers are ok but i now i have no idea how to connect to my router its not showing up in device manager

---

### Post by smile-its-smiley on 2008-04-29
bump still needing help unfortuantly:(

---

### Post by renzokuken on 2008-04-30
do you get anything from

```
sudo iwlist scan
```

---

### Post by 85fb on 2008-04-30
jake@jake-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

jake@jake-laptop:~$ sudo iwlist scan
[sudo] password for jake:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

jake@jake-laptop:~$ 

BTW Im on the comp right now? Weird. Im using 7.10. Sound doesnt work, drivers arent recognized. I thought i had it bad with 8.04...

---

