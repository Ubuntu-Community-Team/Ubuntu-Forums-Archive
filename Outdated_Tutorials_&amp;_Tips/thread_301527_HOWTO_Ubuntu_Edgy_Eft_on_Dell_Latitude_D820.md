---
title: "HOWTO: Ubuntu Edgy Eft on Dell Latitude D820"
date: 2006-11-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Jan Hrbacek on 2006-11-17
(This Howto is being adapted and updated as new solutions, ideas, and experience occur...)

**Ubuntu 6.10 Edgy Eft on Dell Latitude D820**

This text describes hardware related issues during the installation of Ubuntu 6.10 Edgy Eft on the laptop Dell Latitude D820.  


**Configuration**

Intel Duo Core T2500 (2.00 GHz)
nVidia Quatro NVS 120M 256 MB 
1 GB DDR2 667 MHz
100 GB SATA HD
15.4" WSXGA+ 1680x1050
Dell Wireless 1490 Minicard
Internal Bluetooth Card
DVD+RW


**Installation**

I downloaded CD image ubuntu-6.10-desktop-i386.iso. No problems with the installation whatsoever. I have chosen custom layout for hard drive partitioning. This is what my set of partitions looks like:

```
/dev/sda1	ext3		/		20 GB
/dev/sda2	swap				2 GB
/dev/sda3	extended
 /dev/sda5	ext3		/home		50 GB
 /dev/sda6	vfat		/home/work	18 GB
/dev/sda4	ntfs		winXP		5 GB

```


**First booting**

The entire system boots in 21 seconds!
Monitor is set to the correct resolution.
Sound is supported.
Hotkeys for changing sound volume work properly.

! Wireless card is not operating. 
! It is not possible to adjust sensitivity of the touchpad.
! During the fade out to the screensaver, sharp flashing of the monitor. After few days of using the system, this occassionally messes up colors. Restart solves this. 

CD/DVD drive works out of the box. Playing CDs and DVDs is fluent (after installing appropriate codecs). Recording of CDs and DVDs has not been tested yet.


**WiFi**

This is the trickiest part of Ubuntu installation. 

It is not problem to install the proper driver and make the wifi to work. But I had to encounter two other issues, one of them not being solved up to now...


**Installing Dell Wireless 1490 minicard driver**

This card doesn't have a linux driver. Windows driver with ndiswrapper has to be used instead.

Download approriate Windows driver from [www.dell.com](www.dell.com). As a customer with 3-year support, I have only entered my service tag number that is linked to my laptop configuration and Dell webpage offered me a list of drivers available for my laptop. Find the one related to the wifi.

There will be a list of different versions of the driver, I have downloaded the latest: R115321.EXE from 06/23/2006. This file needs to be run on a win computer. It extracts files into chosen directory. In the directory you will find "driver" subdirectory. Copy the files inside this directory to a certain directory in your linux box (e.g. /home/user/drivers).

The native driver bcm43xx that was associated with the wifi during Ubuntu installation doesn't work and it needs to be blacklisted so it is not loaded during booting:

```
sudo nano /etc/modprobe.d/blacklist
sudo blacklist bcm43xx
```

Further, ndiswrapper packages need to installed from Ubuntu CD (using Synoptics Package manager):

ndiswrapper (1.18-1ubuntu2)
ndiswrapper-utils-1.8 (1.18-1ubuntu2)

Driver implementation:
```
sudo ndiswrapper -i ~/drivers/drivername.inf
```

To check that the driver is installed properly:
```
ndiswrapper -l 
```

```
sudo depmod -a
sudo modprobe ndiswrapper
```

Check for possible errors:
```
tail /var/log/messages
```

Check functionality:
```
sudo ifdown eth1
sudo ifup eth1
```

Auto load at startup:
```
sudo ndiswrapper -m
```

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)


**Configuring the wifi**

I have encountered a lot of problems trying to configure the wifi to connect to WPA access point with the hidden SSID. Thanks to wieman01 from ubuntuforums.com, I found a recipe how to make wifi connect to the access point without the neccessity of /etc/wpa_supplicant.conf, which didn't work for me.

Install wpa_supplicant 0.5.4-5 from Ubuntu CD.

This is how I had to configure /etc/network/interfaces (wpa_supplicant.conf stays empty, unconfigured):

```
auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid Carlo
wpa-ap-scan 2
wpa-proto TKIP
wpa-pairwise TKIP
wpa-key-mgmt WPA-PSK
wpa-psk my_very_secret_pass_in_hex_form
```

