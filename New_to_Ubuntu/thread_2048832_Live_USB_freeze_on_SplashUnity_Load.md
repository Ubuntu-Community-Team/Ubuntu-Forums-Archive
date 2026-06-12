---
title: "Live USB freeze on Splash/Unity Load"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by UltraNoobian on 2012-08-27
Hi everyone, I'm new here but I've got a little bit of outdated linux know-how.

Briefly, I'm having a problem installing Ubuntu 12.04 (.1) LTS on my desktop and it's driving me mad. Here are some specs first off.
[I]
Gigabyte EP-45 UD3P
Intel Core 2 Quad Q9550
OCZ DDR2 8GB's
Zotac Nvidia 295 GTX
-Hard Drives
[/I][INDENT]*3x Western Digital 500GB*
2x Seagate 500GB
[/INDENT]*TP-LINK 300Mbps Wireless N PCI Adapater TL-WN851ND*

I've tried 2 methods of trying to boot from the GRUB menu
1. Run from USB - Choosing USB as boot device and letting it run from USB
2. Install from USB - Choosing to install Ubuntu from USB in the GRUB loader

#1 - Results in _freeze on splash screen_. All the little holes below the Ubuntu logo are filed.

#2 - Results in successfully passing the splash screen, then after loading in only a few elements (specifically the Grey bar at the top of the desktop with a few icons, Keyboard, Wireless signal strength, Speaker and Shutdown Cog)_ Unity freezes_. You can move the mouse around but cannot use any keyboard shortcuts or mouse actions. I tried to use Ctrl-Alt-F1 and it didn't switch to tty1.

Actions I have tried:

[LIST=1]
[*]Updating BIOS
[*]Disabling all BIOS settings (ie. AHCI/RAID, C2/4E, etc.)
[*]Mem-test (Did 16 Passes without fail)
[*]CPU Test (4 Days of PRIME86 without fail)
[*]Something else.... Forget.
[*]Checksummed ISOs
[/LIST]
I am really stumped. Someone have any ideas? Feel free to ask questions about anything else.


PS. I cannot provide logs (Unless you want me to type out everything that the console spits outs), or screen shots as there is no usably interface on the desktop when I try to load.

---

### Post by UltraNoobian on 2012-08-28
Solved. Must use -NOMODESET option for first boot if I have Nvidia card.
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]
http://ubuntuforums.org/showthread.php?t=1613132[/URL]

---

