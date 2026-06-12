---
title: "Qt Serial seems to be deaf on Ubuntu 12.04"
date: 2012-12-02
forum: Programming Talk
---

### Post by Zilax on 2012-12-02
I have a continuous-duty program that polls an embedded RS-485 serial device periodically. It had been running fine on Ubuntu 10.04 with Qt 2010.05.1 and QExtSerial 1.1. That installation ran through an FTDI based USB to serial convertor. I found the FTDI device to be a little annoying in that it would spontaneously change the tty device it was listed under. I was able to work around that behavior and the program ran fine for a couple of years.

I would now like to upgrade to Ubuntu 12.04. Initially I attempted to use the Ubuntu qt-sdk package and QExtSerial 1.2beta 2 from Google Code. I found that the FTDI driver issues seemed a lot worse and my program would occasionally freeze (about once per a week). So I gave up on the USB based serial converter and created a custom RS-232 to RS-485 convertor using the RTS line to toggle the RS-485 transmit enable.

What I've found with that setup is that while transmission works just fine, the program never gets any bytes in return even though the embedded devices (and a logic analyzer) indicate bytes are in fact being sent to the RS-232 port in reply to the Qt program's transmissions. Further, they return to the RS-232 port within about 70ms. (My timeout is set to 300ms). Nonetheless, readyRead() never fires. When the time out fires, I check bytesAvailable and it always says zero.

Maddeningly, on the command line, if I run 'cat /dev/ttyS0' I can clearly see the reply bytes from the embedded devices. So the reply bytes are definitely inside the operating system, they just don't make it to my program.

I thought that perhaps QExtSerial might have some issue, so I dropped back a version. Same symptom. I then ported the code to use the newer QSerialDevice library. Again same symptom. I thought that perhaps the ubuntu spin of qt-sdk was bugged so I removed it and installed 2010.05.01 from the old binary installer. Once more, same symptom.

On Windows XP this code works fine whether via the RS-232 port or via the USB port.

[My original code from 2010.]("https://github.com/roycepipkins/MakerAccessControl/blob/master/server/AccessServer/busmngr.cpp")

Has anyone seen anything like this? Why can cat see the reply bytes but Qt is convinced there are no such bytes?

Thanks for any tips or ideas on things I can try. I'm about to surrender and just require this program be hosted on windows. Its just that the whole point of writing it in Qt was to get cross platform functionality.

---

