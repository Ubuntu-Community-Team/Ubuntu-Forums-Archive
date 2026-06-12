---
title: "Keyboard and mouse become unresponsive frequently"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by omegacrown on 2014-01-06
Hello,


I use an external wireless Logitech keyboard and mouse and have been having major issues. Very frequently (about once every half hour) the keyboard becomes completely unresponsive (both the one on the laptop and the external one), and although I am able to move the mouse, it does not respond as it should. This has been going on for many weeks now. I have tried both the Unity and Gnome 3 desktop environments as well as different versions of Ubuntu.


I have found these two workarounds:
1. Change to any tty by doing Ctrl-Alt-Fx, then switch it back - Ctrl-Alt-F7
2. Unplug the wireless USB adapter for the keyboard and mouse and plug it back in


Are there any system logs I can check that may reveal the underyling problem? Or is there any known solution?

Please let me know if you need any other information/logs, etc.



Thank you for your efforts,
John

---

### Post by hoopia on 2014-01-06
Can you please provide hardware specs, specifically your motherboard?

Have you tried other mouse/keyboard combos?

---

### Post by omegacrown on 2014-01-07
The laptop is an HP Pavilion dv6. This is the motherboard info:
# dmidecode 2.11
SMBIOS 2.6 present.

Handle 0x0005, DMI type 2, 16 bytes
Base Board Information
    Manufacturer: Hewlett-Packard
    Product Name: 366B
    Version: 06.1D
    Asset Tag: Base Board Asset Tag
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: Base Board Chassis Location
    Chassis Handle: 0x0006
    Type: Motherboard
    Contained Object Handles: 0


I have tried two sets of keyboard/mouse combos
1) The built-in laptop ones
2) External wireless Logitech MK320 keyboard and mouse combo

Thank you,
John

---

### Post by hoopia on 2014-01-07
So we'll need to figure out what is occurring at the time of the freeze. Can you leave a program such as **htop **running for 30 minutes and see what is the active process during failure?

edit:

Also take a look at this solution, you may want to try booting into recovery and trying it with ACPI off:
[http://windowssecrets.com/forums/showthread.php/157789-SOLVED!-Ubuntu-13-10-keybored-and-mouse-stops-working-after-some-time!](http://windowssecrets.com/forums/showthread.php/157789-SOLVED!-Ubuntu-13-10-keybored-and-mouse-stops-working-after-some-time!)

---

