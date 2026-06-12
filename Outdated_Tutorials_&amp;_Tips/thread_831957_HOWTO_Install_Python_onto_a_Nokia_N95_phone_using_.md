---
title: "HOWTO Install Python onto a Nokia N95 phone using Ubuntu"
date: 2008-06-17
forum: Outdated Tutorials &amp; Tips
---

### Post by nebc on 2008-06-17
**Overview**

This guide is meant to allow you to connect your Debian based x86 computer with Gnome to your N95 phone via Bluetooth. It also covers how to add a Python interpreter to the phone.

**Software for the Computer**
You will need the following packages on your computer:
> 
gnome-bluetooth
libbluetooth2
gnome-vfs-obexftp
libopenobex1
obex-data-server
bluez-gnome
bluez-utils

Just copy and paste this line of code into the terminal:

```
sudo apt-get install gnome-bluetooth libbluetooth2 gnome-vfs-obexftp libopenobex1 obex-data-server bluez-gnome bluez-utils

```
At time of writing there is a bug in the bluez-utils package that comes with Ubuntu 8.04 which prevents serial port discovery. To see if the bug is fixed check here. If the bug still exists, you can download a working version here.

**Software for the Phone**
You now need to download the Python SDK as well as the Python script shell. These come in several different versions and so you should check the chart on this page to determine what you need. You should download the appropriate .SIS (Symbian Installation Source) files. At the time of writing (June 08) the lastest versions for the N95/N95 8GB were:
> 
   1. PythonForS60_1_4_3_SDK_3rdEd.SIS
   2. PythonScriptShell_1_4_3_3rdEd.SIS 

(NOTE: You can download these files directly onto the phone, the following paragraph describes what to do if you download them via your computer. If you do download via the phone, be sure to get the SDK before the script shell).

Now we're going to transfer the SIS files on your computer to your phone via bluetooth. Open up a terminal and type

```
bluetooth-sendto
```

browse to wherever the SDK SIS file is and select it. Now select your phone as the "destination device" and hit "Connect". After the transfer completes, your phone should beep and say you have a message. Open it, to start the installation process. If you accidentally close the message, go to Main Menu->Messaging->Inbox.

Once the installation completes, repeat the process for the Script Shell SIS. Then go to Main Menu->Applications->Python. In the "Option" tab you should see "Run script", "Interactive console", and "Bluetooth console" (the last one is important for the next step). Hooray!

**Running the Python shell remotely via Bluetooth**

Use this script to start a serial port on your computer. On the phone go from Main Menu->Applications->Python->Options->Bluetooth Console. You should see your computer listed, if not select "More Devices"; the phone will then search for Bluetooth enabled devices in the area.

Once you have selected your computer you should see something like
> 
Connecting to ('<YOUR COMPUTER'S MAC ADDRESS>',2)...OK

At this point you can now run the connect script The terminal should say
> 
"Connected."

Hit 'enter' and now you have an interpreter! To logout all you need to do is hit "Ctrl-D" on an empty line. Note that if you quit, everything dies and to reconnect you'll need to redo the entire process starting with the listen script.
[edit] Oddities

If for some reason a connection persists after it should have died try
```

ps aux | grep krfc

```
If there is a process titled [krfcommd] kill it. That should fix your problems.

[B]References/Sources
[/B]
[http://wiki.opensource.nokia.com/projects/Python_for_S60](http://wiki.opensource.nokia.com/projects/Python_for_S60)
[http://wiki.opensource.nokia.com/projects/PyS60_Bluetooth_console](http://wiki.opensource.nokia.com/projects/PyS60_Bluetooth_console)
[http://crschmidt.net/blog/11/bluetooth-console/](http://crschmidt.net/blog/11/bluetooth-console/)

---

