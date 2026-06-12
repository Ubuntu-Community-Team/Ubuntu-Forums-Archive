---
title: "Nvidia Nightmare after software update (sep 25th 2012)"
date: 2012-09-26
forum: New to Ubuntu
---

### Post by Fractaline on 2012-09-26
Hello.
I wonder if anyone could please help me.
I am running Ubuntu 12.04 Kernel number ending in 31 and I have an Nvidia GTX 560 card and all was running fine until a Nvidia driver update appeared in the software updater yesterday (sep 25th) after install I lost 3d acceleration and after trying to remove that and rebooting I was then booting into TTY1 (?) console.

I tried sudo apt-get purge nvidia-current
and sudo apt-get purge nvidia*
And then sudo apt-get install nvidia-current-updates-dev

And still after reboot it was still going to terminal

I think I made a mistake by typing sudo apt-get purge nvidiaa*

Basically I ended up having to boot through recovery mode and would only get the smallest imaginable resolution and unless i removed the nvidia drivers I was getting a fatal error no display detected alert.  So I have swapped back to the GS 7900 Nvidia card and I have full spectrum of resolutions but detected screen shows as Laptop and I still have no 3D acceleration.

I know this is not a hardware fault as everything was running brilliantly until the Software update yesterday.

Any ideas anyone? I am completely at a loss as to what has happened.

---

### Post by NikTh on 2012-09-26
Hi , 
follow this commands CAREFULLY  

```
sudo apt-get purge nvidia*
``` 
```
sudo apt-get install ubuntu-desktop
``` 
```
sudo rm /etc/X11/xorg.conf
``` 
```
echo 'nouveau' | sudo tee -a /etc/modules
```
and reboot with this command 
```
sudo reboot
``` 

Thanks

---

### Post by Frogs Hair on 2012-09-26
Hello and Welcome 

Please post some information about your graphics card if the commands above work for you. ```
lspci
```

---

### Post by pqwoerituytrueiwoq on 2012-09-26
i would open synaptic and reinstall your Nvidia driver ([FONT=Courier New]nvidia-current[/FONT] and [FONT=Courier New]nvidia-settings[/FONT])
and purge [FONT=Courier New]nvidia-current-updates-dev[/FONT]
i just installed the updates on my 12.04 install on my gtx 550 ti without issue
```
me@precise-desktop:~$ uname -r
3.2.0-31-generic
me@precise-desktop:~$ nvidia-settings --version

nvidia-settings:  version 304.51  (buildd@pluot)  Tue Sep 25 01:59:08 UTC 2012
  The NVIDIA X Server Settings tool.

  This program is used to configure the NVIDIA Linux graphics driver.
  For more detail, please see the nvidia-settings(1) man page.

  Copyright (C) 2004 - 2010 NVIDIA Corporation.

me@precise-desktop:~$
```i am using the xswat ppa
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by Fractaline on 2012-09-26
Thank you so much that has worked perfectly. I am now back up and running.
Thank you all for your time and help.

---

### Post by NikTh on 2012-09-27
Hi , 

can you please give the result of this command ? 
```
lspci -nnk | grep -iA2 vga
```

Thanks

---

### Post by xavivars on 2012-09-27
> **Fractaline said:**
> Thank you so much that has worked perfectly. I am now back up and running.
Thank you all for your time and help.

Fractaline, I had exactly the same problem, and I don't know how to solve it.

Could you please tell me what worked for you? **NikTh** or **pqwoerituytrueiwoq** answer?

Thank you so much.

---

### Post by Fractaline on 2012-09-27
> **NikTh said:**
> Hi , 

can you please give the result of this command ? 
```
lspci -nnk | grep -iA2 vga
```Thanks

Thanks Nikth.

To be honest even though the system is booting it still doesn't seem right, it still seems slow and gaming on Steam (L4D2) is very slow and the graphics are really stuttery so I suspect there is still something wrong with the drivers as when I try to update the driver to v304 i am still getting dumped to command line after a reboot.

---

### Post by Fractaline on 2012-09-27
> **NikTh said:**
> Hi , 

can you please give the result of this command ? 
```
lspci -nnk | grep -iA2 vga
```Thanks

And [xavivars]("http://ubuntuforums.org/member.php?u=120642") it was Nikths solution that gave me back a GUI. :)

---

### Post by NikTh on 2012-09-27
Hi , 
is not nessesarcy to attach the results . Just copy-paste them in here between the brackets . **[noparse]```
Here
```[/noparse]**. 

These are your results ```
 lspci -nnk | grep -iA2 vga
 01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF114 [GeForce GTX 560] [10de:1201] (rev a1)
     Subsystem: eVga.com. Corp. Device [3842:1463]
     Kernel driver in use: nvidia
     Kernel modules: nvidia_current_updates, nouveau, nvidiafb
```and it seems that something went wrong. 

