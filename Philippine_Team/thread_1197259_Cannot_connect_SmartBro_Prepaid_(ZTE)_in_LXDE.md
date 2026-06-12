---
title: "Cannot connect SmartBro Prepaid (ZTE) in LXDE"
date: 2009-06-25
forum: Philippine Team
---

### Post by sieg06 on 2009-06-25
im using LXDE under Ubuntu 9.04 the problem is i cannot use my SmartBro Prepaid (ZTE) ung unang issue na usb kit ng Smart.

hindi sya madetect

---

### Post by loell on 2009-06-25
are you using network manager when accessing the modem? when you were still in GNOME?

if so, try to launch **nm-applet** in the terminal when you're in LXDE.

---

### Post by sieg06 on 2009-06-25
hindi na gumagana ang network manager sa lxde. im using wicd. nireinstall ko ang network manager hindi pa din madetect ang network connection ko hinanahanap ko network manager wala din

---

### Post by loell on 2009-06-25
have you executed **wicd** when you first used LXDE, LXDE doesn't automatically add startups that were made in GNOME, you have to add majority of the previous startups.

---

### Post by sieg06 on 2009-06-26
wicd na po ginagamit ko dahil hindi pwede ang network manager ilang beses na ako nagtry. the problem is how can i setup my smartbro prepaid in wicd

---

### Post by loell on 2009-06-26
> **sieg06 said:**
> wicd na po ginagamit ko dahil hindi pwede ang network manager ilang beses na ako nagtry. the problem is how can i setup my smartbro prepaid in wicd

kaya nga tinatanong ko kung na start mo na ba ang **wicd** nung nandoon ka na sa LXDE environment? i would assume nag work na ang wicd at smartbro prepaid mo nung hindi ka pa gumagamit ng LXDE environment?

---

### Post by sieg06 on 2009-06-26
wala di madetect ang smartbro ng wicd sa ubuntu lang.

---

### Post by daxumaming on 2009-06-26
check mo sa likod model no. para alam namin ang link na ipo-post.

---

### Post by sieg06 on 2009-06-28
> **daxumaming said:**
> check mo sa likod model no. para alam namin ang link na ipo-post.


ang model po ng modem:

ZTE Model: Mf622
HSDPA USB Modem

---

### Post by loell on 2009-06-28
from [https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/305968/comments/17]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/305968/comments/17")




**edit [COLOR="Blue"]10-modem.fdi[/COLOR]**

```
sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
```

**then copy paste this**

      ```
<match key="@info.parent:usb.vendor_id" int="0x19d2">
        <!-- Qualcomm: Telstra/NextG CDMA , ZTE CDMA Tech -->
        <match key="@info.parent:usb.product_id" int="0xfffe">
          <match key="@info.parent:usb.interface.number" int="0">
            <append key="modem.command_sets" type="strlist">IS-707-A</append>
          </match>
        </match>
        <!-- ZTE MF628 HSDPA USB dongle -->
        <match key="@info.parent:usb.product_id" int="0x0015">
          <match key="@info.parent:usb.interface.number" int="3">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>
        <!-- ONDA MF632 HSDPA USB dongle -->
        <match key="@info.parent:usb.product_id" int_outof="0x0001;0x0002">
          <match key="@info.parent:usb.interface.number" int="0">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>
      </match>
```

**then delete [COLOR="Blue"]fid.cache[/COLOR]**
```

sudo rm /var/cache/hald/fdi-cache
```
 

[B]then reboot
[/B]

Use wicd or network-manager to connect.

---

