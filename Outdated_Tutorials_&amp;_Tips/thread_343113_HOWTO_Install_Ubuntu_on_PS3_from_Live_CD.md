---
title: "HOWTO: Install Ubuntu on PS3 from Live CD"
date: 2007-01-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Ciego on 2007-01-20
[CENTER]**[SIZE=5]Installing Ubuntu Linux on the PLAYSTATION 3 - (PS3)[/SIZE]**

** [SIZE="4"]Check out [PSUbuntu.com]("http://psubuntu.com") for more related information.[/SIZE]**
[HowTo: Enable Java for Firefox]("http://psubuntu.com/2007/02/13/howto-enable-java-for-firefox/")
[HowTo: NES Emulator]("http://psubuntu.com/2007/02/06/howto-nes-emulator/")
[HowTo: SNES Emulator]("http://psubuntu.com/2007/02/05/howto-snes-emulator/")
[HowTo: Fullscreen on a 1080p HDTV]("http://psubuntu.com/forum/viewtopic.php?t=13")
[HowTo: Share a Hard Drive Between Linux and the XMB]("http://psubuntu.com/forum/viewtopic.php?t=16")

**[size="2"]We also have a dedicated [PSUbuntu forum[/size]]("http://psubuntu.com/forum/index.php")**

[SIZE="5"]
**The installation process has been simplified now that we have a Live CD for the PS3.  Please see the guide at [http://psubuntu.com/installation-instructions/](http://psubuntu.com/installation-instructions/) before you do this the hard way.**
[/SIZE][/CENTER]


**[SIZE=3]Introduction:[/SIZE]**
These instructions are for installing Ubuntu (Edgy Eft 6.10) on a 60GB PS3. We will install Linux on the 10GB portion of the partitioned PS3 hard drive. You may add external USB storage later to beef up your system should you prefer. This method requires the use of a Live CD but no other previous installation is required. Your PS3 will need to be connected to the internet. Please note that the wireless connection will not work so you will need to be hard wired into your network.
 
Please keep in mind that I am trying to write this guide in a manner that will enable a user who has never experienced Linux before to pick it up and get Ubuntu running.
 
```
$ Anything that you see that looks like this is to be typed at the command line
```

You should note that if you print this document as it is shown here that you may be missing some information that is in a box that has a scrollbar.  You may not notice this on a printed version so you may want to make a quick comparison after printing.
 
**[SIZE=3]Credits/References:[/SIZE]**
All of the information was originally composed by Louis Candell and was adapted by Ciego for installing Ubuntu without having installed Fedora prior to the Ubuntu installation. You can view this document in its original form at [http://www.louiscandell.com/ps3/](http://www.louiscandell.com/ps3/)
 
Credit should also be given to the Gentoo developers for creating the Live CD that makes this possible

Thank you to all of the Ubuntuforums.org users who helped us get where we are.
[INDENT]Thanks to "juanzone" for correcting several code errors.  
Thanks to "Strydre" for correcting some code errors and for the tip about copying the modules.  
A special thanks to "NobodySpecial" for correcting some code errors and showing us how to install the Ubuntu desktop (that one was giving me a headache) as well as the Java support.  
Thanks to "theBishop" for showing us how to use debootstrap from the Gentoo Live CD.  
Thanks to "S-Anarchy" for the tip about editing files created using notepad in windows.  
Thanks to "mb26" for several contributions concerning corrections/additions including resolving the sound issue.  
Thanks to "Geta-Ve" for the tip  on using the Live CD for everything up to step 5.  
Thanks to "joechoes" for the tip on saving files in Windows.  
Thanks to "3vi1" for the tip concerning audio permissions and other code corrections/tips and also fixing the "boot-game-os" command for Kubuntu.  
Thanks to "Joel1234567" for the tip concerning the xorg.conf and some errors that were showing up.
[/INDENT]
The following sites were used as additional references.
[INDENT]
Ubuntu Installation documentation
[INDENT][https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/linux-upgrade.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/linux-upgrade.html)[/INDENT]
Here is more information on kboot if you are interested:
[INDENT][http://kboot.sourceforge.net/](http://kboot.sourceforge.net/)[/INDENT]
 
You may find more detailed instructions at the Sony site.
[INDENT][http://www.playstation.com/ps3-openplatform/manual.html](http://www.playstation.com/ps3-openplatform/manual.html)[/INDENT][/INDENT]

 
 
**[SIZE=3]01 &#8211; Collect the items that you need for the installation.[/SIZE]**

*NOTE - It is possible to do everything up to step 5 using cut/paste within the Gento Live CD desktop with the exception of burning the Gentoo iso for obvious reasons.  I would recommend reading this entire document as well as the following discussions before trying this unless you have some Linux experience.
 
You will need a computer with an internet connection as well as a PS3 with a hard wired internet connection
 
[INDENT]*USB Mouse
*USB Keyboard
* 256MB USB Thumb drive 
    [INDENT](Any storage device that the PS3 can handle will work. Adjust commands accordingly)[/INDENT] 
* Addon CD iso
     [INDENT][http://dl.qj.net/dl.php?fid=11308](http://dl.qj.net/dl.php?fid=11308)[/INDENT]
*Gentoo Live CD BETA for PPC iso
     [INDENT][http://gentoo.mirrors.pair.com/experimental/ppc64/livecd/livecd-ppc64-beta.iso](http://gentoo.mirrors.pair.com/experimental/ppc64/livecd/livecd-ppc64-beta.iso)[/INDENT]
*Otheros.self
     [INDENT][http://www.playstation.com/ps3-openplatform/terms.html](http://www.playstation.com/ps3-openplatform/terms.html)[/INDENT][/INDENT]
 

**[SIZE=3]02 &#8211; Prepare your media[/SIZE]**
 
Burn the Gentoo iso onto a CD. Note that you cannot burn the iso as a regular file. It must be burned as a disk image. I also recommend burning important disks like this at very slow speeds. (4x or 8x if possible) Here is a link to more information regarding iso burning.
[INDENT][https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)[/INDENT]
 
Plug your USB storage drive into your computer and create the directory structure [INDENT]USB:\PS3\OTHEROS[/INDENT]
In other words ... create a folder called &#8220;PS3&#8221; then create a folder inside that called &#8220;OTHEROS&#8221; 
 
Save the Otheros.self file that you downloaded in the &#8220;OTHEROS&#8221; folder
 
Extract the ADDON CD iso to the root of your thumb drive using 7zip or similar program. Make sure that you extract the iso so that the contents of the &#8220;CELL-Linux-CL_20061110-ADDON&#8221; folder are in the root of the USB drive.
Here is a link to a program that will help you if you cannot extract an iso 
[INDENT][http://www.7-zip.org/](http://www.7-zip.org/)[/INDENT]
(note that there are some helpful documents in the /doc folder)
 
Copy otheros.bld from the new &#8220;kboot&#8221; folder on your USB drive into the &#8220; OTHEROS&#8221; folder that we made earlier
 
Create another folder in the root of your USB drive called &#8220;config&#8221;
 
Create a file called &#8220;fstab&#8221; and copy/paste this into it. You can use notepad if you are in Windows. (If you do it in notepad, you may need to rename it to remove the file extension,  You may want/need to edit your fstab file to get rid of the Windows return line characters (^M) at the end of each line ... you can do this when you are in Linux with nano after you copy it over later in the guide.  Another solution is to "save as" and type "fstab" with the quotes as the filename.) 
 
```

# /etc/fstab: static file system information.
# file system mount point type options dump pass
LABEL=/ / ext3 defaults 0 0
LABEL=/boot /boot  ext2 defaults 0 2
LABEL=SWAP SWAP swap sw 0 0
proc /proc proc defaults 0 0
sys /sys sysfs defaults 0 0
/dev/fd0 /mnt/floppy auto noauto,rw,sync,user,exec 0 0
/dev/cdrom /mnt/cdrom iso9660 noauto,ro,user,exec 0 0
###### /etc/fstab done    

```
 
Save your &#8220;fstab&#8221; file in the &#8220;config&#8221; folder that you made.
 
Create a file called &#8220;xorg.conf&#8221; and copy/paste this into it. You can use notepad if you are in Windows. (If you do it in notepad, you will need to rename it to change the file extension)
```

### PS3 xorg.conf for Ubuntu / Debian Linux
### http://www.louiscandell.com/ps3/files/xorg.conf
 
Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    FontPath    "/usr/share/fonts/X11/misc"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
 
Section "Module"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection
 
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
    Option        "XkbOptions"    "lv3:ralt_switch"
EndSection
 
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
EndSection
 
 
Section "Device"
    Identifier    "Generic Video Card"
    Driver        "fbdev"
 
    Option        "ShadowFB"        "false"
#    Option        "UseFBDev"        "true"
EndSection
 
Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "IgnoreEDID"
    HorizSync    30-90
    VertRefresh    20-150
    ModeLine "720p" 73.825 1280 1320 1368 1640 720 722 724 751 +hsync +vsync
    DisplaySize    320 180
EndSection
 
Section "Screen"
    Identifier    "Default Screen"
    Device        "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    DefaultFbBpp    32
 
 
    SubSection "Display"
        Viewport    0    0
        Depth        24
        FbBpp        32
        Modes        "1024x720" "1124x644"
    EndSubSection
 
    SubSection "Display"
        Depth        15
        Modes        "1024x720" "1024x768" "800x600" "640x480"
    EndSubSection
 
    SubSection "Display"
        Depth        16
        Modes        "576x384" "1024x768" "800x600" "640x480"
    EndSubSection
 
EndSection
 
Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection
 
Section "DRI"
    Mode    0666
EndSection

```
 
Save your &#8220;xorg.conf&#8221; file in the &#8220;config&#8221; folder that you made.
 
Remove the USB storage drive from your computer and plug it into your PS3.
Insert the Gento Live CD into the PS3 
 
**[SIZE=3]03 - Install kboot on the PLAYSTATION 3[/SIZE]**
 
If you already have data saved on the PS3 hard drive, you may back it up using the PS3 backup utility and restore the data after you format and partition the hard drive. (These instructions have already changed due to PS3 firmware updates, but you should still be able to figure out what to do)
 
 
* On the XMB go into Settings Menu > System Settings > Format Drive
* Choose 10GB for the &#8220;other OS&#8221;
* After the drive is formatted, go into Settings Menu > System Settings > Install Other OS
* Click "OK" and it will install the kboot image onto your PS3.
* Once finished, go back into Settings Menu > System Settings > Default System > Choose "Other OS"
* Restart your PS3 and you should be on the kboot prompt
 
Now once you are on the kboot prompt you are within a minimal Linux environment.
 
**[SIZE=3]04 &#8211; Partition and format the &#8220;Other OS&#8221; portion of the hard drive[/SIZE]**
 
We will partition the 10GB portion of the hard drive as follows using fdisk. 
LABEL PARTITION SIZE SYSTEM
1) boot /dev/sda1 256MB ext2
2)SWAP /dev/sda2 512MB swap 
3) / /dev/sda3 the remaining space ext3
 
We need to boot into Gentoo to do this since the Kboot environment does not support the creation of swap partitions. (If you have some experience with Linux, you may want to take care of the root and boot partitions now and worry about the swap partition after you can chroot into Ubuntu. If so, you can do this from the kboot prompt rather than booting the Live CD)
 
Use the <tab> key to select your screen resolution and press <enter>. Gentoo will boot up. This takes a while since the entire operating system is booting from the CD. You should be looking at the Gentoo desktop. (Note that you may boot into the command line by adding a space and &#8220;nox&#8221; after the resolution command.) Take it for a spin if you would like. You can install Gentoo from this disk if you like it.
 
Open a terminal (Alternatively, you can hit Ctrl+Alt+F1 to get to the command line as root ... if you do this, you will not need the following two commands)
Click Applications>Terminal
```

$ sudo -s
$ /etc/init.d/xdm stop

```
 
You should now be looking at the command line.
 
```

$ cd
$ fdisk /dev/sda

```
 
At the fdisk prompt:
[INDENT]Create partition 1
[INDENT]N (new) <enter>
P (primary) <enter>
1 <enter>
(default) <enter>
256 <enter>[/INDENT]
 
Create partition 2
[INDENT]N (new) <enter>
P (primary) <enter>
2 <enter>
(default) <enter>
769 <enter>[/INDENT] 

Create partition 3
[INDENT]N (new) <enter>
P (primary) <enter>
3 <enter>
(default) <enter>
(default) <enter>
 [/INDENT]

Mark partition 1 with the boot flag
[INDENT]A <enter>
1 <enter> [/INDENT]
Label Partition 2 as a swap file system
[INDENT]T <enter>
2 <enter>
82 <enter>[/INDENT]
Write the partition table
[INDENT]W <enter>[/INDENT][/INDENT] 
This part is extremely important &#8230; reboot the PS3 at this point. I wasted about 3 hours trying to get this to work until I realized that the newly created partitions needed a reboot to be recognized. 
 
```

$ reboot

```
 
This will shutdown Gentoo and reboot the PS3. It should automatically boot into Kboot.
<tab> to select your resolution and press <enter> to boot the Live CD again. (Remember we can type &#8220;nox&#8221; at the end to boot straight to the command line.)
 
Open a terminal
Click Applications>Terminal
```

$ sudo -s
$ /etc/init.d/xdm stop

```
 
You should now be looking at the command line again.
Now we will need to create a filesystem on our partitions and then mount them. The &#8220;-L&#8221; option adds a label to the partitions.
 
```

$ mkfs.ext2 -L "/boot" /dev/sda1
$ mkfs.ext3 -L "/" /dev/sda3
$ mkswap -L "SWAP" /dev/sda2
$ sync; sync; sync
$ swapon /dev/sda2 
$ mkdir /mnt/ubuntu
$ mount /dev/sda3 /mnt/ubuntu
$ mkdir /mnt/ubuntu/boot
$ mount /dev/sda1 /mnt/ubuntu/boot

```
 
 
**[SIZE=3]05 - Install Ubuntu on the PLAYSTATION 3[/SIZE]**
 
```

$ cd /tmp
$ wget http://archive.ubuntulinux.org/ubuntu/pool/main/d/debootstrap/debootstrap_0.3.3.0ubuntu7_all.deb
$ ar -xf debootstrap_0.3.3.0ubuntu7_all.deb
$ zcat < data.tar.gz | tar xv

```
 
We need to edit debootstrap since we are running it off of a Live CD
 
```

$ cd usr/sbin
$ vim debootstrap

```
 
Now you will be inside of a text editor. Use the arrow keys to go down to line 11 and over to the &#8220;/&#8221; in that line. Hit the <insert> key to go into edit mode. Add &#8220;/tmp&#8221; to the beginning of the path. Hit the <esc> key to exit editing mode. That line should look like this now.
```

DEBOOTSTRAP_DIR=/tmp/usr/lib/debootstrap

```
 
Type &#8220;:wq&#8221; to save and quit. 
You should be back at the command line now.
 
Run debootstrap
(If you have a slow internet connection, you can use the Ubuntu CD to install by replacing the url with &#8220;file:/mnt/cdrom/ubuntu&#8221; ... note that you will need the correct CD and have it mounted at /mnt/cdrom )
 
```

$ /tmp/usr/sbin/debootstrap --arch powerpc edgy /mnt/ubuntu http://archive.ubuntulinux.org/ubuntu

``` 
 
This will install your base Ubuntu system. 
We still need to copy a few things from the CD onto the PS3 hard drive.
 
```

$ cp /boot/* /mnt/ubuntu/boot
$ cd /mnt/ubuntu/boot
$ cp kernel-genkernel-ppc-2.6.16-ps3 /mnt/ubuntu/boot/vmlinux
$ cp initramfs-genkernel-ppc-2.6.16-ps3 /mnt/ubuntu/boot/initrd.img
$ cp -R /lib/modules/* /mnt/ubuntu/lib/modules/

```
 
Now we can reboot the PS3 and take out the Live CD since we no longer need it.
 
```

$ reboot

```
 
**[SIZE=3]06 - Configuring Minimal Install of Ubuntu Base System[/SIZE]**
 
We will have to mount the partitions manually for now. 
 
```

$ umount /mnt/root
$ mkdir /mnt/ubuntu
$ mount /dev/sda3 /mnt/ubuntu
$ mount /dev/sda1 /mnt/ubuntu/boot

```
 
Copy the &#8220;fstab&#8221; file from your USB drive. We have to mount the USB drive first. You can find the location of your USB drive by typing 
 
```

$ fdisk -l

```
 
Try to locate which one your USB drive is by the size. If it says &#8220;sdd&#8221; then your drive will be recognized as &#8220;sdd1&#8221;
 
```

$ mkdir /mnt/usbdrive
$ mount /dev/sdd1 /mnt/usbdrive
$ cp /mnt/usbdrive/config/fstab /mnt/ubuntu/etc/fstab

```
 
CHROOT into ubuntu and install nano. (You can use nano to create your config files or you can create them on your computer to save some typing and then transfer them via the usb drive)
 
```

$ chroot /mnt/ubuntu /bin/bash
$ source /etc/profile
$ apt-get install nano

```
 
The above command has you in your new Ubuntu system in its infant state.

You can manually mount each filesystem once you are chrooted into your Ubuntu System, or you can automatically mount them with ...
 
```

$ mount -a

```
 
The above game some errors, so make sure that both /proc and /sys were mounted. Check to see if they are mounted by seeing if there is anything in them:
 
```

$ ls /proc /sys

```
 
If /proc and /sys are not mounted then you will manually mount them like this:
 
```

$ cd /
$ mount -t proc proc proc
$ mount -t sysfs sysfs sys

```
 
**[SIZE=3]07 - Installing The Xubuntu / Ubuntu / Kubuntu desktop[/SIZE]**
 
At this stage you have a choice of installing whatever desktop you like. You can either install the Ubuntu, Xubuntu or the Kubuntu desktop. You will want to issue one of the following commands depending on what desktop you want. (The Ubuntu desktop install had too many dependencies to resolve and eventually stopped after running out of system memory in my case. You may try it, but it would not work for me. Don't worry though ... we can install the Ubuntu desktop later ... go ahead and install Kubuntu for now)
 
```

$ aptitude -y install '~txubuntu-desktop'
$ aptitude -y install '~tubuntu-desktop'
$ aptitude -y install '~tkubuntu-desktop'

```
 
Once the above is done you are finished. You have installed Ubuntu on your PS3.
 
**[SIZE=3]08 - More Configuration and Adding Users[/SIZE]**
   
We need to create a username and give the user the ability to use sudo.  We will go ahead and add you to the audio, admin, and users groups now also

```

$ passwd root
$ adduser YOUR_USER_NAME
$ addgroup --system admin
$ adduser YOUR_USER_NAME admin
$ adduser YOUR_USER_NAME audio
$ adduser YOUR_USER_NAME users
$ visudo -f /etc/sudoers

```
 
add this to the end of the file so that users in the admin group can use sudo

```

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

Configure the Keyboard
```

$ dpkg-reconfigure console-setup

```

Configure /etc/network/interfaces

```

$ nano /etc/network/interfaces

```
Make it look like this
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

configure /etc/resolv.conf

```

$ nano /etc/resolv.conf

```
Make it look like this (just an example ... you will have to configure it for your internet connection)  If you are running linux on another computer in your house, just look at the /etc/resolv.conf on that computer.
```

search hsd1.ma.comcast.net.
nameserver 192.168.1.1
nameserver 192.168.1.2
domain YOUR_WORKGROUP

```

Edit your hostname (this can be whatever you want)
```

$ echo playstation > /etc/hostname

```

Edit /etc/hosts
```

$ nano /etc/hosts

```
Make it look like this
```

127.0.0.1 localhost
127.0.1.1 YOUR_HOSTNAME.YOUR_WORKGROUP

```

Don't leave that command line because we will be using it in the next section.
 
**[SIZE=3]09 - Configuring /etc/X11/xorg.conf and ps3videomode.[/SIZE]**
 
We need to copy a few more files from our USB drive.  We will also have to install alien to tranform our rmp packages into deb packages.
 
```

$ exit
$ cp /mnt/usbdrive/target/ps3pf_utils-1.0.9-2.ppc.rpm /mnt/ubuntu/tmp/ 
$ cp /mnt/usbdrive/target/vsync-sample-1.0.1-4.ppc.rpm /mnt/ubuntu/tmp/
$ cp /mnt/usbdrive/config/xorg.conf /mnt/ubuntu/etc/X11/xorg.conf
$ chroot /mnt/ubuntu /bin/bash
$ cd /tmp 
$ apt-get install alien
$ alien ps3pf_utils-1.0.9-2.ppc.rpm
$ alien vsync-sample-1.0.1-4.ppc.rpm
$ dpkg -i ps3pf-utils_1.0.9-3_powerpc.deb
$ dpkg -i vsync-sample_1.0.1-5_powerpc.deb
$ sudo nano /etc/kboot.conf

```
 
We need to create a kboot.conf file.  It should look like this
```

default=ubuntu
timeout=10
root=/dev/sda3
 
ubuntu="/boot/vmlinux initrd=/boot/initrd.img video=ps3fb:mode:5"

```
 
Make sure you edit the video mode to match what you found on the chart earlier.  Here is the chart for reference.

[INDENT]Video mode ID:
 0:automode
 YUV 60Hz 1:480i 2:480p 3:720p 4:1080i 5:1080p
 YUV 50Hz 6:576i 7:576p 8:720p 9:1080i 10:1080p
 RGB 60Hz 33:480i 34:480p 35:720p 36:1080i 37:1080p
 RGB 50Hz 38:576i 39:576p 40:720p 41:1080i 42:1080p
 VESA 11:WXGA 12:SXGA 13:WUXGA

 full screen mode: <video mode ID> + 128
 dither ON mode : <video mode ID> + 2048[/INDENT]
 
Now you should be in good shape. 

Make sure that you are at the actual kboot prompt and not still inside the chroot at this point. Use the exit command if you are still in the chroot.
```
 $ exit
```

This is the command for starting Ubuntu from kboot.
```

$ mnt/ubuntu/boot/vmlinux initrd=mnt/ubuntu/boot/initrd.img root=/dev/sda3

```

We should go ahead and reboot first just to make sure that Ubuntu will boot automatically now.

```

$ reboot

```

You should then be booting Ubuntu and end up at the login screen.  Do not press any keys when the kboot prompt comes up.  It will take 10 seconds for the command to kick in.
If all went well you should be at the login screen. Use the user name that you just created and login. You will then be prompted to setup your KDE configurations.

**[SIZE=3]10 - Install the Ubuntu Desktop[/size]** (this section is optional and should be used if you wanted the Ubuntu desktop and it wouldn't work during the normal installation)

If you would like to use the Ubuntu desktop rather than the Kubuntu or Xubuntu that you installed.  Open up a terminal and issue the commands ... 

```

$ sudo apt-get install ubuntu-desktop

```
Choose "gdm" as your desktop when the install screen pops up at the end.

When that is finished installing everything, you should reboot. (you can do this using the graphical interface or by issuing the command in the terminal)

After the system reboots, you should be looking at the Ubuntu log in screen.  Go ahead and login.  Open a terminal by  clicking Applications>Accessories>Terminal and issue the following command to uninstall the KDE components of the desktop. (This is if you installed the KDE desktop previously)

```

$ sudo apt-get remove adept kaddressbook kaffeine kamera kappfinder karm katapult kate kaudiocreator kcron kde-guidance kde-systemsettings kdeadmin-kfile-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdm kghostview khelpcenter kicker kio-apt kio-locate klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguardd ksystemlog kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin

```

If you ever want to get back to the PS3 XMB from the kboot prompt or from inside of Ubuntu, open a teminal and type ...
 
```

$ sudo boot-game-os

```
 
If you are using the Kubuntu desktop and issue the command "boot-game-os"... you might notice it doesn't work. The reason is that the script depends on another script, "find-other-os-flash", that uses at least one bash-ism, yet the script specifies that it should be run by sh. sh on Kubuntu will be using Dash, not Bash... so it will fail. To fix it, open up /sbin/find-other-os-flash with your favorite editor and change the first line from: "#! /bin/sh" to '#! /bin/bash".

```
$ sudo nano /sbin/find-other-os-flash 
```
The command "boot-game-os" should work fine after that.

Ubuntu Starter guide
[INDENT][http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)[/INDENT]

You May want to get some restricted formats to play (MP3s, DVDs, etc.)
[INDENT][https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)[/INDENT]

You may also want to add some additional repositories
[INDENT][https://help.ubuntu.com/community/Repositories/Ubuntu?highlight=%28REPOSITORIES%29](https://help.ubuntu.com/community/Repositories/Ubuntu?highlight=%28REPOSITORIES%29)[/INDENT]
 
I am sure we will be seeing you here
[INDENT][http://www.ubuntuforums.org/index.php](http://www.ubuntuforums.org/index.php)[/INDENT]

Share your PS3 alias with us here
[indent][http://ubuntuforums.org/showthread.php?t=319528]("http://ubuntuforums.org/showthread.php?t=319528")[/indent]
 
Enjoy!
 
**[SIZE=3]11 - Change Log[/SIZE]**
01/21/07 - formatting
01/22/07 - edited fstab for file system labeling, formatting, resolved sudo issues by changing the commands for adding a user, changed file labeling commands, edited kboot.conf, changed the order of commands to reduce the number of reboots needed, added configuration of network.
01/23/07 - added -f option to the visudo command to edit /etc/sudoers. (Thanks for the catch jaunzone)
01/24/07 - changed a few commands (Thanks for the catch NobodySpecial), added section 10 for installing the Ubuntu Desktop(A big thanks to NobodySpecial for this one)
01/25/07 - added some helpful links at the end of the document.
01/26/07 - changed code in section 6 and 9 correcting chroot issues, editd kboot file, added the video mode chart, added notes concerning switching from Kubuntu to Ubuntu (Thanks to Strydre for the corrections)
01/31/07 - Added note concerning editing files that were created in notepad (Thanks for the tip S-Anarchy).
02/05/07 - Removed an extra "/" that was in the command for mounting the USB drive. (Thanks again to NobodySpecial)
02/13/07 - Added some PSUbuntu.com links, added the exit command at the end of step 9 (Thanks to mb26), added note concerning using the Live CD up to step 5 (thanks to Geta-Ve), added tip for saving files in Windows, added code that will add you to the audio and users groups (Thanks to mb26 and 3vi1 for the tip), edited the xorg.conf by removing some lines that were suggested to be commented out (thanks to Joel1234567 for the tip ... also note that if you need to change this you will need to logout and log back in for it to take effect), removed the command in step 6 that tried to make a directory that is already made (thanks to 3vi1 for the tip), added tip for getting to root prompt (thanks to 3vi1), added a note about the "boot-game-os" command (thanks to 3vi1)
02/16/07 - Added a line of code that will copy the modules from the Gentoo Live CD in the section where we copy the kernel. (Thanks to DarthStrydre for the tip), added link to 1080p fullscreen HowTo.
02/20/07 - added a link to the guide for sharing a hard drive between Linux and the XMB

**[SIZE=3]TO DO:[/SIZE]**
All known issues with the install resolved.
I may write more guides to add repositories, run emulators, install codecs, etc. in the near future.  If so, they will be linked in this guide.

Please let me know if there are any errors that you find here. If you contribute, you will be added to the credits section.

---

### Post by NobodySpecial on 2007-01-23
Fantastic post - it works great!  Many thanks for all your hard work, Ciego.

I couldn't get get ubuntu-desktop to install either, so I installed kubuntu-desktop.

After rebooting and logging into kubuntu, I did:

```
sudo apt-get install ubuntu-desktop
```

Logged out of Kubunt, then logged into Ubuntu.  Then,
```

sudo apt-get remove adept kaddressbook kaffeine kamera kappfinder karm katapult kate kaudiocreator kcron kde-guidance kde-systemsettings kdeadmin-kfile-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdm kghostview khelpcenter kicker kio-apt kio-locate klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguardd ksystemlog kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin
```

So now I have Ubuntu with Gnome desktop on my PS3.

---

### Post by Ciego on 2007-01-24
> **NobodySpecial said:**
> Fantastic post - it works great!  Many thanks for all your hard work, Ciego.

I couldn't get get ubuntu-desktop to install either, so I installed kubuntu-desktop.

After rebooting and logging into kubuntu, I did:

```
sudo apt-get install ubuntu-desktop
```

Logged out of Kubunt, then logged into Ubuntu.  Then,
```

sudo apt-get remove adept kaddressbook kaffeine kamera kappfinder karm katapult kate kaudiocreator kcron kde-guidance kde-systemsettings kdeadmin-kfile-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdm kghostview khelpcenter kicker kio-apt kio-locate klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguardd ksystemlog kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin
```

So now I have Ubuntu with Gnome desktop on my PS3.

I also tried this but I could not get it to work.  My commands were a little bit different though.  I will have to try this(with your commands) and if it works for me I will add it to the guide with credit to you.  Thanks.

UPDATE: It worked ... added it to the main HOWTO.  Thank you for the great tip "NobodySpecial"

---

### Post by sam_w on 2007-01-25
thanks :D great guide, i will definately try it out when I get my PS3 on March 23rd :D 
(stupid uk delay :mad: :( )

---

### Post by Ciego on 2007-01-25
The delay is unfortunate ... but at least you will have Oblivion at launch. :D (and hopefully a better supply than us over here in the US at launch)

---

### Post by DarthStrydre on 2007-01-26
There appear to be a few problems in this procedure with regards to what exists and doesnt in the chrooted environment... I got through them, but an uninitiated may trip up.

In step 6, fstab is copied to the non-chroot /etc. Possible correction here:
```
$ mkdir /mnt/usbdrive
$ mount /dev/sdd1/ /mnt/usbdrive
$ cp /mnt/usbdrive/config/fstab /mnt/ubuntu/etc/fstab
```

In step 9, we are still chrooted, so /mnt/usbdrive does not exist. The path to vsync is missing an entry as well. Possible correction here:
```
$ exit
$ cp /mnt/usbdrive/target/ps3pf_utils-1.0.9-2.ppc.rpm /mnt/ubuntu/tmp/
$ cp /mnt/usbdrive/target/vsync-sample-1.0.1-4.ppc.rpm /mnt/ubuntu/tmp/
$ cp /mnt/usbdrive/config/xorg.conf /mnt/ubuntu/etc/X11/xorg.conf
$ chroot /mnt/ubuntu /bin/bash
$ cd /tmp
$ apt-get install alien
$ alien ps3pf_utils-1.0.9-2.ppc.rpm
$ alien vsync-sample-1.0.1-4.ppc.rpm
$ dpkg -i ps3pf-utils_1.0.9-3_powerpc.deb
$ dpkg -i vsync-sample_1.0.1-5_powerpc.deb
$ sudo nano /etc/kboot.conf
```

The kboot file is missing a slash:
```
default=ubuntu
timeout=10
root=/dev/sda3
 
ubuntu="/boot/vmlinux initrd=/boot/initrd.img video=ps3fb:mode:1"
```

The video mode chart should probably be copied here since it is a new thread and it does not exist earlier.

In step 10, the apt-get remove step is only needed if kubuntu was selected, not for xubuntu, which would install other packages.

I might have some suggestions for the xorg.conf... but not done experimenting yet.

Thanks for the cookbook :-)

 - Strydre

---

### Post by Ciego on 2007-01-26
Thank you for the input.  I changed the order of the guide around and those corrections were not caught.  I will make the changes.

---

### Post by astonius on 2007-01-26
Great HOWTO, just having one problem with kboot seemingly not mounting ubuntu on startup.  I keep getting the following error:  /boot/vmlinux: not found.  I was able to get into ubuntu by doing the following:

```

umount /mnt/root
mkdir /mnt/ubuntu
mkdir /mnt/ubuntu/boot
mount /dev/sda3 /mnt/ubuntu
mount /dev/sda1 /mnt/ubuntu/boot
mnt/ubuntu/boot/vmlinux initrd=mnt/ubuntu/boot/initrd.img root=/dev/sda3 video=ps3fb:mode:3

```

I have to retype that everytime I restart if I want to get into ubuntu.  I figure it's a problem with kboot.conf or fstab, but I copied them exactly how was described in the HOWTO.  Any suggestions?

---

### Post by astonius on 2007-01-26
Well I played around and figured it out.  It was in fact the kboot.conf file.  I changed it around and got it to boot on its own!  Here's what I have in my kboot.conf:

```

default=ubuntu
timeout=10
root=/dev/sda3

ubuntu="sda1:vmlinux initrd=sda1:initrd.img video=ps3fb:mode:3"

```

I don't know if anyone else has had the same problem, but it might be a possible update to the HOWTO (?).

Thanks again Ciego.

---

### Post by Ciego on 2007-01-27
If I had to guess, I would say that your problem was with a missing "/" somewhere in there.  The way that you ended up doing it is the way that I wanted to do it in the first place buy I couldn't get it to work for some reason.  Either way .... the same command is being issued overall.

---

### Post by DarthStrydre on 2007-01-28
I found myself unable to use vfat filesystems, as the driver was a kernel module.

The solution is to mount the gentoo livecd, then mount the squashfs as loopback, then copy the /lib/modules from that to one's system.

I have been unable to get any sound working though, except the bootup drum sound. Seems to be an inconsistency with ALSA... but linux sound systems give me headaches.

---

### Post by NobodySpecial on 2007-01-28
I can't get ALSA to work right either.  Anybody figure out a solution?

---

### Post by DarthStrydre on 2007-01-29
If I have time, I will be re-installing Xubuntu tonight. I intend to use this method, but use the Fedora kernel from the extra CD tonight, with the associated modules, etc, rather than the Gentoo one. This may help the sound issue, or maybe not :-)

I will be reinstalling rather than modifying to double check this cookbook again.

---

### Post by theBishop on 2007-01-29
No credit to theBishop, eh?

I'm hurt. [-(

---

### Post by Ciego on 2007-01-29
> **theBishop said:**
> No credit to theBishop, eh?

I'm hurt. [-(

I am sorry I didn't credit you ... it will be added.

---

### Post by Inbetweener on 2007-01-30
I don't suppose anyone who has ubuntu running on their PS3 has figured out how to get the wireless internet connection running?

Thanks

---

### Post by Ciego on 2007-01-30
> **Inbetweener said:**
> I don't suppose anyone who has ubuntu running on their PS3 has figured out how to get the wireless internet connection running?

Thanks

This is currently not possible.  This is not a problem with Ubuntu specifically, we just do not have drivers for the wifi yet.

---

### Post by Inbetweener on 2007-01-30
Thanks for the reply! another question from the complete Noob, are there any specific advantages to having Ubuntu on there instead of YDL?

---

### Post by NobodySpecial on 2007-01-30
I played around with YDL at first.  Install is REALLY smoothe.  Sound worked great.

On the other hand, there wasn't nearly the huge amount of packages like in Ubuntu.  Many things have to be compiled from source.

If we can just get ALSA working, Ubuntu will be THE setup to do for PS3.

So where would we go for ALSA help?  Would the ALSA config on a YDL install help?  I'm not really sure where to ask besides here . . .

---

### Post by Ciego on 2007-01-31
> If we can just get ALSA working, Ubuntu will be THE setup to do for PS3.

So where would we go for ALSA help? Would the ALSA config on a YDL install help? I'm not really sure where to ask besides here . . .

Is your sound not working at all?  Mine seems to work fine.  I can play mp3s and the splash screen sounds work fine also.  I haven't tested much else yet but those seem to work.

---

### Post by s-anarchy on 2007-01-31
Thanks for the great how-to! I've got Xubuntu working beautifully as of last night with very few issues.  One note for Notepad users (I hate admitting I used it but I do have on M$ box still around and it was most convenient).  You may want to / need to edit your fstab file to get rid of the Windows return line characters (^M) at the end of each line for your mount -a to work.

Thanks again,

S-Anarchy

---

### Post by Ciego on 2007-01-31
> **s-anarchy said:**
> Thanks for the great how-to! I've got Xubuntu working beautifully as of last night with very few issues.  One note for Notepad users (I hate admitting I used it but I do have on M$ box still around and it was most convenient).  You may want to / need to edit your fstab file to get rid of the Windows return line characters (^M) at the end of each line for your mount -a to work.

Thanks again,

S-Anarchy

Thanks for the reply ... I do not use Windows so I was unaware of the issue.  I will add this to the guide.

---

### Post by NobodySpecial on 2007-02-01
Ciego - No, I can't get sound working at all, only the initial blurb at the gdm login screen.

I even tried re-installing fresh, but sound won't work with gnome or kde.

In gnome, if I click on the volume control icon:
> No volume control GStreamer plugins and/or devices found.

If I run alsamixer, I get:
> alsamixer: function snd_ctl_open failed for default: No such device

I think these messages mean the hardware isn't properly detected.

What did you do to get your sound running???

---

### Post by Ciego on 2007-02-02
I had that problem at one time and realized that I had the power on my speakers turned off but other than that, the sound works right out of the box for me.  I have heard of people having problems with HDMI sound but I hooked up my HDMI cable this weekend and it works fine too.  I don't really know what else to tell you other than make sure that all of the cables are plugged in and working when in PS3 mode.

What cables are you using for sound?  If you are using optical, I would definitely try something else.  

I won't be able to respond again until Monday but we will get this working.  Good luck.

---

### Post by stormyuk on 2007-02-02
I know this might be a little bit offtopic but I am possibly looking at getting a Ps3 at some point and really like the idea of running ubuntu on it. The main reason for doing this would be to be *hopefully* able to play HD divX and HD Xvid (as well as standard divx/xvid) on a LCD HDTV via HDM as well of course having a great games console.

Is it possible to get xine working on Ubuntu on the PS3 and will the codecs work ok? divx, xvid HD and standard work fine with my kubuntu PC install.

Can some kind soul check these movie trailers out please? The PS3 wont be in the UK for a while.

[http://www.digital-digest.com/movies/da_vinci_code.html](http://www.digital-digest.com/movies/da_vinci_code.html) (HD Xvid 1280x608)

[http://www.digital-digest.com/movies..._wardrobe.html](http://www.digital-digest.com/movies..._wardrobe.html) (HD DivX 1280x544)

[http://www.dvdloc8.com/clip.php?movieid=630&clipid=1](http://www.dvdloc8.com/clip.php?movieid=630&clipid=1) (Xvid 5 720x400)

[http://www.digital-digest.com/movies...t_of_fire.html](http://www.digital-digest.com/movies...t_of_fire.html) (HD Xvid 1280x544)

Thanks very much, and much appreciated.

Mike

---

### Post by mb26 on 2007-02-02
Hello. thanks for attempting the guide. i am having trouble after the reboot at the end of #5. when i reboot and take out the CD, the kboot prompt comes up, but pressing tab doesn't bring up anything anymore and i can't get to a prompt which will accept unmount /mnt/root etc.. er, help please!

---

### Post by NobodySpecial on 2007-02-02
mb26 - As soon as the kboot prompt comes up, don't touch the tab button at all.  Just type:
```
umount /mnt/root
```
and continue on with the process.

Does that work for you?  If not, what does the prompt say?

---

### Post by sg333 on 2007-02-02
> Copy the “fstab” file from your USB drive. We have to mount the USB drive first. You can find the location of your USB drive by typing

Code:

$ fdisk -l

Try to locate which one your USB drive is by the size. If it says “sdd” then your drive will be recognized as “sdd1”

Code:

$ mkdir /mnt/usbdrive $ mount /dev/sdd1/ /mnt/usbdrive $ cp /mnt/usbdrive/config/fstab /mnt/ubuntu/etc/fstab



I cannot mount the usb drive.  It says:  > Cannot create directory '/mnt/usbdrive': File exists

I am new to Linux

---

### Post by mb26 on 2007-02-02
> **NobodySpecial said:**
> mb26 - As soon as the kboot prompt comes up, don't touch the tab button at all.  Just type:
```
umount /mnt/root
```
and continue on with the process.

Does that work for you?  If not, what does the prompt say?thanks for the reply.. no it doesn't work. its hard to tell what it says, being (i think) 480i on a PAL SDTV, but i think it is../init: e(?)val: 1: unmount: not found.

---

### Post by NobodySpecial on 2007-02-03
sg333 - I believe the code is wrong.  It should be:
```
mount /dev/sdd1 /mnt/usbdrive
```
(i.e. omit the trailing "/" after "sdd1" - Ciego, please fix this line in your how-to)

mb26 - Not sure what to say, but please be sure you type "umount" and not "unmount".

---

### Post by sg333 on 2007-02-03
I changed the code but it says it cannot find 'usbdrive' or the '/mnt/ubuntu/etc/fstab'

Thank you for your help.

---

### Post by NobodySpecial on 2007-02-03
What does
```
fdisk -l
```
show you?  Does it refer to sdd1 or to something else?

Also, when you get errors in the terminal, tell us which command the error followed.  You listed several commands.  After which one did it fail?

---

### Post by sg333 on 2007-02-03
It refers to it as 'sdd'

> cp: /mnt/usbdrive/config/fstab: no such file or directory

everything seems to work until I try to copy the fstab file.

---

### Post by mb26 on 2007-02-03
thanks nobodyspecial, i was typing unmount, i could have sworn thats what it said but oh well.

i am also having trouble around the mount /dev/sdd1/ /mnt/usbdrive bit, (for me the 'usb drive' is down as sdc? (so i put sdc1).. [why would that be?].[fyi i'm using an ipod as usb.. should be ok?]
and anyway, it says that i need to specify the filesystem or something (sorry not more specfic!)
i keep getting 'file exists' (or similar) when doing MKDIR stuff too.

---

### Post by NobodySpecial on 2007-02-03
mb26 - 
Again, do NOT type "mount /dev/sdd1/ /mnt/usbdrive" - it has one "/" too many!

Type:
```
mount /dev/sdd1 /mnt/usbdrive
```

or instead of sdd1, substitute whatever you saw under "fdisk -l"

sg333 - That error seems to mean you weren't able to properly mount the usbdrive.  Try the command I listed above in this post.

---

### Post by mb26 on 2007-02-03
i see, thanks.. note to Ciego as the extra "/" was in the guide! (will try soon..)

---

### Post by joedachs on 2007-02-05
Ok, I got to the beginning of step 5 w/ no problems.  but the link in step 5 does not work. :confused:  I substituted with:  ......"0.3.3.1ubuntu1_all.deb" at the end of the command  for both the second and third commands which seemed to work.  (is that file an ok alternative??)
I got to the reboot and did that, but i got the kboot prompt and could not go forward from there after the reboot without the live cd.  :mad:   I will try the : "umount /mnt/root"   and see if that works

I tried to move ahead anyway and put the cd back in and rebooted.  I then found out that the : fdisk -1 command brought up a bunch of stuff I did not understand so I did not know what my usb drive was called.   I tried multiple options that looked like they might have been it but i was told there was no such disk or file or something like that ...i dont remember the specifics.   maybe i was adding the extra "/" i will try again without it.
It these fixes don't help anyone have any other ideas come to mind?

also, my fstab file i renamed, but it still is showing as a text file, is that right as long as the actual file _name_ is "fstab" and not fstab.txt?

                                         First time linux user- not at all a computer know-how
                  Any help greatly appreciated!:) 
                                            Thanks,
                                 Joseph S.

---

### Post by NobodySpecial on 2007-02-05
joedachs - do you mean this command:
```
wget http://archive.ubuntulinux.org/ubuntu/pool/main/d/debootstrap/debootstrap_0.3.3.0ubuntu7_all.deb
```

It works perfectly.  Try to cut and paste into the terminal now.  The problem might be that you mis-typed it, which is VERY easy to do when you have to manually type it onto the PS3.  It certainly took me more than one try to get it right.

You might want to try it again.

---

### Post by joechoes on 2007-02-05
Nobody special- this is joedachs I had trouble logging in so i had to re-register.

That is the line, but when i printed the directions they did not show it with the ".deb" at the end, that is probably all it is!  I did not know that it scrolled to the right because i was looking at a printed copy.  so I figured my printed directions had to be right.

                           I was typing just "all" at the end.
Thanks, nobody special

Joseph S.

---

### Post by Ciego on 2007-02-05
> **joedachs said:**
> 

also, my fstab file i renamed, but it still is showing as a text file, is that right as long as the actual file _name_ is "fstab" and not fstab.txt?


You will need to remove the file extension.  This file is very important for mounting all of your file systems and Linux is looking specifically for a file named "fstab" with no extension.  


Another note ... I changed the guide by removing that extra "/"

---

### Post by Achetar on 2007-02-05
I am hoping to get a PS3 when the BestBuy near us gets some more in stock. Are there any side effects of reformatting to Ubuntu??? Can i play PS3 games in the Ubuntu?? Can someone  give me some specifics on what i can/can't do with Ubuntu on the PS3?

---

### Post by joechoes on 2007-02-05
Ok, adding ".deb" to the end worked.

My current problem is this:  when I get to the reboot where i am supposed to remove the cd i get to kboot and am stuck.

I tried "umount /mnt/root" and that did not help.  I get teh reply: "couldn't umount /mnt/root: Invalid argument"   and then it keeps repeating: " kboot : g ..."

---

### Post by Ciego on 2007-02-05
> **joechoes said:**
> Ok, adding ".deb" to the end worked.

My current problem is this:  when I get to the reboot where i am supposed to remove the cd i get to kboot and am stuck.

I tried "umount /mnt/root" and that did not help.  I get teh reply: "couldn't umount /mnt/root: Invalid argument"   and then it keeps repeating: " kboot : g ..."

OK ... first, make sure that something is mounted at /mnt/root
```
$ ls -al /mnt/root
```
If that does't return anything then there is nothing mounted at root to unmount.  If that is the case, then there was a problem when labeling your drives. 

Is there any output from that command?

---

### Post by joechoes on 2007-02-05
it says: "cannot access /mnt/root: No such file or directory"

---

### Post by Ciego on 2007-02-05
> it says: "cannot access /mnt/root: No such file or directory"

This means that it is not mounted in the first place ... just continue on with the instructions.  You should still be able to continue without this command.  You will need to relabel the partition when you are finished though so that kboot will automatically mount the root partition.  

To relabel a partition
```
$ e2label /dev/sda3 "/"
```

---

### Post by Ciego on 2007-02-05
After you relabel the drive you can check the label 
```
$ e2label /dev/sda3
```

It should just show a backslash

---

### Post by joechoes on 2007-02-05
I reformatted my ps3 hard drive (full format), and burnt a new cd at 1x.

If I get stuck again (i am expecting I will at the same spot) I will relabel the drive.  
I am having fun trying to get it working though.:) 
I think I am going to look for a "programming linux for dummies" book!

Thanks for the help guys, I'll let you know how it turns out this time!

Oh yeah, I saved the "fstab" and "xorg.conf" files as rich text- will that work, if not what type of file should they be if not any kind of text?   :confused: 
 
Thanks,
 Joseph S.

---

### Post by Ciego on 2007-02-05
I do not use Windows so I cannot help you there.  You can actually make the files in linux after you have it installed but you will have to type out all of the information.  This shouldn't be a big deal for the fstab (I typed it out) but you have to make sure that you have no mistakes.

---

### Post by Geta-Ve on 2007-02-06
I am fairly new to all of this but when I am at step 5, the wget part, I input the address correctly yet it comes up as a failure when resolving the address.  Something about the address resolution.

I attribute this to it not picking up my net signal however I am on the net as we speak on my ps3 using gentoo. I had went in to the network options and found 2 things, one saying local host, the other said 127.0.0.8  I deleted the latter and will attempt step 5 once more. I am thinking it was just reading the wrong network setting.

Thanks for all the help you are able to provide! it is much appreciated. By the way, this Gentoo is pretty neat. ;)

---

### Post by DarthStrydre on 2007-02-06
Rich text will not work. It is a human readable markup language (like HTML, but not) that would insert formatting tags sufficient to make the files unusable as configuration files.

On another note... I found that my sound problems in Xubuntu had to do with user permissions to access the sound card. One has to enable access in "Users and Groups" in the system settings menu. May as well add the capability to mount external drives, use the cd drive, etc while in there.

Also, the system updates at least currently sould be avoided. At least in Xubuntu, one of the updates seems to break the ability to automount devices. I think I notices a udev update, which might be the culprit.

Even though sound now works in some programs, others still have troubles, even though they are using the same interfaces. I still dislike sound in Linux :-P

---

### Post by mb26 on 2007-02-06
> **Achetar said:**
> I am hoping to get a PS3 when the BestBuy near us gets some more in stock. Are there any side effects of reformatting to Ubuntu??? Can i play PS3 games in the Ubuntu?? Can someone  give me some specifics on what i can/can't do with Ubuntu on the PS3?You can't run the ps3 games from ubuntu (AFAIK). it is sepatate from the playstation's XMB; which launches the games etc. to play games u have to exit ubuntu and go to the xmb- it will then be like a regular ps3. 
the advantage is u have a full OS u can do what u like (with a bit of tweaking).. play divx, use word processor, bittorrent, better internet browser, email.. all that stuff. u can't play 3d games as the graphics card isn't supported yet.. and sound is a bit 'maybe'.. hopefully it will be sorted properly soon.

ciego- u need to add in that u need to put type "exit" before "$ mnt/ubuntu/boot/vmlinux initrd=mnt/ubuntu/boot/initrd.img root=/dev/sda3" (or "reboot"). Also, the ^M issue highlighted doesn't seem to be an existant issue-- i made the files using XP and they didn't show up with ^M at the end of the lines with nano. (also ur guide doesn't actually say 'when' to change them anyway).
In addition, the bit around the video mode is pretty confusing; it would be better to put the chart before what it says to type (refers to a 'chart earlier' which isn't there). i wasn't sure whether it was a case of type "+128" at the end of the mode for fullscreen, or add the 2 numbers (correct). a mention about overscan re:SDTVs would also be good.

more general points; would it be possible to make a (or several) batch-type file which would do most of this?.. it is very difficult typing so much accurately on regular TVs.
also suggesting downloading all the stuff that it DLs with the ps3 beforehand would be quite useful for many people, and then burning it to CD or putting it on a usb drive.
also the more people can do in a GUI (either previous OS or ps3(k)ububtu), the better. copy and paste is pretty useful here.. so if its possible to load the GUI quicker, or do more on the PC.. that would be better.

questions:
-is there some way i can get it to fill the screen of my CRT tv?
.. 'normal' mode leaves a large border around everything, and fullscreen looses a lot due to overscan.
-are there any tweaks to optimise desk space for people with SDTVs? eg. i'd like the top and bottom bars in ubuntu to auto-minimize!
- how do i sort the sound out? (!!)
-.. and how to i access (the root of) a drive? (eg i can get to sdc2, but it won't let me open it)

posting from PS3 :), thanks.

---

### Post by Geta-Ve on 2007-02-06
Well I fixed the internet issue, was just a matter of deleting the 127-etc from the network window.

However I got stuck somewhere else. In step 5 right after you run the debootstrap

instead of typing **$cp /boot/* /mnt/ubuntu/boot**    I had typed **$cp /boot* /mnt/ubuntu/boot ** - which alternatively caused it to omit the boot directory.

I only realized when I went to copy the **kernel-genkernel** and it wouldn't find the file.

so I tried going back to the **sbin** directory by typing **$cd /usr/sbin** but that didn't work (probably had to type **/tmp/usr/sbin **?)  So instead I typed **$cd /sbin **  and that worked. I redid the **$cp /boot/*** command and went from there. I think it seemed to work alright, if I remember correctly there was a message of some sort that didn't look proper, but I went ahead anyways and rebooted.  

EDIT: The error that came up said not enough space on the device. or something similar. Meaning it couldn't copy the files because there wasn't enough space or some such thing.

At the **kboot **using the **$umount /mnt/root**  didn't work at all, a message saying it was an invalid argument came up. So I attempted to skip that and went on to the **mkdir **and **mount** commands, but when mounting the the **/mnt/ubuntu** dir it said it didn't exist.

I tried **$cd /mnt/ubuntu**   but the directory didn't exist. 

So that is as far as I got, I am now reformatting with a FULL format instead of quick and I am going to start from scratch see if I can get it working again.


A question for you, does quick or full format matter? And does it matter if my USB drive is my Ipod shuffle? (there are a few other folders on the ipod then just the ones specified in the guide. Should the only things on the ipod be the folders and files specified in the guide?

Thanks!

EDIT2: also a request that would most likely take too much of your time, but would it be possible to give a short description of what each of the commands are doing. more or less. or at least the more obscure ones like $sudo -s, or the zcat/ar -xf lines.  And perhaps explain that (from what I understand) SDA refers to a device. either the cdrom or the hdd.. I am not really sure which.

Apart from that I am finding the guide to be very helpful, and pretty good for newcomers though if I had no dos experience I probably would not be able to make heads or tales of anything. :p

---

### Post by Ciego on 2007-02-06
> **Geta-Ve said:**
> Well I fixed the internet issue, was just a matter of deleting the 127-etc from the network window.

However I got stuck somewhere else. In step 5 right after you run the debootstrap

instead of typing **$cp /boot/* /mnt/ubuntu/boot**    I had typed **$cp /boot* /mnt/ubuntu/boot ** - which alternatively caused it to omit the boot directory.

I only realized when I went to copy the **kernel-genkernel** and it wouldn't find the file.

so I tried going back to the **sbin** directory by typing **$cd /usr/sbin** but that didn't work (probably had to type **/tmp/usr/sbin **?)  So instead I typed **$cd /sbin **  and that worked. I redid the **$cp /boot/*** command and went from there. I think it seemed to work alright, if I remember correctly there was a message of some sort that didn't look proper, but I went ahead anyways and rebooted.  

EDIT: The error that came up said not enough space on the device. or something similar. Meaning it couldn't copy the files because there wasn't enough space or some such thing.

I would guess that your command was attempting to copy files to the CDROM which isn't possible.  Make sure that you have the copy location correct.
> 
At the **kboot **using the **$umount /mnt/root**  didn't work at all, a message saying it was an invalid argument came up. So I attempted to skip that and went on to the **mkdir **and **mount** commands, but when mounting the the **/mnt/ubuntu** dir it said it didn't exist.

Sounds like you made a mistake when making the file system ... specifically, labeling it.  If it said that the directory didn't exist ... right after you created it ... then you must have typed something incorrectly.
> 
I tried **$cd /mnt/ubuntu**   but the directory didn't exist. 

It didn't exist because your partitions were not mounted.
> 
So that is as far as I got, I am not reformatting with a FULL format instead of quick and I am going to start from scratch see if I can get it working again.


A question for you, does quick or full format matter?

I did the quick one so I guess it doesn't matter much.


It seems like you are having some problems here.  I would suggest starting over and following the instructions very carefully.  Try not to get in a hurry because when that happens, you will make very small mistakes typing that will make a very big difference.  I have not tried it yet, but you could probably do all of this from inside the Gentoo GUI by copying and pasting from the browser.  If you do it that way, you won't have to worry about typing mistakes ... unless I made them ;-)

---

### Post by Geta-Ve on 2007-02-06
If doing it inside Gentoo, would I be using the terminal? And would I still need to use the $sudo -s command before going ahead?

However would I still need the $/etc/init.d/xdm stop line? or part of it rather.

I guess I will be the first to try it from the GUI. 

One other thing the quick format, will that get rid of any traces of the otheros and such? I assume so but I just want to know if I make another mistake whether I have to full format each time... lol

Thanks for the speedy reply, it is much appreciated. Not that I can do anything for another 2 hours. haha

---

### Post by Ciego on 2007-02-06
> **Geta-Ve said:**
> If doing it inside Gentoo, would I be using the terminal? And would I still need to use the $sudo -s command before going ahead?
Yes ... to both
> 
However would I still need the $/etc/init.d/xdm stop line? or part of it rather.

Noooooo ... lol ... that will kill your GUI
> 
I guess I will be the first to try it from the GUI. 

Probably so ... hope it works.
> 
One other thing the quick format, will that get rid of any traces of the otheros and such? I assume so but I just want to know if I make another mistake whether I have to full format each time... lol

You should not even have to reformat now but if you are too lost (or just new enough to Linux that you cannot figure it out yet ... don't worry it gets easier) it may be a good idea.  The format should get rid of everything besides the PS3 files. I would back up your game saves though.

---

### Post by joechoes on 2007-02-06
Although I am already the most needy person on here.. I have two more questions before attempting this for a final go.

1. When creating the partitions and the instructions say (default)<enter> do i just click enter or do I type the default number shown?

2. After the second reboot do I type "umount /mnt/root" from the "kboot" prompt or should I be seeing a different prompt?

Thanks again,  If it doesnt work this time I will leave yall alone!):P

---

### Post by Ciego on 2007-02-06
> **joechoes said:**
> Although I am already the most needy person on here.. I have two more questions before attempting this for a final go.

1. When creating the partitions and the instructions say (default)<enter> do i just click enter or do I type the default number shown?
Just hit the enter key ... the default value will be chosen
> 
2. After the second reboot do I type "umount /mnt/root" from the "kboot" prompt or should I be seeing a different prompt?

It is the kboot prompt

> 
Thanks again,  If it doesnt work this time I will leave yall alone!):P
Hey ... don't give up ... at least you are trying.  I have a feeling this will be much easier with Feisty.  I think we can make a live CD with little effort since the kernel will support the PS3 out of the box.

---

### Post by Geta-Ve on 2007-02-06
> **joechoes said:**
> Although I am already the most needy person on here.. I have two more questions before attempting this for a final go.

1. When creating the partitions and the instructions say (default)<enter> do i just click enter or do I type the default number shown?

2. After the second reboot do I type "umount /mnt/root" from the "kboot" prompt or should I be seeing a different prompt?

Thanks again,  If it doesnt work this time I will leave yall alone!):P

1. just hit enter (almost sure this is correct)

2. from what I could tell you do it all from the kboot. 

and thanks again ciego! You are most most helpful and understanding :p

---

### Post by joechoes on 2007-02-06
Well, I don't know what I did, but it wasn't goood.:( 

when im trying to type commands I keep getting interrupted with the followin:

"end_request: I/O error, dev sr1 sector 8484"    repeats itself a gazillion times. (ony the digits at the end change.

Anyone wanna buy an almost new ps3?:lolflag: :lolflag:

---

### Post by Geta-Ve on 2007-02-06
what devices are attached to your ps3?

looks to me like one of the devices are not functioning properly or perhaps not being recognized properly. either that or every time you try to input anything key stroke or mouse button click it is not receiving it correctly.

I would say if you have a mouse or keyboard or anything really attached to your ps3, mem cards, sd cards, mem sticks, controller, etc unplug all reboot  and try again.

That is all I can think of

---

### Post by Geta-Ve on 2007-02-06
Just a quick heads up, but right up to the end of step 5 can be done from the gentoo GUI. Too awesome, and super easy because of copy and paste, wish the rest would be this easy. will just have to go super slow.

Thanks again ciego

---

### Post by Geta-Ve on 2007-02-06
I am stuck again and this time I am unsure why. (as opposed to last time? lol)

When installing Alien everything goes well except at the end it gives a short error about **/dpkg/** either not being there or what not.

I tried moving forward 

[B]$ apt-get install alien
$ alien ps3pf_utils-1.0.9-2.ppc.rpm
$ alien vsync-sample-1.0.1-4.ppc.rpm
$ dpkg -i ps3pf-utils_1.0.9-3_powerpc.deb[/B]

at the **dpkg** part it says that the folder or directory does not exist.

I am unsure of how to proceed.

I didn't see anything previously about **dpkg** directory so I don't really know what the problem is. Should I manually make the directory? then reinstall alien? If so what commands do I put in exactly?  

**$ mkdir /tmp/dpkg**  ?

Thanks kindly for any help :)


EDIT: ok so I got that issue sorted out. However I put myself into a corner by playing around with the resolution numbers in the kboot.conf file. I went to change back but it says it is a read only file. not sure how to just overwrite the damn file :p or even delete it so I can create a new one.

---

### Post by Ciego on 2007-02-07
> **Geta-Ve said:**
> 

EDIT: ok so I got that issue sorted out. However I put myself into a corner by playing around with the resolution numbers in the kboot.conf file. I went to change back but it says it is a read only file. not sure how to just overwrite the damn file :p or even delete it so I can create a new one.

Make sure that you are using sudo.  If all else fails ... reboot and use these commands at the kboot prompt.

Use this to make sure that your file is there.  It should display its contents
```

$ cat /mnt/root/ubuntu/etc/kboot.conf

```
Then you can delete it with this
```

$ rm /mnt/root/ubuntu/etc/kboot.conf

```
Then you should be able to mount your usb drive and copy it back over (instructions in tutorial).  Just remember at this point /dev/sda3 should be mounted at /mnt/root so you will have to change some of the commands slightly.

---

### Post by joechoes on 2007-02-07
Ok, Ciego was right again.

I went into Gentoo on the live cd and found out that dev sr1 was my Usb flash drive (i have one of those goofy drives that tells the computer it's a cd drive)

I removed it when the problem (error I/O .......) occurred and the errors stopped. Now I need another usb drive so I can load the fstab and config files off it.

---

### Post by joechoes on 2007-02-07
Windows users!

I found out how to save fstab and config in notepad without the .txt extension (the renaming thing did not work for me. 

Copy and paste the text into notepad.  Click on -save as- and then type "fstab" with the quotes around it.  Typing the quotes in the file name is the magic trick.

Now if I just answer 30 more questions I can catch up to all the help i've had!:lolflag:

---

### Post by mb26 on 2007-02-07
is there any progress on the sound front?

..having no sound really kills ubuntu for the ps3 right now..

---

### Post by NobodySpecial on 2007-02-08
mb26 - I wish there was a solution to the sound problems.  I installed Ubuntu twice, ran updates, did what I could, still didn't work.

Now I installed Yellow Dog Linux and sound works PERFECTLY, right out of the box.  Of course, everything else is very challenging to get going.  You have to add Fedora repositories and YUM is very slow.  It really makes you appreciate Ubuntu when you try a different distro.

I wonder if using Feisty with the new kernel would help?  I really want Ubuntu back . . . .    :confused:

---

### Post by mb26 on 2007-02-08
NobodySpecial, your in luck! (i think).

perhaps now i can help u.. it is (or, atleast was for me) just a case of user permissions. this explains why people can get the drum sound before login.

goto system>administration>users settings>[Your user name]>properties>user privileges
and check the box next to 'use audio devices' (and some other stuff no doubt while ur at it).

i'm not sure if these were meant to be set before, but may have been lost with the change from the kubuntu desktop to ubuntu. (i know my keyboard settings were for example).

listening to an album as i type :)

now how about a way to get flash to work (would wine or something work?, just for those sites that need it)

---

### Post by NobodySpecial on 2007-02-10
mb26 - YOU rock!!!!  :guitar: 

Sound now works perfectly!  I did have to reboot to make the change take effect (although possibly logging out then in might have done it).

Ciego, please add this tip to your how-to, as I'm not the only one who had trouble with sound (DarthStrydre did, too).

As for the Flash issue, I'll be working on that today and post a solution as soon as possible.   :)

---

### Post by NobodySpecial on 2007-02-10
Here's a quick way to get Realplayer going (can play mp3, quicktime, windows media, etc):

In terminal:
```
sudo apt-get install libstdc++5
wget https://helixcommunity.org/download.php/1346/realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin
chmod +x realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin
sudo ./realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin

```
When prompted for a location to install RealPlayer 10, type: /usr/bin/RealPlayer
 When prompted to configure system-wide symbolic links, type "y". After that, accept the default prefix for symbolic links.

When clicking a link in Firefox and asked which program to play the file with, enter: /usr/bin/realplay

---

### Post by NobodySpecial on 2007-02-10
For Sun Java:
Download from IBM: [http://www-128.ibm.com/developerworks/java/jdk/linux/download.html]("http://www-128.ibm.com/developerworks/java/jdk/linux/download.html")
You will have to register (free).
Choose 32-bit iSeries/pSeries, J2SE5.0.  Download the TGZ version of the SDK.
The following instructions assume the latest version to download is "ibm-java2-sdk-5.0-4.0-linux-ppc.tgz" - modify the text below as needed.
In terminal:
```
sudo apt-get install libgtk1.2 libstdc++5 java-package
mv ibm-java2-sdk-5.0-4.0-linux-ppc.tgz ibm-java2-sdk-50-linux-ppc.tgz
make-jpkg ibm-java2-sdk-50-linux-ppc.tgz
sudo dpkg -i ibm-j2sdk1.5_1.5.0_powerpc.deb
java -version

```
The last command should give you a response: java version "1.5.0"
If not, type:
```
sudo update-alternatives --config java

```
To get working with firefox:```

ln -s /usr/lib/j2sdk1.5-ibm/jre/bin/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins
```
Restart firefox, go to test website: [http://serios.net/content/applets/viewinfoawt.php]("http://serios.net/content/applets/viewinfoawt.php")

Enjoy Java!

Now the bad news: There is no Flash version for PowerPC.  There are some "free" alternatives such as gnash, but they are said not to be very robust, won't work with sites such as Youtube.  The idea of using WINE as suggested by mb26 would be nice, but alas, wine will not work under PowerPC.

So the only solution I can think of to solve the problem would be to use RDP protocol from an x86 box on the network.  Once I get this going, I'll post again here.

---

### Post by NobodySpecial on 2007-02-10
Here are my two solutions for Flash:
1. X session via ssh
Besides your PS3, you likely have another computer on your LAN that is a standard x86 setup (and has Flash working).  On that box, enter into the terminal:
```
sudo apt-get install openssh-server
ifconfig eth0
```
That last command will tell you your LAN ip address.  Let's say it says "inet addr:192.168.1.101"

Now from your PS3, enter in the terminal:
```
ssh -X 192.168.1.101 /usr/bin/epiphany
```
This assmes that Epiphany is instaled on your x86 box.

You can try Firefox, but its sometimes buggy for some reason:
```
ssh -X 192.168.1.101 /usr/bin/firefox --sync
```

BIG disadvantage: No sound!  I'm not aware of any native protocol attaching two Linux desktops that would allow transmission of both sound and video in the way we want.

2. Seamless Windows via RDP
This assumes you have either a separate computer set up on your LAN running Windows, or Windows running in a virtual machine.  I have Windows running on a headless Linux server box (i.e. no monitor attached) which is running VMWare server. 

The How-To is here: [http://www.ubuntuforums.org/showthread.php?t=224212]("http://www.ubuntuforums.org/showthread.php?t=224212")

It takes some work, but is ultimately rewarding.  Not only can you run Flash, but most any elusive I-gotta-have-it Windows program.

Here is a screenshot of my PS3 Ubuntu desktop running Windows Explorer 7 with Youtube and Flash 9 playing in a window with FULL SOUND.
[IMG]http://123pichosting.com/images/97Screenshot2.jpg[/IMG]

---

### Post by 3vi1 on 2007-02-11
I'm not sure how anyone could have sound after doing only the instructions in the tutorial.  I followed them exactly, and have the same "no sound" problem as previous messages have described.

I installed the 64-bit asound and gstreamer libraries, but kmix still shows no mixers.  Toying with the sound options in system settings makes no difference.  Sound works fine under the PS3 OS.

Which module needs to be loaded for sound to work?  lsmod isn't showing me anything, for some reason.

I will investigate further... right now I'm upgrading from edgy to feisty.  I had read that the ps3 fixes had been included in the .20 kernel, so it seems like a good way to get to a kernel that I can re-compile to add vfat support.

-J

---

### Post by 3vi1 on 2007-02-11
Suggestion for the tutorial:

All of the spots where you open up terminal, do "sudo -s", then "/etc/init.d/xdm stop" can be bypassed by simply pressing Ctrl+Alt+F1.  this will switch you to a root prompt much faster.

Also, in step 6, you try to "mkdir /mnt/ubuntu/boot" again.  It should already exist from the last portion of step 4.

Thanks for the cool walkthru - it gave me the courage to try this and god only knows how much trial-and-error.

I still have to get sound working, and wait until someone comes out with the driver for wireless.  I got around the lack of wireless by connecting the PS3 to my wife's laptop with a crossover cable, then starting ICS for her wireless connection.

I'm writing this from Kubuntu on the PS3 right now - waiting for apt-get to finish the feisty dist-upgrade.

-J

---

### Post by 3vi1 on 2007-02-11
Feisty dist-upgrade worked; but I am having problems recompiling the kernel.  I'm getting the following error when recompiling 2.6.23, and I can't find the repositories that are needed for the pre-built ubuntu ps3 kernel images.  :(  Oh well...  Just glad it's working as well as it does for now.

(lots and lots of compiles)...
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
arch/powerpc/platforms/built-in.o: In function `.dump_fir':
ras.c:(.text+0x8ad4): undefined reference to `.cbe_get_cpu_pmd_regs'
ras.c:(.text+0x8ae4): undefined reference to `.cbe_get_cpu_iic_regs'
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.20'
make: *** [debian/stamp-build-kernel] Error 2

There's probably some pre-req option that I didn't enable in my config that's preventing the kernel compile from working... but I'm not so familiar with the kernel as to have a good idea what it might be.

-J

---

### Post by 3vi1 on 2007-02-11
Well... after enabling some more Apple/PowerPC/Cell options, I got the kernel to compile.

Unfortunately... it hangs.  I had to redirect vmlinux to the Gentoo version to boot this time. :\

My vmlinux is WAY smaller than the Gentoo version... so something is probably still missing....  Oh well... will play with it some more.

-J

---

### Post by mb26 on 2007-02-11
has anyone managed to get any form of external hard drive to work?
it worked with kboot but no i just get errors;
[approx] 'filesystem [vfat or ntfs] unknown'.

also, a way to play .flv streaming with VLC would be quite a good solution. i can watch the files (downloading with 'videodownloader' extension or 'videobookmarklet', but u have to wait for the videos to download first.

anyone else had auto-ejecting CDs?

..i haven't managed to get DVDs to play (using VLC) either yet? (installed libdvdcss..)

running fullscreen and putting bars at the unvisable part of the side, and making the top+ bottom bars large has been the best i've got for fullscreen desktop so far too..

---

### Post by Adiuvo on 2007-02-11
OK, first off, I'm new to Linux so don't get mad at me if I sound stupid :p

Anyway, I'm running my PS3 on a 480i TV (will get a better one soon), and I'm stuck at step four. Whenever I press tab, I get no resolutions to choose from, so I can't boot into Gentoo. 

I have tried burning the Gentoo image on a CD and a DVD, but nothing worked.
Please help me lol.

BTW: I can get into kboot, and I do know how to go back to the game-os.

---

### Post by mb26 on 2007-02-11
> **Adiuvo said:**
> OK, first off, I'm new to Linux so don't get mad at me if I sound stupid :p

Anyway, I'm running my PS3 on a 480i TV (will get a better one soon), and I'm stuck at step four. Whenever I press tab, I get no resolutions to choose from, so I can't boot into Gentoo. 

I have tried burning the Gentoo image on a CD and a DVD, but nothing worked.
Please help me lol.

BTW: I can get into kboot, and I do know how to go back to the game-os.
i have a 480i tv (well 576i, but still) and had no problems regarding the screen.
it should come up with the option 'gentoo480i' after a few presses of tab on the kboot menu.
did u use the download linked in this guide?.

---

### Post by 3vi1 on 2007-02-11
> **mb26 said:**
> has anyone managed to get any form of external hard drive to work?
it worked with kboot but no i just get errors;
[approx] 'filesystem [vfat or ntfs] unknown'.
.

This is one of the reason's I'm working on recompiling the kernel.  Apparently the Gentoo kernel from the liveCD does not include vfat support.

The only solution is to recompile your own kernel with vfat support enabled.  Unfortunately, it doesn't look like feisty has everything needed to support the ps3 fb (just a guess, based on where the new kernel hangs, and the fact that I did not see any PS3-specific video devices in the config).  There are other ps3-specific options though:


[IMG]http://www.eternaldusk.com/images/screenshots/snapshot3.png[/IMG]
[IMG]http://www.eternaldusk.com/images/screenshots/snapshot1.png[/IMG]

If I figure it out, I'll be sure to post a link to my working .config file.  But, I don't have a whole lot of time to waste on it, so if anyone else figures it out first - feel free to illuminate me with the solution. 

-J

---

### Post by 3vi1 on 2007-02-11
> **Adiuvo said:**
> Whenever I press tab, I get no resolutions to choose from, so I can't boot into Gentoo. .

Make sure you already have the CD in the drive at that point.  If you don't, you won't get any resolution options.

-J

---

### Post by Adiuvo on 2007-02-11
> **mb26 said:**
> i have a 480i tv (well 576i, but still) and had no problems regarding the screen.
it should come up with the option 'gentoo480i' after a few presses of tab on the kboot menu.
did u use the download linked in this guide?.

Still didn't work. And yes, I used the download in the guide.

Anyway, I was supposed to burn the file called image.squashfs?
Also, does it matter if I changed the extension to .iso so I could burn it?

---

### Post by Adiuvo on 2007-02-11
> **3vi1 said:**
> Make sure you already have the CD in the drive at that point.  If you don't, you won't get any resolution options.

-J

I do.
Not that dumb lol.

---

### Post by 3vi1 on 2007-02-11
> **Adiuvo said:**
> Still didn't work. And yes, I used the download in the guide.

Anyway, I was supposed to burn the file called image.squashfs?
Also, does it matter if I changed the extension to .iso so I could burn it?

The problem appears to be that you did not burn the proper liveCD iso.  The link in step one points directly to the ...ppc64-beta.iso file, you should not have had to rename anything.

-J

---

### Post by Adiuvo on 2007-02-11
Ah, I figured out what I did wrong. I did download it, but since I had WINRar set to recognize it as a compressed image, I unrared it, thinking I had to.

Lol, I'm so dumb :p
Thanks for the help.

---

### Post by 3vi1 on 2007-02-11
> **Adiuvo said:**
> Ah, I figured out what I did wrong. I did download it, but since I had WINRar set to recognize it as a compressed image, I unrared it, thinking I had to.

Lol, I'm so dumb :p
Thanks for the help.

Could happen to anyone.  :)  I didn't have to worry about it because my main system runs Kubuntu.

Speaking of which, the walk-thru could probably use some extra instructions in step 2:  to show Linux users how to get the files out of the add-on iso by mounting it as a cloop device, which is what I did.

-J

---

### Post by mb26 on 2007-02-12
would it be possible to just add vfat (and nfts) support to the edgy kernel its using now? (not too bothered about updating it yet, i just want it to work with everything first.)
..if so how as i don't even know where to start..

---

### Post by 3vi1 on 2007-02-12
> **mb26 said:**
> would it be possible to just add vfat (and nfts) support to the edgy kernel its using now? (not too bothered about updating it yet, i just want it to work with everything first.)
..if so how as i don't even know where to start..

When you complete the walkthru, you won't be using the Edgy kernel.  Do a "uname -a" and you will see that you're still using the Gentoo ps3 kernel.  I don't believe it's possible to add filesystem support unless it's compiled into the kernel (from what I've observed in .config).

Recompiling the Edgy kernel is not an (easy) option, because the additions needed to support the PS3 were not added to mainstream Linux until 2.6.20, whereas Edgy uses 2.6.17.  So, you would have to merge in the patches needed for PS3 support.  It's possible to do... but upgrading to the Feisty kernel would seem to be the easier option.

I left the kernel recompiling again last night when I went to bed, this time with almost everything enabled (as a loadable module, when possible).  I'll test when I get home tonight to see if it gets me past the freeze-up I was experiencing with the Feisty kernel.

Other than the kernel, my system is now 100% Feisty.  It seems completely stable so far.

-J

---

### Post by Ciego on 2007-02-12
Looks like I have some more editing to do here.  I will try to add some of the suggestions today if I get a chance.

---

### Post by 3vi1 on 2007-02-12
WOOT - I just updated my apt sources list for Feisty and found the pre-built image is now in one of the repositories.  I'll update and see how it turns out.

[IMG]http://www.eternaldusk.com/images/screenshots/snapshot4.png[/IMG]

---

### Post by 3vi1 on 2007-02-12
Drat...  the new kernel boots a tiny bit further than the one I had compiled, but then gives an error about VFS not synching and the inability to mount the root filesystem.  I'll have to wait until after work to troubleshoot  :\

-J

---

### Post by Ciego on 2007-02-12
EDIT: I didn't mean the above post was good news ... you slipped another one in while I was typing.


That is good news.  I have a feeling Feisty will be much better for PS3 users since it is likely that they will be new to Linux.  I have been working on trying to get the herd 3 live cd to boot up on the PS3 ... do you know if the 2.6.20 kernel is on that CD yet?

---

### Post by 3vi1 on 2007-02-12
I'm not sure which kernel is on the CD at this time... I did the dist-upgrade thing to get to Feisty, so did not investigate.  It certainly would be desirable for new users to be able to directly install it though.  I'd bet the next release will have the PS3 stuff in... at which point we could use it more directly and avoid Gentoo completely.

Back to the present:  The pre-built .20 image is halting with the following message at bootup (after kboot):

> UDF-fs: No VRS found
No filesystem could mount root tried:  ext3 vfat iso9660 udf
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)

Any idea why it wouldn't be mounting it?  I've had no previous experience with kboot, so I'm figuring out this two-step loading process as I go along.

Our root partition is ext3, so that can't be the problem (sidenote: it's good to see that the ubuntu kernel does have vfat support compiled-in).

I changed fstab to use /dev/sda3 instead of a LABEL=/, thinking it might simply be looking for root in the wrong place - but it made no difference.

Maybe it can't mount it because it's already mounted by kboot?

Gotta think about this one some more...

---

### Post by Ciego on 2007-02-12
I think that you are correct when you said that it will not mount because kboot has already mounted it.  You might try to unmount the partition and run the kernel from the kboot prompt using the command line rather than the kboot.conf.

---

### Post by 3vi1 on 2007-02-12
> **Ciego said:**
> I think that you are correct when you said that it will not mount because kboot has already mounted it.  You might try to unmount the partition and run the kernel from the kboot prompt using the command line rather than the kboot.conf.

I was almost sure that was going to be it, but I gave it a shot a few moments ago and get the same error.  I'll have to think about it some more.

For now, I've configured multiple option in kboot.conf - so I can boot the Gentoo kernel until I figure out what's going on with the Ubuntu version.

-J

---

### Post by Adiuvo on 2007-02-12
Great, now I have more problems....

OK, now I'm at step five, and wget command won't work. So I went into the gentoo GUI, used Firefox, and got the file from there then saved it in the tmp folder.

Everything's going fine, the ls command shows it's there still, and then I type the ar -xf thing and it doesn't work the first time, but then it works. So, then I type zcat < data.tar.gz | tar xv and it tells me the files aren't there. So then I type zcat < data.tar.gz, ignoring the l tar xv part, and get a massive wall of text. I figure that's what's supposed to happen, so then I type  tar xv, but it just sits there, doing nothing....
Yeah, where did I mess up?

---

### Post by 3vi1 on 2007-02-12
I was able to eliminate the error by adding "root=/dev/sda3" to the list of vmlinux parameters.

Butttt....  the kernel still hangs at pretty much the same spot.  I just get no error now.

I think I'll try to compile my own again tonight to see if I get any different results with the new source package.

-J

---

### Post by 3vi1 on 2007-02-12
> **Adiuvo said:**
> Great, now I have more problems....

OK, now I'm at step five, and wget command won't work. So I went into the gentoo GUI, used Firefox, and got the file from there then saved it in the tmp folder.

Everything's going fine, the ls command shows it's there still, and then I type the ar -xf thing and it doesn't work the first time, but then it works. So, then I type zcat < data.tar.gz | tar xv and it tells me the files aren't there. So then I type zcat < data.tar.gz, ignoring the l tar xv part, and get a massive wall of text. I figure that's what's supposed to happen, so then I type  tar xv, but it just sits there, doing nothing....
Yeah, where did I mess up?

I would go back and give wget another try.  I'm not sure how you used Firefox to get it, but if you opened it then used Save As, you lost a lot of binary data (Firefox would treat it as ASCII text).  That would explain why you could not pipe it through tar; it was no longer a valid tar.gz file.

The reason the tar command just sits there is that, if you're not piping a file to it, it expects input from stdin (the keyboard).  You can't split up commands that are piping their output into one another like that.

So, give it another try with wget.  If it produces an error, post it here and I'll try to help you out.

---

### Post by 3vi1 on 2007-02-12
> **3vi1 said:**
> I was able to eliminate the error by adding "root=/dev/sda3" to the list of vmlinux parameters.

Butttt....  the kernel still hangs at pretty much the same spot.  I just get no error now.

I think I'll try to compile my own again tonight to see if I get any different results with the new source package.

-J

Well:  at least now I understand why this was happening.  I looked at the config file they installed with the image package:  It has an "Initial kernel command string" of "root=/dev/sda1".

One mystery solved.  Now, I just need to figure out how to get it to produce more verbose output so that I can figure out what it's hanging on now.

-J

---

### Post by Adiuvo on 2007-02-12
Just tried wget, and this time it worked, but the zcat thing still won't.

Like before, it just says the files aren't there.

---

### Post by 3vi1 on 2007-02-12
> **Adiuvo said:**
> Just tried wget, and this time it worked, but the zcat thing still won't.

Like before, it just says the files aren't there.

Hmmm... I just did it from here, copying and pasting the lines from the walk-thru and it worked....

Do you see a file named "data.tar.gz" in the current (/tmp) directory?  Are you absolutely sure you're typing the zcat command exactly as described (spaces and all)?

If you would, type the command/results here verbatim.  It's probably a simple thing that just needs another pair of eyes on it.

---

### Post by 3vi1 on 2007-02-12
Just a note to anyone else recompiling the kernel for this thing:  As of today, the ubuntu 2.6.20 sources require DTC to compile some of the Playstation files.

I had never heard of it before, but I tracked it down, compiled and installed it (there is no real make install, you have to copy the executable to your path).

You will need to use git-clone to checkout the source here: git://www.jdl.com/software/dtc.git

There is also a source tarball on the homepage ([http://dtc.ozlabs.org/)](http://dtc.ozlabs.org/)), but it does *not* support the -b option (physical boot cpu) needed to build the playstation files.

Compile with "make" (no configure).  You will need bison and flex installed to compile it.

---

### Post by Adiuvo on 2007-02-12
> **3vi1 said:**
> Hmmm... I just did it from here, copying and pasting the lines from the walk-thru and it worked....

Do you see a file named "data.tar.gz" in the current (/tmp) directory?  Are you absolutely sure you're typing the zcat command exactly as described (spaces and all)?

If you would, type the command/results here verbatim.  It's probably a simple thing that just needs another pair of eyes on it.
Yeah, the data.tar.gz thing is there.

It says:
l.gz: No such file or directory.
tar.gz: No such file or directory.
xv.gz: No such file or directory.

The command I'm typing is zcat < data.tar.gz l tar xv.

The l is supposed to be a lowercase L right?

---

### Post by Ciego on 2007-02-12
> **Adiuvo said:**
> Yeah, the data.tar.gz thing is there.

It says:
l.gz: No such file or directory.
tar.gz: No such file or directory.
xv.gz: No such file or directory.

The command I'm typing is zcat < data.tar.gz l tar xv.

The l is supposed to be a lowercase L right?

That isn't the letter "L" it is that long vertical line that is above the "\" on the keyboard.   "|"

Problem solved  :-)

---

### Post by 3vi1 on 2007-02-12
> **Ciego said:**
> That isn't the letter "L" it is that long vertical line that is above the "\" on the keyboard.   "|"

Problem solved  :-)

To add to what Ciego said:  That's called the "pipe" symbol - it pipes the output of one command into another command as an input stream.

-J

---

### Post by 3vi1 on 2007-02-12
Ohhh.... I'm kicking myself for not figuring this one out sooner.  I decided to fix the broken audio tonight... since that's my only real issue at this point.

30 minutes into the investigation, I figured out IT WAS AN AUTHORITY ISSUE.  At the end of the walkthru, the normal user account won't be a member of the "audio" group, and therefore won't have access to /dev/dsp.

The people who weren't having a problem either added themselves to a bunch of groups, or were.... RUNNING AS ROOT!  (for shame on you!  :) ).

So, if Ciego would be so kind as to add "adduser YOUR_USER_NAME audio" to Step 8, we should not have any more confusion.

For those of you that already installed, just go to a command line and sudo the above command.  THEN LOG OUT (group membership will not change for already logged-in users).  When you log back in, you'll be fixed and have sound.

-J

---

### Post by 3vi1 on 2007-02-12
Also, Ciego - you may want to have them add their ID to "users".  I seem to recall that I couldn't write to /tmp and fixed that by adding the group when I was doing something else last night.

-J

---

### Post by 3vi1 on 2007-02-13
Here's another tip.  If you try to use "boot-game-os"... you might notice it doesn't work.

The reason is that the script depends on another script, "find-other-os-flash", that uses at least one bash-ism, yet the script specifies that it should be run by sh.  sh on Kubuntu will be using Dash, not Bash... so it will fail.

To fix it, open up /sbin/find-other-os-flash with your favorite editor and change the first line from: "#! /bin/sh" to '#! /bin/bash".

boot-game-os should work fine after that.

-J

---

### Post by joel1234567 on 2007-02-13
Hi, new to this whole ps3 linux install, and this forum. Thanks for all the great tips, and to Ciego for outlining the install!! I've been pulling my hair out trying to figure out how to get sound working- glad to see someone here figured out that problem!! (thanks mb26!)

Also- I hit that same problem last night as listed in the last post, when trying to run "boot-game-os". Fixed it instead by changing the "==" to "=". Should've thought to change the shell instead...

Another problem that I was seeing was a lot of errors when running applications from the terminal. I would see lots of messages about "uninitialized device 166". Although they didnt seem to be causing any problems, they were annoying. I found another post at [http://www.ubuntuforums.org/showthread.php?t=359091&highlight=device+168](http://www.ubuntuforums.org/showthread.php?t=359091&highlight=device+168) that attempts to solve the problem by removing all of the lines in the xorg.conf file that refer to the input devices called "wacom". I've commented out the necessary lines now but haven't rebooted yet- I'll do another post after...

One other MAJOR problem I cant seem to get around is listening to CD's. Is anyone able to do this? It causes me major headaches. I've tried a number of app's (kaffeine, sound juicer, kscd, etc) and nothing seems to work. Sometimes it refuses to mount or read the CD after several tries. Sometimes the CD player freezes (for example, in 'sound-juicer' this happens). Sometimes it will play, but the sound is really terrible. Then after a few seconds the app will either freeze, or spit out the CD, or sometimes it has even completely frozen the desktop and OS. Are other people able to do this? I'm not sure if it's a software or hardware issue at this point. If other people are able to do this without installing additional software then I'm starting to think that it may be hardware related...

---

### Post by NobodySpecial on 2007-02-13
> **joel1234567 said:**
> 
One other MAJOR problem I cant seem to get around is listening to CD's. Is anyone able to do this? It causes me major headaches. I've tried a number of app's (kaffeine, sound juicer, kscd, etc) and nothing seems to work. Sometimes it refuses to mount or read the CD after several tries. Sometimes the CD player freezes (for example, in 'sound-juicer' this happens). Sometimes it will play, but the sound is really terrible. Then after a few seconds the app will either freeze, or spit out the CD, or sometimes it has even completely frozen the desktop and OS. Are other people able to do this? I'm not sure if it's a software or hardware issue at this point. If other people are able to do this without installing additional software then I'm starting to think that it may be hardware related...

Your answer about playing music CD's comes from [Terra Soft:]("http://www.terrasoftsolutions.com/support/solutions/ydl_5.0/audio-cd.shtml")
> While system sound and .ogg files are well supported, playing and ripping audio CDs is at this time not functional. This is due to an incompatibility between the new Blueray drives and the existing Linux kernel and/or device driver. 

---

### Post by Ciego on 2007-02-13
> **joel1234567 said:**
> Hi, new to this whole ps3 linux install, and this forum. Thanks for all the great tips, and to Ciego for outlining the install!! I've been pulling my hair out trying to figure out how to get sound working- glad to see someone here figured out that problem!! (thanks mb26!)
I should have updated the HowTo with the fixes for this by now ... sorry about that.
> 
Also- I hit that same problem last night as listed in the last post, when trying to run "boot-game-os". Fixed it instead by changing the "==" to "=". Should've thought to change the shell instead...

I will have to add this also
> 
Another problem that I was seeing was a lot of errors when running applications from the terminal. I would see lots of messages about "uninitialized device 166". Although they didnt seem to be causing any problems, they were annoying. I found another post at [http://www.ubuntuforums.org/showthread.php?t=359091&highlight=device+168](http://www.ubuntuforums.org/showthread.php?t=359091&highlight=device+168) that attempts to solve the problem by removing all of the lines in the xorg.conf file that refer to the input devices called "wacom". I've commented out the necessary lines now but haven't rebooted yet- I'll do another post after...

I have noticed the same errors in the terminal ... if that solution works for you , let me know and I will edit the xorg.conf in the HowTo to correct the problem.  Please let me know what lines you commented out if that is the case.
> 
One other MAJOR problem I cant seem to get around is listening to CD's. Is anyone able to do this? It causes me major headaches. I've tried a number of app's (kaffeine, sound juicer, kscd, etc) and nothing seems to work. Sometimes it refuses to mount or read the CD after several tries. Sometimes the CD player freezes (for example, in 'sound-juicer' this happens). Sometimes it will play, but the sound is really terrible. Then after a few seconds the app will either freeze, or spit out the CD, or sometimes it has even completely frozen the desktop and OS. Are other people able to do this? I'm not sure if it's a software or hardware issue at this point. If other people are able to do this without installing additional software then I'm starting to think that it may be hardware related...
I haven't tried an actual audio CD yet ... tried mp3s but not the actual CD.  I will try this evening after work and let you know.

---

### Post by Ciego on 2007-02-13
> **NobodySpecial said:**
> Your answer about playing music CD's comes from [Terra Soft:]("http://www.terrasoftsolutions.com/support/solutions/ydl_5.0/audio-cd.shtml")

I wonder if this was one of the items that was addressed in the 2.6.20 kernel in the PS3 support additions.

---

### Post by joel1234567 on 2007-02-13
[QUOTE=Ciego] I have noticed the same errors in the terminal ... if that solution works for you , let me know and I will edit the xorg.conf in the HowTo to correct the problem.  Please let me know what lines you commented out if that is the case.[/QUOTE]

It did fix the problem. The exact text that gets commented out is documented well in the other post at [http://www.ubuntuforums.org/showthread.php?t=359091&highlight=device+168](http://www.ubuntuforums.org/showthread.php?t=359091&highlight=device+168) - it probably does a much better job at depicting this that I could do.

[QUOTE=Ciego] I haven't tried an actual audio CD yet ... tried mp3s but not the actual CD.  I will try this evening after work and let you know.[/QUOTE]

Sounds like from what I saw posted by NobodySpecial that maybe this is expected behavior. Phew! Glad to hear I just don't have some bad hardware.

---

### Post by Ciego on 2007-02-13
Whew .... I just added all of the changes that everyone has suggested.  If you haven't done so yet, I would suggest changing your xorg.conf, adding yourself to the user groups mentioned, and checking the change log in general.

---

### Post by Ciego on 2007-02-14
QJ.net just posted this on their PS3 page so hopefully we will have many more PSUbuntu users in the near future.

[http://ps3.qj.net/OS-tutorial-Ubuntu-Linux-installation-on-the-PS3/pg/49/aid/82832]("http://ps3.qj.net/OS-tutorial-Ubuntu-Linux-installation-on-the-PS3/pg/49/aid/82832")

I also saw this on Digg.

[http://digg.com/gaming_news/Installing_Ubuntu_Linux_on_the_PLAYSTATION_3]("http://digg.com/gaming_news/Installing_Ubuntu_Linux_on_the_PLAYSTATION_3")

---

### Post by Ciego on 2007-02-14
Fredtech created a PSUbuntu dedicated forum at [http://psubuntu.com/forum/index.php]("http://psubuntu.com/forum/index.php")

We are trying to make that a place to consolidate all of the PS3-Ubuntu related info that we can.  Come join Us!

---

### Post by NobodySpecial on 2007-02-14
Alternative Flash Solution

I have another idea how to get Flash 9 running through a remote desktop setup.  The problem is with sound.  Windows XP will send sound to Linux via RDP, but a Linux system won't send sound via VNCViewer.  One possible solution: FreeNX

FreeNX Server is very easy to install on your x86 machine.
```
sudo gedit /etc/apt/sources.list
```
Add these two lines then save the file:
```
deb http://seveas.imbrandon.com dapper-seveas freenx 
deb-src http://seveas.imbrandon.com dapper-seveas freenx
```
Get the server key and update:
```
wget http://seveas.imbrandon.com/1135D466.gpg -O- | sudo apt-key add - 
sudo apt-get update

```
Install FreeNX:
```
sudo apt-get install freenx openssh-server
```
Now your x86 machine is all set up as a server.

To install the cilent, simply set up the repository as above and:
```
sudo apt-get install nxclient
/usr/NX/bin/nxclient &
```
You can now access your server machine.
One BIG problem: The seveas repository does not have a PPC build of the NX Client.  I cannot another alternative.

Can anyone here figure out how to install FreeNX Client on the PS3?

Sources for the NX Client version 1.5 are available [here.]("http://www.industrial-statistics.com/info/nxclients?IndStats=bbf349f90a518f5a54f290e887d9c768")
Version 2 is available from [No Machine]("http://www.nomachine.com/download.php"), but version 2 has problems interfacing with the 1.5 server (although the Gentoo people apparently have found a work-around).

---

### Post by mb26 on 2007-02-15
joel1234567,
Your answer about playing music CD's comes from [here](http://ubuntuforums.org/showthread.php?t=272009). u don't have to mount audio CDs as they don't actually have a filesystem.. so follow what it says in the linky. (i was playing with VLC for what its worth)

---

### Post by mr.Q on 2007-02-15
Newb questions....

We will partition the 10GB portion of the hard drive as follows using fdisk.
LABEL PARTITION SIZE SYSTEM
1) boot /dev/sda1 256MB ext2
2)SWAP /dev/sda2 512MB swap
3) / /dev/sda3 the remaining space ext3

What if you want to partition 50 gb to ubuntu? Maybe this was answered somewhere already.

---

### Post by Ciego on 2007-02-15
> What if you want to partition 50 gb to ubuntu? Maybe this was answered somewhere already.
It shouldn't matter because you will be making the main file system last so it will just use the rest of the space.  The instructions should work either way.

---

### Post by DarthStrydre on 2007-02-15
I thought I had posted this earlier about the problems with VFAT.

In the Gentoo kernel, the drivers for VFAT and lots of other stuff are compiled as modules. While the Kernel will run without them accessible, it will not be full-featured.

In the install routine where you are copying the kernel and initrd, the last line ofthe following will solve everyone's vfat problems:

```
$ cp /boot/* /mnt/ubuntu/boot
$ cd /mnt/ubuntu/boot
$ cp kernel-genkernel-ppc-2.6.16-ps3 /mnt/ubuntu/boot/vmlinux
$ cp initramfs-genkernel-ppc-2.6.16-ps3 /mnt/ubuntu/boot/initrd.img
$ cp -R /lib/modules/* /mnt/ubuntu/lib/modules/
```

---

### Post by 3vi1 on 2007-02-16
I have finally been successful in booting my recompiled 2.6.20 Feisty kernel.  The trick was that the root and video parameters had to be set in the kernel - it doesn't seem to actually use the ones you supply on the kboot line.

[IMG]http://www.eternaldusk.com/images/screenshots/snapshot5.png[/IMG]

Now, my problem is that it seems to run the system out of memory by the time KDE loads up.  The hard drive never stops paging to swap.  I'm going to play with the other kernel options to see what I can discard, while leaving in the vfat support and a few other features not built into the Gentoo kernel.

-J

---

### Post by Ciego on 2007-02-16
> **3vi1 said:**
> I have finally been successful in booting my recompiled 2.6.20 Feisty kernel.  The trick was that the root and video parameters had to be set in the kernel - it doesn't seem to actually use the ones you supply on the kboot line.
-J

That doesn't sound good.  Are we going to have to recompile the kernel for every video setting and change kernels every time we want to switch?  I guess that this also means that we will not be able to run the standard Live CD either.

---

### Post by 3vi1 on 2007-02-16
I'm hoping that won't be the case.

It's possible that this is a bug in menuconfig, such that it putting default values in the config file even if you don't specify default bootloader kernel arguments.  I will have to do more testing to be sure... but I'm sure we will be able to work around it one way or another.

If I get time tonight, I'll try to rebuild a few different ways to see if I can determine why it's working the way it is.  I will submit a bug report when I have it nailed down.  It might have to wait until tomorrow though, cause I'm taking the wife to see Ghost Rider.  :)

Also, it looks like Fiesty Herd 4 was released today - so there may be quite a few changes/fixes.  I'm updating now.

---

### Post by mr.Q on 2007-02-17
I'm stuck. Please help a newb. I got to the end of step 5, went to reboot and then this happened. 

INIT: Switching to runlevel: 6
INIT: Sending processes the TERM signal
INIT: Sending processes the KILL signal
End request: I/O error on device sr0, logical block 1382
SQUASHFS error: sb_bread failed reading block 0xa77
SQUASHFS error: Unable to read page, block 295473, size 8aca

SYSMGR: sending shutdown request

SYSMGR: starting shutdown sequence

Now I'm back at the kboot and I don't know what to do. Do I need to start over?

---

### Post by mr.Q on 2007-02-17
Nevermind. I fixed the problem. I pop the CD out during the reboot. 

Can you explain this section to a very new linux user...I dont understand why you have to do all this when it automatically detects your internet. 

Configure /etc/network/interfaces

Code:

$ nano /etc/network/interfaces

Make it look like this
Code:

auto lo iface lo inet loopback auto eth0 iface eth0 inet dhcp

configure /etc/resolv.conf

Code:

$ nano /etc/resolv.conf

Make it look like this (just an example ... you will have to configure it for your internet connection) If you are running linux on another computer in your house, just look at the /etc/resolv.conf on that computer.
Code:

search hsd1.ma.comcast.net. nameserver 192.168.1.1 nameserver 192.168.1.2 domain YOUR_WORKGROUP

Edit your hostname (this can be whatever you want)
Code:

$ echo playstation > /etc/hostname

Edit /etc/hosts
Code:

$ nano /etc/hosts

Make it look like this
Code:

127.0.0.1 localhost 127.0.1.1 YOUR_HOSTNAME.YOUR_WORKGROUP

Don't leave that command line because we will be using it in the next section.

---

### Post by tworkemon on 2007-02-17
Ciego and 3vi1 you too should look and join the fluxbuntu community which is currently trying to work on a live bootable PS3 version with all the kernel mods etc without having to run any other distro. Its currently being developed with latest feisty.

---

### Post by mr.Q on 2007-02-18
Ciego: Don't worry about the last reply. Got it figured out. Thanks for an awesome how-to!! Way easier to understand than anything else out there. 

*New linux user*

---

### Post by Ciego on 2007-02-19
> **tworkemon said:**
> Ciego and 3vi1 you too should look and join the fluxbuntu community which is currently trying to work on a live bootable PS3 version with all the kernel mods etc without having to run any other distro. Its currently being developed with latest feisty.

I went to the site and even registered for the forums but I couldn't find anything PS3 related.     I only spent about 20 minuted looking but I am at work now so I couldn't waste any more time looking.  Can you send me a link to the PS3 related info?  A search for "PS3" on the web site and the forums came up empty.

---

### Post by tworkemon on 2007-02-21
> **Ciego said:**
> I went to the site and even registered for the forums but I couldn't find anything PS3 related.     I only spent about 20 minuted looking but I am at work now so I couldn't waste any more time looking.  Can you send me a link to the PS3 related info?  A search for "PS3" on the web site and the forums came up empty.

There isnt much on the forums etc. The best place is via IRC. They have a channel on Freenode.net #fluxbuntu. The issue right now has been trying to get the CD to boot.

---

### Post by steve101101 on 2007-02-21
hey. ive been following your guide on the forums and i get stuck at this step.

$ mnt/ubuntu/boot/vmlinux initrd=mnt/ubuntu/boot/initrd.img root=/dev/sda3

it says that mnt/ubuntu/boot/vmlinux does not exist please help. im a noob

---

### Post by NobodySpecial on 2007-02-21
steve101101 - If you're having trouble at that last step, you can simply skip that line and reboot.

I believe you just enter:
```
reboot
```

When the kboot console comes up again, wait ten seconds and shoot boot to Ubuntu automatically.  If it doesn't, post the error code here.

---

### Post by steve101101 on 2007-02-22
i tried that after the second to last line failed (above)

i just waits at the kboot prompt forever.

This is also the second time i have tried to install ubuntu. (freshly formatted each time) both times had the same error

---

### Post by insyted on 2007-02-22
Once Ubuntu or any other OS is installed, how can you do anything else like play games?

Say I have a PS3 game:
How do I back it up onto a blank disk or ISO.
Then play either the blank disk from the PS3 BR-Drive or the ISO from the PS3 hard drive.

Is it still not possible to do this?

---

### Post by steve101101 on 2007-02-22
right now people are playing around with copying BlueRay Discs to the Harddrive.

---

### Post by Ciego on 2007-02-22
> **steve101101 said:**
> hey. ive been following your guide on the forums and i get stuck at this step.

$ mnt/ubuntu/boot/vmlinux initrd=mnt/ubuntu/boot/initrd.img root=/dev/sda3

it says that mnt/ubuntu/boot/vmlinux does not exist please help. im a noob

paste the output of the following commands if you would like some help.
```

$ ls -al /mnt/ubuntu
$ ls -al /mnt/ubuntu/boot
```

---

### Post by mb26 on 2007-02-22
So, is there any way to add vfat support after installing this? or do u have to go through the whole thing again?
[if latter i strongly urge adding the relavent to the guide asap]

---

### Post by Ciego on 2007-02-22
You just need to boot into the Gentoo Live CD and copy the modules over ... no need to reinstall.  You will have to mount the partitions first though.

```
$ mkdir /mnt/ubuntu
$ mount /dev/sda3 /mnt/ubuntu
$ cp -R /lib/modules/* /mnt/ubuntu/lib/modules/
```

That should do it ... then just shutdown Gentoo and take out the CD and reboot into Ubuntu.

I have since fixed the guide to address this problem (It is in the change log if you want to know when).

---

### Post by steve101101 on 2007-02-22
I was able to boot into kubuntu some how but the internet does not work. i think i messed up the network setup. (/etc/resolv.conf)

I was not sure what to put in as the nameserver spaces.

---

### Post by steve101101 on 2007-02-22
i got it to work after playing with the /etc/network/interfaces file.

---

### Post by steve101101 on 2007-02-23
hey. I first installed the kubuntu environment and reciently added the ubuntu environment. If i would like to remove the ubuntu environment from inside kubuntu what would i type into the console.

It should be like this command but for the ubuntu environment uninstall instead. Thanks

 **** sudo apt-get remove adept kaddressbook kaffeine kamera kappfinder karm katapult kate kaudiocreator kcron kde-guidance kde-systemsettings kdeadmin-kfile-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdm kghostview khelpcenter kicker kio-apt kio-locate klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguardd ksystemlog kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin ****

---

### Post by Andaconda on 2007-02-25
I have installed ubuntu on my PS3 successfully and it's great. i had a few questions though. 

1. Has anybody gotten Wine to install and run properly?

2. Is it possible to get Direct Rendering to work so that you can install Beryl. 

3. Are there drivers anywhere for the PS3 contoller?

Any help would be apreciated. 
  Thanks

---

### Post by Ciego on 2007-02-25
> **Andaconda said:**
> I have installed ubuntu on my PS3 successfully and it's great. i had a few questions though. 

1. Has anybody gotten Wine to install and run properly?

I do not think that it is possible on the PPC arch.
> 
2. Is it possible to get Direct Rendering to work so that you can install Beryl. 

No ... not at this time.  
> 
3. Are there drivers anywhere for the PS3 contoller?

What do you need drivers for?  Plug it in and it just works.  I do not think that anyone has had the bluetooth work yet but it will work just fine if you plug it in.

---

### Post by Andaconda on 2007-02-26
> **Ciego said:**
> I do not think that it is possible on the PPC arch.

No ... not at this time.  

What do you need drivers for?  Plug it in and it just works.  I do not think that anyone has had the bluetooth work yet but it will work just fine if you plug it in.

Yeah, I would think that it wouldn't work on PPC either. And yes, I was looking for bluetooth. I didn't know you could plug it in and have it work. 
Anyway, thanks for the quick reply.

---

### Post by Ciego on 2007-03-01
I just noticed someone put an article about this post up on Digg.  Here is a link if you would like to digg it.  If it gets noticed we may be able to expand the PS3 - Linux Community.

[COLOR="Blue"]http://www.digg.com/gaming_news/Installing_Ubuntu_Linux_on_the_PLAYSTATION_3[/COLOR]

---

### Post by Dropknee on 2007-03-04
I follow the tutorial step by step and I re-check everything but got this problem:

```
cp -R /lib/modules/* /mnt/ubuntu/lib/modules/
```

then press enter and :

cp : target `/mnt/ubuntu/lib/modules/' is not a directory

any help?? I need to create that dir??

thx

---

### Post by Ciego on 2007-03-04
The directory should already exist but you may just want to skip that step and try it again after you get your system up and running.  I guess you could also try to create the directory.  I would suggest making sure that you have the drive mounted.

---

### Post by Dropknee on 2007-03-05
Thx Ciego but I guess im going to start all over to be sure I dont miss something, maybe I miss a step or something dont know, but thx again for the fast replay

---

### Post by Ciego on 2007-03-05
I am sorry that I couldn't be of more help, but you really should not need to start over because of this.  Your system will still operate without the modules but it will have less functionality.  You can always copy the modules over later (that is what I had to do because I missed this step when I installed the first time).  Good luck either way ... let us know if you have any other problems.

---

### Post by frankjann on 2007-03-10
I am a total newbie to linux but it appears I have successfully installed it on my PS3.  The problem is that there is no gui loading.  It successfully boots to a login but when I log in it just goes to a terminal type prompt that looks like an e-mail address of my username@playstation

I don't know what to do to get the gui to work.

I originally went with the kubuntu option but when there was no gui I tried the optional install of the standard ubuntu but when that finished I go no prompt to select gdm or anything, it just dumped me back to the same old prompt.

Could someone please tell me how to get the gui working?

Thanks

Frank

edit: Never mind.  I booted back to game os, found some info online that I wanted to try and when I rebooted it was booting into the gui.  I guess I just needed to reboot the system some other way than typing reboot.  Thanks anyway!  I look forward to playing with this.

---

### Post by ATT-Half on 2007-03-11
having problems accessing my DVD/CDROM drive 

here my fstab & mtab

```

# /etc/fstab: static file system information.
# file system mount point type options dump pass
LABEL=/ / ext3 defaults 0 0
LABEL=/boot /boot  ext2 defaults 0 2
LABEL=SWAP SWAP swap sw 0 0
proc /proc proc defaults 0 0
sys /sys sysfs defaults 0 0
/dev/fd0 /mnt/floppy auto noauto,rw,sync,user,exec 0 0
/dev/cdrom /mnt/cdrom iso9660 noauto,ro,user,exec 0 0
###### /etc/fstab done

```


```
/dev/sda3 / ext3 rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/sda1 /boot ext2 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
```

everytime i insert a DVD it tells me mount: mount point /mnt/cdrom does not exist
even the livecd tells me that 
so it's not like it's having problems reading the media
when in kboot promt i enter fdisk -l it only shows sda partitions ext2 ex3t swap

 i did allow my user cdrom access + external storage devices if that helps
i even tried to edit this line on fstab 
/dev/cdrom /mnt/cdrom iso9660 noauto,ro,user,exec 0 0
to /dev/sr0 /mnt/cdrom iso9660 noauto,ro,user,exec 0 0
but nothing anyone know what's goin on ?

thx

---

### Post by ATT-Half on 2007-03-12
well i was googleing looking for solutions but much of content out there is not for PS3. found out about mac-fdisk and i confirm it to be install when i check package manager but neither
 fdisk -l  or mac-fdisk -l work   :mad:  can't tell if it's been detected or not and what path.

i can sudo them all i want nothing :confused: 

only in the kboot prompt does fdisk - l work which list 3 mian sda patitions
dam everything when perfect aside from this am already running anime with vlc & mplayer USB sticks even mount fine haven't tried CF or SD yet.

anyone help me :(

could KDE have taken something related to CDROM/DVD when i uninstall it

---

### Post by ATT-Half on 2007-03-12
well i got it to work but not working properly


what i did play with cdrom mount commands but always come back
mount mount point mnt/cdrom not found

i when to fstab and deleted 
```
/dev/cdrom /mnt/cdrom iso9660 noauto,ro,user,exec 0 0
```

this time fstab was not in the way & now terminal return with: 
you need root privileges to run mount /dev/cdrom /mnt/cdrom
:) 
tried sudo mount /dev/cdrom /mnt/cdrom
got this back
did not provide file system will try udf  
mnt/cdrom do not exist
 but it still it mounted :) 

when on to play my few files after while i come back (disc still in drive)

so i figured now find a way to automate mounting using the command i found without going to terminal every time

keep trying mount commands  in one those cases i think i mistype something
i think i got list of all mount options  i think

so there i read something about labeling the dev/sda -L
so i remember when installing linux i had to label sda partitions
an figure i'll give it tray with cdrom

but made mistakes here
```
i open a terminal window
sudo /dev/cdrom -L "/cdrom
hit enter
i forgot to close with " so i did again 
sudo /dev/cdrom/ -L "/cdrom"
```

hope this doesn't make double /cdrom cause have no clue of the delete command for label's 

well kinda forgot about it
when on back to fstab

and figure i give it a try to mix/match somewhat like ext3 and boot lines with but using cdrom 
LABEL=/ / ext3 defaults 0 0
LABEL=/boot /boot  ext2 defaults 0 2

and i enter this LABEL=cdrom /mnt cdrom iso9660 noauto,ro,user,exec 0 0

well much to my surprise it worked  but now i got a problem it won't eject ](*,) so i got up and tried ps3 eject button won't work.
after testing i figurre out a way to eject by right clicking mounted DVD icon and press eject  then i have to get up walk to ps3 and press the eject button to finally eject.


can someone help you can't say i didn't put effort
linux nOOb signing off 

have been awake 15 hours now for love of god help so i can go to sleep :-D

---

### Post by cbreaker on 2007-03-13
Okay I know this is somewhat redundant, but I was really hoping to just get a few pieces of the puzzle filled in before replacing YDL with Ubuntu:

- I was never able to get sound working properly in YDL.  Sound plays but it is very scratchy and it's not listenable.   Does ALSA sound work correctly with the instructions provided on page 1?  Meaning, I want to run Amarok, so will that work?  Folks here seem to have no problems.  I'm using sound over HDMI, although I could do sound over the RCA jacks if necessary. 

- I'll be using a 1080p Aquos - I'm assuming you can get 1080p working without much trouble?  It wasn't a big deal with YDL, just the kernel parm and the normal changes to xorg.conf.  I used mode 133.

That's really it.   The PS3 isn't a fantastically fast linux box but I've been satisfied with the performance on YDL with KDE.  The sound won't work past the "sound test" program, and that's really the only reason I need to switch.

I really hope some day they allow access to the GPU, if for nothing else but for the ability to v-sync.  Nothing I can't stand more then video that's got tearing.

---

### Post by ATT-Half on 2007-03-13
I figure it out :guitar: 

i reset my fstab file to default settings although not sure how to remove label that i made on /cdrom but hey now it's working.

all i needed to do was: 

sudo mkdir /mnt/cdrom 

8)

---

### Post by weixiong80 on 2007-03-13
for the last part about installing the ubuntu desktop.
can i use the downloaded image instead of downloading it using the ps3 coz it is taking a long time.
how should i go about the command line to direct the installation from disc instead of internet?
please advise, thank you.

---

### Post by LemonyVengeance on 2007-03-14
I''m gettingstuck at this bit:

```
$ mkfs.ext2 -L "/boot" /dev/sda1
$ mkfs.ext3 -L "/" /dev/sda3
$ mkswap -L "SWAP" /dev/sda2  <-------------------------------- [HERE]
$ sync; sync; sync
$ swapon /dev/sda2 
$ mkdir /mnt/ubuntu
$ mount /dev/sda3 /mnt/ubuntu
$ mkdir /mnt/ubuntu/boot
$ mount /dev/sda1 /mnt/ubuntu/boot
```

When I type the command in I get the response:

```
Usage: mkswap [-c] [-v0| -v1] [-pPAGESZ] [-L label] /dev/name [blocks]
```

It's looking like there's something that has been left out of that command... does anyone have any input on this?

---

### Post by Ciego on 2007-03-14
Try taking out the label

```
$ mkswap /dev/sda2
```

or you could try just taking out the quotes

```
$ mkswap -L SWAP /dev/sda2
```

Please let me know if that fixes your problem so that I can change the guide.

---

### Post by LemonyVengeance on 2007-03-14
leaving the label out completely resolved the issue. Thanx man!

---

### Post by LemonyVengeance on 2007-03-14
> **Ciego said:**
> OK ... first, make sure that something is mounted at /mnt/root
```
$ ls -al /mnt/root
```
If that does't return anything then there is nothing mounted at root to unmount.  If that is the case, then there was a problem when labeling your drives. 

Is there any output from that command?

I am also having issues with the umount /mnt/root command. I get the reply:

```
couldn't umount /mnt/root: invalid argument
```

So I typed in the command above (ls -al /mnt/root) and got this reply:

```
drwxr-xr-x   2 kboot
drwxr-xr-x   4 kboot
```

That means that there's something mounted, Right?

I went ahead and tried to force the umount by using the -f switch infront of the directory and it said that the forced unmount failed. I could probably use the -a switch to unmount ALL the directories, but I'm not sure if that would work. 

Again, Input on this would be greatly appreciated.

---

### Post by raidlost on 2007-03-14
Second curtian

no luck with the needed server after so many hours
no docs to do the trick
not enough sleep

and my boss walks in with red hat enterprise, now if that is not a hint

my heart goes out to ubuntu so if any one can help soon i might be able
to restore whatever reputation there is 

please check the threads i have

ps sorry for doing this..... you have the highest views

---

### Post by LemonyVengeance on 2007-03-15
> **raidlost said:**
> Second curtian

no luck with the needed server after so many hours
no docs to do the trick
not enough sleep

and my boss walks in with red hat enterprise, now if that is not a hint

my heart goes out to ubuntu so if any one can help soon i might be able
to restore whatever reputation there is 

please check the threads i have

ps sorry for doing this..... you have the highest views


Off Topic. Very off Topic.

---

### Post by heffa209 on 2007-03-15
first of all thanks for the walk though
But i am having some problems i cant get out of a kboot i am new to this and i don't know what i am doing wrong can some one help

---

### Post by Ciego on 2007-03-16
> **LemonyVengeance said:**
> I am also having issues with the umount /mnt/root command. I get the reply:

```
couldn't umount /mnt/root: invalid argument
```

So I typed in the command above (ls -al /mnt/root) and got this reply:

```
drwxr-xr-x   2 kboot
drwxr-xr-x   4 kboot
```

That means that there's something mounted, Right?

I went ahead and tried to force the umount by using the -f switch infront of the directory and it said that the forced unmount failed. I could probably use the -a switch to unmount ALL the directories, but I'm not sure if that would work. 

Again, Input on this would be greatly appreciated.

I am confused .... is this a new problem? Please explain a little more.

---

### Post by Ciego on 2007-03-16
Here is an article concerning the PS3 kernel.  I know some people were having troubles compiling ... the article explains it and provides a solution.

[http://julipedia.blogspot.com/2007/03/building-updated-kernel-for-ps3.html](http://julipedia.blogspot.com/2007/03/building-updated-kernel-for-ps3.html)

---

### Post by KageSennin on 2007-03-16
Hi, I;m new to linux so I don't know how to fix this, and I apologize if this has been answered somewhere else.
I'm having a problem with copying the files from the usbdrive/target folder over to the ps3.
Everything worked up until that part of step 9.
I typed exit, then the cp /mnt/usb...ps3pf...etc. line, and it says:
"cp: unable to stat '/mnt/usbdrive/target/ps3pf_utils-1.0.9-2.ppc.rpm': Not a directory or file."
I'm not exactly sure what's wrong, did I mess something up?

---

### Post by Ciego on 2007-03-17
> **KageSennin said:**
> Hi, I;m new to linux 
Welcome!
> **KageSennin said:**
> I don't know how to fix this, and I apologize if this has been answered somewhere else.
No problem ... that's what we are here for.
> **KageSennin said:**
> 
I'm having a problem with copying the files from the usbdrive/target folder over to the ps3. Everything worked up until that part of step 9.
I typed exit, then the cp /mnt/usb...ps3pf...etc. line, and it says:
"cp: unable to stat '/mnt/usbdrive/target/ps3pf_utils-1.0.9-2.ppc.rpm': Not a directory or file."
I'm not exactly sure what's wrong, did I mess something up?

First make sure that the file you are trying to copy is there in the first place.
```
$ ls -al /mnt/usbdrive/target/
```
Do you see your file there?  If not ... why isn't it there?  Is the drive mounted? Is the file actaully on the drive? Can you see any other files that are on the drive? If it is there ... try again, you probably mistyped something.

---

### Post by KageSennin on 2007-03-17
Hey, thanks for the help, but I decided to give up on ubuntu and just use yellow dog.
I still don't know what was wrong with my original cp command, because I just cd'd my way into the target folder then cp'd the files into /mnt/ubuntu/tmp and it worked.
After that, I couldn't get the alien install to work because my college requires us to run a network client to connect to the internet, and it doesn't like to allow other things to connect to the internet easily, so I couldn't figure the internet settings in the config files that would allow the ps3 to connect to the internet to install the alien, so I decided to just call it quits since YDL is just that much easier to install.
Thanks again for the help.

---

### Post by Ciego on 2007-03-17
The next version should be easier to install ... you will have to check back with us.

---

### Post by LemonyVengeance on 2007-03-19
> **Ciego said:**
> I am confused .... is this a new problem? 

Yes. It is. I'm at the very beginning of step 06 - Configuring Minimal Install of Ubuntu Base System



> Please explain a little more.

CERTAINLY!

Im in the process of issuing the umount /mnt/root command but I'm getting 
```
couldn't umount /mnt/root: invalid argument
```
In response. Previously you had asked a person having a similar issue to do the ls -al /mnt/root command to see if it was mounted or not. I did that command and got this in reply:

```
drwxr-xr-x   2 kboot
drwxr-xr-x   4 kboot
```

I'm not sure if that means that there is something mounted or not. I apologize for my questions.. I, too, am a neophyte when it comes to linux, but have experience using command line for cisco routers (which, as you know have UNIX based OSs on them).

Also, I appologize for the delay in replying. My grandmother died last tuesday and I was out of town for a few days.

---

### Post by ttr_loves_mittens on 2007-03-20
Hey, I'm very VERY new to linux, and I need a little help installing Ubuntu :/

So, I'm at the part were you have to wget the bootstrap, but I've runb into a little problem.

I have no high-speed internet connection that wired (Only wireless)

I have the 6.10 Desktop PowerPC Install CD burned to a disc, and I also have the gentoo livecd. I might want to start the installation fresh though, so once I get the answer to this I'll start over.

It said that if you only have a lowspeed connection, you would mount the ubuntu PPC CD to the directory and you'd be able to get the bootstrap from there, however, I have no clue how to do this :(

Anyway, any help is greatly apprecieted :)

---

### Post by ATT-Half on 2007-03-20
can anyone upload ibm java verison to free hosting site

i register but IBM is been little B*#$&
been waiting for days they said they will review my info then try to contact me ](*,) 

&#8220;ibm-java2-sdk-5.0-4.0-linux-ppc.tgz&#8221;

thx

[http://www6.software.ibm.com/sdfdl/1v2/regs2/linuxjavasdks/java/java5/SR4/linuxppc32/Xa.2/Xb.V4HO5ljJ5hGvt9M1WhmOupn7vt1G7BGvJP0GPK4/Xc.java/java5/SR4/linuxppc32/ibm-java2-sdk-5.0-4.0-linux-ppc.tgz/Xd./Xf.Ltr./Xg.3804093/Xi.sdk5/XY.regsrvs/XZ.BKiEaSYlRBv-NKRlFGN8qR_PR1M/ibm-java2-sdk-5.0-4.0-linux-ppc.tgz](http://www6.software.ibm.com/sdfdl/1v2/regs2/linuxjavasdks/java/java5/SR4/linuxppc32/Xa.2/Xb.V4HO5ljJ5hGvt9M1WhmOupn7vt1G7BGvJP0GPK4/Xc.java/java5/SR4/linuxppc32/ibm-java2-sdk-5.0-4.0-linux-ppc.tgz/Xd./Xf.Ltr./Xg.3804093/Xi.sdk5/XY.regsrvs/XZ.BKiEaSYlRBv-NKRlFGN8qR_PR1M/ibm-java2-sdk-5.0-4.0-linux-ppc.tgz)

someone PM to me thx sharing now

---

### Post by killerskippy on 2007-03-21
Hi 

I seem to be stuck on base install

i have downloaded the iso image and unpacked it keeping structure and i issue the command to install the edgy release but i see this as the output

failure trying to run: chroot /mnt/ubuntu mount -t proc proc /proc


my command is: /tmp/usr/sbin/debootstrap --arch powerpc edgy /mnt/ubuntu [http://192.168.1.3/ubuntu/dists/edgy/Release](http://192.168.1.3/ubuntu/dists/edgy/Release)

Any ideas what ive done wrong. i have started over many times and always end at this point.

Thanks for any elp you maybe able to provide.

Skippy

---

### Post by Ciego on 2007-03-22
> **killerskippy said:**
> Hi 

I seem to be stuck on base install

i have downloaded the iso image and unpacked it keeping structure and i issue the command to install the edgy release but i see this as the output

failure trying to run: chroot /mnt/ubuntu mount -t proc proc /proc


my command is: /tmp/usr/sbin/debootstrap --arch powerpc edgy /mnt/ubuntu [http://192.168.1.3/ubuntu/dists/edgy/Release](http://192.168.1.3/ubuntu/dists/edgy/Release)

Any ideas what ive done wrong. i have started over many times and always end at this point.

Thanks for any elp you maybe able to provide.

Skippy

I am not entirely sure what you are doing or where you are at but I don't think you are supposed to unpack the iso.

---

### Post by Ciego on 2007-03-22
For anyone who is  having difficulties with the installation ... you may want to try the new Live CD for Feisty Fawn (the PS3 build).  There are still issues with the installation but they are minor and should be easily fixed. Please note that it is not in its final release form yet but it will work for now.

---

### Post by Bossieman on 2007-03-23
Can someone help me with this step:

**Copy otheros.bld from the new “kboot” folder on your USB drive into the “ OTHEROS” folder that we made earlier**

Where are otheros.bld and what is the new"kboot" folder?

---

### Post by Ciego on 2007-03-23
> **Bossieman said:**
> Can someone help me with this step:

**Copy otheros.bld from the new “kboot” folder on your USB drive into the “ OTHEROS” folder that we made earlier**

Where are otheros.bld and what is the new"kboot" folder?

When you extract the iso to your thumb drive, there will be a directory named "kboot" that contains a file called "otheros.bld".  You need to copy that file to your USB drive in the  /PS3/otheros directory. 

I don't mean to offend you, but if you are having difficulties this early in the tutorial, I would suggest trying the new Ubuntu Feisty Fawn Live CD which will boot up and install Ubuntu for you with ease.  It is not in its final form yet (sound isn't working and some other issues may occur) but it is very easy to use.  Just make sure that you get the PS3 version.

---

### Post by stevenz on 2007-03-24
> **Ciego said:**
> I am not entirely sure what you are doing or where you are at but I don't think you are supposed to unpack the iso.

Unpacking the ISO in Windows will break all the symbolic links and stop the install working as once the directory is chrooted, binaries won't be able to find their libraries anymore. If you unpack it under OS X or write the ISO straight to disk it should be fine.

I made the mistake of downloading the "Desktop" CD of 7.04 for the PS3 and it took me a while to work out that it was a Live-CD version. The installer seems to be a bit broken, but it at least boots to the desktop ok. I got as far as the actual install-phase before I noticed the word "desktop" in the filename. Oops. if I'd just used the 6.10 installer CD it probably would've been fine, but I prefer to be on the bleeding edge ;)

After booting with the CD in the PS3 instead, I'm now looking at an Ubuntu desktop after having done basically no work whatsoever. Now I just need to do the GUI based install and I'll hopefully be in business.

Thanks for the great HOWTO though :)

---

### Post by stevenz on 2007-03-24
> **ttr_loves_mittens said:**
> I have the 6.10 Desktop PowerPC Install CD burned to a disc, and I also have the gentoo livecd. I might want to start the installation fresh though, so once I get the answer to this I'll start over.

It said that if you only have a lowspeed connection, you would mount the ubuntu PPC CD to the directory and you'd be able to get the bootstrap from there, however, I have no clue how to do this :(

As the Live-CD is locked in the drive after booting, you'll either need another external CD/DVD ROM drive to access the disk from, or copy the contents of the CD to an SD card or somesuch and use that. (Please correct me if I'm wrong here guys)

Assuming you've got an external CD drive you just do;

mkdir /mnt/extcdrom
mount /dev/sr1 /mnt/extcdrom

That _should_ work to mount the disk, then use the commandline;

tmp/usr/sbin/debootstrap --arch powerpc edgy /mnt/ubuntu file:/mnt/extcdrom/ubuntu

instead of the normal one. All going well, that should work.

If you use an SD card, then you'll need to replace "/dev/sr1" with whatever the devicename of the SD card port is. (It mentions it during bootup, or you can "cat /var/log/dmesg" and look in there for it).

---

### Post by vannguyen0 on 2007-03-24
Hi... first off great guide!  I'm writing this post on Firefox in my newly installed Kubuntu OS.  I have a question about the sound.  I am using an HDMI cable to output video to my TV.  I have the PS3 configured to output sound through the digital (optical) out.  I'm getting a lot of static when playing any type of audio.  Any insights as to why??

Thanks!

---

### Post by coozz on 2007-03-24
Hi,

thanks for the great how-to. I've never even used any other OS than Windows and I got my Kubuntu running on the first try. However, I have a problem when I'm trying to install Ubuntu. When I type the command "sudo apt-get install ubuntu-desktop" in the terminal it says that I don't belong to the sudoers group. Same thing if I try to get back to the XMB via "sudo boot-game-os" command. I'd appreciate any help to resolve this issue...

BR, Marko

---

### Post by Ciego on 2007-03-24
> **coozz said:**
> Hi,

thanks for the great how-to. I've never even used any other OS than Windows and I got my Kubuntu running on the first try. However, I have a problem when I'm trying to install Ubuntu. When I type the command "sudo apt-get install ubuntu-desktop" in the terminal it says that I don't belong to the sudoers group. Same thing if I try to get back to the XMB via "sudo boot-game-os" command. I'd appreciate any help to resolve this issue...

BR, Marko
You must have skipped this portion of the guide
> 08 - More Configuration and Adding Users

We need to create a username and give the user the ability to use sudo. We will go ahead and add you to the audio, admin, and users groups now also


```
$ passwd root
$ adduser YOUR_USER_NAME
$ addgroup --system admin
$ adduser YOUR_USER_NAME admin
$ adduser YOUR_USER_NAME audio
$ adduser YOUR_USER_NAME users
$ visudo -f /etc/sudoers
```

add this to the end of the file so that users in the admin group can use sudo

```

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

Go through that part again and you should be ok.

> **vannguyen0 said:**
> Hi... first off great guide!  I'm writing this post on Firefox in my newly installed Kubuntu OS.  I have a question about the sound.  I am using an HDMI cable to output video to my TV.  I have the PS3 configured to output sound through the digital (optical) out.  I'm getting a lot of static when playing any type of audio.  Any insights as to why??

Thanks!
I cannot help you there ... I haven't used optical yet with Ubuntu ... sorry.  My HDMI works great though.

---

### Post by coozz on 2007-03-24
> **Ciego said:**
> You must have skipped this portion of the guide


Go through that part again and you should be ok.


Hi, 

thanks for the quick reply. I tried to do that but it says that the file system is read-only. And it keeps prompting an error: "Mounting /dev/sda3 on /mnt/root failed: Device or resource busy".

BR, Marko

---

### Post by vannguyen0 on 2007-03-24
> **Ciego said:**
> I cannot help you there ... I haven't used optical yet with Ubuntu ... sorry.  My HDMI works great though.

That's what I feared you would say... so I booted back into the Sony XMB and configured sound to go through HDMI (automatic).  I am still getting static whenever I play sound.  I played around with a couple of sound settings... but to no avail.  

Are there any sound modules/settings I can tweak/play around with in Linux??

---

### Post by vannguyen0 on 2007-03-24
ok... so i got rid of kde and installed gnome.  sound works great now.  now i cannot access the dvdrom.  everytime i stick an audio cd in there, it gives me this error:

"... could not access the CD-ROM device '/dev/scd0'
Reason: Permission denied"

I changed my fstab from what was on the guide to:

/dev/scd0 /mnt/cdrom iso9660 noauto,ro,user,exec 0 0

and i gave group user access to /mnt/cdrom

but can't seem to access the dvdrom.  help?

--------------

EDIT: I can't seem to access audio cds.  If I put in a data cd/dvd, I can access it.

---

### Post by coozz on 2007-03-24
> **coozz said:**
> Hi, 

thanks for the quick reply. I tried to do that but it says that the file system is read-only. And it keeps prompting an error: "Mounting /dev/sda3 on /mnt/root failed: Device or resource busy".


I've reinstalled kubuntu but now it doesn't accept my root password when I try to use the sudo command although I'm 100% sure I type it correctly...

---

### Post by fsando on 2007-03-25
Can some of you say something about how the ps3 is to work with compared to an ordinary pc?
I've seen the hype and am seriously thinking of getting one - for computational reasons (not for gaming).
The idea is that I will be getting a very fast computer for far less than a similar pc would cost. 
Is my thinking right? Is this a good idea?

---

### Post by NobodySpecial on 2007-03-25
vannguyen0  - Regarding your CD issues, see previous posts.  CD isn't working right on the PS3 under Linux yet, it is up to Sony to fix.

coozz - Are you sure you set the root password correctly?  Set it like this:
```
sudo passwd root
```

fsando - Do NOT buy a PS3 for the reason you mentioned.  It is kind of disappointing.  We hear about the Cell processor being fast, but this experience is quite slow.  Plus, remember that hooked up to your TV, the picture is not anywhere near as good as even a mid-level quality monitor (and I'm even using a Sony HDTV).  It is fast enough to do web browsing, E-mail, and word processing.  But, the one BIG thing I wanted to do was to stream video from my home server (like you can on the X-Box 360).  Well, it streams fine, but the PS3 **cannot** keep up with the stream, so it stutters and skips.  Part of the problem is that you only end of having less than HALF of the 512 megs of memory available because of the way Sony set up the hypervisor.

Placing Linux on the PS3 is fun, but Sony has crippled it so badly, that the experience is quite disappointing overall.  It is definitely worth doing if you have a PS3, but I wouldn't recommend you buy one for this reason.  You can get a Koala Mini from [System 76]("http://www.system76.com") for $599 and have much better performance.  I just bought their Darter laptop, and can attest that they are a great company and highly recommend them.

---

### Post by vannguyen0 on 2007-03-26
> **NobodySpecial said:**
> vannguyen0  - Regarding your CD issues, see previous posts.  CD isn't working right on the PS3 under Linux yet, it is up to Sony to fix.

Thanks

> **NobodySpecial said:**
> 
fsando - Do NOT buy a PS3 for the reason you mentioned.  It is kind of disappointing.  We hear about the Cell processor being fast, but this experience is quite slow.  Plus, remember that hooked up to your TV, the picture is not anywhere near as good as even a mid-level quality monitor (and I'm even using a Sony HDTV).  It is fast enough to do web browsing, E-mail, and word processing.  But, the one BIG thing I wanted to do was to stream video from my home server (like you can on the X-Box 360).  Well, it streams fine, but the PS3 **cannot** keep up with the stream, so it stutters and skips.  Part of the problem is that you only end of having less than HALF of the 512 megs of memory available because of the way Sony set up the hypervisor.

Damn... this is exactly why I am trying install Ubuntu on my PS3.  I had a computer with Windows MCE on it, and it was in a case that had a special size power supply.  That power supply died and so I figured why not give this a chance (but I'm guessing you do not want to read about my sob stories...)

Are you streaming video from your home server via wired or wireless connection (or does it not matter??).  I'm at the point where I have all the codecs installed and I have my smb mounts.  I haven't had a chance to try to stream something because all of my video content is on the computer that died.  I guess I'll convert something on my desktop later on tonight and try.

---

### Post by Ciego on 2007-03-26
> **NobodySpecial said:**
> 
fsando - Do NOT buy a PS3 for the reason you mentioned.  It is kind of disappointing.  We hear about the Cell processor being fast, but this experience is quite slow.  Plus, remember that hooked up to your TV, the picture is not anywhere near as good as even a mid-level quality monitor (and I'm even using a Sony HDTV).  It is fast enough to do web browsing, E-mail, and word processing.  But, the one BIG thing I wanted to do was to stream video from my home server (like you can on the X-Box 360).  Well, it streams fine, but the PS3 **cannot** keep up with the stream, so it stutters and skips.  Part of the problem is that you only end of having less than HALF of the 512 megs of memory available because of the way Sony set up the hypervisor.

Placing Linux on the PS3 is fun, but Sony has crippled it so badly, that the experience is quite disappointing overall.  It is definitely worth doing if you have a PS3, but I wouldn't recommend you buy one for this reason.  You can get a Koala Mini from [System 76]("http://www.system76.com") for $599 and have much better performance.  I just bought their Darter laptop, and can attest that they are a great company and highly recommend them.

I agree 100%  I like how you put that.  Hopefully we will see this change in the future.

---

### Post by Takenover83 on 2007-03-26
Anyone tried the Feisty Beta for the PS3?
The latest can be found here.
[http://cdimage.ubuntu.com/ports/daily-live/current/](http://cdimage.ubuntu.com/ports/daily-live/current/)

Only problem is that the "snd_ps3pf" is missing from the kernel, so no sound.

I edited the config, and then recompiled the kernel, but that didn't work. Using menuconfig, I could not find the option for the module, so maybe we will just have to wait for the kernel update, through the update manager. 

That is, unless someone else can figure out how to fix the sound. The live CD is great. Installation is a breeze. Just got to get the sound working.

---

### Post by Ciego on 2007-03-26
I will have to rework the guide when the final version comes out but it will be MUCH easier to do.  I hope we do get the sound working though.

And yes .... I have tried it. :)

---

### Post by Crazy_spam on 2007-03-27
Hi there yet another newb in trouble and in need of help.
I have managed to install ubuntu on my PS3 using this well put together How To, my only problem is that I cant get back to the sony XMB.
when I type $ sudo boot-game-os in eather ubuntu or Kboot I get the following error
[: 12: ==: unexpected operator
[: 12: ==: unexpected operator
[: 12: ==: unexpected operator
[: 12: ==: unexpected operator
[: 12: ==: unexpected operator
[: 12: ==: unexpected operator
Usage:
  other-os-flash-util [-b|-B] [-g|-r] flash_device [boot_loader_img]
  other-os-flash-util -s flash_device
  other-os-flash-util -d flash_device

Options:
  -s   show current settings
  -d   print difference of clock time between game os and linux
  -b   change boot flag : boot game os
  -B   change boot flag : boot linux
  -g   change boot loader format flag : compressed by gzip
  -r   change boot loader format flag : not compressed
ERROR: can't change boot flag

I am unsure what is wrong I have a feeling it has to do with the clock as it  is wrong and said something about it before, and when I change it to the correct time it changes back. Any help would be extremly welcome, as my wife wants to play sonic and if I cant do that the whole world is doomed :popcorn:

---

### Post by Takenover83 on 2007-03-27
Source:
[http://psubuntu.com/forum/viewtopic.php?t=60](http://psubuntu.com/forum/viewtopic.php?t=60)

> I had the same trouble. Here is a hint for you...
```
ls -l /bin/sh
```



> And the fix for me was:
```
rm /bin/sh
ln -s /bin/bash /bin/sh
```

---

### Post by Crazy_spam on 2007-03-27
Thanks heaps, you are a Hero you have no idea what you have saved the world from (ie: me)

---

### Post by Ciego on 2007-03-27
Please note that the above is only needed for the Kubuntu desktop.

---

### Post by granite123 on 2007-03-29
Ok im a huge n00b but can someone tell me what the hell i type on the kboot screen ...i only know one command and its boot-game-os ...
whats the one to start installing or get into ubuntu ?

---

### Post by Rasmusd on 2007-03-29
> **granite123 said:**
> Ok im a huge n00b but can someone tell me what the hell i type on the kboot screen ...i only know one command and its boot-game-os ...
whats the one to start installing or get into ubuntu ?

That would be Enter, if you have a linux install cd in the drive.

---

### Post by Vendeta on 2007-03-30
Im up to the point of transfering the fstab file but i dont have a flash drive handy so i used my psp but it cant detect it i guess cause fdisk -l  only finds my hdd's... any ideas? Ive tryed just using  the mem stick and a mp3... please help

---

### Post by Ciego on 2007-03-30
>  	Im up to the point of transfering the fstab file but i dont have a flash drive handy so i used my psp but it cant detect it i guess cause fdisk -l only finds my hdd's... any ideas? Ive tryed just using the mem stick and a mp3... please help

Make sure that you have the PSP on and that you activate the USB mode on the PSP.  It will work as a normal USB drive in this way.  You could also take the memory stick out of the PSP and put it directly in the PS3 if you have the Memory stick Pro Duo adapter that comes with most memory sticks.

---

### Post by Vendeta on 2007-03-30
i have tryed that... the ps3 dosent need the adapter tho...

---

### Post by ceros on 2007-03-30
> **Takenover83 said:**
> Anyone tried the Feisty Beta for the PS3?
The latest can be found here.
[http://cdimage.ubuntu.com/ports/daily-live/current/](http://cdimage.ubuntu.com/ports/daily-live/current/)

Only problem is that the "snd_ps3pf" is missing from the kernel, so no sound.

I edited the config, and then recompiled the kernel, but that didn't work. Using menuconfig, I could not find the option for the module, so maybe we will just have to wait for the kernel update, through the update manager. 

That is, unless someone else can figure out how to fix the sound. The live CD is great. Installation is a breeze. Just got to get the sound working.

I'm also having a problem with the sound. For me, there's also a problem with getting a network connection. I'm using ethernet. Are you using the same?

---

### Post by ceros on 2007-03-31
I've added a wiki page on Installing Ubuntu on the PS3. The web address is [https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3). It could use some improvement I think but I'm done with editing it for now.

---

### Post by Gecko2k on 2007-04-01
This is shaping up to be a great guide for people who have had no experience of Linux b4 :KS   I wonder if someone could help me I&#8217;ve been stuck with this problem for days and its starting to do my head in. I got up to step 5 with no problems but i cant continue past step 6 after typing ;

 cp /mnt/usbdrive/config/fstab /mnt/ubuntu/etc/fstab

i get an error :( 

cp: unable to open '/mnt/ubuntu/etc/fstab' : No such file or directory

:confused:

Don't worry I've done it!!!! :)

---

### Post by 4bc on 2007-04-02
Could someone please shed some light on a problem i am having with the install.

In step 5, when i run the debootstrap, i get an error saying - Failed getting release file - [http://archive.ubuntulinux.org/ubuntu/dists/edgy/release](http://archive.ubuntulinux.org/ubuntu/dists/edgy/release).

Anyone offer any suggestions please?

Keep up the good work everyone!

EDIT: Just started from scratch again, and it has now worked for me. Dont know what the problem was.

---

### Post by JustinMeltz on 2007-04-03
Hi everyone,

I have carefully scanned a million and one different forums for the help I need.  I noticed someone was having the same problem before, but it didn't seem to be resolved.  I tried the fix recommended and no such luck so I will start anew.

Ok,  I have Ubuntu installed.  I even have the xubuntu desktop setup!  I edited my kboot.conf file properly, except...I set it up for "mode:5" (1080p), but my TV is only 480p I believe.  So when Ubuntu loads up it goes to an unusable signal screen since my tv does not support it.

My problem is, whenever I try to edit the kboot.conf or overwrite it, I get an error because it is a readonly format file.

Can anyone tell me what to do?

I am afraid of bricking my PS3 haha!

Thanks in advance everyone.

Justin

---

### Post by Ciego on 2007-04-03
> **JustinMeltz said:**
> 
My problem is, whenever I try to edit the kboot.conf or overwrite it, I get an error because it is a readonly format file.

Can anyone tell me what to do?

I am afraid of bricking my PS3 haha!

Thanks in advance everyone.

Justin

First ... you cannot brick your PS3 in this manner,  

You need to give us more information ... are you at the kboot prompt trying to overwrite the file?  Are you in Ubuntu?  Are you using root or sudo?

---

### Post by wolvorine4424 on 2007-04-04
I believe he set the Mode to the wrong setting...

And if this is the case, he will only see the kboot prompt and after 10sec the screen turns black and thats it...

Well, here is what I did to make my life a little easyer... So far no problems. I have to many TV's lol

I set my mode to "0" for automatic (I know maybe a dumb Idea) But it works.

At the kboot prompt:
umount /mnt/root
mkdir /mnt/ubuntu
mkdir /mnt/ubuntu/boot
mount /dev/sda3 /mnt/ubuntu
mount /dev/sda1 /mnt/ubuntu/boot
chroot /mnt/ubuntu /bin/bash
sudo nano /etc/kboot.conf

Here is what I have in it:

default=ubuntu
timeout=10
root=/dev/sda3

ubuntu="sda1:vmlinux initrd=sda1:initrd.img video=ps3fb:mode:0"


You need to type the commands fast, because linux will load fast on you. I believe if you umount the root you can take your time after that.

Please correct me if i missed something...

BTW: Thank you for the Exelent Guide, I'm a bit of a noob in Linux, But I got it to work from the first try...

P.S. When will a fully supported Distro be out for the PS3??? (Ubuntu 7, when is it due out?)

---

### Post by wolvorine4424 on 2007-04-05
Forgot...

I did the same as you, but my TV is a 720p and can support 1080i (just not the 1080p).


Thats what I did. I didnt get any readonly errors...

And to save, Press CTRL + X, then Y then just Press Enter.
you should be back at the prompt. type exit to get to the Kboot Prompt, Then REBOOT.

PS3 will restart and everything should be good and working.

---

### Post by tsclieuser on 2007-04-07
great guide !!!

i have one problem though, it seemed that my installation is complete but i cant seem to make the  GUI work. 

it gets stuck on "*Running local boot Scripts (/etc/rc.local)"

when I press the enter key, it shows the login prompt. I can login with my password, but i cant get the Kubuntu gui. 

help! :(

---

### Post by wolvorine4424 on 2007-04-07
I'm sorry, but I cant help you there... I'm still a noob in troubleshooting linux...
Just getting the hang of using it and learning as much as I can... Soon it will replace all my Win systems.

Someone with more knowledge in this field please assist.


BTW: Did you install everything (especially the Desktop)??? this is the command to install it:
aptitude -y install "~tkubuntu-desktop"

I was able to install it in about 10 to 15 min... also did you finish section 9 without any problems?
And what desktop are you trying to run/installed???

I will try to help, but I'm sure I cannot answer all the questions.
Can you post the error you get, if any?

This is just a guess, but if the desktop is not starting. you may have not installed or conf the xorg correctly. But, I could be wrong.

---

### Post by ceros on 2007-04-07
New live CD builds are available for Ubuntu, Kubuntu, Xubuntu, and Edubuntu at [cdimage.ubuntu.com](cdimage.ubuntu.com). There are also alternate install CDs available for Ubuntu, Kubuntu, and Xubuntu. 

These builds makes installing Ubuntu, Kubuntu, Xubuntu, and Edubuntu on the PS3 much simpler as they place the "otheros.bld" file in the images as "/PS3/otheros/otheros.bld". This makes the PS3 detect the otheros.bld file directly from the disc, making any use for other mediums unnecessary.

I made changes to the HOWTO guide at [https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3) to reflect this.

---

### Post by tsclieuser on 2007-04-08
as far as i can remember, i completed everything without any problems, except for a few errors due to mistyped commands/paths. 

i installed kubuntu with that command 
"aptitude -y install "~tkubuntu-desktop""

surprisingly though, mine took almost a day to finish.. (probably my net connection) while yours only take 15mins?? 

hmm... anyother command to install kubuntu?? anyway i can download the files beforehand,burn to a cd/dvd then install from there?

i'll give it shot again later.. 

thanks for the help :)

---

### Post by reloadSE on 2007-04-08
I kind of failed at installing Ubuntu on my ps3 with following the guide and now i have a very serious error something that goes like this... No default root fs was found, or one was found and it didnt contains = config file :(. So could you help me out as I really want Both the Ps3 to work as a ps3 as well as using ubuntu on it. :)

---

### Post by ritterrav on 2007-04-11
I have installed Kubuntu desktop after a long period of trial and error, and i am at the login screen, and i cant rmemeber for the LIFE of me, what was my username and password, i remember making RITTERRAV and my pass , but it denies me everytime.... what can i do???

---

### Post by kosta008 on 2007-04-22
I've only installed linux once on my pc years ago, so I'm behind on the times.  What would be the best version to install on a PS3? Ubuntu, Kubuntu, Xubuntu, or Edubuntu?  I went to their respective sites, and I'm not sure what the difference is between all of them...  Is one going to run faster on a PS3, one going to look cooler, etc.?  Also, will Beryl run nicely on a PS3, has anyone tried it?  Thanks so much.

---

### Post by cbreaker on 2007-04-22
Although Ubuntu 7.x supports PPC, I read somewhere that they're discontinuing it.

I've had very limited success with the "official" Yellow Dog version; straight install on a 60GB PS3 and sound didn't work, it was a pain in the *** to get my video mode to work, and it was a pain to install new stuff.

You can install any version that supports the PPC, and you'll have to do a little extra work to install the PS3 specific stuff, but it's going to be the same pain on any distribution I think.

While video does work at high resolutions, it's the vesa driver, and it's slow.  I don't need snazzy 3D on Linux but I would like an accelerated X server that doesn't use so much CPU just to put a picture on the screen.

Until they get some better video going on PS3 linux, it's not much more then a gimmick for the normal Linux user.   Sure, you can apparently program for the Cell processor with it, but I'm not going to be doing any of that.

---

### Post by Ciego on 2007-04-23
I have not tried Xubuntu, but I believe that you will see the benefits of the lightweight manager when running it on the PS3 due to the very limited amount of RAM available.  I personally use Ubuntu just because that is what I run on my PC and It is the most familiar to me.  

I don't think we will be seeing anything that uses the graphics card very soon.

---

### Post by lvalics on 2007-04-28
I installed all OK, with Kubuntu Desktop, but when I try to start kdm, I get scrambled image (actually I cannot see much on TV, I see 5 times the login, with vertical lines, unreadable).
I tried all possibble hints, resolutions from the forum, but still no luck.
My TV is an LG 26LC2R and Playstation3.
If anyone have a guide how can I succeed, I want to have the Linux on computer, but I stucked since 2 days now.

LATER EDIT:
I resolved the problem 90% by copying from URL
[http://louiscandell.com/ps3/files/xorg.conf](http://louiscandell.com/ps3/files/xorg.conf) the content into my one. Actually I made backup and replace.

My only problem now is that the screen is too large with around 50 pixel in each part and I cannot resize it. Now I do not see the menu bars ...

---

### Post by Juo on 2007-04-29
Hello people

I am pretty new to linux and new to Ubuntu, but i really want it on my ps3...  anwho, I am stuck on Step 7 where you install Kubuntu...  I type the code "$ aptitude -y install '~tkubuntu-desktop' " in and then the program tries to reach [http://archive.ubuntulinux.org](http://archive.ubuntulinux.org) to install the program but it fails..  and keeps failing....  I dont know if the site has problems or its a problem on my end...  

pls help guys and gals

---

### Post by ThenonS on 2007-05-01
> **Juo said:**
> Hello people

I am pretty new to linux and new to Ubuntu, but i really want it on my ps3...  anwho, I am stuck on Step 7 where you install Kubuntu...  I type the code "$ aptitude -y install '~tkubuntu-desktop' " in and then the program tries to reach [http://archive.ubuntulinux.org](http://archive.ubuntulinux.org) to install the program but it fails..  and keeps failing....  I dont know if the site has problems or its a problem on my end...  

pls help guys and gals

I`m getting the same trouble ... try 

sudo apt-get install ubuntu-desktop

this might work not tried t on mine yet .... to busy on my sister wii :) 

:lolflag:

---

### Post by JohnBougiou on 2007-05-02
$ mkfs.ext3 /dev/sda3

It say The devise apparently doew not exist; did you specify it correctly?

Help!

---

### Post by ATT-Half on 2007-05-02
anyone heard the news  the new version of yellow dog has working WiFi Driver when combine with fw 1.70.


anyone working on it for ubuntu ?  :)

---

### Post by JohnBougiou on 2007-05-03
Problem with :

Step 5:

$ cp /boot/* /mnt/ubuntu/boot

Help!

---

### Post by Actreon on 2007-05-04
> **ATT-Half said:**
> anyone heard the news  the new version of yellow dog has working WiFi Driver when combine with fw 1.70.


anyone working on it for ubuntu ?  :)

I heard the news as well, I hope someone will do it. Bump for everyone who wants Wi-Fi enabled Feisty on PS3 :)

---

### Post by wwx on 2007-05-06
> **Actreon said:**
> I heard the news as well, I hope someone will do it. Bump for everyone who wants Wi-Fi enabled Feisty on PS3 :)

It has been working on my PS3 ever since I installed Ubuntu. My entire internet service is wireless and I live out in the middle of nowhere so I don't have an encryption turned on. When I boot up Ubuntu Linux I simply launch Firefox and start surfing the net.

---

### Post by rimasa on 2007-05-08
Instalation is very simple if you have latest updates installed on yor ps3 console.Eerything works perfectly exept WIFI. Any solutions???


Thanks

---

### Post by alex-eduardo on 2007-05-12
Same here.. Feisty-installation on my PS3 worked like a charm, but without wifi it's a bit pointless in my case..

Anyone know if there is a HOWTO on how to recompile the kernel with the driver patch from YDL? 

This is the only thing missing for Ubuntu PS3 to be a full-blown media center.

 I am considering scrapping Ubuntu and installing YDL if it looks like wifi support is not coming, but I've finally gotten my girlfriend used to Ubuntu on my HTPC, and I don't want to force yet another distro on her :)

---

### Post by spacefreak on 2007-05-17
Hey guys. Thanks for the great how to. I must say I'm really glad that I had *SOME* previous linux experience, even though it was not much. I ran into a snag at the end of the process. I was fairly confident I'd done everything right. this is my second attempt at the install, the first attempt was through a router that muffed up the internet connection and made some things work as they should not. Well, I got to the end of the process and ran the part where it goes mnt/ubuntu/boot/vmlinux. At first I had trouble with that part working, but then I figured it out and it restarted and went into ubuntu. The only reason I realized it was actually ubuntu is because I installed gentoo on a home computer once. it says starting system log, then ubuntu 6.10 playstation tty1. starts up some applications and the stalls at Running local boot scripts (/etc/rc.local). If I hit enter it says login incorrect, and I have to log in as root to reboot. If I let it do its thing when it first starts up from kboot, it acts like it's going to start ubuntu, then just sends me to the blue video screen. Anyone have any ideas? I apologize for my general lack of knowledge when it comes to linux, I'm still just a noob. And thank you for your help, it's not my playstation 3. lol.

---

### Post by LincolnT24 on 2007-10-17
I downloaded the newer version of Java which is 5.0.5.1 and edited the code you provided...everything worked except that the version that comes up is Java 1.4......I entered the update code but it keeps telling me that there is only 1 program that provides java (/usr/bin/gij-wrapper-4.1) and that there isn't anything to configure..................How can i get java 1.5 so that i can use "Frostwire"?
Thanks in Advance

By da Way Dis Message is for "No One Special"....but if anyone knows how i can get Java 1.5 on my PS3 using Ubuntu it would help alot :-)

---

### Post by startgame412 on 2007-10-17
Just FYI, this guide is outdated. For the latest guide on how ot install ubuntu on the ps3, visit [www.psubuntu.com](www.psubuntu.com) or search the community guide on here for ps3.

---

### Post by Avis Phlox on 2008-02-09
Outdated?  I spent about an hour reading the first few pages, I guess I should have started from the end.  #-o

But either way, thank you Ciego for putting a lot of effort to this HowTo.   :KS

---

### Post by Luk@s on 2008-03-04
It's pretty much outdated... the PSUbuntu community isn't very active. :-(

---

### Post by Lorneboy on 2008-06-13
Hi I just Installed Ubuntu on my PS3 and when I tried to switch back to my PS3 home menu It said It does not recognize the command so I connected the PS3 HDD to my computer and my computer would not recognize the Drive. So I took it into Pc Medic They formated it in NTFS format. So I got home an plugged it in to my PS3 It gave me a black screen and kboot said that It could not find the files to boot Ubuntu. So I plugged the drive into my computer once again. It recognized it so I formated It in FAT32 gave me the same messages as before. so I plugged it into my computer and deleted all partitions on the drive. Same thing happened. I emailed Sony but they said that they do not support "other OS'S". I think I need the PS3 boot files. If anyone could help me, or has the boot files for the PS3. It would be greatly apreciated. Thanks 
Lorne

---

### Post by mhw001 on 2008-07-30
i am trying to install the sun jave but when i get to the tgz file it says no such file or document...where do i place that file plz help leave me a message at my hotmail or here plz plz plz [email]hadihadihadihadi@hotmail.com[/email]

---

### Post by mistercreamer on 2009-04-28
after speading about a week googling to try to find a common solution to increase the screen resolution on the PS3(Linux 7.10) It finally was clear. all you have to do to change your resolution after you have installed unbuntu is:

sudo chmod a=rwx kboot.conf (where ever you put that file)

then add the line 

video=ps3fb:mode:5

inside of the the location of where your sys looks to find kboot.

I guess the sys determs the resolution before the sys starts to load ubuntu..


I didnt have to change anything else, just added that to my Linux="what ever info you have listed here and add video=ps3fb:mode:5" 

Hint:
using mode 5 kinda turned my screen green, but it was at the right resolution, so you may want to use mode:4.

---

### Post by CapstonePS3 on 2011-04-07
I can't get past the basic installer because the screen won't allow me to see the full ubuntu window.  How can this be fixed?

---

