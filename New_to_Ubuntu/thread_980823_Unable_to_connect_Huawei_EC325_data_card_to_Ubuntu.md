---
title: "Unable to connect Huawei EC325 data card to Ubuntu 8.04"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by anandss2004 on 2008-11-13
Hi 
I am trying to connect Huawei E325 card with Ubuntu machine to run the internet.

In short I am getting ‘Modem Identifier: ATI -- ERROR’. Just incase you can help me out with below points.

A, I understand that the moment we plug any usb device the kernel makes an enrty in /proc/bus/usb/devices. However in my case if I try cat /proc/bus/usb/devices, it prints nothing, which seems wrong to me. However when I try lsusb below is printed.

abc@abc-desktop:/proc/bus/usb$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem 
Bus 001 Device 001: ID 0000:0000  

B. So not sure how to tell the kernel that Huawei card is inserted, also I have inserted Huawei card EC325 however it is recognized as E620 USB Modem

C. In my opinion A and B are the main issues which is causing ‘Modem Identifier: ATI -- ERROR’, however please see the below steps what I have tried out. 

1. I fired modprobe to set modem.

abc@abc-desktop:~$ sudo modprobe usbserial vendor=0x12d1 product=0x1001
abc@abc-desktop:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   
WvModem<*1>: Cannot get information for serial port.  // I added: not sure if this is an issue.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- ERROR
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"


2. My wvdial.conf file looks below.

cat /etc/wvdial.conf

[Dialer Defaults]
Inherits = Modem 0
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
New PPPD = Yes
Phone = #777
Modem = /dev/ttyUSB0
Username = internet
Password = internet
Baud = 9600

[Modem 0]
Modem = /dev/ttyUSB0
Dial Command = ATDT
Baud = 115200
FlowControl = Hardware (CRTSCTS)
Init1 = ATZ

3. Incase I try to run Modem below is printed. But I am unable to access internet.

abc@abc-desktop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT 230400
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Nov 13 15:02:23 2008
--> Pid of pppd: 9371
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> local  IP address 121.245.91.239
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> remote IP address 172.23.137.14
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> primary   DNS address 202.54.15.30
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]
--> secondary DNS address 202.54.1.30
--> pppd: &#65533;&#65533;[06][08]8&#65533;[06][08]

Please help me out..

Thanks in Advance,
Anand

---

### Post by karanpals on 2009-01-20
The output from wvdial clearly shows that you have got the ip address and dns from your provider.
The problem area can b
 You already have default route set before dialing with wvdial
   resolution
     before running wvdial run this command
        ip route del default

---

### Post by anet on 2009-04-04
> **karanpals said:**
> The output from wvdial clearly shows that 
     before running wvdial run this command
        ip route del default

Hi, I'm a complete NOOB, but have gotten Ubuntu hardy on a partition on my laptop (pats herself on the back), and now my first goal is to get my Ubuntu online. So I don't have to re-boot into Windows just to search the Ubuntu Forum!!

How does one 'do' that command in wvdial?

Thanks in advance for any help!

---

