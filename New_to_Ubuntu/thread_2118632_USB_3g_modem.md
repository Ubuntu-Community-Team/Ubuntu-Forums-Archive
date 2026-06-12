---
title: "USB 3g modem"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by djangofawkes on 2013-02-21
Hello, I have recently purchased a Huawei E3231 3g Modem. 

I run lsusb and get:
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 008: ID 12d1:1f01 Huawei Technologies Co., Ltd. 
Bus 003 Device 007: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 2232:1028  
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

then I do:  
sudo modprobe usbserial vendor = 0x12d1 product=0x1f01

this spits out the following error:

FATAL: Error inserting usbserial (/lib/modules/3.2.6/kernel/drivers/usb/serial/usbserial.ko): Invalid argument

Moving on, I do: 
wvdialconf 

it says:

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7   
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

sudo gedit /etc/wvdial.conf

in my conf file is:

Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = *99#
ISDN = 0
Password = pass  (your modem password)
New PPPD = yes
Dial Command = ATDT
Username = user  (your modem username)
Modem = /dev/ttyUSB0
Baud = 9600
Stupid Mode = 1

Some of these parameters maybe incorrect, but nevertheless, I then do wvdial to start connecting and I get:

--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

I do believe the problem is the fact that /dev/ttyUSB0 does not exist.  
Can somebody please give me advice as to how I go about sorting this mess? Thanks.

---

### Post by Sealbhach on 2013-02-21
Hi, see the post by bmork in [this thread ]("http://ubuntuforums.org/showthread.php?t=2110519&page=2"). It may help. Normally those Huawei USB modems should just work straight away in Ubuntu.

.

---

