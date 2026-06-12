---
title: "cpu temperature (high)"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by shafaghi on 2013-04-21
my laptop is k42jp(asus).
4gig ram 
cpu : core i3
amd readon HD 6570M installed from additional drive.

cpu work hight temperature
ubuntu 12.04.2 32bit
please help me for solve hight temperature.


[CODEAdapter: Virtual device
temp1:        +65.0°C  (crit = +93.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +60.0°C  (high = +80.0°C, crit = +90.0°C)
Core 2:       +70.0°C  (high = +80.0°C, crit = +90.0°C)][/CODE]

sometimes 75 - 86 °C

---

### Post by Dreamer Fithp Apprentice on 2013-04-23
It's not clear to me what you are asking. But if you are getting excessive temperatures:

Get a flashlight, open up the case and inspect closely for dust. Be sure to check the heatsinks. Often they get clogged with dust, cat hair, lint, tiny green men from Mars, etc. Check all the grills. Get it all really clean. Use a vacuum cleaner if you need to. Or a can of pressurised air. Or something like a twist tie you can poke in between the vanes of the heat sinks.

Make sure all your fans are working. Little fan on top of the cpu. Big case ventilation fans. Power supply fan. If that isn't enough to solve the problem you need more or bigger fans. The more cfm the better. As a temporary measure it might help to point a box fan directly into the housing with the case open. Then buy some badass fans from someplace like newegg or Tiger.  There are more extraordinary steps you can take to cool your system more but if you had the kind of system that really needed immersion coolling or other Star Trek stuff, you'd already know about it. See if this solves the problem anyway. If I've misunderstood the question, please restate it more clearly.

---

### Post by 3rdalbum on 2013-04-23
Dreamer: You've misread, this is a laptop.

Shafaghi: Have you installed the graphics driver for your system? Go into Ubuntu Software Center, go to the Edit menu and come down to Software Sources. The last tab in this new program allows you to install the ATI graphics driver. This may help.

If your problems remain, try looking in System Monitor when the computer is getting hot. See if there are any programs taking up large amounts of CPU time (5% or more). End or quit the programs that are running your CPU high.

---

### Post by shafaghi on 2013-04-23
thanks.[COLOR=#000000]

ATI graphics drive (6570m)[/COLOR] = installed


for example:
in trisquel linux:

( my friend laptop)

result:

```
[COLOR=#000000][FONT=dejavu sans mono]acpitz-virtual-0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Adapter: Virtual device[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]temp1:        +47.0°C  (crit = +128.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]temp2:         +58.0°C  (crit = +128.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]temp3:        +29.0°C  (crit = +128.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]temp4:        +43.0°C  (crit = +128.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]temp5:        +20.0°C  (crit = +128.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]temp6:         +0.0°C  (crit = +128.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]temp7:         +0.0°C  (crit = +128.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]temp8:         +0.0°C  (crit = +128.0°C)[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]coretemp-isa-0000[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Adapter: ISA adapter[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Physical id 0:  +49.0°C  (high = +86.0°C, crit = +100.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Core 0:         +47.0°C  (high = +86.0°C, crit = +100.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Core 1:         +49.0°C  (high = +86.0°C, crit = +100.0°C)[/FONT][/COLOR]
```




but , ubuntu 12.10

```
[COLOR=#000000][FONT=dejavu sans mono]acpitz-virtual-0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Adapter: Virtual device[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]temp1:        +82.0°C  (crit = +128.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]temp2:         +70.0°C  (crit = +128.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]temp3:        +38.0°C  (crit = +128.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]temp4:        +62.0°C  (crit = +128.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]temp5:        +20.0°C  (crit = +128.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]temp6:         +0.0°C  (crit = +128.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]temp7:         +0.0°C  (crit = +128.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]temp8:         +0.0°C  (crit = +128.0°C)[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]coretemp-isa-0000[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Adapter: ISA adapter[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Physical id 0:  +80.0°C  (high = +86.0°C, crit = +100.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Core 0:         +68.0°C  (high = +86.0°C, crit = +100.0°C)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Core 1:         +80.0°C  (high = +86.0°C, crit = +100.0°C)[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]radeon-pci-0100[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Adapter: PCI adapter[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]temp1:        +70.0°C[/FONT][/COLOR]
```

I think unity is heavy.

---

### Post by pqwoerituytrueiwoq on 2013-04-23
what hardware is on your friends laptop

a dedicated GPU will make a system run hotter, laptops generally only have one cooling fan and a heatsync that connects the fan CPU and GPU, so one fan cools both the CPU and GPU
my laptop only has a CPU (Intel Pentium B970 @ 2.3GHz, sandy bridge based BTW), by idle temps are only 40-45C, would go lower but the fan turns off at 40C and comes back on at 45C
*this CPU has a integrated GPU (Intel HD 3000)
your temps look like my old laptop (HP Compaq CQ60-215-DX)

you should be able to access the cooling fan by lifting the keyboard up, there are 4 or 5 pins that push up towards the monitor
they are above the ESC, F5, F10/F11, and Delete keys
push the pin in, i suggest using a tooth pick to avoid scratches, and lifting up on the key then move to the next pin
they keyboard will lift up and you will see the fan on the left side,take a can of air and treat the dust bunnies like a Dalek treats a non Dalek

---

### Post by abhich on 2013-04-23
try using jupiter ... works for mw

---

### Post by 3rdalbum on 2013-04-23
> **3rdalbum said:**
> If your problems remain, try looking in System Monitor when the computer is getting hot. See if there are any programs taking up large amounts of CPU time (5% or more). End or quit the programs that are running your CPU high.

^Did you try this?

---

### Post by shafaghi on 2013-04-29
> **abhich said:**
> try using jupiter ... works for mw

jupiter dose not work very well.
no change ...

---

### Post by shafaghi on 2013-04-29
installed :ATI/AMD proprietary FGLRX graphics driver
from additional drivers

---

### Post by Kopkins on 2013-04-29
Did that fix your issue?

Did you try looking for processes that are using a lot of CPU?

---

### Post by DrBob89 on 2013-04-29
I have an old Toshiba laptop that runs really hot when streaming video.  There was a weather website that ran a video automatically when Chrome opened it and would loop the video indefinitely.  Since I usually keep the audio off, my only tip off was when it was getting hot.

---

### Post by shafaghi on 2013-04-29
```
xamin@xamin-K42JP:~$ top

top - 12:37:48 up  2:14,  2 users,  load average: 0.58, 0.54, 0.49
Tasks: 174 total,   1 running, 173 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.7%us,  3.9%sy,  0.0%ni, 91.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3979536k total,  1378884k used,  2600652k free,    62664k buffers
Swap:  8416252k total,        0k used,  8416252k free,   815032k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1894 xamin     20   0  283m 108m  39m S   15  2.8  13:01.38 compiz             
 1143 root      20   0  228m 105m  59m S    7  2.7   6:13.85 Xorg               
 8360 xamin     20   0 91608  14m  10m S    2  0.4   0:00.33 gnome-terminal     
 2514 xamin     20   0  121m  17m  13m S    1  0.4   0:59.09 psensor            
 1866 xamin     20   0  6868 3212  632 S    0  0.1   0:09.56 dbus-daemon        
 1902 xamin     20   0  3708  792  656 S    0  0.0   0:01.59 syndaemon          
 1987 xamin     20   0 67736 6772 3272 S    0  0.2   0:12.75 hud-service        
 7571 root      20   0     0    0    0 S    0  0.0   0:01.03 kworker/2:0        
 8424 xamin     20   0  2852 1176  876 R    0  0.0   0:00.03 top                
    1 root      20   0  3656 1984 1288 S    0  0.0   0:01.03 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.09 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.19 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.11 watchdog/0         
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset             
   22 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper            
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 kdevtmpfs  
```

---

### Post by Mopar1973Man on 2013-04-29
Ok...

I would physically check the fan, heat sink, and the heat sink compound. Make sure the fan is actually turn a good rate of speed, the heat sink is clean and clean of debris, and the heat sink compound is completely dried out. Then I would watch system process, CPU load the fan speed. Run the computer hard and see how hot it gets. 

Like typically I run AMD's Cool and Quiet on my main computer. I clock back and keeps the CPU cooler this way also since I'm on solar, hydro, battery power house I need to conserve power. Like right now my CPU temp are about 25-27*C and at full load for several hours it might touch 60-65*F depending on room temperature. If I touch 70*F its time for a clean up of the case and heat sink. 

Now like my laptop Toshiba Satellite it runs hot naturally while on battery operation. It only turns on the fan if the CPU get critically hot at about 60-65*C then cools to about 50*C and stops. But in battery operation the AMD is clocked back to 1.4 GHz (4 core) but plugged in its full speed ahead 1.9 GHz and the fan run continuous but the CPU temps are much lower with it plugged in. (25-40*C)

---

### Post by shafaghi on 2013-04-29
> **Mopar1973Man said:**
> Ok...

I would physically check the fan, heat sink, and the heat sink compound. Make sure the fan is actually turn a good rate of speed, the heat sink is clean and clean of debris, and the heat sink compound is completely dried out. Then I would watch system process, CPU load the fan speed. Run the computer hard and see how hot it gets. 

Like typically I run AMD's Cool and Quiet on my main computer. I clock back and keeps the CPU cooler this way also since I'm on solar, hydro, battery power house I need to conserve power. Like right now my CPU temp are about 25-27*C and at full load for several hours it might touch 60-65*F depending on room temperature. If I touch 70*F its time for a clean up of the case and heat sink. 

Now like my laptop Toshiba Satellite it runs hot naturally while on battery operation. It only turns on the fan if the CPU get critically hot at about 60-65*C then cools to about 50*C and stops. But in battery operation the AMD is clocked back to 1.4 GHz (4 core) but plugged in its full speed ahead 1.9 GHz and the fan run continuous but the CPU temps are much lower with it plugged in. (25-40*C)



I don't know exactly.
I usually use laptop without battery.

intel corei3.
vga:amd 6570M 1 g.

---

### Post by dandroid13 on 2013-04-29
Give this a try: [http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html](http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html)
Here, with many tabs opened, it stays around 50ºC, Core i7 with Nvidia GPU.

---

### Post by shafaghi on 2013-04-29
but ,ubuntu 12.04.2 wrong recognize vga.
my vga is amd 6570 but ubuntu show:
```
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Mobility Radeon HD 5000
OpenGL version string: 4.2.11627 Compatibility Profile Context
```

---

### Post by shafaghi on 2013-04-29
> **dandroid13 said:**
> Give this a try: [http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html](http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html)
Here, with many tabs opened, it stays around 50ºC, Core i7 with Nvidia GPU.

```
xamin@xamin-K42JP:~$ sudo add-apt-repository ppa:linrunner/tlp
[sudo] password for xamin: 
Sorry, try again.
[sudo] password for xamin: 
You are about to add the following PPA to your system:
 TLP is a power management tool for Linux. It brings you the benefits of advanced power management without the need to understand every technical detail.

Project homepage: http://linrunner.de/tlp
 More info: https://launchpad.net/~linrunner/+archive/tlp
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpy0kCqZ/secring.gpg' created
gpg: keyring `/tmp/tmpy0kCqZ/pubring.gpg' created
gpg: requesting key 02D65EFF from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpy0kCqZ/trustdb.gpg: trustdb created
gpg: key 02D65EFF: public key "Launchpad PPA for linrunner" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
xamin@xamin-K42JP:~$ sudo apt-get update
Hit http://security.ubuntu.com precise-security Release.gpg                    
Get:1 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Hit http://extras.ubuntu.com precise Release.gpg                     
Hit http://us.archive.ubuntu.com precise Release.gpg                 
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://security.ubuntu.com precise-security Release                        
Get:2 http://ppa.launchpad.net precise Release [11.8 kB]                       
Hit http://extras.ubuntu.com precise Release                                   
Hit http://us.archive.ubuntu.com precise Release                               
Hit http://security.ubuntu.com precise-security/main Sources                   
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://us.archive.ubuntu.com precise-updates Release              
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://security.ubuntu.com precise-security/universe Sources               
Hit http://security.ubuntu.com precise-security/multiverse Sources             
Hit http://security.ubuntu.com precise-security/main i386 Packages    
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex 
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Get:3 http://ppa.launchpad.net precise/main Sources [1,075 B]                  
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources             
Hit http://us.archive.ubuntu.com precise/multiverse Sources           
Hit http://us.archive.ubuntu.com precise/main i386 Packages           
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Get:4 http://ppa.launchpad.net precise/main i386 Packages [1,120 B]   
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com precise/main TranslationIndex        
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex  
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex  
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex    
Hit http://us.archive.ubuntu.com precise-updates/main Sources                  
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://security.ubuntu.com precise-security/main Translation-en   
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Sources     
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources   
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages      
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://us.archive.ubuntu.com precise-backports/main Sources       
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources 
Hit http://us.archive.ubuntu.com precise-backports/universe Sources   
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources 
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en          
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en    
Hit http://us.archive.ubuntu.com precise/universe Translation-en      
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en  
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en
Fetched 14.4 kB in 4s (3,390 B/s)
Reading package lists... Done
xamin@xamin-K42JP:~$ sudo apt-get install tlp tlp-rdw
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ethtool heirloom-mailx smartmontools
Suggested packages:
  exim4 mail-transport-agent gsmartcontrol smart-notifier acpi-call
  tp-smapi-dkms
Recommended packages:
  mailx mailutils
The following NEW packages will be installed:
  ethtool heirloom-mailx smartmontools tlp tlp-rdw
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 840 kB of archives.
After this operation, 2,477 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/linrunner/tlp/ubuntu/ precise/main tlp all 0.3.8.1-3~precise [46.0 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main ethtool i386 1:3.1-1 [91.6 kB]
Get:3 http://ppa.launchpad.net/linrunner/tlp/ubuntu/ precise/main tlp-rdw all 0.3.8.1-3~precise [9,012 B]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise/universe heirloom-mailx i386 12.5-1build1 [238 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise/main smartmontools i386 5.41+svn3365-1 [455 kB]
Fetched 840 kB in 7s (106 kB/s)                                                
Selecting previously unselected package ethtool.
(Reading database ... 173915 files and directories currently installed.)
Unpacking ethtool (from .../ethtool_1%3a3.1-1_i386.deb) ...
Selecting previously unselected package heirloom-mailx.
Unpacking heirloom-mailx (from .../heirloom-mailx_12.5-1build1_i386.deb) ...
Selecting previously unselected package smartmontools.
Unpacking smartmontools (from .../smartmontools_5.41+svn3365-1_i386.deb) ...
Selecting previously unselected package tlp.
Unpacking tlp (from .../tlp_0.3.8.1-3~precise_all.deb) ...
Selecting previously unselected package tlp-rdw.
Unpacking tlp-rdw (from .../tlp-rdw_0.3.8.1-3~precise_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up ethtool (1:3.1-1) ...
Setting up heirloom-mailx (12.5-1build1) ...
update-alternatives: using /usr/bin/heirloom-mailx to provide /usr/bin/mailx (mailx) in auto mode.
Setting up smartmontools (5.41+svn3365-1) ...
Setting up tlp (0.3.8.1-3~precise) ...
acpid restarted.
Setting up tlp-rdw (0.3.8.1-3~precise) ...
xamin@xamin-K42JP:~$ sudo tlp start
TLP started in ac mode.
xamin@xamin-K42JP:~$ sudo apt-get install tp-smapi-dkms acpi-call-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  acpi-call-tools tp-smapi-dkms
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 41.6 kB of archives.
After this operation, 240 kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/linrunner/tlp/ubuntu/ precise/main acpi-call-tools all 1.1.1-2~precise [5,822 B]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/universe tp-smapi-dkms all 0.41-1 [35.8 kB]
Fetched 41.6 kB in 2s (19.6 kB/s)                                              
Selecting previously unselected package acpi-call-tools.
(Reading database ... 174017 files and directories currently installed.)
Unpacking acpi-call-tools (from .../acpi-call-tools_1.1.1-2~precise_all.deb) ...
Selecting previously unselected package tp-smapi-dkms.
Unpacking tp-smapi-dkms (from .../tp-smapi-dkms_0.41-1_all.deb) ...
Setting up acpi-call-tools (1.1.1-2~precise) ...

Creating symlink /var/lib/dkms/acpi-call/1.1.1/source ->
                 /usr/src/acpi-call-1.1.1

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.2.0-40-generic-pae IGNORE_CC_MISMATCH=1 KDIR=/lib/modules/3.2.0-40-generic-pae/build PWD=/var/lib/dkms/acpi-call/1.1.1/build.....
cleaning build area....

DKMS: build completed.

acpi_call:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-40-generic-pae/updates/dkms/

depmod........

DKMS: install completed.
Setting up tp-smapi-dkms (0.41-1) ...

Creating symlink /var/lib/dkms/tp-smapi/0.41/source ->
                 /usr/src/tp-smapi-0.41

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.2.0-40-generic-pae -C /lib/modules/3.2.0-40-generic-pae/build M=/var/lib/dkms/tp-smapi/0.41/build....
cleaning build area....

DKMS: build completed.

thinkpad_ec:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-40-generic-pae/updates/dkms/

tp_smapi.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-40-generic-pae/updates/dkms/

hdaps.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/3.2.0-40-generic-pae/updates/dkms/

depmod....

DKMS: install completed.
```

---

### Post by dandroid13 on 2013-04-29
You need to reboot so the service can start. Then give it a try and check the temp again.

---

### Post by shafaghi on 2013-04-29
```
xamin@xamin-K42JP:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +59.0°C  (crit = +93.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +53.0°C  (high = +80.0°C, crit = +90.0°C)
Core 2:       +54.0°C  (high = +80.0°C, crit = +90.0°C)
```

---

### Post by dandroid13 on 2013-04-29
So, is it any better?

---

### Post by Kopkins on 2013-04-29
I would say so, his old temps were in the 80's.

---

### Post by shafaghi on 2013-04-30
NOt bad.

---

### Post by speedy_sz on 2013-08-06
I've got the same problem... Stop your second card from the bios and everything will be alright.. The "extra" temp is coming from your AMD chip.. I have Lenovo G570 with Radeon 6xxx inside as a secondary card. Spending 2-3 days for solving my problem.. So i'd tried to leave active only the APU and voila ;) My temp now is between 40 and 50 degrees Celsius..

---

