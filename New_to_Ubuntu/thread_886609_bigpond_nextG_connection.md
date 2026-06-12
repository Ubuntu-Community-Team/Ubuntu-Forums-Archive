---
title: "bigpond nextG connection"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by david0075 on 2008-08-11
im trying to connect to bigpond using one of the blue modems. i read around tring to find out how to do it. this is what ive done so far

interminal sudo insmod /lib/modules/2.6.24-16-generic/kernel/drivers/usb/serial/usbserial.ko vendor=0X16d8 product=0X6280

the instructions that i was following said to do this using 'uname -r' instead of the 2.6.24-16-generic part, and using usb-serial.ko at the end. but when i searched the folders, the above is what i found, and it didnt say file not found like the others.

dmesg shows tons of stuff, some stuff that i think is important is:

usb 1-1:new full speed usb device using uhci_hcd and address 2
usb 1-1: configuration #1 chosen from 1 choice
/build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: usb serial support registered for generic
usbserial_generic 1-1:1.0 generic converter detected
usb 1-1:generic converter now attached to ttyUSB0
usbserial_generic 1-1:1.1 generic converter detected
usb 1-1:generic converter now attached to ttyUSB1
usbserial_generic 1-1:1.2 generic converter detected
usb 1-1:generic converter now attached to ttyUSB2
usbcore: registered new interface driver usbserial_generic
/build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: usb serial driver core

lsusb shows

Bus 003 Device 002: ID 054c:0069 Sony Corp. memorystick MSC-U03 reader
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 16d8:62800
Bus 001 Device 001: ID ID0000:0000


for pppconfig, i use the settings

number      *99#
ISPLogin    ogin:  //this was the recommended setting
User        [email]myusername@bigpond.com[/email]  //changed, of course
ISPPrompt   ssword:    //recommended setting
password    bigpondpassword
com         /dev/ttyUSB1  //i have tried USB0 and USB2, both come up with 'in file /ect/ppp/peers/bigpond: unrecognized option '/dev/ttyUSB1'


i have no idea where to go from here, and its really annoying not being able to connect to the net unless i boot windows.

---

