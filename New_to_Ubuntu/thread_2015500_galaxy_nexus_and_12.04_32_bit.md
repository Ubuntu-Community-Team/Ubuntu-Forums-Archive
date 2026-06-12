---
title: "galaxy nexus and 12.04 32 bit"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by philosophking on 2012-07-03
Hi everyone,

I can't mount and transfer files to my galaxy nexus phone. I was able to do it when I had 10.04 LTS version of ubuntu by connecting it as a camera instead of a media device, but with 12.04 LTS version of ubuntu this method does not work.

Nor does installing GMTP which is the main solution that I found through googling. I even tried changing the settings within GMTP so that the download path would be to my home file, which is what some people suggested to do, and it still didn't work.

I am quite a beginner when it comes to Ubuntu -- even though I had 10.04 for a while I am not the most tech-savvy person. But I can certainly help provide any info from my computer that you think might help. Thank you :)

---

### Post by Redblade20XX on 2012-07-03
What version of mtp-tools do you have installed?

With the device connected, type in the terminal
```
mtp-detect
```

and post the output!

-Red

---

### Post by philosophking on 2012-07-03
Thanks for your reply. When I connect as MTP this is what I get:

> dan@dan-computer:~$ mtp-detect
libmtp version: 1.1.3

Listing raw device(s)
Device 0 (VID=04e8 and PID=685c) is a Samsung Galaxy Nexus/Galaxy S i9000/i9250, Android 4.0 updates.
   Found 1 device(s):
   Samsung: Galaxy Nexus/Galaxy S i9000/i9250, Android 4.0 updates (04e8:685c) @ bus 2, dev 5
Attempting to connect device(s)

...and then it doesn't connect.

---

### Post by philosophking on 2012-07-03
After doing research on it I see that it might have something to do with the fact that i have the latest version of libmtp (i.e., 1.1.3) instead of the older one (1.1.2). 

Do you think that's the issue? If that's the case, how can i remove the 1.1.3 and reinstall 1.1.2?

---

### Post by Redblade20XX on 2012-07-03
> **philosophking said:**
> After doing research on it I see that it might have something to do with the fact that i have the latest version of libmtp (i.e., 1.1.3) instead of the older one (1.1.2). 

Do you think that's the issue? If that's the case, how can i remove the 1.1.3 and reinstall 1.1.2?

Most likely it isn't related with the version number. You should contact the libmtp developer's through thier bug tracker to get some feedback. Unless you like to hack it yourself by looking throught their source code. ;)

-Red

---

### Post by lolpenguin on 2012-07-04
I can connect as both a media device and a camera, but on the former it seems to unmount whenever it wants to, and operations are excruciatingly slow, but everything works fine with the camera option.
My libmtp* is 1.1.3

---

### Post by philosophking on 2012-07-05
Hi,

Thanks for your comments. I am getting the following message when I try to access it via MTP through gMTP:

" Failed to get storage parameters from the device"

I read on another forum that there is a simple fix for this. In particular, the following:

"You can just mount phone storage to the file system:
# apt-get install mtp-tools libmtp9 mtpfs
# mtpfs -o allow_other /mnt/**somedir**"

However, I have difficulty here because I don't understand the second step, given my lack of computer knowledge. Can anyone please help me with which "**somedir**" I should be typing in the terminal here? I just don't know what that means. Should I mount it to, literally, "FileSystem" or "home" or what?

Thanks for your help :)

---

### Post by psyclechick on 2012-07-05
Just a guess but I would suggest (after having read a similar repsonse on another site) that **somedir **refers to whatever directory /mnt/xxxxx your Android device is.
 
Similar to when you are looking inside your Android file structure and it will have your sdcard under /mnt/sd-card (or whatever your device calls it - having had Motorola and now HTC they are all different)
 
```
l-usb
``` (rusty here hope thats correct if not someone can confirm or deny!)
 
should give you the output of the USB devices attached to Ubuntu and there you *should *find your phone.
 
Good luck :)

---

### Post by philosophking on 2012-07-05
Hi,

It's lsusb. When I type lsusb -v into the terminal I get the following code. Where here do I find what I need to put after the /mnt/_____ (see my previous post)? 

thanks for your help so far!!

> Bus 002 Device 004: ID 04e8:685c Samsung Electronics Co., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04e8 Samsung Electronics Co., Ltd
  idProduct          0x685c 
  bcdDevice            2.16
  iManufacturer           2 samsung
  iProduct                3 Galaxy
  iSerial                 4 01498FC01800B010
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
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
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol      0 
      iInterface              1 MTP
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x001c  1x 28 bytes
        bInterval               6
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

