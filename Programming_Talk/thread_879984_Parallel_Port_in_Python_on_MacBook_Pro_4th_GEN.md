---
title: "Parallel Port in Python on MacBook Pro 4th GEN"
date: 2008-08-04
forum: Programming Talk
---

### Post by Botto on 2008-08-04
Ok, so I have a USB parallel port. I have downloaded the PyParallel and installed it, I have unloaded the lp module and loaded the ppdev module. However I am still getting a error every time I try to run the command: 
```
p = parallelppdev.Parallel("/dev/usblp0")
```
In Idle

The error is as follows:
```

Traceback (most recent call last):
  File "<pyshell#1>", line 1, in <module>
    p = parallelppdev.Parallel("/dev/usblp0")
  File "/home/martin/Downloads/Client/Development/pyparallel-0.2/parallel/parallelppdev.py", line 187, in __init__
    self.PPEXCL()
  File "/home/martin/Downloads/Client/Development/pyparallel-0.2/parallel/parallelppdev.py", line 235, in PPEXCL
    fcntl.ioctl(self._fd, PPEXCL)
IOError: [Errno 25] Inappropriate ioctl for device

```
I have read through the forums and looked all over the place, can't find a solution.

Thank you for any help on this.

---

### Post by Botto on 2008-08-05
I love the way this has really been looked at. I must say this community thing is a lot of hot air and no business.

---

### Post by samjh on 2008-08-05
Not enough info.  And complaining about not having your problem answered only 13 hours after posting an extremely rare and obscure problem, is a bit demanding. ;)

First, /dev/usblp0 doesn't seem to be a parallel port, but rather a printer connected via USB.  Are you sure PyParallel works on such an arrangement?

Second, do you have read and write access to /dev/usblp0 ?  You may be surprised, but sometimes Python can't access the parallel port because of permission problems and need to be run as root.

Third, have you tried:
```
import parallel
p = parallel.Parallel()
```?  Does it cause the same error?

You may also try [PortIO](http://portio.iriti.cnr.it/) as an alternative.  Some people have more success with it than PyParallel.

---

### Post by Zugzwang on 2008-08-05
If I see it correctly, then "lpusb0" is just some virtual port for "line printers" conntected to the usb port, so that's not your actual parallel port.

Also, the error "Inappropriate ioctl for device" states that the device is not in stream mode, so even if that is the parallel port on your computer, then is device is not served by the Linux parallel port services and therefore unsupported by PyParallel.

Try "/dev/parport0" for your computer's parallel port.

---

### Post by Botto on 2008-08-05
I mainly complained because I had posted something in the past and it was never answered, even when I continued with the topic. I also saw other posts in this forum being replied to quite fast. I don't usually do it, however my last straw had been met while working with it.


Yes, it is a usb to printer emulator, however I cracked it open took a look and checked the data sheet(Prolific PL-2305H) of the chip inside. It was a basic usb to parallel port chip, according to the datasheet it is fully compliant with the ieee1284 standard. However it might be that they have modified the chip.
[http://www.datasheetarchive.com/pdf/2766290.pdf](http://www.datasheetarchive.com/pdf/2766290.pdf) That's the datasheet.

I ran the python program through sudo in order to avoid the issues with read/write access. I have also tried portio but to no avail, it shows no errors, but when measuring the voltages on the ports for data bits 0-7 they still showed as high when I had outputed 0x00 to the port.

I did a diff of the output from ls /dev/ between when the port was connected and when it was disconnected.
It showed the following.
```

686,688d685
< usbdev5.4_ep00
< usbdev5.4_ep01
< usbdev5.4_ep82
699d695
< usblp0

```

Thank you in advance

---

### Post by samjh on 2008-08-05
> **Botto said:**
> Yes, it is a usb to printer emulator, however I cracked it open took a look and checked the data sheet(Prolific PL-2305H) of the chip inside. It was a basic usb to parallel port chip, according to the datasheet it is fully compliant with the ieee1284 standard. However it might be that they have modified the chip.
[http://www.datasheetarchive.com/pdf/2766290.pdf](http://www.datasheetarchive.com/pdf/2766290.pdf) That's the datasheet.
usblp is not a parallel port device.  From the point of view of the operating system, it's just a USB device with a printer attached to it.  The hardware emulator does the USB-to-Parallel conversion.

Also, usblp is a separate kernel module from ppdev.  As PyParallel requires ppdev, that already indicates it won't work with PyParallel.

What you probably really need is a Python module to access USB devices.  Try [PyUSB](http://pyusb.berlios.de/).

---

