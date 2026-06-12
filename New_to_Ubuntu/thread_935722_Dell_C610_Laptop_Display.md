---
title: "Dell C610 Laptop Display"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by jivabill on 2008-10-02
Have a Dell C610 Laptop.  The display is not bright enough for use in outdoor conditions or bright rooms.

When the LT was made it came with Win XP and the Fn key + up or down arrow keys controlled brightness.

There are a number of threads found in Google about this problem in Ubuntu, that is in Ubuntu those keys don't work.  Also I found a thread that described a command line work around but when I try to use it I get an error message, no such file.

this is the command:
echo -n 100 > /proc/acpi/video/VID/LCD/brightness
There is another variation using VGA instead of VID but my system has VID
100 would be the value for max brightness

Anyone has any ideas how to control display brightness on the C610 under Ubuntu 7.10 I would appreciate hearing about them.
Thanks

---

### Post by mike1234 on 2008-10-02
> **jivabill said:**
> Have a Dell C610 Laptop.  The display is not bright enough for use in outdoor conditions or bright rooms.

When the LT was made it came with Win XP and the Fn key + up or down arrow keys controlled brightness.

There are a number of threads found in Google about this problem in Ubuntu, that is in Ubuntu those keys don't work.  Also I found a thread that described a command line work around but when I try to use it I get an error message, no such file.

this is the command:
echo -n 100 > /proc/acpi/video/VID/LCD/brightness
There is another variation using VGA instead of VID but my system has VID
100 would be the value for max brightness

Anyone has any ideas how to control display brightness on the C610 under Ubuntu 7.10 I would appreciate hearing about them.
Thanks


 Strangely enough synaptic has one for Toshiba laptops. Maybe it could be reconfigured for your Dell. 

fnfxd

ACPI and hotkey daemon for Toshiba laptops fnfx enables owners of Toshiba laptops to change the LCD brightness, control, the internal fan and use the special keys on their keyboard (Fn-x combinations, hot-keys). The internal functions will give the possibility to map the Fn-Keys to functions like volume up/down, mute, suspend to disk, suspend to ram and switch LCD/CRT/TV-out. These functions heavily depend on the system and/or kernel configuration. You will need at least a kernel (v2.4.x, v2.5.x, v2.6.x) with ACPI and Toshiba support (CONFIG_ACPI and CONFIG_ACPI_TOSHIBA).

M.

---

### Post by jivabill on 2008-10-02
Hi Mike, and thank you for the info.  I'll check that out and see if I can use it.
Regards
Bill

---

### Post by jivabill on 2008-10-03
Well, it looks like I am going to have to dump Ubuntu and try another distro.  Appears that the brightness settings on my LT are not supported in Ubuntu.  Perhaps in Xubuntu, guess I'll try that first, then maybe Mephis or some other lightweight distro.  Too bad as I will lose all the work I put into getting my Ubuntu install set up so I could play flash and videos with full screen and restricted formats etc.

So that is the latest report.  Looks like I have some work to do.
Bill

---

### Post by jivabill on 2008-10-11
OK, solved the problem.  Found that when I installed Xubuntu 8.04 then in the Desktop Properties dialogs there was a slider for LCD brightness that works perfectly.  So what was wrong is that Ubuntu 7.10 forgot to include support for the Dell LT.  Now with Xubuntu I have it.  Thanks all for the help.
bill

---