---

### Post by Redblade20XX on 2012-07-06
> **philosophking said:**
> Hi,

It's lsusb. When I type lsusb -v into the terminal I get the following code. Where here do I find what I need to put after the /mnt/_____ (see my previous post)? 

thanks for your help so far!!

Can you post the link to the site that gave you that info because from what you've posted it could be looking for a mount point or creating a mount point?

-Red

---

### Post by gandaran on 2012-07-06
> **philosophking said:**
> Hi,

Thanks for your comments. I am getting the following message when I try to access it via MTP through gMTP:

" Failed to get storage parameters from the device"

I read on another forum that there is a simple fix for this. In particular, the following:

"You can just mount phone storage to the file system:
# apt-get install mtp-tools libmtp9 mtpfs
# mtpfs -o allow_other /mnt/**somedir**"

However, I have difficulty here because I don't understand the second step, given my lack of computer knowledge. Can anyone please help me with which "**somedir**" I should be typing in the terminal here? I just don't know what that means. Should I mount it to, literally, "FileSystem" or "home" or what?

Thanks for your help :)
# mtpfs -o allow_other **/mnt/somedir**" for the somedir directory create a folder on the root file system **/mnt**, name the folder anything you like, Android or Nexus is a good name choice then replace **somedir** on the mtpfs mount command with the real folder mount name and remember here you are dealing with the root file system where you will need to use sudo every-time, alternately you can mount the phone storage on any other root directory like /media or even on your home directory if mtpfs command allows it where there is no need for root sudo use.

---

### Post by psyclechick on 2012-07-06
> **Redblade20XX said:**
> Can you post the link to the site that gave you that info because from what you've posted it could be looking for a mount point or creating a mount point?
 
-Red
 
This!
 
Thats what I meant...bit rusty with Ubuntu at the moment though
 
/mnt/somedir with somedir being the mount point of your phone on ubuntu 
 
Can you connect the phone just as usb mass storage?

---

### Post by philosophking on 2012-07-16
I've tried connecting the phone as mass storage with no success

Now i'm having a simple problem of creating a file in my mnt folder. can someone please walk me through that step? everytime I try to enter into the mnt folder by typing "cd /home/mnt" it does not work.

By the way, I also tried looking on Android forums for this with no luck. Thanks for your help!

---

### Post by philosophking on 2012-07-16
Ok, something seems to be wrong here and I am just getting more confused.

My origiinal problem was accessing my files on my Nexus. I'm running 12.04.

I tried connecting as both camera and media device. Neither thing worked. Then I tried entering USB debugging and tried that. Again, nothing worked.

Then I learned about gMTP. I tried installing that with the relevant files. Then I tried accessing it. Still, didn't work. I tried at that point to get it to simply find the files on my computer (since it is technically mounted). I can't find them anywhere!

I'm really at a loss. Has anyone else encountered this issue?

---

### Post by Redblade20XX on 2012-07-16
> **philosophking said:**
> I've tried connecting the phone as mass storage with no success

Now i'm having a simple problem of creating a file in my mnt folder. can someone please walk me through that step? everytime I try to enter into the mnt folder by typing "cd /home/mnt" it does not work.

By the way, I also tried looking on Android forums for this with no luck. Thanks for your help!

Usually mnt is located in the root.
```
cd /mnt
```As for the other stuff, I don't really know. Have you tried connecting it in Windows?

- Red

---

### Post by TenPlus1 on 2012-07-16
I switched the nexus phone to Camera mode which connected and mounted in Ubuntu to show a photos directory, then on the phone switched to MTP mode while still connected and it somehow mounted correctly and let me use all available directories on the phone read and write...

---

### Post by janz84 on 2012-07-23
I had a similiar issue too, but was able to get a connection after enabling usb debugging 
settings - > developer options -> usb debugging.

Bear in mind this is on a wubi installed 12.04 64 bit ubuntu and a jelly bean version of bugless beast rom (7/19/12). 

