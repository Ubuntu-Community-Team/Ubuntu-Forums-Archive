---
title: "Installing Broadcom Drivers"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Natron716 on 2008-11-13
I am trying to install the b43 drivers for my Broadcom 4310 wireless minicard but I am running into some trouble.

I ran this to install the firmware:
wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
tar xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta.o


and i have verified that the extracted files do exist in the firmware directory.  Now my card is still running off the wl driver and I don't know what to do next.  Any help would be appreciated.

Thanks,
Nate

---

### Post by igknighted on 2008-11-13
First, you should not ever have to install b43-fwcutter.  That is installed by default in Ubuntu.

Second, blacklist the wl driver and un-blacklist the b43 and ssb drivers.

Third, any reason you are downgrading from wl to b43?  The wl is the best and latest broadcom driver, that should probably be the driver you use.

Fourth, you don't even need to install the firmware for b43 manually.  There is a script in Ubuntu's hardware drivers app that downloads and installs the firmware.  You can run it manually, I'd do a quick forum search for it (I can't remember where it is off the top of my head).

Good luck.

---

### Post by Natron716 on 2008-11-13
hah yes i am kindof fumbling around with linux right now.  it is a learning experience.

the reason i am downgrading is because i cannot connect to WPA or WEP secure networks with the wl driver, nor can I get monitor mode to work.  I will try blacklisting the wl driver, but a quick check shows that neither b43 or ssb drivers are blacklisted.

---

### Post by Natron716 on 2008-11-13
I blacklisted the wl driver, and on restart my broadcom card did not work at all.  It did not recognize an eth1 device...

---

### Post by igknighted on 2008-11-13
> **Natron716 said:**
> I blacklisted the wl driver, and on restart my broadcom card did not work at all.  It did not recognize an eth1 device...

Try 'sudo modprobe b43', and then restart NM (sudo killall NetworkManager; sudo NetworkManager)

---

### Post by Natron716 on 2008-11-13
tried that and it still doesnt work

nate@nate-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:9b:d2:f4:dd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19708 (19.7 KB)  TX bytes:19708 (19.7 KB)

---

### Post by igknighted on 2008-11-13
Can you run the command 'lspci' so we can see exactly what linux is calling the card?

---

### Post by Natron716 on 2008-11-13
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

