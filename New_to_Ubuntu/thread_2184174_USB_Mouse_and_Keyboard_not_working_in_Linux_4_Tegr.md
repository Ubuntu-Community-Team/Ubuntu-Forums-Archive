---
title: "USB Mouse and Keyboard not working in Linux 4 Tegra"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by sijomathewk on 2013-10-27
Hi

I am a new person in Tegra Linux development. I have Tamontem NG Evaluation board with Tegra 3 Chip. I installed L4T sample file system from NVIDIA tegra Resources ([https://developer.nvidia.com/linux-tegra](https://developer.nvidia.com/linux-tegra)) and installed the file system as described in the documentation provided in NVIDIA site. Already these was an SD card with L4T running. i dont want to change the boot loader. So I copied the boot.scr.uimg to root (/) folder and uImage to boot(/boot/) and it starts booting from the existing SD card. After that while booting, some errors occurred in some Bluetooth devices (there is no bluetooth device in the board). So I disabled Bluetooth by giving the following command

sudo mv /etc/init/bluetooth.conf /etc/init/bluetooth.conf.noexec

Now the problem is that mouse and keyboard are not working. So i cannot login. Even though i installed desktop, the mouse and keyboard are not working. But mouse and keyboard are enumerating. lsusb command is showing the USB mouse and keyboard.

The installed file system is Ubuntu 13.04.
Linux Kernel version is 3.1

What to do.

Please help.Thanks in Advance.

---

