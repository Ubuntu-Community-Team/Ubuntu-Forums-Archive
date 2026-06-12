---
title: "/dev/rtc and user access (with qlc)"
date: 2008-04-09
forum: Programming Talk
---

### Post by bernt_ on 2008-04-09
Hello,

I have some problems with /dev/rtc.
starting the program qlc as root: all is working.
But as normal user:

$ ls -l /dev/rtc
crw-rw-rw- 1 root audio 10, 135 2008-04-09 21:38 /dev/rtc

$ id
uid=1000(bernt) gid=1000(bernt) Gruppen=4(adm),20(dialout),24(cdrom),25(floppy),[COLOR="Blue"]29(audio)[/COLOR],
30(dip),44(video),46(plugdev),104(scanner),106(fuse),108(lpadmin),
114(netdev),116(powerdev),118(admin),124(vboxusers),1000(bernt)

$ strace qlc
[FONT="Courier New"]open("/dev/rtc", O_RDONLY)              = 7
ioctl(7, RTC_IRQP_SET, 64)              = 0
ioctl(7, RTC_IRQP_READ, 3214882928[COLOR="Black"])[/COLOR]     = 0
write(2, "\nPeriodic IRQ rate is 1024Hz.\n", 30
Periodic IRQ rate is 1024Hz.
) = 30
ioctl(7, RTC_PIE_ON, 0)                 = -1 EACCES (Permission denied)
write(2, "ioctl: Permission denied\n", 25ioctl: Permission denied
) = 25
exit_group(13)                          = ?
Process 28125 detached[/FONT]


Why has only root the right to make an ioctl and not a normal user?
Also changing /dev/rtc to crw-rw-rw- does not help.

---

