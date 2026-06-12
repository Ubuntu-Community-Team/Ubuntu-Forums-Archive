---
title: "Wifi regularly disconnects and short battery life"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by VulpesLagopus on 2012-11-18
Hello,

I've just started using Ubuntu 12.04.1 LTS on my Alienware M14x. And I'm having some trouble.
The wifi keeps disconnecting every 5 to 15min. I've read a lot about this on the Internet, but the only solution I found didn't work for me (it was to deactivate the IPv6).
And the other problem is that my battery life is really short since I have a dual-boot Windows 7 and Ubuntu. On Ubuntu it lasts 3 hours maximum!!!

So I'm really new to all this stuff, I know I have to give you a lot more details but I just don't know what. So if someone is kind enough to help me, I'll do anything :).

Thank you in advance.

---

### Post by offgridguy on 2012-11-18
> **VulpesLagopus said:**
> Hello,

I've just started using Ubuntu 12.04.1 LTS on my Alienware M14x. And I'm having some trouble.
The wifi keeps disconnecting every 5 to 15min. I've read a lot about this on the Internet, but the only solution I found didn't work for me (it was to deactivate the IPv6).
And the other problem is that my battery life is really short since I have a dual-boot Windows 7 and Ubuntu. On Ubuntu it lasts 3 hours maximum!!!

So I'm really new to all this stuff, I know I have to give you a lot more details but I just don't know what. So if someone is kind enough to help me, I'll do anything :).

Thank you in advance.

I would be real happy with 3 hours of battery life.:)  I usually never get much more than 2.

---

### Post by VulpesLagopus on 2012-11-18
Yeah I'm not really happy because before the dual-boot I had like 7 or 8 hours on Windows 7. So it is kind of a big change for me :)

---

### Post by wildmanne39 on 2012-11-18
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by VulpesLagopus on 2012-11-18
Hi,
so I pasted your command and I think all went good, but the file was to big so I parsed it into smaller pieces with the split command on the terminal, hope that's ok.

---

### Post by wildmanne39 on 2012-11-18
Hi, please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Thanks

---

### Post by VulpesLagopus on 2012-11-18
So for now on I think it works, but it can take a while until it disconnects me from a network so if tomorrow everything works fine I'll consider this problem solved.
Thank you very much

And I have a question how can I learn to use Ubuntu (I mean like you, you fixed the problem in five minutes)? Do you have any advice or a web site?

---

### Post by wildmanne39 on 2012-11-18
Hi, that usually fixes the issue with your wireless driver.

There is no easy and fast way to learn, I study posts from other people on the topic I want to learn, and that is a big part of learning is figuring out what you want to know because there is so much to know that no one can know everything it is best to specialize in one topic..
Thanks

---

### Post by gbrowning on 2012-11-18
This list is a bit heavy for someone new to Linux. I lifted it from a 2009 post by Knifemonk regarding energy efficient Ubuntu machines. I cannot endorse these packages but would definitely explore them if I were on a laptop and having battery life problems.

cpufreqd
 fully configurable daemon for dynamic frequency and voltage scaling

 cpufrequtils
 tools to switch between frequency modes, availability depends on your kernel: conservative, ondemand, or performance modes exist.

 cpudyn
 It saves battery, lowers temperature, and can put the computer disks in standby mode if a given period has passed without any I/O operation.

 powertop
 finds the software component(s) that make your {system} use more power than necessary while it is idle. - (this one is really smart)

 upower
 an abstraction of the power controls present in HAL which are now officially obsolete... not yet fully implemented(?).

 cpulimit
 limits the cpu usage of a process, good when something is causing an overload or simply to reduce the load.

 procmeter3
 my fav system monitor- temp, load, usage, in, out, average, etc. cpu, gpu, hdd, network. if it gives a reading, this little beastie will pick it up and give you the facts.

 pm-utils
 suspend / hibernate... this is what you want to know about for these functions.

 bum / rcconf
 these let you disable the things that lurk in the background eating power and resources.


    When you run into a problem solve it the best you can and ask for help when you need it.

---

### Post by idoitprone on 2012-11-18
> **VulpesLagopus said:**
> Hello,

