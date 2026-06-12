---
title: "no wwan adapter found"
date: 2023-10-13
forum: New to Ubuntu
---

### Post by den-denzel on 2023-10-13
Help solve the problem after switching from Windows to Ubuntu 22.04, I do not have an Internet connection through a SIM card.

---

### Post by grahammechanical on 2023-10-13
Google translate

> To help solve the problem after switching from Windows to Ubuntu 22.04, there is no connection to the Internet via the SIM card.

Regards

---

### Post by den-denzel on 2023-10-13
&#1052;&#1086;&#1078;&#1077;&#1090;&#1077; &#1076;&#1086;&#1087;&#1086;&#1084;&#1086;&#1075;&#1090;&#1080;???

---

### Post by MAFoElffen on 2023-10-13
&#1052;&#1086;&#1078;&#1077;&#1090;&#1077; &#1083;&#1080; &#1074;&#1099; &#1089;&#1086; &#1089;&#1074;&#1086;&#1077;&#1081; &#1089;&#1090;&#1086;&#1088;&#1086;&#1085;&#1099; &#1087;&#1077;&#1088;&#1077;&#1074;&#1077;&#1089;&#1090;&#1080; &#1085;&#1072; &#1072;&#1085;&#1075;&#1083;&#1080;&#1081;&#1089;&#1082;&#1080;&#1081;? &#1069;&#1090;&#1086; &#1072;&#1085;&#1075;&#1083;&#1086;&#1103;&#1079;&#1099;&#1095;&#1085;&#1099;&#1081; &#1092;&#1086;&#1088;&#1091;&#1084;, &#1080; &#1085;&#1080;&#1082;&#1090;&#1086; &#1085;&#1077; &#1079;&#1085;&#1072;&#1077;&#1090;, &#1082;&#1072;&#1082; &#1086;&#1090;&#1074;&#1077;&#1090;&#1080;&#1090;&#1100;. &#1042;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;, &#1090;&#1086;&#1075;&#1076;&#1072; &#1074;&#1099; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1077; &#1086;&#1090;&#1074;&#1077;&#1090;... (&#1063;&#1077;&#1088;&#1077;&#1079; Google-&#1087;&#1077;&#1088;&#1077;&#1074;&#1086;&#1076;&#1095;&#1080;&#1082;.)

---

### Post by MAFoElffen on 2023-10-13
&#1048;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1103;, &#1082;&#1086;&#1090;&#1086;&#1088;&#1091;&#1102; &#1074;&#1072;&#1084; &#1085;&#1091;&#1078;&#1085;&#1086; &#1073;&#1091;&#1076;&#1077;&#1090; &#1087;&#1088;&#1077;&#1076;&#1086;&#1089;&#1090;&#1072;&#1074;&#1080;&#1090;&#1100;, &#8212; &#1101;&#1090;&#1086; &#1084;&#1072;&#1088;&#1082;&#1072; &#1080; &#1084;&#1086;&#1076;&#1077;&#1083;&#1100; &#1085;&#1086;&#1091;&#1090;&#1073;&#1091;&#1082;&#1072;. &#1047;&#1072;&#1090;&#1077;&#1084; &#1086;&#1087;&#1091;&#1073;&#1083;&#1080;&#1082;&#1091;&#1081;&#1090;&#1077; &#1089;&#1090;&#1088;&#1086;&#1082;&#1091; &#1074;&#1099;&#1074;&#1086;&#1076;&#1072; lsusb, &#1075;&#1076;&#1077; &#1085;&#1072;&#1093;&#1086;&#1076;&#1080;&#1090;&#1089;&#1103; &#1074;&#1072;&#1096;&#1072; &#1073;&#1077;&#1089;&#1087;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1072;&#1103; &#1082;&#1072;&#1088;&#1090;&#1072; WWAN, &#1095;&#1090;&#1086;&#1073;&#1099; &#1084;&#1099; &#1079;&#1085;&#1072;&#1083;&#1080; &#1084;&#1086;&#1076;&#1077;&#1083;&#1100; &#1082;&#1072;&#1088;&#1090;&#1099;. &#1055;&#1086;&#1078;&#1072;&#1083;&#1091;&#1081;&#1089;&#1090;&#1072;, &#1088;&#1072;&#1079;&#1084;&#1077;&#1089;&#1090;&#1080;&#1090;&#1077; &#1101;&#1090;&#1086; &#1084;&#1077;&#1078;&#1076;&#1091; &#1090;&#1077;&#1075;&#1072;&#1084;&#1080; CODE &#1074; &#1089;&#1086;&#1086;&#1073;&#1097;&#1077;&#1085;&#1080;&#1080;.

---

### Post by den-denzel on 2023-10-14
OK got it.  My problem is that after switching to Ubuntu 22.04 I cannot connect to the Internet via a SIM card.  laptop model hp 840g1.  lsusb:

Bus 002 Device 003: ID 03f0:521d HP, Inc HP hs3110 HSPA+ Mobile Broadband Device

---

### Post by MAFoElffen on 2023-10-14
I see there was a problem with that Laptop and the WWAN card back a while, where the package that had to be fixed was package  'usb-modeswitch-data'... But that was two versions ago from the version in 22.04.

What does this show?
```

sudo lshw -C Network | grep -A7 -Ei 'whs3110' | grep -E 'product|driver

```

---

### Post by den-denzel on 2023-10-14
grep Ei: no such file or directory
grep whs3110: no such file or directory

---

### Post by MAFoElffen on 2023-10-14
Oh Dang. Sorry. Had a typo.
```

sudo lshw -C Network | grep -A7 -Ei 'hs3110|broadband' | grep -E 'product|driver

```

---

### Post by den-denzel on 2023-10-15
this command also did not produce results.  But I found the usb-modeswitch-data file, there are instructions and an archive that needs to be unpacked, but it doesn’t work there either.
If it helps, here is the log entry:
Code:13:26:44 NetworkManager: <info>  [1696760804.3166] audit: op="radio-control" arg="wwan-enabled:on" pid=2374 uid=1000 result="success"
13:26:44 NetworkManager: <info>  [1696760804.3166] audit: op="radio-control" arg="wwan-enabled:on" pid=2374 uid=1000 result="success"
13:26:44 NetworkManager: <info>  [1696760804.3159] manager: rfkill: WWAN hardware radio set enabled
12:37:51 NetworkManager: <info>  [1696757871.8350] manager: rfkill: WWAN enabled by radio killswitch; disabled by state file
12:37:51 NetworkManager: <info>  [1696757871.8190] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-wwan.so)
12:37:51 NetworkManager: <info>  [1696757871.8124] manager[0x55e016153040]: rfkill: WWAN hardware radio set disabled

---

### Post by den-denzel on 2023-10-15
If it helps, here is the log entry:
Code:13:26:44 NetworkManager: <info>  [1696760804.3166] audit: op="radio-control" arg="wwan-enabled:on" pid=2374 uid=1000 result="success"
13:26:44 NetworkManager: <info>  [1696760804.3166] audit: op="radio-control" arg="wwan-enabled:on" pid=2374 uid=1000 result="success"
13:26:44 NetworkManager: <info>  [1696760804.3159] manager: rfkill: WWAN hardware radio set enabled
12:37:51 NetworkManager: <info>  [1696757871.8350] manager: rfkill: WWAN enabled by radio killswitch; disabled by state file
12:37:51 NetworkManager: <info>  [1696757871.8190] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-wwan.so)
12:37:51 NetworkManager: <info>  [1696757871.8124] manager[0x55e016153040]: rfkill: WWAN hardware radio set disabled

---

### Post by den-denzel on 2023-10-15
13:26:44 NetworkManager: <info>  [1696760804.3166] audit: op="radio-control" arg="wwan-enabled:on" pid=2374 uid=1000 result="success"
13:26:44 NetworkManager: <info>  [1696760804.3166] audit: op="radio-control" arg="wwan-enabled:on" pid=2374 uid=1000 result="success"
13:26:44 NetworkManager: <info>  [1696760804.3159] manager: rfkill: WWAN hardware radio set enabled
12:37:51 NetworkManager: <info>  [1696757871.8350] manager: rfkill: WWAN enabled by radio killswitch; disabled by state file
12:37:51 NetworkManager: <info>  [1696757871.8190] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-wwan.so)
12:37:51 NetworkManager: <info>  [1696757871.8124] manager[0x55e016153040]: rfkill: WWAN hardware radio set disabled
If it helps, here is the log entry

---

### Post by MAFoElffen on 2023-10-15
What does it say if you do
```

nmcli radio wwan on
rfkill list

```

---

### Post by den-denzel on 2023-10-15
rfkill list:

0: phy0: Wireless LAN
  Soft blocked: no
  Hard blocked: no
1: brcmwl-0: Wireless LAN
  Soft blocked: no
  Hard blocked: no
2: hci0: Bluetooth
  Soft blocked: no
  Hard blocked: no

---

### Post by MAFoElffen on 2023-10-15
You are really going to have to start using CODE tags to post raw output, especially for this next one. When you go to Post, Press either "Adv Reply" or "Go Advanced" and it will bring up an editor with the Extended Tool Bar... Select the "#" Icon... That will insert CODE Tags for you to paste the contents of your raw output into.

