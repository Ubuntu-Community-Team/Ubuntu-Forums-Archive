---
title: "inspiron 1520 wireless not working."
date: 2011-10-20
forum: New to Ubuntu
---

### Post by mon94key on 2011-10-20
I know nothing about "ubuntu" wanted to test it on a machine that windows doesn't like manged to install it etc but i cannot get wireless to work it is using "broadcom wireless" thing driver containing "This package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware." but it still will not work i'm not one to post right away with a problem i looked round, seems i require a custom driver, i found it read the instructions and didn't  understand how you get access to type in all this root stuff, don't also understand why there isn't just a driver you can just in theory "drag and drop" but i suppose this is why Linux is open source, if someone could explain what you need to do to get wireless working it would be awesome. i went on the IRC channel but they didn't reply to my messages so this is last ditch attempt for help.
thanks :)

---

### Post by gandaran on 2011-10-20
have you looked in additional drivers to activate the broadcom driver?

---

### Post by mon94key on 2011-10-20
it does say "this driver is activated and currently in use" i found someone said in the latest version the wireless buttons actually work so i flicked it up and down and no difference as towards wireless working i also unplugged the LAN and typed in all the Wi-Fi details (because i presume it wont scan without it working) and put every detail in and waited... and waited and it didn't connect to anything it seems i need a driver and i found it here [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/) (i believe this will make it work) but its well over my head to understand :/

---

### Post by gandaran on 2011-10-20
> **mon94key said:**
> it does say "this driver is activated and currently in use" i found someone said in the latest version the wireless buttons actually work so i flicked it up and down and no difference as towards wireless working i also unplugged the LAN and typed in all the Wi-Fi details (because i presume it wont scan without it working) and put every detail in and waited... and waited and it didn't connect to anything it seems i need a driver and i found it here [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/) (i believe this will make it work) but its well over my head to understand :/
there is an easier way, first find out which  broacom chipset model
type in terminal
```
lspci
```
then with the chipset model find threads in the search box, there are plenty threads on broadcom wireless problems, you will find the fix here.
I doubt you have to download any driver, ubuntu provides them in the software package center, you just need to know exactly which one to install. 
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by mon94key on 2011-10-20
> **gandaran said:**
> there is an easier way, first find out which  broacom chipset model
type in terminal
```
lspci
```then with the chipset model find threads in the search box, there are plenty threads on broadcom wireless problems, you will find the fix here.
I doubt you have to download any driver, ubuntu provides them in the software package center, you just need to know exactly which one to install. 
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)


tried this typed it all in etc rebooted thought "whew wireless finally" unplugged the LAN and again device wasn't detected its the "Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311]"

also then did a fourm search with a file you install after un-installing the original one but again that didn't work, trust me to always have problems regardless of the operating system.

---

### Post by gandaran on 2011-10-20
> Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311
just typing 'BCM4311' in the forum search box finds a lot of threads withe same chipset.
here's one guide that should be very easy to fix your problem with drivers, remove what you have installed first.
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by computerandu on 2011-10-20
This might be helpful:

[http://www.computerandyou.net/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://www.computerandyou.net/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

---

