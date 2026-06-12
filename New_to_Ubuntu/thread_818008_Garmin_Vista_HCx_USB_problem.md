---
title: "Garmin Vista HCx USB problem"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by gewitty on 2008-06-04
Having eventually got my original Extrex H working with a serial connection, which allowed me to use both Mapsource in WINE and also the rather excellent Viking GPS Viewer, I then went and upgraded to the GArmin Etrex Vista HCx. This is a terrific unit which does a whole lot more than the basic Extrex H. However, the connection is USB and for some reason, although Mapsource recognises the unit and transfers maps, Viking will not connect at all.

When I try to upload or download in Viking, it offers me a number of possible port connections: /dev/ttyS0, /dev/ttyS1, /dev/ttyUSB0, /dev/ttyUSB1, and also usb:   None of these will connect to the Vista though and I can find no way to modify the settings in Viking.

If it's any help, I ran  dmesg | grep tty, which returned the following:

[   34.124157] console [tty0] enabled
[   36.491091] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   36.491263] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   36.492106] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   36.492402] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   74.762689] audit(1212560772.967:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5274 profile="/usr/sbin/cupsd" namespace="default"

This doesn't appear to be showing the connected Garmin USB device, although as I said earlier, Mapsource can transfer files with no problem.

Has anyone any ideas on how I can get the unit working with Viking?

---

