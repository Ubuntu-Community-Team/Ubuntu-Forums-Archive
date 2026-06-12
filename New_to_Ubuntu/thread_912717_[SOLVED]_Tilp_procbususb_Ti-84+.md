---
title: "[SOLVED] Tilp /proc/bus/usb Ti-84+"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Commander_Bob on 2008-09-07
I have a Ti-84+ silver edition calculator I would like to get to work. My teacher makes us clear the memory each time before a test so all the programs I make are gone. I need a way to back them up. I have installed tilp2 but nothing happens when I plug in my calculator.

I setup udev to give me write permissions. However I read that tilp looks for the calculator in /proc/bus/usb when Ubuntu (8.04) puts it in /dev/bus/usb. I tried making a symbolic link but I only ran into errors. Do I need to do anything on the calculator to get it to work? Doing lsusb shows it. Any help is greatly appreciated.

When I start tilp I get:
```
TiLP2 - Version 1.01, (C) 1999-2006 Romain Lievin
THIS PROGRAM COMES WITH ABSOLUTELY NO WARRANTY
PLEASE READ THE DOCUMENTATION FOR DETAILS
built on Sep  3 2007 16:56:25
tilp-INFO: setlocale: <en_US.UTF-8>
tilp-INFO: bindtextdomain: </usr/share/locale/>
tilp-INFO: textdomain: <tilp2>
ticables-INFO: ticables library version 1.0.3
ticables-INFO: setlocale: <en_US.UTF-8>
ticables-INFO: bindtextdomain: </usr/share/locale>
ticables-INFO: textdomain: <libticables2>
ticables-INFO: kernel: 2.6.24-17-generic
tifiles-INFO: tifiles library version 1.0.2
tifiles-INFO: setlocale: <en_US.UTF-8>
tifiles-INFO: bindtextdomain: </usr/share/locale>
tifiles-INFO: textdomain: <libtifiles2>
ticalcs-INFO: ticalcs library version 1.0.2
ticalcs-INFO: setlocale: <en_US.UTF-8>
ticalcs-INFO: bindtextdomain: </usr/share/locale>
ticalcs-INFO: textdomain: <libticalcs2>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted <--WRONG
```

Thanks,
Justin

---

### Post by gletob on 2008-09-07
just a shot in the dark but try it with sudo

---

### Post by Commander_Bob on 2008-09-07
I got it to work! By entering ```
sudo mount --rbind /dev/bus/usb /proc/bus/usb
```

gletob using sudo did nothing. It was not finding it because it was looking in /proc not /dev. I have had similar problems with other devices before so I kinda knew what to do. Thanks for the help though!

Is there a way to do this permanently?

---

### Post by Commander_Bob on 2008-09-07
I made it permanent.
```
sudo apt-get install gnome-schedule
sudo gnome-schedule
```
then do  
```

New
A task that launches recurrently 

Description: USB Workaround
Command: mount --rbind /dev/bus/usb /proc/bus/usb
Basic: At reboot

Click Add and reboot
```

That should do it. Works for me. Doing ls /proc/bus/usb shows the devices (001-005)

---

