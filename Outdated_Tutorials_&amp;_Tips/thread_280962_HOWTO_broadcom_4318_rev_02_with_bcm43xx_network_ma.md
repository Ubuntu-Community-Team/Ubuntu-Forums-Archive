---
title: "HOWTO: broadcom 4318 rev 02 with bcm43xx network manager &amp; WEP/WPA on Dapper"
date: 2006-10-20
forum: Outdated Tutorials &amp; Tips
---

### Post by finite9 on 2006-10-20
I could not find a quick, concise guide for this anywhere so I wrote my own.  It's very quick to implement and is an elegant solution as upgrades should not break this (kernel upgrades on Acer hardware are catered for--see the Acer notes) and there is minimal scripting involved--none if you don't own an Acer, but maybe you need another utility to turn on your wireless adapter.

A few caveats: It only runs at 11Mbit, but if like me you only use PC to connect to internet at <8Mbit then it's not an issue.  Some people report it being unstable with bcm43xx driver but I have never had issues.  The only thing is the syslog errors for broken packets.  If it's not an issue for you that syslog gets filled with errors then use this guide.

This was tested on an Acer Aspire 5021WLMi.

Pre-requisites:

clean install of Ubuntu 6.06.1 amd64, but arch. shouldn't matter.
Install all updates as of 2006-10-20 (again; shouldn't matter)
A working wired ethernet connection
Broadcom AirForce54g 4318 (rev 02) adapter.
The universe repository must be enabled.


Open a terminal and cut/paste the following commands (ignore comments)...

echo 'deb http://ubuntu.cafuego.net dapper-cafuego bcm43xx' | sudo tee -a /etc/apt/sources.list
wget http://ubuntu.cafuego.net/969F3F57.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install bcm43xx-fwcutter bcm43xx-firmware

echo 'blacklist ndiswrapper' | sudo tee -a /etc/modprobe.d/blacklist
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

sudo mv /etc/network/interfaces /etc/network/interfaces~
echo 'auto lo' | sudo tee -a /etc/network/interfaces
echo 'iface lo inet loopback' | sudo tee -a /etc/network/interfaces



## ******************** ONLY FOR ACER USERS ********************
#install acer_acpi to turn on wireless adapter through software
#this is the only package that will be manually installed
#as it will be compiled, it works on 32-bit and 64-bit systems whereas acerhk #only works on 32-bit systems AFAIK
#when upgrading kernel, make sure to re-compile/re-install acer_acpi in the new kernel 

wget http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz
tar -xvf acer_acpi-0.3.tar.gz
cd acer_acpi-0.3
sudo apt-get install build-essential linux-kernel-headers linux-headers-$arch linux-headers-´uname -r´
make
sudo make install

echo 'acer_acpi' | sudo tee -a /etc/modules
echo 'pre-up /etc/network/StartAcerWireless' | sudo tee -a /etc/network/interfaces

sudo touch /etc/network/StartAcerWireless
echo 'chmod 777 /proc/acpi/acer/wireless' | sudo tee -a /etc/network/StartAcerWireless
echo 'echo "enabled: 1" > /proc/acpi/acer/wireless' | sudo tee -a /etc/network/StartAcerWireless
echo 'iwconfig eth1 ap any' | sudo tee -a /etc/network/StartAcerWireless
sudo chmod 754 /etc/network/StartAcerWireless
## *************************************************************



Start GDM and from the menu, go to System|Preferences|Sessions|Startup Programs, click the Add button and write in:
nm-applet –sm-disable

reboot PC

When rebooted, left-click on nm-applet and choose to “connect to other wireless network” even if your AP is visible.  Write in the SSID, choose WEP or WPA and enter the password.  Upon connecting nm-applet will ask for a master password for the wallet.  Choose something simple.

DONE!

---

