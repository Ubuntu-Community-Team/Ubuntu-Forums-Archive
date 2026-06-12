---
title: "ubuntu server restarting instead of shutting down"
date: 2014-08-23
forum: New to Ubuntu
---

### Post by Robin_van_der_Veer on 2014-08-23
[COLOR=#333333][FONT=UbuntuRegular]Whenever I try to shutdown my pc by using `sudo shutdown -... now` (it doesn't matter what I fill in for the ...), it always shutdowns down for about 3-4 seconds, and than just powers up again. I'm sure WOL is disabled, and just to be sure I tested it with ethernet cable unplugged.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]It's a fresh install of ubuntu server 14.04. It's also a new pc so I do not have any prior experience with it.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Any help would be very much appreciated[/FONT][/COLOR]

---

### Post by lah7 on 2014-08-24
Welcome to the forums! The 'sudo shutdown -**...** now' has various parameters which you didn't specify, so I don't know exactly what command you used, as this can affect what happens after Linux is shut down.

What you should use is "[COLOR=#000080]sudo shutdown -**P** now"[/COLOR] or "[COLOR=#000080]sudo poweroff"[/COLOR] to **p**ower it off after it has shut down.
[COLOR=#000080]shutdown -**h** [/COLOR]would **h**alt the system (freeze)
[COLOR=#000080]shutdown -**r **[/COLOR]would **r**estart the system.
[COLOR=#808080](See shutdown --help for more information)

[/COLOR]If you have used the **-P** switch, or the [COLOR=#000080]poweroff[/COLOR] command and it still happens, then it might be the hardware that's preventing the system from powering off. Check the BIOS settings, particularly the power management options. I can't specifically outline what to look for, as it varies on the manufacturer.

---

