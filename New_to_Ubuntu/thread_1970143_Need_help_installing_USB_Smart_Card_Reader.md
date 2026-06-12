---
title: "Need help installing USB Smart Card Reader"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by Onoku on 2012-04-30
I just got a smart card reader for my laptop and I need help installing the driver. Here are the instructions, I'm not sure how to utilize them... please help.

If the version of  libusb is under 0.1.9 , it need to update to latest one.
Otherwise skip  step1.

=========================================
[Optional]
Step1. Install  libusb

 # tar zxvf  libusb-0.1.12.tar.gz 
 # cd libusb-0.1.12                          
 # ./configure                             
 # make                                    
 # make install          ( Login as a root to install driver )          
========================================= 

Step2. Install  pcsc-lite

 # PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig;export PKG_CONFIG_PATH
 # LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib; export LD_LIBRARY_PATH
 
 # tar xjf pcsc-lite-1.5.5.tar.bz2
 # cd pcsc-lite-1.5.5
 # ./configure --disable-libhal
 # make                                    
 # make install          (Login as a root to install driver)
 
Step3. Install ccid driver
 
 # tar zxvf ccid-1.3.12_alcormicro.tar.gz
 # cd ccid-1.3.12_alcormicro
 # PCSC_LIBS="-L/usr/local/lib -lpcsclite" ./configure --enable-usbdropdir=/usr/local/pcsc/drivers --disable-pcsclite
 # make                                    
 # make install          (Login as a root to install driver)
 
 Note:
 	Make sure pkg-config already installed.
 	./pcscd
 	Add PATH=$PATH:/usr/local/sbin

---