### Post by daxumaming on 2009-06-28
ZTE MF622 should work without extra configuration on Jaunty.
[http://ubuntuforums.org/showpost.php?p=6129257&postcount=62](http://ubuntuforums.org/showpost.php?p=6129257&postcount=62)

Here's a few links that'll help you out.
[http://streetsmartingit.blogspot.com/2008/07/how-to-use-smartbro-prepaid-kit-on.html](http://streetsmartingit.blogspot.com/2008/07/how-to-use-smartbro-prepaid-kit-on.html)
[http://ubuntuforums.org/showthread.php?t=665332](http://ubuntuforums.org/showthread.php?t=665332)


@loell
Any howtos on ZTE MF627? I've been trying to get this working for 2 days now. Driver's installed, Jaunty detects it and all, configuration's correct. It simply won't connect.

---

### Post by sieg06 on 2009-06-28
> **daxumaming said:**
> ZTE MF622 should work without extra configuration on Jaunty.
[http://ubuntuforums.org/showpost.php?p=6129257&postcount=62](http://ubuntuforums.org/showpost.php?p=6129257&postcount=62)

Here's a few links that'll help you out.
[http://streetsmartingit.blogspot.com/2008/07/how-to-use-smartbro-prepaid-kit-on.html](http://streetsmartingit.blogspot.com/2008/07/how-to-use-smartbro-prepaid-kit-on.html)
[http://ubuntuforums.org/showthread.php?t=665332](http://ubuntuforums.org/showthread.php?t=665332)


@loell
Any howtos on ZTE MF627? I've been trying to get this working for 2 days now. Driver's installed, Jaunty detects it and all, configuration's correct. It simply won't connect.

bosing ang sinasabi ko po ay connection nya sa LXDE, hindi madetect ng wicd ang smartbro. na isetup ko na ang smartbro before sa jaunty using network manager. but using wicd hindi ko maisetup ang smartbro

---

### Post by loell on 2009-06-29
> **daxumaming said:**
> 
@loell
Any howtos on ZTE MF627? I've been trying to get this working for 2 days now. Driver's installed, Jaunty detects it and all, configuration's correct. It simply won't connect.

searching some launchpad bug entries but i ended up in your blog post instead. :)

ever tried on some windows pc yet?

---

### Post by sieg06 on 2009-06-29
windows pc is ok. ginagamit ko na ubuntu since version 8.10. then ng mag jaunty jackalope i try na rin ang smartbro with network manager its working no need to install and reconfigure. when i install LXDE, network manager is not working in LXDE only WICD can work in LXDE. the reason why i used LXDE jaunty jackalope is not compatible with ASUS A3A laptop with specs of 1.7 ghz and 256 mb ram.

---

### Post by loell on 2009-06-29
> **sieg06 said:**
> windows pc is ok. ginagamit ko na ubuntu since version 8.10. then ng mag jaunty jackalope i try na rin ang smartbro with network manager its working no need to install and reconfigure. when i install LXDE, network manager is not working in LXDE only WICD can work in LXDE. the reason why i used LXDE jaunty jackalope is not compatible with ASUS A3A laptop with specs of 1.7 ghz and 256 mb ram.

oh.. i see, so it's working with network manager.

so just use network manager in LXDE, you have to mannully start network manager in LXDE though,

from the command line ```
nm-applet
```

---

### Post by sieg06 on 2009-06-29
> **loell said:**
> oh.. i see, so it's working with network manager.

so just use network manager in LXDE, you have to mannully start network manager in LXDE though,

from the command line ```
nm-applet
```


thanks for the reply. i'm a newbie here, pero ng iinstall ko ang jaunty sa pc ko, nagreresearch na ako how to use this ubuntu.

---

### Post by loell on 2009-06-29
parang hindi talaga tayo magkaka-intidihan dito eh.. :redface:

review natin ang mga sinabi mo ha?
nung tinanong kita kung na start mo na ang network manager ang sabi mo

> hindi na gumagana ang network manager sa lxde. im using wicd. nireinstall ko ang network manager hindi pa din madetect ang network connection ko **hinanahanap ko network manager wala din**


diba sabi ko, start ang mo network-manager sa LXDE using the command **nm-applet**? or start wicd kung wicd talaga gagamitin mo

pero sinabi mo naman

> wala di madetect ang smartbro ng wicd sa ubuntu lang.

at kalaunan

> then ng mag jaunty jackalope i try na rin ang smartbro with network manager its working no need to install and reconfigure. when i install LXDE, network manager is not working in LXDE only WICD can work in LXDE

ngaun, nasabi mo na nag work pala ang network manager nung hindi ka gumagamit ng LXDE malamang ng gumagamit ka pa nung GNOME sa ubuntu.

so okay, wala palang problem sa detection ng modem, ok pala. kailangan mo lang i-start ang netwrok manager sa LXDE. again sinugest ko na start mo ang **nm-applet** para mag start ang network manager.

pero iba na naman ang sinabi mo.. ;)

> 
i'm a newbie here, pero ng iinstall ko ang jaunty sa pc ko, nagreresearch na ako how to use this ubuntu.

ano naman connection nun sa current problem mo? ;)

heto ha? last question ko, para sa ibang tutulong sayo..

ano palang error ang lumabas nung nag execute ka na nung **nm-applet**, at nasabi mo agad na hindi nag wo-work ang network manager sa LXDE?

---

### Post by daxumaming on 2009-06-29
lOL, kulit e! hehe

> **loell said:**
> searching some launchpad bug entries but i ended up in your blog post instead. :)

right, it detects it and even tries to connect, but ends up getting disconnected as soon as it authenticates.

> **loell said:**
> ever tried on some windows pc yet?

I did, and got great speed as well. I even verified its configuration - I just need to change APN to **SMARTBRO** and method to **PAP** (just **PAP**).

Apparently, _I have to completely shut down my netbook_ (rebooting doesn't work) _and turn it back on with the wifi switched off_ (from the hardware). And it'll connect just fine.

Again, I just hope it improves over time. I'm sure tons of 3 UK and SmartBro users would want native support. 

I'm staring at you Karmic Koala.... yes, staring... yes, you!

---

### Post by johnrizle on 2009-07-01
pwede din ba to sa ubuntu netbook remix?  I mean, tong ZTE is ung bagong smartbro right? So magwwork ba siya if i use it with wicd? kasi sabi sa mga nasearch ko, la pang 3G suport ang wicd.  tnx

---

### Post by killer_d76 on 2009-08-25
pede makigulo :) .. pasensya ha... i have installed **WICD** on my jaunty, and since then my wireless works great!.. now i have a Huwaei USB modem that works flawlessly on **Gnome Network Manager** before, since i have WICD now and during the installation of it, it removed the Gnome Network Manager, now my question is, can I use the WICD to work with my USB (Sun Broadband) modem? and how?.. i have plugged the USB modem on my laptop (jaunty/wicd) but no reaction!, i checked the preferences and I only have wireless and ethernet option but no USB modem?, take note that this USB Modem is working fine and has been detected by Gnome Network Manager thanks guys! ;)

---

### Post by killer_d76 on 2009-08-25
ouch so no 3G support yet on WICD?.. :confused:  i found this link from WICD site about connecting 3G USB modem though i haven't tried it yet!

[http://wicd.sourceforge.net/moinmoin/3GUsbModem](http://wicd.sourceforge.net/moinmoin/3GUsbModem)

ok.. i tested what was indicated on the site but here is what i got!.. and still failed to connect.

> arvin@arvin-laptop:~$ sudo -s
[sudo] password for arvin: 
root@arvin-laptop:~# /usr/sbin/pppd idle 7200 asyncmap 0 updetach 460800 lock crtscts modem /dev/ttyUSB0
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup


here is what i get with **lsusb**

> root@arvin-laptop:~# lsusb
Bus 001 Device 005: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 003: ID 0c45:624f Microdia PC Camera (SN9C201)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

### Post by apolloltiujr on 2010-09-15
Sun, Smart, or Globe Broadband on Ubuntu 10.04


If  you are using Sun Broadband Wireless (tested on Huawei E1550) and want  it to work on Ubuntu 10.04 (Lucid Lynx), just install the  linux-backports-modules-headers-lucid-generic package and the  usb-modeswitch package.view plainprint?   


$ sudo apt-get install linux-backports-modules-headers-lucid-generic usb-modeswitch


After installing, reboot.


Plug  in the Sun Broadband. Then, a notification “New Mobile Broadband  Connection” should appear. Follow the wizard dialog (you can just click  next since the default values should be alright). Then, you should be  connected now.


Connection Name: Digitel (Sun Cellular) Connection


Mobile: *99#
Username:
Password:


Advance 
APN: fbband
Network:
Pin:&#65279;

---

