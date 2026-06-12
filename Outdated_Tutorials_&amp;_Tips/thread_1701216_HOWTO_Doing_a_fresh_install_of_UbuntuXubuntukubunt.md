---
title: "HOWTO: Doing a fresh install of Ubuntu/Xubuntu/kubuntu"
date: 2011-03-06
forum: Outdated Tutorials &amp; Tips
---

### Post by wei2912 on 2011-03-06
Please note this is my first How-To, if there is an error please let me know. I made this with some information from a website and posts i read. 

ONLY Ubuntu is tested, Xubuntu and kubuntu are not.

A fresh install of Ubuntu is necessary if the OS runs slowly. In this guide, i will teach you how to reinstall Ubuntu.

This guide is meant to be used in order. Once you are done with the installation, reboot your computer and check if everything is going well. If the installation fails, repeat the steps. If it still doesn't work, move on to the next set of steps.

[U][B]If you installed Ubuntu/Xubuntu/Kubuntu with wubi.exe (Windows installation):
[/B][/U][COLOR=Red]Step 1:
[COLOR=Black]Boot up windows.
[COLOR=Red]Step 2:
[COLOR=Black]Go to add/remove programs. Remove Ubuntu/Xubuntu/Kubuntu.
[COLOR=Red]Step 3:
[COLOR=Black]Using wubi.exe (If it is no longer with you, download from [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)[COLOR=Red][COLOR=Black]. You can also follow the next set of steps.), install Ubuntu/Xubuntu/Kubuntu.

If it fails, restart. If it still fails, proceed to the next set of steps.
[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]
[U][B]If you do not have a CD/USB device with Ubuntu/Xubuntu/Kubuntu with it, follow these steps:
[/B][/U][COLOR=Red]Step 1:
[COLOR=Black]Download Ubuntu from [http://www.ubuntu.com/desktop/get-ubuntu/download.]("http://www.ubuntu.com/desktop/get-ubuntu/download")
If you are going to install Xubuntu/Kubuntu, download them from [http://www.xubuntu.org/getubuntu](http://www.xubuntu.org/getubuntu) and [http://www.kubuntu.org/getkubuntu](http://www.kubuntu.org/getkubuntu) respectively.
[/COLOR]Step 2:
[COLOR=Black]To create a CD -> Use a burning software and burn the image (iso file) to the blank CD.
To create a USB plug (recommended):
1. Download Universal USB Installer from [http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe)
2. Select Ubuntu Desktop Edition (Kubuntu Desktop Edition and Kubuntu Desktop Edition).
3. Click browse and open the image (iso file).
4. Choose the USB drive and press "Create".

Proceed to the next set of steps. 

[/COLOR][/COLOR]_**If you have a CD/USB device with Ubuntu/Xubuntu/Kubuntu with it, follow these steps:**_
[COLOR=Red]Step 1:[/COLOR]
[COLOR=Black]Reboot your computer with the CD in the CD ROM or the USB device in the USB plug.
[COLOR=Red]Step 2:
[COLOR=Black]Boot up from the CD/USB device. This can be done by editing the BIOS if it does not work.
1. Take a look at the key specified when you boot up the computer.
2. Press that key to enter the BIOS.
3. Find boot order and move the CD/USB option to the top of the list.
4. Save your changes and reboot.
[COLOR=Red]Step 3:
[COLOR=Black]Press try Ubuntu/Xubuntu/Kubuntu.
[COLOR=Red]Step 4:
[COLOR=Black]Run GParted in System -> Administration.
[COLOR=Red]Step 5:
[COLOR=Black]Right click linux-swap and select swapoff. Unmount ext4. Delete ext4 and linux-swap.
[COLOR=Red]Step 6:[/COLOR]
[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]Close GParted and run the installer.

------------------------------------------------------------------------------------------------
If you have any questions, post. :P Hope you enjoy your fresh install.

:KSTo update your new OS, type:
[/COLOR][/COLOR][/COLOR]```

sudo apt-get update && sudo apt-get upgrade

```
[COLOR=Black][COLOR=Red][COLOR=Black][]("http://www.ubuntu.com/desktop/get-ubuntu/download")
[/COLOR][/COLOR][/COLOR]

---