Open a terminal and give the results of these commands
```
dpkg -l | grep -i nvidia
``````
ls /etc/X11/
``````
grep -R nouveau /etc/modprobe.d/
```Thanks

---

### Post by Fractaline on 2012-09-28
> **NikTh said:**
> Hi , 
is not nessesarcy to attach the results . Just copy-paste them in here between the brackets . **[noparse]```
Here
```[/noparse]**. 

These are your results ```
 lspci -nnk | grep -iA2 vga
 01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF114 [GeForce GTX 560] [10de:1201] (rev a1)
     Subsystem: eVga.com. Corp. Device [3842:1463]
     Kernel driver in use: nvidia
     Kernel modules: nvidia_current_updates, nouveau, nvidiafb
```and it seems that something went wrong. 

Open a terminal and give the results of these commands
```
dpkg -l | grep -i nvidia
``````
ls /etc/X11/
``````
grep -R nouveau /etc/modprobe.d/
```Thanks

Hi

The results are as follows 
dpkg -l | grep -i nvidia
[B]```
rc  nvidia-173                                173.14.35-0ubuntu0.2                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                             1:0.2.44                                     Find obsolete NVIDIA drivers
rc  nvidia-current                            304.51-0ubuntu1~precise~xup1                 NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-updates                    295.49-0ubuntu0.2                            NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                           304.51-0ubuntu1~precise~xup1                 Tool of configuring the NVIDIA graphics driver
ii  nvidia-settings-updates                   295.33-0ubuntu1                              Tool of configuring the NVIDIA graphics driver
```[/B]

ls /etc/X11/
[B]```
app-defaults             xkb                                Xreset.d
cursors                  xorg.conf                          Xresources
default-display-manager  xorg.conf.backup                   Xsession
fonts                    xorg.conf-backup-120925191458      Xsession.d
rgb.txt                  xorg.conf.failsafe                 Xsession.options
X                        xorg.conf.nvidia-xconfig-original  Xwrapper.config
xinit                    Xreset

```[/B]

grep -R nouveau /etc/modprobe.d/
 [B]```
/etc/modprobe.d/nvidia-current_hybrid.conf:blacklist nouveau
/etc/modprobe.d/nvidia-current_hybrid.conf:blacklist lbm-nouveau
/etc/modprobe.d/nvidia-current_hybrid.conf:alias nouveau off
/etc/modprobe.d/nvidia-current_hybrid.conf:alias lbm-nouveau off
/etc/modprobe.d/nvidia-current-updates_hybrid.conf:blacklist nouveau
/etc/modprobe.d/nvidia-current-updates_hybrid.conf:blacklist lbm-nouveau
/etc/modprobe.d/nvidia-current-updates_hybrid.conf:alias nouveau off
/etc/modprobe.d/nvidia-current-updates_hybrid.conf:alias lbm-nouveau off
/etc/modprobe.d/nvidia-graphics-drivers.conf:blacklist nouveau
/etc/modprobe.d/nvidia-graphics-drivers.conf:blacklist lbm-nouveau
/etc/modprobe.d/nvidia-graphics-drivers.conf:alias nouveau off
/etc/modprobe.d/nvidia-graphics-drivers.conf:alias lbm-nouveau off
```[/B]

I hope this makes sense because I am confused by the whole problem.
And thank you again for the help.

---

### Post by NikTh on 2012-09-28
Ok , 

lets purge nvidia , completely. 

```
sudo apt-get remove --purge nvidia-*
``` 
```
sudo rm /etc/X11/xorg.conf*
```
```
sudo rm /etc/modprobe.d/nvidia-*
``` 

Post the results of above commands (2nd and 3rd must return nothing).
and also of this command 
```
cat /etc/modules
``` 

Thanks

---

### Post by Fractaline on 2012-09-28
> **NikTh said:**
> Ok , 

lets purge nvidia , completely. 

```
sudo apt-get remove --purge nvidia-*
``````
sudo rm /etc/X11/xorg.conf*
``````
sudo rm /etc/modprobe.d/nvidia-*
```Post the results of above commands (2nd and 3rd must return nothing).
and also of this command 
```
cat /etc/modules
```Thanks

Ok. :)

```
sudo apt-get remove --purge nvidia-*
[sudo] password for fractal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia-bug-report.log.gz
E: Couldn't find any package by regex 'nvidia-bug-report.log.gz'
``````
fractal@Skynet:~$ sudo rm /etc/X11/xorg.conf*
fractal@Skynet:~$ 

``````
fractal@Skynet:~$ sudo rm /etc/modprobe.d/nvidia-*
fractal@Skynet:~$ 

``````
cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
nouveau

```Is this any help to you?.

---

### Post by NikTh on 2012-09-28
OK. 

reboot your system and again give the results of 

```
dpkg -l | grep -i nvidia
``` 
and 
```
lspci -nnk | grep -iA2 vga
``` 

Thanks

---

### Post by Fractaline on 2012-09-28
> **NikTh said:**
> OK. 

