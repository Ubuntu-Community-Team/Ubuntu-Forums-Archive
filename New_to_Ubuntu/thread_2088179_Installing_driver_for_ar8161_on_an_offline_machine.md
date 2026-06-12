---
title: "Installing driver for ar8161 on an offline machine"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by mvalviar on 2012-11-25
Hello,

I just built a new pc and it currenly has no networking as it uses Atheros AR8161.

I have a laptop running on 12.04 lts. Is there away for me to build the driver on my laptop and copy and install it to the new pc (including depenencies)?

Regards,
mvalviar

---

### Post by personalpc on 2012-11-25
on the working machine with internet:

wget -O- [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2012-07-03-pc.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2012-07-03-pc.tar.bz2) 

then copy that compat-wireless*.tar.bz2 to a usb drive

insert the install cd & usb stick into the machine that needs the drivers and run in terminal (use your thumbdrive in place of USBTHUMB): 

sudo apt-get install build-essential
cd /media/USBTHUMB/
tar -x compat-wireless-2012-07-03-pc.tar.bz2
cd compat-wireless-2012-07-03-pc
./scripts/driver-select alx
make
sudo make install


This is the original post [Eth Controller]("http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller")

---

