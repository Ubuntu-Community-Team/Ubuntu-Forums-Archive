---
title: "usbmon interface with wireshark ; USB sniffing"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by adumur on 2013-02-19
Hello,

I actually have an issue while I install wireshark for usb sniffing.
I have a wireshark installation correctly running with the network interface.
I read the kernel module usbmon is supposed to add some usbmon interfaces to my wireshark I can sniff.

So I do a "modprobe usbmon" and ... nothing = no error nor success ...
When I list running kernel module via lsmod I can't see any usbmon so I should have seen an error when I run modprobe usbmon ...

dmesg ... nothing new.

Have I usbmon.ko installed somewhere ? I think so because modprobe usbmon doesn't issue any error ?

rmq : "mount" gives me this information :
none is mounted to /sys/kernel/debug type debugfs what seems to be the correct config whereas I don't understand what It means ? what is a debugfs filesystem type ?

Thanks for reading
I would be thankful whether you have any idea

---

