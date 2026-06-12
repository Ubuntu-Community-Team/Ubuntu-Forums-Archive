---
title: "ipw3945 drivers"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by pps80 on 2008-04-22
hi guys i am trying to work with aircrack on Ubuntu7.10 gutsy gibson, i am having problem putting my ipw3945 wireless card in to injection mode. I have followed the procedure from [http://www.aircrack-ng.org/doku.php?id=ipw3945](http://www.aircrack-ng.org/doku.php?id=ipw3945)
It seems to installed ok
done this..

sudo apt-get install build-essential
sudo apt-get install libssl-dev

wget [http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2)
tar -xjf ipwraw-ng*
cd ipwraw-ng
make
sudo make install
sudo make install_ucode
echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw
sudo depmod -ae

sudo modprobe -r ipw3945
sudo modprobe ipwraw

Tilll here everything is fine 

for configuring the wireless card it says on the website 
"The device name must not “eth1” it can be “wifi0” or what ever. You can see this with “iwconfig”. "
But when i do iwconfig i got it on eth1


ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any 
          Mode:Monitor  Channel=6  Bit Rate=54 Mb/s

I want to know i can chage it from eth1 to something else and if i did so will i be able to use airodump cause i am using eth1 for that and for Kismet as well.

I am new to unix just started using it few days back. I will really appreciate your help guys.
And i am sorry if i am asking something really easy n stupid... 

Thanks in advance

---

### Post by subzero316 on 2008-04-22
Yea ,ofcourse thatz the beauty of unix based OS(cuztomization). May be u need a little tweak on the kismet and other sniffing tools.But itll work fine.

---

### Post by sdennie on 2008-04-22
If you want to change the ipw3945 driver so that the interface is called wlan0 instead of eth1, you could edit the file /etc/udev/rules.d/70-persistent-net.rules and, where you see the description of ipw3945, change the part where it says eth1 to wlan0.  I'm not sure if that will help with what you are doing but, I believe it will change the name of the interface on reboot.

---

### Post by pps80 on 2008-04-22
> **vor said:**
> If you want to change the ipw3945 driver so that the interface is called wlan0 instead of eth1, you could edit the file /etc/udev/rules.d/70-persistent-net.rules and, where you see the description of ipw3945, change the part where it says eth1 to wlan0.  I'm not sure if that will help with what you are doing but, I believe it will change the name of the interface on reboot.

I am not sure either will it should work or not. i just want to install these drivers so that i can use airocrack.
below are the detailed output when i am installing please help me with this guys i dont know much about it.
i am following this from this website 
[http://www.aircrack-ng.org/doku.php?id=ipw3945](http://www.aircrack-ng.org/doku.php?id=ipw3945)

=============================
-laptop:/etc$ sudo wget [http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2)
--22:08:12--  [http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2)
           => `ipwraw-ng-2.3.4-04022008.tar.bz2.5'
Resolving dl.aircrack-ng.org... 213.186.33.2
Connecting to dl.aircrack-ng.org|213.186.33.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 177,591 (173K) [application/x-tar]

100%[====================================>] 177,591       45.76K/s    ETA 00:00

22:08:19 (45.66 KB/s) - `ipwraw-ng-2.3.4-04022008.tar.bz2.5' saved [177591/177591]

laptop:/etc$ sudo tar -xjf ipwraw-ng-2.3.4-04022008.tar.bz2.5

laptop:/etc$ cd ipwraw-ng
laptop:/etc/ipwraw-ng$ make

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

make -C /lib/modules/2.6.22-14-generic/build M=/etc/ipwraw-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
rm: cannot remove `/etc/ipwraw-ng/.tmp_versions/ipwraw.mod': Permission denied
make[1]: *** [crmodverdir] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2
laptop:/etc/ipwraw-ng$ sudo make

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

make -C /lib/modules/2.6.22-14-generic/build M=/etc/ipwraw-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Entering directory `/etc/ipwraw-ng/util'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/etc/ipwraw-ng/util'
laptop:/etc/ipwraw-ng$ sudo make install

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

Installing to /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/ ... done

Firmware found!
You have version 2.14.4
This version looks adequate for use with the driver!

Please see the README.ipwraw for more information.

You can load the module with
        modprobe ipwraw
laptop:/etc/ipwraw-ng$ nano README.ipwraw
laptop:/etc/ipwraw-ng$ sudo make install_ucode

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

Installing ucode in /lib/firmware ... done
laptop:/etc/ipwraw-ng$ echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw
blacklist ipwraw
laptop:/etc/ipwraw-ng$ sudo depmod -ae
laptop:/etc/ipwraw-ng$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

eth1      unassociated  ESSID:off/any 
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13   Missed beacon:0

laptop:/etc/ipwraw-ng$ sudo modprobe -r ipw3945
laptop:/etc/ipwraw-ng$ sudo modprobe ipwraw
laptop:/etc/ipwraw-ng$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

eth1      unassociated  ESSID:off/any 
          Mode:Monitor  Channel=1  Bit Rate=54 Mb/s   
         
rtap0     no wireless extensions.

laptop:/etc/ipwraw-ng$ iwconfig eth1 channel6
iwconfig: unknown command "channel6"
laptop:/etc/ipwraw-ng$ iwconfig eth1 channel 6
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Operation not permitted.
laptop:/etc/ipwraw-ng$ sudo iwconfig eth1 channel 6
laptop:/etc/ipwraw-ng$ iwconfig eth txpower 16
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth ; Operation not permitted.
laptop:/etc/ipwraw-ng$ sudo iwconfig eth txpower 16
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth ; No such device.
laptop:/etc/ipwraw-ng$ sudo iwconfig eth1 txpower 16
laptop:/etc/ipwraw-ng$ aireplay-ng -9 eth1
This program requires root privileges.
laptop:/etc/ipwraw-ng$ sudo aireplay-ng -9 eth1
22:15:51  Trying broadcast probe requests...
write failed: Network is down
read failed: Network is down
write failed: Network is down
write failed: Network is down
22:15:52  No Answer...
22:15:52  Found 0 APs
laptop:/etc/ipwraw-ng$ sudo aireplay-ng -9 rtap0
22:16:21  Trying broadcast probe requests...
write failed: Network is down
read failed: Network is down
write failed: Network is down
write failed: Network is down
22:16:22  No Answer...
22:16:22  Found 0 APs
laptop:/etc/ipwraw-ng$ sudo aireplay-ng -9 wlan0
Interface wlan0:
ioctl(SIOCGIFINDEX) failed: No such device
laptop:/etc/ipwraw-ng$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

eth1      unassociated  ESSID:off/any 
          Mode:Monitor  Channel=6  Bit Rate=54 Mb/s   
         
rtap0     no wireless extensions.

laptop:/etc/ipwraw-ng$
==================

---

