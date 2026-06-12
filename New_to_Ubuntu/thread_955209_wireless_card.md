---
title: "wireless card"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by chilimac02 on 2008-10-22
I'm beginning to think I was dreaming when I thought I could get wifi working...

I have a broadcom wifi card... I'm running Kubuntu 8.04... I have checked out the website: [http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new)

when reading at that site, I was told to run some commands, the first series worked... the second didn't
the commands to run were:
Use version 4.150.10.5 of Broadcom's proprietary driver.
Download and extract the firmware from this driver tarball:

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o

Note that you must adjust the FIRMWARE_INSTALL_DIR path to your distribution. The standard place where firmware is installed to is /lib/firmware. However some distributions put firmware in a different place. 

the export command worked fine...
the wget command did not. I can manually (firefox) download the file, but it will not download from within komand prompt. 

Help? I'm desperate here folks...

Is wpa2 a pipe dream?

---

### Post by igknighted on 2008-10-22
> **chilimac02 said:**
> I'm beginning to think I was dreaming when I thought I could get wifi working...

I have a broadcom wifi card... I'm running Kubuntu 8.04... I have checked out the website: [http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new)

when reading at that site, I was told to run some commands, the first series worked... the second didn't
the commands to run were:
Use version 4.150.10.5 of Broadcom's proprietary driver.
Download and extract the firmware from this driver tarball:

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o

Note that you must adjust the FIRMWARE_INSTALL_DIR path to your distribution. The standard place where firmware is installed to is /lib/firmware. However some distributions put firmware in a different place. 

the export command worked fine...
the wget command did not. I can manually (firefox) download the file, but it will not download from within komand prompt. 

Help? I'm desperate here folks...

Is wpa2 a pipe dream?

Did you try the "hardware drivers" program (Or in Kubuntu is it called Jockey)?  Those steps should all be automated for you.  You just need to be connected to the internet.

That is a very technical way of saying: download that file, extract it (as you would a zip file), and run the b43-fwcutter application (no need to download it, the proper version comes installed on ubuntu... just type b43 in a terminal and hit tab).  Also, that whole export thing is really pointless.  Just cd to the directory it tells you the wl_apsta_mimo.o is in and type: 'b43-fwcutter -w /lib/firmware wl_apsta_mimo.o'.  As always, hitting tab once you start a command or file/folder will autocomplete for you.

EDIT: run the command 'lspci | grep network' first and post the results, your wireless card might be one of the anomalies that doesn't work with b43.

---

