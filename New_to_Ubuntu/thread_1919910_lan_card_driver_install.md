---
title: "lan card driver install"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by nushe on 2012-02-03
Hi guys, i`m new to linux. i tried to install ubuntu server 10.4 64bit, but i can`t make my lan card to work(atheros ar8152-b). i know that there is a thread already about it [http://ubuntuforums.org/showthread.php?t=1505697]("http://ubuntuforums.org/showthread.php?t=1505697") , but still i couldn`t make it work.
this is what i get when i type ifconfig -a
lo    Link encap:Local Loopback
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING MTU:16436  Metric:1
      RX packets:16 errors:0 dropped:0 overruns:0 frame:0
      TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:1040 (1.0 KB) TX bytes:1040 (1.0 KB)

any help will be appreciate, thanks.

---

### Post by duanedesign on 2012-02-04
I [was reading]("http://ubuntuforums.org/showpost.php?p=9446984&postcount=6") that driver is included in compat-wireless, go figure.

To install the latest drivers, open a Terminal and execute the following commands:

```
wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2

tar -xjvf compat-wireless-2.6.tar.bz2

cd compat-wireless*

scripts/driver-select atl1c

make

sudo make install

sudo modprobe atl1c
```

---

### Post by nushe on 2012-02-05
ok i think i found where is the problem. when i type make it shows: command not found, i get the same for apt-get. i don`t have internet on that pc, so i`m using flash drive to copy the files which i need there. what do i need to do to be able to use make? 
and i don`t have a gui, only text mode. thanks

---

### Post by halitech on 2012-02-05
in order to use *MAKE* you need to install the build-essential and checkinstall packages

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

you should be able to install them from the cd

as to the apt-get error, I think you need to use sudo in order to get that to work but it should already be there

---

### Post by nushe on 2012-02-07
hi guys, i was trying to install the network on 10.04 and still couldn`t do it. instead of that i install 10.10 and everything is working now:) thanks for the info anyway.

---

