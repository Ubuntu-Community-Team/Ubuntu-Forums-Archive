---
title: "USB Wifi (Solved)....now wine gives me problems"
date: 2008-07-24
forum: Philippine Team
---

### Post by dynastywarrior on 2008-07-24
I finally succeeded in installing the driver for my Buffalo USB wifi adapter. I used ndiswrapper to install it. This forum is really indispensable....
However, i encountered a new challenge...i'm having some problem installing through wine the configuration software for my usb device. The software only has windows for platform.
Everytime i use wine to install, i always get the message that i should be "admin" from the software itself not from wine.
Can anybody pls. help on how i can overide this....or is there another way of going around this problem....

---

### Post by adredz on 2008-07-24
just an insight..wine may give you problems in such case cos it's just considered as another app with limited privileges. maybe you should set up wine to run with administrative privileges..or maybe wine isn't intended for any system configuration..

---

### Post by loell on 2008-07-24
care to disclose the name of the app?

many windows application doesn't  run in wine.

do check if its compatible using wine's application database

[http://appdb.winehq.org/]("http://appdb.winehq.org/")

---

### Post by dynastywarrior on 2008-07-24
the name is "Client Manager 3" from Buffalo.....

any feedback about this app sir loell?........

if i can't get this running then my usb wifi adapter is useless...right?

is there a workaround for this problem?

actually i emailed the technical staff of buffalo and they said that it(the usb adapter) will work on linux...however they said that they don't support linux so they cannot tell me how to make it work on linux?!....(how inconsiderate bill gates and his cohorts! ey!)

i tried searching for it on wine's appdb but i can't find it...

ubuntuhcl though did say as well that buffalo's usb wifi adpter should work but they have'nt actually tested it....

---

### Post by dynastywarrior on 2008-07-24
do you know of any way i could overide the error sir loell?

---

### Post by dodimar on 2008-07-24
> **dynastywarrior said:**
> the name is "Client Manager 3" from Buffalo.....

any feedback about this app sir loell?........

if i can't get this running then my usb wifi adapter is useless...right?

is there a workaround for this problem?

actually i emailed the technical staff of buffalo and they said that it(the usb adapter) will work on linux...however they said that they don't support linux so they cannot tell me how to make it work on linux?!....(how inconsiderate bill gates and his cohorts! ey!)

i tried searching for it on wine's appdb but i can't find it...

ubuntuhcl though did say as well that buffalo's usb wifi adpter should work but they have'nt actually tested it....

do you really need to install the client program?

when linux detected the USB WiFi adapter, did you check if it's already working (connecting to wireless network)..

---

### Post by loell on 2008-07-24
as pointed out by sir Marvin , you don't need the client manager for buffalo, there is already ubuntu's network manager, you can just **right click** the network manager and **edit wireless networks**

let us know if it works :)

---

### Post by dynastywarrior on 2008-07-25
that is the problem my comrades...

even with the driver for the usb adapter already installed, it still does'nt work....

when i insert the adapter into the usb terminal the computer detects it but ubuntu's network manager does not...

so it leads me to only one thing - install the client manager and let it control the adapter.....

how about if i try to overide the client manager's root only access? is this doable? how? can it be done in wine?

---

### Post by loell on 2008-07-25
then your wifi usb isn't detected yet, ndiswrapper probably isn't working,

the buffalo client manager can not control your wireless usb adapter through wine. actually no win software can control usb devices using wine.

i guess, you'll be going back to square one, which is to try to install your wifi usb adapter driver.


oh and one more thing don't give wine root privilege, it could be dangerous, besides the win software in question won't work anyway.

---

### Post by dynastywarrior on 2008-07-26
i'm a bit confused on what you said sir loell, that ndiswrapper was not working?

i used ndiswrapper to install the driver for the usb adapter, right? do i still need ndiswrapper everytime i plug-in the usb adapter? if the driver was already installed should'nt it start automatically everytime i insert the usb adapter?

i'm confused really coz' i already installed the driver and still it does'nt work? the driver by the way is an INI file.....and ndiswrapper installed it without any hiccup.....

so wine is just good for gaming apps?
:confused::confused::confused::confused::confused::confused::confused:

---

### Post by dynastywarrior on 2008-07-26
by the way, since that you've mentioned it, i actually gave wine a sudo one time bec of that admin thing with that client manager...but afterwards i did that rm -rf command and re-installed it again with wincfg...

was it enough to bail myself out of danger?

---

### Post by loell on 2008-07-26
don't worry, this particular software doesn't pose a security threat, but from now then on, don't do root with wine. ;)

---

