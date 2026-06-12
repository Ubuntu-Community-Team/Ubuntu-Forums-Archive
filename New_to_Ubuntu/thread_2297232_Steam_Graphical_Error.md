---
title: "Steam Graphical Error"
date: 2015-10-01
forum: New to Ubuntu
---

### Post by Ryan_ONeil on 2015-10-01
I have installed the windows version of Steam with Play On Linux.  I  wanted to play my Windows games on Linux (My distribution is Ubuntu  MATE) through steam, but when I start Steam up there is a black shadow  of nothingness that follows it around and when I open the friends list  and drag it around it is bugging out and leaves images of its self  behind ( It looks like when you would win in an old school version of  Solitaire when the cards would jump out at you), but wait there’s more!   When I tried to launch Insurgency (the game I wanted to play) an error  code comes up saying:
[B]
Engine Error[/B]

Device Info:
Marked unsupported: 0
Supports PCF Sampling: 1
DriverName: "ATI Radeon HD 5600 Series"
VendorID: 0x1002, DeviceID: 0x68D8
DriverHigh: 0x00060011, DriveLow: 0x000A0500
DXLevel: 95, MinDXSupportLevel: 90, 
MaxDXSupportLevel: 95


Please help, I love using Ubuntu and I want to learn to do everything I can do on Windows on here.

---

### Post by android4682 on 2015-10-08
> **Ryan_ONeil said:**
> I have installed the windows version of Steam with Play On Linux.  I  wanted to play my Windows games on Linux (My distribution is Ubuntu  MATE) through steam, but when I start Steam up there is a black shadow  of nothingness that follows it around and when I open the friends list  and drag it around it is bugging out and leaves images of its self  behind ( It looks like when you would win in an old school version of  Solitaire when the cards would jump out at you), but wait there’s more!   When I tried to launch Insurgency (the game I wanted to play) an error  code comes up saying:
[B]
Engine Error[/B]

Device Info:
Marked unsupported: 0
Supports PCF Sampling: 1
DriverName: "ATI Radeon HD 5600 Series"
VendorID: 0x1002, DeviceID: 0x68D8
DriverHigh: 0x00060011, DriveLow: 0x000A0500
DXLevel: 95, MinDXSupportLevel: 90, 
MaxDXSupportLevel: 95


Please help, I love using Ubuntu and I want to learn to do everything I can do on Windows on here.

It's probably because you try to run steam in a virtual windows environment and then tried to run a game in there.
You should install the linux verison of steam. [http://store.steampowered.com/about/](http://store.steampowered.com/about/)
And then try to play games.

I must warn you though not all steam games works/are available on linux.

I hope this would help you. ;)

---

### Post by tristan16 on 2015-10-08
> **android4682 said:**
> It's probably because you try to run steam in a virtual windows environment and then tried to run a game in there.
You should install the linux verison of steam. [http://store.steampowered.com/about/](http://store.steampowered.com/about/)
And then try to play games.

I must warn you though not all steam games works/are available on linux.

I hope this would help you. ;)

The game in question (Insurgency) is only available for Windows and Mac, but a lot of Steam-Windows games work fine through Wine.

Now, back to the question. What drivers do you have installed? See if it works when you have ATI proprietary drivers installed.

---

