---
title: "No wifi with lubuntu 12.04"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by seanthor1 on 2012-09-03
Hello everyone, I did my best to search through the forums for an answer to my problem and still couldn't get it solved. I am using a Compaq Presario c500 and after downloading and installing lubuntu 12.04 as well as the needed drivers I can connect through an ethernet cable, but not wireless. Here's the card I'm working with 
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01).

---

### Post by NikTh on 2012-09-03
Hello , 

Take a look here : [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

If you cannot figure it out , then post back here for further help.

Thanks

---

### Post by seanthor1 on 2012-09-04
Thanks, but I still can't get it to work.

---

### Post by seanthor1 on 2012-09-11
Finally got it. Here's what I did just in case anyone else stumbles across this with a similar issue. First you install: 
```
sudo apt-get install firmware-b43-installer b43-fwcutter
```
 
Then unload both modules:
```
sudo modprobe -r b43 wl
```
 
Then reload the b43 module:
```
sudo modprobe b43
```
 
At this point it should work. If you find that it's not working after you reboot, then you need to add it to "modules" :
```
sudo gedit /etc/modules
```
add b43 at the end of the list
 
If you find that the STA module also loads at boot, blacklist it by:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
and add it like this:
```
blacklist wl
```
 
NOTE: If you don't use the gedit text editor replace "gedit" with "vim" in the commands above. If you want the gedit text editor install it like this:
```
sudo apt-get install gedit
```
 
I take no credit for this one, all thanks to Rich at debianandi.blogspot.com

---

