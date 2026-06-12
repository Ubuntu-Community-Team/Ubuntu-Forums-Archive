---
title: "Getting collections in an HID report descriptor"
date: 2012-01-30
forum: Programming Talk
---

### Post by ptsubin on 2012-01-30
HI,

I have a USB HID sensor device. This is custom made on an MSP430F5528 and is running TI USB stack. I have wrote the HID driver for this and a few fixup was required with the descriptor, and it is running fine now. I can get the reports from /dev/hidraw0. This is actually an HID sensor collection for which microsoft already have a driver and framework. I wish to contribute the Linux driver for this. 

The problem is having hidraw0 is not enough for me. The sensor collection contain different sensors with different report IDs and usages. This is in conformance with [http://www.usb.org/developers/hidpage/HUTRR39b.pdf](http://www.usb.org/developers/hidpage/HUTRR39b.pdf). I want to provide an iio or direct sysfs entries for each sensor in the collection. To do this, i need to know what are the physical collections inside the report descriptor. The descriptor is already parsed by the hid driver and I would like to know if there is any way to retrieve these information in the probe function. In struct hid_device there is a struct hid_collection *collection; and the comment says this is list of HID collections and I don't know how to get all members in the list. 

If anyone has any ideas on this please let me know, so that I too can contribute something back..

---

### Post by ptsubin on 2012-02-01
My very silliness. struct hid_device have a member struct hid_collection *collection, also another member maxcollection which gives total number of parsed collections. All I need to do is access hdev->collection[i].type to see if it is physical and check hdev->collection[i].usage for i=0 to maxcollection. Sometimes very simple things go unnoticed. :)

---

