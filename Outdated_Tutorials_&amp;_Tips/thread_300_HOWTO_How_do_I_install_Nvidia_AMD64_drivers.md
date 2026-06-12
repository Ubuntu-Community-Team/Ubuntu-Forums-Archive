---
title: "HOWTO: How do I install Nvidia AMD64 drivers?"
date: 2004-10-12
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu-geek on 2004-10-12
1. Download the NVIDIA package
wget [http://download.nvidia.com/XFree86/Linux-x86_64/1.0-6111/NVIDIA-Linux-x86_64-1.0-6111-pkg2.run](http://download.nvidia.com/XFree86/Linux-x86_64/1.0-6111/NVIDIA-Linux-x86_64-1.0-6111-pkg2.run)

2. Made sure I had the latest kernel image and kernel headers
sudo update
-- still the same as of 2004/10/07
sudo apt-get install linux-image-2.6.8.1-3-amd64-generic
sudo apt-get install linux-headers-2.6.8.1-3-amd64-generic
sudo apt-get install linux-headers-2.6.8.1-3

3. Rebooted my machine for new kernel to take effect
4. At the GDM login screen I got to a console (One cannot install the driver while X is running) by pressing CTRL-ALT-F1
-- you should be at a prompt now, login using your user details and
sudo killall gdm

5. Run the NVIDIA application from step one
sudo ./NVIDIA-Linux-x86_64-1.0-6111-pkg2.run

-- Go through the menu options, saying yes to install and accept the license, said no to try and download stuff from nvidia as kernel module did not exists. The setup program picked up I had the correct headers for the kernel and built the driver. It then proceeds to try and install the linked modules in /usr/lib64 however it fails with some messages. Do not abort here and just continue through the messages, and continue not to abort the process. At the end you should have a completed message coming back.

-- To check one should have
/lib/modules/2.6.8.1-3-amd64-generic/kernel/drivers/video/nvidia.ko

6. Add nvidia to /etc/modules
sudo gedit /etc/modules
-- move to the bottom of the file and add nvidia

7. Update the X config file
sudo gedit /etc/X11/XF86Config-4
-- In the Section "Module" part of the file make sure you comment out
(#)
Load "dri"
Load "GLcore"
-- and make sure that
Load "glx"
-- is in this section

-- Then change the graphics device in the relevant section
-- It would most probably be
Driver "nv"
-- which should changed to
Driver "nvidia"

8. Reboot the machine and hope for the best ;-)

This howto was taken from the Ubuntu Mailing List thanks to Leon Vismer

---

### Post by goatboy on 2004-10-12
Actually, linux-restricted-modules and nvidia-glx for amd64 are in restricted now. amd64 users can follow the same guide[1] as i386 users for the nvidia binary.

[1] [http://wiki.ubuntu.com/BinaryDriverHowto](http://wiki.ubuntu.com/BinaryDriverHowto)

---

### Post by kio_http on 2009-11-10
Its also possible from the hardware driver manager or at NVIDIA site.

---

