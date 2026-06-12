---
title: "HowTo: Use an external display more comfortably"
date: 2009-06-17
forum: Outdated Tutorials &amp; Tips
---

### Post by elektronaut on 2009-06-17
[EDIT: That's the beauty of online collaboration: You come up with a tricky idea, and then somebody comes along and gives you a better idea in a one-liner... Anyway, thanks, rebegin! disper is really the better way to go. At the moment only possible if you have a NVidia card, though. So Intel card users might still follow my approach. **One big disadvantage though:** ACPI won't work anymore, apparently shuffling around the startup order of the services breaks it. But it came back to life after resurrecting the original order without any trouble. So you might still try this out and see for yourself.]

[SIZE="2"]The motivation[/SIZE]

The use of external displays with Ubuntu has become easier, namely if you have a NVidia graphics card (like me), and you can use the GUI tool *nvidia-settings* to tell your desktop environment to use an external display. But fiddling with such a tool if you use an external display most of the time becomes cumbersome. I wanted to have a solution which automatically displays everything on the external display directly after boot up if the display is connected. At the same time I didn't want to have any trouble if I am on the road and the display is not connected. I don't need Xinerama/TwinView because my laptop is not located next to the external display and it's not comfortable to use it anyway from a distance, given the pixel size.

*But you can change my solution according to your needs. It can surely also be used with an Intel graphics card.*

[SIZE="2"]Let me first explain what my solution does basically:[/SIZE]

[LIST=1]
[*][COLOR="Lime"]Check for a certain IP address[/COLOR]
If a certain IP address has been assigned to the eth0 interface, the laptop must be at home and thus the external display is connected. The graphical desktop will only be displayed on the external display.
[*][COLOR="Red"]Ask the user[/COLOR]
This only happens if the mentioned IP address has not been assigned. In this case the user is presented with the choice of using either the laptop display or the external display, as it could also be a network failure.
[/LIST]
[SIZE="2"]
So how does it work?[/SIZE]

It uses a script which is automatically run at boot time. This script does nothing but manipulating or copying these text files:
[LIST]
[*]/etc/X11/xorg.conf
If the external display shall be used (case 1. above), the corresponding file */etc/X11/xorg.conf.external* is copied to */etc/X11/xorg.conf*, if the user shall decide (case 2. above), the corresponding file */etc/X11/xorg.conf.server-layouts* is copied.
[*]/etc/X11/default-display-manager
GDM is either enabled (case 1.) or disabled (case 2.)
[*]~/.bash_profile
An automatic call to the script for the user dialog (case 2.) is added or deleted (case 1.)
[/LIST]

[SIZE="2"]The fine written[/SIZE]

As the IP address must have been assigned before the start of the boot script and GDM started afterwards, the start order of these services has to be reversed, because Ubuntu by default starts GDM before Network Manager. I'm not 100% sure if this manipulation is completely OK, but I don't see any danger either, and so far my system is running without any troubles. Please correct me if I'm wrong here.

[SIZE="2"]Credits[/SIZE]

