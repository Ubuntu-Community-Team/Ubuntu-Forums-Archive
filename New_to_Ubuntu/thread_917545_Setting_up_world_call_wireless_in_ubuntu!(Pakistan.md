---
title: "Setting up world call wireless in ubuntu!(Pakistan)"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by yam.matt on 2008-09-12
Hello All of you Ubuntu and Linux users. I am a new memeber of Ubuntu forums and this is my first post. Now to my problem. My problem is that my World call wireless huawei CDMA set is not working under Ubuntu, so I am not being able to connect to the internet. I have searched the whole forums but not found anything that satisfies me. it has got a serial to USB connetctor which Ubuntu is not identifying, although it is detecting it. I also have read Saeed Javed's guide but its not for Ubuntu 8.04 and World call wireless. In my opinion those CDMA phone sets are only available in Pakistan, so only a Pakistani user can help me with my problem. I will be really thankful to those who will help me.

---

### Post by ahsanghalib on 2009-02-13
Hi, 

I have the wordcall wireless set of LG. I have made the following configuration and it is working well. I have ubuntu 8.04. 

Step 1:

First made it connect with the usb cable to the system. and then go to the terminal and enter the following command:

dmesg

and check that your hardware is detected or not.

Second is to again verify the hardware by the following commands:

cd /dev
ls

and you will see the ttyACM0 in the list.

if so then your hardware is detected. 

Step 2:

Now enter the following command to the terminal

sudo gedit /etc/wvdial.conf

and pate the following in it:

[Dialer Defaults]
Modem Name = CMDA
Init1 = ATZ
Init2 = at+crm=1;$lgpkt=3
Modem Type = USB Modem
Baud = 115200
PPPD Options = crtcts multilink
Modem = /dev/ttyACM0
Stupid Mode = 1
ISDN = 0
Phone = #777
Password = wcall
Username = wcall

and save and exit the gedit. 

now enter 

wvdial 

in the command and see the internet will connect. 

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: at+crm=1;$lgpkt=3
at+crm=1;$lgpkt=3
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Feb 13 18:43:31 2009
--> Pid of pppd: 26375
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> local  IP address 10.172.104.201
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> remote IP address 172.16.12.2
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> primary   DNS address 203.81.192.10
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]

this will appear in the command.

left it and open the firefox and browse..

ENJOY.

---

### Post by shavaiz786 on 2010-08-06
> **yam.matt said:**
> Hello All of you Ubuntu and Linux users. I am a new memeber of Ubuntu forums and this is my first post. Now to my problem. My problem is that my World call wireless huawei CDMA set is not working under Ubuntu, so I am not being able to connect to the internet. I have searched the whole forums but not found anything that satisfies me. it has got a serial to USB connetctor which Ubuntu is not identifying, although it is detecting it. I also have read Saeed Javed's guide but its not for Ubuntu 8.04 and World call wireless. In my opinion those CDMA phone sets are only available in Pakistan, so only a Pakistani user can help me with my problem. I will be really thankful to those who will help me.
well my brother I am suffering the same problem no one answers.

---

### Post by shavaiz786 on 2010-08-06
> **shavaiz786 said:**
> well my brother I am suffering the same problem no one answers.
but there is a good news too it works with ubuntu 9.04.... i tried it if u have 9.04 than u r lucky.

---

### Post by shavaiz786 on 2010-08-06
> **shavaiz786 said:**
> but there is a good news too it works with ubuntu 9.04.... i tried it if u have 9.04 than u r lucky.
Please click one of the Quick Reply icons in the posts above to activate  Quick Reply.

---

### Post by Sundu on 2012-05-15
> **ahsanghalib said:**
> Hi, 

I have the wordcall wireless set of LG. I have made the following configuration and it is working well. I have ubuntu 8.04. 

Step 1:

First made it connect with the usb cable to the system. and then go to the terminal and enter the following command:

dmesg

and check that your hardware is detected or not.

Second is to again verify the hardware by the following commands:

cd /dev
ls

and you will see the ttyACM0 in the list.

if so then your hardware is detected. 

Step 2:

Now enter the following command to the terminal

sudo gedit /etc/wvdial.conf

and pate the following in it:

[Dialer Defaults]
Modem Name = CMDA
Init1 = ATZ
Init2 = at+crm=1;$lgpkt=3
Modem Type = USB Modem
Baud = 115200
PPPD Options = crtcts multilink
Modem = /dev/ttyACM0
Stupid Mode = 1
ISDN = 0
Phone = #777
Password = wcall
Username = wcall

and save and exit the gedit. 

now enter 

wvdial 

in the command and see the internet will connect. 

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: at+crm=1;$lgpkt=3
at+crm=1;$lgpkt=3
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Feb 13 18:43:31 2009
--> Pid of pppd: 26375
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> local  IP address 10.172.104.201
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> remote IP address 172.16.12.2
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> primary   DNS address 203.81.192.10
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]

this will appear in the command.

left it and open the firefox and browse..

ENJOY.

i have tried this procedure bt ttyACMO is not displayed in the list. what to do??? plz help

---

