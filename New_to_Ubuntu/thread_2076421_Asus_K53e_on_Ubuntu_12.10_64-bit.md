---
title: "Asus K53e on Ubuntu 12.10 64-bit"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by davebold370 on 2012-10-26
Hello there, I am new to the forums and kind of new to the world of Ubuntu. I installed it on my last laptop, but never got around to playing with it. Well that laptop died with a gaint foot. 

So, I bought a Asus K53e! As soon as I turned it on, there was no OS. It only costs 200 dollars. Can't complain. 

So, i placed Ubuntu 12.10 on here. I plugged it into a Ethernet line while installing the ubuntu 12.10 64-bit. The Asus K53e has 8 gb of ram and an I-5 processor.

After a fresh install and a update, i tried to play on my laptop elsewhere and found that my wireless doesn't work correctly. It will connect, but only for 2-4 minutes. 

I have searched the forums and tried many of the different things that was said. I noticed a common trend was the update, but that is done and the wireless is still giving me troubles.  I also set the wireless to all users. But I have no idea what i am doing wrong. 

Inorder to upload this ^. I will have to disconnect and reconnect. The Asus K53e from my understanding have all had this same problem.

So, is there a fix?

---

### Post by squakie on 2012-10-26
We'll need some more information to continue. Please highlight and right-click/copy the below statements:
 
echo "****************************************\n\n" > ~/test.txt
echo -e " lspci" >> ~/test.txt
echo -e " \n\n" >> ~/test.txt
lspci >> ~/test.txt
echo -e \n"****************************************\n\n" >> test.txt
echo -e "\n****************************************\n\n" >> ~/test.txt
echo -e "\n lsusb\n\n" >> ~/test.txt
lsusb >> ~/test.txt
echo -e "\n\n****************************************\n\n" >> test.txt
echo -e "****************************************\n\n" >> ~/test.txt
echo -e " lshw" >> ~/test.txt
echo -e " \n\n" >> ~/test.txt
lshw -C network >> ~/test.txt
echo -e "****************************************\n\n" >> test.txt
echo -e "****************************************\n\n" >> ~/test.txt
echo -e " iwconfig\n\n" >> ~/test.txt
iwconfig >> ~/test.txt
echo -e "\n\n****************************************\n\n" >> test.txt
 
 
Now open a terminal window and do the following:
 
gedit test.sh
 
in the editor window, do a paste to paste the copied text from above into the editor
 
click save, then close the editor
 
 
chmod +x test.sh
 
./test.sh
 
then post back here again attaching the test.txt file from your home folder.

---

### Post by davebold370 on 2012-10-26
This is the results:

****************************************
-e  lspci
-e  
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
03:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
-e ****************************************
****************************************
-e  lsusb
-e  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 058f:a014 Alcor Micro Corp. Asus Integrated Webcam
-e ****************************************
****************************************
-e  lshw
-e  
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:2f:68:67:0b:44
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.5.0-17-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:c000(size=256) memory:dea00000-dea03fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 54:04:a6:22:11:c6
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full ip=192.168.0.145 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:de000000-de03ffff ioport:b000(size=128)
-e ****************************************
****************************************
-e  iwconfig
-e  
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          
-e ****************************************

---

### Post by squakie on 2012-10-26
Ok, so we can see the wireless is rtl8188ce (realtek).  Try an internet search with the following in the search string:
 
ubuntu 12.10 rtl8188ce
 
You can look through the results and see if (1) someone else has had the same problem and (2) a possible solution.  Keep in mind the links don't have to point to the ubuntu forums as there are also plenty of other sites that might have that posted in them (the ubuntu forums should always be the first place you check, the first place you post seeking an answer).
 
If you can't find anything just post back and we can look as well.  I think it's a matter of loading a different module (driver) and blacklisting the existing one.

---

### Post by davebold370 on 2012-10-26
After searching around for a bit, i found this: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

I downloaded the linux 3.2 or later

I then looked up linux commands.

ls to see my options.
cd downloads
i changed the name to drivers.tar.gz inside the download folder instead of command line.
I clicked the properties and make excutable
then in command line i typed: ./drivers.tar.gz 
and it gave me a non binary error.

So, what should I do with these drivers?

---

### Post by davebold370 on 2012-10-26
Update (Currently using the wired)

I have downloaded the drivers. 
Extracted to a folder. 
Following the readme file. 
in the termail i have done sudo su to make a super user mode.
i have done make -C to make a directory 
Now I need to do make install, i'm not to sure why this isn't working, but i will figure it out.

---

### Post by squakie on 2012-10-26
I don't know what the readme says, as I haven't downloaded that - I may just to see.  In the mean time, if you did the sudo su, you won't need to put sudo in front of the rest of the commands (won't hurt anything if it's there, it's just redundant).  Normally the procedure is something like cd to the folder containing the extracted files , then sometimes ./configure, then make and finally make install.

Normally for these things to be successful you have to be sure you have the build-essential package installed.

It's getting late, but I may look at the download yet and see what happens.

---

### Post by squakie on 2012-10-26
Ok, I just did the download, then extracted all out to a single folder (the default in extract).  I then just did the following, as noted in section II of the readme, in a terminal window:

make

sudo make install


This all worked in terms of building the driver.  I don't have your wireless adapter, so there is no use in me doing the reboot they recommend.

You shouldn't need anything else that's in the readme from what I can see - just sudo su, then make, then make install.

I'm running 12.10 with what ever the current kernel with it is.

Note that I also have the build-essential package installed.  It is needed for compiling things from source such as these drivers.

If it works, after you reboot you should see the available networks with network manager.

