---
title: "Pic Microcontroller Programming"
date: 2012-04-14
forum: Programming Talk
---

### Post by 64mgb on 2012-04-14
I'm having a tough time finding good examples for programming a Pic microcontroller USB device (specifically a pic18f4550) from Ubuntu.  The firmware is no problem...Microchip's MPLAB X works well and I've become somewhat comfortable with it.  But I haven't been able to write a host side program that will work.  (I can get it to connect to the device and retrieve the device PID and VID, but haven't been able to send it commands successfully).  I found a small sample using Lazarus (which I am very comfortable with...I've done a lot of Delphi programming) and usblib, but can't make it work.

Does anyone have experience with this?  I found a great example for Windows ([http://www.waitingforfriday.com/index.php/Building_a_PIC18F_USB_device](http://www.waitingforfriday.com/index.php/Building_a_PIC18F_USB_device)) and made it work fine, but really need to find something for Linux.  I'm most comfortable with Pascal, but have done enough C (and relations) and Java to be able to pick it up...I taught myself Objective C so I could write iPhone apps, so I'm capable of learning!

Thanks,
Rich

---

### Post by sisco311 on 2012-04-14
Thread moved to **Programming Talk**.

---

### Post by alexfish on 2012-04-15
> **64mgb said:**
> I'm having a tough time finding good examples for programming a Pic microcontroller USB device (specifically a pic18f4550) from Ubuntu.  The firmware is no problem...Microchip's MPLAB X works well and I've become somewhat comfortable with it.  But I haven't been able to write a host side program that will work.  (I can get it to connect to the device and retrieve the device PID and VID, but haven't been able to send it commands successfully).  I found a small sample using Lazarus (which I am very comfortable with...I've done a lot of Delphi programming) and usblib, but can't make it work.

Does anyone have experience with this?  I found a great example for Windows ([http://www.waitingforfriday.com/index.php/Building_a_PIC18F_USB_device](http://www.waitingforfriday.com/index.php/Building_a_PIC18F_USB_device)) and made it work fine, but really need to find something for Linux.  I'm most comfortable with Pascal, but have done enough C (and relations) and Java to be able to pick it up...I taught myself Objective C so I could write iPhone apps, so I'm capable of learning!

Thanks,
Rich

Do you mean sending a command to the pic , then read back , is so

for serial programming , found the easiest programming language to be tcl . it is easiest  route to configuring the fd  [http://www.tcl.tk/man/tcl8.4/TclCmd/open.htm](http://www.tcl.tk/man/tcl8.4/TclCmd/open.htm)
[http://www.tcl.tk/man/tcl8.4/TclCmd/fconfigure.htm](http://www.tcl.tk/man/tcl8.4/TclCmd/fconfigure.htm)
[http://wiki.tcl.tk/_/search?S=serial&_charset_=UTF-8](http://wiki.tcl.tk/_/search?S=serial&_charset_=UTF-8)

some early PIC programers for TCL
[http://hv.tclcode.com/picprog.html](http://hv.tclcode.com/picprog.html)

[LIST]
[*][picl]("http://www.physics.brocku.ca/Courses/2P32/References/picl")  (version  12.01.05), a compiler/loader for PICLab board written in  TCL/TK (© F.Boseglav). Under Linux, make executable (chmod 755) and run;  under Windo$e, save as picl.tcl, comment out the third line of the  script, and double-click to open; assumes a TCL/TK interpreter is  installed.
[/LIST]


programming a serial port can be quite tricky in c , and will have the same problems with Pascal and Lazarus

once have the serial port R/W working  successfully then can wrap into an executable 

if using Lararus then best option is to add synapse  / or use process control to exec your serial program / only problem is the exec in Lazurus is quite large

I found the easiest gui method was to use BaCon / although the base lang is basic , don't be decieved by it's name , this one can compile c with in
    or if have own say libmyserial then can also use , or exec another prog with in  ,  the executable  is also stand alone

[http://www.basic-converter.org/](http://www.basic-converter.org/)  .. worth looking at

ADDED: you can compile BaCon from Scratch on most platforms "IE ARM" : providing the system has Bash
can give a tip on this one / have a look at the source codes for the gui + 
[http://www.basic-converter.org/bacon.lang](http://www.basic-converter.org/bacon.lang)

it is possible to write your own editor to recognise the commands you would use for programming the pic

How easy it is to send a command to the serial port in BaCon if the device is on ttyUSB1
> OPEN "/dev/ttyUSB1" FOR READWRITE AS pic
WRITELN "<your command>\r" TO piccan also look at this forum thread for ideas
[http://www.murga-linux.com/puppy/viewtopic.php?t=69647&start=135](http://www.murga-linux.com/puppy/viewtopic.php?t=69647&start=135)

[http://basic-converter.proboards.com/index.cgi?board=general&action=display&thread=175](http://basic-converter.proboards.com/index.cgi?board=general&action=display&thread=175)

some about pic programming on linux

[http://www.micahcarrick.com/pic-programming-linux.html](http://www.micahcarrick.com/pic-programming-linux.html)

---

### Post by 64mgb on 2012-04-15
> **alexfish said:**
> Do you mean sending a command to the pic , then read back , is so

for serial programming , found the easiest programming language to be tcl . it is easiest  route to configuring the fd  [http://www.tcl.tk/man/tcl8.4/TclCmd/open.htm](http://www.tcl.tk/man/tcl8.4/TclCmd/open.htm)
[http://www.tcl.tk/man/tcl8.4/TclCmd/fconfigure.htm](http://www.tcl.tk/man/tcl8.4/TclCmd/fconfigure.htm)
[http://wiki.tcl.tk/_/search?S=serial&_charset_=UTF-8](http://wiki.tcl.tk/_/search?S=serial&_charset_=UTF-8)

some early PIC programers for TCL
[http://hv.tclcode.com/picprog.html](http://hv.tclcode.com/picprog.html)

[LIST]
[*][picl]("http://www.physics.brocku.ca/Courses/2P32/References/picl")  (version  12.01.05), a compiler/loader for PICLab board written in  TCL/TK (© F.Boseglav). Under Linux, make executable (chmod 755) and run;  under Windo$e, save as picl.tcl, comment out the third line of the  script, and double-click to open; assumes a TCL/TK interpreter is  installed.
[/LIST]


programming a serial port can be quite tricky in c , and will have the same problems with Pascal and Lazarus

once have the serial port R/W working  successfully then can wrap into an executable 

if using Lararus then best option is to add synapse  / or use process control to exec your serial program / only problem is the exec in Lazurus is quite large

I found the easiest gui method was to use BaCon / although the base lang is basic , don't be decieved by it's name , this one can compile c with in
    or if have own say libmyserial then can also use , or exec another prog with in  ,  the executable  is also stand alone

[http://www.basic-converter.org/](http://www.basic-converter.org/)  .. worth looking at

ADDED: you can compile BaCon from Scratch on most platforms "IE ARM" : providing the system has Bash
can give a tip on this one / have a look at the source codes for the gui + 
[http://www.basic-converter.org/bacon.lang](http://www.basic-converter.org/bacon.lang)

it is possible to write your own editor to recognise the commands you would use for programming the pic

How easy it is to send a command to the serial port in BaCon if the device is on ttyUSB1
can also look at this forum thread for ideas
[http://www.murga-linux.com/puppy/viewtopic.php?t=69647&start=135](http://www.murga-linux.com/puppy/viewtopic.php?t=69647&start=135)

Thanks for the input alexfish.  I don't have time right now to look into the details of your post but will later.

Thanks,
Rich

---

### Post by alexfish on 2012-04-17
Though post this link , if miss in other info

there is a easy to program c / serial / lib  called cssl , probably  easiest option for serial coms in Linux

have posted Here , post #[URL="http://ubuntuforums.org/showpost.php?p=11846464&postcount=11"][B]11 
[/B][/URL]

---

### Post by 64mgb on 2012-04-18
> **alexfish said:**
> Though post this link , if miss in other info

there is a easy to program c / serial / lib  called cssl , probably  easiest option for serial coms in Linux

have posted Here , post #[URL="http://ubuntuforums.org/showpost.php?p=11846464&postcount=11"][B]11 
[/B][/URL]

Thanks again, alexfish.  I think I've found a solution to my problem.  In Microchip's solutions library (microchip_solutions_v2012-02-15) there is a folder called "Device - HID - Custom Demos" that contains another folder called "PnP Demo - Cross Platform Software", which in turn contains a QT project called "HID_PnP_Demo" that gives me exactly what I want, and it works!  I'm now in the process of learning how to use QT, which is cross-platform, so if I want to I can create Windows and OSX versions of my program.

Rich

---

