---
title: "Dual Monitor Setup and Theme/Icon &quot;Problems"
date: 2016-02-02
forum: New to Ubuntu
---

### Post by Jacob_Grishey on 2016-02-02
Hi,

I am having two specific problems with my Ubuntu. I am relatively new to the OS and I have the 14.04 LTS version.

When I boot into Ubuntu, my monitors are mirrored. After about a minute, the monitors return to the usual extended state. (This is the state I want.)

If I try to change the monitor configuration while the monitors are mirrored, I get this error:
[B]
"Failed to apply configuration: %s"

[/B]GDBus.Error:_org.freedesktop.DBus.Error.UnknownMethod: No such interface (Please disregard the _)
'org.gnome.SettingsDaemon.XRANDR_2' on object at path /org/gnome/SettingsDaemon/XRANDR

After the monitors return to the extended state, this error does not happen.

Here is my other problem:

When originally installing Ubuntu, I was able to install the "Flatabulous" theme and the "ultra-flat-icons" icon theme successfully.
However, when I restarted my PC, I was greeted to the original Ubuntu theme. I used Ubuntu-Tweak to apply the themes.
When I go into Ubuntu-Tweak, the themes are still applied and the themes do not change regardless of the option I choose.

Thank you for your help. Please feel free to ask for any information that you may need.

I am also using a NVIDIA GTX 770 Video Card.

---

### Post by Jacob_Grishey on 2016-02-02
Update: I seem to have solved the dual monitor problem by using the NVIDIA Drivers under the Additional Software & Updates Tab, which was accessed by going from System Settings > Software & Updates.

---

