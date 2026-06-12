---
title: "Driver"
date: 2014-03-14
forum: New to Ubuntu
---

### Post by josip3 on 2014-03-14
Hey everybody,

Today i setup my first linux "Ubuntu 13.xx x64", and already 2 hours I am trying to get graphic driver to work, when i go in settings it shows "Gallium 0.4 on AMD REDWOOD",
my graphic card is Ati Radeon HD 5650, I tried everything, some commands that i found on net, tryed download from amd site and run it with root and ./, but there is always some kind of 
dh...something error and i always can not get in my desktop any more so i must remove it from terminal mode,
I wonder what should I do, I am new linux user, it may be easyest thing to do, but i dont know how ...

---

### Post by deadflowr on 2014-03-14
AMD Redwood is the "codename" of the open source driver that was made for your card.
So, in that regard, you already have a graphics driver installed.

If, however, you feel that the quality of that driver is somewhat not up to what you want.
Try installing the closed source drivers through Ubuntu's driver program.

To do so, open the Ubuntu menu
(click the top icon in the left side panel; the launcher) 
and either search the apps, or type
"Software and Updates"

In this go to the section marked 
"Additional Drivers"

You should get several drivers to choose from.
Which one you choose will be entirely up to you.

If things go awry, look here for possible help on what to do
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

Good Luck, in any event.

---

### Post by josip3 on 2014-03-15
Well my graphic and screen rly looks nicely, but my main problem is when i try run CS GO from PlayOnLinux i get this error:

"Your graphic driver does not support all features (CSM) needed to run this game.

Device Info:
Marked unsupported: 0
Supports PCF Samling: 1
DriverName: "AMD Radeon HD 6600M Series" <- My graphic card is 5650
VendorID: 0x1002, DeviceID: 0x6741
DriverHigh: 0x0006000E, DriverLow: 0x000A21E9
DXLevel: 95, MinDXSupportLevel 90, MaxDXSupportLevel: 95

Thank you.

---

