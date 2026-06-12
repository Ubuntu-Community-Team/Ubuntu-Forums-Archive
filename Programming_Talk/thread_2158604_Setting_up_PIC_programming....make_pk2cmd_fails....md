---
title: "Setting up PIC programming....make pk2cmd fails..."
date: 2013-06-29
forum: Programming Talk
---

### Post by wannabegeek on 2013-06-29
hi all,

I just ordered my first PIC12 and programmer....getting ready for the arrival, I've decided to compile the needed software.
I've been following these instructions: [http://hackaday.com/2010/11/03/how-to-program-pics-using-linux/](http://hackaday.com/2010/11/03/how-to-program-pics-using-linux/)

The sdcc installed flawlessly....
I downloaded the pk2cmd per the instructions, extracted and tried to make the executables.

[PHP]
wbg@geek:~/Downloads/pk2cmdv1.20LinuxMacSource$ make linuxmake TARGET=linuxmake[1]: Entering directory `/home/wbg/Downloads/pk2cmdv1.20LinuxMacSource'g++ -Wall -D_GNU_SOURCE -O2 -I/usr/local/include -DLINUX -DUSE_DETACH -DCLAIM_USB -o pk2usbcommon.o  -c pk2usbcommon.cppIn file included from pk2usbcommon.cpp:32:0:pk2usb.h:49:26: fatal error: usb.h: No such file or directorycompilation terminated.make[1]: *** [pk2usbcommon.o] Error 1make[1]: Leaving directory `/home/daniel/Downloads/pk2cmdv1.20LinuxMacSource'make: *** [linux] Error 2[/PHP]


Now, when I ls, I can see the usb.h  header file. I've always been a bit lost with linking complicated C++.... I'm wondering it the usb.h file should be in /usr/local/include ...?

Any help is greatly appreciated...

TIA !
wbg

PS I am running Mint 13

---

### Post by wannabegeek on 2013-06-29
Ok....I posted too quick...

Google returned a Spanish page and translate did a great job...
Needed to install the libusb-dev package....The user in the link below also runs Mint 12, so I guess Mint doesn't include this package
by default where as Ubuntu does...?

Hope this helps someone...please repsond anyways if you feel like chatting about PICs !

wbg


[http://translate.google.com/translate?hl=en&sl=es&u=http://pic-linux.foroactivos.net/t448-problema-al-compilar-pk2cmd&prev=/search%3Fq%3Dpk2usb.h:49:26:%2Bfatal%2Berror:%2Busb.h:%2BNo%2Bsuch%2Bfile%2Bor%2Bdirectory%26biw%3D1163%26bih%3D670](http://translate.google.com/translate?hl=en&sl=es&u=http://pic-linux.foroactivos.net/t448-problema-al-compilar-pk2cmd&prev=/search%3Fq%3Dpk2usb.h:49:26:%2Bfatal%2Berror:%2Busb.h:%2BNo%2Bsuch%2Bfile%2Bor%2Bdirectory%26biw%3D1163%26bih%3D670)

---

