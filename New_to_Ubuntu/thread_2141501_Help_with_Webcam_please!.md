---
title: "Help with Webcam please!"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by BosAndNumbers on 2013-05-02
Hello,

  I just installed Ubuntu 12.10 on my computer and am completely new to Linux. I downloaded Skype and have it working now, but I'm unable to turn on my webcam. I went to testmycam.com and it wasn't detecting that I had a webcam there either. I have browsed through the forums for similar issues and didn't find anything, I'm really really hoping that I can get some help on this because it is very important for me and I don't want to have to go back to Windows just for a webcam.

When I type **lsusb** I get:
Bus 001 Device 005: ID 1058:0748 Western Digital Technologies, Inc. 
Bus 003 Device 006: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[B]
uname -a[/B]:
Linux shaun-NF66 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux

**dmesg**:
[ 2940.450369] usb 3-5: >USB disconnect, device number 5
[ 2959.000056] usb 3-5: >new full-speed USB device number 6 using ohci_hcd
[ 2959.219048] usb 3-5: >New USB device found, idVendor=046d, idProduct=08f0
[ 2959.219054] usb 3-5: >New USB device strings: Mfr=0, Product=1, SerialNumber=0
[ 2959.219058] usb 3-5: >Product: Camera
[ 2959.222152] gspca_main: STV06xx-2.14.0 probing 046d:08f0
[ 2959.222160] gspca_stv06xx: st6422 sensor detected
[ 2959.604155] input: STV06xx as /devices/pci0000:00/0000:00:0b.0/usb3/3-5/input/input15

I downloaded the qc-usb-0.6.6.tar.gz file from sourceforge.net, but I was unable to compile it - or I'm unsure of how to compile it...
I typed in **tar zxf qc-usb-0.6.6.tar.gz** and it returned:
tar (child): qc-usb-0.6.6.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now


I don't know what to do, and any help at all would be **greatly** appreciated!

Thanks, Shaun

---

### Post by arpanaut on 2013-05-02
Have you tried installing cheese? Here's a wiki page of information:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
What is your webcam?  Here's a list of compatible 'cams:
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

Hope this helps!

---

### Post by BosAndNumbers on 2013-05-02
Thanks for the reply arpanaut!

I installed Cheese and its working there, but still not for Skype.
I looked at the list of Skype webcams and my model number: 046d:08f0 is on there under "Fiddle to get working" webcams
It does give some instructions for Ubuntu 9.04 which is typing:** LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype** in the terminal.
I did this and got this back:
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

So now I'm back to being baffled, but at least I know that my webcam works, its just Skype that is the problem now :)

---