That last post, I do not see your WWAN card...

Paste the output of this between CODE tags:
```

lsusb -s 002:003 -v

```

---

### Post by MAFoElffen on 2023-10-15
Then do this... Open the grub default file like this
```

sudo nano /etc/default/grub

```
change this line
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
To this
```

GRUB_CMDLINE_LINUX_DEFAULT="--- quiet splash usbserial.vendor=0x0424 usbserial.product=0x2134"

```
Save and Exit. Then run this
```

sudo update-grub

```
Reboot and test again.

---

### Post by den-denzel on 2023-10-15
ok, done.  I can’t figure out how to write code in tags.

---

### Post by #&amp;thj^% on 2023-10-15
> **den-denzel said:**
> ok, done.  I can’t figure out how to write code in tags.

Like this...[noparse]```
 your copied info between like this
```[/noparse]

---

### Post by den-denzel on 2023-10-15
lsusb -s 002:003 -v
```
Bus 002 Device 003: ID 0424:2134 Microchip Technology, Inc. (formerly SMSC) HubCouldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 
  bDeviceProtocol         2 TT per port
  bMaxPacketSize0        64
  idVendor           0x0424 Microchip Technology, Inc. (formerly SMSC)
  idProduct          0x2134 Hub
  bcdDevice           50.00
  iManufacturer           1 SMSC
  iProduct                2 USB2134B
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x0029
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 
      bInterfaceProtocol      1 Single TT
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 
      bInterfaceProtocol      2 TT per port
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12



```

---

### Post by MAFoElffen on 2023-10-15
So the kernel boot parameters changed based on that ouput. LOL. I don't have to guess at that now. Those instructions about should be amended to:
```

GRUB_CMDLINE_LINUX_DEFAULT="--- quiet splash usbserial.vendor=0x0424 usbserial.product=0x2134"

```

---

### Post by den-denzel on 2023-10-16
Ok,done.

---

### Post by MAFoElffen on 2023-10-16
And did you updategrub, then reboot and test it again?

---

### Post by den-denzel on 2023-10-16
As I understand it, it was necessary to make changes to the file and check if the changes were saved, if so, then this has been done

---

### Post by den-denzel on 2023-10-16
lsusb -s 022:003 -v
```
Bus 002 Device 003: ID 0424:2134 Microchip Technology, Inc. (formerly SMSC) HubCouldn't open device, some information will be missing
Device Descriptor:
   bLength 18
   bDescriptorType 1
   bcdUSB 2.10
   bDeviceClass 9 Hub
   bDeviceSubClass 0
   bDeviceProtocol 2 TT &#1076;&#1086; port
   bMaxPacketSize0 64
   idVendor 0x0424 Microchip Technology, Inc. (Formerly SMSC)
   idProduct 0x2134 Hub
   bcdDevice 50.00
   iManufacturer 1 SMSC
   iProduct 2 USB2134B
   iSerial 0
   bNumConfigurations 1
   Configuration Descriptor:
     bLength 9
     bDescriptorType 2
     wTotalLength 0x0029
     bNumInterfaces 1
     bConfigurationValue 1
     iConfiguration 0
     bmAttributes 0xe0
       Self Powered
       Remote Wakeup
     MaxPower 0mA
     Interface Descriptor:
       bLength 9
       bDescriptorType 4
       bInterfaceNumber 0
       bAlternateSetting 0
       bNumEndpoints 1
       bInterfaceClass 9 Hub
       bInterfaceSubClass 0
       bInterfaceProtocol 1 Single TT
       iInterface 0
       Endpoint Descriptor:
         bLength 7
         bDescriptorType 5
         bEndpointAddress 0x81 EP 1 IN
         bmAttributes 3
           Transfer Type Interrupt
           Synch Type None
           Usage Type Data
         wMaxPacketSize 0x0001 1x 1 bytes
         bInterval 12
     Interface Descriptor:
       bLength 9
       bDescriptorType 4
       bInterfaceNumber 0
       bAlternateSetting 1
       bNumEndpoints 1
       bInterfaceClass 9 Hub
       bInterfaceSubClass 0
       bInterfaceProtocol 2 TT &#1076;&#1086; port
       iInterface 0
       Endpoint Descriptor:
         bLength 7
         bDescriptorType 5
         bEndpointAddress 0x81 EP 1 IN
         bmAttributes 3
           Transfer Type Interrupt
           Synch Type None
           Usage Type Data
         wMaxPacketSize 0x0001 1x 1 bytes
         bInterval 12
```

---

### Post by MAFoElffen on 2023-10-16
After the changes were made and saved. Did you do then do 
```

sudo update-grub
sudo reboot

```
Then do
```

rfkill list

```
Then check the logs like you did in Post #12...

---

