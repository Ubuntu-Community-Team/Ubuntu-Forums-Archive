---
title: "ubuntu linux for Emachines 68xx laptops"
date: 2005-05-16
forum: Outdated Tutorials &amp; Tips
---

### Post by NoTiG on 2005-05-16
Important links:

[http://www.ubuntuforums.org](http://www.ubuntuforums.org)
[http://ubuntuguide.org](http://ubuntuguide.org)
[http://www.ubuntuforums.org/showthread.php?t=31094](http://www.ubuntuforums.org/showthread.php?t=31094)

I would say that ubuntu, gentoo, and slackware are the 3 kings of linux distributions. Ubuntu is aimed for newbies... to learn linux. It uses the debian apt-get to install programs on commandline.. and synaptic for graphical installation. I tried it, like it, and I'm sticking with it. ANyways enough of introductions!!!

The first thing you should decide is whether you want a 64 bit distro or 32. With 64... nothing is really faster... compile times are slightly faster and barely noticeable. But you will run into more headaches... Namely... 32 bit programs that are closed source havne't been ported to 64. For instance... the flash plugin , win32 codecs(so you wont be able to watch most porn), java... etc.... So I would advise 64 bit only if your not planning to use linux as your main OS and just want to hack away and learn stuff. you *can* run 32 bit apps under 64 bit but it is a headache. Here is a link on how to do that if you are interested: [http://www.ubuntuforums.org/showthread.php?t=24575&page=4&pp=10](http://www.ubuntuforums.org/showthread.php?t=24575&page=4&pp=10)

THE GUIDE

Install the ISO image for the architecture that you want, 32 or 64. After you dl the image... you have two choices. you can either burn it to a cd or you can install from the ISO without even burning. I would suggest for convenience and so maybe if you want to pass the distro on to other pals.. that you burn a cd. But if not here is a link on what to do: [http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948)

You should defragment your windows harddrive.. and then use a tool such as partition magic to repartition your hard drive into two partitions... 1 for windows and 1 for linux. Once you have done that you are ready to install. But first........

Before you begin your installation you will need to Dl a file to your windows desktop: [http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper)
Install ndiswrapper... because the one that comes with the 32 bit distro does not work (and there isnt even one that comes with 64).
NOTE:this program is for wifi. So.. if you have a cable and can plug your laptop in you can just DL this file after you install. But i'm going to assume that you don't have a cable and tell you how to install by accessing your windows partition from linux.

IF YOU ARE going to install the 64 bit distro... you will also need to dl the 64 bit drivers for your wifi: [http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php)

BEGIN THE INSTALLATION

It should be pretty straight forward... you have to manually edit the partition table and create a partion in the empty space that you have (from using a repartitioning tool from windows to make room). You can almost do this blind!

ONCE IT IS INSTALLED

It will autodetect everything... BUT your wifi card. THe first step you will need to do is download gcc (a compiler) and linux-headers (source files so you can install things) from the CD since they are not installed by default. you can use the commaned line.. or Synaptic from the system menu. WHen you install the headers.. make sure you get the ones with the name that ends in your architecture:from terminal:
```

sudo apt-get install linux-headers-2.6.10-5-386
```

OR
```

sudo apt-get install linux-headers-2.6.10-5-amd64-generic
sudo apt-get install gcc
```

THE NEXT STEP

once you have those installed... you need to access your files from your windows partition.. your ndiswrapper, and your wifi drivers. Go to applications and system tools and open a ROOT terminal. Type:

```
mkdir /mnt/storage
```

THis is a file that will be your storage point. next type:

```
mount /dev/hda1 /mnt/storage
```

THat will mount your first partition on your hard drive to /mnt/storage . I'm assuming that you will leave windows as your first partition. next:

```
cd /mnt/storage
ls
```

ls .. is the list command and it will help you navigate through the directories in windows. just remember.. to get into documents and settings.. to get to your desktop you need to put quotes . like this:

```
cd "documents and settings"
```

You will need to next copy your drivers files into linux. If you are doing 32 bit:

```
cp Drivers/bmcwl5.* /home/notig
```

NOTE: you replace notig with whatever your home user is. THis will copy bmcwl5.sys and bmcwl5.inf to your home directory. After you do this next you will need to get ndiswrapper.. from wherever you installed it, and use the cp (copy) command . Put it in your home directory as well. IF your 64 bitting.. copy your 64 bit drivers too

```
cp "documents and settings"/joseph/desktop/ndiswrapper-1.1.tar.gz /home/notig
```

Next: you should probably exit out of root and start using the regular terminal. Youl wil notice that "sudo" is before each command. that gives you super user privileges. Switch user to your user and type cd.
That will automatically bring you to your home directory. Next:

```
sudo ln -s /usr/src/linux-headers-2.6.10-5 /lib/modules/2.6.10-5-386/build
```

OR

```
sudo ln -s /usr/src/linux-headers-2.6.10-5/lib/modules/2.6.10-5-amd64-generic/build
```

This creates a symbolic link from the modules/2* directory called build, that will enable you to install and compile the ndiswrapper utility. NEXT, extract ndiswrapper:

```
sudo tar zxvf ndiswrapper-1.1.tar.gz
```

That extracts and uncompresses ndiswrapper into a directory. CHange into the new directory:

```
cd ndis*

Install ndiswrapper

sudo make install 
```

It should complete without error. Next, move out of the ndiswrapper directory back to your home, cd . Or type ../ .

```
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
```

There you just loaded the driver module and -m makes it so that each time you boot up your computer you do not have to repeat this process.
The name of the 64 bit driver is netbc564.inf . JUst replace it with the bcmwl5.inf . Next type:

```
sudo modprobe ndiswrapper
```

At this point you should see the blue e come on for your wifi radio. if it doesnt come on automatically press Fn and F2 to turn it on....... At this point your wifi card is enabled. all you have to do is go to system/administration/networking and configure your wifi card. THe name of the network, password.. and DHCP etc... after that activate it and your internet should work.


AHHhhhhhhhhh. breath, and feel linux goodness :P NEXT:

Here is a script that will chiefly: update your repositories (/etc/apt/sources.list) , install various codecs... a couple of programs and such.NOTE: THIS IS FOR 32 bit distros only. TYpe:

wget [http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh](http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh)

If you want.. open up the file with a text editor to see exactly what it does. Next move to the directory you dled it to and type:

```
sudo sh ubuntusetup.sh
```

THERE. you are now practically multimedia ready. watch porn, dvd's whatever!. Next, Installing the ati graphics driver(dont do this yet if your using 64 bit distro... you will need to update your repositories first):

```
sudo apt-get install xorg-driver-fglrx
```

Next.. you will have to modify your /etc/X11/xorg.conf File. Instead of telling you what to put in i will just paste mine and you can copy it. BUt first back up :

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

type:

```
sudo gedit /etc/X11/xorg.conf
```

remove everything and paste the following (THIS will work for 32 and 64 bit btw)

--------------------------------------------------------------------
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
# cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
# sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
# sudo dpkg-reconfigure xserver-xorg

Section "Files"
FontPath "unix/:7100" # local font server
# if the local font server has problems, we can fall back on these
FontPath "/usr/lib/X11/fonts/misc"
FontPath "/usr/lib/X11/fonts/cyrillic"
FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/Type1"
FontPath "/usr/lib/X11/fonts/CID"
FontPath "/usr/lib/X11/fonts/100dpi"
FontPath "/usr/lib/X11/fonts/75dpi"
# paths to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
Load "bitmap"
Load "dbe"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "GLcore"
Load "int10"
Load "record"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "keyboard"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection
Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
Driver "fglrx"
BusID "PCI:1:0:0"

# === OpenGl Overlay ===
# Note: When OpenGL Overlay is enabled, Video overlay
# will be disabled automatically
Option "OpenGLOverlay" "off"

# === Use internal AGP GART support? ===
# If OpenGL acceleration doesnt work, try using "yes" here
# and disable the kernel agpgart driver.
Option "UseInternalAGPGART" "no"

# === Video Overlay for the Xv extension ===
Option "VideoOverlay" "on"

EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
Modeline "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x800"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection

```
-------------------------------------------------------------------

Make sure you save the file and its written. after this all you will need to do is restart X. you can reboot your computer... OR since its linux and not windows you can just restart the X server. Type:

```
sudo /etc/init.d/gdm stop
```

Then after you log in type:

```
startx
```

THERE!!! congrats.
you can now check your drivers by going into a terminal and typing
```
fglrxinfo
```

It should say that your using "ati ......." and not MESA.

type:
```
glxgears
```

If you want to run a benchmark.

--------------------------------------------------------------------

Some other minor things that you will need to know: you can get wifi working and your ati driver loaded with the 64 bit distro... but you will have to scip that auto script since its for 32 bit distros (it installs codecs, repositories, other stuff).

-your screen will dim when you boot up with the 64 bit distro. just brighten it back up.

- your sound will be low... at its highest setting. to make it louder.. look up at the right and right click on the sound .. open volume controls. once there go to edit/preferences ... and select the
PCM2 box. move PCM1 and PCM2 up to make it louder... but you probably wont want it all the way up.

-if your using wifi and you don't have ethernet plugged in... you will notice each time you boot up your computer that it will hang... for awhile.. on configuring network devices. to fix this :

```
sudo gedit /etc/dhcp3/dhclient.conf
```

Scroll down to the part where it says timeout 60 .. and change 60 to 5. save and exit.

-you will want to have an embedded video player . first type:

```
sudo apt-get install mozplugger
```

Next, DL this file:
[http://www.ubuntuforums.org/attachment.php?attachmentid=392](http://www.ubuntuforums.org/attachment.php?attachmentid=392)

switch to the directory you dl it to and type:

```
sudo mv mozpluggerrc.txt /etc/mozpluggerrc
```

Then move to your home directory, cd .

list all the files by typing ls -a . you should see one that says .mozilla. Cd into .mozilla/firefox and delete pluginreg.dat .

```
sudo rm pluginreg.dat
```

Restart firefox and test your plugins here:

----------------------------------------------------------------
THats about it! . you should be good to go if your using 32 bit. if your using 64 bit... i can show you how to get semi-multimedia ready .
GO to this website: [http://download.ubuntuforums.org/ubuntusetup/sources.list](http://download.ubuntuforums.org/ubuntusetup/sources.list)

Copy all of it. next:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
sudo gedit /etc/apt/sources.list
```

Replace everything in sources.list with what you copied. NExt comment out two lines with the # :

#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

Leave the middle one and save. Now your repositories are updated. next run this modified script:

open up gedit and paste this into it then save it as ubuntusetup.sh:

--------------------------------------------------------------------
```

#!/bin/bash
#
# +*** WANRING WARNING WARNING WARNING WARNING ***----------------------------------------------+
# | ryan (ubuntu-geek) / site@ubuntuforums.org |
# | Purpose of this script is to automate/tweak setting up a new ubuntu system. |
# | |
# | This script installs 3rd party programs and are not supported by canonical/ubuntu. |
# | If this script blows up your installation it's not my fault :) |
# | |
# | This script has been tested on Hoary Hedgehog 5.04. |
# | ++++++++++++++++++++++++++++++++++++++++++++++++++ +++++++++++++++++++++++++++++++++++++++++ |
# | This script will perform the following functions. |
# | 1. Install beep-media-player, gstreamer0.8-mad (for mp3's) |
# | 2. Enable debian-marillat, universe and multiverse repo's |
# | 3. Install latest java and enable java in firefox |
# | 4. Give you nice forms in firefox |
# | 5. Install streamtuner |
# | 6. Install msttcorefonts |
# | 7. Install latest acrobat reader and firefox plugin |
# | 8. Install dvd playback support |
# | 9. Install w32codecs and dvd libraries |
# | 10. Install gnomebaker |
# | --------------------------------------------------------------------------------------------|
# | 5/2/2005 - using backports for java | remove acrobat reader its broke |
# +---------------------------------------------------------------------------------------------+

### global options ###
wget="/usr/bin/wget"
apt="/usr/bin/apt-get"
core_packages="build-essential"
media_packages="beep-media-player gstreamer0.8-mad streamtuner xine-ui totem-xine"
misc_packages="msttcorefonts libdvdcss2 gnomebaker gftp"
#java_jre_url="http://download.ubuntuforums.org/ubuntusetup/jre-1_5_0_02-linux-i586.bin"
firefox_forms="http://download.ubuntuforums.org/ubuntusetup/ff-forms.tar.gz"
#sources_list_url="http://download.ubuntuforums.org/ubuntusetup/sources.list"
misc_fonts_url="http://download.ubuntuforums.org/ubuntusetup/miscfonts.tar.gz"

### functions ###
check_errs()
{
if [ "${1}" -ne "0" ]; then
echo "ERROR # ${1} : ${2}"
exit ${1}
fi
}
### main script starts here ###

### snag the updated sources.list

#cd /etc/apt/ && mv sources.list sources.list.orig && ${wget} ${sources_list_url}
#gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
#gpg --armor --export 1F41B907 | sudo apt-key add -
#check_errs $? "There was an error downloading the sources.list."
#sleep 5

### lets update the apt repo
${apt} update
check_errs $? "There was an error in apt-get update."
sleep 5

### lets install build-esstential
echo "Additional packages maybe need to be installed select yes if asked"
${apt} install ${core_packages}
check_errs $? "There was an error in ${core_packages} installation."
sleep 5

### lets install media_packages
echo "Additional packages maybe need to be installed select yes if asked"
${apt} install ${media_packages}
check_errs $? "There was an error in ${media_packages} installation."
sleep 5

### lets install misc_packages
echo "Additional packages maybe need to be installed select yes if asked"
${apt} install ${misc_packages}
check_errs $? "There was an error in ${misc_packages} installation."
sleep 5

### lets install misc windows fonts that are not in the msttcorefonts package
echo "Installing Misc fonts"
cd /usr/share/fonts/truetype/msttcorefonts
${wget} ${misc_fonts_url}
tar xvzf miscfonts.tar.gz
rm -f miscfonts.tar.gz
check_errs $? "Misc Fonts Installation has failed..."
sleep 5

### lets install firefox forms
echo "Installing firefox forms"
cd /usr/lib/mozilla-firefox/
${wget} ${firefox_forms}
tar xvzf ff-forms.tar.gz
rm -f ff-forms.tar.gz
check_errs $? "Firefox forms Installation has failed..."
sleep 5

### lets install java
#echo "Installing java"
#${apt} install sun-j2re1.5

echo "If you made it this far job well done."

```
----------------------------------------------------------

It's basically the same script as the 32 bit users except no java, windows codecs, or flash plugin for mozilla. after you save it run from the terminal:

```
sudo sh ubuntusetup.sh
```



END OF GUIDE.

---

### Post by Tremblay on 2005-05-18
Neat. I was wondering about the low sound volume. You might want to add that eMachines m68xx users should flash their BIOS (must be done in Windows), since the one that comes with the machine is well... just plain bad.

The BIOS update is available on eMachines' website. For m6805 it's at:
[http://www.emachines.com/support/product_support.html?cat=notebook&subcat=M-Series&model=M6805](http://www.emachines.com/support/product_support.html?cat=notebook&subcat=M-Series&model=M6805)

Others can find it by starting here:
[http://www.emachines.com/support/product_support.html](http://www.emachines.com/support/product_support.html)

---

### Post by jyona on 2006-01-11
Awesome guide! I just wish I had found it before I spent a week getting my 6807 configured to run ubuntu:???:  oh well, now I know where to look if I ever need to reinstall! Thanks-

---

### Post by Viriiguy on 2006-03-02
The guide is great, it is my luck that is horrid.
I followed your directions, and finally after installing a couple other packages I was about to compile the NDISWrapper. I loaded the driver, and yes the wireless light came on. I went into the network settings and set my WEP key and what not. It would still not go online. So I rebooted, and now ever since my wireless will not come back on.

When I try to use modprobe ndiswrapper I get an error. Unfortunately I am not in Linux atm, so I do not know the exact error, but it had to do with /lib/2.19blahblahblah/modules/drivers/net/ndiswrapper There is a single object file int his directory that it seemed to be having trouble with.

Being a bit of a nix newbie I am not certain what I could have done wrong.
But some days I sure do wish this laptop had a differant wireless card.

---

### Post by NoTiG on 2006-05-19
Hey. Try going into console and then 

sudo rmmod bcm43xx

then after that reload the ndiswrapper

sudo modprobe ndiswrapper

if thats what it is.. then you have to blacklist the bcm43xx so it stops loading.

edit: btw you will need to do this each time you restart your computer till you blacklist. and when you rm bcm43xx... you also have to remove ndiswrapper and the bcm module if its loaded and do it over again. i have been out of linux so long my guide is outdated. 

also we have the same computer so its easy to figure out what went wrong. if your wireless light came on that means its working.... and if it didnt work then its most likely because in your wireless properties under networking it is checked as ascii. each time your light is on and its not working look to make sure its under HEX .

right now im trying to find how to get our native resolution supported (1280 X 800 ) . its all glitched when i try it so i guess i will need to change the video driver.

---

