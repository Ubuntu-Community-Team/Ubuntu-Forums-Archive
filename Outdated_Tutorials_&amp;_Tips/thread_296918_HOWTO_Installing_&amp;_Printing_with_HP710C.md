---
title: "HOWTO: Installing &amp; Printing with HP710C"
date: 2006-11-10
forum: Outdated Tutorials &amp; Tips
---

### Post by patrick295767 on 2006-11-10
Hi,

1/ if you have parallel / usb adapter, you might type : ```
sudo lsusb
``` to check your printer.

2/ the script to install the printer HP Deskjet 710C (as root / sudo):
```


clear
echo "================================"
echo " January 2006 "
echo " Installation of HP Deskjet 710C "
echo " Ubuntu Linux "
echo " (for Breezy or Dapper or ...)"
echo "================================"
echo " "
cd /tmp
mkdir /etc/cups
wget http://patrick295767.sitesled.com/miniram/HP-DeskJet_710C-pnm2ppa.ppd
cp /tmp/HP-DeskJet_710C-pnm2ppa.ppd  /etc/cups/
apt-get update
apt-get -f -y     install   
apt-get -f -y     install   kprinter
apt-get -f -y     install   xmessage
apt-get -f -y     install    gnome-panel
apt-get -f -y     install    cupsys
apt-get -f -y     install    cupsys-bsd
apt-get -f -y     install    cupsys-client
apt-get -f -y     install    
apt-get -f -y     install    gnome-cups-manager


#- linuxprinting.org printer support - database for Gimp-Print printer drivers
# I permit to remove hplip
apt-get -f -y  remove   hplip 

apt-get -f -y     install   
apt-get -f -y     install   kprinter
apt-get -f -y     install   xmessage

apt-get -f -y     install    gnome-panel
apt-get -f -y     install    cupsys
apt-get -f -y     install    cupsys-bsd
apt-get -f -y     install    cupsys-client

apt-get -f -y     install    foomatic-filters-ppds
apt-get -f -y     install   foomatic-rip
apt-get -f -y     install    pnm2ppa
killall -HUP cupsd
/etc/init.d/cups restart
/etc/software/init.d/cups stop
/etc/software/init.d/cups start
/etc/init.d/cupsys stop
/etc/init.d/cupsys start
xmessage "I start kprinter; Please when adding the printer, choose the driver /etc/cups/HP-DeskJet_710C-pnm2ppa.ppd; Enjoy!"
kprinter &
# I prefer kprinter than gnome-panel
#gnome-cups-manager&
```

Enjoy Printing !

---