This is based on the work of [**bodhi.zazen**](http://ubuntuforums.org/member.php?u=89054) - more about his user dialog script for choosing a server layout [**here**](http://ubuntuforums.org/showthread.php?t=271045), and [ **this idea**](http://ubuntuforums.org/showpost.php?p=2300599&postcount=25) by 
[**nalberda**](http://ubuntuforums.org/member.php?u=255589).
[**bodhi.zazen**](http://ubuntuforums.org/member.php?u=89054) might probably argue that my solution is less flexible than his one (which is what case 2. above does), because not using server layouts in case 1. doesn't allow for a change of the display arrangement without rebooting. This nowadays is only true if you don't have a NVidia graphics card, which still allows this with nvidia-settings. Also, even if I wouldn't use a NVidia card, I wouldn't care if I'm at home because I don't need the flexibility there but prefer not to have to look at the laptop screen and going through the whole log in and display selection procedure each time.

[SIZE="2"]Step by step[/SIZE]

[LIST=1]
[*]**Let's start with the different xorg.conf files we need.** 
One only for the external display, one with server layout sections. If you have no idea yet about server layouts, take a look at [this thread](http://ubuntuforums.org/showthread.php?t=240150). If you have a NVidia graphics card, you can easily copy and paste these files by using nvidia-settings. For xorg.conf.external, simply choose the laptop display, click "Configure..." and select "Disabled". Now you should have the desktop only on the external display. Then you click "Save to X Configuration File", click "Show preview..." and simply copy and paste the configuration to /etc/X11/xorg.conf.external (being sudo, of course).
For xorg.conf.server-layouts, you have to combine xorg.conf.external with the configuration that you get in the same way as described for your laptop display (disabling the external display). You have to make sure that identifiers like Device0, Screen0, etc. are not used twice. So replace them by non-ambiguous identifiers. Then you have to add the "ServerLayout" sections. Take a look at my xorg.conf.server-layouts for an example:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon Mar 23 15:33:27 PST 2009

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

#################### BOTH SERVER LAYOUTS USE THE SAME GRAPHICS DEVICE

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M G"
EndSection

#################### SERVER LAYOUT FOR EXTERNAL DISPLAY

Section "ServerLayout"
	Identifier	"EXTERNALMONITOR"
	Screen          "Screen_Samsung"
	InputDevice     "Keyboard0" "CoreKeyboard"
	InputDevice     "Mouse0" "CorePointer"
EndSection

Section "Screen"
    Identifier     "Screen_Samsung"
    Device         "Device0"
    Monitor        "Monitor_Samsung"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-2"
    Option         "metamodes" "DFP-2: 1680x1050 +0+0; DFP-2: 1024x768 +0+0; DFP-2: 960x540 +0+0; DFP-2: 840x525 +0+0; DFP-2: 800x600 +0+0; DFP-2: 800x512 +0+0; DFP-2: 720x450 +0+0; DFP-2: 700x525 +0+0; DFP-2: 680x384 +0+0; DFP-2: 640x512 +0+0; DFP-2: 640x480 +0+0; DFP-2: 576x432 +0+0; DFP-2: 512x384 +0+0; DFP-2: 400x300 +0+0; DFP-2: 320x240 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Monitor"
    Identifier     "Monitor_Samsung"
    VendorName     "Samsung"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

#################### SERVER LAYOUT FOR LAPTOP DISPLAY

Section "ServerLayout"
	Identifier	"LAPTOPMONITOR"
	Screen          "Screen_Laptop"
	InputDevice     "Keyboard0" "CoreKeyboard"
	InputDevice     "Mouse0" "CorePointer"
EndSection

Section "Screen"
    Identifier     "Screen_Laptop"
    Device         "Device0"
    Monitor        "Monitor_Laptop"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: 1280x800 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Monitor"
    Identifier     "Monitor_Laptop"
    VendorName     "Benq"
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection


```
[*]**Now we need the script for manual server layout selection.**
I usually put my scripts in ~/bin, so that I don't forget to migrate them to a new installation. Here is the script, save it as *"xmenu"* and don't forget to make it executable ('chmod +x xmenu'):
```
#!/bin/sh
# xmenu, a simplified version of the script described in
# http://ubuntuforums.org/showthread.php?t=271045

dialog --backtitle "Server Layout Selection" --menu "Please choose your desired display" 10 75 5 \
"Laptop" "The laptop display" \
"External" "The external Samsung display" 2>/tmp/xgui.tmp

return_value=$?
monitorcfg=`cat /tmp/xgui.tmp`
rm /tmp/xgui.tmp
echo "return_value =" $return_value
echo "monitorcfg =" $monitorcfg

case $return_value in 
    0)
        #clear
        case $monitorcfg in
	        Laptop)
		        exec /usr/bin/startx -- -layout LAPTOPMONITOR
		        exit 
		        ;;
	        External)
	            exec /usr/bin/startx -- -layout EXTERNALMONITOR
	            exit
	            ;;
	        *)
		        exit
		        ;;
        esac
    1)
        exit
		;;
esac
```
[*]**Then there is the boot up script, which manages all the file handling.**
As this script has to be run during boot, after network configuration and before GDM start (we come to the start order in the next step), we will save this script in **/etc/init.d**. Change the parameters at the beginning according to your system configuration, at least the first three ones (commented with "CHANGE..."). Here it is, save it as **/etc/init.d/display-config**. Again, don't forget to make it executable. 
```
#!/bin/bash -e
#
# display-config
#
# A script to facilitate the use of an external display. Prepares the system
# configuration during boot for either automatic selection of the external
# display in case of receipt of a certain IP address, or manual selection in
# all other cases.
# Manipulates /etc/X11/xorg.conf, /etc/X11/default-display-manager and
# ~/.bash_profile
# Based on the following threads:
# http://ubuntuforums.org/showthread.php?t=308673
# http://ubuntuforums.org/showthread.php?t=271045
# and this idea http://ubuntuforums.org/showpost.php?p=2300599&postcount=25

