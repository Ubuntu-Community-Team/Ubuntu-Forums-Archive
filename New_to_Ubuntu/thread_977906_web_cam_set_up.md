---
title: "web cam set up"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by workshop1702 on 2008-11-10
hi i have an unbranded camera its a cheap video cam,web cam,still cam it works ok on windows as a web cam or pc cam i cannot get it to work on ubuntu . it works ok with still pics,when i plug the usb in f-spot opens and i can copy still pics no problem. i cannot get it to work as a web cam or pc cam. 
have installed camorama. when i try this it says error cannot connect to video device (/dev/video0)please check connection.i have also tried it through vlc media player but i cannot find the relavent video and audio files for the camera. anyone any idea how to do this. or any other advice on how to get it going please.

---

### Post by civillian on 2008-11-10
could you specify a brand name or camera model for it?
It makes it easier to help you :)

---

### Post by workshop1702 on 2008-11-10
HI IT JUST HAS GIZMO ON THE BOX its one of those cheap unbtranded items it is virtualy identical in appearance to ebay item 270300746094 there is no make brand or id numbers of any kind on the actual camera at all.hope this may help

---

### Post by w4ett on 2008-11-10
In your terminal type:

```
lsusb
```

And paste the results back here in another post.   This will let us know the ID of the webcam, and if there is a kernel driver available for it.

---

### Post by workshop1702 on 2008-11-10
this is what it says.
andrew@tatung-tablet:~$ lsusb
Bus 008 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 008 Device 003: ID 046e:300f Behavior Tech. Computer Corp. 
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 008: ID 0979:0371 Jeilin Technology Corp., Ltd 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 08ff:5700 AuthenTec, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 001: ID 0000:0000  
andrew@tatung-tablet:~$

---

### Post by w4ett on 2008-11-10
> Bus 007 Device 008: ID 0979:0371 Jeilin Technology Corp., Ltd 

This is the ID of the Camera.  From what I've read from searching on Google, the driver is possibly built into the current kernel.

You might look here: [http://209.85.171.104/translate_c?hl=en&sl=it&u=http://mxhaard.free.fr/spca5xx.html&prev=/search%3Fq%3D0979:0371%2Blinux%26hl%3Den%26rls%3Dcom.microsoft:en-us:IE-SearchBox%26rlz%3D1I7GGLD&usg=ALkJrhgI8yXsy2ywmiEa6Yw9J57XRSg_hA](http://209.85.171.104/translate_c?hl=en&sl=it&u=http://mxhaard.free.fr/spca5xx.html&prev=/search%3Fq%3D0979:0371%2Blinux%26hl%3Den%26rls%3Dcom.microsoft:en-us:IE-SearchBox%26rlz%3D1I7GGLD&usg=ALkJrhgI8yXsy2ywmiEa6Yw9J57XRSg_hA)
to see if that ID number appears.  Also give the Cheese package a try...

---

### Post by workshop1702 on 2008-11-10
ok so what am i looking for exactly , if its biult into the kernal does this mean i dont need a driver and if it is why can i not get it to work please.

---

### Post by alphacrucis2 on 2008-11-10
> **workshop1702 said:**
> ok so what am i looking for exactly , if its biult into the kernal does this mean i dont need a driver and if it is why can i not get it to work please.

Unplug the camera, then plug it back in. Start up a terminal window and type dmesg. Right at the bottom of the dmesg output you should see what was made of your camera and what driver if any was loaded.

---

### Post by workshop1702 on 2008-11-13
HERE IS THE dmesg OUTPUT FROM TERMINAL JUST THE LAST BIT , ITS BEYOND ME ANYONE ANY OTHER IDEAS HOW TO GET THE CAMERA WORKING PLEASE

andrew@tatung-tablet:~$ [45154.309265] sd 4:0:0:1: [sdg] Assuming drive cache: write through
bash: [45154.309265]: command not found
andrew@tatung-tablet:~$ [45154.318259] sd 4:0:0:1: [sdg] 8191 512-byte hardware sectors (4 MB)
bash: syntax error near unexpected token `('
andrew@tatung-tablet:~$ [45154.320503] sd 4:0:0:1: [sdg] Write Protect is off
bash: [45154.320503]: command not found
andrew@tatung-tablet:~$ [45154.320507] sd 4:0:0:1: [sdg] Mode Sense: 00 00 00 00
bash: [45154.320507]: command not found
andrew@tatung-tablet:~$ [45154.320510] sd 4:0:0:1: [sdg] Assuming drive cache: write through
bash: [45154.320510]: command not found
andrew@tatung-tablet:~$ [45154.320515]  sdg: sdg1
bash: [45154.320515]: command not found
andrew@tatung-tablet:~$ [45154.326589] sd 4:0:0:1: [sdg] Attached SCSI removable disk
bash: [45154.326589]: command not found
andrew@tatung-tablet:~$ [45154.326637] sd 4:0:0:1: Attached scsi generic sg7 type 0
bash: [45154.326637]: command not found
andrew@tatung-tablet:~$ andrew@tatung-tablet:~$ 
bash: andrew@tatung-tablet:~$: command not found
andrew@tatung-tablet:~$

---

### Post by UnderMine on 2008-12-30
OK these camera are a bit strange. They have dual mode depending on howyou connect them to the computer. Yeah not nice.

When connected straight we get :-
```

Bus 003 Device 003: ID 0979:0371 Jeilin Technology Corp., Ltd
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0979 Jeilin Technology Corp., Ltd
  idProduct          0x0371
  bcdDevice            1.00
  iManufacturer           1 Jeilin
  iProduct                2 USB 1.1 Device
  iSerial                 3 JL2007BV2000
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              4 SMC CF SD
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0

```
That is the prity straight forward USB mass storage driver so the device should appear as an SD card. I am using Fedora and this works fine for me.

Looking at these details I could not work out the Web Cam part so i read the manual (Yes it's illogical I know). The windows install instructions say to get it to work as a web cam you need to press the shutter release down and hold it while connecting the USB lead.

When I did this the device returned a completely different set of USB info.
```

 Bus 003 Device 004: ID 0979:0270 Jeilin Technology Corp., Ltd
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0979 Jeilin Technology Corp., Ltd
  idProduct          0x0270
  bcdDevice            1.00
  iManufacturer           1 Jeilin
  iProduct                2 USB 1.1 Device
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              4 SMC CF SD
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               0

```
Not sure what this means but it certainly appears to be a new device that is not supported yet.

Hope someone can shed some light on this info. To me it looks like the first part is a repeat of the SD memory card reader EP 1 OUT/EP 2 IN but with an additional device/data stream EP 3 OUT/EP 4 IN

UnderMine

---