```

jan@ubuntu:~$ mtp-detect
libmtp version: 1.1.3

Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung GT-P7310/P7510/N7000/I9100/Galaxy Tab 7.7/10.1/S2/Nexus/Note.
   Found 1 device(s):
   Samsung: GT-P7310/P7510/N7000/I9100/Galaxy Tab 7.7/10.1/S2/Nexus/Note (04e8:6860) @ bus 1, dev 8
Attempting to connect device(s)
Android device detected, assigning default bug flags
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
Reading in zero packet after header
USB low-level info:
   Interface has a kernel driver attached.
   bcdUSB: 512
   bDeviceClass: 0
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 04e8
   idProduct: 6860
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Raw device info:
      Bus location: 1
      Device number: 8
      Device entry info:
         Vendor: Samsung
         Vendor id: 0x04e8
         Product: GT-P7310/P7510/N7000/I9100/Galaxy Tab 7.7/10.1/S2/Nexus/Note
         Vendor id: 0x6860
         Device flags: 0x48008107
Configuration 0, interface 0, altsetting 0:
   Interface description contains the string "MTP"
   Device recognized as MTP, no further probing.
Device info:
   Manufacturer: samsung
   Model: Galaxy Nexus
   Device version: 1.0
   Serial number: 01498F370300E006
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0; android.com: 1.0;
   Detected object size: 64 bits
   Extensions:
        microsoft.com: 1.0
        android.com: 1.0
Supported operations:
   1001: get device info
   1002: Open session
   1003: Close session
   1004: Get storage IDs
   1005: Get storage info
   1006: Get number of objects
   1007: Get object handles
   1008: Get object info
   1009: Get object
   100a: Get thumbnail
   100b: Delete object
   100c: Send object info
   100d: Send object
   1014: Get device property description
   1015: Get device property value
   1016: Set device property value
   1017: Reset device property value
   101b: Get partial object
   9801: Get object properties supported
   9802: Get object property description
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9810: Get object references
   9811: Set object references
   95c1: Unknown (95c1)
   95c2: Unknown (95c2)
   95c3: Unknown (95c3)
   95c4: Unknown (95c4)
   95c5: Unknown (95c5)
Events supported:
   0x4002
   0x4003
   0x4004
   0x4005
Device Properties Supported:
   0xd401: Synchronization Partner
   0xd402: Friendly Device Name
   0x5003: Image Size
Playable File (Object) Types and Object Properties Supported:
   3000: Undefined Type
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
   3001: Association/Directory
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
   3004: Text
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
   3005: HTML
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
   3008: MS Wave
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
      dc46: Artist STRING data type READ ONLY
      dc9a: Album Name STRING data type READ ONLY
      dc9b: Album Artist STRING data type READ ONLY
      dc8b: Track UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc99: Original Release Date STRING data type DATETIME FORM READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc8c: Genre STRING data type READ ONLY
      dc96: Composer STRING data type READ ONLY
   3009: MP3
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
      dc46: Artist STRING data type READ ONLY
      dc9a: Album Name STRING data type READ ONLY
      dc9b: Album Artist STRING data type READ ONLY
      dc8b: Track UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc99: Original Release Date STRING data type DATETIME FORM READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc8c: Genre STRING data type READ ONLY
      dc96: Composer STRING data type READ ONLY
   300b: MPEG
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
      dc46: Artist STRING data type READ ONLY
      dc9a: Album Name STRING data type READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc48: Description STRING data type READ ONLY
   3801: JPEG
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
      dc48: Description STRING data type READ ONLY
   3802: TIFF EP
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
   3807: GIF
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
      dc48: Description STRING data type READ ONLY
   3808: JFIF
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
   380b: PNG
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
      dc48: Description STRING data type READ ONLY
   380d: TIFF
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
   b901: WMA
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
      dc46: Artist STRING data type READ ONLY
      dc9a: Album Name STRING data type READ ONLY
      dc9b: Album Artist STRING data type READ ONLY
      dc8b: Track UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc99: Original Release Date STRING data type DATETIME FORM READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc8c: Genre STRING data type READ ONLY
      dc96: Composer STRING data type READ ONLY
   b902: OGG
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
      dc46: Artist STRING data type READ ONLY
      dc9a: Album Name STRING data type READ ONLY
      dc9b: Album Artist STRING data type READ ONLY
      dc8b: Track UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc99: Original Release Date STRING data type DATETIME FORM READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc8c: Genre STRING data type READ ONLY
      dc96: Composer STRING data type READ ONLY
   b903: AAC
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
      dc46: Artist STRING data type READ ONLY
      dc9a: Album Name STRING data type READ ONLY
      dc9b: Album Artist STRING data type READ ONLY
      dc8b: Track UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc99: Original Release Date STRING data type DATETIME FORM READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc8c: Genre STRING data type READ ONLY
      dc96: Composer STRING data type READ ONLY
   b982: MP4
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
   b983: MP2
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
   b984: 3GP
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dce0: Display Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
      dc46: Artist STRING data type READ ONLY
      dc9a: Album Name STRING data type READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc48: Description STRING data type READ ONLY
   ba05: Abstract Audio Video Playlist
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
   ba10: WPL Playlist
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
   ba11: M3U Playlist
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
   ba14: PLS Playlist
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
   ba82: XMLDocument
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
   b906: FLAC
      dc01: Storage ID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: Object Format UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc03: Protection Status UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: Object Size UINT64 data type READ ONLY
      dc07: Object File Name STRING data type GET/SET
      dc09: Date Modified STRING data type DATETIME FORM READ ONLY
      dc0b: Parent Object UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: Persistant Unique Object Identifier UINT128 data type READ ONLY
      dc44: Name STRING data type READ ONLY
      dc4e: Date Added STRING data type DATETIME FORM READ ONLY
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003 fixed RAM storage
      FilesystemType: 0x0002 generic hierarchical
      AccessCapability: 0x0000 read/write
      MaxCapacity: 30209540096
      FreeSpaceInBytes: 5017882524
      FreeSpaceInObjects: 1073741824
      StorageDescription: Internal storage
      VolumeIdentifier: (null)
Special directories:
   Default music folder: 0x00000004
   Default playlist folder: 0xffffffff
   Default picture folder: 0x00000792
   Default video folder: 0xffffffff
   Default organizer folder: 0xffffffff
   Default zencast folder: 0xffffffff
   Default album folder: 0xffffffff
   Default text folder: 0xffffffff
MTP-specific device properties:
   Friendly name: (NULL)
   Synchronization partner: (NULL)
libmtp supported (playable) filetypes:
   Folder
   Text file
   HTML file
   RIFF WAVE file
   ISO MPEG-1 Audio Layer 3
   MPEG video stream
   JPEG file
   GIF bitmap file
   JFIF file
   Portable Network Graphics
   TIFF bitmap file
   Microsoft Windows Media Audio
   Ogg container format
   Advanced Audio Coding (AAC)/MPEG-2 Part 7/MPEG-4 Part 3
   MPEG-4 Part 14 Container Format (Audio+Video Emphasis)
   ISO MPEG-1 Audio Layer 2
   Abstract Playlist file
   XML file
   Free Lossless Audio Codec (FLAC)
OK.


```

