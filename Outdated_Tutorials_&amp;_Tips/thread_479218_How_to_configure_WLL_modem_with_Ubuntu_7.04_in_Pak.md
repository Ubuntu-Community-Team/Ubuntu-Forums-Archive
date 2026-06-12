---
title: "How to configure WLL modem with Ubuntu 7.04 in Pakistan"
date: 2007-06-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Nizar on 2007-06-20
Hi people, 

As it has been observed that most of the times, WLL phone is detected by Ubuntu 6.06 onwards by plugging in the USB, I thought to cut down the lengthy procedure I wrote in SPIDER Magazine, which contained a lot of debug / detection details. Here's the quick guide that works on desktop / laptop and will take lot lesser time of your's as compared to pervious one! But previous is still intact and appears at the end for reference.

==== Quick Guide ====

1. Insert the USB cable of WLL phone in PC. Ensure that its other end is securely attached with the phone.

2. Login as root and go to Applications > Terminal. Enter command wvdialconf at the prompt. Ubuntu searches for a modem and finds the attached USB modem – evident by the output lines saying:

Found an USB modem on /dev/ttyACM0.
Modem configuration written to /etc/wvdial.conf.

3. Go to the menu bar Places > Computer > File System > ETC folder and open wvdial.conf file. Remove leading semi-colon character from the lines supplying username, password and phone number and complete the lines by entering correct values. Plus, add one more line setting Stupid Mode to 1. The updated wvdial.conf file should now look like this (order of lines may differ – it does not matter):

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
ISDN = 0
New PPPD = yes
Modem = /dev/ttyACM0
Baud = 460800
Phone = #777
Username = [email]vwireless@ptcl.com[/email]
Password = ptcl
Stupid Mode = 1 

4. In the Terminal window, type wvdial and wait for the lines to appear showing DNS addresses, confirming successful Internet connection, e.g.:

--> primary   DNS address 211.94.65.97
--> pppd: x[08][06][08]&#65533;[10][06][08]
--> secondary DNS address 202.125.148.204
--> pppd: x[08][06][08]&#65533;[10][06][08]

5. To exit any time, press CTRL+C twice in the Terminal window. To connect again, simply type 'wvdial' in Terminal window.

========


(Note: My article in Mar 2007 issue of SPIDER Magazine found its way on a blog. I am pasting it for users who are looking to get WLL phone working in Pakistan).

