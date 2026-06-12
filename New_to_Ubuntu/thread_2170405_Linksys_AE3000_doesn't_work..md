---
title: "Linksys AE3000 doesn't work."
date: 2013-08-26
forum: New to Ubuntu
---

### Post by Vikash_Moelchand on 2013-08-26
Hello,

I just started using Ubuntu. I just can't get my linksys AE3000 adapter to work. I tried to use this guide for it : [http://geekniggle.blogspot.com.au/](http://geekniggle.blogspot.com.au/). But I couldnt get any further then step 2. Does anyone here knows another way to get my adapter to work? Or could anyone help me with this one. I have internet access on my computer now for a little while.

Greetings,

Vikash

---

### Post by Vikash_Moelchand on 2013-08-26
Ok, I think I finished all the steps. I am just not sure if I did it right, because my adapter still doesn't work.

vikash@Vikash:~/Desktop/Linux$ sudo make -j10
[sudo] password for vikash: 
make: *** No targets specified and no makefile found.  Stop.
vikash@Vikash:~/Desktop/Linux$ cd /home/vikash/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0 
vikash@Vikash:~/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0$ sudo make -j10
make -C tools
cp -f os/linux/Makefile.6 /home/vikash/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/os/linux/Makefile
make[1]: Entering directory `/home/vikash/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/tools'
gcc -g bin2h.c -o bin2h
make -C /lib/modules/3.8.0-29-generic/build SUBDIRS=/home/vikash/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/os/linux modules
make[1]: Leaving directory `/home/vikash/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/tools'
/home/vikash/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/tools/bin2h
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-29-generic'
  CC [M]  /home/vikash/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/vikash/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/os/linux/rt3573sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/vikash/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/os/linux/rt3573sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-29-generic'
cp -f /home/vikash/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/os/linux/rt3573sta.ko /tftpboot
vikash@Vikash:~/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0$ sudo make install
make -C /home/vikash/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/vikash/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/vikash/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3573sta.ko /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.8.0-29-generic
make[1]: Leaving directory `/home/vikash/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0/os/linux'
vikash@Vikash:~/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0$ sudo depmod -a
vikash@Vikash:~/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0$ sudo modprobe -v rt3573sta
insmod /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/rt3573sta.ko 
vikash@Vikash:~/Desktop/Linux/DPO_RT3573_LinuxSTA_V2.5.0.0$

---

### Post by Vikash_Moelchand on 2013-08-26
OK.. I know why it isn't working, I have the AE6000, or AC580. Not the AE3000.

---

