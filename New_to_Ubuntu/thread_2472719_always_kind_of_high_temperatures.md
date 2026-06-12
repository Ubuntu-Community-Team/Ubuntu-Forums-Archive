---
title: "always kind of high temperatures"
date: 2022-03-10
forum: New to Ubuntu
---

### Post by kitcarson03 on 2022-03-10
Hi, i've bought a Lenovo Ideapad gaming 3 and installed Lubuntu with Lxqt 21.10.
I've also installed latest nvidia drivers version 470.
with prime-select ondemand settings temperature where always hight also after a long period idle, after switch to prime-intel (thanks nvidia) mode i managed to decrease temperature a bit but it is still higher than windows one (which was cold after idle). Is there some settings i can tune to avoid this temperature issue?

thanks

---

### Post by mastablasta on 2022-03-10
temperature is a cause of work in background. you could check if there is any process running in background. other than that the only thing that could help are better drivers, which is all in nvidia's hands.

---

### Post by kitcarson03 on 2022-03-10
is there a tool you can suggest me to monitor the process running over time so that i can check what is using processor or gpu?

---

### Post by Impavidus on 2022-03-11
There's top to tell you what's using the CPU, plus some variations (htop, system monitor).

But it could very well be that the nvidia drivers on Linux are not as good as those on Windows. Then it's up to nvidia to make better drivers.

Sometimes temperatures are simply not reported correctly. Can you actually feel it's warmer on Linux?

---

### Post by kitcarson03 on 2022-03-11
i can definitely feel higher temperatures on Linux by touching the bottom of the laptop

---

### Post by mezigy on 2022-03-11
Purchase laptop cooling pad.

---

### Post by DuckHook on 2022-03-11
It's a bit of a dark art, but here are the power management and tweaking tools that I use on my laptops:
```
duckhook@Zeus:~$  apt show tlp
Package: tlp
Version: 1.3.1-2
Priority: optional
Section: utils
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Raphaël Halimi <raphael.halimi@gmail.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 354 kB
Depends: lsb-base, hdparm, iw | wireless-tools, pciutils, rfkill, usbutils
Recommends: tlp-rdw, ethtool
Suggests: tp-smapi-dkms, acpi-call-dkms, smartmontools, linux-tools-generic | linux-tools
Conflicts: laptop-mode-tools
Homepage: https://linrunner.de/tlp
Task: ubuntu-mate-core, ubuntu-mate-desktop
Download-Size: 70.0 kB
APT-Sources: http://ca.archive.ubuntu.com/ubuntu impish/main amd64 Packages
Description: Save battery power on laptops
 TLP is an advanced power management tool for Linux. It comes with a
 default configuration already optimized for battery life. At the same
 time it is highly customizable to fulfil specific user requirements.
 .
 TLP supplies separate settings profiles for AC and battery power and can
 enable or disable Bluetooth, Wi-Fi and WWAN radio devices upon system startup.
 .
 For ThinkPads it provides a unified way to configure charging thresholds and
 recalibrate the battery for all models which support it (via tp-smapi or
 acpi-call).
 .
 TLP is a pure command line tool with automated background tasks, it
 does not contain a GUI.
```
```
duckhook@Zeus:~$  apt show thermald
Package: thermald
Version: 2.4.6-3
Priority: optional
Section: admin
Origin: Ubuntu
Maintainer: Colin King <colin.king@canonical.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 588 kB
Depends: libc6 (>= 2.34), libdbus-1-3 (>= 1.9.14), libdbus-glib-1-2 (>= 0.88), libevdev2 (>= 0.9.1), libgcc-s1 (>= 3.3.1), libglib2.0-0 (>= 2.37.3), liblzma5 (>= 5.1.1alpha+20120614), libstdc++6 (>= 11), libupower-glib3 (>= 0.99.0), libxml2 (>= 2.7.4), lsb-base (>= 3.0-6)
Homepage: https://01.org/linux-thermal-daemon
Task: ubuntu-mate-core, ubuntu-mate-desktop, ubuntu-budgie-desktop, ubuntu-budgie-desktop-raspi
Download-Size: 209 kB
APT-Manual-Installed: no
APT-Sources: http://ca.archive.ubuntu.com/ubuntu impish/main amd64 Packages
Description: Thermal monitoring and controlling daemon
 Thermal Daemon is a Linux daemon for monitoring and
 controlling platform temperatures. Once the system
 temperature reaches a certain threshold, the Linux daemon
 activates various cooling methods to try to cool the system.
```
```
duckhook@Zeus:~$  apt show laptop-mode-tools
Package: laptop-mode-tools
Version: 1.74-1.1
Priority: optional
Section: universe/utils
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Ritesh Raj Sarraf <rrs@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 418 kB
Depends: lsb-base (>= 3.0-10), util-linux (>= 2.13), psmisc
Recommends: hdparm, sdparm, ethtool, net-tools, wireless-tools, udev, python3-pyqt5, rfkill
Suggests: acpid | apmd | pbbuttonsd | pmud
Conflicts: noflushd
Homepage: https://github.com/rickysarraf/laptop-mode-tools
Download-Size: 88.2 kB
APT-Sources: http://ca.archive.ubuntu.com/ubuntu impish/universe amd64 Packages
Description: Tools for Power Savings based on battery/AC status
 Laptop mode is a Linux kernel feature that allows your laptop to save
 considerable power, by allowing the hard drive to spin down for longer
 periods of time. This package contains the userland scripts that are
 needed to enable laptop mode.
 .
 It includes support for automatically enabling laptop mode when the
 computer is working on batteries. It also supports various other power
 management features, such as starting and stopping daemons depending on
 power mode, automatically hibernating if battery levels are too low, and
 adjusting terminal blanking and X11 screen blanking
 .
 laptop-mode-tools uses the Linux kernel's Laptop Mode feature and thus
 is also used on Desktops and Servers to conserve power
```
```
duckhook@Zeus:~$  apt show indicator-cpufreq
Package: indicator-cpufreq
Version: 0.2.2-0ubuntu3
Priority: extra
Section: universe/python
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Artem Popov <artfwo@ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 333 kB
Depends: python3:any (>= 3.2~), python3, python3-dbus, python3-gi, gir1.2-appindicator3-0.1, libcpufreq0
Homepage: https://launchpad.net/indicator-cpufreq
Download-Size: 25.5 kB
APT-Sources: http://ca.archive.ubuntu.com/ubuntu impish/universe amd64 Packages
Description: CPU frequency scaling indicator
 Indicator applet for displaying and changing CPU frequency on the fly. It
 provides the same functionality as the GNOME CPU frequency applet, but doesn't
 require GNOME panel and works under Unity.
```
Note that these are almost all CPU tweaking/setting tools. If your overheating problem is GPU, then they will be of limited help, though the power-saving modes may still prove useful.

---

### Post by kitcarson03 on 2022-03-12
thanks, i'll try that ones

---

### Post by DuckHook on 2022-03-12
> **kitcarson03 said:**
> thanks, i'll try that ones
Try them only one at a time and add only enough to get decent results. Some of these may conflict with each other.

When running system utilities, less is always better.

---

### Post by ActionParsnip on 2022-03-14
Do you have the latest BIOS?

---

