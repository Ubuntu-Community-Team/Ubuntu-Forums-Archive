---
title: "Scaner HP Deskjet F2180"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by bmr on 2013-01-04
Hi, i have a NAS DS213 from synology and this nas has connected a usb printer F2180.
Synology shows a fully supported printer with scanner.

printing works fine, but the scanner does not work.

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 001 Device 003: ID 05e3:0723 Genesys Logic, Inc. GL827L SD/MMC/MS Flash Card Reader
Bus 002 Device 003: ID 093a:260e Pixart Imaging, Inc. PAC7311 Gigaware VGA PC Camera:Trust WB-3350p:SIGMA cam 2350
Bus 002 Device 004: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter

sudo sane-find-scanner
 # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x093a, product=0x260e) at libusb:002:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


scanimage --list-devices
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).




I hope someone can help me get the scanner running.
I have installed simple scanner, which does not scan too. i tried with sudo too, no luck.

---

### Post by DuckHook on 2013-01-05
You've done an admirable job of data preparation before asking for help and really must be complimented. It provides a big head start in helping you.

Unfortunately, because your printer/scanner is hooked up to the NAS and not your own computer, *lsusb* won't show either the printer or the scanner. It only shows devices that are attached to your own USB interface, whereas your F2180 is being accessed via your network interface.

Because the printer is connected to your NAS, your NAS is acting not only in its native capacity as a NAS but also doubles as a print server. This looks transparent to you because Ubuntu hides the networking layer, so the printer is automatically recognized, and you can just print. However, the NAS was not programmed to be a scan server, so the scanning functions are not available through the network. You can do one of two things:

1. Connect the printer up directly to your computer and install *hplip* from the repositories. This should make everything, including the scanner, work for your own machine. However, unless you "share" the printer and leave your computer on all the time, others will no longer be able to print to this printer.

2. Investigate if you can set up your NAS (of which I am not familiar) in Linux as a scan server (I doubt that it supports such capability). After that, you would have to research whether and how you can pass scan requests through a server with HP's scanning drivers. This would probably get awful technical in an awful hurry.

Wish I had more options, but that's all I've got to offer. Would love to hear from the network gurus.

---

### Post by bmr on 2013-01-05
Thanx for your two choices. The first one is not good for me, because i have space for a printer at my desk ;)

What i thought about the second point is that the synology nas is a print and scan server.
I hoped i have nothing to do with the nas but with my ubuntu configuration.

in the print setup the printer was found with this adress:
dnssd://usbprinter1%20%40%20DiskStation._printer._tcp.local/

---

### Post by DuckHook on 2013-01-07
> **bmr said:**
> ...the synology nas is a print and scan server...

[http://www.synology.com/products/spec.php?product_name=DS213&lang=us](http://www.synology.com/products/spec.php?product_name=DS213&lang=us)

Your NAS is not a scan server. It only supports multi-function in Windows.

> Printing Protocols : LPR, CIFS, IPP, Apple AirPrint, Google Cloud Print, Multi Functional Print Server (for Windows PC only)

---

