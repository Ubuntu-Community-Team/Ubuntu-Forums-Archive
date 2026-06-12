---
title: "Where's my USB camera mounted at?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by hopelessone on 2008-06-07
Hi,

I can see it in Fspot...but no where else? as fspot is giving me errors importing video files...

Thanks..

---

### Post by cprofitt on 2008-06-07
Hmm... my camera actually mounts as a USB device and automatically mounts as a drive...

did you look under places?

---

### Post by st33med on 2008-06-07
Usually, stuff is mounted at /media.

---

### Post by hopelessone on 2008-06-07
both arn't there? weird that fspot picks it up...

---

### Post by anewguy on 2008-06-08
(1) What kind of camera (brand/model) is it?

(2) What shows on sudo lsusb?

Thanks! :)

---

### Post by hopelessone on 2008-06-08
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 008: ID 040a:05be Kodak Co. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

Kodak EasyShare C763

---

### Post by cariboo on 2008-06-08
Go to Places-->Computer and it should show up there. My Kodak Z700 shows up as **Kodak Z700**

Jim

---

### Post by anewguy on 2008-06-08
Okay, so we know at least the super user can see the device in the usb list (obviously the Bus 004 Device 008: ID 040a:05be Kodak Co.).
 
Does it show if you do a lsusb without the sudo in front?

What does  sudo lsusb -v -d 040a:05be show?

With the camera plugged in, then in a terminal:

sudo ls -al /media


Trying to figure out if this is a permissions problem, a mount problem, etc. I would *assume* that Kodak model would just show as a disk device.  On some Kodak cameras you actually have to go into setup and change it so it looks like a disk device when on USB - some of them default to something I think specific to the Kodak software in Windows (this used to be the case, anyway). :)

---

### Post by hopelessone on 2008-06-08
Hi,

redox@redox-pc:~$ sudo lsusb -v -d 040a:05be
[sudo] password for redox: 

Bus 004 Device 009: ID 040a:05be Kodak Co. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        16
  idVendor           0x040a Kodak Co.
  idProduct          0x05be 
  bcdDevice            1.00
  iManufacturer           1 Eastman Kodak Company
  iProduct                2 KODAK EasyShare C763 Zoom Digital Camera
  iSerial                 3 C76327022367
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         6 Imaging
      bInterfaceSubClass      1 Still Image Capture
      bInterfaceProtocol      1 Picture Transfer Protocol (PIMA 15470)
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
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              16
Device Status:     0x0001
  Self Powered
redox@redox-pc:~$ sudo ls -al /media
total 24
drwxr-xr-x  6 root  root  4096 2008-06-08 09:12 .
drwxr-xr-x 21 root  root  4096 2008-06-06 18:56 ..
lrwxrwxrwx  1 root    999    6 2008-06-06 18:39 cdrom -> cdrom0
drwxr-xr-x  2 root    999 4096 2008-06-06 18:39 cdrom0
-rw-r--r--  1 root  root     0 2008-06-08 09:11 .hal-mtab
drwxr-xr-x  5 redox redox 4096 2008-06-08 09:17 hdd_1
drwxr-xr-x  5 redox redox 4096 2008-06-06 13:15 hdd_2
drwxr-xr-x 21 redox redox 4096 2008-06-08 14:58 hdd_3
redox@redox-pc:~$ 


Thanks..

---

### Post by anewguy on 2008-06-08
What's rather interesting is that I did a Yahoo search on the camera and went to Kodak's pages for it, and it never really shows accessing the camera without using either their printer/dock or using their easyshare software on the PC.  It also did not show anything for set up on the camera to set it as a disk when connected to a PC.  I'll do some more looking and see if I can come up with something for you.

:)

---

### Post by anewguy on 2008-06-08
After doing considerable reading on the web, it turns out there are some cameras which aren't "mountable", meaning you can't just mount them and read the camera as a disk.  There are some things you can do to work around this.  I found this all while searching on the meaning of the information for the transfer protocol on this line output in the latest lsusb I had you do:

bInterfaceProtocol 1 Picture Transfer Protocol (PIMA 15470)

Turns out there are some extra things you can try.  There is an old post from linuxquestions.org that talks about this on another brand of camera.  Forget the top part where someone mentions changing things in udev permissions files (I have to do this with my camcorders, but you shouldn't need to).  Just look at message #6, #7 and #8.  If you're not sure what that all means and what to do, post back and I'll see if I can work you through it.  Be forwarned - never done this myself!  :)

EDIT: I forgot the link!  Here it is:

[http://www.linuxquestions.org/questions/slackware-14/configuring-udev-for-digital-camera-367435/]("http://www.linuxquestions.org/questions/slackware-14/configuring-udev-for-digital-camera-367435/")

---

### Post by anewguy on 2008-06-08
Here's another web page with a different way of doing things - note this is for another Kodak model, but I found all of these types of things worth trying when I have had problems:


[http://linuxgazette.net/148/knaggs.html]("http://linuxgazette.net/148/knaggs.html")

:)

---