reboot your system and again give the results of 

```
dpkg -l | grep -i nvidia
```and 
```
lspci -nnk | grep -iA2 vga
```Thanks

when it booted my display was scattered bars of colour and I had to use recovery mode.
but the new codes are 
```
dpkg -l | grep -i nvidia
rc  nvidia-173                                173.14.35-0ubuntu0.2                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                             1:0.2.44                                     Find obsolete NVIDIA drivers
rc  nvidia-current                            304.51-0ubuntu1~precise~xup1                 NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-updates                    295.49-0ubuntu0.2                            NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                           304.51-0ubuntu1~precise~xup1                 Tool of configuring the NVIDIA graphics driver
ii  nvidia-settings-updates                   295.33-0ubuntu1                              Tool of configuring the NVIDIA graphics driver
```and

```
lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF114 [GeForce GTX 560] [10de:1201] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:1463]
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current_updates, nouveau, nvidiafb
--
    Subsystem: eVga.com. Corp. Device [3842:1463]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

```there you go. :)

---

### Post by NikTh on 2012-09-28
OK, One more time 

```
sudo apt-get -y remove --purge nvidia-*
sudo apt-get -y remove --purge nvidia-settings*
sudo apt-get -y remove --purge nvidia-current-updates
``````
sudo apt-get intsall ubuntu-desktop
```Reboot and again give the results of bellow commands 
```
dpkg -l | grep -i nvidia
``````
lspci -nnk | grep -iA2 vga
```

---

### Post by Fractaline on 2012-09-28
> **NikTh said:**
> OK, One more time 

```
sudo apt-get -y remove --purge nvidia-*
sudo apt-get -y remove --purge nvidia-settings*
sudo apt-get -y remove --purge nvidia-current-updates
``````
sudo apt-get intsall ubuntu-desktop
```Reboot and again give the results of bellow commands 
```
dpkg -l | grep -i nvidia
``````
lspci -nnk | grep -iA2 vga
```

Ok, here are the results.

```
sudo apt-get -y remove --purge nvidia-* 
[sudo] password for fractal:  
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
E: Unable to locate package nvidia-bug-report.log.gz 
E: Couldn't find any package by regex 'nvidia-bug-report.log.gz
``````
sudo apt-get -y remove --purge nvidia-settings* 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Note, selecting 'nvidia-settings-updates' for regex 'nvidia-settings*' 
Note, selecting 'nvidia-settings' for regex 'nvidia-settings*' 
The following packages will be REMOVED 
  nvidia-settings* nvidia-settings-updates* 
0 upgraded, 0 newly installed, 2 to remove and 13 not upgraded. 
After this operation, 4,596 kB disk space will be freed. 
(Reading database ... 421316 files and directories currently installed.) 
Removing nvidia-settings ... 
Purging configuration files for nvidia-settings ... 
Removing nvidia-settings-updates ... 
Purging configuration files for nvidia-settings-updates ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place
``````
sudo apt-get install ubuntu-desktop 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
ubuntu-desktop is already the newest version. 
The following package was automatically installed and is no longer required: 
  screen-resolution-extra 
Use 'apt-get autoremove' to remove them. 
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded. 
fractal@Skynet:~$ sudo apt-get autoremove 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
The following packages will be REMOVED 
  screen-resolution-extra 
0 upgraded, 0 newly installed, 1 to remove and 13 not upgraded. 
After this operation, 127 kB disk space will be freed. 
Do you want to continue [Y/n]? y 
(Reading database ... 421225 files and directories currently installed.) 
Removing screen-resolution-extra ...
```
```
dpkg -l | grep -i nvidia
rc  nvidia-173                                173.14.35-0ubuntu0.2                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                             1:0.2.44                                     Find obsolete NVIDIA drivers
rc  nvidia-current                            304.51-0ubuntu1~precise~xup1                 NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-updates                    295.49-0ubuntu0.2                            NVIDIA binary Xorg driver, kernel module and VDPAU library

```

```
lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF114 [GeForce GTX 560] [10de:1201] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:1463]
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current_updates, nouveau, nvidiafb
--
    Subsystem: eVga.com. Corp. Device [3842:1463]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

```

---

### Post by Fractaline on 2012-09-28
> **Fractaline said:**
> Ok, here are the results.

