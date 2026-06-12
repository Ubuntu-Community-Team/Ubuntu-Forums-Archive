---
title: "Simplified Intel 32 Bit Nvidia Linux 8756 Driver Install"
date: 2006-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by nudnik on 2006-04-27
Simplified Intel 32 Bit Nvidia Linux 8756 Driver Install 

Terminal: 

sudo apt-get install build-essential bin86 kernel-package

sudo apt-get install libqt3-headers libqt3-mt-dev

Go to [www.nvidia.com](www.nvidia.com) and download the IA32 8756 driver to the desktop.

Press control-alt-F1 to exit the graphical interface. 

Log back into your account if needed.

Stop X server....

Terminal:

sudo /etc/init.d/gdm stop

Go to the directory where the Nvidia driver resides.

Terminal:

cd Desktop

Go root

Terminal:

sudo -s

Activate the installer.

Terminal:

sh (name of the driver)

Installer will run. Message will appear stating there is no pre-compiled driver for your system, will ask to check. It will not find one. It will then ask to compile one based on your kernel. Answer OK. 

The driver will be compiled and installed. The installer will then ask if you wish it to configure your settings to ensure all goes well once you reboot. Answer OK.

You are done! Reboot and hopefully all will be well.

---

