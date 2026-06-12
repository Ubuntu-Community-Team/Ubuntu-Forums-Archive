---
title: "HOWTO: Compile em28xx in Intrepid"
date: 2009-02-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Nickedynick on 2009-02-12
This is my first howto, so use with caution, but this process worked for me so I thought I'd share. There seem to be loads of solutions to this problem in other languages (I got this one from an Italian [site]("http://www.quadrantegamma.it/component/content/article/12-intrepid/60-pinnacle-pctv-usb-stick-dvb-t.html")), but I'm yet to find one in English.

Credit to **gborzi** for pointing me towards the solution :)


Right, straight into it then! You're going to need a few packages to start with:
```
sudo apt-get install linux-source mercurial libxine1-ffmpeg dvb-utils kaffeine
```

Linux-source is a large file, so be patient. After this, we need to extract the source.
```
cd /usr/src
sudo tar -xvf linux-source*.tar.bz2
```

A few files need to be copied to Linux headers.
```
sudo cp -v linux-source-2.6.27/drivers/media/dvb/dvb-core/*.h linux-headers-$(uname -r)/drivers/media/dvb/dvb-core/

sudo cp -v linux-source-2.6.27/drivers/media/dvb/frontends/lgdt330x.h linux-headers-$(uname -r)/drivers/media/dvb/frontends/

sudo cp -v linux-source-2.6.27/drivers/media/video/msp3400-driver.h linux-headers-$(uname -r)/drivers/media/dvb/frontends/
```

We then go back to the home directory and download the drivers needed with Mercurial.
```
cd
hg clone http://mcentral.de/hg/~mrec/em28xx-new
```

Finally, go to the directory where the drivers were downloaded to and build them.
```
cd em28xx-new
sudo ./build.sh build && sudo ./build.sh install
```

All that remains is to reboot and open Kaffeine to start watching!

If it doesn't work immediately, try the following line and open Kaffeine again:
```
sudo modprobe em28xx
```

Let me know if it works for you :)

Edit: I've just tested this in Jaunty Alpha 6 - not working so far...

---

### Post by johnjohn2 on 2009-02-12
Thanks but this needs to be moved.

---

