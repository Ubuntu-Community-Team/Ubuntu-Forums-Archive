---
title: "Zotac blank screen after shutdown/restart"
date: 2013-09-19
forum: New to Ubuntu
---

### Post by Malzie on 2013-09-19
[SIZE=3][FONT=arial][SIZE=2]
Recently I purchased a Zotac Zbox D525, the machine itself is pretty slick and does everything that I need it to do, but...[/SIZE]

```
**Specs:**
[COLOR=#000000]Chipset: Intel NM10 Express
[/COLOR]Memory: [COLOR=#000000]1GB DDR3-800 SODIMM
Video: Integrated Onboard Intel GMA 3150 Graphics Controller
Hard Drive: 250GB 5400RPM SATA2 
[/COLOR][COLOR=#000000]CPU: Intel Atom Dual-Core Processor D525(1.8 GHz)[/COLOR]
```[/FONT][/SIZE][COLOR=#000000][FONT=arial]

[/FONT][/COLOR]I have prepared a live USB drive and with it I am able to "try" and "install" Ubuntu 13.04, everything works flawlessly. After the initial install, the computer restarts and works fine with the exception of major overscan. Past that when I shutdown the computer or even just restart the computer the screen goes blank and unless I go into the bios or boot selection screen it shows absolutely nothing. To be more specific, even the bios splash screen does not appear. It is just blank. 

I know that it is sending video through the HDMI cable to the television because the TV does not show "HDMI1" on the screen as it does when there is no input. 

When this happens the only thing I can manage is to load bios through hitting delete, or bringing up the boot selection screen via hitting F11. When I hold shift in the attempt to bring up the Grub menu nothing happens.

While I am new to linux, I have seen that others have had similar problems but none seem to be exactly the same. Any and all help is appreciated.

**PS:** I just tried Ubuntu 12.04 thinking that maybe an older, more stable version would be the solution. However, I am met with the exact same problem.

---

### Post by bweinel on 2013-09-19
It sounds like your video driver is either not working properly or detecting a resolution that your monitor doesn't support.

After booting try pressing Ctl-Alt-F1 to see if you can open a bash command shell. If so, the Xorg video driver is likely your issue. 

cheers,
bill

---

