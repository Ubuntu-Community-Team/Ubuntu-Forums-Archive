---
title: "scanner not working after 08.04 upgrade"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by dmikulec on 2008-11-16
XSANE no longer works with my CanoScan N1220U since upgrading from Gutsy to Hardy. When I launch XSANE a window briefly reports "scanning for devices", then disappears. I've run the following diagnostics:

don@don-desktop:~$ xsane
Segmentation fault


don@don-desktop:~$ groups
don adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev sambashare




don@don-desktop:~$ sane-find-scanner
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x2207 [CanoScan], chip=LM9832/3) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.


don@don-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 04e8:326c Samsung Electronics Co., Ltd 
Bus 001 Device 003: ID 046d:c025 Logitech, Inc. MX500 Optical Mouse
Bus 001 Device 002: ID 04a9:2207 Canon, Inc. CanoScan 1220U
Bus 001 Device 001: ID 0000:0000  


don@don-desktop:~$ scanimage -L
Segmentation fault


Seems that the system recognizes the scanner but xsane does not.
I've uninstalled xsane, removed the ~/.sane dir, and reinstalled xsane.

When I launch xsane, these messages appear in syslog:

Nov 16 13:22:15 don-desktop rmmod: ERROR: Removing 'lp': Operation not permitted 
Nov 16 13:22:15 don-desktop rmmod: ERROR: Module parport_pc is in use 
Nov 16 13:22:15 don-desktop rmmod: ERROR: Removing 'ppdev': Operation not permitted 
Nov 16 13:22:15 don-desktop rmmod: ERROR: Module parport is in use by ppdev,lp,parport_pc 
Nov 16 13:22:15 don-desktop kernel: [14042.822741] xsane[21639] general protection eip:b6d9dbf5 esp:bf9b9ad0 error:0


My hardware: AMD Athalon64 3400+,  2GB RAM, MAXTOR 6L060J3, 6L060J3 NVIDIA 6L060J3


Thanks, Don

---

### Post by yousellstuff on 2008-11-16
if you ever need a clone script of a big website like facebook or you tube, just go to clonedscripts.info

---

