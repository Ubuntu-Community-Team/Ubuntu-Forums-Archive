---
title: "Wifi Problem on HP Stream 11"
date: 2016-02-02
forum: New to Ubuntu
---

### Post by angela7 on 2016-02-02
I'm a total newbie to Ubuntu. I decided to install it because I researched it and loved a lot of what I saw (and my Windows 8.1 was giving me a headache.) So today I installed Ubuntu 14.04 on to my HP Stream 11 using a bootable USB drive (pendrive installer thing). At the trial went great and I was able to connect to the wifi there using the Additional Drivers method (go to Additional Drivers and select the Broadcom thing). When I installed Ubuntu (dual-boot with Windows because I was scared something would happen...good thing I did) I couldn't get the wifi to work using the same method as before. It just goes to the do not use this driver option. I looked EVERYWHERE for help and just couldn't find anything to help me. I have used the terminal and tried to install another drivers but since it was offline, I couldn't download anything. I had also tried getting the bwml(or something) files from the USB and put it on to my Home directory and did the sudo dpkg-i *.deb thing but terminal doesn't understand it???? Please if anyone can help me I would really appreciate it! 

Here's my stuff in case anyone needs it (if this doesn't work then I can copy and paste it but it's pretty long!)

[ATTACH]267083[/ATTACH]

---

### Post by carverj on 2016-02-02
Please run the lspci command and output the result

---

### Post by cariboo on 2016-02-03
If you need the bcmwl driver, connect your usb drive, and navigate to /pool/main/d/dkms and install dkms by using the following command:

```
sudo dpkg -i *deb
```

next navigate to /pool/main/f/fakeroot and issue the following command:

```
sudo dpkg -i *deb
```

and finally navigate to /pool/restricted/b/bcmwl and issue the following command:

```
sudo dpkg -i *deb
```

Wireless should start automagically after the packages are installed. I used this method on my Compaq mini 110 for about 3 years until it died.

---

