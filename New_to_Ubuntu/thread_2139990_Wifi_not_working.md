---
title: "Wifi not working"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by nns2006 on 2013-04-28
Hello,
I am having problem with wifi in ubuntu 12.04 on dell vostro 1500. it was working well before I reinstalled it.
I am trying to make it work since friday night by following the suggestion on forum. But I have not got success in it.
my configuration:
  
[HTML] lspci -vvnn | grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
[/HTML]

and [HTML]
rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
[/HTML]

and [HTML]
 lspci -n | grep 14e4
03:00.0 0200: 14e4:170c (rev 02)
0c:00.0 0280: 14e4:4311 (rev 01)
[/HTML]

... I am desparately looking to make it work today.

 Thank you for your help.

---

### Post by wildmanne39 on 2013-04-28
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by nns2006 on 2013-04-28
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

Thanks for reply. 
Please find the file attached.

---

### Post by nns2006 on 2013-04-28
Another strange thing is when I am going into ubuntu with linux 3.5.0.27 there is not even wired connection. However, when I reboot and goes again to 3.2.0.40, wired connections works. 
I really don't know what has happend to my system.

Thank you fo you help.

---

### Post by nns2006 on 2013-04-28
removing [HTML]bcmwl-kernel-source[/HTML] completely helps. Now it is working.

---