Related links:
[http://www.ubuntuforums.org/showthread.php?t=290414](http://www.ubuntuforums.org/showthread.php?t=290414)
[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)


**Nvidia vs. Dell Wireless conflict**

It has occured that nvidia driver doesn't get along with Broadcom family of wireless cards. Unfortunatelly, Dell Wireless 1490 belongs into this group too. 

After some time wireless stops operate. Only way out of it is to restart the laptop. Dmesg reveals following lines:

[```
17179712.860000] irq 177: nobody cared (try booting with the "irqpoll" option)
[17179712.860000]  <c01499a4> __report_bad_irq+0x24/0x80  <c0149a9d> note_interrupt+0x9d/0x270
[17179712.860000]  <f8c0e002> ndis_isr+0x52/0xc0 [ndiswrapper]  <c0149448> __do_IRQ+0xf8/0x110
[17179712.860000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
[17179712.860000]  <c0149307> handle_IRQ_event+0x17/0x60  <c01493ed> __do_IRQ+0x9d/0x110
[17179712.860000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
[17179712.860000]  <c0149307> handle_IRQ_event+0x17/0x60  <c01493ed> __do_IRQ+0x9d/0x110
[17179712.860000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
[17179712.860000]  <c02daad9> _spin_unlock_irqrestore+0x9/0x10  <c025ee63> i8042_interrupt+0x1d3/0x220
[17179712.860000]  <c010408a> common_interrupt+0x1a/0x20  <c0149323> handle_IRQ_event+0x33/0x60
[17179712.860000]  <c01493ed> __do_IRQ+0x9d/0x110  <c0105c89> do_IRQ+0x19/0x30
[17179712.860000]  <c010408a> common_interrupt+0x1a/0x20  <c012782f> __do_softirq+0x5f/0xe0
[17179712.860000]  <c01278e5> do_softirq+0x35/0x40  <c0105c8e> do_IRQ+0x1e/0x30
[17179712.860000]  <c010408a> common_interrupt+0x1a/0x20 
[17179712.860000] handlers:
[17179712.860000] [<f8c0dfb0>] (ndis_isr+0x0/0xc0 [ndiswrapper])
[17179712.860000] Disabling IRQ #177
```

This issue is a confirmed bug:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57355](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57355)

Let's hope it is going to be solved soon. At this moment, an user has only two options, none of them nice. The conflict is avoided if the nvidia driver is replaced with the original nv driver installed during Ubuntu instalation. However, as you can read further in this text, the performance of nv driver is really bad. Therefore I decided to keep the buggy configuration and if I need the wireless after some time I have to restart my linux box... :-(


**Nvidia drivers**

Flashing of the screen and very poor graphic performance (for instance when enabling some screensavers) is solved by installing nvidia drives. Full description can be found here:

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

Method 1 of the document works with D820:

```
sudo apt-get install linux-generic
sudo apt-get install nvidia-glx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-xconfig
```

This installs the latest kernel (in my case the latest kernel was already present), installs nvidia driver, backs-up xorg.conf and implements the driver into the xorg.conf. As a next step, a file including setting is created:

```
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```

This goes into the NVIDIA-Settings.desktop file:

```
[Desktop Entry] 
Name=NVIDIA Settings 
Comment=NVIDIA X Server Settings 
Exec=nvidia-settings 
Icon= 
StartupNotify=true 
Terminal=false 
Type=Application 
Categories=Application;System;
```

As a final step log out and press CTRL+ALT+BACKSPACE to restart the xserver. At this point, problems with graphic performance are solved. A little detail bothered me after the driver installation: at the login screen, font size has enlarged and was too big. Here is the solution:

[http://www.ubuntuforums.org/showthread.php?t=158974&highlight=font+nvidia](http://www.ubuntuforums.org/showthread.php?t=158974&highlight=font+nvidia)

Go to System -> Administration -> Login Window. Select the "Security" tab and choose "Configure X-Server...". In the command box add "-dpi <value>". I have set dpi to 80 and everything is fine now.


**Touchpad**

Application System -> Preferences -> Mouse was only changing properties of the pointer in the middle of a keyboard, but the touchpad properties remained unchanged.

Using Synaptics Package Manager, I have searched for all touchpad related packages and installed xserver-xorg-input-synaptics package. Installation of this package uninstalls all other packages related to touchpad.

The following line neeeds to be added in /etc/X11/xorg.conf
```
Option "SHMConfig" "1"
```

Now you can run
```
synclient -l
```

This lists all parameters of the touchpad and their current setting. I have tried to alter an acceleration factor several times. In the end I was happy with 

```
synclient AccelFactor=0.060
```

and added this option to xorg.conf
```
sudo nano /etc/X11/xorg.conf
Option         "AccelFactor" "0.06"
```


**Comparison with Fedora Core 5**

To make a long story short, after few weeks of using Ubuntu, I like it more than FC5, which was my first linux box.

Compared to FC5, Ubuntu is minimalistic and more user frienly. For instalation, only one instead of five CDs is needed. The Ubuntu CD serves also as LiveCD. Time required for instalation is slightly shorter in case of Ubuntu. 

Booting time is significantly shorter in Ubuntu. After the instalation, there are no icons present on the desktop. Everything is very simple and synoptic. Graphics is overall much nicer and cleaner in Ubuntu, however, FC5 is an older distribution (FC6 is released now).

After instalation of FC5, at the beginning I could only run the computer with 800x600 resolution. Nvidia drivers had to be implemented manually. Ubuntu starts with the proper resolution and at the first glance graphics seems to be OK. After some time I have discovered issues with flashing of the screen and color changes. Native driver in not optimal and I had to install the nvidia driver.

FC5 had some problems with mixing sounds. All system sounds in Gnome had to be disabled. I wasn't able to solve the problem. Also there was a problem switching sound output between internal speakers and external devices connected throught jack. Sometimes, sound wasn't redirected, so after pluging external speakers, sound was still played using the build-in speakers. In Ubuntu, sound works out of the box and I have not experienced any of the problems.

Wifi doesn't work after the instalation in either of the two distributions. I didn't experience the bug mentioned above in FC5. However, with FC5 I was using the older kernel.

I like the no-root concept of Ubuntu and after working with FC5 for some time I understand it's advantages (see LINK)

Plugging of peripheals works smoothly in Ubuntu. I have a USB memory stick and two external hard drives - 30 GB UltraATA and 40 GB SATA. They are all automatically mounted without any difficulties. In FC5 I had a problem with automated mounting of the SATA external drive.

My digital camera Canon PowerShot A70 works plug'n'play in Ubuntu. I didn't find an easy way how to use it with FC5.

I think Synaptic Package Manager gives user more comfort than pirut. 

I will not compare software applications separately. Nowadays, there is so much variety and it is so much user dependent...

---

### Post by Jere Retzer on 2006-12-01
Please tell us more about how you did the partitioning. I just tried this yesterday and had problems.

Also, be advised that I have run into a severe bug, #43745 reported on [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43745](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43745) that has corrupted the realtime clock. The clock seems to race when running bios, but will synch once ubuntu is up with a network connection. I'm very interested to hear if anyone has a permanent fix for this as the workarounds mentioned (removing the cmos battery to dump the bios) seems temporary at best. Thanks

---

### Post by gen2ux on 2006-12-05
Is there any way you can update us on the graphical performance?  I'm very interested in this laptop however I'd like to know how OpenGL screensavers/XGL/AIGLX/whatever_else works with the Quadro NVS cards.  I'm not a gamer but I do like some eye candy.  Any input would be appreciated.

Thanks

---

### Post by Jan Hrbacek on 2006-12-05
nvidia driver works truly very fine, I do not have any problems with it. All screensavers are running smoothly, you will also enjoy nice fade in fade out effects when the system goes into the screensaver mode or when a window for entering root password appears. I really enjoy all these things...

However, if you are a lot dependent on wifi (wifi is your only option to connect to internet) you will have sometimes a very hard time. Everything works nice after booting the system, and then out of nothing your wireless stops to work. If you type dmesg, you will see there irq#177 disabled...

This happens sometimes after one minute, sometimes after two hours. Sometimes I simply boot to winXP to have undisturbed internet browsing :-(

It is confirmed and rejected bug. It is a clash between two piece of hardware drivers: broadcom family wifi and nvidia driver. It was rejected, because it is responsibility of the producers to fix their drivers. It is not Ubuntu problem. I have read that with a new version ndiswrapper, things could be solved.

The nv driver that is in Ubuntu implicitely has a very very bad performance.

---

### Post by Jan Hrbacek on 2006-12-05
> **Jere Retzer said:**
> Please tell us more about how you did the partitioning. I just tried this yesterday and had problems.

Also, be advised that I have run into a severe bug, #43745 reported on [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43745](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43745) that has corrupted the realtime clock. The clock seems to race when running bios, but will synch once ubuntu is up with a network connection. I'm very interested to hear if anyone has a permanent fix for this as the workarounds mentioned (removing the cmos battery to dump the bios) seems temporary at best. Thanks

I didn't experience any problems of this character. I cannot confirm bug #43745 with my configuration.

Partitioning: yes there were some problems. GUI for partitioning that you enter during the instalation of Ubuntu from liveCD had some little issues. I think I had to close it once and start the partitioning again. But for the second run, everything was ok. Sorry, it has been some weeks ago. I do not remember the details. In principle, it works.

---

### Post by ruewan on 2007-01-09
I have the same dell 1490 card. My machine is a 1501 the 1.18 ndiswrapper did not work for me. I uninstalled the 1.18 stuff and downloaded the latest stable version from sourceforge 1.34 built those, got the driver out of the R140747.EXE file and that worked for me.

---

### Post by Chakademus on 2007-01-15
Can anyone give advice on what should be done to get a composite manager up and running on this laptop? I tried getting Xgl up, but it's doing some odd things, and I haven't even tried compiz on top of that. I've only started with ubuntu recently, so any help would be greatly appreciated. 

Thanks.

---

### Post by Jan Hrbacek on 2007-01-24
From kernel 2.6.19 the issue with the wifi should be solved. I have tried to compile 2.6.20.rc5, compilation was succesfull, however when booting it, computer remains pending at certain point during booting....

I have followed this instruction
[http://www.ubuntuforums.org/showthread.php?t=334373&highlight=2.6.20+rc3](http://www.ubuntuforums.org/showthread.php?t=334373&highlight=2.6.20+rc3)

At this point I cannot confirm, if it works or not.
I wish someone who sees into things prepares kernel optimized for Latitude D820. Life would be so much easier and I could actually begin to use linux applications and not only try to make linux work...

---

### Post by slick_rick on 2007-02-10
Does it suspend to RAM/DISK correctly and also wake up?

---

