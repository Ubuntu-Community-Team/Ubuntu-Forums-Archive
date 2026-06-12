---
title: "Ubuntu Utopic 14.10 No Bluetooth Adapter"
date: 2014-11-01
forum: New to Ubuntu
---

### Post by Dinh_Quoc_Han on 2014-11-01
[img]http://i.imgur.com/GbV00Sq.png[/img]
On test USB tick, Bluetooth working fine, second test, it was not work. After installed my laptop, restart laptop, have bluetooth, restart laptop, not have bluetooth (picture here). After, i try update, now my laptop dont have buetooth adapter (picture here).
Pleaze help me, my English is very bad ! sorry :(

---

### Post by JeQhdMD on 2014-11-01
Is the bluetooth adapter built-in to the laptop, or as it seems, are you using a usb bluetooth adapter that you plugin?  What is the model of bluetooth adapter?  Have you also tried installing the "blueman" package from the Ubuntu Software Center?  Also, do you actually have Ubuntu installed to the hard drive, or are you operating it from a USB-Flash-Stick?

---

### Post by Dinh_Quoc_Han on 2014-11-01
> **JeQhdMD said:**
> Is the bluetooth adapter built-in to the laptop, or as it seems, are you using a usb bluetooth adapter that you plugin?  What is the model of bluetooth adapter?  Have you also tried installing the "blueman" package from the Ubuntu Software Center?  Also, do you actually have Ubuntu installed to the hard drive, or are you operating it from a USB-Flash-Stick?

The bluetooth adapter is built-in to the laptop.I have tried installing the "blueman" package from the Ubuntu Software Center but not working. Ubuntu installed to the hard drive.

My infomation:
```
dinhquochan@TiLovePo:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 04ca:300b Lite-On Technology Corp. 
Bus 002 Device 002: ID 1bcf:2c17 Sunplus Innovation Technology Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dinhquochan@TiLovePo:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.16
S:  Manufacturer=Linux 3.16.0-24-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8000 Rev=00.04
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.16
S:  Manufacturer=Linux 3.16.0-24-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=04 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1bcf ProdID=2c17 Rev=00.12
S:  Manufacturer=SunplusIT INC.
S:  Product=HD WebCam
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=01 Prnt=01 Port=05 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04ca ProdID=300b Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=(none)

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.16
S:  Manufacturer=Linux 3.16.0-24-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

```

---

### Post by JeQhdMD on 2014-11-02
Perhaps similar problem as in this thread?

[http://ubuntuforums.org/showthread.php?t=2249996&highlight=bluetooth+issue](http://ubuntuforums.org/showthread.php?t=2249996&highlight=bluetooth+issue)

---

### Post by Dinh_Quoc_Han on 2014-11-02
What do i do to fix this ?

---

### Post by Dinh_Quoc_Han on 2014-11-02
Now my bluetooth is working. I try reinstall 
```
sudo apt-get install --reinstall linux-headers-generic build-essential
```
After that, compile and install the driver as follows -
1) Download the latest backported driver package from here - [http://drvbp1.linux-foundation.org/~...tml/backports/]("http://drvbp1.linux-foundation.org/%7Emcgrof/rel-html/backports/")
2) Copy the downloaded tar.bz2 package to your Ubuntu Desktop > Right-click > Extract here.
3) Open a terminal and run the following commands one-by-one 
 	```
cd Desktop/backports-3.18-rc1-1
make defconfig-ath9k
make
sudo make install 
```

4) Reboot for the newer driver to take effect.

Now Solved. Thank you bro :)

---

### Post by rob-a-stone on 2014-11-03
Thanks for that tip - it got the bluetooth working perfectly on my Lenovo Y50-70 :)

> **Dinh_Quoc_Han said:**
> Now my bluetooth is working. I try reinstall 
```
sudo apt-get install --reinstall linux-headers-generic build-essential
```
After that, compile and install the driver as follows -
1) Download the latest backported driver package from here - [http://drvbp1.linux-foundation.org/~...tml/backports/]("http://drvbp1.linux-foundation.org/%7Emcgrof/rel-html/backports/")
2) Copy the downloaded tar.bz2 package to your Ubuntu Desktop > Right-click > Extract here.
3) Open a terminal and run the following commands one-by-one 
     ```
cd Desktop/backports-3.18-rc1-1
make defconfig-ath9k
make
sudo make install 
```

4) Reboot for the newer driver to take effect.

Now Solved. Thank you bro :)

---

### Post by furina on 2014-11-21
worked for me. thank you.

---

### Post by lava2 on 2014-11-28
I just attempted this fix. Upon reboot, bluetooth is not fixed and now my wireless doesn't work. Also, while booting I get an error message that says "failed to load module iwldvm". How do I revert back to what I had before?

---

### Post by m.m.shahabi on 2015-09-11
> **lava2 said:**
> I just attempted this fix. Upon reboot, bluetooth is not fixed and now my wireless doesn't work. Also, while booting I get an error message that says "failed to load module iwldvm". How do I revert back to what I had before?

I know it is a bit too late but:

1- Navigate to the backport folder
2- sudo make uninstall
3- sudo reboot

---

### Post by Jaladhi_R_Trivedi on 2015-12-14
install reinstalling linux build essentials works fine

---

### Post by jeremy31 on 2015-12-14
Installing backports for wifi shouldn't affect bluetooth whatsoever.  The original poster likely had a kernel older than 3.16.0-32 where there was a fix for Atheros bluetooth devices as the OP had.  I would strongly advise to not use this and post a new thread regarding bluetooth issues

---

### Post by arjundabra on 2016-09-07
Don't try this my wireless also stopped working after doing this.

---

### Post by howefield on 2016-09-07
Old thread based on Utopic closed.

---

