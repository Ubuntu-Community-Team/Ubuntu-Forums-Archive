---
title: "Having a hard time using wine"
date: 2024-06-17
forum: New to Ubuntu
---

### Post by fluffycookie7 on 2024-06-17
Hi everyone, hope this is in the right spot. I have ubuntu noble freshly installed on my laptop. I will be donating this device to a school or church. They may want to install windows applications so i want to get it ready to do so. I installed wine according to the instructions here [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu) but for some reason the applications don't open with the wine app loader. I installed the nobule 24.02 version and did the devel option as well. I could use some assistance. Thanks!

---

### Post by grahammechanical on 2024-06-17
What Windows applications? Have you looked in the wine applications database to see how well wine runs those applications?

[https://appdb.winehq.org/](https://appdb.winehq.org/)

Wine is more successful running applications that run on older versions of Microsoft Windows. 

Run

```
winecfg
``` 

and select an appropriate Windows version.

Do these applications have install or setup exe files?

Run

```
wine explorer.exe
```

That will give you a Windows type file manager. Use it to browser to the location of the applications install/setup exe file and double click.

See how it goes

Regards

---

### Post by TheFu on 2024-06-17
WINE only works with about 20% of Windows applications.  Expecting too much from it is a common misconception.  

It most definitely is not a way to run very many MS-Windows programs.  

Every program I've ever tried to get working under WINE needed a dedicated WINEPREFIX and different DLLS and settings, via winetricks, setup.  It definitely wasn't click and run - ever.  There are front-end tools that claim to make specific programs run under WINE. Those typically have been paid programs for very specific uses, like running old MS-Office versions, but definitely NOT all MS-Office programs.

The better method is to install native Linux programs that fill the same needs as the MS-Windows programs.  LibreOffice is an example.

There is no magic answer for running MS-Windows programs under Linux. Sorry.

---

### Post by fluffycookie7 on 2024-06-18
Thank you very much for this info! I tried winecfg and i got an error "wine: could not load kernel32.dll, status c0000135". i googled that error and it turns out i had to delete the /.wine directory and now it's working! I can now use winecfg and wine explorer.exe. I successfully ran some windows installers also. Thanks for the assistance.

EDIT:
I was trying to quote you 
 	[**[COLOR=#000000]grahammechanical[/COLOR]**]("https://ubuntuforums.org/member.php?u=1087323")  your commands helped me succed.

---

### Post by TheFu on 2024-06-18
explorer.exe is a good test case, but not really useful, since there are 5-20 other native file managers on Linux with built-in capabilities that are far beyond what Exploder.exe provides.

Installers often work even then the installed program does not. Full testing of each installed program under WINE is necessary.  Every time WINE gets updated, things break and other things start working. 

To quote others, just use the "Reply with Quote" button.

---

### Post by fluffycookie7 on 2024-06-18
> **TheFu said:**
> WINE only works with about 20% of Windows applications.  Expecting too much from it is a common misconception.  

It most definitely is not a way to run very many MS-Windows programs.  

Every program I've ever tried to get working under WINE needed a dedicated WINEPREFIX and different DLLS and settings, via winetricks, setup.  It definitely wasn't click and run - ever.  There are front-end tools that claim to make specific programs run under WINE. Those typically have been paid programs for very specific uses, like running old MS-Office versions, but definitely NOT all MS-Office programs.

The better method is to install native Linux programs that fill the same needs as the MS-Windows programs.  LibreOffice is an example.

There is no magic answer for running MS-Windows programs under Linux. Sorry.

Installing and using the Ubuntu operating system like a windows product is absurd. I'm grateful that wine exists and it being able to install 20% of windows applications is an incredible feat. From what I've seen and with working on Ubuntu it is a premier product, it's quite enjoyable.

---