I've just started using Ubuntu 12.04.1 LTS on my Alienware M14x. And I'm having some trouble.
The wifi keeps disconnecting every 5 to 15min. I've read a lot about this on the Internet, but the only solution I found didn't work for me (it was to deactivate the IPv6).
And the other problem is that my battery life is really short since I have a dual-boot Windows 7 and Ubuntu. On Ubuntu it lasts 3 hours maximum!!!

So I'm really new to all this stuff, I know I have to give you a lot more details but I just don't know what. So if someone is kind enough to help me, I'll do anything :).

Thank you in advance.

```
lspci -nnk 
```
battery life is based on hardware

I suspect your have nvidia optimus

---

### Post by Aaron Christianson on 2012-11-18
laptop-mode-tools is the best one-stop solution for battery life. Just install it and restart, and your power usage will be significantly improved. It can also be tweaked, but the default settings are good.

Some of the programs gbrowning mentioned are also good, but some are out of date. laptop-mode-tools should be the first thing you try these days, though some of the others may be used to supplement it.

Also, turn off bluetooth when not it use.

---

### Post by idoitprone on 2012-11-18
> **Aaron Christianson said:**
> laptop-mode-tools is the best one-stop solution for battery life. Just install it and restart, and your power usage will be significantly improved. It can also be tweaked, but the default settings are good.

Some of the programs gbrowning mentioned are also good, but some are out of date. laptop-mode-tools should be the first thing you try these days, though some of the others may be used to supplement it.

Also, turn off bluetooth when not it use.
laptop tools are not kernel drivers. 
Alienware M14X is a gaming laptop which mean it will probably have nvidia optimus.

If he does have nvidia optimus, that suggest will not help much when there is a graphic chip draining all the power. I never understand laptop-tools. The user is usually not better than the kernel at optimizing power performance

---

### Post by VulpesLagopus on 2012-11-19
Idoitprone hi,

I've run your command and got the following

```
00:00.0 Host bridge [0600]: Intel Corporation Ivy Bridge DRAM Controller [8086:0154] (rev 09)
    Subsystem: Dell Device [1028:0552]
    Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation Ivy Bridge PCI Express Root Port [8086:0151] (rev 09)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0166] (rev 09)
    Subsystem: Dell Device [1028:0552]
    Kernel driver in use: i915
    Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation Panther Point USB xHCI Host Controller [8086:1e31] (rev 04)
    Subsystem: Dell Device [1028:0552]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation Panther Point MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: Dell Device [1028:0552]
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
    Subsystem: Dell Device [1028:0552]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation Panther Point High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: Dell Device [1028:0552]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 1 [8086:1e10] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 3 [8086:1e14] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 4 [8086:1e16] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
    Subsystem: Dell Device [1028:0552]
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation Panther Point LPC Controller [8086:1e57] (rev 04)
    Subsystem: Dell Device [1028:0552]
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
    Subsystem: Dell Device [1028:0552]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Panther Point SMBus Controller [8086:1e22] (rev 04)
    Subsystem: Dell Device [1028:0552]
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:0fd1] (rev a1)
    Subsystem: Dell Device [1028:0552]
    Kernel modules: nouveau, nvidiafb
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0e1b] (rev ff)
    Kernel driver in use: snd_hda_intel
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: Dell Device [1028:0552]
    Kernel driver in use: atl1c
    Kernel modules: atl1c
08:00.0 Network controller [0280]: Atheros Communications Inc. AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Bigfoot Networks, Inc. Device [1a56:2003]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
09:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader [10ec:5209] (rev 01)
    Subsystem: Dell Device [1028:0552]
    Kernel driver in use: rts_pstor
    Kernel modules: rts_pstor
09:00.1 SD Host controller [0805]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader [10ec:5209] (rev 01)
    Subsystem: Dell Device [1028:0552]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
```So I tried to read, it I don't know if it's optimus but I surely have something from Nvidia. In the case where the battery life is shorten beacause of the Nvidia optimus is there a possible solution ? And I don't understand because under Windows 7 I still have at least 6 hours when the battery is full and with Ubuntu only three.

Aaron Christianson hi,

thank you for your answer and I will certainly test your laptop-mode tools, but yesterday I installed something like this called Jupiter. Maybe yours will be better.

gbrowning hi,

Like you said it seems "a bit" complicated for a new on Linux, but i will try to figure it out. Maybe something will help me.

---