---

### Post by davebold370 on 2012-10-27
I have tried and tired again, Failing each time.
This is the error message i keep getting:
```
make -C /lib/modules/3.5.0-17-generic/build M=/home/davebold370/Downloads/rtl modules
make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory.  Stop.
make: *** [all] Error 2
```

I have searched the web and found:
[http://linuxwireless.org/en/users/Download/stable/#compat-wireless_3.5_stable_releases](http://linuxwireless.org/en/users/Download/stable/#compat-wireless_3.5_stable_releases)

I have searched through all the 3.5 and all yield the same results (Slightly different because of the folders/download names):

```
root@davebold370-Lap-Ubu:/home/davebold370/Downloads/compat-wireless-3.5.4-1-snpc# make
./scripts/gen-compat-autoconf.sh /home/davebold370/Downloads/compat-wireless-3.5.4-1-snpc/.config /home/davebold370/Downloads/compat-wireless-3.5.4-1-snpc/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.5.0-17-generic/build M=/home/davebold370/Downloads/compat-wireless-3.5.4-1-snpc modules
make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory.  Stop.
```

According to this, my current linux build is 3.5.0-17, thus, i need those drivers. I can't find them anywhere. What should I do?
Edit: Instead of reply posting

after seeing the 3.5.0-17 compat is what i needed to find, i opened up the ubuntu repository and searched from the 3.5.0-17 and found the headers, modules, and tools for this level. I installed all of these, and it gave me an extra 3 minutes before the wireless cuts off once again. 

After studying it, it's almost as if the power is not regulated and the wireless card itself shuts down. I don't know if that could be the case. I wish the wireless usbs were linux compatible, because i would just buy one of those and be done with it. Then again, i would not know if that would truly fix the problem or not. 

Thus, at this point, I have used all i know to fix this problem and i have nothing else i can do that i Know of. So, i plead with you all. Free me from my wire. Please

---

### Post by squakie on 2012-10-27
I don't know - the make and make install worked fine for me - none of the troubles you encountered - but I don't have that device to test with.
 
Perhaps you should check for a ubuntu-compatible USB adapter (I use a Tenda N USB adapter - it was extremely inexpensive at Micro Center).

---

### Post by Linuxisfast on 2012-10-27
This is strange indeed, that means there is a hardware issue in the wireless module. Try flashing the BIOS to latest. I picked this laptop last week and installed 12.10,it just works brilliant, battery lasts for five hours, runs cool, way better than my hot running VAIO with i7/nvidia combo and also lasts longer. If flashing BIOS doesn't work, take it back and exchange for another unit.

---

### Post by davebold370 on 2012-10-27
> **Linuxisfast said:**
> This is strange indeed, that means there is a hardware issue in the wireless module. Try flashing the BIOS to latest. I picked this laptop last week and installed 12.10,it just works brilliant, battery lasts for five hours, runs cool, way better than my hot running VAIO with i7/nvidia combo and also lasts longer. If flashing BIOS doesn't work, take it back and exchange for another unit.

I was able to acquire windows from my school yesterday and I have installed it along side of the Ubuntu partition. (well, re-installed ubuntu 12.10 64-bit). The windows partition had troubles until i downloaded the drivers from asus. Asus does not have driver support for Linux though. 

I have downloaded and going to try to flash the bios with [http://support.asus.com/download.aspx?SLanguage=en&p=3&m=K53E&hashedid=fCGFt3hiSAQYMnvO](http://support.asus.com/download.aspx?SLanguage=en&p=3&m=K53E&hashedid=fCGFt3hiSAQYMnvO) and update it to the newest one. Maybe that will work.

Edit: That did not work. The wireless card itself has all the drivers that ubuntu offers, but it dies every so often. It shifts from day to day on how long it will last as well. There has to be something else like the PCI connection drivers or power control drivers. I'm am not giving up on Ubuntu. Others have this same problem, and from the forums i have read so far, no one has truly figured it out. 

How would i go about testing the PCI drivers and the Power Control Drivers? In windows I click on the device and driver box and it loads a list. I have not found that in ubuntu. So, where should I go?

---

### Post by squakie on 2012-10-30
It's something with the driver - if you search the net for ubuntu and this adapter you'll see many, many posts about varying lengths of time the adapter runs without dropping out.

---

### Post by davebold370 on 2012-11-05
Well, after a week of searching and hunting for something for 64bit, i have hit a brick wall. I mean, i even stole drivers from windows! The ONLY system that seems to even know what drivers for this computer are is the kaspersky rescue disk, but that's because it's a different linux kernal.

Sometimes being free from windows costs to much for us beginners. 

So, i'm sitting at this:
Asus K532e rquires rlt8188ce drivers
Ubuntu 12.10 64-bit is linux kernal 3.0.5-18-generic.
Realtecks 32bit and 64 bit does not work with 3.0.5-18.
Windows XP 32/64 drivers do not work with ndiswrapper or any veration of it. (Windows Wireles drivers in the unbuntu softwares) Neither does vista drivers or 7 drivers. 

My windows partition (windows 7-64bit) works wonderfully with interent. 

I have seen others in different forums solve this problem with a lower version of ubnutu or with the ubuntu 12.10 upgrade. Which i did and didn't work.

My next plan of action, deleting ubuntu because it can't do the job of an OS for this system. Then start downloading different systems and trying them on the live CD/DVD. Going from top to bottom on distrowatch.com. I might get lucky and find an OS that is as nice as ubuntu but has interent access. If not, then I will be a slave to windows. At least i know how to hack it and make it do what i want. I will miss the ubuntu software center. :(

---

