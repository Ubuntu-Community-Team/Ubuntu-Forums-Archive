---
title: "Ubuntu slow on third boot only + Other problems"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by WindPower on 2008-08-24
(This is my whole Linux story, most parts are probably irrelevant).

I'm semi-new to Linux land, having it used thoroughly enough through Live CDs/USB drives and the like. I enjoyed it, so I decided to install it alongside Windows. During installation, I had to use the ACPI workarounds, because the regular installation just shows a black screen and stays like that forever. Installation with ACPI workarounds went fine, and Ubuntu successfully booted, yay~
First thing I did was to update all packages, and rebooted immediately after. Ubuntu rebooted fine and asked me if I wanted to use a closed-source binary driver for my ATI graphics card. I enabled it, rebooted, and Gnome refused to show anything past the login screen. Screw it - I uninstalled Ubuntu (from Windows), installed Kubuntu, did the same thing (ACPI workarounds, update all, get closed-source driver), and same thing happened: Black screen past login screen in KDE. So I uninstalled Kubuntu and reinstalled Ubuntu. ACPI workarounds again, update all again, but this time I kept Ubuntu's default graphic driver. I installed CCSM and a few other packages, and rebooted (because I wanted to, not because I was asked to do so), so this was Ubuntu's third boot (at least the third boot of this Ubuntu installation), and the whole system got VERY slow (As an example, it takes more than 15 seconds for the System or Applications menu to open). So I said screw it again, and I reinstalled Ubuntu again. ACPI workarounds again, update again, reboot, Ubuntu works all right, and, on the next boot, unusuable system. Since the system became unusuably slow on the third boot every time, I decided to install Ubuntu again, update all on first boot, do **absolutely nothing** on second boot (not even log in), and see what would happen on the third boot: Same thing! And same problems for all subsequent boots. The system monitor, which takes tens of minutes to open, shows very little CPU and RAM usage.
Here am my specs:
[LIST][*]Pentium 4 CPU, 2.40 GHz, overclocked and hyperthreaded
[*]1.5 GB RAM
[*]I gave Ubuntu from 8 to 15 GB of disk space on my main C: drive (NTFS, 120 GB)
[*]Graphics card: ATI Radeon X800 XL
[*]Network card: Intel(R) PRO/1000 CT Network Connection - Packet Scheduler Miniport (1000Mb/s)
[*]Two old CRT monitors, but I shut off the secondary one (the one plugged on my graphics card), set to 1024x768 at 85 Hz[/LIST]
If this problem is unsolvable for some reason, don't worry much about it, I'm getting a whole new computer in a week, so it doesn't matter much, I'll still install Ubuntu on it.

I've got three other problems, which are more of an annoyance than real problems:
- I can't get dual-screen working, but then again I never tried to. I'll give Xinerama a shot when I get my new desktop (with an nVidia) :)
- On Windows, each monitor is set to 1280x960 at 72 Hz. On Ubuntu, I can set the monitor to 1280x960, but can't set the frequency to 72 Hz, while I know my monitor is capable of it (since it works on Windows). I get headaches whenever the refresh rate is lower than 70 Hz, and the highest resolution in whichc I can get a refrsh rate higher than that is 1024x768, which goes up to 85 Hz on Ubuntu. Is there any way I can "force" Ubuntu to set the refresh rate to 72 Hz?
- Flash hogs the sound! As soon as Flash gets a handle on the sound output, I can't get Amarok or any media player to play anything (I get a "device is busy" error), no matter what engine I select in Amarok's preferences.

---

### Post by talsemgeest on 2008-08-24
Try doing the memtest and see if that is the problem.

---

### Post by WindPower on 2008-08-30
Nope, memtest went just fine, no errors :???:

---

