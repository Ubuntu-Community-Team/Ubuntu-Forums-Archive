---
title: "problem getting kodak esp 7250 to scan"
date: 2012-07-06
forum: New to Ubuntu
---

### Post by Karl1973 on 2012-07-06
Hello, I am trying to use my scanner through only one usb port which is used for also printing (printing is no problem). I have the Kodak ESP 7250 AiO. Is CUPS interfering with SANE ? 

I tested if SANE recognises the scanner using** sane-find-scanner** and got the following:
 # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

[B]found USB scanner (vendor=0x040a [Eastman Kodak Company], product=0x4056 [KODAK ESP 7200 Series AiO]) at libusb:001:003
found USB scanner (vendor=0x0bda, product=0x8197) at libusb:001:002[/B]
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

I checked the driver config file kodak.conf and I see "scsi kodak" not commented out. should it be "usb kodak"?

How can I get scanning to work? I have version 12.04 of Ubuntu.

---

### Post by paulnewall on 2012-07-07
Confusingly, the backend kodak does not support the AiO printer/scanners.
Instead you need the backend koadakaio.
This can be found in the latest git version of sane
Instructions for getting the git version are here
[https://help.ubuntu.com/community/CompileSaneFromSource](https://help.ubuntu.com/community/CompileSaneFromSource)
Be warned that compiling sane takes ages. You can make it a little quicker by only compiling the backends that you need. This is determined at the configure stage.
Instead of
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
use
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var BACKENDS=kodakaio

 
more information about kodakaio is here
[https://sourceforge.net/projects/cupsdriverkodak/forums/forum/2125778](https://sourceforge.net/projects/cupsdriverkodak/forums/forum/2125778)

---

### Post by Karl1973 on 2012-07-07
Thank you for your help:guitar:
I compiled sane from source using the ubuntu doculink you gave and still I get no scanners identified with the scanimage -L command. Could it be a security issue? I went into the file kodakaio.conf and enabled the command: usb <deviceid> <productid> but still I get no scanner identified. sane-find-scanner sees the kodak esp 7200 series. I went in udev permissions using the ATTRS syntax to enable access to the scanner but still no change I see. Maybe the "make" was not fulling making with some security lock down to directories or something.

What could be the problem?

---

### Post by paulnewall on 2012-07-08
Some ideas:
Check that  /etc/saned/dll.conf has "kodakaio" in it, not commented out.
sane will not look for our scanner without that.

Set the environment variable SANE_DEBUG_KODAKAIO to get debug information.
For example:
export  SANE_DEBUG_KODAKAIO=40
scanimage -L

You should then see sane calling the kodakaio library to try and find the scanner.

---

### Post by Karl1973 on 2012-07-08
The problem was that kodakaio was not in the dll.conf file at all, so I added it and then ran scanimage -L and got success. I used the SimpleScan program to scan in a document and success:KS Thank you for your help once again PaulNewall :guitar:

---

