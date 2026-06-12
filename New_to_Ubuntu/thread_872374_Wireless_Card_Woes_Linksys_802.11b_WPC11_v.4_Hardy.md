---
title: "Wireless Card Woes Linksys 802.11b WPC11 v.4 Hardy Heron"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by gigi1234 on 2008-07-27
For the last two years I was content to run Edgy on my Thinkpad T21. But tonight I got the bug to play again and installed 8.04. Under Dapper and Edgy my Linksys PCI Ethernet Card (802.11b WPC11 v.4) worked great out of the box. But I have a no-go with Hardy Heron and I am a little lost!

I don't even know where to start. Hardy doesn't even seem to have a device list. 

Here is a little output:

iwconfig

lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

And when I do:  sudo lshw -C network
The card seems to be recognized (I can't give the output because I am using a different PCI card for the ethernet at the moment).

Please someone help!

I know nothing about ndiswrapper, etc.

Thanks in advance!

---

### Post by gigi1234 on 2008-07-28
OK I installed ndiswrapper and installed a driver for the wireless card (I had the cd with drivers). Now it seems to be recognized but it still won't connect. 

The device is listed now in Network Manager but when I try to enter my WEP key nothing happens and it won't connect. 

Any ideas???

I am lost!

Why would this setup work perfectly in 6.10 and not in 8.04?

Please, please...help!

---

### Post by gigi1234 on 2008-07-28
Anyone???

BTW my modem is a 2WIRE231 and the wired ethernet connection works fine. 

Please help me figure this issue out. 

Thanks!

---

### Post by Tom--d on 2008-07-28
Try using Wifi-radar in the repos. 

It works with my wireless card. and WEP works aswell. (Network Manager doesnt like my Wireless card and doesnt connect to anything)

If it does connect. 
Uninstall Network Manager
```
sudo apt-get remove network-manager
```

---

### Post by gigi1234 on 2008-07-28
Thanks for the wifi radar tip. I tried it and the network is recognized but it won't let me edit it or anything. I can't enter my WEP key, etc. So I am still stuck. 

I was thinking about going somewhere with a non-secure network to see if I can get online that way-maybe narrow down what is wrong. 

Anyone else have a suggestion???

I am thinking of trying another distro because this is pretty frustrating.

---

### Post by dmizer on 2008-07-30
Please do not create duplicate threads, thread closed.

Duplicate can be found here: [http://ubuntuforums.org/showthread.php?t=873384](http://ubuntuforums.org/showthread.php?t=873384)

---

