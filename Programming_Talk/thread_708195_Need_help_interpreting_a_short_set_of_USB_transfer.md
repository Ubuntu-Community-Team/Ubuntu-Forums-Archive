---
title: "Need help interpreting a short set of USB transfers logged with SnoopyPro"
date: 2008-02-26
forum: Programming Talk
---

### Post by robotool on 2008-02-26
Hey all,

I'm trying to write a Linux driver for a USB device that I recently purchased.  I have a Windows driver for the product, but the company does not offer a Linux driver, and their documentation does not describe the USB interface to the device.  I'm trying to reverse-engineer a Linux driver by snooping the USB connection in Windows using SnoopPro.  I've gotten it to the point where I can configure the device, claim the USB port, and initialize the USB interface in Linux.  It looks like there are only about three transfers that are sent from the computer to the device before the device is fully initialized.  I've reproduced the logs for those transfers below:

9	out down	n/a	18.518	VENDOR_DEVICE	-	
URB Header (length: 80)
SequenceNumber: 9
Function: 0017 (VENDOR_DEVICE)
PipeHandle: 00000000

SetupPacket:
0000: 00 00 ff ff 00 00 f4 83 
bmRequestType: 00
  DIR: Host-To-Device
  TYPE: Standard
  RECIPIENT: Device
bRequest: 00  
  GET_STATUS


No TransferBuffer

9	out up	n/a	18.519	CONTROL_TRANSFER	-	0xc0000004
URB Header (length: 80)
SequenceNumber: 9
Function: 0008 (CONTROL_TRANSFER)
PipeHandle: 84aef180

SetupPacket:
0000: 40 00 ff ff 00 00 00 00 
bmRequestType: 40
  DIR: Host-To-Device
  TYPE: Vendor
  RECIPIENT: Device
bRequest: 00  


No TransferBuffer

10	out down	n/a	18.519	VENDOR_DEVICE	-	
URB Header (length: 80)
SequenceNumber: 10
Function: 0017 (VENDOR_DEVICE)
PipeHandle: 84aef180

SetupPacket:
0000: 00 02 02 00 00 00 00 00 
bmRequestType: 00
  DIR: Host-To-Device
  TYPE: Standard
  RECIPIENT: Device
bRequest: 02  
  reserved for future use!!


No TransferBuffer

10	out up	n/a	18.520	CONTROL_TRANSFER	-	0x00000000
URB Header (length: 80)
SequenceNumber: 10
Function: 0008 (CONTROL_TRANSFER)
PipeHandle: 84aef180

SetupPacket:
0000: 40 02 02 00 00 00 00 00 
bmRequestType: 40
  DIR: Host-To-Device
  TYPE: Vendor
  RECIPIENT: Device
bRequest: 02  


No TransferBuffer

11	??? down	n/a	18.520	BULK_OR_INTERRUPT_TRANSFER	-	
URB Header (length: 72)
SequenceNumber: 11
Function: 0009 (BULK_OR_INTERRUPT_TRANSFER)
TransferFlags: 0x00000003

No TransferBuffer

Basically, I just need to know how to create and send these packets using the libusb API in Ubuntu.  Any help with this would be greatly appreciated :-).

---

### Post by supirman on 2008-02-26
Did you look at the documentation for libusb?  [http://libusb.sourceforge.net/doc/](http://libusb.sourceforge.net/doc/)

The packets in your trace each have a 'function'.  Those match up to the APIs in the libusb guide...

---

### Post by robotool on 2008-02-26
I looked through the libusb documentation when I started writing the program I'm working on, and it's pretty obvious what values to use for the "requesttype" and "request" parameters in the messages (and what message type to use) because the SnoopyPro log writes those values out explicitly in the log.

What I was looking for help with are the "index" and "value" parameters.  How would I determine what those should be?  And what's a "Transfer Flag", and how would I set it?

---

