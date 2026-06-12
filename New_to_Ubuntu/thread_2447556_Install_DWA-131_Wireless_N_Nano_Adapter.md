---
title: "Install DWA-131 Wireless N Nano Adapter"
date: 2020-07-21
forum: New to Ubuntu
---

### Post by shahidr100 on 2020-07-21
Hello room
I am new in Linux world. 
I have installed ubuntu server 16.04 without gui. I want to install Dlink DWA-131 wireless n adapter. No matter what I do it does not work.

I followed following:
sudo apt-get install git build-essential
git clone [https://github.com/Mange/rtl8192eu-linux-driver.git](https://github.com/Mange/rtl8192eu-linux-driver.git)
cd rtl8192eu-linux-driver
sudo make
sudo make install

After that i can see some weird wifi info in iwconfig.



I am sorry i m using virtualbox hence could not copy the output so took the screenshot.

lsusb output - attached png file
iwconfig - attached png file
ifconfig - attached png file
dmesg - attached png file

I dont know what to do next. I am unable to connect to any wireless.

Please help me to install this driver.

Thanks

---

