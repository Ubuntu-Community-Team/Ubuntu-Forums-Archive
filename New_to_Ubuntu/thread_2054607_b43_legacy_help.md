---
title: "b43 legacy help"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by totaln00 on 2012-09-07
okay I load Ubuntu it says I need to get drivers for wireless card okay look up instructions use lspci -vnn | grep 14e4 command 
 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=223820&d=1347048510[/IMG]



okay need b43legacy got it, instructions say to use 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=223821&d=1347048510[/IMG]

but no files found apparently run a ls and get 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=223822&d=1347048510[/IMG]

okay exactly I need! Try another step the instructions recommend

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=223823&d=1347048510[/IMG]

no luck. Can anyone help me out?

---

### Post by Bachstelze on 2012-09-07
Please provide a link to the instructions that you are following.

---

### Post by NikTh on 2012-09-08
> **Bachstelze said:**
> Please provide a link to the instructions that you are following.

Hi , 

Yes , I want to see that link too. 

Here , I give you another link , more trust-able (I.M.O) : [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) 

Take a look .

Thanks

---

### Post by totaln00 on 2012-09-08
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access) 

I believe this is the same link that NikTh gave me

---

### Post by NikTh on 2012-09-08
> **totaln00 said:**
> [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access) 

I believe this is the same link that NikTh gave me

:lolflag:

Hi , yes exactly the same. 

Where did you stuck ? 

In that link , exited multiple methods to make the wireless work. 

First , what version of Ubuntu you use ? 

Please open a terminal and give the results of bellow commands 

```
cat /etc/lsb-release && uname -r 
iwconfig 
lsmod 
dpkg -l | grep -ie bcm -ie b43
dmesg | grep -ie firm -ie wlan 
lspci -nnk | grep -iA3 net | egrep use
```You can copy-paste the commands from here to your terminal , one line at time. Copy-paste the results back here

_Put the results between ```
 brackets so can be readable. _

**[noparse][code]The Results Here
```[/noparse]**

Thanks

---

### Post by totaln00 on 2012-09-08
> **NikTh said:**
> 

```
cat /etc/lsb-release && uname -r 
iwconfig 
lsmod 
dpkg -l | grep -ie bcm -ie b43
dmesg | grep -ie firm -ie wlan 
lspci -nnk | grep -iA3 net | egrep use
```

I am trying b43 without internet access 
sorry about any misspellings if anything isn't clear let me know

```
 
cat /etc/lsb-release && uname -r
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_COODENAME=precise
DISTRIB_DESCRIPTION="ubuntu 12.04.1 LTS"
3.2.0-29-generic-pae
```

```

iwconfig 
lo         no wireless exensions.

wlan0     IEEE 802.11b ESSID:off/any 
          Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm
          Retry long limit:7  RTS thr: off Fragment thr:off
          Power Management:on

eth0      no wireless extensions


``` 

there's a lot here so I'm just going to copy where I see b43legacy
```

Module           Size   Used by
b43legacy        127187   0
cfg80211         178679   2 b43legacy, mac80211
ssb              50691    1 b43legacy

```

```

dpkg -l | grep -ie bcm -ie b43
ii  libcm-0.2.0                     0.1.0-1
   CMIS protocol client library

```


```

dmesg | grep -ie firm -ie wlan 
[168.009854]b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode2.fw" not found or load failed
[168.009862} b43legacy-phy0 ERROR: you must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3)

```

```

lspci -nnk | grep -iA3 net | egrep use
Kernel driver in use: b43-pci-bridge 
Kernel driver in use: e100

```

---

### Post by NikTh on 2012-09-08
Hello , 

try 

```
sudo apt-get install firmware-b43-installer
sudo apt-get install firmware-b43legacy-installer
```and reboot your PC, without ethernet plugged. 

Thanks

---

### Post by totaln00 on 2012-09-08
> **NikTh said:**
> Hello , 

try 

```
sudo apt-get install firmware-b43-installer
sudo apt-get install firmware-b43legacy-installer
```and reboot your PC, without ethernet plugged. 

Thanks

```

sudo apt-get install firmware-b43-installer
[sudo] password for :
Reading package lists....Done
Building dependency tree
Reading state information...Done
E: Unable to locate package firmware-b43-installer

```

```

sudo apt-get install firmware-b43legacy-installer
[sudo] password for :
Reading package lists....Done
Building dependency tree
Reading state information...Done
E: Unable to locate package firmware-b43legacy-installer

```


no luck :(

---

### Post by NikTh on 2012-09-08
> **totaln00 said:**
> 
no luck :(

Do you have Internet Connection ? via Ethernet . 

You must have an active Internet Connection to install packages. 

Thanks

---

### Post by anewguy on 2012-09-08
Since you don't have wireless yet, just run a hard-wire connection between your PC and the router and run as nikth has recommended.  Once you get those packages installed, disconnect the hard-wire connection and just for the fun of it reboot. ;)

---

### Post by totaln00 on 2012-09-09
Alrighty, I'll let you know how it goes

---

### Post by totaln00 on 2012-09-09
It Worked! had to carry the cpu into the dinning room to connect it but now it's wireless, Thanks for the Help everyone! ):P

---

### Post by tinman6700 on 2012-09-15
having exactly the same problem here, and I followed through the same steps with similar results, but I am connected to the internet and still unable to locate packages. I am running a clean install of jaunty, and I think I have repository problems :(

---

### Post by bkratz on 2012-09-15
> **tinman6700 said:**
> having exactly the same problem here, and I followed through the same steps with similar results, but I am connected to the internet and still unable to locate packages. I am running a clean install of jaunty, and I think I have repository problems :(


 
Jaunty is no longer a supported version, so you would have to change your software sources to old-releases to find any of the files you seek.  See section 4 of

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)


Here is an easier explanation

[http://www.warpconduit.net/2011/07/31/apt-repository-for-old-ubuntu-releases/](http://www.warpconduit.net/2011/07/31/apt-repository-for-old-ubuntu-releases/)

---

### Post by tinman6700 on 2012-09-17
thanks a lot! this computer has been driving me crazy. I'm going to have a chance to try this a little bit later, and I'm thinking that it will, most likely fix both of my problems.

---

### Post by tinman6700 on 2012-09-17
Ok, so I have changed the repositories, and have definately gotten updates, but I am still unable to find firmware-b43-installer. any idea what repository that is in, because it's obviously not on my list

---

