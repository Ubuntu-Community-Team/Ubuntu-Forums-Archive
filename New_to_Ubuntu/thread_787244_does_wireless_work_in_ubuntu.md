---
title: "does wireless work in ubuntu"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by hazman on 2008-05-08
i have been trying now for over a week now to get my belkin wirless g network card to work. nothing doing at all tried various drivers only one that works is original one of the cd.the driver is installed but nothing i do makes it work. sudo modprobe ndiswrapper just hangs there and does nothing plz help someone

---

### Post by cmnorton on 2008-05-08
Please post some information about your hardware, including the contents of /etc/network/interfaces.

---

### Post by hazman on 2008-05-08
hi,
all i get off that is - auto lo    
iface lo inet loopback
am getting really downhearted wanted to try linux for a while and now i'm there getting naffed off of it but really like feel and how it works . all i want to do is browze net for now

---

### Post by dark_harmonics on 2008-05-08
have you tried ndiswrapper? You need the INF files from the windows driver.

---

### Post by hazman on 2008-05-08
yea tried that gone thru all process driver installed but when i put ==sudo modprobe ndiswrapper== it does nothing and just hangs there

---

### Post by hazman on 2008-05-08
looks like am going to go back to windows. nothing i try works. i've reinstalled twice now i WAS that eager to try ubuntu

---

### Post by bodhi.zazen on 2008-05-08
yea, wireless suppport can be a pain, even in your precious windows.

In fact the local library is handing out fliers informing that there is a bug in Vista and you can no longer connect @ the library with Vista ...

In my experience, if the card does not work out of the box, it can be a hassle.

List the device with :

```
sudo iwconfig
```

Output of that command ?

What happens when you try to connect with network manager ?

In addition we need to know more about your hard ware. It is insufficient information to simply state something is not working.

1. Model of Belkin (min works out of the box). That is why I bought it. You need to google your model and find the INF file to use  with ndiswrapper.

2. How are you connecting to your router ? Security ?

---

### Post by malangaman on 2008-05-08
Did you go to this link?
It helped me.

[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

---

### Post by Whiffle on 2008-05-08
Which card is it... i have a belkin g that uses madwifi sitting in my desk and works fine, but they used more than one chipset.

---

### Post by dark_harmonics on 2008-05-09
wow i wonder if OP tried madwifi then. I use that on my macbook pro and it works flawlessly. I want to mention that i also use 4 different types of wireless cards from a d-link dual channel to an old Cisco Aironet card.

---

