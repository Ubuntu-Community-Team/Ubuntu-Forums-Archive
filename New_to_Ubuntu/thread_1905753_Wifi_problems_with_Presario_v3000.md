---
title: "Wifi problems with Presario v3000"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by rbales427 on 2012-01-07
Hello everyone,
I recently inherited a Presario v3000 with a BCM4311 wifi card. It originally had XP on it, but it was buggy and I decided to download to Ubuntu 11.04 for multiple reasons. 1. I have always supported the open source movement and 2. I am currently going to school for information technology specializing in programming so I figured it would be great to try and learn a few things. So here is the situation. After installing Ubuntu, my wireless wont even register my connection. I found the Broadcom 43xx connection issues forum, but all the methods I used didn't work. I connected the laptop to a wired connection just fine, updated, and it had installed bcmwl kernal automatically. It still didn't work so I uninstalled it and manually installed it again through Synaptic, rebooted, and it still didn't work. It wont even let me scan. I input modprobe w1, and this was the message I recieved. 
 
FATAL: module w1 not found.
 
I continued my search for a solution, but nothing has come up. Any help would be greatly appreciated. I am currently living upstairs at my house and I don't want to have to run a 100 ethernet upstairs to use the internet if you know what I mean. Thanks in advance.

---

### Post by TBABill on 2012-01-07
For some reason the wl module doesn't work properly for the BCM4311 on either 11.04 or 11.10. Easy fix though. Open a terminal and ```
sudo apt-get install b43-fwcutter firmware-b43-installer
```When it finishes either restart or ```
sudo modprobe -r wl
```Then ```
sudo modprobe b43
```

If necessary, you may need to blacklist the wl module by ```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Add the following to the end of the file and save it ```
blacklist wl
```

---

### Post by rbales427 on 2012-01-07
I'll give it a try and let you know what happens.

---

### Post by rbales427 on 2012-01-07
> **TBABill said:**
> For some reason the wl module doesn't work properly for the BCM4311 on either 11.04 or 11.10. Easy fix though. Open a terminal and ```
sudo apt-get install b43-fwcutter firmware-b43-installer
```When it finishes either restart or ```
sudo modprobe -r wl
```Then ```
sudo modprobe b43
```
 
If necessary, you may need to blacklist the wl module by ```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Add the following to the end of the file and save it ```
blacklist wl
```
 It worked! Thanks for the help.

---

### Post by TBABill on 2012-01-07
No problem at all...enjoy!

---