### Post by idoitprone on 2012-11-19
```
sudo modprobe -r nvidiafb
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic bbswitch


```

```
sudo bash -c 'echo "options bbswitch load_state=0" >> /etc/modprobe.d/bbswitch.conf'
```
reboot


[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by VulpesLagopus on 2012-11-19
So i think everything went well until the 4th command line, it says it can't find the package bbswitch : 

```
denis@denis-M14xR2:~$ sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic bbswitch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bbswitch

```

Edit : 
Maybe I can try with vga_switcheroo ?

---

### Post by idoitprone on 2012-11-19
> **VulpesLagopus said:**
> So i think everything went well until the 4th command line, it says it can't find the package bbswitch : 

```
denis@denis-M14xR2:~$ sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic bbswitch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bbswitch

```Edit : 
Maybe I can try with vga_switcheroo ?

```
sudo add-apt-repository ppa:bumblebee/stable

sudo apt-get update
```?

---

### Post by VulpesLagopus on 2012-11-19
```
sudo apt-get update
```

gives me this : 

```
denis@denis-M14xR2:~$ sudo apt-get update
[sudo] password for denis: 
Ign http://security.ubuntu.com precise-security InRelease
Ign http://ppa.launchpad.net precise InRelease                      
Ign http://ppa.launchpad.net precise InRelease                       
Ign http://ppa.launchpad.net precise InRelease                       
Ign http://extras.ubuntu.com precise InRelease                       
Hit http://security.ubuntu.com precise-security Release.gpg          
Hit http://ppa.launchpad.net precise Release.gpg                     
Hit http://ppa.launchpad.net precise Release.gpg                                    
Hit http://extras.ubuntu.com precise Release.gpg                                    
Hit http://security.ubuntu.com precise-security Release                             
Hit http://ppa.launchpad.net precise Release.gpg                                    
Hit http://extras.ubuntu.com precise Release                                        
Ign http://ch.archive.ubuntu.com precise InRelease                    
Hit http://ppa.launchpad.net precise Release                          
Hit http://security.ubuntu.com precise-security/main Sources                        
Hit http://extras.ubuntu.com precise/main Sources                                   
Hit http://ppa.launchpad.net precise Release                         
Hit http://security.ubuntu.com precise-security/restricted Sources                  
Hit http://security.ubuntu.com precise-security/universe Sources                    
Hit http://security.ubuntu.com precise-security/multiverse Sources                  
Hit http://security.ubuntu.com precise-security/main i386 Packages                  
Hit http://extras.ubuntu.com precise/main i386 Packages                             
Ign http://extras.ubuntu.com precise/main TranslationIndex                          
Hit http://security.ubuntu.com precise-security/restricted i386 Packages            
Ign http://ch.archive.ubuntu.com precise-updates InRelease                          
Hit http://ppa.launchpad.net precise Release                                        
Hit http://security.ubuntu.com precise-security/universe i386 Packages              
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages            
Hit http://security.ubuntu.com precise-security/main TranslationIndex               
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex         
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex         
Hit http://security.ubuntu.com precise-security/universe TranslationIndex           
Hit http://ppa.launchpad.net precise/main Sources                                   
Hit http://ppa.launchpad.net precise/main i386 Packages                             
Ign http://ppa.launchpad.net precise/main TranslationIndex                          
Ign http://ch.archive.ubuntu.com precise-backports InRelease                        
Hit http://ch.archive.ubuntu.com precise Release.gpg                 
Hit http://security.ubuntu.com precise-security/main Translation-en                 
Hit http://security.ubuntu.com precise-security/multiverse Translation-en           
Hit http://ppa.launchpad.net precise/main Sources                                   
Hit http://ppa.launchpad.net precise/main i386 Packages                             
Ign http://ppa.launchpad.net precise/main TranslationIndex           
Hit http://ch.archive.ubuntu.com precise-updates Release.gpg         
Hit http://security.ubuntu.com precise-security/restricted Translation-en           
Hit http://ch.archive.ubuntu.com precise-backports Release.gpg                      
Hit http://ppa.launchpad.net precise/main Sources                                   
Hit http://ppa.launchpad.net precise/main i386 Packages                             
Ign http://ppa.launchpad.net precise/main TranslationIndex                          
Hit http://ch.archive.ubuntu.com precise Release                                    
Hit http://security.ubuntu.com precise-security/universe Translation-en             
Hit http://ch.archive.ubuntu.com precise-updates Release                            
Hit http://ch.archive.ubuntu.com precise-backports Release                          
Hit http://ch.archive.ubuntu.com precise/main Sources                               
Hit http://ch.archive.ubuntu.com precise/restricted Sources          
Hit http://ch.archive.ubuntu.com precise/universe Sources            
Hit http://ch.archive.ubuntu.com precise/multiverse Sources          
Hit http://ch.archive.ubuntu.com precise/main i386 Packages          
Hit http://ch.archive.ubuntu.com precise/restricted i386 Packages    
Hit http://ch.archive.ubuntu.com precise/universe i386 Packages      
Hit http://ch.archive.ubuntu.com precise/multiverse i386 Packages    
Hit http://ch.archive.ubuntu.com precise/main TranslationIndex       
Hit http://ch.archive.ubuntu.com precise/multiverse TranslationIndex 
Hit http://ch.archive.ubuntu.com precise/restricted TranslationIndex 
Hit http://ch.archive.ubuntu.com precise/universe TranslationIndex   
Hit http://ch.archive.ubuntu.com precise-updates/main Sources        
Hit http://ch.archive.ubuntu.com precise-updates/restricted Sources  
Hit http://ch.archive.ubuntu.com precise-updates/universe Sources    
Ign http://extras.ubuntu.com precise/main Translation-en             
Hit http://ch.archive.ubuntu.com precise-updates/multiverse Sources  
Hit http://ch.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://ch.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://ch.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://ch.archive.ubuntu.com precise-updates/multiverse i386 Packages
Ign http://extras.ubuntu.com precise/main Translation-fr             
Hit http://ch.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://ch.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://ch.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://ch.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://ch.archive.ubuntu.com precise-backports/main Sources
Hit http://ch.archive.ubuntu.com precise-backports/restricted Sources
Hit http://ch.archive.ubuntu.com precise-backports/universe Sources
Hit http://ch.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://ch.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://ch.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://ch.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://ch.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://ch.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://ch.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://ch.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://ch.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://ch.archive.ubuntu.com precise/main Translation-en
Hit http://ch.archive.ubuntu.com precise/main Translation-fr
Hit http://ch.archive.ubuntu.com precise/multiverse Translation-en
Hit http://ch.archive.ubuntu.com precise/multiverse Translation-fr
Hit http://ch.archive.ubuntu.com precise/restricted Translation-en
Hit http://ch.archive.ubuntu.com precise/restricted Translation-fr
Hit http://ch.archive.ubuntu.com precise/universe Translation-en
Hit http://ch.archive.ubuntu.com precise/universe Translation-fr
Hit http://ch.archive.ubuntu.com precise-updates/main Translation-en
Hit http://ch.archive.ubuntu.com precise-updates/main Translation-fr
Hit http://ch.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://ch.archive.ubuntu.com precise-updates/multiverse Translation-fr
Hit http://ch.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://ch.archive.ubuntu.com precise-updates/restricted Translation-fr
Hit http://ch.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://ch.archive.ubuntu.com precise-updates/universe Translation-fr
Hit http://ch.archive.ubuntu.com precise-backports/main Translation-en
Hit http://ch.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://ch.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://ch.archive.ubuntu.com precise-backports/universe Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-fr
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-fr
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-fr
Reading package lists... Done
```

---

### Post by idoitprone on 2012-11-19
are you sure you cannnot install bbswitch?

sudo apt-get install bbswitch?

ok i guess i will have to install it manuallly if that not happen

install the other components first 

```
sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic
```

---

### Post by idoitprone on 2012-11-19
```
sudo apt-get install build-essential checkinstall

sudo apt-get install cvs subversion git-core mercurial dkms

cd

git clone git://github.com/Bumblebee-Project/bbswitch.git bbswitch

cd bbswitch

sudo make -f Makefile.dkms
```

dont forget to run this command

```

sudo bash -c 'echo "options bbswitch load_state=0" >> /etc/modprobe.d/bbswitch.conf'
``` before you reboot

---

### Post by VulpesLagopus on 2012-11-19
I ran all the last commands you gave me. Everything seems fine : 

```
denis@denis-M14xR2:~$ sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libnl2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  bbswitch-dkms dkms libturbojpeg linux-headers-3.2.0-33-generic nvidia-current
  nvidia-settings screen-resolution-extra virtualgl virtualgl-libs
The following NEW packages will be installed:
  bbswitch-dkms bumblebee bumblebee-nvidia dkms libturbojpeg
  linux-headers-3.2.0-33-generic linux-headers-generic nvidia-current
  nvidia-settings screen-resolution-extra virtualgl virtualgl-libs
0 upgraded, 12 newly installed, 0 to remove and 3 not upgraded.
Need to get 36.7 MB of archives.
After this operation, 115 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ch.archive.ubuntu.com/ubuntu/ precise-updates/universe libturbojpeg i386 1.1.90+svn733-0ubuntu4.1 [127 kB]
Get:2 http://ppa.launchpad.net/bumblebee/stable/ubuntu/ precise/main virtualgl-libs i386 2.3.2-1~preciseppa1 [198 kB]
Get:3 http://ch.archive.ubuntu.com/ubuntu/ precise/main dkms all 2.2.0.3-1ubuntu3 [73.1 kB]
Get:4 http://ch.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-33-generic i386 3.2.0-33.52 [975 kB]
Get:5 http://ppa.launchpad.net/bumblebee/stable/ubuntu/ precise/main virtualgl i386 2.3.2-1~preciseppa1 [851 kB]
Get:6 http://ppa.launchpad.net/bumblebee/stable/ubuntu/ precise/main bbswitch-dkms all 0.4.2-2~preciseppa1 [10.1 kB]
Get:7 http://ppa.launchpad.net/bumblebee/stable/ubuntu/ precise/main bumblebee i386 3.0.1-3~preciseppa1 [52.1 kB]
Get:8 http://ppa.launchpad.net/bumblebee/stable/ubuntu/ precise/main bumblebee-nvidia i386 3.0.1-3~preciseppa1 [3968 B]
Get:9 http://ch.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-generic i386 3.2.0.33.36 [2638 B]
Get:10 http://ch.archive.ubuntu.com/ubuntu/ precise-updates/restricted nvidia-current i386 295.40-0ubuntu1.1 [33.4 MB]
Get:11 http://ch.archive.ubuntu.com/ubuntu/ precise/main screen-resolution-extra all 0.14ubuntu2 [12.8 kB]
Get:12 http://ch.archive.ubuntu.com/ubuntu/ precise/main nvidia-settings i386 295.33-0ubuntu1 [926 kB]
Fetched 36.7 MB in 28s (1282 kB/s)                                                  
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "en",
    LC_ALL = (unset),
    LC_TIME = "fr_CH.UTF-8",
    LC_MONETARY = "fr_CH.UTF-8",
    LC_ADDRESS = "fr_CH.UTF-8",
    LC_TELEPHONE = "fr_CH.UTF-8",
    LC_NAME = "fr_CH.UTF-8",
    LC_MEASUREMENT = "fr_CH.UTF-8",
    LC_IDENTIFICATION = "fr_CH.UTF-8",
    LC_NUMERIC = "fr_CH.UTF-8",
    LC_PAPER = "fr_CH.UTF-8",
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously unselected package libturbojpeg.
(Reading database ... 204449 files and directories currently installed.)
Unpacking libturbojpeg (from .../libturbojpeg_1.1.90+svn733-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package virtualgl-libs.
Unpacking virtualgl-libs (from .../virtualgl-libs_2.3.2-1~preciseppa1_i386.deb) ...
Selecting previously unselected package virtualgl.
Unpacking virtualgl (from .../virtualgl_2.3.2-1~preciseppa1_i386.deb) ...
Selecting previously unselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package bbswitch-dkms.
Unpacking bbswitch-dkms (from .../bbswitch-dkms_0.4.2-2~preciseppa1_all.deb) ...
Selecting previously unselected package bumblebee.
Unpacking bumblebee (from .../bumblebee_3.0.1-3~preciseppa1_i386.deb) ...
Selecting previously unselected package linux-headers-3.2.0-33-generic.
Unpacking linux-headers-3.2.0-33-generic (from .../linux-headers-3.2.0-33-generic_3.2.0-33.52_i386.deb) ...
Selecting previously unselected package linux-headers-generic.
Unpacking linux-headers-generic (from .../linux-headers-generic_3.2.0.33.36_i386.deb) ...
Selecting previously unselected package nvidia-current.
Unpacking nvidia-current (from .../nvidia-current_295.40-0ubuntu1.1_i386.deb) ...
Selecting previously unselected package bumblebee-nvidia.
Unpacking bumblebee-nvidia (from .../bumblebee-nvidia_3.0.1-3~preciseppa1_i386.deb) ...
Selecting previously unselected package screen-resolution-extra.
Unpacking screen-resolution-extra (from .../screen-resolution-extra_0.14ubuntu2_all.deb) ...
Selecting previously unselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_295.33-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
locale: Cannot set LC_ALL to default locale: No such file or directory
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libturbojpeg (1.1.90+svn733-0ubuntu4.1) ...
Setting up virtualgl-libs (2.3.2-1~preciseppa1) ...
Setting up virtualgl (2.3.2-1~preciseppa1) ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up bbswitch-dkms (0.4.2-2~preciseppa1) ...
Loading new bbswitch-0.4.2 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-33-generic-pae
Building initial module for 3.2.0-33-generic-pae
Done.

bbswitch:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-33-generic-pae/updates/dkms/

depmod.......

DKMS: install completed.
Setting up bumblebee (3.0.1-3~preciseppa1) ...
Adding members from group(s) 'adm sudo admin' to 'bumblebee':
denis
Adding user denis to group bumblebee
update-initramfs: deferring update (trigger activated)
bumblebeed start/running, process 13235
Setting up linux-headers-3.2.0-33-generic (3.2.0-33.52) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
Setting up linux-headers-generic (3.2.0.33.36) ...
Setting up nvidia-current (295.40-0ubuntu1.1) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libOpenCL.so because associated file /usr/lib32/nvidia-current/libOpenCL.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match Alienware with Dell Inc.
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match Alienware with LENOVO
DEBUG:Quirk doesn't match
Loading new nvidia-current-295.40 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-33-generic-pae
Building for architecture i686
Building initial module for 3.2.0-33-generic-pae
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-33-generic-pae/updates/dkms/

depmod....

DKMS: install completed.
Setting up screen-resolution-extra (0.14ubuntu2) ...
Setting up nvidia-settings (295.33-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-settings/ld.so.conf to provide /etc/ld.so.conf.d/nvidia_settings.conf (nvidia_settings_conf) in auto mode.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up bumblebee-nvidia (3.0.1-3~preciseppa1) ...
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in manual mode.
bumblebeed stop/waiting
bumblebeed start/running, process 15312
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-33-generic-pae
denis@denis-M14xR2:~$ sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic bbswitch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bbswitch
denis@denis-M14xR2:~$ sudo apt-get install bbswitch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bbswitch
denis@denis-M14xR2:~$ sudo apt-get install build-essential checkinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following package was automatically installed and is no longer required:
  libnl2
Use 'apt-get autoremove' to remove them.
Suggested packages:
  gettext
The following NEW packages will be installed:
  checkinstall
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 118 kB of archives.
After this operation, 514 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ch.archive.ubuntu.com/ubuntu/ precise/universe checkinstall i386 1.6.2-3ubuntu1 [118 kB]
Fetched 118 kB in 0s (428 kB/s)  
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "en",
    LC_ALL = (unset),
    LC_TIME = "fr_CH.UTF-8",
    LC_MONETARY = "fr_CH.UTF-8",
    LC_ADDRESS = "fr_CH.UTF-8",
    LC_TELEPHONE = "fr_CH.UTF-8",
    LC_NAME = "fr_CH.UTF-8",
    LC_MEASUREMENT = "fr_CH.UTF-8",
    LC_IDENTIFICATION = "fr_CH.UTF-8",
    LC_NUMERIC = "fr_CH.UTF-8",
    LC_PAPER = "fr_CH.UTF-8",
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously unselected package checkinstall.
(Reading database ... 213221 files and directories currently installed.)
Unpacking checkinstall (from .../checkinstall_1.6.2-3ubuntu1_i386.deb) ...
Processing triggers for man-db ...
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up checkinstall (1.6.2-3ubuntu1) ...
denis@denis-M14xR2:~$ sudo apt-get install cvs subversion git-core mercurial dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
dkms set to manually installed.
The following package was automatically installed and is no longer required:
  libnl2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  git git-man libapr1 libaprutil1 libdb4.8 liberror-perl libsvn1 mercurial-common
Suggested packages:
  mksh rcs git-daemon-run git-daemon-sysvinit git-doc git-el git-arch git-cvs
  git-svn git-email git-gui gitk gitweb qct wish vim emacs kdiff3 tkdiff meld
  xxdiff python-mysqldb python-pygments subversion-tools db4.8-util
The following NEW packages will be installed:
  cvs git git-core git-man libapr1 libaprutil1 libdb4.8 liberror-perl libsvn1
  mercurial mercurial-common subversion
0 upgraded, 12 newly installed, 0 to remove and 3 not upgraded.
Need to get 13.1 MB of archives.
After this operation, 31.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ch.archive.ubuntu.com/ubuntu/ precise/main libdb4.8 i386 4.8.30-11ubuntu1 [711 kB]
Get:2 http://ch.archive.ubuntu.com/ubuntu/ precise/main libapr1 i386 1.4.6-1 [91.3 kB]
Get:3 http://ch.archive.ubuntu.com/ubuntu/ precise/main libaprutil1 i386 1.3.12+dfsg-3 [75.4 kB]
Get:4 http://ch.archive.ubuntu.com/ubuntu/ precise/main libsvn1 i386 1.6.17dfsg-3ubuntu3 [839 kB]
Get:5 http://ch.archive.ubuntu.com/ubuntu/ precise/main cvs i386 2:1.12.13+real-8 [2469 kB]
Get:6 http://ch.archive.ubuntu.com/ubuntu/ precise/main liberror-perl all 0.17-1 [23.8 kB]
Get:7 http://ch.archive.ubuntu.com/ubuntu/ precise/main git-man all 1:1.7.9.5-1 [630 kB]
Get:8 http://ch.archive.ubuntu.com/ubuntu/ precise/main git i386 1:1.7.9.5-1 [5963 kB]
Get:9 http://ch.archive.ubuntu.com/ubuntu/ precise/main git-core all 1:1.7.9.5-1 [1384 B]
Get:10 http://ch.archive.ubuntu.com/ubuntu/ precise/universe mercurial-common all 2.0.2-1ubuntu1 [1945 kB]
Get:11 http://ch.archive.ubuntu.com/ubuntu/ precise/universe mercurial i386 2.0.2-1ubuntu1 [37.1 kB]
Get:12 http://ch.archive.ubuntu.com/ubuntu/ precise/main subversion i386 1.6.17dfsg-3ubuntu3 [293 kB]
Fetched 13.1 MB in 10s (1268 kB/s)                                                  
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "en",
    LC_ALL = (unset),
    LC_TIME = "fr_CH.UTF-8",
    LC_MONETARY = "fr_CH.UTF-8",
    LC_ADDRESS = "fr_CH.UTF-8",
    LC_TELEPHONE = "fr_CH.UTF-8",
    LC_NAME = "fr_CH.UTF-8",
    LC_MEASUREMENT = "fr_CH.UTF-8",
    LC_IDENTIFICATION = "fr_CH.UTF-8",
    LC_NUMERIC = "fr_CH.UTF-8",
    LC_PAPER = "fr_CH.UTF-8",
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously unselected package libdb4.8.
(Reading database ... 213253 files and directories currently installed.)
Unpacking libdb4.8 (from .../libdb4.8_4.8.30-11ubuntu1_i386.deb) ...
Selecting previously unselected package libapr1.
Unpacking libapr1 (from .../libapr1_1.4.6-1_i386.deb) ...
Selecting previously unselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.3.12+dfsg-3_i386.deb) ...
Selecting previously unselected package libsvn1.
Unpacking libsvn1 (from .../libsvn1_1.6.17dfsg-3ubuntu3_i386.deb) ...
Selecting previously unselected package cvs.
Unpacking cvs (from .../cvs_2%3a1.12.13+real-8_i386.deb) ...
Selecting previously unselected package liberror-perl.
Unpacking liberror-perl (from .../liberror-perl_0.17-1_all.deb) ...
Selecting previously unselected package git-man.
Unpacking git-man (from .../git-man_1%3a1.7.9.5-1_all.deb) ...
Selecting previously unselected package git.
Unpacking git (from .../git_1%3a1.7.9.5-1_i386.deb) ...
Selecting previously unselected package git-core.
Unpacking git-core (from .../git-core_1%3a1.7.9.5-1_all.deb) ...
Selecting previously unselected package mercurial-common.
Unpacking mercurial-common (from .../mercurial-common_2.0.2-1ubuntu1_all.deb) ...
Selecting previously unselected package mercurial.
Unpacking mercurial (from .../mercurial_2.0.2-1ubuntu1_i386.deb) ...
Selecting previously unselected package subversion.
Unpacking subversion (from .../subversion_1.6.17dfsg-3ubuntu3_i386.deb) ...
Processing triggers for doc-base ...
Processing 6 added doc-base files...
Processing triggers for install-info ...
/etc/environment: line 4: warning: setlocale: LC_NUMERIC: cannot change locale (fr_CH.UTF-8)
/etc/environment: line 5: warning: setlocale: LC_TIME: cannot change locale (fr_CH.UTF-8)
/etc/default/locale: line 3: warning: setlocale: LC_NUMERIC: cannot change locale (fr_CH.UTF-8)
/etc/default/locale: line 4: warning: setlocale: LC_TIME: cannot change locale (fr_CH.UTF-8)
Processing triggers for man-db ...
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up libdb4.8 (4.8.30-11ubuntu1) ...
Setting up libapr1 (1.4.6-1) ...
Setting up libaprutil1 (1.3.12+dfsg-3) ...
Setting up libsvn1 (1.6.17dfsg-3ubuntu3) ...
Setting up cvs (2:1.12.13+real-8) ...
Allowing use of questionable username.
Adding group `_cvsadmin' (GID 125) ...
Done.
Setting up liberror-perl (0.17-1) ...
Setting up git-man (1:1.7.9.5-1) ...
Setting up git (1:1.7.9.5-1) ...
Setting up git-core (1:1.7.9.5-1) ...
Setting up mercurial-common (2.0.2-1ubuntu1) ...
Setting up mercurial (2.0.2-1ubuntu1) ...
locale: Cannot set LC_ALL to default locale: No such file or directory

Creating config file /etc/mercurial/hgrc.d/hgext.rc with new version
Setting up subversion (1.6.17dfsg-3ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
denis@denis-M14xR2:~$ cd
denis@denis-M14xR2:~$ 
denis@denis-M14xR2:~$ git clone git://github.com/Bumblebee-Project/bbswitch.git bbswitch
Cloning into 'bbswitch'...
remote: Counting objects: 314, done.
remote: Compressing objects: 100% (175/175), done.
remote: Total 314 (delta 156), reused 293 (delta 135)
Receiving objects: 100% (314/314), 50.42 KiB, done.
Resolving deltas: 100% (156/156), done.
denis@denis-M14xR2:~$ cd bbswitch
denis@denis-M14xR2:~/bbswitch$ sudo make -f Makefile.dkms
mkdir -p '/usr/src/bbswitch-0.5'
cp Makefile bbswitch.c '/usr/src/bbswitch-0.5'
sed 's/#MODULE_VERSION#/0.5/' dkms/dkms.conf > '/usr/src/bbswitch-0.5/dkms.conf'
dkms build -m bbswitch -v 0.5

Creating symlink /var/lib/dkms/bbswitch/0.5/source ->
                 /usr/src/bbswitch-0.5

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.2.0-33-generic-pae KVERSION=3.2.0-33-generic-pae....
cleaning build area....

DKMS: build completed.
dkms install -m bbswitch -v 0.5

bbswitch:
Running module version sanity check.
 - Original module
   - This kernel never originally had a module by this name
 - Installation
   - Installing to /lib/modules/3.2.0-33-generic-pae/updates/dkms/

depmod....

DKMS: install completed.

```So is it installed now ? Should I reboot and check the battery life ?

---

### Post by idoitprone on 2012-11-19
did you run this?
```
sudo bash -c 'echo "options bbswitch load_state=0" >> /etc/modprobe.d/bbswitch.conf'
```

reboot

---

### Post by VulpesLagopus on 2012-11-19
I ran it, I rebooted and now I have 7 hours of battery life

Thanks very much to all of you!!!

---

