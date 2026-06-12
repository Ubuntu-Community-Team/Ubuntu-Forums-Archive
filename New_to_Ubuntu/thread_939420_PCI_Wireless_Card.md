---
title: "PCI Wireless Card"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Roach360 on 2008-10-05
I'm a new user to linux, and every guide i find for how to use a wireless pci card skips steps.

I'm using a PCI linsys W11 V4 card.

All help is appreciated.

---

### Post by pytheas22 on 2008-10-05
Please open up a terminal (Applications>Accessories menu), run the following commands (one per line), and post the output here (you can copy output from the terminal by highlighting it with your mouse, then right-clicking and selecting 'copy'.  Paste as you would in Windows):
```

lshw -C Network
lspci -nn
uname -m
```

With that information, we can figure out which steps you need to get your card working.

---

### Post by Roach360 on 2008-10-05
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: EN-1216 Ethernet Adapter
       vendor: Accton Technology Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 11
       serial: 00:d0:59:7b:0c:d7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=129.82.245.224 latency=64 maxlatency=255 mingnt=255 module=tulip multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=64 mingnt=32
roach@Sakura:~$ lspci -nn
00:00.0 Host bridge [0600]: ALi Corporation M1647 Northbridge [MAGiK 1 / MobileMAGiK 1] [10b9:1647] (rev 04)
00:01.0 PCI bridge [0604]: ALi Corporation PCI to AGP Controller [10b9:5247]
00:02.0 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:04.0 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]
00:04.1 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]
00:06.0 Bridge [0680]: ALi Corporation M7101 Power Management Controller [PMU] [10b9:7101]
00:07.0 ISA bridge [0601]: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] [10b9:1533]
00:08.0 Multimedia audio controller [0401]: ESS Technology ES1988 Allegro-1 [125d:1988] (rev 12)
00:08.1 Communication controller [0780]: ESS Technology ESS Modem [125d:1989] (rev 12)
00:0f.0 IDE interface [0101]: ALi Corporation M5229 IDE [10b9:5229] (rev c4)
00:10.0 Ethernet controller [0200]: Accton Technology Corporation EN-1216 Ethernet Adapter [1113:1216] (rev 11)
01:00.0 VGA compatible controller [0300]: Trident Microsystems CyberBlade/XP [1023:9910] (rev 63)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC [10ec:8180] (rev 20)

```


Yes?

---

### Post by pytheas22 on 2008-10-06
Please try running these commands to get your card working.  Make sure you're connected to the Internet using your ethernet connection before running these commands:
```

sudo apt-get install ndiswrapper*
wget ftp://ftp.targetgroup.it/digicom/comuni/driver/PalladioWaveC/PalWavC__WIN.zip
unzip PalWavC__WIN.zip 
sudo ndiswrapper -i NETR8180.INF
echo ndiswrapper > sudo tee -a /etc/modules
```

Then reboot, and you should be able to connect to wireless networks using Network Manager (the applet in the upper-right portion of your screen whose icon looks like two computer monitors).  If your wireless still doesn't work after a reboot, please post the output of the following commands:
```

lshw -C Network
ndiswrapper -l
uname -m
dmesg | grep -e ndis -e wlan
sudo iwlist scan
```

---

### Post by Roach360 on 2008-10-06
It didn't work, and this is what i got from the second bit of code.

Feel free to explain what the hell is going on.

```
roach@Sakura:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: EN-1216 Ethernet Adapter
       vendor: Accton Technology Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 11
       serial: 00:d0:59:7b:0c:d7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=129.82.245.224 latency=64 maxlatency=255 mingnt=255 module=tulip multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=64 mingnt=32
roach@Sakura:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
roach@Sakura:~$ uname -m
i686
roach@Sakura:~$ dmesg | grep -e ndis -e wlan
roach@Sakura:~$ sudo iwlist scan
[sudo] password for roach: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

roach@Sakura:~$ 

```

Help?

---

### Post by pytheas22 on 2008-10-06
Sorry it didn't work the first time, but we'll get it.

It looks like something was not installed correctly, as nothing changed from your original situation.  Please first go to System>Administration>Software Sources.  A window will open up.  Under the "Ubuntu Software" tab of that window, please check all of the boxes.  Then close the window.  If you're asked about updating the sources list, say yes.  This will eliminate one potential source of errors that caused the installation to fail the first time.

Then please run the following commands, and post all of their output here, so that we can make sure that you're installing the wireless drivers properly:
```

sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
wget ftp://ftp.targetgroup.it/digicom/comuni/driver/PalladioWaveC/PalWavC__WIN.zip
unzip PalWavC__WIN.zip 
sudo ndiswrapper -i NETR8180.INF
echo ndiswrapper > sudo tee -a /etc/modules
```

I may not be able to respond again till tomorrow, but I'll answer when I can.

---

### Post by pytheas22 on 2008-10-06
Just wondering if you'd resolved this yet; if not, please let me know...

---

### Post by Roach360 on 2008-10-08
Sorry it took a little while for me to get back to you,

I'm not sure what's going on...

```
roach@Sakura:~$ sudo apt-get update
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg                   
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US        
Hit http://archive.canonical.com hardy Release                       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release                
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release 
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://security.ubuntu.com hardy-security/main Packages          
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://archive.canonical.com hardy/partner Sources                         
Hit http://security.ubuntu.com hardy-security/restricted Packages    
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
roach@Sakura:~$ sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
ndiswrapper-common is already the newest version.
The following packages were automatically installed and are no longer required:
  x11proto-kb-dev mesa-common-dev libxdmcp-dev xtrans-dev x11proto-core-dev
  libglu1-mesa-dev dkms x11proto-input-dev libpthread-stubs0-dev libxau-dev
  libpthread-stubs0 nvidia-new-kernel-source-envy libgl1-mesa-dev libx11-dev
  libxcb-xlib0-dev libxcb1-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
roach@Sakura:~$ wget ftp://ftp.targetgroup.it/digicom/comuni/driver/PalladioWaveC/PalWavC__WIN.zip
--19:46:50--  ftp://ftp.targetgroup.it/digicom/comuni/driver/PalladioWaveC/PalWavC__WIN.zip
           => `PalWavC__WIN.zip.2'
Resolving ftp.targetgroup.it... 62.173.160.170
Connecting to ftp.targetgroup.it|62.173.160.170|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /digicom/comuni/driver/PalladioWaveC ... done.
==> PASV ... done.    ==> RETR PalWavC__WIN.zip ... done.

    [     <=>                             ] 181,504      119.48K/s             

19:46:55 (119.09 KB/s) - `PalWavC__WIN.zip.2' saved [181504]

