---
title: "Usb web cam"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by nutpants on 2008-05-14
i have a centrios web cam and would like to see if i can get it working in ubuntu 8.04

i cannot find anywhere that it is supported in linux so i am not hopefull
but then i have not found where it says it is not supported at all either.

this is the info i get from lsusb

us 005 Device 008: ID 0c45:6280 Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 04b3:3025 IBM Corp. 
Bus 004 Device 004: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


and at the end of dmesg

[  701.522529] usb 5-2: new high speed USB device using ehci_hcd and address 8
[  701.656436] usb 5-2: configuration #1 chosen from 1 choice
[  701.662733] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:1296: 8:2:1: cannot get freq at ep 0x84
[  702.128222] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:1296: 8:2:1: cannot get freq at ep 0x84


it has a build in speaker and it looks like it finds that but does not work..

how do i tell if my web cam was found?
or if drivers tried to get it to work or if it failed.

nutz

---

### Post by nicedude on 2008-05-14
For starters here is a tip to update your USB device list.

Update for USB device list

sudo update-usbids

You might run that to update your detection list then run lsusb again and post the results here along with your exact model of webcam and I will run it down and can answer you 99.9% yes or no. 99.9% because anything is supported if you can write your own driver :-)

---

### Post by nutpants on 2008-05-14
linuxtop:~$ sudo update-usbids
[sudo] password for XXXXXX: 
--15:35:28--  [http://linux-usb.sourceforge.net/usb.ids](http://linux-usb.sourceforge.net/usb.ids)
           => `/var/lib/misc/usb.ids.new'
Resolving linux-usb.sourceforge.net... 66.35.250.209
Connecting to linux-usb.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 347,477 (339K) [text/plain]

100%[====================================>] 347,477       61.04K/s    ETA 00:00

15:35:40 (34.33 KB/s) - `/var/lib/misc/usb.ids.new' saved [347477/347477]

Done.
linuxtop:~$ lsusb
Bus 005 Device 012: ID 0c45:6280 Microdia Composite Device
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 007: ID 04b3:3025 IBM Corp. 
Bus 004 Device 006: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  



Centrios
model no.2516514
portable and collapsible webcam

thanks for the help 

nutz

---

### Post by nicedude on 2008-05-14
Apearently the webcam in question is not supported unless the link below works and I am not sure as I don't have a similar camera to test. 

Your webcam makers internet address by the way is [http://www.centrios.com](http://www.centrios.com) here is their support email address -> [email]support@orbyxelectronics.com[/email] . Please send them an email complaining about no linux support - even if the driver below works, the more we all complain and threaten to take our buisness elsewhere the more all hardware vendors will support linux.

The actual camera chipset in this camera is aparently made by a company called sonix technologies ( I am 90% sure this is the correct chipset maker ) their website address is ->  [http://www.sonix.com.tw](http://www.sonix.com.tw) and your cameras chipset is aparently a sonix SN9C202 chipset.

I found the following download link to a experimental driver to support the SN9C202 chipset it is in the form of a deb package so you just have to download it and then doubleclick it and choose install.

[http://www.linux-projects.org/modules/mydownloads/visit.php?cid=7&lid=48](http://www.linux-projects.org/modules/mydownloads/visit.php?cid=7&lid=48)

Also I would recomend opening synaptic package manager ( Ubuntu's #1 software installation software interface ) by in the top menu bar clicking System -> Administration -> Synaptic Package Manager - and then search for "cheese" and install it too test the webcam driver above as if it works then cheese should pick it up ( I tested several webcam utiilities and cheese worked the best for me ).

Please PM me by clicking my name tag and selecting "send PM" so I will know how this turned out for you. Also feel free to PM if you can't get this driver file or can't figure out how to install it :-)

Good luck and I hope this helps anyone else who is searching for these drivers.

---

### Post by intel on 2008-05-15
please post your support request for microdia here
[https://groups.google.com/group/microdia](https://groups.google.com/group/microdia)

---

