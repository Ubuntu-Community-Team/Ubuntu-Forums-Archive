---
title: "HELP wireless signal is not working anymore :("
date: 2012-08-12
forum: New to Ubuntu
---

### Post by hkmy on 2012-08-12
hi there, 

I did not know what to do so I follow the instruction on this website: [http://ubuntuforums.org/showthread.php?p=12165054#post12165054](http://ubuntuforums.org/showthread.php?p=12165054#post12165054) and now my wireless interface "eth0" is not working anymore. I need help getting it back now i am just using the Ethernet. 
This is what i did:


wan@Wan-Inspiron-910:~$ iwconfig
lo        no wireless extensions.

eth3      no wireless extensions.

eth0      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:194  Noise level:199
          Rx invalid nwid:0  invalid crypt:2194  invalid misc:0

wan@Wan-Inspiron-910:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1507]
	Kernel driver in use: wl
--
02:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: Hewlett-Packard Company Device [103c:308f]
	Kernel driver in use: atl1c
wan@Wan-Inspiron-910:~$ sudo ifconfig eth0 down
[sudo] password for wan: 
wan@Wan-Inspiron-910:~$ sudo rmmod -f wl
wan@Wan-Inspiron-910:~$ sudo modprobe wl nohwcrypt=1
FATAL: Error inserting wl (/lib/modules/3.0.0-24-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)
wan@Wan-Inspiron-910:~$ sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device
wan@Wan-Inspiron-910:~$ sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device
wan@Wan-Inspiron-910:~$ iwconfig
lo        no wireless extensions.

eth3      no wireless extensions.

wan@Wan-Inspiron-910:~$ sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device

---

### Post by Bashing-om on 2012-08-12
Hi!
 wireless is not my cup of tea... but I am willing to take a stab at it and try to assist.....
 Firstly lets see if any devices are recognized. In terminal run this command and and post the output back to this thread:
```
lshw -C network
```
Depends on this result what our next step will be.

[INDENT]Best regards <====BDQ
[/INDENT]

---

### Post by anewguy on 2012-08-13
I'd wait for wildmanne39 to come to this thread - he is an expert at this.  He may know right away what to do, but he also has a script that gives him a lot of information when you run it and post the results back.  Get a head start and follow post number 8 in this thread:

[http://ubuntuforums.org/showthread.php?t=2038977]("http://ubuntuforums.org/showthread.php?t=2038977")  

Post the requested information back in another post in this thread.

---

### Post by wildmanne39 on 2012-08-14
Hi, I know part of the issue but we need to see more information before I post a solution, please copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by hkmy on 2012-08-15
Nevermind I got it working again by plugging the ethernet on to my netbook. Thanks you guys! :popcorn::KS

---

