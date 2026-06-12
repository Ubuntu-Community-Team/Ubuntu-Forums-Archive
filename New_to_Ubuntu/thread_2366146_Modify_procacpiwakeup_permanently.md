---
title: "Modify /proc/acpi/wakeup permanently"
date: 2017-07-14
forum: New to Ubuntu
---

### Post by oraora20 on 2017-07-14
Hi all,

I recently bought a new wireless keyboard and it has messed up the wakeup file in the proc filesystem.
This is the content of the file:

Device    S-state      Status   Sysfs node
PEG1      S4    *disabled
PEGP      S4    *disabled
PEG2      S4    *disabled
PEGP      S4    *disabled
PEG0      S4    *disabled
PEGP      S4    *disabled
GLAN      S4    *disabled
XHC      S3    *enabled   pci:0000:00:14.0
XDCI      S4    *disabled
HDAS      S4    *disabled  pci:0000:00:1f.3
RP01      S4    *disabled
PXSX      S4    *disabled
RP02      S4    *disabled
PXSX      S4    *disabled
RP03      S4    *disabled
PXSX      S4    *disabled
RP04      S4    *disabled
PXSX      S4    *disabled
RP05      S4    *disabled  pci:0000:00:1c.0
PXSX      S4    *enabled   pci:0000:01:00.0
RP06      S4    *disabled  pci:0000:00:1c.5
PXSX      S4    *disabled  pci:0000:02:00.0
RP07      S4    *disabled
PXSX      S4    *disabled
RP08      S4    *disabled
PXSX      S4    *disabled
RP09      S4    *disabled  pci:0000:00:1d.0
PXSX      S4    *disabled  pci:0000:03:00.0
RP10      S4    *disabled
PXSX      S4    *disabled
RP11      S4    *disabled
PXSX      S4    *disabled
RP12      S4    *disabled
PXSX      S4    *disabled
RP13      S4    *disabled
PXSX      S4    *disabled
RP14      S4    *disabled
PXSX      S4    *disabled
RP15      S4    *disabled
PXSX      S4    *disabled
RP16      S4    *disabled
PXSX      S4    *disabled
RP17      S4    *disabled
PXSX      S4    *disabled
RP18      S4    *disabled
PXSX      S4    *disabled
RP19      S4    *disabled
PXSX      S4    *disabled
RP20      S4    *disabled
PXSX      S4    *disabled

What I would like is to put the XHC entry to disabled permanently to prevent wakeup when I move my mouse slightly.
I have searched a bit on google but have found nothing good so far.
Any ideas?

Thanks,

oraora20.

---

### Post by &amp;KyT$0P# on 2017-07-14
Try putting the command to disable it in [FONT=Courier New]/etc/rc.local[/FONT] ?

---