### Post by den-denzel on 2023-10-16
&#1057;&#1087;&#1080;&#1089;&#1086;&#1082; rfkill 
[&#1050;&#1054;&#1044;]0: phy0: &#1041;&#1077;&#1079;&#1076;&#1088;&#1086;&#1090;&#1086;&#1074;&#1072; &#1083;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072; &#1084;&#1077;&#1088;&#1077;&#1078;&#1072; &#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1085;&#1077; &#1073;&#1083;&#1086;&#1082;&#1091;&#1074;&#1072;&#1085;&#1085;&#1103;: &#1085;&#1110; 
    &#1046;&#1086;&#1088;&#1089;&#1090;&#1082;&#1077; &#1073;&#1083;&#1086;&#1082;&#1091;&#1074;&#1072;&#1085;&#1085;&#1103;: &#1085;&#1110; 
1: hci0: Bluetooth 
    &#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1085;&#1077; &#1073;&#1083;&#1086;&#1082;&#1091;&#1074;&#1072;&#1085;&#1085;&#1103;: &#1085;&#1110; 
    &#1046;&#1086;&#1088;&#1089;&#1090;&#1082;&#1077; &#1073;&#1083;&#1086;&#1082;&#1091;&#1074;&#1072;&#1085;&#1085;&#1103;: &#1085;&#1110; 
2: brcmwl-0: &#1041;&#1077;&#1079;&#1076;&#1088;&#1086;&#1090;&#1086;&#1074;&#1072; &#1083;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072; &#1084;&#1077;&#1088;&#1077;&#1078;&#1072; 
    &#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1085;&#1077; &#1073;&#1083;&#1086;&#1082;&#1091;&#1074;&#1072;&#1085;&#1085;&#1103;: &#1085;&#1110; 
    &#1046;&#1086;&#1088;&#1089;&#1090;&#1082;&#1077; &#1073;&#1083;&#1086;&#1082;&#1091;&#1074;&#1072;&#1085;&#1085;&#1103;: &#1085;&#1110; 


[/ &#1050;&#1054;&#1044;]

---

### Post by den-denzel on 2023-10-16
log messages

```
19:42:41 NetworkManager: <info>  [1697474561.9829] audit: op="radio-control" arg="wwan-enabled:off" pid=4016 uid=1000 result="success"19:42:41 NetworkManager: <info>  [1697474561.9829] audit: op="radio-control" arg="wwan-enabled:off" pid=4016 uid=1000 result="success"
19:42:41 NetworkManager: <info>  [1697474561.9825] manager: rfkill: WWAN hardware radio set disabled
19:42:40 NetworkManager: <info>  [1697474560.9565] audit: op="radio-control" arg="wwan-enabled:on" pid=4016 uid=1000 result="success"
19:42:40 NetworkManager: <info>  [1697474560.9561] manager: rfkill: WWAN hardware radio set enabled
18:56:49 NetworkManager: <info>  [1697471809.3324] audit: op="radio-control" arg="wwan-enabled:off" pid=2744 uid=1000 result="success"
18:56:49 NetworkManager: <info>  [1697471809.3321] manager: rfkill: WWAN hardware radio set disabled
18:56:46 NetworkManager: <info>  [1697471806.5724] audit: op="radio-control" arg="wwan-enabled:on" pid=2744 uid=1000 result="success"
18:56:46 NetworkManager: <info>  [1697471806.5719] manager: rfkill: WWAN hardware radio set enabled
18:56:07 NetworkManager: <info>  [1697471767.0855] manager: rfkill: WWAN enabled by radio killswitch; disabled by state file
18:56:07 NetworkManager: <info>  [1697471767.0667] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-wwan.so)
18:56:07 NetworkManager: <info>  [1697471767.0552] manager[0x5578243ec040]: rfkill: WWAN hardware radio set disabled
```

---

### Post by MAFoElffen on 2023-10-16
Does it work now or is staying disabled? I can see Network Manager addressing it and the plugin loaded... 
```

0667] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-wwan.so)

```
That was new...

But do not understand this one, which is still there:
```

0855] manager: rfkill: WWAN enabled by radio killswitch; [COLOR=#ff0000]disabled by state file[/COLOR]

```

I think at this point,it is being seen and addressed by the system, but for some reason, (if it is still not working) that there is some issue with Network Manager and this device. I think at this point
```

ubuntu-bug network-manager

```
There is still something that is going on there and you need to file a Bug Report so they can check to see what has changed in the code for this to stop working. It worked right? The system now see's it, yet is still not working. Everything seems to be there for it to be able to... Yet it is not.

Please file a link to the Bug Report here in a post, so we can follow it's progress.

---

### Post by den-denzel on 2023-10-16
MESA-INTEL: warning: Haswell Vulkan support is incomplete
libva error: /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so init failed

---

### Post by den-denzel on 2023-10-16
maybe I need to install a driver?  or install a new OS?

---

### Post by MAFoElffen on 2023-10-16
We can now see where the device is recognized and a driver loaded...

I see where "this card" has problems from time to time, not just as being a problem on Ubuntu, but in Linux itself (lots of other distributions" SUSE, Fedora, RedHat). I'm fairly sure it's a regression problem that needs to be addressed.

That, they can find out what is going on, and correct that at Launchpad.

---

### Post by den-denzel on 2023-10-17
ok, thank you, what should I do?

---

### Post by MAFoElffen on 2023-10-17
You might want to read the first post of this first: [https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078)

Then:
```

ubuntu-bug network-manager

```
It will collect the appropriate files and start a bug. You will have to give it a title and describe what is going on.

After it is filed, please copy the link to it here in a post.

---

### Post by den-denzel on 2023-10-17
here is the link, if something is wrong, please correct me. thank you.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/2039592](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/2039592)

---

### Post by jeremy31 on 2023-11-12
Please post results for ```
sudo cat /var/lib/NetworkManager/NetworkManager.state
sudo cat /sys/kernel/debug/usb/devices | awk '/521d/' RS= 
```

---

### Post by den-denzel on 2023-11-12
sudo cat /var/lib/NetworkManager/NetworkManager.state 

```
NetworkingEnabled=trueWirelessEnabled=true 
WWANEnabled=false
``` 

sudo cat /sys/kernel/debug/usb/devices | awk '/521d/' RS= 

```
Bus=02 Lev=01 Prnt=01 Port=05 Cnt=03 Dev#= 4 Spd=480 MxCh= 0D: Ver= 2.00 Cls=ff(vend.) Sub=02 Prot=01 MxPS=64 #Cfgs= 2 
P: Vendor=03f0 ProdID=521d Rev= 0,01 
S: &#1055;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1100;=Hewlett-Packard 
S: &#1055;&#1088;&#1086;&#1076;&#1091;&#1082;&#1090;=HP hs3110 HSPA+ &#1052;&#1086;&#1073;&#1080;&#1083;&#1100;&#1085;&#1086;&#1077; &#1096;&#1080;&#1088;&#1086;&#1082;&#1086;&#1087;&#1086;&#1083;&#1086;&#1089;&#1085;&#1086;&#1077; &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 
C: #Ifs= 6 Cfg#= 1 Atr= a0 MxPwr=500 &#1084;&#1040; 
I: If#= 0 Alt= 0 #EPs= 3 Cls=ff(&#1090;&#1086;&#1088;&#1075;.) Sub=02 Prot=01 Driver= 
E: Ad=81(I) Atr=03(Int.) MxPS= 64 Ivl=2&#1084;&#1089; 
E: Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms 
E: Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms 
I: If#= 1 Alt = 0 #EPs= 2 Cls=ff(&#1074;&#1077;&#1085;&#1076;.) Sub=02 Prot=02 Driver= 
E: Ad=83(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms 
E: Ad=02(O) Atr =02(Bulk) MxPS= 512 Ivl=4ms 
I: If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=03 Driver= 
E: Ad=84(I) Atr=02 (&#1052;&#1072;&#1089;&#1089;&#1086;&#1074;&#1086;&#1077;) MxPS= 512 Ivl=0 &#1084;&#1089; 
E: Ad=03(O) Atr=02(&#1052;&#1072;&#1089;&#1089;&#1086;&#1074;&#1086;&#1077;) MxPS= 512 Ivl=4 &#1084;&#1089; 
I: If#= 3 Alt= 0 #EPs= 3 Cls=0b(scard) Sub= 00 Prot=00 Driver= 
E: Ad=04(O) Atr=02(Bulk) MxPS= 512 Ivl=1&#1084;&#1089; 
E: Ad=85(I) Atr=02(Bulk) MxPS= 512 Ivl=0&#1084;&#1089; 
E: Ad= 86(I) Atr=03(Int.) MxPS= 8 Ivl=1ms 
I: If#= 4 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=02 Prot=07 Driver= 
E: Ad=87 (I) Atr=03(Int.) MxPS= 64 Ivl=2ms 
I: If#= 4 Alt= 1 #EPs= 3 Cls=ff(vend.) Sub=02 Prot=07 Driver= 
E: Ad=87( I) Atr=03(Int.) MxPS= 64 Ivl=2&#1084;&#1089; 
E: Ad=88(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms 
E: Ad=05(O) Atr=02(Bulk) MxPS = 512 Ivl=4ms 
I: If#= 5 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=05 Driver= 
E: Ad=89(I) Atr=02(Bulk) MxPS= 512 Ivl=0&#1084;&#1089; 
E: Ad=06(O) Atr=02(Bulk) MxPS= 512 Ivl=4&#1084;&#1089; 
C: #Ifs= 3 Cfg#= 2 Atr=a0 MxPwr=500&#1084;&#1040; 
A: FirstIf#= 0 IfCount= 2 Cls= 02(&#1089;&#1074;&#1103;&#1079;&#1100;) Sub=0e Prot=00 
I: If#= 0 Alt= 0 #EPs= 1 Cls=02(&#1089;&#1074;&#1103;&#1079;&#1100;) Sub=0e Prot=00 Driver= 
E: Ad=81(I) Atr=03 (&#1042;&#1085;&#1091;&#1090;&#1088;.) MxPS= 64 Ivl=2ms 
I: If#= 1 Alt= 0 #EPs= 0 Cls=0a(data ) Sub=00 Prot=02 Driver= I: 
If#= 1 Alt= 1 #EPs= 2 Cls=0a(&#1076;&#1072;&#1085;&#1085;&#1099;&#1077;) Sub=00 Prot=02 Driver= 
E: Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms 
E: Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=4&#1084;&#1089; 
I: If#= 2 Alt= 0 #EPs= 2 Cls=ff(&#1090;&#1086;&#1088;&#1075;.) Sub=02 Prot=05 Driver= 
E: Ad=83(I) Atr=02(Bulk) MxPS= 512 Ivl =0 &#1084;&#1089; 
E: Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms 



```

---

### Post by jeremy31 on 2023-11-12
Lets try ```
sudo sed -i 's/false/true/' /var/lib/NetworkManager/NetworkManager.state
sudo modprobe option 
echo 03f0 521d | sudo tee /sys/bus/usb-serial/drivers/option1/new_id
```
See if it works

---

### Post by den-denzel on 2023-11-12
after entering the first two commands, there was no output, and after echo the output 03f0 521d

---

### Post by jeremy31 on 2023-11-12
Results for ```
iwconfig; ifconfig
```

---

### Post by den-denzel on 2023-11-12
```
lo        no wireless extensions.

enp0s25   no wireless extensions.


wlo1      IEEE 802.11  ESSID:"ONEPLUS_A5000_co_aptsvo"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 46:B2:B5:7C:68:32   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
enp0s25: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether d0:bf:9c:26:ba:71  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xd0700000-d0720000  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback))
        RX packets 1904  bytes 205552 (205.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1904  bytes 205552 (205.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.43.83  netmask 255.255.255.0  broadcast 192.168.43.255
        inet6 fe80::acdf:bd37:7b49:9823  prefixlen 64  scopeid 0x20<link>
        ether ac:b5:7d:84:26:cb  txqueuelen 1000  (Ethernet)
        RX packets 18998  bytes 9824205 (9.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 4282
        TX packets 16225  bytes 5251509 (5.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 19  



```

---

### Post by jeremy31 on 2023-11-12
Might need to try
```
sudo modprobe usbserial
echo 03f0 521d | sudo tee /sys/bus/usb-serial/drivers/generic/new_id
```
Then check ```
ifconfig
```

---

### Post by den-denzel on 2023-11-12
ifconfig
```
enp0s25: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500        ether d0:bf:9c:26:ba:71  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xd0700000-d0720000  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback))
        RX packets 515  bytes 55231 (55.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 515  bytes 55231 (55.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.43.83  netmask 255.255.255.0  broadcast 192.168.43.255
        inet6 fe80::acdf:bd37:7b49:9823  prefixlen 64  scopeid 0x20<link>
        ether ac:b5:7d:84:26:cb  txqueuelen 1000  (Ethernet)
        RX packets 2206  bytes 1540460 (1.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 115
        TX packets 2230  bytes 469374 (469.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 19  
```

---

### Post by jeremy31 on 2023-11-12
Post results for ```
sudo dmesg | tail -75
```

---

### Post by den-denzel on 2023-11-13
```
[    7.194774] Bluetooth: hci0: BCM: 'brcm/BCM20702A1-0a5c-21f1.hcd'[    7.194779] Bluetooth: hci0: BCM: 'brcm/BCM-0a5c-21f1.hcd'
[    7.207149] RAPL PMU: API unit is 2^-32 Joules, 4 fixed counters, 655360 ms ovfl timer
[    7.207156] RAPL PMU: hw unit of domain pp0-core 2^-14 Joules
[    7.207159] RAPL PMU: hw unit of domain package 2^-14 Joules
[    7.207161] RAPL PMU: hw unit of domain dram 2^-14 Joules
[    7.207163] RAPL PMU: hw unit of domain pp1-gpu 2^-14 Joules
[    7.250149] cryptd: max_cpu_qlen set to 1000
[    7.286155] AVX2 version of gcm_enc/dec engaged.
[    7.286208] AES CTR mode by8 optimization enabled
[    7.297666] wl 0000:02:00.0 wlo1: renamed from wlan0
[    7.338141] snd_hda_intel 0000:00:03.0: enabling device (0000 -> 0002)
[    7.349890] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[    7.360153] audit: type=1400 audit(1699853443.457:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lsb_release" pid=833 comm="apparmor_parser"
[    7.366369] audit: type=1400 audit(1699853443.465:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=842 comm="apparmor_parser"
[    7.366379] audit: type=1400 audit(1699853443.465:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=842 comm="apparmor_parser"
[    7.366387] audit: type=1400 audit(1699853443.465:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=842 comm="apparmor_parser"
[    7.367595] audit: type=1400 audit(1699853443.465:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe" pid=837 comm="apparmor_parser"
[    7.367603] audit: type=1400 audit(1699853443.465:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe//kmod" pid=837 comm="apparmor_parser"
[    7.376904] audit: type=1400 audit(1699853443.477:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="tcpdump" pid=844 comm="apparmor_parser"
[    7.387265] audit: type=1400 audit(1699853443.485:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-oosplash" pid=851 comm="apparmor_parser"
[    7.388186] audit: type=1400 audit(1699853443.485:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=838 comm="apparmor_parser"
[    7.388197] audit: type=1400 audit(1699853443.485:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=838 comm="apparmor_parser"
[    7.412186] [drm] Initialized i915 1.6.0 20201103 for 0000:00:02.0 on minor 0
[    7.423269] ACPI: video: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    7.427639] snd_hda_codec_idt hdaudioC1D0: autoconfig for 92HD91BXX: line_outs=1 (0xa/0x0/0x0/0x0/0x0) type:line
[    7.427649] snd_hda_codec_idt hdaudioC1D0:    speaker_outs=1 (0xd/0x0/0x0/0x0/0x0)
[    7.427653] snd_hda_codec_idt hdaudioC1D0:    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
[    7.427657] snd_hda_codec_idt hdaudioC1D0:    mono: mono_out=0x0
[    7.427660] snd_hda_codec_idt hdaudioC1D0:    inputs:
[    7.427662] snd_hda_codec_idt hdaudioC1D0:      Mic=0xc
[    7.427665] snd_hda_codec_idt hdaudioC1D0:      Internal Mic=0x11
[    7.427668] snd_hda_codec_idt hdaudioC1D0:      Line=0xf
[    7.434762] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input20
[    7.454140] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    7.469857] fbcon: i915drmfb (fb0) is primary device
[    8.603821] Console: switching to colour frame buffer device 200x56
[    8.622746] i915 0000:00:02.0: [drm] fb0: i915drmfb frame buffer device
[    8.681316] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input21
[    8.681430] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input22
[    8.681516] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input23
[    8.690684] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input24
[    8.690776] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input25
[    8.690858] input: HDA Intel PCH Dock Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card1/input26
[    8.690938] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input27
[    8.721306] intel_rapl_common: Found RAPL domain package
[    8.721312] intel_rapl_common: Found RAPL domain core
[    8.721315] intel_rapl_common: Found RAPL domain uncore
[    8.721317] intel_rapl_common: Found RAPL domain dram
[    9.900910] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.900918] Bluetooth: BNEP filters: protocol multicast
[    9.900924] Bluetooth: BNEP socket layer initialized
[    9.903790] Bluetooth: MGMT ver 1.22
[    9.925662] NET: Registered PF_ALG protocol family
[   12.052280] loop23: detected capacity change from 0 to 8
[   13.500610] kauditd_printk_skb: 62 callbacks suppressed
[   13.500615] audit: type=1326 audit(1699853449.597:74): auid=4294967295 uid=0 gid=0 ses=4294967295 subj=snap.modem-manager.modemmanager pid=1199 comm="ModemManager" exe="/snap/modem-manager/541/usr/sbin/ModemManager" sig=0 arch=c000003e syscall=314 compat=0 ip=0x7f0722c6fa3d code=0x50000
[   14.044432] rfkill: input handler disabled
[   34.793126] Bluetooth: RFCOMM TTY layer initialized
[   34.793142] Bluetooth: RFCOMM socket layer initialized
[   34.793151] Bluetooth: RFCOMM ver 1.11
[   34.815007] rfkill: input handler enabled
[   38.301730] rfkill: input handler disabled
[   38.638240] audit: type=1400 audit(1699853474.737:75): apparmor="DENIED" operation="capable" class="cap" profile="/snap/snapd/20290/usr/lib/snapd/snap-confine" pid=2511 comm="snap-confine" capability=12  capname="net_admin"
[   38.638252] audit: type=1400 audit(1699853474.737:76): apparmor="DENIED" operation="capable" class="cap" profile="/snap/snapd/20290/usr/lib/snapd/snap-confine" pid=2511 comm="snap-confine" capability=38  capname="perfmon"
[   43.770618] audit: type=1107 audit(1699853479.869:77): pid=1113 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.3" pid=2511 label="snap.snap-store.ubuntu-software" peer_pid=1124 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
[   43.771023] audit: type=1107 audit(1699853479.869:78): pid=1113 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.3" pid=2511 label="snap.snap-store.ubuntu-software" peer_pid=1124 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
[   43.774254] audit: type=1107 audit(1699853479.873:79): pid=1113 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.3" pid=2511 label="snap.snap-store.ubuntu-software" peer_pid=1124 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
[   43.774692] audit: type=1107 audit(1699853479.873:80): pid=1113 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.3" pid=2511 label="snap.snap-store.ubuntu-software" peer_pid=1124 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
[   44.185421] audit: type=1400 audit(1699853480.285:81): apparmor="DENIED" operation="open" class="file" profile="snap.snap-store.ubuntu-software" name="/etc/appstream.conf" pid=2511 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   55.392402] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready



```

---

### Post by jeremy31 on 2023-11-13
```
cd /etc/usb_modeswitch.d
sudo cp /usr/share/usb_modeswitch/configPack.tar.gz /etc/usb_modeswitch.d/
sudo tar -xvf configPack.tar.gz
```
Reboot, then
```
sudo modprobe usbserial
echo 03f0 521d | sudo tee /sys/bus/usb-serial/drivers/generic/new_id
sudo apt install wvdial
sudo dmesg| tail -75
ifconfig
sudo wvdialconf
```

---

### Post by den-denzel on 2023-11-13
ifconfig
```
enp0s25: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500        ether d0:bf:9c:26:ba:71  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xd0700000-d0720000  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback))
        RX packets 481  bytes 52343 (52.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 481  bytes 52343 (52.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.43.83  netmask 255.255.255.0  broadcast 192.168.43.255
        inet6 fe80::acdf:bd37:7b49:9823  prefixlen 64  scopeid 0x20<link>
        ether ac:b5:7d:84:26:cb  txqueuelen 1000  (Ethernet)
        RX packets 1969  bytes 1578410 (1.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 56
        TX packets 1855  bytes 363153 (363.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 19  



```

---

### Post by den-denzel on 2023-11-13
sudo dmesg| tail -75
```
[   15.503880] snd_hda_intel 0000:00:03.0: enabling device (0000 -> 0002)[   15.504259] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[   15.512191] Console: switching to colour dummy device 80x25
[   15.512275] i915 0000:00:02.0: vgaarb: deactivate vga console
[   15.547998] i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   15.552574] snd_hda_codec_idt hdaudioC1D0: autoconfig for 92HD91BXX: line_outs=1 (0xa/0x0/0x0/0x0/0x0) type:line
[   15.552585] snd_hda_codec_idt hdaudioC1D0:    speaker_outs=1 (0xd/0x0/0x0/0x0/0x0)
[   15.552589] snd_hda_codec_idt hdaudioC1D0:    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
[   15.552593] snd_hda_codec_idt hdaudioC1D0:    mono: mono_out=0x0
[   15.552595] snd_hda_codec_idt hdaudioC1D0:    inputs:
[   15.552599] snd_hda_codec_idt hdaudioC1D0:      Mic=0xc
[   15.552602] snd_hda_codec_idt hdaudioC1D0:      Internal Mic=0x11
[   15.552605] snd_hda_codec_idt hdaudioC1D0:      Line=0xf
[   15.613379] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input17
[   15.613476] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input18
[   15.613567] input: HDA Intel PCH Dock Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card1/input19
[   15.613674] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input20
[   15.731036] [drm] Initialized i915 1.6.0 20201103 for 0000:00:02.0 on minor 0
[   15.734529] ACPI: video: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   15.735050] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input21
[   15.735659] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   15.744213] fbcon: i915drmfb (fb0) is primary device
[   16.009622] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.009626] Bluetooth: BNEP filters: protocol multicast
[   16.009631] Bluetooth: BNEP socket layer initialized
[   16.799062] loop23: detected capacity change from 0 to 8
[   16.889002] Console: switching to colour frame buffer device 200x56
[   16.907958] i915 0000:00:02.0: [drm] fb0: i915drmfb frame buffer device
[   16.931057] Bluetooth: MGMT ver 1.22
[   16.945511] NET: Registered PF_ALG protocol family
[   17.021093] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input22
[   17.024077] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input23
[   17.029523] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input24
[   17.300852] usbcore: registered new interface driver cdc_ether
[   17.325627] usbcore: registered new interface driver cdc_ncm
[   17.342846] usbcore: registered new interface driver cdc_wdm
[   17.366382] usbcore: registered new interface driver cdc_mbim
[   19.823480] kauditd_printk_skb: 61 callbacks suppressed
[   19.823484] audit: type=1326 audit(1699894045.345:73): auid=4294967295 uid=0 gid=0 ses=4294967295 subj=snap.modem-manager.modemmanager pid=1148 comm="ModemManager" exe="/snap/modem-manager/541/usr/sbin/ModemManager" sig=0 arch=c000003e syscall=314 compat=0 ip=0x7f20c73c5a3d code=0x50000
[   21.184773] rfkill: input handler disabled
[   23.221905] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
[   29.399631] audit: type=1400 audit(1699894054.921:74): apparmor="DENIED" operation="capable" class="cap" profile="/snap/snapd/20290/usr/lib/snapd/snap-confine" pid=1863 comm="snap-confine" capability=12  capname="net_admin"
[   29.399650] audit: type=1400 audit(1699894054.921:75): apparmor="DENIED" operation="capable" class="cap" profile="/snap/snapd/20290/usr/lib/snapd/snap-confine" pid=1863 comm="snap-confine" capability=38  capname="perfmon"
[   29.544018] rfkill: input handler enabled
[   30.697314] Bluetooth: RFCOMM TTY layer initialized
[   30.697325] Bluetooth: RFCOMM socket layer initialized
[   30.697333] Bluetooth: RFCOMM ver 1.11
[   32.959827] rfkill: input handler disabled
[   38.684078] audit: type=1107 audit(1699894064.205:76): pid=860 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.3" pid=2459 label="snap.snap-store.ubuntu-software" peer_pid=884 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
[   38.684506] audit: type=1107 audit(1699894064.205:77): pid=860 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.3" pid=2459 label="snap.snap-store.ubuntu-software" peer_pid=884 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
[   38.687248] audit: type=1107 audit(1699894064.209:78): pid=860 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.3" pid=2459 label="snap.snap-store.ubuntu-software" peer_pid=884 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
[   38.687565] audit: type=1107 audit(1699894064.209:79): pid=860 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.3" pid=2459 label="snap.snap-store.ubuntu-software" peer_pid=884 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
[   39.100928] audit: type=1400 audit(1699894064.621:80): apparmor="DENIED" operation="open" class="file" profile="snap.snap-store.ubuntu-software" name="/etc/appstream.conf" pid=2459 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  112.512158] usbcore: registered new interface driver usbserial_generic
[  112.512172] usbserial: USB Serial support registered for generic
[  112.512189] usbserial_generic 2-6:2.0: The "generic" usb-serial driver is only for testing and one-off prototypes.
[  112.512191] usbserial_generic 2-6:2.0: Tell linux-usb@vger.kernel.org to add your device to a proper driver.
[  112.512193] usbserial_generic 2-6:2.0: device has no bulk endpoints
[  112.512205] usbserial_generic 2-6:2.1: The "generic" usb-serial driver is only for testing and one-off prototypes.
[  112.512206] usbserial_generic 2-6:2.1: Tell linux-usb@vger.kernel.org to add your device to a proper driver.
[  112.512207] usbserial_generic 2-6:2.1: device has no bulk endpoints
[  112.512214] usbserial_generic 2-6:2.2: The "generic" usb-serial driver is only for testing and one-off prototypes.
[  112.512216] usbserial_generic 2-6:2.2: Tell linux-usb@vger.kernel.org to add your device to a proper driver.
[  112.512217] usbserial_generic 2-6:2.2: generic converter detected
[  112.512325] usb 2-6: generic converter now attached to ttyUSB0
[  132.134533] usbserial_generic 2-6:2.0: The "generic" usb-serial driver is only for testing and one-off prototypes.
[  132.134556] usbserial_generic 2-6:2.0: Tell linux-usb@vger.kernel.org to add your device to a proper driver.
[  132.134560] usbserial_generic 2-6:2.0: device has no bulk endpoints
[  132.134576] usbserial_generic 2-6:2.1: The "generic" usb-serial driver is only for testing and one-off prototypes.
[  132.134577] usbserial_generic 2-6:2.1: Tell linux-usb@vger.kernel.org to add your device to a proper driver.
[  132.134579] usbserial_generic 2-6:2.1: device has no bulk endpoints



```

---

### Post by den-denzel on 2023-11-13
sudo wvdialconf

```
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.


Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7   
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: Hewlett-Packard
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK


Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"



```

---

### Post by jeremy31 on 2023-11-13
Reboot, then do ```
sudo modprobe usbserial
echo 03f0 521d | sudo tee /sys/bus/usb-serial/drivers/generic/new_id
```
Check WWAN under Network Manager and see if there is something under WWAN

---

### Post by den-denzel on 2023-11-14
no changes in the network manager, but here are the log entries
```
07:39:49 NetworkManager: <info>  [1699940389.1771] audit: op="radio-control" arg="wwan-enabled:off" pid=3399 uid=1000 result="success"07:39:49 NetworkManager: <info>  [1699940389.1771] audit: op="radio-control" arg="wwan-enabled:off" pid=3399 uid=1000 result="success"
07:39:49 NetworkManager: <info>  [1699940389.1768] manager: rfkill: WWAN hardware radio set disabled
07:39:48 NetworkManager: <info>  [1699940388.3601] audit: op="radio-control" arg="wwan-enabled:on" pid=3399 uid=1000 result="success"
07:39:48 NetworkManager: <info>  [1699940388.3596] manager: rfkill: WWAN hardware radio set enabled
07:39:47 NetworkManager: <info>  [1699940387.6181] audit: op="radio-control" arg="wwan-enabled:off" pid=3399 uid=1000 result="success"
07:39:47 NetworkManager: <info>  [1699940387.6177] manager: rfkill: WWAN hardware radio set disabled
07:39:44 NetworkManager: <info>  [1699940384.9054] audit: op="radio-control" arg="wwan-enabled:on" pid=3399 uid=1000 result="success"
07:39:44 NetworkManager: <info>  [1699940384.9050] manager: rfkill: WWAN hardware radio set enabled
07:38:58 NetworkManager: <info>  [1699940338.3297] manager: rfkill: WWAN enabled by radio killswitch; disabled by state file
07:38:58 NetworkManager: <info>  [1699940338.2906] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-wwan.so)
07:38:58 NetworkManager: <info>  [1699940338.2746] manager[0x560614aa3040]: rfkill: WWAN hardware radio set disabled

```

---

### Post by jeremy31 on 2023-11-14
Post results for ```
sudo cat /etc/wvdial.conf
sudo cat /var/lib/NetworkManager/NetworkManager.state 
```

---

### Post by den-denzel on 2023-11-14
sudo cat /etc/wvdial.conf

```
[Dialer Defaults]Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = <Target Phone Number>
ISDN = 0
; Password = <Your Password>
New PPPD = yes
; Username = <Your Login Name>
Modem = /dev/ttyUSB0
Baud = 9600

```

---

### Post by den-denzel on 2023-11-14
sudo cat /var/lib/NetworkManager/NetworkManager.state
```

Manager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false



```

---

### Post by den-denzel on 2023-11-14
sudo cat /var/lib/NetworkManager/NetworkManager.state

this is when the mobile network switch is turned on

```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true



```

---

### Post by jeremy31 on 2023-11-14
Try ```
sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules
```
Scroll down to line 35 or so where you see 
```
# HP hs3110
ATTR{idVendor}=="03f0", ATTR{idProduct}=="521d", RUN+="usb_modeswitch '/%k'"
```
Just below that add ```
ATTR{idVendor}=="03f0", ATTR{idProduct}=="521d", RUN+="/bin/bash -c 'modprobe option && echo 03f0 521d > /sys/bus/usb-serial/drivers/option1/new_id'"
```
Save, exit and reboot, then in terminal ```
wvdial
```
Who is your cell provider?  The wvdial conf file may need that if this doesn't work after a reboot

---

### Post by den-denzel on 2023-11-15
wvdial
```

--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory



```

---

### Post by den-denzel on 2023-11-15
my cellular operator mts

---

### Post by jeremy31 on 2023-11-15
Lets try```
sudo adduser $USER dialout
```
Reboot
```
sudo wvdial
```
```
sudo cat /sys/kernel/debug/usb/devices | awk '/521d/' RS=
```
```
cat /etc/default/grub
```

---

### Post by den-denzel on 2023-11-15
the user is added, and everything else is unchanged, there is no network

---

### Post by den-denzel on 2023-11-15
sudo cat /sys/kernel/debug/usb/devices | awk '/521d/' RS=


```

T:  Bus=02 Lev=01 Prnt=01 Port=05 Cnt=03 Dev#=  4 Spd=480  MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=02 Prot=01 MxPS=64 #Cfgs=  2
P:  Vendor=03f0 ProdID=521d Rev= 0.01
S:  Manufacturer=Hewlett-Packard
S:  Product=HP hs3110 HSPA+ Mobile Broadband Device
C:  #Ifs= 6 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=02 Prot=01 Driver=
E:  Ad=81(I) Atr=03(Int.) MxPS=  64 Ivl=2ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=02 Driver=
E:  Ad=83(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=03 Driver=
E:  Ad=84(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=03(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms
I:  If#= 3 Alt= 0 #EPs= 3 Cls=0b(scard) Sub=00 Prot=00 Driver=
E:  Ad=04(O) Atr=02(Bulk) MxPS= 512 Ivl=1ms
E:  Ad=85(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=86(I) Atr=03(Int.) MxPS=   8 Ivl=1ms
I:  If#= 4 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=02 Prot=07 Driver=
E:  Ad=87(I) Atr=03(Int.) MxPS=  64 Ivl=2ms
I:  If#= 4 Alt= 1 #EPs= 3 Cls=ff(vend.) Sub=02 Prot=07 Driver=
E:  Ad=87(I) Atr=03(Int.) MxPS=  64 Ivl=2ms
E:  Ad=88(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=05(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms
I:  If#= 5 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=05 Driver=
E:  Ad=89(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=06(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms
C:* #Ifs= 3 Cfg#= 2 Atr=a0 MxPwr=500mA
A:  FirstIf#= 0 IfCount= 2 Cls=02(comm.) Sub=0e Prot=00
I:* If#= 0 Alt= 0 #EPs= 1 Cls=02(comm.) Sub=0e Prot=00 Driver=option
E:  Ad=81(I) Atr=03(Int.) MxPS=  64 Ivl=2ms
I:* If#= 1 Alt= 0 #EPs= 0 Cls=0a(data ) Sub=00 Prot=02 Driver=option
I:  If#= 1 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=02 Driver=option
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms
I:* If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=05 Driver=usbserial_generic
E:  Ad=83(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms



```

---

### Post by den-denzel on 2023-11-15
cat /etc/default/grub


```

 If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="--- quiet splash usbserial.vendor=0x03f0 usbserial.product=0x521d"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"





```

---

### Post by jeremy31 on 2023-11-15
Do a ```
sudo gedit /etc/default/grub
```
Change ```
GRUB_CMDLINE_LINUX_DEFAULT="--- quiet splash usbserial.vendor=0x03f0 usbserial.product=0x521d"
```
To ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Save, exit gedit, and reboot
With WWAN enabled, is there any WWAN listing when you click the icon on the top right of the screen that shows you wifi and other options?

---

### Post by den-denzel on 2023-11-16
no, this option was not there from the very beginning, I find it through the search, and it says that no adapter was found

---

### Post by den-denzel on 2023-11-16
and I also noticed that there is no record in the error log, it says that the driver is being loaded, but there is also a record that the radio module is turned off in some file

---

### Post by MAFoElffen on 2023-11-16
Those parameters were from me... Still here watching the progress.

---

### Post by jeremy31 on 2023-11-16
Can you find this screen from settings
[img]https://download.lenovo.com/km/media/images/HT513558/mobile-network_2022071507061289.png[/img]
This is likely where you can enable the WWAN if the driver is working

---

### Post by den-denzel on 2023-11-16
the mobile network option itself is not displayed in the menu, but I can find it when I enter the word sim in the search
and there it is written that wwan adapter not found.

---

### Post by den-denzel on 2023-11-16
can't upload screenshot photo

---

### Post by den-denzel on 2023-11-16
on your screenshot I see different options, I don't have them

---

### Post by jeremy31 on 2023-11-17
Lets try ```
sudo gedit /etc/wvdial.conf
```
Add this below anything that is there
```
[Dialer 3G]
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init5 = AT+CGDCONT=1,"IP"
ISDN = 0
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
Baud = 460800
```
Now save and exit the editor and
```
wvdial 3G
```

---

### Post by den-denzel on 2023-11-17
wvdial 3G
```

--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory



```

---

### Post by den-denzel on 2023-11-17
this message in terminals after the command sudo gedit /etc/wvdial.conf
```

(gedit:3745): dconf-WARNING **: 18:29:57.536: failed to commit changes to dconf: Failed to commit child process "dbus-launch" (No such file or directory)


(gedit:3745): dconf-WARNING **: 18:29:57.542: failed to commit changes to dconf: Failed to commit child process "dbus-launch" (No such file or directory)


(gedit:3745): dconf-WARNING **: 18:29:57.699: failed to commit changes to dconf: Failed to commit child process "dbus-launch" (No such file or directory)


(gedit:3745): dconf-WARNING **: 18:29:57.700: failed to commit changes to dconf: Failed to commit child process "dbus-launch" (No such file or directory)


(gedit:3745): dconf-WARNING **: 18:29:57.700: failed to commit changes to dconf: Failed to commit child process "dbus-launch" (No such file or directory)


** (gedit:3745): WARNING **: 18:30:09.163: Set document metadata failed: Setting metadata::gedit-spell-language attribute is not supported


** (gedit:3745): WARNING **: 18:30:09.164: Set document metadata failed: Setting metadata::gedit-encoding attribute is not supported


** (gedit:3745): WARNING **: 18:30:19.522: Set document metadata failed: Setting metadata::gedit-spell-language attribute is not supported


** (gedit:3745): WARNING **: 18:30:19.523: Set document metadata failed: Setting metadata::gedit-encoding attribute is not supported


** (gedit:3745): WARNING **: 18:30:23.130: Set document metadata failed: Setting the metadata::gedit-position attribute is not supported


(gedit:3745): dconf-WARNING **: 18:30:23.133: failed to commit changes to dconf: Failed to commit child process "dbus-launch" (No such file or directory)

```

---

### Post by jeremy31 on 2023-11-17
What results for ```
sudo cat /sys/kernel/debug/usb/devices | awk '/521d/' RS=
```

---

### Post by den-denzel on 2023-11-17
sudo cat /sys/kernel/debug/usb/devices | awk '/521d/' RS=
```

T:  Bus=02 Lev=01 Prnt=01 Port=05 Cnt=03 Dev#=  4 Spd=480  MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=02 Prot=01 MxPS=64 #Cfgs=  2
P:  Vendor=03f0 ProdID=521d Rev= 0.01
S:  Manufacturer=Hewlett-Packard
S:  Product=HP hs3110 HSPA+ Mobile Broadband Device
C:  #Ifs= 6 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=02 Prot=01 Driver=
E:  Ad=81(I) Atr=03(Int.) MxPS=  64 Ivl=2ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=02 Driver=
E:  Ad=83(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=03 Driver=
E:  Ad=84(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=03(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms
I:  If#= 3 Alt= 0 #EPs= 3 Cls=0b(scard) Sub=00 Prot=00 Driver=
E:  Ad=04(O) Atr=02(Bulk) MxPS= 512 Ivl=1ms
E:  Ad=85(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=86(I) Atr=03(Int.) MxPS=   8 Ivl=1ms
I:  If#= 4 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=02 Prot=07 Driver=
E:  Ad=87(I) Atr=03(Int.) MxPS=  64 Ivl=2ms
I:  If#= 4 Alt= 1 #EPs= 3 Cls=ff(vend.) Sub=02 Prot=07 Driver=
E:  Ad=87(I) Atr=03(Int.) MxPS=  64 Ivl=2ms
E:  Ad=88(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=05(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms
I:  If#= 5 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=05 Driver=
E:  Ad=89(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=06(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms
C:* #Ifs= 3 Cfg#= 2 Atr=a0 MxPwr=500mA
A:  FirstIf#= 0 IfCount= 2 Cls=02(comm.) Sub=0e Prot=00
I:* If#= 0 Alt= 0 #EPs= 1 Cls=02(comm.) Sub=0e Prot=00 Driver=option
E:  Ad=81(I) Atr=03(Int.) MxPS=  64 Ivl=2ms
I:* If#= 1 Alt= 0 #EPs= 0 Cls=0a(data ) Sub=00 Prot=02 Driver=option
I:  If#= 1 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=02 Driver=option
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms
I:* If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=05 Driver=usbserial_generic
E:  Ad=83(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms



```

---

### Post by den-denzel on 2023-11-17
[IMG]&#1092;&#1072;&#1081;&#1083;:///home/denis/%D0%97%D0%BE%D0%B1%D1%80%D0%B0%D0%B6%D0%B5%D0%BD%D0%BD%D1 %8F/%D0%97%D0%BD%D1%96%D0%BC%D0%BA%D0%B8%20%D0%B5%D0%BA%D1%80%D0%B0%D0%BD% D0%B0/%D0%97%D0%BD%D1%96%D0%BC%D0%BE%D0%BA%20%D0%B5%D0%BA%D1%80%D0%B0%D0%BD %D0%B0%20%D0%B7%202023-11-16%2019-12-53.jpg[/IMG]

---

### Post by jeremy31 on 2023-11-17
Can you upload your image to imgur.com or another photo hosting site and post the URL here?

Did you have the device enabled when you got this result
```
--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/ttyUSB0: No such file or directory
```

Does this device work in Windows?

---

### Post by den-denzel on 2023-11-18
[https://ibb.co/V9M5SbZ](https://ibb.co/V9M5SbZ)

---

### Post by den-denzel on 2023-11-18
Yes, it works on Windows, but after installing Ubuntu as the main and only OS on my laptop, this problem arose.
and even on windows, in the absence of a driver, there is an option to select a mobile network, and on ubuntu, I find this setting in the search engine when I write the word sim

---

### Post by jeremy31 on 2023-11-18
Try ```
echo "2" | sudo tee /sys/bus/usb/devices/2-6/bConfigurationValue
```
then try ```
sudo wvdial 3G
```

---

### Post by den-denzel on 2023-11-18
I don't know how it is, but yesterday nothing worked, but today I turned on the laptop to enter your new commands and I see that the network is displayed.
thank you very much for your help.
but it does not work to connect to the Internet, the laptop sees mobile options but cannot establish a connection.

---

### Post by den-denzel on 2023-11-18
but it does not work to connect to the Internet, the laptop sees mobile options but cannot establish a connection.

---

### Post by jeremy31 on 2023-11-18
Edit the /etc/wvdial.conf and go to ```
[Dialer 3G]
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init5 = AT+CGDCONT=1,"IP"
ISDN = 0
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
Baud = 460800
```
Change the ```
Init5 = AT+CGDCONT=1,"IP"
```
to ```
Init5 = AT+CGDCONT=1,"IP","mts"
```
Then run ```
sudo wvdial 3G
```
Reboot

---

### Post by den-denzel on 2023-11-19
sudo wvdial 3G
```

--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory



```

---

### Post by jeremy31 on 2023-11-19
any results for ```
sudo dmesg| grep ttyUSB
```

---

### Post by den-denzel on 2023-11-19
already when the laptop is turned on, the search for the mobile network is automatically turned on, but after half a minute a message appears that there is no connection

---

### Post by den-denzel on 2023-11-19
sudo dmesg| grep ttyUSB
```

[   12.128016] usb 2-6: GSM modem (1-port) converter now attached to ttyUSB0
[   12.128162] usb 2-6: GSM modem (1-port) converter now attached to ttyUSB1
[   12.128299] usb 2-6: GSM modem (1-port) converter now attached to ttyUSB2
[   12.128430] usb 2-6: GSM modem (1-port) converter now attached to ttyUSB3
[   12.128631] usb 2-6: GSM modem (1-port) converter now attached to ttyUSB5
[   15.548218] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[   15.548374] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[   15.548498] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[   15.548612] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[   15.548771] option1 ttyUSB5: GSM modem (1-port) converter now disconnected from ttyUSB5
[   15.676827] usb 2-6: GSM modem (1-port) converter now attached to ttyUSB2



```

---

### Post by jeremy31 on 2023-11-19
Do a ```
sudo dmesg|nc termbin.com 9999
```
Post termbin.com URL from terminal

---

### Post by den-denzel on 2023-11-19
[https://termbin.com/i6zr](https://termbin.com/i6zr)

---

### Post by jeremy31 on 2023-11-19
Can you try that again, results weren't complete

---

### Post by den-denzel on 2023-11-19
[https://termbin.com/laah](https://termbin.com/laah)

---

### Post by jeremy31 on 2023-11-19
According to that, we should
```
sudo sed -i 's/ttyUSB0/ttyUSB2/' /etc/wvdial.conf
sudo wvdial 3G
```

---

### Post by den-denzel on 2023-11-19
sudo wvdial 3G
```

--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
AT+CREG?
+CREG: 2,4
OK
--> Sending: AT+CGDCONT=1,"IP","mts"
AT+CGDCONT=1,"IP","mts"
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

```

---

### Post by jeremy31 on 2023-11-19
Edit the /etc/wvdial.conf and enter this below the Dialer 3G header
```
Phone = *99***1#
Username = " "
Password = " "
```
Save and exit, then ```
sudo wvdial 3G
```

---

### Post by den-denzel on 2023-11-19
sudo wvdial 3G
```

--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","mts"
AT+CGDCONT=1,"IP","mts"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
AT+CREG?
+CREG: 2,4
OK
AT+CGREG?
+CGREG: 2,0
OK
AT+COPS=0
OK
--> Timed out while dialing.  Trying again.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
+CME ERROR: 148
--> Invalid dial command.
--> Disconnecting at Sun Nov 19 16:10:27 2023



```

---

### Post by jeremy31 on 2023-11-19
Edit /etc/wvdial.conf and change
```
Phone = *99***1#
```
to ```
Phone = *99#
```
Then ```
sudo wvdial 3G
```

---

### Post by den-denzel on 2023-11-19
sudo wvdial 3G
```

--> Ignoring malformed input line: "Phon *99#"
--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
AT+CREG?
+CREG: 2,4
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","mts"
AT+CGDCONT=1,"IP","mts"
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.



```

---

### Post by jeremy31 on 2023-11-19
Looks like a typo, it should be Phone = *99#  and not Phon *99#

---

### Post by den-denzel on 2023-11-19
```

--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
AT+CREG?
+CREG: 2,4
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","mts"
AT+CGDCONT=1,"IP","mts"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
+CME ERROR: 148
--> Invalid dial command.
--> Disconnecting at Sun Nov 19 17:23:50 2023

```

---

### Post by den-denzel on 2023-11-19
maybe it will be necessary, this SIM card is a SIM pair of my main card, it is only for the Internet.
the number starts with 095.

---

### Post by jeremy31 on 2023-11-19
You may be able to delete that Phone = *99#
Then try ```
echo "2" | sudo tee /sys/bus/usb/devices/2-6/bConfigurationValue
sudo wvdial 3G
```

---

### Post by den-denzel on 2023-11-19
do i need to remove this number *99# in the file itself /etc/wvdial.conf?

---

### Post by jeremy31 on 2023-11-19
You could try ```
Phone = " "
``` or just delete the line and see what the sudo wvdial 3G does
Does mts have support on the website with APN info?

---

### Post by den-denzel on 2023-11-19
sudo wvdial 3G
```

--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","mts"
OK
--> Modem initialized.
--> Sending: ATDT 
--> Waiting for carrier.
ATDT 
+CME ERROR: 4
--> Invalid dial command.
--> Disconnecting at Sun Nov 19 20:18:50 2023



```

---

### Post by MAFoElffen on 2023-11-19
Just an observation, but I see where that string is usually either "*99#" or "*99***1#"... And you have tried both right?

From something I had in my notes:
```

#!/usr/bin/perl -l
# wvdiald.pl - Auto connect USB modems on Linux
# Author: naveenk <dndkumarasnghe@gmail.com>
# License: MIT
# Make sure you have wvdial and usb-modeswitch installed. Fill the connection parameters below.
# Run this as root. Add "perl /path/to/wvdiald.pl" to /etc/rc.local to make this a service

######################### CHANGE AS NEEDED ################################

# connection parameters
my $MODEM = '/dev/ttyUSB0';     # can be ttyUSB0, ttyUSB1 or ttyUSB2
**[COLOR=#ff0000]my $APN = '';                  # ask your Internet service provider[/COLOR]**
my $USERNAME = 'None';          # ignore if you're not given one
my $PASSWORD = 'None';          # ignore if you're not given one
my $PHONE = '*99#';             # usually *99# or *99***1#
my $BAUD_RATE = 460800;         # modem's communication speed. usually 9600, 57600, 115200 460800 or 760000
my $NOTIFICATION_EMAIL = '';                                            # email to notify when connection is up
my $DEFAULT_INTERNET_INTERFACE = 'ppp0';                        # route Internet through this interface

###########################################################################

# AT commands
my $AT_CMD_1='ATZ';
my $AT_CMD_2='ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0';
my $AT_CMD_3='AT+CGDCONT=1,"IP","' . $APN . '"';

###########################################################################

use threads;
use Sys::Hostname;
use autodie;
my $thr;
$|=1;   # enable immediate STDOUT flushing

sub setDefaultInternetInterface{
    $SIG{'KILL'} = sub { threads->exit(); };
    print "Waiting to default $DEFAULT_INTERNET_INTERFACE...";
    while(system("route add default $DEFAULT_INTERNET_INTERFACE") != 0){ sleep(1);}
    print "$DEFAULT_INTERNET_INTERFACE is now the default Internet interface.";
    system('printf "Subject: $USER@' . hostname . '\nwvdiald.pl: USB modem connected to Internet." | sendmail ' . $EMAIL);
}

# write config
open CONFIGFILE, ">/tmp/wvdial.conf";
print CONFIGFILE "[Dialer Defaults]";
print CONFIGFILE "Modem=$MODEM";
print CONFIGFILE "Phone=$PHONE";
print CONFIGFILE "Username=$USERNAME";
print CONFIGFILE "Password=$PASSWORD";
print CONFIGFILE "Init1=$AT_CMD_1";
print CONFIGFILE "Init2=$AT_CMD_2";
print CONFIGFILE "Init3=$AT_CMD_3";
print CONFIGFILE "Baud=$BAUD_RATE";
print CONFIGFILE "Modem Type=Analog Modem";
print CONFIGFILE "Stupid mode=1";
print CONFIGFILE "Dial Command=ATDT";
print CONFIGFILE "Abort on Busy=yes";
print CONFIGFILE "Dial Attempts=1";
print CONFIGFILE "ISDN=0";
close CONFIGFILE; 

# start wvdial loop
while(1){
        # if modem exists
        if (-e $MODEM){
                # set modem as the default internet when ready
                $thr = threads->create(\&setDefaultInternetInterface);
                print "Dialing modem on $MODEM...";
                system("wvdial --config=/tmp/wvdial.conf");
                $thr->kill('KILL')->join();
                print "Connection failed on $MODEM.";
        }
        sleep(5);
}
```

---

### Post by den-denzel on 2023-11-19
Yes, I tried both options

---

### Post by MAFoElffen on 2023-11-19
Couldn't hurt: You said that your number started with "095"... Lets see what happens if you try "*95***1#" or "*95#".

If wrong, it will just throw another error.

Another would be, since you know your own number, try that instead of the wildcard.

---

### Post by den-denzel on 2023-11-19
I did not say that mts is already vodafone, maybe this is the problem

---

### Post by den-denzel on 2023-11-19
tried to change 99 to 95
it didn't help

---

### Post by den-denzel on 2023-11-19
there are apn settings for Windows on the Vodafone website.

---

### Post by jeremy31 on 2023-11-19
Try ```
sudo sed -i 's/mts/internet.mts.ru/' /etc/wvdial.conf
```
Run the sudo wvdial 3G

---

### Post by MAFoElffen on 2023-11-19
Call Vodaphone and ask for a 4G SIMM Card. 

jeremy31 and I talked about this a few weeks ago, and coincidentally, this was what he was afraid of...

You had mentioned that your SIMM was 3G. Vodaphone announced back in May 2023 that they were switching off legacy compatibility with 3G in their cellular networks in 4th Quarter, which this is the 3rd week of November 2023 (4th Quarter)... So that may be switched off right now in your area.

---

### Post by den-denzel on 2023-11-19
it is possible to change the prefix ru to uk since I live in Ukraine

---

### Post by jeremy31 on 2023-11-19
Try this then ```
sudo sed -i 's/mts/internet/' /etc/wvdial.conf
```

---

### Post by jeremy31 on 2023-11-19
> **MAFoElffen said:**
> Call Vodaphone and ask for a 4G SIMM Card. 

jeremy31 and I talked about this a few weeks ago, and coincidentally, this was what he was afraid of...

You had mentioned that your SIMM was 3G. Vodaphone announced back in May 2023 that they were switching off legacy compatibility with 3G in their cellular networks in 4th Quarter, which this is the 3rd week of November 2023 (4th Quarter)... So that may be switched off right now in your area.

It might take a replacement of the hardware as the device currently being used has been around for 12 years

---

### Post by den-denzel on 2023-11-19
my sim card supports 4g, and the laptop itself only supports 3g, but this did not prevent it from working on windows

---

### Post by den-denzel on 2023-11-19
> **jeremy31 said:**
> &#1055;&#1086;&#1087;&#1088;&#1086;&#1073;&#1091;&#1081;&#1090;&#1077; &#1090;&#1086;&#1075;&#1076;&#1072; ```
sudo sed -i 's/mts/internet/' /etc/wvdial.conf
``` 
sudo wvdial 3G 
```
 
--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
ATQ0
--> Re-Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
--> Sending: ATQ0
ATQ0
--> Re-Sending: AT+CGDCONT=1,"IP","internet"
--> Modem not responding.



```

---

### Post by jeremy31 on 2023-11-19
Try a reboot, then 
```
echo "2" | sudo tee /sys/bus/usb/devices/2-6/bConfigurationValue
sudo wvdial 3G
```

---

### Post by den-denzel on 2023-11-19
> **jeremy31 said:**
> Try a reboot, then 
```
echo "2" | sudo tee /sys/bus/usb/devices/2-6/bConfigurationValue
sudo wvdial 3G
```

```

--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATDT 
--> Waiting for carrier.
ATDT 
+CME ERROR: 4
A
--> Invalid dial command.
--> Disconnecting at Sun Nov 19 22:20:45 2023



```

---

### Post by jeremy31 on 2023-11-19
Might have to put this under the 3G header in wvdial.conf
```
Dial Command = ATD
```
As it doesn't seem to like ATDT

---

### Post by den-denzel on 2023-11-19
> **jeremy31 said:**
> &#1042;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;, &#1087;&#1088;&#1080;&#1076;&#1077;&#1090;&#1089;&#1103; &#1087;&#1086;&#1084;&#1077;&#1089;&#1090;&#1080;&#1090;&#1100; &#1101;&#1090;&#1086; &#1087;&#1086;&#1076; &#1079;&#1072;&#1075;&#1086;&#1083;&#1086;&#1074;&#1082;&#1086;&#1084; 3G &#1074; wvdial.conf 
```
Dial Command = ATD
``` 
&#1058;&#1072;&#1082; &#1082;&#1072;&#1082; ATDT &#1077;&#1084;&#1091; &#1085;&#1077; &#1085;&#1088;&#1072;&#1074;&#1080;&#1090;&#1089;&#1103;
```

--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
--> Sending: ATQ0
ATQ0
--> Re-Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATD 
--> Waiting for carrier.
ATD 
+CME ERROR: 3
--> Invalid dial command.
--> Disconnecting at Sun Nov 19 22:44:19 2023



```

---

### Post by jeremy31 on 2023-11-19
I am thinking we need to put ```
Phone = *99#
```
back in the file under ```
Dial Command = ATD
```
As it doesn't know what to dial
A newer device might work better but that might be tough.  I found one like yours cheap on ebay so I should have one to test tomorrow

---

### Post by MAFoElffen on 2023-11-19
I've still been busy searching for answers... I just found this which might be interesting:
> 
Although, some claim that they were able to get the device working  via the usbserial driver, that won&#8217;t expose the QMI functionality that  the device is capable of. Refer to this [reply 2]("https://www.mail-archive.com/linux-usb@vger.kernel.org/msg45818.html") by Bjorn Mork) with a suggestion to first try

 ```

modprobe qmi_wwan
echo 03f0 521d  /sys/bus/usb/drivers/qmi_wwan/new_id

```
 
[LIST]
[*]some further steps outlined there. It might be that the udev rule  can be changed to reflect the desired configuration, and a recent  ModemManager is required as well. 
[/LIST]


[https://forums.opensuse.org/t/hp-hs3110-hspa-mobile-broadband-module-in-hp-probook-645-g2-not-working/123237/7](https://forums.opensuse.org/t/hp-hs3110-hspa-mobile-broadband-module-in-hp-probook-645-g2-not-working/123237/7)
[https://forums.linuxmint.com/viewtopic.php?t=202487#p1055397](https://forums.linuxmint.com/viewtopic.php?t=202487#p1055397)
```

mafoelffen@Mikes-ThinkPad-T520:~$ find /usr/lib/modules -name qmi_wwan*
/usr/lib/modules/6.2.0-33-generic/kernel/drivers/net/usb/qmi_wwan.ko
/usr/lib/modules/5.15.0-88-generic/kernel/drivers/net/usb/qmi_wwan.ko
/usr/lib/modules/6.2.0-36-generic/kernel/drivers/net/usb/qmi_wwan.ko

```

---

### Post by MAFoElffen on 2023-11-20
@jeremy31 -- What do you think of what is there?

---

### Post by den-denzel on 2023-11-20
> **jeremy31 said:**
> I am thinking we need to put ```
Phone = *99#
```
back in the file under ```
Dial Command = ATD
```
As it doesn't know what to dial
A newer device might work better but that might be tough.  I found one like yours cheap on ebay so I should have one to test tomorrow

```

--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
OK
AT+CREG?
+CREG: 2,4
OK
--> Sending: ATZ
ATZ
AT+CGREG?
+CGREG: 2,0
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATD*99#
--> Waiting for carrier.
AT+CREG?
+CREG: 2,4
OK
AT+CGREG?
+CGREG: 2,0
OK
AT+COPS=0AT+CREG?AT+CGREG?AT+CREG?
+CREG: 2,4
OK
AT+CGREG?
+CGREG: 2,0
OK
AT+COPS=0
OK
--> Timed out while dialing.  Trying again.
--> Sending: ATD*99#
--> Waiting for carrier.
ATD*99#
+CME ERROR: 148
--> Invalid dial command.
--> Disconnecting at Mon Nov 20 07:50:55 2023

```

---

### Post by den-denzel on 2023-11-21
congratulations, I don't understand how this happens, but today I decided to check the network and, miraculously, it works

---

### Post by jeremy31 on 2023-11-21
Good as I finally got my card and adapter today and have had limited luck so far but I just realized I didn't have the antenna connectors attached, so I might try again tomorrow and see if I can make a tutorial somewhere

---

