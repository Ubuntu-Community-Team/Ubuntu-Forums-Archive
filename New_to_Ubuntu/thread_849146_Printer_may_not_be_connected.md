---
title: "Printer may not be connected"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by mherrin on 2008-07-04
Hello all,

I have a problem printing all of a sudden...

The message comes up "Printer DCP135C may not be connected" when I try to print.

I have done a search on this, and could find nothing specific to this problem.

I have been printing happily for a while, but it's just stopped working.

I have Hardy AMD64, Brother DCP135-c on a USB connection

Any other information needed to solve this & I'll happily post up.

Here's some more info:
Typed:
[COLOR="Red"]mikeh@workstation:~$ lsmod | grep usb
usblp                  17664  0 
usb_storage            82496  0 
libusual               23520  1 usb_storage
usbhid                 35296  0 
hid                    44992  1 usbhid
scsi_mod              178488  6 sbp2,sr_mod,sg,sd_mod,usb_storage,libata
usbcore               169904  7 usblp,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd[/COLOR]

Then tried:

[COLOR="Red"]mikeh@workstation:~$ lpinfo -v
network socket
network beh
direct hal:///org/freedesktop/Hal/devices/usb_device_4f9_1ce_BROE7F477453_if0_printer_noserial
direct hpfax
direct hp
network http
network ipp
network lpd
file cups-pdf:/
direct scsi
network smb[/COLOR]

Uplugged printer then typed:
[COLOR="Red"]mikeh@workstation:~$ tail -f /var/log/messages
Jul  4 11:01:08 workstation kernel: [49504.067623] usb 1-10: new full speed USB device using ohci_hcd and address 7
Jul  4 11:01:08 workstation kernel: [49504.137310] usb 1-10: configuration #1 chosen from 1 choice
Jul  4 11:01:08 workstation kernel: [49504.142260] usblp0: USB Bidirectional printer dev 7 if 0 alt 0 proto 2 vid 0x04F9 pid 0x01CE
Jul  4 11:01:08 workstation kernel: [49504.154223] scsi11 : SCSI emulation for USB Mass Storage devices
Jul  4 11:01:13 workstation kernel: [49507.463802] scsi 11:0:0:0: Direct-Access     Brother  DCP-135C         1.00 PQ: 0 ANSI: 2
Jul  4 11:01:13 workstation kernel: [49507.477143] sd 11:0:0:0: [sdd] Attached SCSI removable disk
Jul  4 11:01:13 workstation kernel: [49507.477170] sd 11:0:0:0: Attached scsi generic sg4 type 0
Jul  4 11:15:41 workstation -- MARK --
Jul  4 11:22:41 workstation kernel: [50089.215641] usb 1-10: USB disconnect, address 7
Jul  4 11:22:41 workstation kernel: [50089.215747] usblp0: removed[/COLOR]

Plugged back in and...
[COLOR="Red"]Jul  4 11:23:24 workstation kernel: [50103.741292] usb 1-9: new full speed USB device using ohci_hcd and address 8
Jul  4 11:23:24 workstation kernel: [50103.811074] usb 1-9: configuration #1 chosen from 1 choice
Jul  4 11:23:24 workstation kernel: [50103.815691] usblp0: USB Bidirectional printer dev 8 if 0 alt 0 proto 2 vid 0x04F9 pid 0x01CE
Jul  4 11:23:25 workstation kernel: [50103.838329] scsi12 : SCSI emulation for USB Mass Storage devices
Jul  4 11:23:30 workstation kernel: [50108.160879] scsi 12:0:0:0: Direct-Access     Brother  DCP-135C         1.00 PQ: 0 ANSI: 2
Jul  4 11:23:30 workstation kernel: [50108.200872] sd 12:0:0:0: [sdd] Attached SCSI removable disk
Jul  4 11:23:30 workstation kernel: [50108.200906] sd 12:0:0:0: Attached scsi generic sg4 type 0[/COLOR]


TIA
Mike.

---

### Post by plucky on 2008-07-04
Open Firefox and in address bar input ```
http://localhost:631/admin/
```

You should then have access to the error log.See if there are any printer errors or communication errors.


Good Luck

---

### Post by mherrin on 2008-07-05
Thanks - I never knew that even existed.

Looking @ the page this brings up I see one "glaring error"...

[COLOR="Red"]**DCP-135C (Default Printer) "Filter "brlpdwrapperdcp135c" for printer "DCP-135C" not available: No such file or directory"**[/COLOR]

I assume that this is the spooling directory? What should the directory be?

Thanks,
Mike.

---

### Post by plucky on 2008-07-05
> DCP-135C (Default Printer) "Filter "brlpdwrapperdcp135c" for printer "DCP-135C" not available: No such file or directory"



```
/usr/lib/cups/filter/
``` is the location of that file.

You can now install the brother drivers from **Synaptic Package Manager**.Open synaptic and search for brother and install the "brother-cups-wrapper-extra" and brother-lpr-drivers-extra" for your printer


Good Luck

---

### Post by blueturtl on 2008-07-08
This could be Debian bug #383091.

I had the same problem on Hardy 32-bit. To fix it, I had to add the following line to the file /etc/cups/cupsd.conf:

```
FileDevice Yes
```

After this, I went to localhost:631 with my browser and changed the device URI of the printer to

file:/dev/usb/lp0

That did it for me!

---

