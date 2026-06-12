---
title: "Resolution autostart on Lubuntu"
date: 2020-10-07
forum: New to Ubuntu
---

### Post by vect13 on 2020-10-07
Hi,

I am a beginner on Lubuntu (and Linux in general). I am running Lubuntu atm on a virtual machine (VirtualBox), but eventually I would like to permanently switch to Linux on my work laptop (or at least, with dual boot).
My current problem is the following one: everytime I restart my virtual machine, the resolution switches back to the default one. I managed to set a custom resolution thanks to a few threads I found online (using xrandr by creating and adding modes), such that after typing the commands, I can just type xrandr -s 1920x1080 -r 60 . But when I restart the machine, this doesn't work anymore.

I read online that I could add the commands I wished into the autostart file. All the threads I saw said to modify the autostart file located at: ~/.config/lxsession/Lubuntu/autostart . However, there is no lxsession directory in .config. In .config, there is an autostart directory, and in it there is a file called: "lxqt-config-monitor-autostart.desktop", so I opened it with nano. I tried to type the commands I wished in it (and also in Exec, separated by a ; ), but when i reboot nothing happens. Some people said to modify the autostart in /etc/xdg/lxsession/LXDE/autostart , but again, there is no lxsession directory. 

Somebody could help?

Current version: Ubuntu 19.10

---

### Post by CelticWarrior on 2020-10-07
> [COLOR=#000000]Current version: Ubuntu 19.10[/COLOR]

Welcome. Please upgrade to a supported release.

---

### Post by vect13 on 2020-10-07
I just upgraded to 20.04. I thought it was up-to-date when doing apt-get update and apt-get upgrade, but I hadn't checked the manual stating to do full-upgrade and do-release-upgrade.
Anyways, I still cannot find the lxsession directory that people seem to say on other threads. Is the autostart file in .config the one I should modify?

---

### Post by CelticWarrior on 2020-10-07
I don't use Lubuntu so can't help you with that except to mention that I think you've been reading some old tutorials that likely aren't applicable now. Lubuntu used to have LXDE but now it has LXQt (the change was before 19.10 so the same method should work for 20.04 but old method shouldn't for 19.10 or 20.04).

---

### Post by vect13 on 2020-10-07
Ah indeed that does make sense! I thought it was still LXDE, thanks for the heads up. I am gonna read LXQt threads, and I will let you know

---

### Post by TheFu on 2020-10-07
~/.xprofile is the old school method, from before all the DE stuff.
Create that file if it doesn't exist and put the commands you want run there.  
```
 /usr/bin/xrandr -s 1920x1080 -r 60
```
Though I think the output device i missing in tat command, but if you only have 1 monitor, perhaps it is fine?

I don't know if Wayland supports it or not.

That file is handy for mouse, touchpad settings and to launch some programs and place them at every GUI login too.  Like a screensaver or to do some global key remapping or to remove bluetooth kernel modules.  Sometimes having the old way makes tings easier than searching for a screen buried in some settings program. OTOH, if you don't know about these .dotfiles, tat is just as hidden.

---

### Post by guiverc on 2020-10-07
I'd suggest looking up the manual - [https://manual.lubuntu.me/stable/3/3.2/3.2.10/monitor_settings.html](https://manual.lubuntu.me/stable/3/3.2/3.2.10/monitor_settings.html)

The manual doesn't include a picture of the Monitor.Settings -> Setup tab for a monitor, but you'll see resolution, ability to make the display the primary (or extends..) etc.

You click APPLY to make the change for the current session only.
Clicking SAVE will cause the setting to be saved for subsequent settings.

Note: The settings only impact LXQt (ie. take effect the moment you're logged in), and not `sddm` or the display manager/greeter. It has it's own settings (covered in the manual elsewhere).

Once I change the settings for monitors, I've had them stick for  subsequent boots in Lubuntu. Settings in VMs can be somewhat limited by the HOST settings (t*hough I've not had issues with VMs in VirtualBox unless the host settings were incorrect*).

The last four Lubuntu releases have used  LXQt, so changing settings intended for the older desktop may have no or  negative effects (depending on what is changed).

---

### Post by vect13 on 2020-10-07
Thank you both for your replies.

TheFu> So I created with nano the .xprofile file (in ~/.xprofile), and I typed the following commands inside
```
xrandr --newmode "1920x1080_60.00" 173.00 1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr -- addmode Virtual1 1920x1080_60.00
xrandr -s 1920x1080 -r 60
```

(What I wrote after newmode for the first command came from cvt 1920 1080 60. If I type directly ```
xrandr -s 1920x1080 -r 60
``` in the terminal I get an error message.)
After that, I saved it and reboot the machine, but it still goes back to 800x600, and I have to type again in the Terminal the three commands above. Did I do something wrong?


guiverc> Thanks for the link. I tried to apply and save it as you suggested, but I still end up with 800x600 when starting again the virtual machine.
[COLOR=#DD4814]guiverc[/COLOR]

---

### Post by TheFu on 2020-10-07
```
/usr/bin/xrandr --output Virtual-1  --mode 1680x1050
```
is exactly what I have in my 20.04 KVM VM.
The mode is already valid according to xrandr. I didn't need to force anything.

I connect via spice using virt-viewer.  The login screen is whatever resolution, but just after login, when my desktop, fvwm, is running on regulus, the resolution changes. The exact connecton command is:
```
/usr/bin/virt-viewer --connect qemu+ssh://hadar/system regulus &
```

I have to say that spice completely rocks!  hadar is the VM host system.  I'm connecting from a laptop named posc. 

That's all the details I have to share.

---

