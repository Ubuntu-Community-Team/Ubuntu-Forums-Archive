---
title: "Tried to install NVIDIA drivers, now 12.04 won't boot. Recovery mode hangs."
date: 2012-06-25
forum: New to Ubuntu
---

### Post by K0j0 on 2012-06-25
Hey there. I'm new to the forums but not exactly new to Ubuntu. I've been running through a maddening gauntlet of issues for the last couple of days that have led me quite far away from the original problem I was trying to solve. I'm really shaving the yak here. Here's the situation.

I had 12.04 installed and running fine but without multiple monitor support.

Could not install additional drivers because jockey-gtk and jockey-text always crashed (DBus.Error.NoMemory)

Started playing with settings, removed NVIDIA settings from startup applications (I think this is my main problem)

Downloaded proprietary NVIDIA drivers and killed XServer process (this is when things went bad)

Upon restart, unable to log in as my user. A blank screen appears then the login screen reappears.

Restarted in recovery mode and attempted to install NVIDIA drivers. Received warning that I was running in runlevel 1 and that I should switch to runlevel 3. I switched to runlevel 3 which took me away from the command line and returned me to the GUI login screen I could not advance past. (Now it gets weird)

Restarted again in recovery mode but now I never reach the command line because the initialization for recovery mode hangs at a certain spot. It always hangs at the line
[1.7562961] firewire_core: created device fw0: GUID 00dc100000094e01, S400

The funny thing is I don't have firewire on this machine so I'm not sure what that line is about.

I've tried to boot from grub with the setting blacklist=firewire_core but grub doesn't seem to save my settings when I edit an entry. Also, it seems to restart my machine when I choose boot from the edit entry screen. I'm about to create a DVD and try to boot from the disk.

Anyone have any idea how I can get recovery mode working again? Thanks, in advance.

---

### Post by bogan on 2012-06-25
Hi!,** KOjO**,

Have you tried pressing 'Ctrl+Alt+F1'>6 to get a text Terminal log-in prompt ??

Chao!,** bogan**.

---

### Post by ranger1021994 on 2012-06-25
You can boot into non-gui mode??...as bogan said
I had same problem but with my ATI drivers nd my recovery mode also workd..
i can help with ATI...
1 : i uninstalled fglrx drivers
2 : purge xorg driver (ati)
3 : reinstalled libgl1-mesa-glx nd -dri
4 : dpkg-reconfigure xserver-xorg
5 : sudo reboot
nd my PC was fixed..see if sumthing like this works for u :) :)

---

