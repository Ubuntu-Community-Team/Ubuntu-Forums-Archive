---
title: "B43 driver install for Broadcom 43xx"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by alexsaysshoutitout on 2012-04-24
for some reason i cant get mine to work at all i install the b43installer and now i cant get the additional drivers to show anything it just says no proprietary drivers are in use on this system 
i am using a macbook pro 8-1 and no wireless please help

---

### Post by bkratz on 2012-04-24
> **alexsaysshoutitout said:**
> for some reason i cant get mine to work at all i install the b43installer and now i cant get the additional drivers to show anything it just says no proprietary drivers are in use on this system 
i am using a macbook pro 8-1 and no wireless please help



here is the easiest way to offline install the b43 driver.

[http://ubuntuforums.org/showpost.php?p=11860231&postcount=8](http://ubuntuforums.org/showpost.php?p=11860231&postcount=8)

---

### Post by oldos2er on 2012-04-24
Posts moved to their own thread.

---

### Post by alexsaysshoutitout on 2012-04-25
Quote:
 	 	 		 			 				 					Originally Posted by **wildmanne39** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11860231#post11860231") 				
 				[I]Hi, since you have no internet connection this should get you going but we may have to blacklist another driver.

Download the b43 zip file from a computer that has internet to a usb  flash drive then drag and drop the file to your ubuntu desktop.  Right-click it and select Extract Here. Open a terminal and do:
 	Code:
 	sudo mkdir /lib/firmware/b43 sudo cp Desktop/b43/* /lib/firmware/b43 sudo rmmod -f b43 sudo rmmod -f ssb sudo modprobe b43 
Thanks[/I]
 			 		 	 	 
i tryed what you sugested but this is all i got


alex@alex-MacBookPro:~$ sudo mkdir /lib/firmware/b43
alex@alex-MacBookPro:~$ sudo cp Desktop/b43/* /lib/firmware/b43
alex@alex-MacBookPro:~$ sudo rmmod -f b43
ERROR: Removing 'b43': No such file or directory
alex@alex-MacBookPro:~$ sudo rmmod -f ssb
ERROR: Removing 'ssb': No such file or directory
alex@alex-MacBookPro:~$ sudo rmmod -f ssb
ERROR: Removing 'ssb': No such file or directory
alex@alex-MacBookPro:~$ sudo modprobe b43


any help ???

---

### Post by TBABill on 2012-04-25
Since you are on a Macbook Pro I'll assume you can connect via ethernet. All you need to do to setup the b43 is ```
sudo apt-get install b43-fwcutter firmware-b43-installer
```Once it finishes either restart or activate the driver by ```
sudo modprobe b43
```

---

### Post by alexsaysshoutitout on 2012-04-25
i have it pluged in right now

---

### Post by alexsaysshoutitout on 2012-04-25
alex@alex-MacBookPro:~$ sudo apt-get install b43-fwcutter firmware-b43-installer[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en language-pack-kde-zh-hans
  language-pack-kde-en-base kde-l10n-engb kde-l10n-zhcn
  language-pack-zh-hans-base firefox-locale-zh-hans
  language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
alex@alex-MacBookPro:~$ sudo modprobe b43
alex@alex-MacBookPro:~$ 


still no wifi

---

### Post by CoDeHacKer on 2012-04-25
I had a Broadcom wlan on my hp and after reading around a lot, I was directed to the software center, the shopping bag and to type in bcm and install the firmware from there, and it worked for me, you have to have internet connection though

---

### Post by TBABill on 2012-04-25
Can you give us the actual output of lspci in a terminal? It's possible  you have a LPPHY device which is a bit different in setup.  Just a hunch at this point.

---

