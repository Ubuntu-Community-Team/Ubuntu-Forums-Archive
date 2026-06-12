---
title: "HOWTO: Use ath9l_htc driver for Pronet PN-11NUSB"
date: 2010-10-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Myth123 on 2010-10-14
This is my first HOWTO so please correct me if something goes wrong.

Today I purchased a PRONET PN-11NUSB wifi adapter in a hurry which is based on atheros chip. After googling a lot I managed to get it work.
[B]
Here are the steps:[/B]

I followed the initial steps from [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9142140&postcount=9") but with slight difference.

**1.** Download the compat wireless drivers from [[COLOR="Red"]here[/COLOR].]("http://wireless.kernel.org/download/compat-wireless-2.6/")

**2.** Extract the downloaded file

**3.** Now open the terminal and change directory to extracted directory
```
e.g. $ cd ~/Downloads/compat-wireless-2.6.35-1/
```
 
**4.** You will need to make the drivers.
```
$ make
```

**4.** Install drivers.
```
$ sudo make install
$ sudo make unload
$ sudo modprobe ath9k_htc


```

**5.** You need to install firmware for the drivers to work.

Download the firmware from [[COLOR="Red"]here[/COLOR]]("http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree") [Look for ar9271.fw].

**6.** Copy the ar9271.fw file to /lib/firmware
```
$ sudo cp /path/to/file /lib/firmware
```

**7.** We are done!! cross check if your new hardware is installed correctly.
```
$ sudo lshw
$ iwconfig
 
```

---

### Post by taditya on 2010-12-12
Hey thanks, I've Ubuntu 10.10 installed on an Intel x86 machine and have bought the same PRONET PN-11NUSB wi-fi dongle. I followed the steps mentioned in your post and the PRONET wirelss device is working now. But I have a new problem. Now, my Tata Indicom Photon+ has stopped working on this machine. 

Earlier, when I listed the usb devices using lsusb, it used to show up as "12d1:140b". But now, the same device is listed as "12d1:1446" in lsusb listing. 

I tried to re-install the usb-modswitch & relevant data pkg and again modified the etc/usb-modswitch.d/12d1:1446 file, but to no awail. Can you please help me make the device functional again?

Thanks again,
Aditya

---

### Post by Myth123 on 2010-12-15
Aditya,
Unfortunately I do not have the photon+ to reproduce the problem. I am out of clue of what might had happened. Have you tried reconfiguring modem again? To check if the problem is due to pronet drivers, you can just unload ath9k_htc and try using your photon+.

---