```
sudo apt-get -y remove --purge nvidia-* 
[sudo] password for fractal:  
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
E: Unable to locate package nvidia-bug-report.log.gz 
E: Couldn't find any package by regex 'nvidia-bug-report.log.gz
``````
sudo apt-get -y remove --purge nvidia-settings* 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Note, selecting 'nvidia-settings-updates' for regex 'nvidia-settings*' 
Note, selecting 'nvidia-settings' for regex 'nvidia-settings*' 
The following packages will be REMOVED 
  nvidia-settings* nvidia-settings-updates* 
0 upgraded, 0 newly installed, 2 to remove and 13 not upgraded. 
After this operation, 4,596 kB disk space will be freed. 
(Reading database ... 421316 files and directories currently installed.) 
Removing nvidia-settings ... 
Purging configuration files for nvidia-settings ... 
Removing nvidia-settings-updates ... 
Purging configuration files for nvidia-settings-updates ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place
``````
sudo apt-get install ubuntu-desktop 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
ubuntu-desktop is already the newest version. 
The following package was automatically installed and is no longer required: 
  screen-resolution-extra 
Use 'apt-get autoremove' to remove them. 
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded. 
fractal@Skynet:~$ sudo apt-get autoremove 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
The following packages will be REMOVED 
  screen-resolution-extra 
0 upgraded, 0 newly installed, 1 to remove and 13 not upgraded. 
After this operation, 127 kB disk space will be freed. 
Do you want to continue [Y/n]? y 
(Reading database ... 421225 files and directories currently installed.) 
Removing screen-resolution-extra ...
``````
dpkg -l | grep -i nvidia
rc  nvidia-173                                173.14.35-0ubuntu0.2                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                             1:0.2.44                                     Find obsolete NVIDIA drivers
rc  nvidia-current                            304.51-0ubuntu1~precise~xup1                 NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-updates                    295.49-0ubuntu0.2                            NVIDIA binary Xorg driver, kernel module and VDPAU library

``````
lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF114 [GeForce GTX 560] [10de:1201] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:1463]
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current_updates, nouveau, nvidiafb
--
    Subsystem: eVga.com. Corp. Device [3842:1463]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

```


I missed out one stage and re-did it, now I have limited resolution and I cannot access the terminal even with ctrl+T.

---

### Post by Fractaline on 2012-09-28
> **Fractaline said:**
> I missed out one stage and re-did it, now I have limited resolution and I cannot access the terminal even with ctrl+T.
it's ok I am in now.

```
dpkg -l | grep -i nvidia
rc  nvidia-173                                173.14.35-0ubuntu0.2                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                             1:0.2.44                                     Find obsolete NVIDIA drivers
rc  nvidia-current                            304.51-0ubuntu1~precise~xup1                 NVIDIA binary Xorg driver, kernel module and VDPAU library

```

```
lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF114 [GeForce GTX 560] [10de:1201] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:1463]
    Kernel modules: nouveau, nvidiafb
01:00.1 Audio device [0403]: NVIDIA Corporation GF110 High Definition Audio Controller [10de:0e0c] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:1463]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

```

Is this looking any better?

---

### Post by NikTh on 2012-09-29
Yes , this is looking better , but no as it must be. 

You have not the nouveau driver loaded. Now you must have a little problem with graphics. Don't you ?

Now you cleared up the nvidia , cuz you had 2-3 nvidia drivers installed at same time , lets install the latest nvidia-current driver and see . 

First of all , open /etc/modules and remove nouveau . 

```
gksudo gedit /etc/modules
``` and remove nouveau . Save the file. 

Then apply bellow commands in terminal 

```
sudo apt-get update 
sudo apt-get clean all 
sudo apt-get autoclean 
sudo apt-get autoremove 
sudo dpkg --clear-avail
```Then again ```
sudo apt-get update 
sudo apt-get dist-upgrade
``` to upgrade all your packages to latest version.

Install Nvidia current driver. 304.51 from X-Swat PPA , I can see you have added this PPA already. 
```
sudo apt-get install nvidia-current
sudo nvidia-xconfig
```Reboot you PC and let me know if your graphics are OK.

---

### Post by Fractaline on 2012-09-29
[QUOTE=NikTh;12267658]Yes , this is looking better , but no as it must be. 

You have not the nouveau driver loaded. Now you must have a little problem with graphics. Don't you ?

Now you cleared up the nvidia , cuz you had 2-3 nvidia drivers installed at same time , lets install the latest nvidia-current driver and see . 

First of all , open /etc/modules and remove nouveau . 

```
gksudo gedit /etc/modules
``` and remove nouveau . Save the file. 

Then apply bellow commands in terminal 