### Post by gborzi on 2009-02-12
Hello Nickedynick,
there is a small error in the HOWTO, the first "sudo cp" line should read > sudo cp -v linux-source-2.6.27/drivers/media/dvb/dvb-core/*.h linux-headers-$(uname -r)/drivers/media/dvb/dvb-core/
please fix it.
Also, I think it could be useful to mention the [w_scan]("http://edafe.org/vdr/w_scan/") program, it's a DVB channel scanner that doesn't require region-specific initial transponder data, like kaffeine.

Regards.

---

### Post by Nickedynick on 2009-02-12
Oops, quite an oversight - thanks! It's fixed now.

I'm not familiar with w_scan, but I'll have a look and update again soon.

How can I get this moved to a tutorials secion?

---

### Post by gborzi on 2009-02-12
I don't know how to move to another section, I think you have to ask to a mod. BTW, w_scan is a CLI program, after compiling it, you may use it as follows
> ./w_scan -X > channels.conf
to have a channel file for mplayer/xine/totem/me-tv/vlc and perhaps others. It has other options and can generate a channel file for kaffeine.

---

### Post by 010878 on 2009-02-21
Finally, I'm able to use my TV Tuner on Linux. But unfortunately there's no sound whenever I try to play in TVTime. Is there any suggestion perhaps ?

---

### Post by gborzi on 2009-02-22
The problem with tvtime sound, like other analog tv programs, can be solved using sox to redirect the sound. I use this script to start tvtime
```
#!/bin/sh

padsp sox -r 48000 -w -v 1 -c 2 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp &
tvtime
killall sox
```
You need to install sox for the above script to work.

Regards.

---

### Post by gridsleep on 2009-02-24
I get:

sox soxio: Can't open input file '/dev/dsp1/: unknown file type 'ossdsp'

Video runs fine in tvtime after running "modprobe tuner", although it is slightly choppy, especially if some other program is occupying the screen or the mouse is moved.  Audio does not come through at all, and apparently sox is looking for something that doesn't exist in my GNU/Linux.  Is that /dev/dsp1 supposed to be the audio from the Hauppauge card?  Apparently my card has a different designator.

I can't understand why this has to be more difficult than it is.  If Windows TV viewing programs can catch the video and the audio, why can't Linux TV viewing programs?

---

### Post by Nickedynick on 2009-02-24
Sorry, I don't have a solution to your problem (I posted this guide in order to share what I know worked in my case) but I will say this regarding your Windows/Linux statement:

The drivers and programs written for Windows are done so by companies looking to make a profit in some way. To this end, you'd be shocked if a product didn't work. By contrast, Linux still isn't seen by many companies as a mainstream OS and as such a large proportion of drivers for these types of products are written by independent parties. While the majority of devices are supported and work well under this approach, there will always be some that slip through the net.

In the case of this driver, I believe that there was some sort of conflict within the development and one of the developers left and took his work with him (this is off the top of my head, I don't recall exact details). Hence, devices with this chip in them aren't supported by default.

I know this wasn't really any help to you, but I hope it has explained the situation a bit.

---

### Post by gborzi on 2009-02-24
@gridsleep,
I'm not sure about it, but I think you need to install libsox-fmt-oss to get rid of that error message.

---

### Post by budi_indira on 2009-02-25
thanks a lot !
now i can watch tv using Gadmei utv 330+ hahahahaha...

since a week ago i try to install, but still no good result. After trying this "HOWTO", now i can watch tv in my lovely ubuntu intrepid !

thanks again ^^

PS : sorry for my bad english.. hehehe.. :p

---

### Post by budi_indira on 2009-02-25
thanks a lot !
now i can watch tv using Gadmei utv 330+ hahahahaha...

since a week ago i try to install, but still no good result. After trying this "HOWTO", now i can watch tv in my lovely ubuntu intrepid !

thanks again ^^

PS : sorry for my bad english.. hehehe.. :p

---

### Post by heffo_j on 2009-03-11
Hi there,

thank you for posting your success with this. I'm having a persistent problem getting the "make" function to work. I have build-essentials installed. I get the following error. 

 ```
 *** No rule to make target `modules'.  Stop.
```

It seems to me that it wants to put the modules somewhere but can't find it.

Any help appreciated.

John

---

### Post by Nickedynick on 2009-03-11
Do you have up to date kernel headers? I've had a look [here]("http://ubuntuforums.org/showthread.php?t=132477") and it seems to be an issue.
```
sudo apt-get install linux-headers-`uname -r`
```

If it turns out to be this, then I'll add it to the tutorial.

---

### Post by ezha on 2009-03-18
Hello..
I've been trying install em28xx just like your post, but never works.
when i compile/make it, show error at the end just like this:

make[2]: *** [/home/resha/tv/em28xx-new/em28xx-cards.o] Error 1
make[1]: *** [_module_/home/resha/tv/em28xx-new] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2
cp: cannot stat `sharp/s921.ko': No such file or directory
cp: cannot stat `drx3973d/drx3973d.ko': No such file or directory
cp: cannot stat `tvp5150/tvp5150.ko': No such file or directory
cp: cannot stat `lgdt3304/lgdt3304.ko': No such file or directory
cp: cannot stat `mt352/mt352.ko': No such file or directory
cp: cannot stat `zl10353/zl10353.ko': No such file or directory
cp: cannot stat `cx25843/em28xx-cx25843.ko': No such file or directory
cp: cannot stat `xc3028/tuner-xc3028.ko': No such file or directory
cp: cannot stat `xc5000/tuner-xc5000.ko': No such file or directory
cp: cannot stat `em28xx.ko': No such file or directory
cp: cannot stat `em28xx-audioep.ko': No such file or directory
cp: cannot stat `em28xx-aad.ko': No such file or directory
cp: cannot stat `em28xx-audio.ko': No such file or directory
cp: cannot stat `em28xx-dvb.ko': No such file or directory
cp: cannot stat `qt1010/qt1010.ko': No such file or directory
cp: cannot stat `mt2060/mt2060.ko': No such file or directory
cp: cannot stat `modules/*': No such file or directory

I hope you can help me to solve this problem. Thank's..

---

### Post by Nickedynick on 2009-03-18
Do you have your system up to date? I notice that you have linux-headers-2.6.27-7-generic, rather than the latest Intrepid kernel 2.6.27-11.

---

### Post by ezha on 2009-03-20
ya.. you right..
Now i've update my system and no error. But I still can turn my tv tunner on.
I am using tvtime application, it show error like this:
"Cannot open capture divice /dev/video0."

Thanks before.

---

### Post by zaurus on 2009-03-24
Hello

Thanks for your excellent guide! Finally my stick starts working.
I did not use cp -v option as it was suggested somewhere in the beginning of this tread and it works anyway.
I have a question however.
I have 2 cards installed: Pinnacle 320e and Twinhan VP-1041 DVB-S2 PCI which uses S2API driver. When I compile the driver for my PCI card according to DVB-WIKI Pinnacle 320e stops working. It seems a new compilation overwrites em28xx driver compiled according this guide.
Any idea how to avoid this conflict?

Thanks

---

### Post by Nickedynick on 2009-03-24
Hi all, I've had a bit of a laptop crisis (it's screwed) and the only other PC I have is on Jaunty, so I'm not going to be able to offer much meaningful advice for a while I'm afraid.

ezha: I'm not too familiar with tvtime, but Kaffeine should work. I seem to remember trying tvtime in an old guide for Gutsy/Hardy and it not detecting my card.

zaurus: Again, I'll reference the old method I used on Gutsy/Hardy - it definitely stopped my webcam from working when I set it up. It seems certain drivers conflict with compiling for em28xx. I did however have both my webcam and TV card working under Intrepid (until my laptop broke).

Sorry I can't be of any more help - I'll try and hunt down some info in a few days (I have a project deadline on Fri) and get back here when I have advice!

---

### Post by ASL4U on 2009-03-28
I'm having a problem. This is the second "way" I've tried to get this going. The first set of directions I followed but they just didnt work - or at least I have no way of knowing how to check if it did except try to get a picture... and I was unable to get a picture. (TVTime, Kaffeine, and MythTV)...
I'm trying to use a Pinnacle PCTV HD Pro stick. I'm using Intrepid.
I have followed the directions you've laid out and  - and I now have the pinnacle recognized when I type in lsusb (I'm really NEW to linux.. so I'm kinda fumbling around)
after following the directions here, I thought it should work - but it didn't... so I typed in sudo modprobe 3m28xx 
and I got: 
FATAL: Error inserting em28xx (/lib/modules.2.5.27.11-generic/empia/em28xx.ko):
Unknown symbol in module, or unknown parameter (see dmesg)

the last few lines of the dmesg are:
160.935297] em28xx: disagrees about version of symbol v4l_compat_translate_ioctl
   160.935313] em28xx: Unknown symbol v4l_compat_translate_ioctl
   160.941818] em28xx: disagrees about version of symbol video_unregister_device
   160.941831] em28xx: Unknown symbol video_unregister_device
   160.942359] em28xx: disagrees about version of symbol video_device_alloc
   160.942364] em28xx: Unknown symbol video_device_alloc
   160.942588] em28xx: disagrees about version of symbol video_register_device
   160.942593] em28xx: Unknown symbol video_register_device
   160.944210] em28xx: disagrees about version of symbol video_usercopy
   160.944215] em28xx: Unknown symbol video_usercopy
   160.944445] em28xx: disagrees about version of symbol video_device_release
   160.944450] em28xx: Unknown symbol video_device_release

I tried to include the whole thing but was told that I had too many pictures in the text (I have no idea why it thinks a plain text file includes pictures)...


so it seems that em28xx is not doing what it should be.. any ideas what I need to do to make it work?

thanks

---

### Post by Nickedynick on 2009-03-30
I've not encountered this before, but there's a thread [here]("https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/160814") which may be of use. It's not the same module, but it's the same kind of error being displayed.

---

### Post by ASL4U on 2009-03-31
sigh
thank you for your reply. 
I do believe that those instructions might help me - but I do not know enough about how to do the things they are suggesting - to do them.

dead in the water.
I'll just put it on my XP machine and be done with it... bummed...
but eventually my system will be updated - and it will update the right files (or not) and it'll either start working or it wont.

thanks for you help.

---

### Post by lacoona on 2009-06-10
hi,
has anyone managed to get rid of the errors ASL4U mentioned in post #20?
I have the same problem and could not find a solution to it yet.
I use Linux Mint 7 (Gloria), which is based on Ubuntu 9.04 Jaunty, kernel version 2.6.28.

After em28xx install and reboot, the lsusb recognizes correctly the device but there are some errors present in the dmesg.
lsusb output:
```

The output of lsusb -v is:
Bus 002 Device 002: ID eb1a:e323 eMPIA Technology, Inc.
Device Descriptor:
 bLength                18
 bDescriptorType         1
 bcdUSB               2.00
 bDeviceClass            0 (Defined at Interface level)
 bDeviceSubClass         0
 bDeviceProtocol         0
 bMaxPacketSize0        64
 idVendor           0xeb1a eMPIA Technology, Inc.
 idProduct          0xe323
 bcdDevice            1.10
 iManufacturer           0
 iProduct                1
 iSerial                 0
 bNumConfigurations      1
 Configuration Descriptor:
   bLength                 9
   bDescriptorType         2
   wTotalLength          305
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
     bInterfaceSubClass      0
     bInterfaceProtocol    255
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
       bInterval             100
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x82  EP 2 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0000  1x 0 bytes
       bInterval               1
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x83  EP 3 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0000  1x 0 bytes
       bInterval               1
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x84  EP 4 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0000  1x 0 bytes
       bInterval               1
   Interface Descriptor:
     bLength                 9
     bDescriptorType         4
     bInterfaceNumber        0
     bAlternateSetting       1
     bNumEndpoints           4
     bInterfaceClass       255 Vendor Specific Class
     bInterfaceSubClass      0
     bInterfaceProtocol    255
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
       bInterval             100
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x82  EP 2 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0200  1x 512 bytes
       bInterval               1
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x83  EP 3 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0000  1x 0 bytes
       bInterval               1
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x84  EP 4 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0000  1x 0 bytes
       bInterval               1
   Interface Descriptor:
     bLength                 9
     bDescriptorType         4
     bInterfaceNumber        0
     bAlternateSetting       2
     bNumEndpoints           4
     bInterfaceClass       255 Vendor Specific Class
     bInterfaceSubClass      0
     bInterfaceProtocol    255
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
       bInterval             100
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x82  EP 2 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0280  1x 640 bytes
       bInterval               1
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x83  EP 3 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0000  1x 0 bytes
       bInterval               1
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x84  EP 4 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0000  1x 0 bytes
       bInterval               1
   Interface Descriptor:
     bLength                 9
     bDescriptorType         4
     bInterfaceNumber        0
     bAlternateSetting       3
     bNumEndpoints           4
     bInterfaceClass       255 Vendor Specific Class
     bInterfaceSubClass      0
     bInterfaceProtocol    255
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
       bInterval             100
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x82  EP 2 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0300  1x 768 bytes
       bInterval               1
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x83  EP 3 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0000  1x 0 bytes
       bInterval               1
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x84  EP 4 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0000  1x 0 bytes
       bInterval               1
   Interface Descriptor:
     bLength                 9
     bDescriptorType         4
     bInterfaceNumber        0
     bAlternateSetting       4
     bNumEndpoints           4
     bInterfaceClass       255 Vendor Specific Class
     bInterfaceSubClass      0
     bInterfaceProtocol    255
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
       bInterval             100
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x82  EP 2 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0340  1x 832 bytes
       bInterval               1
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x83  EP 3 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0000  1x 0 bytes
       bInterval               1
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x84  EP 4 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0000  1x 0 bytes
       bInterval               1
   Interface Descriptor:
     bLength                 9
     bDescriptorType         4
     bInterfaceNumber        0
     bAlternateSetting       5
     bNumEndpoints           4
     bInterfaceClass       255 Vendor Specific Class
     bInterfaceSubClass      0
     bInterfaceProtocol    255
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
       bInterval             100
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x82  EP 2 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0380  1x 896 bytes
       bInterval               1
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x83  EP 3 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0000  1x 0 bytes
       bInterval               1
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x84  EP 4 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0000  1x 0 bytes
       bInterval               1
   Interface Descriptor:
     bLength                 9
     bDescriptorType         4
     bInterfaceNumber        0
     bAlternateSetting       6
     bNumEndpoints           4
     bInterfaceClass       255 Vendor Specific Class
     bInterfaceSubClass      0
     bInterfaceProtocol    255
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
       bInterval             100
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x82  EP 2 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x03c0  1x 960 bytes
       bInterval               1
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x83  EP 3 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0000  1x 0 bytes
       bInterval               1
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x84  EP 4 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0000  1x 0 bytes
       bInterval               1
   Interface Descriptor:
     bLength                 9
     bDescriptorType         4
     bInterfaceNumber        0
     bAlternateSetting       7
     bNumEndpoints           4
     bInterfaceClass       255 Vendor Specific Class
     bInterfaceSubClass      0
     bInterfaceProtocol    255
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
       bInterval             100
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x82  EP 2 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x03fc  1x 1020 bytes
       bInterval               1
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x83  EP 3 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0000  1x 0 bytes
       bInterval               1
     Endpoint Descriptor:
       bLength                 7
       bDescriptorType         5
       bEndpointAddress     0x84  EP 4 IN
       bmAttributes            1
         Transfer Type            Isochronous
         Synch Type               None
         Usage Type               Data
       wMaxPacketSize     0x0000  1x 0 bytes
       bInterval               1
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
```

dmesg output:
```

[    8.612207] em28xx: Unknown symbol v4l_compat_translate_ioctl
[    8.612365] em28xx: Unknown symbol v4l2_video_std_construct
[    8.612732] em28xx: Unknown symbol v4l2_type_names
[    8.612881] em28xx: Unknown symbol v4l_printk_ioctl
[    8.613322] em28xx: Unknown symbol video_unregister_device
[    8.613472] em28xx: Unknown symbol video_device_alloc
[    8.613545] em28xx: Unknown symbol video_register_device
[    8.613950] em28xx: Unknown symbol video_usercopy
[    8.614023] em28xx: Unknown symbol video_device_release

```

any help is appreciated.
Thanks, Laszlo

---

### Post by Nickedynick on 2009-06-11
lacoona - sorry, but I don't think I can help. I've not managed to get it working in Jaunty yet - this guide was for Intrepid (since the way to get it working seems to change with each release).

jamiyoel - Yeah, it should work. It worked fine with my low-end Pinnacle card.

---

### Post by Nickedynick on 2009-06-11
Just a quick note to say that you'll need to change the kernel number if you're working on a newer kernel.

In which case,
```
sudo cp -v linux-source-2.6.27/drivers/media/dvb/dvb-core/*.h linux-headers-$(uname -r)/drivers/media/dvb/dvb-core/
```
becomes
```
sudo cp -v linux-source-2.6.28/drivers/media/dvb/dvb-core/*.h linux-headers-$(uname -r)/drivers/media/dvb/dvb-core/
```
and so on.

This *should* work on jaunty, unfortunately the mercurial files are absent from the server at the moment as the driver is being updated.

---

### Post by lacoona on 2009-06-12
Hi Nickedynick,
Thanks for your answer. First I tried without those copies without success, it's the same with the copies too.
I think I kind of found the problem, now I have to find a solution.
After the install of Linux Mint 7, I had the kernel 2.6.28-11, but the nvidia driver installation messed up the whole thing, because it uses things related to version 2.6.28-13.
It seems that the nvidia driver can be installed only with 2.6.28-13 related libc package (if I recall correctly this was the package).
I have to investigate further on this next week.
I assume that having 2.6.28-13 will further decrease my chances to compile the em28xx, right?
Thanks, Laszlo

---

### Post by newton21989 on 2009-06-16
> **Nickedynick said:**
> This *should* work on jaunty, unfortunately the mercurial files are absent from the server at the moment as the driver is being updated.

Ya, that's bugging me. Any chance someone hasn't deleted the source code and is willing to share until the new driver is released? I can't find it anywhere else.

**EDIT:** Well, I thought I need a driver, but then this:
```
# modprobe -l | grep em28xx
kernel/drivers/media/video/em28xx/em28xx-alsa.ko
kernel/drivers/media/video/em28xx/em28xx-dvb.ko
```Do I still need the driver or is the reason Ubuntu doesn't see my capture card elsewhere?

**EDIT:** More info:
```
$ sudo modprobe em28xx-dvb
FATAL: Error inserting em28xx_dvb (/lib/modules/2.6.28-11-generic/kernel/drivers/media/video/em28xx/em28xx-dvb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
$dmesg
...
[ 3449.310886] em28xx_dvb: Unknown symbol em28xx_set_mode
[ 3449.310886] em28xx_dvb: Unknown symbol em28xx_uninit_isoc
[ 3449.310886] em28xx_dvb: Unknown symbol em28xx_init_isoc
[ 3449.310886] em28xx_dvb: Unknown symbol em28xx_unregister_extension
[ 3449.310886] em28xx_dvb: Unknown symbol em28xx_register_extension
[ 3449.310886] em28xx_dvb: Unknown symbol em28xx_tuner_callback
```

---

### Post by zaurus on 2009-06-17
Yes. I have. You should sell it and never again buy something with Empia and Microna to do with or go to Microsoft. I am so frustrated by the guy who is payed to develop Linux driver for these chips but instead just struggling with the rest of Linux comunity. He has no time. It is sad.
  
> **ASL4U said:**
> I'm having a problem. 

so it seems that em28xx is not doing what it should be.. any ideas what I need to do to make it work?

thanks

---

### Post by newton21989 on 2009-07-01
> **Nickedynick said:**
> This *should* work on jaunty, unfortunately the mercurial files are absent from the server at the moment as the driver is being updated.
In fact, the server is down now!

> **newton21989 said:**
> Ya, that's bugging me. Any chance someone hasn't deleted the source code and is willing to share until the new driver is released? I can't find it anywhere else.
Bump.

---

### Post by MakisM1 on 2009-07-02
> **zaurus said:**
> Yes. I have. You should sell it and never again buy something with Empia and Microna to do with or go to Microsoft. I am so frustrated by the guy who is payed to develop Linux driver for these chips but instead just struggling with the rest of Linux comunity. He has no time. It is sad.
I got stuck with the same problem with my eMPIA webcam wich is integrated into my laptop.

After reading this:

[http://lwn.net/Articles/306601/](http://lwn.net/Articles/306601/)

I understand the history behind the problem, and, for the time being, I give up. I don't want to install an experimental driver that can mess up the rest of my system, I am only a week-old user of Ubuntu ;)

To be honest, I use a webcam very seldom, and I have another laptop with an integrated webcam, which works. If I really need one, they're cheap enough and not worth my time to try to correct the eMPIA problems.

I guess I can boot up XP, but I am developing moral principles...;)

Best regards

MakisM

---

### Post by aldeluis on 2009-07-11
Thank you, it worked for me in Ubuntu 9.04 2.6.28-13-generic x86_64

Attached is the source code. Please fork it.

---

### Post by gcc2011 on 2009-11-26
Thank you aldeluis. I will download your attachment and check if it is useful.

I found this question today suddendly. I worked well during June on my Ubuntu 9.04.

---

