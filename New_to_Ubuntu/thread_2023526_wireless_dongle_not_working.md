---
title: "wireless dongle not working"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by Kojak Peg on 2012-07-12
I'm trying out lubuntu on my old computer before I install linux on my new computer

I bought the asus wl 167g v3. It is detecting my wireless network but it isn't connecting to the network. I have tried install rtl8192SU but it didn't work

I'm obviously doing something wrong can you please explain it to me in a simple step be step way and remember I'm a compete newbie

I have looked at this site  [http://samiux.blogspot.co.uk/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.co.uk/2010/05/howto-realtek-8192su-usb-dongle.html)

---

### Post by NikTh on 2012-07-12
> **Kojak Peg said:**
> 
It is detecting my wireless network but it isn't connecting to the network.

**Hello and Welcome to UbuntuForums !**
Can you explain this little more ? Is network manager detects networks ? 
Why you not be able to connect ? wrong password ? what happen and you cannot connect ?
Thanks

---

### Post by Kojak Peg on 2012-07-12
Hi NikTh
It is picking up the network but it can't connect and when I enter the password it trys to connect but fail and give me a message saying it is disconnected 

I'm entering the correct password but it doesn't work and when I try to install the linux drivers from the CD is doesn't work. I have downloaded drivers from a website but I don't know what to do. There are no additional drivers either

The problem is me I'm a microsoft user and don't understand linux.

---

### Post by Cheesehead on 2012-07-12
You shouldn't need to install anything - that dongle (if I recall correctly) is already supported.
Normally, if it were really a kernel (driver) issue, nothing would be detected at all. That dongle would power, but simply wouldn't respond at all.

Please open a terminal, try the following commands, copy the results, and paste the results here. 
```
uname -a
lsusb -v
ifconfig -a
```

Have you previously added some kind of security (like MAC filtering or static-IPs-only) to your network that would prevent new hardware from connecting and acquiring an IP address? That happens sometimes.

Have you tried disabling your network security to see if the hardware can then connect? If so, does it connect?

---

### Post by NikTh on 2012-07-12
Hi,
Did you mention that network manager on Lubuntu its a little bit different ? What i mean is , Lubuntu first want administration privileges to let network manager handle your network connection. 
So in case that you didn't mention that ,  **first** you give your user password and then you will be able to give your network password. 

Another think might help ... Open lxterminal and write 
```
sudo nm-connection-editor
``` Network Connections window will open , click on wireless > Add > and try to put your network info (SSID , PASSWD) manualy. 
Then give command
```
sudo service network-manager restart
```See if something corrected.
Thanks

---

### Post by Kojak Peg on 2012-07-12
Hi Cheesehead
I don't think I added any extra security, but I'm a complete newbie to linux so I may have, but don't think so

Please excuse the stupid newbie question, but I don't know how to open a terminal.

---

### Post by Kojak Peg on 2012-07-12
Hi NikTh
I have actually tried doing it both ways. Admin password then isp password and just isp password.

It trys to connect fails and tells me I am disconnected

---

### Post by Kojak Peg on 2012-07-12
Hi Cheesehead
I have two old dongle which are not compatible with linux but lubuntu detected them and the network but the same thing happened it could not connect. That's why I got the new dongle, but the same problem

---

### Post by Kojak Peg on 2012-07-12
Hi everyone
It is working. The caps lock was the problem. when it was turned off it didn't work when I used Shift it didn't work, but in frustration I turned the caps lock on. it gave a warning icon I ignored it and it worked

So the solution was very simple. Turn the caps lock on

However I still don' know how to use the terminal in lubuntu

Many thanks

---

### Post by NikTh on 2012-07-12
> **Kojak Peg said:**
>  but I don't know how to open a terminal.
Hi 
Go to menu (Lubuntu icon down-left on panel) and accessories and lxterminal. 
copy-paste the commands from here to terminal and reverse with results of commands . 
Post results here inside [CODE] tags . Highlight the text and click # symbol on top of message pane.
Thanks

---

### Post by Kojak Peg on 2012-07-12
Hi Nikth
Thanks for all your help. It is all working it turned out that all I had to do was turn on the caps lock

it didn't work in lower case and it didn't work in uppercase using Shift, but it worked with caps lock on

> Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            3.02
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
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
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            3.02
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
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
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255

Bus 001 Device 002: ID 04b4:aefa Cypress Semiconductor Corp. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x04b4 Cypress Semiconductor Corp.
  idProduct          0xaefa 
  bcdDevice            5.50
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10

Bus 002 Device 002: ID 0b05:1791 ASUSTek Computer, Inc. WL-167G v3 802.11n Adapter [Realtek RTL8188SU]
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0b05 ASUSTek Computer, Inc.
  idProduct          0x1791 WL-167G v3 802.11n Adapter [Realtek RTL8188SU]
  bcdDevice            2.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0d  EP 13 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0

Bus 001 Device 003: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0781 SanDisk Corp.
  idProduct          0x5406 Cruzer Micro U3
  bcdDevice            2.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0

---

### Post by NikTh on 2012-07-13
Hi , 
Those are 3 commands , not one. Copy them from here one at time and paste them to your lxterminal and the hit Enter. 
Put the results of each command separately here in forum , inside ```
 tags. Highlight the text and click # symbol on top of message pane (you will see this symbol as you answer to this forum)

> **Cheesehead said:**
> 
[CODE]uname -a
lsusb -v
ifconfig -a
```

> **Kojak Peg said:**
> 
  It is all working it turned out that all I had to do was turn on the caps lock
So problem solved ? it was a problem with caps lock ? i did not exactly understand. Is your WiFi work now ? 
IF YES , the you can mark **thread as solved** from **thread tools**
Thanks

---

### Post by gudcode on 2012-07-13
I dunno if this will help but with my dongel all I had to do was plug it in, open dash/home and then add additional drivers, put the dongel up in there, then just connect in the tool bar...

---

### Post by Kojak Peg on 2012-07-13
Hi Nikth
I did copy it and enter it as you said and that is what happened. I didn't do it three times I only did it once and that was what was generated. I did realise that there was three commands, but I thought since it had generated all of them in one go I sound add them all here in one for you to see

I have also tried installing flash player. In the lxterminal it didn't recognise my admin password as I had typed it in correctly. I did begin install a different way. I can't add code as I'm not on my linux computer at the moment. just thought it may be linked as it failed to recognise two different passwords on two different occasions

thanks for all your help

---

### Post by Kojak Peg on 2012-07-13
Hi Gudcode
Thanks for the suggestion I did try that but there where no additional drives. 

There are obviously still problems but I am now connected to the internet. In desperation I turned the caps lock on, got the ! triangle warning and retyped the password and it connected

THe great thing is it's on an old laptop so I can solve these problems with you guys and mess around until I've learn how to use it then I can install a distro to my computer. I have a pile of them and I'm looking forward to trying them all, but first I what to solve the problems I'm now having and I totally appreciate that one of the problems is me. As I'm not a linux user. yet

Thanks for all of your help

---

### Post by NikTh on 2012-07-13
> **Kojak Peg said:**
> Hi Nikth
I did copy it and enter it as you said and that is what happened. I didn't do it three times I only did it once and that was what was generated. I did realise that there was three commands, but I thought since it had generated all of them in one go I sound add them all here in one for you to see

I have also tried installing flash player. In the lxterminal it didn't recognise my admin password as I had typed it in correctly. I did begin install a different way. I can't add code as I'm not on my linux computer at the moment. just thought it may be linked as it failed to recognise two different passwords on two different occasions

thanks for all your help

Hi , 
you probably didn't know , but lxterminal has a limit of printing  output. The command **lsusb -v** creates a big output and terminal cannot print it full. 
So try to give this commands separately one-by-one 
OR 
configure the lxterminal to print unlimited output. If i remember correct its Edit -> Profile -> Edit -> Scrolling -> and tick Unlimited. 

For password problem , check either keyboard layout or caps lock , cause in terminal password will not be shown (for security reasons). 
Thanks

---

### Post by Kojak Peg on 2012-07-13
Hi Nikth
I don't know. I will give it a go. I'm not on my lubuntu computer so can't try it at the moment

The good thing about all of this is it is giving me a chance to become familiar with linux which was the point of trying it out on an old computer first, and with your help I'm sure I'll crack it eventually

Many thanks

---

