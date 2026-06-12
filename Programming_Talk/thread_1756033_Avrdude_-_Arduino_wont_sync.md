---
title: "Avrdude - Arduino wont sync"
date: 2011-05-11
forum: Programming Talk
---

### Post by RawthiL on 2011-05-11
Hello, I recently migrated to Ubuntu 11.04 and I installed Arduino via Synaptic, it seems to work fine but it wont upload.

I have a self-made boarduino with an Atmega168, under windowsOS it works perfectly, selecting the arduino board: "diecimila w/168", so I upload a serial test program to test my ubuntu drivers. Wen I open the Serial Monitor on ubuntu I can comunicate with it just fine at 9600 bd.

The problem is uploading in ubuntu OS, I selected the same board and the correct port, but it says "avrdude: stk500_getsync(): not in sync: resp=0x20" (I have tested all the "reset" options, while, before, after pressing upload)

verbose output:
```
Binary sketch size: 990 bytes (of a 14336 byte maximum)
/usr/share/arduino/hardware/tools/avrdude -C/usr/share/arduino/hardware/tools/avrdude.conf -v -v -v -v -patmega168 -carduino -P/dev/ttyS4 -b19200 -D -Uflash:w:/tmp/build6136871358548744634.tmp/Blink.cpp.hex:i 

avrdude: Version 5.10, compiled on Jun 29 2010 at 03:44:14
         Copyright (c) 2000-2005 Brian Dean, http://www.bdmicro.com/
         Copyright (c) 2007-2009 Joerg Wunsch

         System wide configuration file is "/usr/share/arduino/hardware/tools/avrdude.conf"
         User configuration file is "/home/rawthil/.avrduderc"
         User configuration file does not exist or is not a regular file, skipping

         Using Port                    : /dev/ttyS4
         Using Programmer              : arduino
         Overriding Baud Rate          : 19200
avrdude: Send: 0 [30]   [20] 
avrdude: Send: 0 [30]   [20] 
avrdude: Send: 0 [30]   [20] 
avrdude: Recv:   [20] 
avrdude: stk500_getsync(): not in sync: resp=0x20

avrdude done.  Thank you.
```And I also tried via command line with sudo and "-Cstk500v1" but it makes no diference.

the verbose uploading from windows its similar, but it works

```
Binary sketch size: 2520 bytes (of a 14336 byte maximum) 
D:\Documentos RawthiL\Arduino\arduino-0021\hardware/tools/avr/bin/avrdude -CD:\Documentos RawthiL\Arduino\arduino-0021\hardware/tools/avr/etc/avrdude.conf -v -v -v -v -patmega168 -cstk500v1 -P\\.\COM2 -b19200 -D -Uflash:w:C:\DOCUME~1\RawthiL\CONFIG~1\Temp\build3852963370463831576.tmp\ubuntu.cpp.hex:i  
 
avrdude: Version 5.4-arduino, compiled on Oct 11 2007 at 19:12:32 
         Copyright (c) 2000-2005 Brian Dean, http://www.bdmicro.com/ 
 
         System wide configuration file is "D:\Documentos RawthiL\Arduino\arduino-0021\hardware/tools/avr/etc/avrdude.conf" 
 
         Using Port            : \\.\COM2 
         Using Programmer      : stk500v1 
         Overriding Baud Rate  : 19200 
avrdude: ser_open(): setting dtr 
avrdude: Send: 0 [30]   [20]  
avrdude: Send: 0 [30]   [20]  
avrdude: Send: 0 [30]   [20]  
avrdude: Recv:  
avrdude: Recv:  
         AVR Part              : ATMEGA168 
         Chip Erase delay      : 9000 us 
         PAGEL                 : PD7 
         BS2                   : PC2 
         RESET disposition     : dedicated 
         RETRY pulse           : SCK 
         serial program mode   : yes 
         parallel program mode : yes 
         Timeout               : 200 
         StabDelay             : 100 
         CmdexeDelay           : 25 
         SyncLoops             : 32 
         ByteDelay             : 0 
         PollIndex             : 3 
         PollValue             : 0x53 
         Memory Detail         : 

...bla bla bla ...

```Im using a PCI-Serial board based on a WCH352L

Thanks!

---

### Post by RawthiL on 2011-05-12
Well after a week looking I found out what was the problem.

It looks like my pci-serial card drivers for Linux (ch35x_80x86) wont do the whole work, so I found out that my setserial output has something wrong:

```
rawthil@Smaug:~$ setserial -g /dev/ttyS[04]
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS4, UART: undefined, Port: 0x9010, IRQ: 21

```So I googled it and found out this realy helpfull page out there:
[http://www.placona.co.uk/359/linux/getting-serial-ports-to-work-on-linux/](http://www.placona.co.uk/359/linux/getting-serial-ports-to-work-on-linux/)

with this simple command (where "ttyS4" is your serial port) I fixed it
 ```

sudo setserial /dev/ttyS4 uart 16550A

```And now its working wonderfully!

edit: I tried to add this to /etc/rc.local but it doesnt work, soy If someone knows how to do it please tell me :P 

Hope this help someone!

---