roach@Sakura:~$ unzip PalWavC__WIN.zip 
Archive:  PalWavC__WIN.zip
replace NETR8180.INF? [y]es, [n]o, [A]ll, [N]one, [r]ename: Y
error:  invalid response [s]
replace NETR8180.INF? [y]es, [n]o, [A]ll, [N]one, [r]ename: error:  invalid response [s]
replace NETR8180.INF? [y]es, [n]o, [A]ll, [N]one, [r]ename: error:  invalid response [ ]
replace NETR8180.INF? [y]es, [n]o, [A]ll, [N]one, [r]ename: error:  invalid response [8]
replace NETR8180.INF? [y]es, [n]o, [A]ll, [N]one, [r]ename: error:  invalid resp]nse [
replace NETR8180.INF? [y]es, [n]o, [A]ll, [N]one, [r]ename: error:  invalid response [i]
replace NETR8180.INF? [y]es, [n]o, [A]ll, [N]one, [r]ename: new name:   inflating:  tee -a /etc/modulesY   
replace Netr8180n.cat? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: Netr8180n.cat           
replace rtl8180.sys? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: rtl8180.sys             
replace Aggiornamento.pdf? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: Aggiornamento.pdf roach@Sakura:~$ sudo apt-get update
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg                   
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US        
Hit http://archive.canonical.com hardy Release                       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release                
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release 
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://security.ubuntu.com hardy-security/main Packages          
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://archive.canonical.com hardy/partner Sources                         
Hit http://security.ubuntu.com hardy-security/restricted Packages    
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
roach@Sakura:~$ sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
ndiswrapper-common is already the newest version.
The following packages were automatically installed and are no longer required:
  x11proto-kb-dev mesa-common-dev libxdmcp-dev xtrans-dev x11proto-core-dev
  libglu1-mesa-dev dkms x11proto-input-dev libpthread-stubs0-dev libxau-dev
  libpthread-stubs0 nvidia-new-kernel-source-envy libgl1-mesa-dev libx11-dev
  libxcb-xlib0-dev libxcb1-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
roach@Sakura:~$ wget ftp://ftp.targetgroup.it/digicom/comuni/driver/PalladioWaveC/PalWavC__WIN.zip
--19:46:50--  ftp://ftp.targetgroup.it/digicom/comuni/driver/PalladioWaveC/PalWavC__WIN.zip
           => `PalWavC__WIN.zip.2'
Resolving ftp.targetgroup.it... 62.173.160.170
Connecting to ftp.targetgroup.it|62.173.160.170|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /digicom/comuni/driver/PalladioWaveC ... done.
==> PASV ... done.    ==> RETR PalWavC__WIN.zip ... done.

    [     <=>                             ] 181,504      119.48K/s             

19:46:55 (119.09 KB/s) - `PalWavC__WIN.zip.2' saved [181504]

roach@Sakura:~$ unzip PalWavC__WIN.zip 
Archive:  PalWavC__WIN.zip
replace NETR8180.INF? [y]es, [n]o, [A]ll, [N]one, [r]ename: Y
error:  invalid response [s]
replace NETR8180.INF? [y]es, [n]o, [A]ll, [N]one, [r]ename: error:  invalid response [s]
replace NETR8180.INF? [y]es, [n]o, [A]ll, [N]one, [r]ename: error:  invalid response [ ]
replace NETR8180.INF? [y]es, [n]o, [A]ll, [N]one, [r]ename: error:  invalid response [8]
replace NETR8180.INF? [y]es, [n]o, [A]ll, [N]one, [r]ename: error:  invalid resp]nse [
replace NETR8180.INF? [y]es, [n]o, [A]ll, [N]one, [r]ename: error:  invalid response [i]
replace NETR8180.INF? [y]es, [n]o, [A]ll, [N]one, [r]ename: new name:   inflating:  tee -a /etc/modulesY   
replace Netr8180n.cat? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: Netr8180n.cat           
replace rtl8180.sys? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: rtl8180.sys             
replace Aggiornamento.pdf? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: Aggiornamento.pdf 
```

---

### Post by pytheas22 on 2008-10-08
hmmm, there's something strange going on when you try to unzip that archive.  I'm not sure why, as it works on my machine.  But please try running these commands; they will grab the drivers from a different source that will hopefully work better:
```

wget http://burnthesorbonne.com/files/rtl8180_win32.tar.gz
tar -xzvf rtl81*
sudo ndiswrapper -i NETR8180.INF
echo ndiswrapper > sudo tee -a /etc/modules
```

In principle, that should do it.  If you get any weird errors again (like being asked multiple times about renaming a file), please post that output.  Otherwise, reboot, and the wireless should work.  If it doesn't, please post the output of:
```

lshw -C Network
dmesg | grep -e ndis -e wlan
```

---

### Post by Roach360 on 2008-10-08
no success, and this is what i got.

```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: EN-1216 Ethernet Adapter
       vendor: Accton Technology Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 11
       serial: 00:d0:59:7b:0c:d7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=129.82.245.224 latency=64 maxlatency=255 mingnt=255 module=tulip multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=64 mingnt=32

```

---

### Post by pytheas22 on 2008-10-08
Sorry to hear that, but we'll get it...

Please reboot, run these commands (in this order) and post all output:
```

ndiswrapper -l
lsmod | grep ndis
sudo modprobe ndiswrapper
sudo iwlist scan
dmesg | grep -e ndis -e wlan
```

---

### Post by Roach360 on 2008-10-09
Here it is

```
netr8180 : driver installed
	device (10EC:8180) present
roach@Sakura:~$ lsmod | grep ndis
ndiswrapper           192920  0 
usbcore               146028  3 ndiswrapper,ohci_hcd
roach@Sakura:~$ sudo modprobe ndiswrapper
roach@Sakura:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

roach@Sakura:~$ dmesg | grep -e ndis -e wlan
[ 3409.002716] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 1704.583288] ndiswrapper: driver netr8180 (Realtek,12/12/2003,5.200.1212.2003) loaded
[ 1704.653527] ndiswrapper: using IRQ 11
[ 2131.615294] wlan0: ethernet device 00:0c:41:72:ba:cf using NDIS driver: netr8180, version: 0x100, NDIS version: 0x500, vendor: 'Realtek RTL8180 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8180.5.conf
[ 2131.625267] ndiswrapper (set_ndis_auth_mode:628): setting auth mode to 3 failed (C0010015)
[ 2131.625292] wlan0: encryption modes supported: WEP
[ 2131.626557] usbcore: registered new interface driver ndiswrapper

```

---

### Post by pytheas22 on 2008-10-09
It looks like everything should be working now.  Were you able to connect?

Also note that your wireless card doesn't support 11g mode, which is the most common wireless mode now.  You will need to make sure that your router supports 11b mode to use with your wireless card.

---

### Post by Roach360 on 2008-10-12
It's still not even an option in the drop down menu.

What's the problem?

---

### Post by pytheas22 on 2008-10-12
I'm not sure what's wrong, but I suspect a problem with Network Manager (the graphical connection manager), since by all indications from the command-line, everything should be working.  It may help to install [wicd]("http://wicd.sourceforge.net") and use it instead of NM.  Also, are you sure that you're left-clicking on the NM icon when you want to select a network?  Some users new to Linux don't realize that you have to left click, not right.

It may also help to try using a different Windows driver with ndiswrapper.  You can do that by running these commands:
```

sudo ndiswrapper -r netr8180
wget ftp://66.104.77.130/cn/wlan/ndis5x-8180\(173\).zip
unzip ndis5x-8180\(173\).zip 
sudo ndiswrapper -i NET8180.INF 
```

You may have better luck with that driver--actually you should probably try using it first, and if that still fails, give wicd a shot.

---