It's slow but I can access my files this way.

---

### Post by Chew N Tobacca on 2012-12-03
I would like to post my findings on this topic, since I ran into the same issue with my Galaxy Nexus running Android 4.1 and Kubuntu 12.04. At first I could connect using gMTP, but actions were limited before I got the error and forced disconnect. After a decent bit of research, I was finally able to use this program to move any and all files to and from my device. After installing gMTP, I also installed the following packages: libusb-dev, mtp-tools, libmtp9, mtpfs. I could then move files/folders TO the device, but would force disconnect after one action. Then after enabling USB debugging mode as mentioned by janz84, everything works perfectly, and have not ran into the same issue since. I hope this helps anyone with similar complications.

---

### Post by techvish81 on 2012-12-03
i have tried all the things mentioned here and there and the easiest method to transfer files easily with reasonable speed is using "**airdroid" **,    install it on your nexus phone and follow the instructions in the app. only three steps to do it.

install airdroid and start wifi-tethering hotspot on your phone and connect your pc to it.   open a browser (preferably chromium) on your pc ,  visit web.airdroid.com in it and insert the passcode from the airdroid screen on your phone. 

now you can transfer anything to and fro.

cheers!!

---

### Post by pixideps on 2012-12-14
I have similar problem but even after searching web and forums cannot find answer. Namely I have htc one x and after jb update whenever I connect phone to ubuntu (usb connection) I cannot access entire phone storage. Namely, upon the connection there is no more choice whether I want just to charge or use phone as disk drive etc. Phone is instantly mounted as media player device. Regarding phone storage there are two partitions; internal and "virtual sd card" (which is bigger). When connected to win seems that bigger partition is mounted (25 GB available) but connected to ubuntu (both 12.04 and 10.04 that I use) I see just 2 GB of available storage space. 
Before this jb update - ie with ICS - everything worked fine ..
Anyone with similar experience?

---

### Post by BigFatTony on 2012-12-19
use this great script / ppa:
[http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html]("http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html")
worked for me, my ubuntu 12.10 and my one x on Jelly Bean 4.1.1.
it updates libmtp, adds an unity-mount-unmount-launcherscript and go-mtpfs. (had to reboot)

now it's fast and stable.

---

