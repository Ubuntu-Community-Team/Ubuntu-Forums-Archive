---
title: "Wireless Card not working Acer Aspire One D255"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by gyenyame357 on 2012-03-22
Hello.  I am new to the world of linux and I am trying to get this particular problem fixed.  I cannot access the internet wireless or wired.  It shows on the home screen no network connections.  I have tried using the search function but i did not have any luck after searching for and hour.  If anyone can help me out with this matter it would be greatly appreciated.  Thanks

---

### Post by leMasoud on 2012-03-22
have you started up your device with Ubuntu live?!
see if it recognizes the wireless device while in live mode and then go to your installed version and try installing your device driver from your Ubuntu CD through Synaptic Package Manager.
search "ndis" and install it.

 if you are sure your device is installed correctly try setting up the device by its defaults ...by default it obtains IP and configs by DHCP so try setting up your wired connection with DHCP and with no particular IP assigned to your network devices it would find and work automatically!

---

### Post by wildmanne39 on 2012-03-22
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by gyenyame357 on 2012-03-22
gyenyame357@gyenyame357-laptop:~$ cat /etc/lsb-release; uname -a 
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=10.04 
DISTRIB_CODENAME=lucid 
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS" 
Linux gyenyame357-laptop 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux 
gyenyame357@gyenyame357-laptop:~$ lspci -nnk | grep -iA2 net 
01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1) 
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01) 
gyenyame357@gyenyame357-laptop:~$ iwconfig 
lo        no wireless extensions. 

gyenyame357@gyenyame357-laptop:~$ rfkill list all 
gyenyame357@gyenyame357-laptop:~$ lsmod

---

### Post by miegiel on 2012-03-22
> **gyenyame357 said:**
> gyenyame357@gyenyame357-laptop:~$ cat /etc/lsb-release; uname -a 
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=10.04 
DISTRIB_CODENAME=lucid 
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS" 
Linux gyenyame357-laptop 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux 
gyenyame357@gyenyame357-laptop:~$ lspci -nnk | grep -iA2 net 
01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1) 
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01) 
gyenyame357@gyenyame357-laptop:~$ iwconfig 
lo        no wireless extensions. 

gyenyame357@gyenyame357-laptop:~$ rfkill list all 
gyenyame357@gyenyame357-laptop:~$ lsmod

You have a Broadcom wifi card which needs drivers that are not FOSS and can't be distributed with ubuntu. However there is an installer for the driver, but you need to connect to the internet using your ethernet to get the driver.

Next time you buy a laptop avoid Broadcom :lolflag:

---

### Post by wildmanne39 on 2012-03-22
Hi, if you installed from the CDROM you can simply add the install CD as a package source and install bcmwl-kernel-source, automatically installing the required dependencies. 
Thanks

---

### Post by westie457 on 2012-03-22
Hi, take a look at this thread [http://ubuntuforums.org/showthread.php?t=1889170](http://ubuntuforums.org/showthread.php?t=1889170)

This has step by step instructions on which driver you need and how to obtain them. It also has a way to install them if you have no wired connection.

Hope this helps.


wildmanne39 got in first, again. Out ninja'd by the black-belt.

---

### Post by Gleichsnerd on 2012-03-22
> **miegiel said:**
> You have a Broadcom wifi card which needs drivers that are not FOSS and can't be distributed with ubuntu. However there is an installer for the driver, but you need to connect to the internet using your ethernet to get the driver.

Next time you buy a laptop avoid Broadcom :lolflag:


True story. Just got my wireless working yesterday on a Broadcom card, however my ethernet was still working.

Try the Live CD first and see if it can connect to a network. It should have the appropriate driver (Broadcom STA driver) all set to go on there. If it still doesn't work, then it sounds like either a hardware issue or an epic failure.

In the terminal, please enter

```
lshw -C network
lsmod
```

and post what is printed here. Mind you, that's a capital C, not lowercase. sudo shouldn't be necessary, but you can if it's your heart's desire.

---

### Post by gyenyame357 on 2012-03-22
It worked running the livecd and installing the broadcom sta wireless driver.  I was able to connect to my home network.  How do I get the drivers to stay on the system.  When I rebooted ubuntu no network connection.

---

### Post by gyenyame357 on 2012-03-22
Again, thanks for the help and support!  Greatly appreciated!

---

### Post by gyenyame357 on 2012-03-22
Okay I figured it out. I re installed ubuntu and everything is kosher. Thanks again!

---