IPADDR="192.168.1.2" # CHANGE IP TO REFLECT THE ONE ASSIGNED BY YOUR ROUTER
HOMEDIR="/home/elektronaut"                 # CHANGE TO YOUR HOME DIRECTORY
XSCRIPT="/home/elektronaut/bin/xmenu"           # CHANGE SCRIPT PATH

LOGFILE="/var/log/display-config.log"           # change eventually
XORGEXT="/etc/X11/xorg.conf.external"           # change eventually
XORGLAYOUTS="/etc/X11/xorg.conf.server-layouts" # change eventually


# logging
echo `date` " display-config started" > $LOGFILE

################# automatic display configuration for external display
for a in {1..10} # give the network interface time to come up
do
  if ifconfig eth0|grep -q "$IPADDR" 
    # we are at home
  then
    echo `date` " home IP in use" >> $LOGFILE

    # and use the external display
    cp $XORGEXT /etc/X11/xorg.conf

    # set the display manager
    echo `date` " enabling gdm" >> $LOGFILE
    echo "/usr/sbin/gdm" > /etc/X11/default-display-manager

    # we delete the automatic call for the manual display selection script in bash_profile
    if grep -q "$XSCRIPT" $HOMEDIR/.bash_profile
      then
        echo `date` " deleting call for XServer start script from bash_profile" >> $LOGFILE
        grep -v "$XSCRIPT" $HOMEDIR/.bash_profile > /tmp/bash_profile.tmp
        cat /tmp/bash_profile.tmp > $HOMEDIR/.bash_profile
        rm /tmp/bash_profile.tmp
    fi
      echo `date` " display configuration for external display finished" >> $LOGFILE
      exit 0 # display configuration finished
    else
      echo `date` " waiting 2 seconds" >> $LOGFILE
      sleep 1 # give the network interface time to come up
  fi
done

################# manual display configuration
# if we get to this point, we will go bodhi.zazen's way
# and let the user decide - see http://ubuntuforums.org/showthread.php?t=240150

echo `date` " starting manual display configuration" >> $LOGFILE

# the configuration with different server layouts
cp /etc/X11/xorg.conf.server-layouts /etc/X11/xorg.conf

# disable gdm, enable easy reactivation
echo "#/usr/sbin/gdm" > /etc/X11/default-display-manager

# automatic call of the script described in http://ubuntuforums.org/showthread.php?t=271045
if ! grep -q "$XSCRIPT"  $HOMEDIR/.bash_profile
then
  echo "$XSCRIPT" >> $HOMEDIR/.bash_profile
fi

echo `date` " display configuration for user dialog finished" >> $LOGFILE

exit 0
```
As you can see, there are still some logging commands which you can delete or uncomment.
One more thing you might want to change is the waiting time for the network interface coming up. At the moment it is waiting for 10 seconds at max. If you would like to expand this to 20 seconds, for example, you would do this change in line 29:
```
for a in {1..10}
```to```
for a in {1..20}
```

[*]**Finally, we have to change the start up order.**
Here comes the dirty work. We need the network before our script is run, and GDM start afterwards. We also need a symlink to the script. First we let NetworkManager start earlier:
```
cd /etc
cp -ax rc2.d/S50NetworkManager rc2.d/S30NetworkManager
rm rc2.d/S50NetworkManager 
cp -ax rc3.d/S50NetworkManager rc3.d/S30NetworkManager
rm rc3.d/S50NetworkManager 
cp -ax rc4.d/S50NetworkManager rc4.d/S30NetworkManager
rm rc4.d/S50NetworkManager 
cp -ax rc5.d/S50NetworkManager rc5.d/S30NetworkManager
rm rc5.d/S50NetworkManager

```
...and GDM later...
```
cp -ax rc2.d/S30gdm rc2.d/S34gdm
rm rc2.d/S30gdm
cp -ax rc3.d/S30gdm rc3.d/S34gdm
rm rc3.d/S30gdm
cp -ax rc4.d/S30gdm rc4.d/S34gdm
rm rc4.d/S30gdm
cp -ax rc5.d/S30gdm rc5.d/S34gdm
rm rc5.d/S30gdm

```
Finally we add symlinks in the relevant runlevel directories for our start script:
```

cd rc2.d
ln -s S33display-config ../init.d/display-config
cd ../rc3.d
ln -s S33display-config ../init.d/display-config
cd ../rc4.d
ln -s S33display-config ../init.d/display-config
cd ../rc5.d
ln -s S33display-config ../init.d/display-config

```
[/LIST]

That's it. Additions and corrections welcome :D

---

### Post by rebegin on 2009-06-21
maybe you also want to check out the program called disper :)

---

