---
title: "Ubuntu 10.04 Resolution Change: No 16:9"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by dcgr on 2012-02-19
Hi all,

I recently installed Ubuntu 10.04 on my desktop alongside Windows 7.  In Windows 7 on this monitor, I was using the default resolution of 1600x900.  In Ubuntu however, it defaults to 1152x864.  When I go to System>preferences>monitors to change it, there are only 4:3 resolutions available, with no 16:9.  So, I started looking around for ways to change it.  First, I came to this page:  [[COLOR="Blue"]http://newtoubuntu.wordpress.com/2010/07/17/ubuntu-10-04-fixing-the-monitor-resolution-with-xrandr/[/COLOR]]("http://newtoubuntu.wordpress.com/2010/07/17/ubuntu-10-04-fixing-the-monitor-resolution-with-xrandr/")
And it didn't fix my problem.  Here's what happens when I follow those instructions:  
```
username@username-lnxdesk:~$ xrandr
Screen 0: minimum 640 x 400, current 1152 x 864, maximum 1152 x 864
default connected 1152x864+0+0 0mm x 0mm
   1152x864        0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  
   720x400         0.0  
username@username-lnxdesk:~$ cvt 1600 900
# 1600x900 59.95 Hz (CVT 1.44M9) hsync: 55.99 kHz; pclk: 118.25 MHz
Modeline "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
username@username-lnxdesk:~$ xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
username@username-lnxdesk:~$ xrandr --addmode default 1600x900_60.00
username@username-lnxdesk:~$ xrandr --output default --mode 1600x900_60.00
xrandr: screen cannot be larger than 1152x864 (desired size 1600x900)
username@username-lnxdesk:~$ 

```
So it didn't work.  When I go to system>preferences>monitors, there is a 1600x900 option, but when I click on it and hit "apply," nothing happens.  

Next, I came across this page: [[COLOR="blue"]http://www.linuxquestions.org/questions/linux-hardware-18/video-resolution-issue-for-ubuntu-10-04-a-809681/[/COLOR]]("http://www.linuxquestions.org/questions/linux-hardware-18/video-resolution-issue-for-ubuntu-10-04-a-809681/")
However, I do not have a xorg.conf file in /etc/X11. 

So, I went here: [[COLOR="blue"]http://ubuntuforums.org/showthread.php?t=1336863[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1336863")
And followed the instructions.  Hit **ctrl+alt+f1**, and then typed the following commands:  
```
sudo service gdm stop
sudo Xorg -configure
sudo service gdm start
```
I still do not have an xorg.conf file in /etc/X11, but now I have an xorg.conf.new file in home/username.  So, I went to the second page I referred to, and re-followed the instructions there (with the exception that I was altering my home/username/xorg.conf.new file, not /etc/X11/xorg.conf).  So, in that file, my monitor section and screen section look like this:

```
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	Modeline "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
	Option	    "PreferredMode" "1600x900"
EndSection
Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Depth 	24
		Modes 	"1600x900" "1152x864" "1024x768" "800x600"
	EndSubSection
EndSection

```

I saved that, then stopped gdm, typed:
```
sudo dpkg-reconfigure xserver-xorg
sudo xinit -- :2
```
And restarted gdm.  Nothing happened, I'm still stuck in 1152x864.  The 1600x900 option in system>preferences>monitors still doesn't work.  

So, that's where I'm at.  If anyone can give me any help, it would be greatly appreciated.  Thanks!

---

### Post by sadaruwan12 on 2012-02-19
Welcome to the forum.

Please run the following command in the terminal and please paste the out put here.

```
$ lspci
```

---

### Post by dcgr on 2012-02-19
Alright, 
```
username@username-lnxdesk:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 0100 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Device 1c5c (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6759
01:00.1 Audio device: ATI Technologies Inc Device aa90
05:00.0 Network controller: RaLink Device 5390
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
```

---

### Post by JKyleOKC on 2012-02-19
> **dcgr said:**
> I still do not have an xorg.conf file in /etc/X11, but now I have an xorg.conf.new file in home/username.  So, I went to the second page I referred to, and re-followed the instructions there (with the exception that I was altering my home/username/xorg.conf.new file, not /etc/X11/xorg.conf).  So, in that file, my monitor section and screen section look like this:

```
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	Modeline "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
	Option	    "PreferredMode" "1600x900"
EndSection
Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Depth 	24
		Modes 	"1600x900" "1152x864" "1024x768" "800x600"
	EndSubSection
EndSection

```

I saved that, then stopped gdm, typed:
```
sudo dpkg-reconfigure xserver-xorg
sudo xinit -- :2
```
And restarted gdm.  Nothing happened, I'm still stuck in 1152x864.  The 1600x900 option in system>preferences>monitors still doesn't work.You need to copy that file from your home directory to /etc/X11, which you can do with this command:```
sudo cp $HOME/xorg.conf.new /etc/X11/xorg.conf
```However be sure it's still the way you made it, since that later "dpkg-reconfigure" command you gave may have changed it.

There's no need to stop gdm and reconfigure after copying the file over to /etc/X11. Just restart the system; it will then read the new file and attempt to configure the drivers accordingly. It might still fail, if the monitor's "EDID" response during the boot sequence is faulty, but you should at least find some clues in the xorg logs if it does.

During boot, the system looks only in /etc/X11 for the configuration file, which is why your first attempt had no effect. The reconfigure command puts the new file into your home directory specifically to prevent it from making your video totally unusable if something goes wrong -- which could happen. If it does, however, you can go into "recovery mode" and fix it from the command line by simply deleting the xorg.conf file from /etc/X11. If you need to do this, let us know and we can give you the details...

---

### Post by sadaruwan12 on 2012-02-19
You've a ATI graphic card which is little troublesome when it comes to linux 'cos unlike nvidia which have grate linux driver support ATI is little behind and when using it in lucid you need a special fglrx driver.

So I found this try this and see.

Original post by jngrim his [post]("http://ubuntuforums.org/showpost.php?p=9062521&postcount=158")

```

1. sudo apt-get purge fglrx-modaliases fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx xorg-driver-fglrx-dev
2. reboot
3. sudo rm -r /etc/ati
4. sudo rm /etc/X11/xorg.conf*
5. Opened synaptics, ad installed fglrx(it will reinstall dkms,and amdcccle)
6. Immediately after, open terminal: sudo aticonfig --initial
7. Reboot

```

> **NOTE:** If you don't find a /etc/ati then use rm -rf /usr/share/ati then reboot

Please Report back when finished.

---

### Post by dcgr on 2012-02-19
Okay.  I copied the file to /etc/X11, like JKyleOKC said, and while it still works fine, at boot I get this message:
```
Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) FBDEV(0): FBIOPUT_VSCREENIONFO: Invalid argument
(EE) FBDEV(0): FBIOPUT_VSCREENIONFO: Invalid argument
(EE) FBDEV(0): FBIOPUT_VSCREENIONFO: Invalid argument
(EE) FBDEV(0): EGA/VGA planes are not yet supported by the fbdev driver.
```

I hit "ok," and I got this list of options:

```
[LIST]
[*]Run Ubuntu in low-graphics mode for just one session
[*]Reconfigure graphics
[*]Troubleshoot the error
[*]Exit to console login
[*]Restart X
[/LIST]
```
And I chose the first one. It runs, but still in 1152x864.

Then, I followed sadaruwan12's instructions.  All went well. I didn't find /etc/ati so I removed /usr/share/ati instead.  Then I hit the last step, and I got this:  
```
username@username-lnxdesk:~$ sudo aticonfig --initial
aticonfig: No supported adapters detected
```
Now when I go to system>preferences>monitors, I get the following message:
> It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?
If I click No, I go to the normal monitors screen.  But when I click Yes, I get:
> Initialization error
There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.  
No ATI graphics driver is installed, or the ATI driver is not functioning properly.  Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
I already tried aticonfig, and that didn't work, so is it possible that there's a driver that the fglrx package didn't get?

---

### Post by dcgr on 2012-02-20
Okay, I got it working.  Based on what was going on before, I figured out that I didn't have the right drivers for the ATI card that I had.  Based on looking on other threads, I figured out that I would probably have to install new drivers.  I came across this page: [[COLOR="RoyalBlue"][COLOR="Blue"]http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide[/COLOR][/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide")  

And I followed the section "Removing the Driver" and then the section "Installing the drivers manually."  Now it seems to be working just fine, in 1600x900.  Thanks, both sadaruwan12 and JKyleOKC!

---

