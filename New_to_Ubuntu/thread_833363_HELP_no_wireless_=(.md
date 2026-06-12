---
title: "HELP no wireless =("
date: 2008-06-18
forum: New to Ubuntu
---

### Post by That Guy X on 2008-06-18
Hi, i recently purchased a gateway M-series laptop model w650a. It came with Vista but i got three blue screens of death the first two days. So i wiped my hard drive and decided to give Ubuntu a shot. Everything work's great except for the most important feature, the wireless doesn't work. :(   Could someone please give me instructions to get it going so i can start using my laptop, i really don't want to resort to Vista, that OS is crap. Im using Ubuntu Hardy 64-bit edition.

---

### Post by Hospadar on 2008-06-18
Well I would try two things, depending on how much time you have to play around with your machine:
If you have a lot of time, just install 32 bit and see if that works, 32 bit tends to have better hardware support.
If you don't want to bother, or really want 64 bit, do an "lspci" and "lsmod" in the terminal and post the output here.  also maybe try an "iwconfig" and post the output.

---

### Post by That Guy X on 2008-06-23
Yeah it doesn't work in 32-bit either unfortunately, but ide rather use 64-bit anyway, here are my outputs. 

steve@MoDramida:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
08:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a08 (rev 03)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)


steve@MoDramida:~$ lsmod
Module                  Size  Used by
xt_limit                4608  8 
xt_tcpudp               4992  10 
ipt_LOG                 8192  8 
ipt_MASQUERADE          5504  0 
ipt_TOS                 3712  0 
ipt_REJECT              6528  1 
nf_conntrack_irc        8992  0 
nf_conntrack_ftp       11688  0 
xt_state                4096  6 
af_packet              27272  2 
ipv6                  311848  10 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
powernow_k8            16608  1 
cpufreq_powersave       3200  0 
cpufreq_userspace       6180  0 
cpufreq_conservative    10632  0 
cpufreq_ondemand       11152  1 
cpufreq_stats           8416  0 
freq_table              6464  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sbs                    17808  0 
sbshc                   8960  1 sbs
container               6656  0 
dock                   12960  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0 
usb_storage            82496  0 
uvcvideo               62084  0 
libusual               23520  1 usb_storage
compat_ioctl32         11136  1 uvcvideo
videodev               30720  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
sr_mod                 20132  0 
snd_hda_intel         440408  3 
cdrom                  41512  1 sr_mod
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
fglrx                1804800  26 
video                  23444  0 
output                  5632  1 video
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
battery                16776  0 
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
ac                      8328  0 
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 10912  0 
snd                    70856  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4              11148  0 
ata_generic             9988  0 
atiixp                  6672  0 [permanent]
serio_raw               9092  0 
i2c_core               28544  1 i2c_piix4
ide_core              136600  1 atiixp
evdev                  14976  7 
k8temp                  7680  0 
soundcore              10400  1 snd
psmouse                46236  0 
pcspkr                  4992  0 
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
iptable_nat             9604  0 
nf_nat                 23980  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      21904  8 iptable_nat
nf_conntrack           79216  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle          4480  0 
iptable_filter          4608  1 
ip_tables              24104  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               23560  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sd_mod                 33280  3 
pata_atiixp            10496  0 
ehci_hcd               41996  0 
ohci_hcd               27524  0 
pata_acpi               9856  0 
usbcore               169904  6 usb_storage,uvcvideo,libusual,ehci_hcd,ohci_hcd
r8169                  36612  0 
ahci                   33028  2 
libata                176432  4 ata_generic,pata_atiixp,pata_acpi,ahci
scsi_mod              178488  5 usb_storage,sr_mod,sg,sd_mod,libata
thermal                19744  0 
processor              41448  2 powernow_k8,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 


steve@MoDramida:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by balagosa on 2008-06-23
```
08:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown 
device 2a08 (rev 03)
```

I am guessing this is your Wireless card? Because the other one (Realtek) is for your Wired Network.

---

### Post by That Guy X on 2008-06-23
Yes, it is integrated

---

### Post by RomeReactor on 2008-06-23
Hi. According to [this thread]("http://ubuntuforums.org/showthread.php?t=575785") you need the wn311t driver; if you don't have it, and have wired internet in Ubuntu, open a terminal (Applications->Accessories->Terminal) and paste the following:
```
mkdir Wireless
```
This will make a folder named 'Wireless' in which to do the rest of the steps, so your home folder doesn't get cluttered. Then change directory to that folder:
```
cd Wireless
```
And download the driver:
```
wget ftp://downloads.netgear.com/files/wn311t_setup_4_1.exe
```
Then you need to install ndiswrapper, unshield and cabextract:
```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9 unshield cabextract
```
Now, to extract the necessary files:
```
cabextract wn311t_setup_4_1.exe
```
This will extract a folder named 'Disk1'; change directory to it:
```
cd Disk1
```
And to extract the **.inf** and **.sys** files required:
```
unshield x data1.cab
```
Now, inside the 'Disk1' folder you'll see a folder named 'Driver'. Change directory to it:
```
cd Driver
```
Here are the .inf and .sys files. To install the driver, use NdisWrapper:
```
sudo ndiswrapper -i NetMW14x.inf
```
As stated in the other thread, it's necessary to force the wireless to associate with the driver:
```
sudo ndiswrapper -a 11ab:2a08 netmw14x
```
To verify that the driver is installed correctly:
```
ndiswrapper -l
```
And lastly, run the three following commands:
```
sudo ndiswrapper -m
```
```
sudo depmod -a
```
```
sudo modprobe ndiswrapper
```

---------------------------------------------------------------------
If this works for you, make sure you store the 'Driver' folder with the .inf and .sys files somewhere safe, in case you decide to reinstall Ubuntu later on and need to install the drivers again.

---

### Post by That Guy X on 2008-06-27
It didn't work :( I may have messed it up when i was playing around with ndiswrapper a few weeks ago, i was trying to set it up myself but i did it wrong. I completely uninstalled it before starting your instructions but i think it came out wrong, here's the output. 




steve@MoDramida:~$ mkdir Wireless
steve@MoDramida:~$ cd Wireless
steve@MoDramida:~/Wireless$ wget [ftp://downloads.netgear.com/files/wn311t_setup_4_1.exe](ftp://downloads.netgear.com/files/wn311t_setup_4_1.exe)
--17:13:48--  [ftp://downloads.netgear.com/files/wn311t_setup_4_1.exe](ftp://downloads.netgear.com/files/wn311t_setup_4_1.exe)
           => `wn311t_setup_4_1.exe'
Resolving downloads.netgear.com... 207.211.82.170
Connecting to downloads.netgear.com|207.211.82.170|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /files ... done.
==> PASV ... done.    ==> RETR wn311t_setup_4_1.exe ... done.
Length: 6,818,378 (6.5M) (unauthoritative)

100%[====================================>] 6,818,378     90.56K/s    ETA 00:00

17:15:05 (88.46 KB/s) - `wn311t_setup_4_1.exe' saved [6818378]

steve@MoDramida:~/Wireless$ sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9 unshield cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.9 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 38.3kB of archives. After unpacking 217kB will be used.
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main ndiswrapper-common 1.50-1ubuntu1 [11.4kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main ndiswrapper-utils-1.9 1.50-1ubuntu1 [26.9kB]
Fetched 38.3kB in 0s (40.6kB/s)             
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 131101 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.50-1ubuntu1_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.50-1ubuntu1_amd64.deb) ...
Setting up ndiswrapper-common (1.50-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.50-1ubuntu1) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
steve@MoDramida:~/Wireless$ cabextract wn311t_setup_4_1.exe
wn311t_setup_4_1.exe: library not compiled to support large files.
wn311t_setup_4_1.exe: library not compiled to support large files.
Extracting cabinet: wn311t_setup_4_1.exe
  extracting Disk1/data1.cab
  extracting Disk1/data1.hdr
  extracting Disk1/data2.cab
  extracting Disk1/dbgprint.dll
  extracting Disk1/DIFxAPI.dll
  extracting Disk1/DPInstia64.exe
  extracting Disk1/DPInstx64.exe
  extracting Disk1/DRC.exe
  extracting Disk1/ikernel.ex_
  extracting Disk1/ISL.exe
  extracting Disk1/layout.bin
  extracting Disk1/RMV.exe
  extracting Disk1/RM_DEV_CODE.dll
  extracting Disk1/Setup.exe
  extracting Disk1/Setup.ini
  extracting Disk1/setup.inx
  extracting Disk1/Wlan.ini
  extracting Disk1/_isuser.dll

All done, no errors.
steve@MoDramida:~/Wireless$ cd Disk1
steve@MoDramida:~/Wireless/Disk1$ unshield x data1.cab
Cabinet: data1.cab
  extracting: ./RemoveInstall/DRC.EXE
  extracting: ./RemoveInstall/ISL.exe
  extracting: ./RemoveInstall/RMV.exe
  extracting: ./RemoveInstall/COI.EXE
  extracting: ./RemoveInstall/dbgprint.dll
  extracting: ./RemoveInstall/RM_DEV_CODE.dll
  extracting: ./_Support_English_Files/_IsRes.dll
  extracting: ./_Engine_Engine_Files/corecomp.ini
  extracting: ./_Support_Non-SelfRegistering/isrt.dll
  extracting: ./_Support_Non-SelfRegistering/default.pal
  extracting: ./APP/GTW32N50.dll
  extracting: ./APP/GTNDIS3.VXD
  extracting: ./APP/GTNDIS5.sys
  extracting: ./APP/uninstall.ico
  extracting: ./APP/desktop_32x32.ico
  extracting: ./APP/Dev64.exe
  extracting: ./APP/DevCon64.dll
  extracting: ./APP/DevCon.dll
  extracting: ./APP/Mrv8000x.dll
  extracting: ./APP/NETWEP.dll
  extracting: ./APP/oasisrc0a.dll
  extracting: ./APP/oasisrc0c.dll
  extracting: ./APP/oasisrc07.dll
  extracting: ./APP/oasisrc10.dll
  extracting: ./APP/odSupp_M.dll
  extracting: ./APP/PCARmDrv.exe
  extracting: ./APP/ProcNICs.dll
  extracting: ./APP/Security.dll
  extracting: ./APP/TcpWindowSize.exe
  extracting: ./APP/AutoLinkLib.dll
  extracting: ./APP/ML_GR_WN311T.ini
  extracting: ./APP/pos.ini
  extracting: ./APP/SmartWizard.dll
  extracting: ./APP/WN311T.exe
  extracting: ./APP/ML_GR_BigFont_WN311T.ini
  extracting: ./APP/Marvell.dll
  extracting: ./APP/ML_JP_BigFont_WN311T.ini
  extracting: ./APP/ML_JP_WN311T.ini
  extracting: ./APP/ML_US_BigFont_WN311T.ini
  extracting: ./APP/ML_US_WN311T.ini
  extracting: ./APP/etsitxpwr.ini
  extracting: ./APP/fcctxpwr.ini
  extracting: ./APP/jptxpwr.ini
  extracting: ./APP/Wlan.ini
  extracting: ./_Support_German_String_Tables/value.shl
  extracting: ./PCAUSA/GTW32N50.dll
  extracting: ./PCAUSA/GTNDIS3.VXD
  extracting: ./PCAUSA/GTNDIS5.sys
  extracting: ./_Engine_ScriptEngine/iscript.dll
  extracting: ./_Support_German_Files/_IsRes.dll
  extracting: ./VistaAPP/gNG.dll
  extracting: ./VistaAPP/gACS.dll
  extracting: ./_Support_English_Intel_32_Files/_isuser.dll
  extracting: ./Help/WN311T_Networks_JP.rtf
  extracting: ./Help/WN311T_About_JP.rtf
  extracting: ./Help/WN311T_About_US.rtf
  extracting: ./Help/WN311T_Networks_GR.rtf
  extracting: ./Help/WN311T_About_GR.rtf
  extracting: ./Help/WN311T_Networks_US.rtf
  extracting: ./Help/WN311T_Settings_GR.rtf
  extracting: ./Help/WN311T_Settings_JP.rtf
  extracting: ./Help/WN311T_Settings_US.rtf
  extracting: ./Help/WN311T_Statistics_GR.rtf
  extracting: ./Help/WN311T_Statistics_JP.rtf
  extracting: ./Help/WN311T_Statistics_US.rtf
  extracting: ./_Support_German_OS_Independent_Files/license.TXT
  extracting: ./Vista32/mrvw147.sys
  extracting: ./Vista32/netmw147.inf
  extracting: ./Vista32/CB8xN6x.cat
  extracting: ./Vista32/DPInstx64.exe
  extracting: ./Vista32/DPInstia64.exe
  extracting: ./Driver/netmw145.sys
  extracting: ./Driver/netmw143.sys
  extracting: ./Driver/NetMW14x.inf
  extracting: ./Vista64/mrvw148.sys
  extracting: ./Vista64/netmw148.inf
  extracting: ./Vista64/CB8xN6x.cat
  extracting: ./Vista64/DPInstx64.exe
  extracting: ./Vista64/DPInstia64.exe
  extracting: ./_Support_English_String_Tables/value.shl
  extracting: ./_Support_Language_Independent_OS_Independent_Files/LICENSE.txt
  extracting: ./_Support_Language_Independent_OS_Independent_Files/RMAPP.exe
  extracting: ./_Support_German_Intel_32_Files/_Isuser.dll
  extracting: ./_Engine_SelfRegistering/ctor.dll
  extracting: ./_Engine_SelfRegistering/objectps.dll
  extracting: ./_Engine_SelfRegistering/iuser.dll
  extracting: ./_Engine_Kernel_Placeholder/iKernel.exe
 --------  -------
          87 files
steve@MoDramida:~/Wireless/Disk1$ cd Driver
steve@MoDramida:~/Wireless/Disk1/Driver$ sudo ndiswrapper -i NetMW14x.inf
driver netmw14x is already installed
steve@MoDramida:~/Wireless/Disk1/Driver$ sudo ndiswrapper -a 11ab:2a08 netmw14x
Driver 'netmw14x' is already used for '11AB:2A08'
steve@MoDramida:~/Wireless/Disk1/Driver$ ndiswrapper -l
netmw14x : invalid driver!
steve@MoDramida:~/Wireless/Disk1/Driver$ sudo ndiswrapper -m
module configuration already contains alias directive

steve@MoDramida:~/Wireless/Disk1/Driver$ sudo depmod -a
steve@MoDramida:~/Wireless/Disk1/Driver$ sudo modprobe ndiswrapper
steve@MoDramida:~/Wireless/Disk1/Driver$

---

### Post by RomeReactor on 2008-06-27
> **That Guy X said:**
> It didn't work I may have messed it up when i was playing around with ndiswrapper a few weeks ago, i was trying to set it up myself but i did it wrong. I completely uninstalled it before starting your instructions but i think it came out wrong, here's the output.

> steve@MoDramida:~/Wireless/Disk1/Driver$ sudo ndiswrapper -i NetMW14x.inf
driver netmw14x is already installed
It seems you didn't uninstall the driver before removing ndiswrapper; and the driver you installed previously may not be the same one you just downloaded:
> netmw14x : invalid driver!

Try:
```
sudo ndiswrapper -r netmw14x
```
```
sudo rmmod ndiswrapper
```

And then install the one you downloaded:
```
sudo ndiswrapper -i NetMW14x.inf
```
```
ndiswrapper -l
```
If it still complains about it being an invalid driver, then this new driver isn't going to work either; if it *doesn't* say 'invalid driver', then continue with the rest of the steps:
```
sudo ndiswrapper -m
```
```
sudo depmod -a
```
and:
```
sudo modprobe ndiswrapper
```

---

### Post by That Guy X on 2008-07-09
Im about to pull my hair out lol It's saying the drivers aren't there when they are.   :confused:




bash: cd: Driver: No such file or directory
steve@MoDramida:~$ cd '/home/steve/Wireless/Disk1/Driver' 
steve@MoDramida:~/Wireless/Disk1/Driver$ sudo ndiswrapper -i NetMW14x.inf
installing netmw14x ...
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
steve@MoDramida:~/Wireless/Disk1/Driver$ sudo ndiswrapper -r netmw14x
steve@MoDramida:~/Wireless/Disk1/Driver$ sudo rmmod ndiswrapper
steve@MoDramida:~/Wireless/Disk1/Driver$ sudo ndiswrapper -i NetMW14x.inf
installing netmw14x ...
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
steve@MoDramida:~/Wireless/Disk1/Driver$ ndiswrapper -l
netmw14x : invalid driver!

---

### Post by RomeReactor on 2008-07-10
> **That Guy X said:**
> Im about to pull my hair out lol It's saying the drivers aren't there when they are.

NetMW146.sys does not come with that driver; try making a copy of NetMW145.sys and rename it to NetMW146.sys as [posted here]("http://ubuntuforums.org/showpost.php?p=4233401&postcount=13").

Sorry for the late reply.

---

