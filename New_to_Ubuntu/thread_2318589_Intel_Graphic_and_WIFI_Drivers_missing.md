---
title: "Intel Graphic and WIFI Drivers missing"
date: 2016-03-27
forum: New to Ubuntu
---

### Post by asif9 on 2016-03-27
Hello,

I am new to ubuntu or any linux OS, switched from windows7.

I have installed Ubuntu Desktop 14.04.4 LTS (64bit) on my desktop pc Intel Q35 Chipset.

Currently i am facing these issues:
1. The Intel Graphic driver is not install and the display resolution is too large 1024px on 22" screen. So how do i install the correct Intel driver.
2. I have WIFI and LAN adapters, but ubuntu showing only wired connection which is LAN. So how do i enable the WIFI connection?


Thanks

---

### Post by QIII on 2016-03-27
Hello!

It is generally best to use a "one problem, one thread" approach.

Threads started with several questions tend to get confusing very quickly.  

The first two you listed are probably fairly straight forward, so you're probably OK.  However, the last is not a simple question.  I would recommend editing that one out and starting a new thread in the Programming sub-forum.

---

### Post by asif9 on 2016-03-27
Thanks for the tip, i have removed the additional question.

---

### Post by grahammechanical on 2016-03-27
The Intel graphic drivers should be installed by default. If we select About this computer in the power/cog menu we will open System Settings at the Details page. What does that say about your graphics set up.

While you have System Settings open go to Software & Updates>Additional Drivers tab. You need to be connected to the internet and to wait for the utility to do its job. What video driver does it say is activated?

while you are in Additional Drivers is it offering a WiFi driver? The WiFi driver may already be installed. In the Network Manager drop down menu is there a tick against Enable Networking? And Enable WiFi?

You also need to make sure that the WiFi adapter is switched on. If the machine is a laptop you may need to activate a keyboard combination to switch on the WiFi adapter. Also, If WiFi is switched off in Windows 7 than the WiFi adapter will still be switched off in Ubuntu.

Regards.

---

### Post by asif9 on 2016-03-27
The Display window in System settings showing "Unknown Display".

The Additional Drivers tab not showing anything, it takes few seconds to load and then shows an empty page.

The network manager dropdown menu on top/right have only Enable Networking option Enable Wifi option is not there.

The Wifi adapter is ON and its working fine on windows 7.

---

### Post by jeremy31 on 2016-03-27
Post ```
lspci -nnk
``` results from terminal using code tags

---

### Post by lynx6 on 2016-03-28
This command: ***lspci -nnk*** is to know the kernel module for this video chipset?

---

### Post by jeremy31 on 2016-03-28
> **lynx6 said:**
> This command: ***lspci -nnk*** is to know the kernel module for this video chipset?

It will display everything connected to a pci slot along with the devices ID and kernel module if one is loaded
I could have added a filter to only see the video and networking
```
lspci -nnk | egrep -iA2 'vga|net'
```

---

### Post by mastablasta on 2016-03-29
you can copy and paste the commands into terminal. also it might be good to give some system specs.

edit. How to get your threads answered quickly: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by retr02 on 2016-03-29
Some drivers are probably not enabled in the "Additional drivers" section. Try running an update and upgrade before.

---

### Post by Rob Sayer on 2016-03-29
You are simply not going to get any Intel video drivers in Additional Drivers.  Intel doesn't really do binary drivers.  This ain't Windows.  There are linux driver downloads for intel (and AMD) cards from the manufacturers but I won't touch that stuff with a 10 foot pole unless it's a card that's too new, which is not your problem.

According to this ...

[https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Third_generation](https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Third_generation)

... you have a 2007 vintage Intel Bearlake series GMA, but since you can't always trust Wikipedia, copy/paste these into terminal:

```
sudo lshw -C video
```

and

```
glxinfo | grep OpenGL
```

N.B. I actually use Mint nowadays so I forget if you get glxinfo by default.  If you get an error on the last command install mesa-utils.

---

### Post by lynx6 on 2016-03-30
> [COLOR=#000000]It will display everything connected to a pci slot along with the devices ID and kernel module if one is loaded[/COLOR]
[COLOR=#000000]I could have added a filter to only see the video and networking[/COLOR]

This command is very interesting.
Thank you.

---