```
sudo apt-get update 

NikTh, it seems 'better' but it still isn't behaving 100%, I am still getting extreme lag in Steam games and it seems Unity desktop is a bit broken as auto-hide on the unity panel is not working. Is this a bug in the newest driver?

here is the code from the processes I ran.

[code]fractal@Skynet:~$ gksudo gedit /etc/modules 
fractal@Skynet:~$ gksudo gedit /etc/modules 
fractal@Skynet:~$ sudo apt-get update 
Ign http://extras.ubuntu.com precise InRelease 
Ign http://archive.canonical.com precise InRelease                              
Ign http://gb.archive.ubuntu.com precise InRelease                              
Ign http://archive.canonical.com precise InRelease                              
Ign http://gb.archive.ubuntu.com precise-updates InRelease                      
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://gb.archive.ubuntu.com precise-backports InRelease                    
Hit http://deb.playonlinux.com precise InRelease                                
Ign http://security.ubuntu.com precise-security InRelease                       
Ign http://dl.google.com stable InRelease                                       
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]                       
Hit http://archive.canonical.com precise Release.gpg                            
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Hit http://gb.archive.ubuntu.com precise Release.gpg                            
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Get:2 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]          
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]           
Hit http://packages.medibuntu.org precise InRelease                             
Hit http://deb.playonlinux.com precise/main i386 Packages                       
Hit http://dl.google.com stable Release.gpg                                     
Hit http://extras.ubuntu.com precise Release                                    
Ign http://ppa.launchpad.net precise InRelease                                  
Hit http://archive.canonical.com precise Release.gpg                            
Hit http://gb.archive.ubuntu.com precise-backports Release.gpg                  
Get:4 http://security.ubuntu.com precise-security Release [49.6 kB]             
Ign http://ppa.launchpad.net precise InRelease                                  
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://dl.google.com stable Release                                         
Ign http://deb.playonlinux.com precise/main TranslationIndex                    
Hit http://archive.canonical.com precise Release                                
Hit http://extras.ubuntu.com precise/main Sources                               
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://gb.archive.ubuntu.com precise Release                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://archive.canonical.com precise Release                                
Hit http://extras.ubuntu.com precise/main i386 Packages                         
Ign http://extras.ubuntu.com precise/main TranslationIndex                      
Hit http://dl.google.com stable/main i386 Packages                              
Hit http://packages.medibuntu.org precise/free i386 Packages                    
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://archive.canonical.com precise/partner Sources                        
Hit http://archive.canonical.com precise/partner i386 Packages                  
Hit http://ppa.launchpad.net precise Release.gpg                                
Get:5 http://gb.archive.ubuntu.com precise-updates Release [49.6 kB]            
Ign http://archive.canonical.com precise/partner TranslationIndex               
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Ign http://dl.google.com stable/main TranslationIndex                           
Hit http://archive.canonical.com precise/partner i386 Packages                  
Ign http://archive.canonical.com precise/partner TranslationIndex               
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://packages.medibuntu.org precise/non-free i386 Packages                
Hit http://ppa.launchpad.net precise Release                                    
Get:6 http://security.ubuntu.com precise-security/main Sources [46.7 kB]        
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Hit http://gb.archive.ubuntu.com precise-backports Release                      
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://packages.medibuntu.org precise/free TranslationIndex                 
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://gb.archive.ubuntu.com precise/main Sources                           
Hit http://gb.archive.ubuntu.com precise/restricted Sources                     
Hit http://gb.archive.ubuntu.com precise/universe Sources                       
Hit http://gb.archive.ubuntu.com precise/multiverse Sources                     
Hit http://gb.archive.ubuntu.com precise/main i386 Packages                     
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages               
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages                 
Get:7 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]  
Get:8 http://security.ubuntu.com precise-security/universe Sources [13.5 kB]    
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages               
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex                  
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex            
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex            
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex              
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Get:9 http://gb.archive.ubuntu.com precise-updates/main Sources [171 kB]        
Get:10 http://security.ubuntu.com precise-security/multiverse Sources [1,386 B] 
Get:11 http://security.ubuntu.com precise-security/main i386 Packages [174 kB]  
Ign http://extras.ubuntu.com precise/main Translation-en_GB                     
Ign http://packages.medibuntu.org precise/non-free TranslationIndex             
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://extras.ubuntu.com precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Get:12 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B] 
Get:13 http://security.ubuntu.com precise-security/universe i386 Packages [46.8 kB] 
Ign http://deb.playonlinux.com precise/main Translation-en_GB                   
Ign http://archive.canonical.com precise/partner Translation-en_GB              
Get:14 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,369 B] 
Hit http://security.ubuntu.com precise-security/main TranslationIndex           
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex     
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex     
Hit http://security.ubuntu.com precise-security/universe TranslationIndex       
Ign http://archive.canonical.com precise/partner Translation-en                 
Ign http://archive.canonical.com precise/partner Translation-en_GB              
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Ign http://deb.playonlinux.com precise/main Translation-en                      
Ign http://dl.google.com stable/main Translation-en_GB                          
Get:15 http://gb.archive.ubuntu.com precise-updates/restricted Sources [3,285 B] 
Get:16 http://gb.archive.ubuntu.com precise-updates/universe Sources [55.9 kB]  
Ign http://archive.canonical.com precise/partner Translation-en                 
Ign http://dl.google.com stable/main Translation-en                             
Get:17 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B] 
Get:18 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [400 kB] 
Hit http://security.ubuntu.com precise-security/main Translation-en             
Hit http://security.ubuntu.com precise-security/multiverse Translation-en       
Hit http://security.ubuntu.com precise-security/restricted Translation-en       
Hit http://security.ubuntu.com precise-security/universe Translation-en         
Ign http://archive.getdeb.net precise-getdeb InRelease                          
Get:19 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [6,732 B] 
Get:20 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [140 kB] 
Get:21 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,673 B] 
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex          
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex    
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex    
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex      
Hit http://gb.archive.ubuntu.com precise-backports/main Sources                 
Hit http://gb.archive.ubuntu.com precise-backports/restricted Sources           
Hit http://gb.archive.ubuntu.com precise-backports/universe Sources             
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Sources           
Hit http://gb.archive.ubuntu.com precise-backports/main i386 Packages           
Hit http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages     
Hit http://gb.archive.ubuntu.com precise-backports/universe i386 Packages       
Hit http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages     
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex        
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex  
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex  
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex    
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB                 
Hit http://gb.archive.ubuntu.com precise/main Translation-en                    
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB           
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en              
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB           
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en              
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB             
Hit http://gb.archive.ubuntu.com precise/universe Translation-en                
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB         
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en            
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB   
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en      
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB   
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en      
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB     
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en        
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en          
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en    
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en    
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en      
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Hit http://archive.getdeb.net precise-getdeb Release.gpg 
Ign http://packages.medibuntu.org precise/free Translation-en_GB 
Ign http://packages.medibuntu.org precise/free Translation-en 
Ign http://packages.medibuntu.org precise/non-free Translation-en_GB 
Ign http://packages.medibuntu.org precise/non-free Translation-en 
Hit http://archive.getdeb.net precise-getdeb Release        
Hit http://archive.getdeb.net precise-getdeb/games i386 Packages 
Ign http://archive.getdeb.net precise-getdeb/games TranslationIndex 
Ign http://archive.getdeb.net precise-getdeb/games Translation-en_GB            
Ign http://archive.getdeb.net precise-getdeb/games Translation-en               
Fetched 1,181 kB in 10s (112 kB/s)                                              
Reading package lists... Done 
fractal@Skynet:~$ sudo apt-get clean all 
fractal@Skynet:~$ sudo apt-get autoclean 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
fractal@Skynet:~$ sudo apt-get autoremove 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
0 upgraded, 0 newly installed, 0 to remove and 27 not upgraded. 
fractal@Skynet:~$ sudo dpkg --clear-avail 
fractal@Skynet:~$ sudo apt-get update 
Ign http://extras.ubuntu.com precise InRelease 
Ign http://archive.canonical.com precise InRelease                              
Ign http://archive.canonical.com precise InRelease                              
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://gb.archive.ubuntu.com precise InRelease                              
Ign http://gb.archive.ubuntu.com precise-updates InRelease                      
Ign http://gb.archive.ubuntu.com precise-backports InRelease                    
Ign http://dl.google.com stable InRelease                                       
Hit http://deb.playonlinux.com precise InRelease                                
Hit http://extras.ubuntu.com precise Release.gpg                                
Hit http://archive.canonical.com precise Release.gpg                            
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Ign http://ppa.launchpad.net precise InRelease                                  
Hit http://gb.archive.ubuntu.com precise Release.gpg                            
Ign http://security.ubuntu.com precise-security InRelease                       
Hit http://extras.ubuntu.com precise Release                                    
Hit http://archive.canonical.com precise Release.gpg                            
Hit http://gb.archive.ubuntu.com precise-updates Release.gpg                    
Hit http://dl.google.com stable Release.gpg                                     
Ign http://ppa.launchpad.net precise InRelease                                  
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://security.ubuntu.com precise-security Release.gpg                     
Hit http://gb.archive.ubuntu.com precise-backports Release.gpg                  
Hit http://archive.canonical.com precise Release                                
Hit http://deb.playonlinux.com precise/main i386 Packages                       
Hit http://extras.ubuntu.com precise/main Sources                               
Hit http://packages.medibuntu.org precise InRelease                             
Hit http://dl.google.com stable Release                                         
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://gb.archive.ubuntu.com precise Release                                
Hit http://security.ubuntu.com precise-security Release                         
Hit http://extras.ubuntu.com precise/main i386 Packages                         
Ign http://extras.ubuntu.com precise/main TranslationIndex                      
Hit http://archive.canonical.com precise Release                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://gb.archive.ubuntu.com precise-updates Release                        
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Hit http://ppa.launchpad.net precise Release.gpg                                
Ign http://deb.playonlinux.com precise/main TranslationIndex                    
Hit http://archive.canonical.com precise/partner Sources                        
Hit http://archive.canonical.com precise/partner i386 Packages                  
Ign http://archive.canonical.com precise/partner TranslationIndex               
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://dl.google.com stable/main i386 Packages                              
Hit http://gb.archive.ubuntu.com precise-backports Release                      
Hit http://security.ubuntu.com precise-security/main Sources                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://gb.archive.ubuntu.com precise/main Sources                           
Hit http://gb.archive.ubuntu.com precise/restricted Sources                     
Hit http://gb.archive.ubuntu.com precise/universe Sources                       
Hit http://gb.archive.ubuntu.com precise/multiverse Sources                     
Hit http://gb.archive.ubuntu.com precise/main i386 Packages                     
Hit http://packages.medibuntu.org precise/free i386 Packages                    
Ign http://dl.google.com stable/main TranslationIndex                           
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages               
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages                 
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages               
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex                  
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://ppa.launchpad.net precise Release                                    
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex            
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
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex            
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex              
Hit http://gb.archive.ubuntu.com precise-updates/main Sources                   
Hit http://gb.archive.ubuntu.com precise-updates/restricted Sources             
Hit http://gb.archive.ubuntu.com precise-updates/universe Sources               
Hit http://archive.canonical.com precise/partner i386 Packages                  
Ign http://archive.canonical.com precise/partner TranslationIndex               
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://security.ubuntu.com precise-security/universe TranslationIndex       
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Sources             
Hit http://gb.archive.ubuntu.com precise-updates/main i386 Packages             
Hit http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages       
Hit http://gb.archive.ubuntu.com precise-updates/universe i386 Packages         
Hit http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages       
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Hit http://security.ubuntu.com precise-security/main Translation-en             
Hit http://security.ubuntu.com precise-security/multiverse Translation-en       
Hit http://packages.medibuntu.org precise/non-free i386 Packages                
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex          
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex    
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex    
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex      
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB                 
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://security.ubuntu.com precise-security/restricted Translation-en       
Hit http://gb.archive.ubuntu.com precise/main Translation-en                    
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB           
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en              
Hit http://gb.archive.ubuntu.com precise-backports/main Sources                 
Hit http://gb.archive.ubuntu.com precise-backports/restricted Sources           
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://security.ubuntu.com precise-security/universe Translation-en         
Hit http://gb.archive.ubuntu.com precise-backports/universe Sources             
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Sources           
Hit http://gb.archive.ubuntu.com precise-backports/main i386 Packages           
Hit http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages     
Hit http://gb.archive.ubuntu.com precise-backports/universe i386 Packages       
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages     
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex        
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex  
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex  
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex    
Ign http://extras.ubuntu.com precise/main Translation-en_GB                     
Ign http://packages.medibuntu.org precise/free TranslationIndex                 
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB           
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en              
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB             
Hit http://gb.archive.ubuntu.com precise/universe Translation-en                
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB         
Ign http://extras.ubuntu.com precise/main Translation-en                        
Ign http://archive.canonical.com precise/partner Translation-en_GB              
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en            
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB   
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en      
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB   
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en      
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB     
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en        
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en          
Ign http://packages.medibuntu.org precise/non-free TranslationIndex             
Ign http://archive.canonical.com precise/partner Translation-en                 
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Hit http://ppa.launchpad.net precise/main Sources                               
Hit http://ppa.launchpad.net precise/main i386 Packages                         
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en    
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en    
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en      
Ign http://ppa.launchpad.net precise/main TranslationIndex                      
Ign http://archive.canonical.com precise/partner Translation-en_GB              
Ign http://dl.google.com stable/main Translation-en_GB                          
Ign http://deb.playonlinux.com precise/main Translation-en_GB                   
Ign http://archive.canonical.com precise/partner Translation-en                 
Ign http://dl.google.com stable/main Translation-en                             
Ign http://deb.playonlinux.com precise/main Translation-en                      
Ign http://archive.getdeb.net precise-getdeb InRelease                          
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en              
Ign http://ppa.launchpad.net precise/main Translation-en_GB           
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                     
Ign http://ppa.launchpad.net precise/main Translation-en                        
Hit http://archive.getdeb.net precise-getdeb Release.gpg                        
Ign http://packages.medibuntu.org precise/free Translation-en_GB                
Ign http://packages.medibuntu.org precise/free Translation-en                   
Ign http://packages.medibuntu.org precise/non-free Translation-en_GB            
Ign http://packages.medibuntu.org precise/non-free Translation-en               
Hit http://archive.getdeb.net precise-getdeb Release                            
Hit http://archive.getdeb.net precise-getdeb/games i386 Packages 
Ign http://archive.getdeb.net precise-getdeb/games TranslationIndex 
Ign http://archive.getdeb.net precise-getdeb/games Translation-en_GB 
Ign http://archive.getdeb.net precise-getdeb/games Translation-en 
Reading package lists... Done                              
fractal@Skynet:~$ sudo apt-get dist-upgrade 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Calculating upgrade... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
fractal@Skynet:~$ sudo apt-get install nvidia-current 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
The following extra packages will be installed: 
  dkms nvidia-settings screen-resolution-extra 
The following NEW packages will be installed 
  dkms nvidia-current nvidia-settings screen-resolution-extra 
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded. 
Need to get 39.5 MB of archives. 
After this operation, 111 MB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Get:1 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main nvidia-current i386 304.51-0ubuntu1~precise~xup1 [38.1 MB] 
Get:2 http://gb.archive.ubuntu.com/ubuntu/ precise/main dkms all 2.2.0.3-1ubuntu3 [73.1 kB] 
Get:3 http://gb.archive.ubuntu.com/ubuntu/ precise/main screen-resolution-extra all 0.14ubuntu2 [12.8 kB] 
Get:4 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main nvidia-settings i386 304.51-0ubuntu1~precise~xup1 [1,301 kB] 
Fetched 39.5 MB in 9s (4,055 kB/s)                                              
Selecting previously unselected package dkms. 
(Reading database ... 421015 files and directories currently installed.) 
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ... 
Selecting previously unselected package nvidia-current. 
Unpacking nvidia-current (from .../nvidia-current_304.51-0ubuntu1~precise~xup1_i386.deb) ... 
Selecting previously unselected package screen-resolution-extra. 
Unpacking screen-resolution-extra (from .../screen-resolution-extra_0.14ubuntu2_all.deb) ... 
Selecting previously unselected package nvidia-settings. 
Unpacking nvidia-settings (from .../nvidia-settings_304.51-0ubuntu1~precise~xup1_i386.deb) ... 
Processing triggers for man-db ... 
Setting up dkms (2.2.0.3-1ubuntu3) ... 
Setting up nvidia-current (304.51-0ubuntu1~precise~xup1) ... 
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode. 
update-alternatives: warning: skip creation of /usr/lib32/libOpenCL.so because associated file /usr/lib32/nvidia-current/libOpenCL.so (of link group i386-linux-gnu_gl_conf) doesn't exist. 
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group i386-linux-gnu_gl_conf) doesn't exist. 
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group i386-linux-gnu_gl_conf) doesn't exist. 
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode. 
update-initramfs: deferring update (trigger activated) 
INFO:Enable nvidia-current 
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here 
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude 
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad 
DEBUG:Processing quirk Latitude E6530 
DEBUG:Failure to match Foxconn with Dell Inc. 
DEBUG:Quirk doesn't match 
DEBUG:Processing quirk ThinkPad T420s 
DEBUG:Failure to match Foxconn with LENOVO 
DEBUG:Quirk doesn't match 
Loading new nvidia-current-304.51 DKMS files... 
Building only for 3.2.0-31-generic-pae 
Building for architecture i686 
Building initial module for 3.2.0-31-generic-pae 
Done. 
 
nvidia: 
Running module version sanity check. 
 - Original module 
   - No original module exists within this kernel 
 - Installation 
   - Installing to /lib/modules/3.2.0-31-generic-pae/updates/dkms/ 
 
depmod...... 
 
DKMS: install completed. 
Setting up screen-resolution-extra (0.14ubuntu2) ... 
Setting up nvidia-settings (304.51-0ubuntu1~precise~xup1) ... 
update-alternatives: warning: alternative /usr/lib/nvidia-settings-updates/ld.so.conf (part of link group nvidia_settings_conf) doesn't exist. Removing from list of alternatives. 
update-alternatives: warning: /etc/alternatives/nvidia_settings_conf is dangling, it will be updated with best choice. 
update-alternatives: using /usr/lib/nvidia-settings/ld.so.conf to provide /etc/ld.so.conf.d/nvidia_settings.conf (nvidia_settings_conf) in auto mode. 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for initramfs-tools ... 
update-initramfs: Generating /boot/initrd.img-3.2.0-31-generic-pae 
fractal@Skynet:~$ sudo nvidia-xconfig 
 
WARNING: Unable to locate/open X configuration file. 
 
New X configuration file written to '/etc/X11/xorg.conf' 
 
```

---

### Post by Fractaline on 2012-09-29
```
dpkg -l | grep -i nvidia
rc  nvidia-173                                173.14.35-0ubuntu0.2                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                             1:0.2.44                                     Find obsolete NVIDIA drivers
ii  nvidia-current                            304.51-0ubuntu1~precise~xup1                 NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                           304.51-0ubuntu1~precise~xup1                 Tool of configuring the NVIDIA graphics driver

```

Should nvidia-173 still be showing in the list?

---

### Post by NikTh on 2012-09-29
If your graphics are ok , then you can ignore the list. 

[rc] means 

r = mark for removal 
c= configuration files are still present. 
but I assume config files for 173 are similar to 304.  

[ii] means , the package successfully installed.


Are your graphics OK ?

---

### Post by Fractaline on 2012-09-29
> **NikTh said:**
> If your graphics are ok , then you can ignore the list. 

[rc] means 

r = mark for removal 
c= configuration files are still present. 
but I assume config files for 173 are similar to 304.  

[ii] means , the package successfully installed.


Are your graphics OK ?

Oh I see.

Yes they seem ok now, Thank you so very much for all your help. I really feared having to reinstall the whole system.

---

