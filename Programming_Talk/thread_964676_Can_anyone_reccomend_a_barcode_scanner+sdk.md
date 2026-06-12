---
title: "Can anyone reccomend a barcode scanner+sdk"
date: 2008-10-31
forum: Programming Talk
---

### Post by Jive Turkey on 2008-10-31
I need one for my business, spreadsheets work ok for now but I could be way more productive if I made a custom app that interfaced with a barcode scanner and a precision balance.

---

### Post by CoolRanchLuke on 2008-10-31
*bump*

Did you ever find a suitable product?

---

### Post by dribeas on 2008-10-31
> **Jive Turkey said:**
> I need one for my business, spreadsheets work ok for now but I could be way more productive if I made a custom app that interfaced with a barcode scanner and a precision balance.

I used one some time ago, cannot remember make or model, but the scanner simulated a keyboard so there would be no such thing as a sdk. Once configured it would read the barcode into the sequence of numbers and enter that followed by a newline. Rather simple.

When you search for hardware consider the ease of use that keyboard input provides (we used it to enter data into a web application).

---

### Post by slavik on 2008-10-31
Symbol LS2208

it is USB and emulated a keyboard. It is also programmable by scanning bar codes (but you will need a windows system to print those out last I checked).

plug it in, and it works (I did it myself).

---

### Post by slavik on 2008-10-31
Symbol LS2108

it is USB and emulated a keyboard. It is also programmable by scanning bar codes (but you will need a windows system to print those out last I checked).

plug it in, and it works (I did it myself).

---

### Post by sickasabat on 2008-11-05
I have just recently purchased a usb barcode scanner. It appears to be a keyboard emulating scanner. So I was just wondering how you read the barcodes from the scanner? I've been searching the internet for a while now and haven't found anything particularly helpful.

---

### Post by mssever on 2008-11-05
> **sickasabat said:**
> I have just recently purchased a usb barcode scanner. It appears to be a keyboard emulating scanner. So I was just wondering how you read the barcodes from the scanner? I've been searching the internet for a while now and haven't found anything particularly helpful.The last time I messed with barcodes, I simply plugged my keyboard wedge scanner (PS/2 in my case) into the computer, focused a text box, and scanned. As long as you're using a type of barcode that the scanner recognizes, then it works as if you manually typed the barcode.

---

### Post by John Q (be) on 2009-01-07
Hi I have found a scanner @ my work and 'd like to use it for inventorying.

If i scan using XP = ok it works...
If i connect to Ubuntu 8.10 it seems to recognise in dmesg (see below)
but upon scanning the buffer of the scanner isn't sending to the PC (it stores the scanned numbers in the internal memory.)

The following commands give

> pc@pc-desktop:~$ dmesg | tail
[ 7887.739437] usb 1-2: USB disconnect, address 8
[ 7888.043923] usb 1-2: new full speed USB device using uhci_hcd and address 9
[ 7888.223539] usb 1-2: configuration #1 chosen from 1 choice
[ 7888.275789] input: The Code Corporation Code Corporation Code Reader 2.0 as /devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2:1.0/input/input10
[ 7888.300315] input,hidraw0: USB HID v1.10 Keyboard [The Code Corporation Code Corporation Code Reader 2.0] on usb-0000:00:07.2-2
[ 7917.996965] usb 1-2: USB disconnect, address 9
[23571.565171] usb 1-2: new full speed USB device using uhci_hcd and address 10
[23571.730576] usb 1-2: configuration #1 chosen from 1 choice
[23571.742953] input: The Code Corporation Code Corporation Code Reader 2.0 as /devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2:1.0/input/input11
[23571.745489] input,hidraw0: USB HID v1.10 Keyboard [The Code Corporation Code Corporation Code Reader 2.0] on usb-0000:00:07.2-2
pc@pc-desktop:~$ sudo modprobe -v usbkbd
[sudo] password for pc:
insmod /lib/modules/2.6.27-9-generic/kernel/drivers/hid/usbhid/usbkbd.ko
pc@pc-desktop:~$ lsusb
Bus 001 Device 066: ID 11fa:0200 
Bus 001 Device 028: ID 050d:0249 Belkin Components
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


From dmesg i assume that the scanner is recognised (which is nice), however i also read "USB disconnect" always between the lines... so is it attempting to communicate further and is is holding/stopping somewhere?

Using the command "sudo modprobe -v usbkbd" does something but i can't verify more (i guess)

In the "lsusb" i don't see the device (or any pointer to something like it)

Now i didn't write down the serial number and vendor... (post tomorrow if necessary)

But does anyone know some more debug commands, or element's that i can test out for seeing how far the things are going well and determine where...

|Thx|

---