Here's the blog I have referred to in the above line. Thanks for spreading the word Javed!
[http://sbjaved.blogspot.com/](http://sbjaved.blogspot.com/)


Getting Ubuntu Online with Wireless Modem

Getting Internal Modems (winmodems) to work under Linux is a daunting task...even for the pros. It holds back many users from experiencing what Linux has to offer...and that goes especially for Pakistani users. Thankfully WLL (CDMA) Phones have made it easier to get online with Linux. These phones double as a USB Modem and hook into service provider's own network keeping things simple. Read on to know how to set up a WLL Wireless Phone under Ubuntu.

(Credit: This guide originally appeared in SPIDER issue March 2007 and was written by Nizar Diamond Ali. Kudos to him!)

This guide was tested on my configuration [and theoretically should work for better ones]:

Intel Pentium 4
512MB RAM
Ubuntu 6.06.1 LTS (“Dapper Drake”)
ZTE Phone Set (Qualcomm CDMA Technology MSM)

Now Diamond's guide wants you to login as 'root' but I succeeded in performing it without it. Just 'sudo' does fine.

STEP 1 – Plug in the V-Phone and verify auto-detection

Plug in the USB Cable that came with your set into the PC (make sure set is turned ON, there is an ON/OFF button at the back). Now to check whether the phone has been auto-detected, open the Terminal and enter the following command:

dmseg

A probe for attached devices and interfaces is performed. You have to check the existence of the following lines:

[4294697.728000] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
[4294697.731000] usbcore: registered new driver cdc_acm
[4294697.731000] drivers/usb/class/cdc-acm.c: v0.23:USB Abstract Control Model driver for USB modems and ISDN adapters

This gives the confirmation that the connected phone has been detected as a USB Modem and its device location is ttyACM0 (try to remember this). If you are having trouble sifting through the output of dmesg, try:

dmseg > Desktop/info.txt

This will create a text file named 'info.txt' on the Desktop (assuming you are still in /home)

Lets verify this USB Modem detection output further. At the terminal, type:

cd /dev
ls

This again shows a lengthy output but this is alphabetically ordered so it won't take much time to verify the existence of ttyACM0.

Finally, perform a third and final check on the auto-detection of USB Modem. At the terminal, type:

cd /
cat proc/modules

The list that appears should show cdc_acm as:

cdc_acm 13344 0 – Live 0xd0a25000

and

usbcore 129668 3 cdc_acm,uhcl_hcd, Live 0xd08c9000

This is not alphabetically listed, so it would be a good idea to export the output and search 'acm' through the text editor.

A final note on checking, if cdc-acm is not detected so far, it is suggested to check the following command:

cd /sbin
modprobe cdc-acm

If there is no output, it means everything is fine, otherwise 'FATAL: Module cdc-acm not found' error appears.

STEP 2 – Setting up config files (this step can be omitted - as these files are auto-updated)

Open the file 'chap-secrets' in the etc/ppp folder through the terminal:

sudo gedit /etc/ppp/chap-secrets

It will ask for your login password and then open the file in a text editor. Now enter the following line at the end (enclosed in quotes and seperated by dots and asterik)

“vwireless@ptcl.com”.*.”ptcl”

Now save it and exit from the editor to get back into the terminal. Back in the terminal open the file 'pap-secrets':

sudo gedit /etc/ppp/pap-secrets

Enter the following line at the end of the file (this time without the dots)

“vwireless@ptcl.com”*”ptcl”

Save and exit from editor.

STEP 3 – Setting up the Dialer

Execute the Dialer configuration by using the following command at terminal:

wvdialconf

It would give a lengthy output which basically means that no modem was detected over the serial interfaces, but one was detected over ttyACM0, and a safe speed has been identified. Also initial configuration has been written in the wvdial.conf file (the file that is read ti dial internet connections) which will be used as default.

Now open the file /etc/wvdial.conf and add the following settings in addition to default settings. By that i mean that your wvdial.conf file should have a section as the one shown below, in addition to default settings:

[Dialer ptcl]
Modem Name = CDMA
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2+FCLASS=0
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
PPPD Options = crtcts multilink
Init1 = ATZ
Phone = #777
Username = [email]vwireless@ptcl.com[/email]
Password = ptcl
Baud = 460800

Save and exit.

[NOTE: Please note presence of Stupid Mode = 1 w/o which connection will not be made!]

Note that the Dialer configuration added only the default settings and values and we have to specify valid username, password and a dialer name. This will ensure that any further auto-configuration would not delete the Dialer defined in this file (i.e. 'ptcl')

STEP 4 – Connecting to the Internet

We are all ready and set to take off at this point. Enter the following command at the terminal to dial:

sudo wvdial ptcl

The output would be something like this:

--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ ATZ OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2+FCLASS=0 ATQ0 V1 E1 S0=0 &C1 &D2+FCLASS=0 OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Mon Apr 2 16:33:24 2007
--> Pid of pppd: 4990
--> Using interface ppp0
--> pppd: &#65533;&#65533;[05][08](&#65533;[05][08]
--> pppd: &#65533;&#65533;[05][08](&#65533;[05][08]
--> pppd: &#65533;&#65533;[05][08](&#65533;[05][08]
--> pppd: &#65533;&#65533;[05][08](&#65533;[05][08]
--> pppd: &#65533;&#65533;[05][08](&#65533;[05][08]
--> local IP address 10.0.205.167
--> pppd: &#65533;&#65533;[05][08](&#65533;[05][08]
--> remote IP address 2.2.2.2
--> pppd: &#65533;&#65533;[05][08](&#65533;[05][08]
--> primary DNS address 211.94.65.97
--> pppd: &#65533;&#65533;[05][08](&#65533;[05][08]
--> secondary DNS address 202.125.148.204
--> pppd: &#65533;&#65533;[05][08](&#65533;[05][08]

Note that the DNS Detection at the last four lines is an indication that the connection has been successfully made and you are ready to surf the internet. Leave the terminal running and browse the internet through the default Firefox browser.
To Disconnect press CTRL+C twice in the terminal and the prompt will appear again indicating that connection has been terminated.

At this point, the following three files are updated automatically in the /etc/ppp folder:
1.resolv.conf (holds DNS entries)
2.pap-secrets
3.chap-secrets

---

### Post by sbjaved on 2007-06-26
You could have had the courtesy to link to my [ blog]("http://sbjaved.blogspot.com"), from where you copy/pasted.

---

