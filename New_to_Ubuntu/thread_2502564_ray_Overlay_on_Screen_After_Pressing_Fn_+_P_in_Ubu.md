---
title: "ray Overlay on Screen After Pressing Fn + P in Ubuntu 22.04 (Wayland) – Brightness Ad"
date: 2024-11-19
forum: New to Ubuntu
---

### Post by myself-usman on 2024-11-19
Hello,
I am experiencing an issue on my Ubuntu 22.04 system (running GNOME Shell with Mutter 42.9 on Wayland). I accidentally pressed the Fn + P key combination, and since then, a persistent **gray overlay** has appeared on my full screen.
While I can adjust the screen brightness by pressing the super(windows) + Brightness keys (with sun icon), this only affects the brightness and **does not remove the gray overlay**.
As a beginner, I took help from ChatGPT to troubleshoot the issue, but unfortunately, I haven't been able to find a solution yet.
[HR][/HR]**[B]Steps I Have Tried**:[/B]


[LIST=1]
[*]Pressed Fn + P multiple times to cycle through display modes (no effect).
[*]Adjusted the brightness slider in **Settings > Displays** (no effect).
[*]Rebooted the system using sudo reboot (overlay remains after reboot).
[*]Tried resetting display settings using:bash

Copy code


xrandr --output $(xrandr | grep " connected" | cut -f1 -d " ") --brightness 1


This changed the brightness but did not remove the overlay.
[*]Reset GNOME settings using:bash

Copy code


dconf reset -f /org/gnome/


Again, this did not fix the overlay issue.
[/LIST]

---

### Post by 1fallen on 2024-11-19
Is It the same on X11 session?

If so then please included this, copy all of it to your terminal
```
[FONT=monospace][COLOR=#000000]gdbus call \ [/COLOR]
--session \ 
--dest=org.gnome.Mutter.DisplayConfig \ 
--object-path /org/gnome/Mutter/DisplayConfig \ 
--method org.gnome.Mutter.DisplayConfig.GetResources


[/FONT]
```

EDIT after I closely read the your post, Please just try this first:
```
[FONT=monospace][COLOR=#000000]mutter --replace
```[/COLOR]
[/FONT]

---

### Post by myself-usman on 2024-11-19
This is what I am getting after trying "mutter --replace"

libmutter-Message: 00:51:02.126: Running Mutter (using mutter 42.9) as a Wayland display server
Failed to setup: Could not take control: GDBus.Error:System.Error.EBUSY: Device or resource busy

---

### Post by 1fallen on 2024-11-19
> **myself-usman said:**
> This is what I am getting after trying "mutter --replace"

libmutter-Message: 00:51:02.126: Running Mutter (using mutter 42.9) as a Wayland display server
Failed to setup: Could not take control: GDBus.Error:System.Error.EBUSY: Device or resource busy

yep it's been a beat since I last used Gnome, but that command will fail on Wayland, Please Logout and select a Xorg session.

---

### Post by Irihapeti on 2024-11-20
*Thread moved to **New to Ubuntu** because it's a support request. (Forum Feedback and Help is for problems with the forums software.)*

---

