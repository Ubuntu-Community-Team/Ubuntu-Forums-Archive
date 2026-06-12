---
title: "linux noob &lt;------     wifi issues &gt;,&lt;"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by tomwantsthedamnlinux on 2012-09-18
ok. i got an old laptop from a friend and it needed an os. so i went and put ubuntu 12.04 on it. single boot. so it wouldnt let me on the internet, in anyway no connections were available i googled everything troubleshooted a billion different things and nothing helped i did the aptget install crap and it would say command not found and all this crap. so i i found out i need a driver, ok not bad, but i cant get a driver without internet.... cat 5 ethernet? yeah well the ethernet port on the laptop must be busted becasue i tryed 3 different cat 5's and none worked. so i looked some more crap up and someone said, get linux mint cinnamon, it will have the driver. so i uninstalled ubuntu 12.04 and got cinnamon, same issues. then someone said ty ubuntu 10.04 so i go and uninstall mint and get ubntu 10.04    iv yet to connect to the internet and im going on 3 days of trouble shooting and this is becoming a verry bid headache, one of my friends sent me to this website. someone please help me, iv never done linux before and i dont have a win disk to put on the computer.  if possible if someone could shoot me a private message or what ever that would be awesome

---

### Post by Bashing-om on 2012-09-18
tomwantsthedamnlinux;

these links will provide needed guidance.
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections)

That should get you on the track.

---

### Post by tomwantsthedamnlinux on 2012-09-18
> **Bashing-om said:**
> tomwantsthedamnlinux;

these links will provide needed guidance.
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections)

That should get you on the track.

yeah dudei  did all this already none of it works for me idk why. i jsut did all 3 of those links you gave me, none of them gave me wifi  -_- thanks anyway man :/

---

### Post by blade4 on 2012-09-18
What make is your wireless card ?

---

### Post by tomwantsthedamnlinux on 2012-09-18
> **blade4 said:**
> What make is your wireless card ?

Broadcom Corporation BCM4318 (Wireless)

---

### Post by TheMTtakeover on 2012-09-19
Try this?

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers)

---

### Post by Hadaka on 2012-09-19
Hi, try this...broadcom 4318 requires b43 driver

```
sudo apt-get install b43-fwcutter firmware-b43-installer 
```

---

### Post by Scott Harrison on 2012-09-19
Please paste the output of ```
lspci
``` from a command terminal.

Also, did your friend have wireless connectivity before he gave it to you?

---

### Post by rybnik on 2012-09-19
Why not try installing the driver through ndiswrapper?

---

### Post by grahammechanical on 2012-09-19
The links that you were provided contain commands to run as a diagnostic. If you do not include the information that the OS is giving you when you run those commands then we will continue to have no idea as to what the problem is.

This old laptop, does it require the pushing of a combination of keys in order to switch on the wireless adapter in the motherboard?

If you run the command

```
rfkill list
```

What do you see?

On my machine I see:

0: phy0: Wireless LAN
      Softblocked: yes
      Hardblocked: no

I get that message because I am connected by ethernet and I have disabled Wireless connection. So, the Wireless LAN (the wireless adapter on the motherboard) is switched off by software.

If on your system it says Hardblocked: yes, then you need to press a key combination to physically switch the wireless adapter on.

Regards.

P.S. Recognition of wireless adapters or devices is done by the Linux kernel and not by the distribution. So, if Linux does not recognise the wireless adapter (have a built in driver module) then Ubuntu will not be able to use it and neither will any other Linux distributions. So, installing other distributions is not the way to solve these issues.

I doubt very much if an older version of Ubuntu will have drivers that the very latest version does not have. As this laptop is old then there should be a driver module for it and it maybe installed. Running those diagnostic tests will provide that information.

---

### Post by tomwantsthedamnlinux on 2012-09-22
> **rybnik said:**
> Why not try installing the driver through ndiswrapper?

what's ndiswrapper ?

---

### Post by tomwantsthedamnlinux on 2012-09-22
sorry i  took a couple days to reply, i tryed these but all have failed, accept ndiswrapper, i dont know what that is, do i need an internet astablished to get that? because i cannont connect to the internet even wired via cat 5. will ndiswrapper let me do it on my windows desktop put it on a thumb drive and transfer iv=t over ?

---

### Post by rybnik on 2012-10-04
ndiswrapper lets you use windows drivers on a linux system.  Go to a computer that HAS internet, then download both the drivers and the ndiswrapper tarball.  Then on your computer, install ndiswrapper, then install the driver.

---

### Post by DuckHook on 2012-10-04
> **tomwantsthedamnlinux said:**
> Broadcom Corporation BCM4318 (Wireless)
Broadcoms are known to be problematic in Ubuntu. You may need to replace the Broadcom STA module with the older b43 module to make it work. Try using the native Linux module before resorting to ndiswrapper. For instructions and breakdown of possible problem, go to these links:

[http://ubuntuforums.org/showthread.php?t=1890109](http://ubuntuforums.org/showthread.php?t=1890109)
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

Also, it is always worthwhile Googling for similar problems/solutions in the WWW.

---

### Post by rybnik on 2012-10-06
This might not be worth the trouble, but a linux mint install might have it working because that installs proprietary drivers on the fly during the installation.

If you do want to try ndiswrapper, check if it's on the device list:
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:WORKS](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:WORKS)

^There ARE several broadcoms on there.

---

### Post by wildmanne39 on 2012-10-06
Hi, if you have no other drivers installed then please do:

Download the b43 zip file to a flash drive then then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Thanks

---

