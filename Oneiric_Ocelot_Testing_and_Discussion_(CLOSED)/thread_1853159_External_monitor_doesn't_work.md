---
title: "External monitor doesn't work"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tsg1zzn on 2011-10-01
After installing Oneiric beta and installing the updates, I can't get any image on my external monitor. Please help.

The "displays" window shows just one display (my laptop display). I know the external monitor is connected and working, because the loading screen was shown on it.

In 11.04 I used the noveau driver, but I can't find this for 11.10.

---

### Post by effenberg0x0 on 2011-10-01
In my case, using nvidia-proprietary drivers (not Nouveau) version 280.13, I have to boot the PC with the second monitor plugged in and turned on, otherwise I can't add it later. Then I see the second monitor on nvidia-settings and can properly configure it, etc. Doing that, it works OK for me. Maybe its the same thing for Nouveau, but I am not sure.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2011-10-01
In my case, using nvidia-proprietary drivers (not Nouveau) version 280.13, I have to boot the PC with the second monitor plugged in and turned on, otherwise I can't add it later. Then I see the second monitor on nvidia-settings and can properly configure it, etc. Doing that, it works OK for me. Maybe its the same thing for Nouveau, but I am not sure.

PS: The "Displays" windows is always wrong, showing only one monitor. nvidia-settings show them both, considering the secondary was plugged in and on when the machine booted.

Regards,
Effenberg

---

### Post by tsg1zzn on 2011-10-01
> **effenberg0x0 said:**
> In my case, using nvidia-proprietary drivers (not Nouveau) version 280.13, I have to boot the PC with the second monitor plugged in and turned on, otherwise I can't add it later. Then I see the second monitor on nvidia-settings and can properly configure it, etc. Doing that, it works OK for me. Maybe its the same thing for Nouveau, but I am not sure.

Regards,
Effenberg

I had the same behaviour as you with 11.04. The problem is, with 11.10, no matter what I do, the second monitor does not show up.

---

### Post by effenberg0x0 on 2011-10-01
This is really weird. Wild guessing: 

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo lightdm restart (or sudo reboot now, which is probably better)

If it doesn't fix it, my best advice would be remove / reinstall of nvidia drivers.

Is there anything different special about your secondary monitor, in terms of connection, technology, etc that we should take under special consideration?

Regards,
Effenberg

---

### Post by MAFoElffen on 2011-10-01
> **effenberg0x0 said:**
> In my case, using nvidia-proprietary drivers (not Nouveau) version 280.13, [COLOR=Red]I have to boot the PC with the second monitor plugged in and turned on, otherwise I can't add it later[/COLOR]. Then I see the second monitor on nvidia-settings and can properly configure it, etc. Doing that, it works OK for me. Maybe its the same thing for Nouveau, but I am not sure.

PS: The "Displays" windows is always wrong, showing only one monitor. nvidia-settings show them both, considering the secondary was plugged in and on when the machine booted.

Regards,
Effenberg
That happens to me in both 11.04 and 11.10. nVidia says their driver loads the nvidia kernel, then searches through the ports for connected devices by looking for EDID data.  If no device found, then it turns off that port.

Using the nouveau driver, I had autoconnect on that one (at least on my laptop, as I remember)... but that was with Intel GPU  (<-- I can't test on this one anymore as my "gamer" girlfriend "adopted" my laptop!!! I don't touch it anymore except for maintenance, updates and upgrades)

On nvidia-- To get around that for my Media Servers (where their display is not turned on while booting), I generated a local EDID file and configured the xorg.conf to force output to that port... That way it turns on that port, which is assigned to a screen/monitor and it uses the edid file for its settings, so it finds that EDID data even though that monitor was turned off.
```
# In Device Section[FONT=monospace]
[/FONT]Option "ConnectedMonitor" "CRT-0"
Option "CustomEDID" "CRT-0:/etc/X11/crt0.edid" 

```> WARNING: this option overrides what display devices are detected by the NVIDIA kernel module, and is very seldom needed. You really only need this if a display device is not detected, either because it does not provide DDC information, or because it is on the other side of a KVM (Keyboard-Video-Mouse) switch. In most other cases, it is best not to specify this option.On a laptop, using these options will use more battery as that port will be on all the time.

---

### Post by tsg1zzn on 2011-10-02
> **effenberg0x0 said:**
> This is really weird. Wild guessing: 

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo lightdm restart (or sudo reboot now, which is probably better)

If it doesn't fix it, my best advice would be remove / reinstall of nvidia drivers.

Is there anything different special about your secondary monitor, in terms of connection, technology, etc that we should take under special consideration?

Regards,
Effenberg
I reinstalled a different nvidia driver from the list (I have no idea what the differences are) and rebooted *twice*. Now the monitor shows up in nvidia-settings, but trying to use it resulted in a garbled screen the first time, when I tried again it crashed compiz...

---

