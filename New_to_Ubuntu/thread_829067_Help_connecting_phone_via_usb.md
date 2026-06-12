---
title: "Help connecting phone via usb"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by nothingspecial on 2008-06-14
Hi. Bit of a problem here connecting my wifes new mobile phone. Its a Samsung SGH-G600.
 The phone knows it is plugged into a computer it beeps.
 The computer knows it`s plugged into a phone - here`s dmesg

```
[175500.154634] usb 3-1: new full speed USB device using uhci_hcd and address 7
[175500.358341] usb 3-1: configuration #2 chosen from 1 choice
[175500.366338] cdc_acm 3-1:2.1: ttyACM0: USB ACM device


```

I`m completely clueless what to do next. I`d like to be able to transfer files between them.
Thankyou.
 
(btw I don`t know if this matters but I`ve set Ubuntu so that removable media devices don`t show on my desktop but do appear in places on the main menu)

Thanks in advance

---

### Post by Happy_Man on 2008-06-14
Could you post the output of ```
sudo fdisk -l
```? This will tell us if your computer knows the phone is there. Also, try looking in /media for a folder that could be your phone.

---

### Post by nothingspecial on 2008-06-14
Nothing in /media except my normal stuf.

Here`s the requested output - 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6edfd38

 ```
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30d73ab4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

```

Thanks for helping:)

---

### Post by Happy_Man on 2008-06-14
Hm, unless your phone has 500 GB of storage, I'm going to assume that that's an external HDD and your phone isn't being picked up. Now to see if the computer knows it even has something plugged into it. Could you post the output of ```
lsusb
``` please?

---

### Post by rraj.be on 2008-06-14
Just try some applications in synaptic like wammu gammu phone manager etc.

Its better to go specific than messing out.

---

### Post by nothingspecial on 2008-06-14
Yep it`s a hard drive. Here`s lsusb

Bus 005 Device 003: ID 0d49:7310 Maxtor 
Bus 005 Device 002: ID 0d49:3200 Maxtor 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 007: ID 04e8:663e Samsung Electronics Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 006: ID 03f0:8704 Hewlett-Packard 
Bus 002 Device 008: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 002 Device 007: ID 046e:5808 Behavior Tech. Computer Corp. 
Bus 002 Device 005: ID 046e:5908 Behavior Tech. Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000 

Line 4 has the phone. I`ve nothing else made by samsung connected.

---

### Post by nothingspecial on 2008-06-14
I`ve installed wammu which sees the phone but it will not let me transfer files. Thanks anyway.

---

### Post by rraj.be on 2008-06-14
You just need to configure a bit.

I think you can do it by ur self.

If you need help you can ask it.

---

### Post by nothingspecial on 2008-06-14
From Wammu`s website -

    *  complete support (can read/edit/delete/copy) for contacts, todo, calendar
    * can read/create/save/send/backup smses
    * sending files to phone (OBEX and Sony Ericsson phones only)
    * sms composer for multi part smses (currently only text and predefined bitmap/sound can be edited)
    * display message including pictures and ringtones playback
    * support for backup and import in various formats (vCard, vCalendar, vTodo, iCalendar, gammu own backup,...)
    * export messages to mail (IMAP4, maildir and mailbox storages are supported)
    * searching for phone
    * translated into several languages
    * rated as best on many software servers

It says file transfer only works with sony ericsson and obex.

I can retrieve sms messages and contact lists but it won`t let me retrieve files.

---

### Post by rraj.be on 2008-06-14
Oh.

i am using sonny ericsson.

So i am not much exposed to samsung.

But i think you can use some mobile file transfer utilities.

I use My phone explorer in windows.

But i dont know about that regarding ubuntu>

you could try wining that in ubuntu.

It might help.

---

### Post by nothingspecial on 2008-06-14
That`s for another day I think. I`ve never used wine. Thanks for your help though.

---

### Post by rraj.be on 2008-06-14
K. Try but solve the thread marked if solved.

So i can too refer here. bye.

---

### Post by nothingspecial on 2008-06-16
Using bluetooth I can get photos from the phone to my laptop and from there to my pc which solves my immediate issue. However I`d still like to achieve data transfer through usb so I`m leaving this open for now.

---

### Post by eldalion on 2008-09-14
Hey, though I'm not using ubuntu anymore (switched to arch a while ago), I've found out that KDE3 with Hal mount the G600 automatically, provided that you enable the following in the phone :
Settings -> USB Settings -> Mass Storage
Hope it helps someone else :)

---

### Post by faster1982 on 2008-11-11
Thans for wammu.
i downloaed it and try at home.. :)

---

