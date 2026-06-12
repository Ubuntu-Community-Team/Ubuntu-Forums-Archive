---
title: "[SOLVED] AT&amp;amp;T wireless broadband problems"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by bradch on 2008-11-30
I have been trying for several days to get this to work. I tried Ubuntu 8.04 and ppp wouldnt work for me. Tried kubuntu 8.04 and kppp would connect but nothing else would see the connection. Now on ubuntu 8.1. It see's the sierra wireless 881u and wants me to configure the connection. I tried leaving the defaults and also changing a few things that seemed to work in kppp on kubuntu. No matter what I try it says network has been disconnected and I can't get it to connect. Getting very frustrated. I want to switch to linux but with no internet I can't.How do I connect?

---

### Post by FreewheelinFrank on 2008-11-30
Is this any use?

[http://allaboutubuntu.wordpress.com/2008/03/19/sierra-wireless-881u-a-great-choice-for-mobile-internet-on-ubuntu/](http://allaboutubuntu.wordpress.com/2008/03/19/sierra-wireless-881u-a-great-choice-for-mobile-internet-on-ubuntu/)

This is actually mobile broadband right? Ubuntu 8.10 has better support for this in Network Manager.

Give the liveCD a shot to test it out.

---

### Post by bradch on 2008-11-30
I am on 8.1 now. Network manager won't connect.

---

### Post by bradch on 2008-11-30
Banging my head against the wall!! This has to be something simple but I am at a loss.

---

### Post by FreewheelinFrank on 2008-12-01
Have you read the link I posted earlier?

> Support for a variety of Sierra Wireless devices has actually existed in the mainline kernel since version 2.6.23, and a driver is available from them to add support to kernel versions as old 2.6.18. That means it would be possible to get supported devices working with Ubuntu versions as old as 7.04 (Feisty Fawn).

The driver, support scripts, and the guide I used to get setup are all available at the Sierra Wireless website. I chose to use the pppd method of installation, as Network Manager doesn’t quite yet seem able to configure this device on its own. I understand that there is a version in development though that plays nice with cellular cards like this. I look forward to that release!

The one gotcha I ran into was needing AT&T’s APN (Access Point Name) and my username and password for configuring the device. I called AT&T and surprisingly was routed to exactly the right person as soon as I said “I’m setting up my 881U on Linux and I need to know the APN and user information I need to put in the configuration.”

They were very helpful and not once did I feel like a second-class customer because I was not using Windows. Good on them.

It turns out that information for AT&T is already entered as examples in the pppd helper scripts, so that call was largely unnecessary, but it was nice to have the information confirmed. In the “gsm_chat” file I set the APN line to “OK ‘AT+CGDCONT=1,”IP”,”ISP.CINGULAR”‘”, and I made no changes to the “gsm” file. After making that one change invoking “pppd call gsm” got me online!

You could try contacting AT&T, as they seem to be helpful, or leave a comment on that blog, as the person concerned seems to be knowledgeable. 

> The driver, support scripts, and the guide I used to get setup are all available at the Sierra Wireless website

Have you obtained these?

---

### Post by bradch on 2008-12-01
I'v tried this and I still can't connect. I have to enter this without the quotes because the quotes grey out the ok button. When I enter this and click ok it tries to connect and says the network has been disconnected. entering pppd call gsm in the command line gets me an error. I will try to contact the writer of this blog. Maybe they can help.

---

### Post by bradch on 2008-12-01
I think I found the problem. Ubuntu is showing the 881 as a usb drive. Now I need to know how to make it see it properly. I'm really new at this.

---

### Post by cozmicharlie on 2008-12-01
What is the output of the command below (type it in a terminal after connecting the modem)?
```
lsusb
```

---

### Post by bradch on 2008-12-01
brad@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 1199:6856 Sierra Wireless, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:c51b Logitech, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
brad@ubuntu:~$ 

It is showing as unmounted and will not mount.

---

### Post by cozmicharlie on 2008-12-01
First install the latest version of network manager from the maintainer. Go here:
[https://launchpad.net/~network-manager/+archive](https://launchpad.net/~network-manager/+archive)
In the dialog box choose Hardy.
Copy and paste the two lines (one at a time) to your software source list.  Go to system>administration>software sources>.  In the menu go to Third Party Software>add then add the two lines one at a time.  Close and reload.  This will update your network manager to the latest version which has better broadband support.

Note, according to the instructions (see below), it is supposed be recognized as a usb device so I think you just need the new network manager. Before you do everything in the instructions, plug it in, right click on the network daemon in the panel and take a shot at setting it up.  Also, you could try this: set up in network manager to connect automatically, exit the compute, plug the device in and restart the computer.  Maybe it will connect.  If this does not work, follow the instructions below.

The instructions for setting it up are found here:.
[http://sierrawireless.custhelp.com/app/answers/detail/a_id/500/session/L3NpZC9GdTYzUmprag==/sno/0](http://sierrawireless.custhelp.com/app/answers/detail/a_id/500/session/L3NpZC9GdTYzUmprag==/sno/0)
You probably have the drivers and may not need the patch.

---

### Post by bradch on 2008-12-02
I tried doing this in ubuntu 8.04 and kubuntu 8.04. Couldn't get it to work. I installed ubuntu 8.10 with the 881 in place. It recognized it and ask if I wanted to configure it. I clicked on it and everything was already filled out. when I clicked ok it said network disconected. I tried changing apn and it didn't help. I think I need to tell it to connect somehow but I'm not sure.

---

### Post by bradch on 2008-12-02
Finally!! This is a bug with the network manager. Just leave all fields blank except phone number.In it enter *99#, and leave everything else blank.Now I am connected with ubuntu. Thanks for the help.:)

---

### Post by cozmicharlie on 2008-12-03
> **bradch said:**
> Finally!! This is a bug with the network manager. Just leave all fields blank except phone number.In it enter *99#, and leave everything else blank.Now I am connected with ubuntu. Thanks for the help.:)

Excellent - I think your post is going to help a lot of people with the same problem.  Glad you got it worked out.

Enjoy!

---

### Post by copai on 2008-12-10
hallo, I am new user for this ubuntu, and this is my first time I am install ubuntu 810, my problem same as haves no incircuit internet, I am not at all understands ubuntu but wish to learn. please help me, how so that my modem earn having internet, always disconnected. My modem sierra 881u. please help me...

---

### Post by cozmicharlie on 2008-12-12
Your modem should be supported in 8.10.  Since you are a new user I will explain this in more detail.  You have in your top panel a network daemon.  It is the icon that looks like two monitor.  This shows all your connections (wireless, wired, 3G).  If you right click on it brings up a dialog box. Go to edit.  Now you should see a tabbed dialog box for wireless, wired, broadband etc.  With your device plugged in go to Broadband and tell me what it says.  FYI - I am traveling for work so it may take me a day to get back to you but I will - be patient.

Also, have you activated your broadband account on a windows computer?

---

### Post by copai on 2008-12-16
> **bradch said:**
> Finally!! This is a bug with the network manager. Just leave all fields blank except phone number.In it enter *99#, and leave everything else blank.Now I am connected with ubuntu. Thanks for the help.:)

thank to @cozmicharlie, my forgiveness late answers. My problems have can be finalized. I follow like the one is upper [by] and this my terminal.

[Dialer Defaults]
Init1 = AT
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","indosatm2"
Stupid Mode = 1
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
; Phone = *99***1#
; Password = indosat
; Username = indosat


In network manager just only put the phone number..  Just leave all fields blank except phone number. soory my inggris is not good.. 

Thx a lot to @cozmicharlie...

---

### Post by cozmicharlie on 2008-12-17
Great copia - glad to know you got it working.

Enjoy!

---

