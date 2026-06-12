---
title: "Serial Port communication Not working"
date: 2016-04-15
forum: New to Ubuntu
---

### Post by aamir6 on 2016-04-15
[COLOR=#111111][FONT=Ubuntu]I want to use serial port to send/receive data. I have joind dialout group. sudo chmod a+rw /dev/ttyS0 is done[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]On checking sudo dmesg | grep tty, I get following message[/FONT][/COLOR]
[    0.000000] console [tty0] enabled
[    3.389473] 00:03: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    3.410045] 00:04: ttyS1 at I/O 0x2f8 (irq = 4, base_baud = 115200) is a 16550A
[    3.430616] 00:05: ttyS2 at I/O 0x3e8 (irq = 7, base_baud = 115200) is a 16550A
[    3.451176] 00:06: ttyS3 at I/O 0x2e8 (irq = 7, base_baud = 115200) is a 16550A
[COLOR=#111111][FONT=Ubuntu]But still I am not able to send or receive data. I have "gtkterm" and "minicom", both installed, they are just blank showing nothing, even not showing any error. Similarly my written (in c language)application is also behaving similar, initially permission denied did appear, but by joining dialout group and chmod read write permission, it disappear. I am very new in Linux. I have confirmed that hardware is working fine. [/FONT][/COLOR]

---

### Post by HermanAB on 2016-04-16
Well, what kind of serial port are you using?  If it is a USB device, then the name would be /dev/ttyUSB0.

You also need to make yourself a member of the dialout group, otherwise you need to run minicom or cutecom with sudo.

---

