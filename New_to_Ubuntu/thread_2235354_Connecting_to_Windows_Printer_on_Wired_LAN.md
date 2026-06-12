---
title: "Connecting to Windows Printer on Wired LAN"
date: 2014-07-20
forum: New to Ubuntu
---

### Post by davec51 on 2014-07-20
Solved by Morbius1! Thanks. I just installed the latest Lubuntu (32 bit) on an old Dell. When I try to set up my HP printer on my wired LAN, I get no choice "Windows Printer via Samba," but a search find my printer and reports it as accessible. When I clidk to go on, however, I get endless churning and no moving forward. I have set up this printer successfully on with several other versions of Ubuntu, including Xubuntu and Mint.

---

### Post by Rex Bouwense on 2014-07-20
HP printers and Linux are quite compatable.  If you are having problems use HPLIP.
[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

### Post by davec51 on 2014-07-20
My problem doesn't seem to be a correct driver. I don't get to that point; the connection stalls after I find the printer on the network and before I get to entering the make and model.

---

### Post by varunendra on 2014-07-20
You should clearly mention the model number of the printer. Some of us may have experience with it.

---

### Post by davec51 on 2014-07-21
It's HP Officejet 6600.

---

### Post by Morbius1 on 2014-07-21
I haven't used Lubuntu in quite a while but for reasons unknown it always seemed to be missing one or all of the following packages so you might want to install them and see if the situation improves:
```
sudo apt-get install libsmbclient
```
```
sudo apt-get install smbclient
```
```
sudo apt-get install python-smbc
```
Worst case it will tell you it's already installed.

You may have to restart cups:
```
sudo service cups restart
```

---

### Post by davec51 on 2014-07-21
Thanks a lot, Morbius1. It was smbclient that I needed.

---

