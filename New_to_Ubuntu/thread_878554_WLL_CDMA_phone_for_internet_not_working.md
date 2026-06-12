---
title: "WLL CDMA phone for internet not working"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by Guruprasad on 2008-08-03
I have WLL CDMA phone which is providing me internet connection on windows but it doesnot work properly with Linux.

In windows it show as via telecom cbp usb modem

I tried lsusb after connecting the modem. It showed the device with few numbers like 15eb:0001 but no name mentioned after then What can be done so that inux detects it?

Then i used sudo modprobe usbserial vendor=0x15eb product=0x0001

At times the modem works but most of the time it doesnot.

What can be done to make it work regulerly?

---

### Post by birenjith on 2008-10-29
I have the same type of modem, and have configured it with the help of suggestions and guidelines given in many blogs. Given below is the way i have configured it. Hopefully it helps.

Step 1: (To ensure that the usb modem is detected by the kernel)

Connect the usb modem and type

sudo tail -f /var/log/messages

Check if the following messages are displayed

Oct 29 17:08:52 birenjith-laptop kernel: [18094.628000] usb 3-1: new full speed USB device using uhci_hcd and address 7

Oct 29 17:08:52 birenjith-laptop kernel: [18094.784000] usb 3-1: configuration #1 chosen from 1 choice

Oct 29 17:08:52 birenjith-laptop kernel: [18094.792000] usbserial_generic 3-1:1.0: generic converter detected

Oct 29 17:08:52 birenjith-laptop kernel: [18094.792000] usb 3-1: generic converter now attached to ttyUSB0


If the message is displayed, your usbmodem is getting detected automatically. Most likely it wont happen - only the first two lines will be displayed. Then, do the following. 

Step 1.1 (In case of ubuntu linux installation, need changes in /etc/init.d/mountdevusbfs.sh
)



Go to  /etc/init.d/mountdevusbfs.sh and check if the following lines are commented in the do_start() function



#

# Magic to make /proc/bus/usb work

#

mkdir -p /dev/bus/usb/.usbfs

domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644

ln -s .usbfs/devices /dev/bus/usb/devices

mount --rbind /dev/bus/usb /proc/bus/usb



If they are commented, uncomment them.

Step 1.2 (To attach the usbserial module to the kernel) 

First, we need to find out the vendor id and product id of the usb modem. Type lsusb or lsusb -v to identify the vendor & product id of the usb modem. For the usb modem which shows up as CBP VIA Telecom in Windows, the vendor id is 0x15eb and product id is 0x0001.

Now attach the module usbserial to the kernel by typing the command

sudo modprobe usbserial vendor=0x15eb product=0x0001

To make it happen everytime the system boots, add the following line to the file /etc/modules
usbserial vendor=0x15eb product=0x0001

After these steps, the usb device would have been detected. 

Step 2: (To edit wvdial configuration file)

Back up the /etc/wvdial.conf and then edit the /etc/wvdial.conf to add the following lines

[Dialer Defaults]

Init1 = ATZ

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Init3 = at+crm=1;+cmux=1;+cps=33;+cta=0

Modem Type = Analog Modem

ISDN = 0

Phone = #777

Modem = /dev/ttyUSB0

Username = <username>
Password = <password>
Baud = 460800

Stupid Mode = 1

Auto DNS

Check Def Route


Step 3: (Connect)

Type wvdial to connect to internet

---

### Post by begemoti on 2009-04-21
thank you

---

