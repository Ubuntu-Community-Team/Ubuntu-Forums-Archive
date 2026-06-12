---
title: "map usb printer to parallel port"
date: 2015-12-22
forum: New to Ubuntu
---

### Post by Paul_Samuel on 2015-12-22
I am using wine 1.6 in ubuntu 14.04 and I am trying to run a vb application with the help of the wine. I'm succeed it by running wine and with winetricks but I have one issues in printing. The vb application will create a text file and the text file has to printed and in windows it is printed by "c:filename.txt >prn" with both parallel printer and usb printer. The usb printer is mapped to lpt1 with "net use" command in windows 7. The printer works fine with parallel port But in wine I can't able to map usb printer to lpt1. Instead of that I gave the direct path of the usb printer "c:filename.txt >/dev/usb/lp0" and gave 777 rights to that path. Now printer works but not printing the content properly such as font may differs or some content missing. Please help me with your valuable answer.

Thank you,

---

### Post by DuckHook on 2015-12-26
Hi Paul and welcome to Ubuntu and the forums.

Redirecting plain text output will work in Linux, but redirecting any other output will not. Especially if that output includes control commands. Such output needs to be filtered through a printer driver before all of the control and formatting commands get translated in a way that the printer understands. Redirection bypasses the printer driver, so it is no wonder that you are getting gobbledegook output. I am not at all familiar with WINE printing procedures so can't help you with specifics. Ask one of the mods to move your post to the WINE subforum for access to the WINE gurus.

---

### Post by coldraven on 2015-12-27
Did you create the links as described here?    [https://www.winehq.org/docs/wineusr-guide/misc-things-to-configure](https://www.winehq.org/docs/wineusr-guide/misc-things-to-configure)


>           Serial and parallel port configuration is very similar to drive           configuration - simply create a symbolic link in           ~/.wine/dosdevices with the name of the           device.  Windows serial ports follow a naming convention of the           word com followed by a number, such as           com1, com2, etc.  Similarly, parallel ports use           lpt followed by a           number, such as lpt1.           You should link these directly to the corresponding Unix           devices, such as /dev/ttyS0 and           /dev/lp0. **Make sure you have the needed           access rights to that device**. For example, to configure           one serial port and one parallel port, run the following commands: 

ln -s /dev/ttyS0 com1
ln -s /dev/lp0 lpt1         

---

