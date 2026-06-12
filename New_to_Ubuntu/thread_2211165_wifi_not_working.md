---
title: "wifi not working"
date: 2014-03-14
forum: New to Ubuntu
---

### Post by zee4 on 2014-03-14
Dear all,

I have a dell d530 core 2 duo. Recently upgraded from 10.10 to 12.04 from a live DVD. My wifi has stopped working. <pressing Fn+F2 turns on the blue tooth rather than the wifi. I am total newbie and a computer illiterate. By the way, I have installed it sisde by side with Windows XP. The wifi is not working in the windows as well. 

Regards.

---

### Post by grahammechanical on 2014-03-14
Have you changed some hardware setting in the BIOS? As Wifi is not working in XP I would conclude that it is not Ubuntu specific. Also, I think that the F keys are a function of the hardware and not of the operating system. Pressing Fn+F2 is switching on/off hardware adapters. Should be the WiFi adapter but is actually the Bluetooth adapter.

Have you recently added a Bluetooth adapter? I do not know about Bluetooth but the Wifi adapter on my machine is PCI. Could it be that Bluetooth is now using the hardware device assignment that was previously assigned to the WiFi adapter? Is the Wifi adapter still connected into the motherboard?

Regards.

---

### Post by zee4 on 2014-03-14
Thanks for the reply. Would not think of tinkering with the BIOS. Your r right the F2 buton has a radio signal on it.  however the wifi also stopped working when I installed 10.10

---

### Post by Vladlenin5000 on 2014-03-14
[ftp://ftp.dell.com/Manuals/all-products/esuprt_laptop/esuprt_latitude_laptop/latitude-d530_user%27s%20guide_en-us.pdf](ftp://ftp.dell.com/Manuals/all-products/esuprt_laptop/esuprt_latitude_laptop/latitude-d530_user%27s%20guide_en-us.pdf) -> page 48:

[FONT=serif][I]<Fn><F2>                                                 Enables and disables wireless networking 
[/I][/FONT]
[FONT=serif]*and Bluetooth wireless technology.*
[/FONT]

---

### Post by zee4 on 2014-03-14
Vladlenin, Yes , realised that, thanks. But the wifi....

---

### Post by Vladlenin5000 on 2014-03-14
About the WiFi... Was it working _before_, in Windows?

YES -> It should work as always. [FONT=serif]<Fn><F2> to enable/disable both radios[/FONT] (make sure it's enabled in Windows before rebooting back to Ubuntu, just in case -- and -- note down the name of the WiFi card). Troubleshoot in Ubuntu.
NO -> You shouldn't expect it to work in Ubuntu either.

---

### Post by zee4 on 2014-03-14
Last time when I installed 10.10, the wifi stopped working again

---

### Post by Vladlenin5000 on 2014-03-14
OK, but it worked again with th FN switch, right?

---

### Post by zee4 on 2014-03-14
managed to switch on wifi thru windows but ubuntu is still not recognising it. What now?

---

### Post by zee4 on 2014-03-14
wifi light on , working in windows, but ubuntu not detecting it

---

### Post by zee4 on 2014-03-14
if this is of any help, this is the output of ifconfig


eth0      Link encap:Ethernet  HWaddr 00:1d:09:a9:55:ce  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:53083 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68104930 (68.1 MB)  TX bytes:5200401 (5.2 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1535 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:229676 (229.6 KB)  TX bytes:229676 (229.6 KB)

---

### Post by wildmanne39 on 2014-03-14
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

Also there are probably several issues upgrading from 10.10 to 12.04,it is a bad idea because there are so many changes that a fresh install is almost the only way to go.

If you post the output of the script we will take a look. 
Thanks

---

### Post by fbrand on 2014-03-14
I suspect you either do not have the correct driver or the driver you have is not properly configured. Laptop Wifi always seems to be a bit of an issue.

Try here for some information:-

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)


[http://linux.ittoolbox.com/groups/technical-functional/ubuntu-l/installing-drivers-for-dell-1390-wlan-mini-card-on-ubuntu-1110-4495330](http://linux.ittoolbox.com/groups/technical-functional/ubuntu-l/installing-drivers-for-dell-1390-wlan-mini-card-on-ubuntu-1110-4495330)

---

### Post by zee4 on 2014-03-15
Dear Moderator,

Thanks for the input. I am attaching the file.

---

### Post by Hadaka on 2014-03-15
Hi, zee4, it looks like you loaded the wl module when you
upgraded to 12.04. When it asks or offers a "proprietary"
driver...just ignore..or say NO.
this should get you up and running...please do.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43 
```

---

### Post by zee4 on 2014-03-16
Dear Hadaka,

Thank you. Wifi up and running. Wooooooo:p.
And thanks to everybody else as well.

---

### Post by Hadaka on 2014-03-16
glad that worked for you!!

---

