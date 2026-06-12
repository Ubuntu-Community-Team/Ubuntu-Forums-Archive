---
title: "How to set up WUSB600N wireless with Ubuntu"
date: 2009-04-21
forum: Outdated Tutorials &amp; Tips
---

### Post by z.s.tar.gz on 2009-04-21
How to set up WUSB600N wireless with Ubuntu

------------------------------------

First things first: 

I did not make this up. I got it from mizunoX who didn't make it either. I'm just making it easier and cutting out unnecessary parts.

The parts in orange are explanations for what is happening, so you may even learn some stuff!

Also, when I say "wusb" I mean the physical WUSB600N router.

Note: Most of this guide is meant to be run in a terminal. If you don't like the terminal, shake hands and play nice for now.

------------------------------------

Part 1: Obtain the drivers

If you have wired internet + wusb, run:
```

	wget http://rapidshare.com/files/160951015/WUSB600N.tar
	tar -xvvf WUSB600N.tar
```

[COLOR="DarkOrange"]These two commands will download the drivers and extract them into your home directory[/COLOR]

If you only have wusb:

Go to [http://rapidshare.com/files/160951015/WUSB600N.tar](http://rapidshare.com/files/160951015/WUSB600N.tar) and download

Copy to the computer with wusb (or the ubuntu partition), and put it in your home folder.

Now run:

	```
tar -xvvf WUSB600N.tar
```

[COLOR="DarkOrange"]This will extract the file you just copied into your home folder[/COLOR]

Ok, now that you have the drivers, its time to install them.

------------------------------------

Part 2: Installing the drivers

Run:

	```
cd WUSB600N
	sudo make
```

[COLOR="DarkOrange"]this will create the drivers for your system[/COLOR]


Then run:

	```
sudo mkdir /etc/Wireless
	sudo mkdir /etc/Wireless/RT2870STA
	sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
```

[this will copy the drivers to your system]

First, find out what kernel version you have:

	```
cd /lib/modules
	ls
```

Make note of this, as you will need it in the next parts.

Run:

	```
cd ~/WUSB600N/os/linux
	sudo mkdir /lib/modules/<kernel version>/wireless
	sudo cp rt2870sta.ko /lib/modules/<kernel version>/wireless
```

[COLOR="DarkOrange"]This installs the drivers[/COLOR]

Now we just have to edit two files so that the driver is used.

Run:

	```
sudo gedit /etc/modules
```

Add "rt2870sta" to the bottom of the file (without the quotes, of course).

Now, run:

	```
sudo gedit /etc/rc.local
```

Add this to the bottom of the file (but before "exit 0") 

	```
sudo insmod /lib/modules/<kernel version>/wireless/rt2870sta.ko
```

[COLOR="DarkOrange"]these two things will load the drivers when you start up[/COLOR]

Congratulations! Your wireless card should be working now. If it isn't, you're already in the right place!

---

### Post by BoboKrull on 2010-01-14
Hi, I wonder if anyone here has used this guide but with a WUSB600N v.2 adapter instead!
I'm using Ubuntu 9.10.
I have downloaded the driver that is used in this version from Ralink RT3572 and tried to apply this guide. I have read from other forums that you must add the adapter device and vendor id in "common/rtusb_dev_id.c" file so it will link this driver to the adapter.

But after running these steps described in this guide with the modification above I still get no respone when plugging in my adapter. 

Anyone done this?

Thanks, Bobo.

__

---

### Post by bbear1 on 2010-02-02
BoboKrull,
I have got my Linksys WUSB600N V2 (rt3572 chipset) *working* using the steps detailed in the following thread:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165")

See post #38

when I say *working* it is not 100% working, as I can't even stream 128Kbps AAC audio files without the sound glitching every minute. I can however transfer 3Gb files, no problem and surf the net are respectable speeds.

A number of people have tried to help me but I think the issue is very complex (going into the intricacies of TCP over wireless), plus having a Dlink router with Linksys adapter you can't rule out the possibility of some sort of compatibility issue between the two.

Anyway, for me, I have about given up on the idea of Wireless n with Linux. In fact I am so frustrated with the whole thing that I am about ready to ditch Linux altogether. This is after spending a couple of years using various versions of Ubuntu and most recently Linux Mint (which I understand is built on top of Ubuntu). I would love to have stuck with Linux, and ditched my Windowz boxes but this wireless stuff has really tested my patience.

Anyway, I hope that you have every success with your wireless-n adapter with Linux.

---

### Post by bleecher on 2011-03-08
I tried the solution that you describe but the program bombed at step 2.  See the error message below and let me know if you can help:

root@david-desktop:/home/david/Desktop/WUSB600N# sudo make
make -C tools
make[1]: Entering directory `/home/david/Desktop/WUSB600N/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/david/Desktop/WUSB600N/tools'
/home/david/Desktop/WUSB600N/tools/bin2h
cp -f os/linux/Makefile.6 /home/david/Desktop/WUSB600N/os/linux/Makefile
make  -C  /lib/modules/2.6.32-26-generic/build SUBDIRS=/home/david/Desktop/WUSB600N/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-26-generic'
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../common/md5.o
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../common/mlme.o
/home/david/Desktop/WUSB600N/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/david/Desktop/WUSB600N/os/linux/../../common/mlme.c:4259: warning: the frame size of 1572 bytes is larger than 1024 bytes
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../common/rtmp_wep.o
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../common/action.o
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../common/cmm_data.o
/home/david/Desktop/WUSB600N/os/linux/../../common/cmm_data.c: In function ‘RTMP_FillTxBlkInfo’:
/home/david/Desktop/WUSB600N/os/linux/../../common/cmm_data.c:713: warning: label ‘FillTxBlkErr’ defined but not used
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../common/rtmp_init.o
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../common/rtmp_tkip.o
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../common/cmm_sync.o
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../common/eeprom.o
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../common/cmm_info.o
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../common/cmm_wpa.o
/home/david/Desktop/WUSB600N/os/linux/../../common/cmm_wpa.c: In function ‘AES_GTK_KEY_WRAP’:
/home/david/Desktop/WUSB600N/os/linux/../../common/cmm_wpa.c:836: warning: the frame size of 1092 bytes is larger than 1024 bytes
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../common/dfs.o
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../common/spectrum.o
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../sta/assoc.o
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../sta/aironet.o
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../sta/auth.o
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../sta/sync.o
/home/david/Desktop/WUSB600N/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/david/Desktop/WUSB600N/os/linux/../../sta/sync.c:1393: warning: the frame size of 1312 bytes is larger than 1024 bytes
/home/david/Desktop/WUSB600N/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/david/Desktop/WUSB600N/os/linux/../../sta/sync.c:934: warning: the frame size of 1252 bytes is larger than 1024 bytes
/home/david/Desktop/WUSB600N/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/david/Desktop/WUSB600N/os/linux/../../sta/sync.c:675: warning: the frame size of 1256 bytes is larger than 1024 bytes
/home/david/Desktop/WUSB600N/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/david/Desktop/WUSB600N/os/linux/../../sta/sync.c:533: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../sta/sanity.o
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../sta/connect.o
/home/david/Desktop/WUSB600N/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/david/Desktop/WUSB600N/os/linux/../../sta/connect.c:351: warning: the frame size of 1600 bytes is larger than 1024 bytes
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../sta/wpa.o
/home/david/Desktop/WUSB600N/os/linux/../../sta/wpa.c: In function ‘CCKMPRF’:
/home/david/Desktop/WUSB600N/os/linux/../../sta/wpa.c:1848: warning: the frame size of 1044 bytes is larger than 1024 bytes
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../os/linux/rt_linux.o
/home/david/Desktop/WUSB600N/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/david/Desktop/WUSB600N/os/linux/../../os/linux/rt_linux.c:1043: warning: the frame size of 1084 bytes is larger than 1024 bytes
  CC [M]  /home/david/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.o
/home/david/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c: In function ‘RTMPReadParametersHook’:
/home/david/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:928: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/david/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:929: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/david/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/david/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/david/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:1593: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/david/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:1594: error: ‘struct task_struct’ has no member named ‘fsgid’
make[2]: *** [/home/david/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/david/Desktop/WUSB600N/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-26-generic'
make: *** [LINUX] Error 2
root@david-desktop:/home/david/Desktop/WUSB600N# 



Thanks in advance.

David

---

