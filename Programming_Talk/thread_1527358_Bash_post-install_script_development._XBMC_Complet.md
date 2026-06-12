---
title: "Bash post-install script development. XBMC Complete Installer."
date: 2010-07-09
forum: Programming Talk
---

### Post by X3lectric on 2010-07-09
Hi folks

Myself and another guy started developing a post install script targeted at minimal installs of Ubuntu, to configure, fix and setup XBMC and resolve various common hardware specific problems. Some information about [XCI (XBMC Complete Installer) is found here.]("https://sourceforge.net/apps/wordpress/xci/2010/07/08/xbmc-complete-installer/")

It soon became apparent that we could help others and not just ourselves so the script grew and now its quite a massive beast.

Problem is that admittedly my bash scripting skills are awful and have massive limitations. The other guy **(andy) is MIA**, so I been lumped with the lot :(

Therefore I'm requesting for a partner or partners to help take the script to the next level and help improve the whole 

I have been trying to package for ppa and still haven't quite got it right, this is needed to add newer packages which already dont exist. Again lack of experience is a major fault.
Added several new fixes and features and am working on others, though lucid support is now becoming desirable. 

If you folks are willing to help and join forces, I thank you in advance.

to grab script do;

```
[LEFT]**[COLOR=#800000]sudo wget  http://sourceforge.net/projects/xci/files/Release/xci.sh/download[/COLOR]**[/LEFT]
 [LEFT]**[COLOR=#800000]sudo chmod +x xci.sh; sudo ./xci.sh[/COLOR]**
[/LEFT]

```[LEFT] Once run it should trigger to update from 1.0922 to 1.0952 there you can read the changelog.

Below is the script so you see it doesnt contain any dangerous code and so you kinda see what needs improving on bash syntax etc.

```
#!/bin/bash
#
###########################################################################
#                                                                         #
#      Copyright (C) 2010 Team iQuik                                      #
#      http://sourceforge.net/projects/xci/                               #
#                                                                         #
#   This file is part of XBMC Complete Installer (XCI).                   #
#                                                                         #
#   XCI is free software: you can redistribute it and/or modify           #
#   it under the terms of the GNU General Public License as published by  #
#   the Free Software Foundation, either version 3 of the License, or     #
#   (at your option) any later version.                                   #
#                                                                         #
#   XCI is distributed in the hope that it will be useful,                #
#   but WITHOUT ANY WARRANTY; without even the implied warranty of        #
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         #
#   GNU General Public License for more details.                          #
#                                                                         #
#   You should have received a copy of the GNU General Public License     #
#   along with XCI. see the file XCI_License.GPL, If not see              #
#   <http://www.gnu.org/licenses/>.                                       #
#                                                                         #
###########################################################################

clear
APPLOC=$(pwd)
VERSION="1.0953"
BETA="true"
OSBIT=$(uname -m)
SYS=$(uname -s; uname -r; uname -m)
if [ "$(id -u)" != "0" ]; then
    clear
    echo "Sorry, you must execute me with sudo."
    exit 1
fi

mkdir ~/setup &>/dev/null
mkdir ~/setup/logs &>/dev/null
rm -fr /tmp/xci &>/dev/null
mkdir /tmp/xci &>/dev/null

cd $APPLOC
if [ "$(dpkg -s wget | grep -i "Status:" | awk '{print $4}' 2>/dev/null)" != "installed" ]; then
    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Installing required tools..." 3 45
    aptitude install wget -y &>> ~/setup/logs/xci-installer.log
fi
if [ ! -e .dialogrc ]; then
wget http://dl.dropbox.com/u/4325533/XCI/dialogrc &>> ~/setup/logs/xci-script-upgrade.log
mv dialogrc .dialogrc &>> ~/setup/logs/xci-script-upgrade.log
fi
if [ "$(dpkg -s dialog | grep -i "Status:" | awk '{print $4}' 2>/dev/null)" != "installed" ]; then
    echo -e '\E[1;37m\033[1mInstalling Dialog...\033[0m'
    aptitude install dialog -y &>> ~/setup/logs/xci-installer.log
fi  
if [ "$(uname -a | grep -i "PAE")" != "" ]; then
    dialog --sleep 5 --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "Sorry, you seem to be running a PAE kernel, and this script does not support it." 5 40
    exit 1
fi  
if [ "$(dpkg -s pv | grep -i "Status:" | awk '{print $4}' 2>/dev/null)" != "installed" ]; then
    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Installing required tools..." 3 45
    aptitude install pv -y &>> ~/setup/logs/xci-installer.log
fi  
if [ "$(dpkg -s bind9 | grep -i "Status:" | awk '{print $4}' 2>/dev/null)" != "installed" ]; then
    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Installing required tools..." 3 45
    aptitude install bind9 -y &>> ~/setup/logs/xci-installer.log
fi  
if [ "$(dpkg -s tar | grep -i "Status:" | awk '{print $4}' 2>/dev/null)" != "installed" ]; then
    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Installing required tools..." 3 45
    aptitude install tar -y &>> ~/setup/logs/xci-installer.log
fi  
if [ "$(dpkg -s pastebinit | grep -i "Status:" | awk '{print $4}' 2>/dev/null)" != "installed" ]; then
    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Installing required tools..." 3 45
    aptitude install pastebinit -y &>> ~/setup/logs/xci-installer.log
fi
if [ ! -e XCI_License.GPL ]; then
wget http://dl.dropbox.com/u/4325533/XCI/XCI_License.GPL &>> ~/setup/logs/xci-script-upgrade.log
fi
function f_AgtB(){
    cd $APPLOC
    wget http://dl.dropbox.com/u/4325533/XCI/version-check &>> ~/setup/logs/xci-script-upgrade.log
    if [ "$BETA" != "true" ]; then
        a=$(grep "VERSION" version-check | awk -F\" '{print $(NF-1)}')
    elif [ "$BETA" = "true" ]; then
        a=$(grep "BETAVER" version-check | awk -F\" '{print $(NF-1)}')
    fi  
    b=$VERSION
    if [ "${a}" != "" -a "${b}" != "" ]
    then
        len_a=${#a}
        len_b=${#b}
        if [ $len_a -gt $len_b ]
        then
            b=${b}`f_add_zeros $(( $len_a - $len_b ))`
        else
            a=${a}`f_add_zeros $(( $len_b - $len_a ))`
        fi
        a=`echo $a | sed 's/\.//'`
        b=`echo $b | sed 's/\.//'`
        if [ $a -gt $b ]
        then
            echo 1
        else
            echo 0
        fi
    fi
}

function f_add_zeros(){
    i=0
    while [ $i -lt $1 ]
    do
        out=${out}0
        ((i++))
    done
    echo $out
}

function Update_Check(){
while [ `f_AgtB $a $b` == 1 ] ; do
    if [ "$BETA" != "true" ]; then
        NEWVERSION=$(grep "VERSION" version-check | awk -F\" '{print $(NF-1)}')
        NEWINFOTEXT=$(grep "INFOTEXT" version-check | awk -F\" '{print $(NF-1)}')
    elif [ "$BETA" = "true" ]; then
        NEWVERSION=$(grep "BETAVER" version-check | awk -F\" '{print $(NF-1)}')
        NEWINFOTEXT=$(grep "BETAINFOTEXT" version-check | awk -F\" '{print $(NF-1)}')
    fi  
    dialog --colors --yes-label "Yes Please" --no-label "Not Now" --help-button --help-label "Release Notes" --title "\Z1[ INFORMATION ]\Zn" --yesno "\nXCI Version $NEWVERSION is now available to download.\nWould you like to download it now or later?" 8 51
    case $? in
        0)
            dialog --colors --title "\Z1[ UPDATING ]\Zn" --infobox "   Please wait..." 3 25
            rm -f xbmc-installer.sh &>> ~/setup/logs/xci-script-upgrade.log
            rm -f xci.sh &>> ~/setup/logs/xci-script-upgrade.log
            if [ "$BETA" != "true" ]; then
                wget http://dl.dropbox.com/u/4325533/XCI/xci.sh &>> ~/setup/logs/xci-script-upgrade.log
            elif [ "$BETA" = "true" ]; then
                wget http://dl.dropbox.com/u/4325533/XCI/Beta/xci.sh &>> ~/setup/logs/xci-script-upgrade.log
            fi  
            chmod +x xci.sh
            ln -s xci.sh xbmc-installer.sh
            sudo ./xci.sh
            exit 1;;
        1)
            break;;
        2)
            dialog --colors --title "\Z1[ INFORMATION ]\Zn" --msgbox "$NEWINFOTEXT" 20 60;;
    esac
done
cd $APPLOC
rm -fr version-check* &>/dev/null
}
Update_Check
####### DETERMINE OPERATING SYSTEM ########
# Make sure we have egrep
EGREP_VER=`egrep --version | head -n 1`
if [ "${EGREP_VER:0:8}" != "GNU grep" ] ; then
    echo "egrep is Not installed, Sorry."
    exit 1
fi

# Make sure we have /etc/issue
if [ ! -r '/etc/issue' ] ; then
    echo "/etc/issue isn't readable."
    exit 1
fi
# Run checks
JAUNTY_OS=`egrep -i 'Ubuntu 9.04' /etc/issue`
KARMIC_OS=`egrep -i 'Ubuntu 9.10' /etc/issue`
if [ ${#JAUNTY_OS} -gt 0 ] ; then
    CUR_OS="jaunty"
    CUR_KER="Ubuntu 9.04"
elif [ ${#KARMIC_OS} -gt 0 ] ; then
    CUR_OS="karmic"
    CUR_KER="Ubuntu 9.10"
else
    CUR_OS="unknown"
dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox " You are not using a supported OS! \n Only Ubuntu 9.04 Jaunty Jackalope or\n Ubuntu 9.10 Karmic Koala Are Supported! " 5 45
exit 1
fi

##### MAIN INSTALL SCRIPT #####
function Main_Install(){
    while true
    do
    nvidiachoice=""
    dialog  --clear  --cancel-label "Go Back" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ CHOOSE VERSION NVIDIA DRIVER TO INSTALL ]\Zn" \
            --menu "\n XBMC needs Video Drivers to work! \n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 17 50 4 \
            1 "NVIDIA Display Driver 185 Default" \
            2 "NVIDIA Display Driver 190 Stable" \
            3 "NVIDIA Display Driver 195 New" \
        4 "NVIDIA Display Driver 256 Newer " 2>/tmp/xci/nvidiamenu
    case $? in
      0)
        nvidiamenuitem=$(</tmp/xci/nvidiamenu)
        case $nvidiamenuitem in
            1) nvidiachoice=185;;
            2) nvidiachoice=190;;
            3) nvidiachoice=195;;
            4) nvidiachoice=256;;
        esac;;
      1)
            break;;
      255)
            break;;
    esac

    ##--[ BOOT SELECTOR PROMPT ]---------------------------------------------------------------
    while true
    do
    bootscrnchoice=""
    dialog  --clear --cancel-label "Go Back" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ SELECT BOOT SCREEN TO INSTALL ]\Zn" \
            --menu "\n This is the splash you see during boot time\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 17 50 4 \
            1 "Black & Silver" \
            2 "Pulsating Logo" \
            3 "Spinner Black" \
            4 "Spinner Blue" 2>/tmp/xci/bootmenu
     
    case $? in
      0)
        bootmenuitem=$(</tmp/xci/bootmenu)
        case $bootmenuitem in
            1) bootscrnchoice=black-silver;;
            2) bootscrnchoice=pulse;;
            3) bootscrnchoice=black-spin;;
            4) bootscrnchoice=blue-spin;;
        esac;;
      1)
            break;;
      255)
            break;;
    esac

    ##--[ SCREEN RES SELECTOR PROMPT ]---------------------------------------------------------------
    while true;    do
    scrnreschoice=""
    dialog  --clear --cancel-label "Go Back" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ SELECT SCREEN RESOLUTION ]\Zn" \
            --menu "\n This will set the boot screen resolution\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 17 50 4 \
            1 "1080p" \
            2 "720p" \
            3 "1360 x 768" \
            4 "1024 x 768" 2>/tmp/xci/scrnresmenu
     
    case $? in
      0)
        scrnresmenuitem=$(</tmp/xci/scrnresmenu)
        case $scrnresmenuitem in
            1) scrnreschoice=1080p;;
            2) scrnreschoice=720p;;
            3) scrnreschoice=1360;;
            4) scrnreschoice=1024;;
        esac;;
      1)
            break;;
      255)
            break;;
    esac

    ##--[ ALSA PROMPT ]---------------------------------------------------------------
    while true
    do
    alsachoice=""
    dialog  --clear --cancel-label "Go Back" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ SELECT ALSA VERSION TO INSTALL ]\Zn" \
            --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 14 50 2 \
            1 "Standard $CUR_KER Version" \
            2 "1.0.22.1 Version" 2>/tmp/xci/alsamenu

    case $? in
      0)
        alsamenuitem=$(</tmp/xci/alsamenu)
        case $alsamenuitem in
            1) alsachoice=standard;;
            2) alsachoice=1.0.22.1;;
        esac;;
      1)
            break;;
      255)
            break;;
    esac

    ##--[ FILESYSTEM PROMPT ]---------------------------------------------------------------
    while true;    do
    smbfsfilesystem="no"
    nfsfilesystem="no"
    dialog  --clear --cancel-label "Go Back" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ PLEASE CHOOSE A SHARE FILE SYSTEM ]\Zn" \
            --checklist "\n Please select what additional file system\n to add\n\n Press space to (de)select items:" 14 50 2 \
            1 "SMB/CIFS Share File System" ON \
            2 "NFS Share File System" ON 2>/tmp/xci/filesystemmenu
    case $? in
        0)
            filesystemmenuitem=$(</tmp/xci/filesystemmenu)
            case $filesystemmenuitem in
                *1*) smbfsfilesystem="yes";;&
                *2*) nfsfilesystem="yes";;
            esac;;
        1)
            break;;
        255)
            break;;
    esac

    ##--[ READY PROMPT ]---------------------------------------------------------------
    while true ;do
    dialog  --clear --colors --cancel-label "Go Back" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z4[ INSTALL SUMMARY ]\Zn" --yesno "\n Below is what you have selected to install:\n\n\
    \Z4      nVidia Driver Version: \Z1$nvidiachoice\n \
    \Z4     Bootscreen: \Z1$bootscrnchoice\n \
    \Z4     Screen Reslolution: \Z1$scrnreschoice\n \
    \Z4     Alsa Version: \Z1$alsachoice\n \
    \Z4     Install SMB Filesystem: \Z1$smbfsfilesystem\n \
    \Z4     NFS Filesystem: \Z1$nfsfilesystem\n\Zn \
    \Z4     WOL Address: \Z1$(ifconfig | grep HW | awk '{print $5}')\Zn \
    \n\n\Z1                ## WARNING ##\Zn\n \
    \n\Z8 Once \Z4XBMC\Zn install has completed, Please run\n script again to setup \Z1Remote\Zn, \Z1Sensors\Zn \Z8or\n anything else your system may require! " 20 50
    case $? in
        0)
# Hardware Blocking - Add here the hardware that needs to be blocked
            echo "0" | dialog --colors --title "\Z1[ INSTALLING ]\Zn" --gauge "  Please wait..." 6 70 0
            echo blacklist snd_ca0106 >> /etc/modprobe.d/blacklist.conf
            echo blacklist xpad >> /etc/modprobe.d/blacklist.conf
            aptitude install python-software-properties -y &>> ~/setup/logs/xci-installer.log
            echo "3" | dialog --colors --title "\Z1[ INSTALLING ]\Zn" --gauge "  Please wait..." 6 70 0
            aptitude install unzip -y &>> ~/setup/logs/xci-installer.log
            echo "4" | dialog --colors --title "\Z1[ INSTALLING ]\Zn" --gauge "  Please wait..." 6 70 0
            aptitude install pkg-config -y &>> ~/setup/logs/xci-installer.log
            if [ "$CUR_OS" = "karmic" ]; then
# ADDING XBMC REPOSITORIES Repositories make it easier to download and stay up-to-date
                echo "5" | dialog --colors --title "\Z1[ INSTALLING REPOSITORY ]\Zn" --gauge "  XBMC PPA! Please wait..." 6 70 0
                add-apt-repository ppa:team-xbmc/ppa &>> ~/setup/logs/xci-installer.log
                echo "10" | dialog --colors --title "\Z1[ INSTALLING REPOSITORY ]\Zn" --gauge "  NVIDIA PPA! Please wait..." 6 70 0
                add-apt-repository ppa:nvidia-vdpau/ppa &>> ~/setup/logs/xci-installer.log
## [ lm-sensors v3.1.1 Repositories ] ## >> /etc/apt/sources.list
                echo "15" | dialog --colors --title "\Z1[ INSTALLING REPOSITORY ]\Zn" --gauge "  LM-SENSORS PPA! Please wait..." 6 70 0
                add-apt-repository ppa:ari-tczew/ppa &>> ~/setup/logs/xci-installer.log
            elif [ "$CUR_OS" = "jaunty" ]; then
# ADDING XBMC REPOSITORIES Repositories make it easier to download and stay up-to-date
                echo "2" | dialog --colors --title "\Z1[ INSTALLING REPOSITORY ]\Zn" --gauge "  XBMC PPA! Please wait..." 6 70 0
                echo  >> /etc/apt/sources.list
                echo '#' XBMC Repositories >> /etc/apt/sources.list
                echo deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu jaunty main >> /etc/apt/sources.list
                echo deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu jaunty main >> /etc/apt/sources.list
                echo "4" | dialog --colors --title "\Z1[ INSTALLING REPOSITORY ]\Zn" --gauge "  NVIDIA PPA! Please wait..." 6 70 0
                echo  >> /etc/apt/sources.list
                echo '#' NVIDIA Repositories >> /etc/apt/sources.list
                echo deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu jaunty main >> /etc/apt/sources.list
                echo deb-src http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu jaunty main >> /etc/apt/sources.list
#  Alsa v1.0.20 Repositories ]## >> /etc/apt/sources.list 
                echo "6" | dialog --colors --title "\Z1[ INSTALLING REPOSITORY ]\Zn" --gauge "  ALSA PPA! Please wait..." 6 70 0
                echo  >> /etc/apt/sources.list
                echo '#' ALSA 1.0.20 Repositories >> /etc/apt/sources.list
                echo deb http://ppa.launchpad.net/mark-catley/ppa/ubuntu jaunty main >> /etc/apt/sources.list 
                echo deb-src http://ppa.launchpad.net/mark-catley/ppa/ubuntu jaunty main >> /etc/apt/sources.list 
# lm-sensors v3.1.2 Repositories ] ## >> /etc/apt/sources.list
                echo "8" | dialog --colors --title "\Z1[ INSTALLING REPOSITORY ]\Zn" --gauge "  LM-SENSORS PPA! Please wait..." 6 70 0
                echo  >> /etc/apt/sources.list
                echo '#' LM-SENSORS V3.1.2 Repositories >> /etc/apt/sources.list
                echo deb http://ppa.launchpad.net/ari-tczew/ppa/ubuntu jaunty main >> /etc/apt/sources.list
                echo deb-src http://ppa.launchpad.net/ari-tczew/ppa/ubuntu jaunty main >> /etc/apt/sources.list
# Lirc 0.8.6 Repositories ] ## >> /etc/apt/sources.list
                echo "10" | dialog --colors --title "\Z1[ INSTALLING REPOSITORY ]\Zn" --gauge "  LIRC PPA! Please wait..." 6 70 0
                echo  >> /etc/apt/sources.list
                echo '#' Lirc v0.8.6 Repositories >> /etc/apt/sources.list
                echo deb  http://ppa.launchpad.net/jyoder/ppa/ubuntu jaunty main>> /etc/apt/sources.list
                echo deb-src http://ppa.launchpad.net/jyoder/ppa/ubuntu jaunty main >> /etc/apt/sources.list
                echo "15" | dialog --colors --title "\Z1[ GRABBING REPOSITORY KEYS ]\Zn" --gauge "  Please wait..." 6 70 0
                apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 91E7EE5E CEC06767 EFF0FF8D AA700EA2 73F08E40 &>> ~/setup/logs/xci-installer.log 
                gpg --keyserver pgp.mit.edu --recv 1DABDBB4CEC06767 && gpg --export --armor 1DABDBB4CEC06767 | apt-key add - && aptitude update &>> ~/setup/logs/xci-installer.log
            fi
#  BACKUP GPG KEY CHECK 
            for APT in `find /etc/apt/ -name *.list`; do
                grep -o "^deb http://ppa.launchpad.net/[a-z0-9\-]\+/[a-z0-9\-]\+" $APT | while read ENTRY ; do
# work out the referenced user and their ppa
                    USER=`echo $ENTRY | cut -d/ -f4`
                    PPA=`echo $ENTRY | cut -d/ -f5`
# some legacy PPAs say 'ubuntu' when they really mean 'ppa', fix that up
                    if [ "ubuntu" = "$PPA" ]
                    then
                        PPA=ppa
                    fi
# scrape the ppa page to get the keyid
                    KEYID=`wget -q --no-check-certificate https://launchpad.net/~$USER/+archive/$PPA -O- | grep -o "1024R/[A-Z0-9]\+" | cut -d/ -f2`
                    apt-key adv --list-keys $KEYID >/dev/null 2>&1 
                    if [ $? != 0 ]; then
                    echo Trying 2nd kerserver to grab key $KEYID for archive $PPA by ~$USER &>> ~/setup/logs/xci-installer.log
                apt-key adv --recv-keys --keyserver keys.gnupg.net $KEYID &>> ~/setup/logs/xci-installer.log
                else
                    echo 2nd keyserver was not needed you already have key $KEYID for archive $PPA by ~$USER &>> ~/setup/logs/xci-installer.log
                fi
                apt-key adv --list-keys $KEYID >/dev/null 2>&1 
                if [ $? != 0 ]; then
                        echo Trying 3rd kerserver to grab key $KEYID for archive $PPA by ~$USER &>> ~/setup/logs/xci-installer.log
                        apt-key adv --recv-keys --keyserver pool.sks-keyservers.net $KEYID &>> ~/setup/logs/xci-installer.log
                else
                    echo 3rd keyserver was not needed you already have key $KEYID for archive $PPA by ~$USER &>> ~/setup/logs/xci-installer.log
                fi
                apt-key adv --list-keys $KEYID >/dev/null 2>&1 
                if [ $? != 0 ]; then
                        echo Trying 4th kerserver to grab key $KEYID for archive $PPA by ~$USER &>> ~/setup/logs/xci-installer.log
                        apt-key adv --recv-keys --keyserver pool.subkeys.pgp.net $KEYID &>> ~/setup/logs/xci-installer.log
                else
                        echo 4th keyserver was not needed you already have key $KEYID for archive $PPA by ~$USER &>> ~/setup/logs/xci-installer.log
                fi
                done
            done
# RUNNING A SYSTEM UPDATE TO GET LATEST VERSION OF PACKAGES 
            echo "20" | dialog --colors --title "\Z1[ CHECKING FOR SYSTEM UPDATES ]\Zn" --gauge "  Please wait..." 6 70 0
            aptitude update -y &>> ~/setup/logs/xci-installer.log
# INSTALLS XBMC Media Center 
            if [ "$CUR_OS" = "karmic" ]; then
                echo "25" | dialog --colors --title "\Z1[ INSTALLING XBMC ]\Zn" --gauge "  Please wait..." 6 70 0
                aptitude install xinit -y &>> ~/setup/logs/xci-installer.log
                echo "30" | dialog --colors --title "\Z1[ INSTALLING XBMC ]\Zn" --gauge "  Please wait..." 6 70 0
                aptitude install x11-xserver-utils -y &>> ~/setup/logs/xci-installer.log
                echo "35" | dialog --colors --title "\Z1[ INSTALLING XBMC ]\Zn" --gauge "  Please wait..." 6 70 0
                aptitude install xbmc -y &>> ~/setup/logs/xci-installer.log
                echo "40" | dialog --colors --title "\Z1[ INSTALLING XBMC ] ]\Zn" --gauge "  Please wait..." 6 70 0
                aptitude install ~nxbmc-eventclients -y &>> ~/setup/logs/xci-installer.log
                echo "45" | dialog --colors --title "\Z1[ INSTALLING XBMC ] ]\Zn" --gauge "  Please wait..." 6 70 0
                aptitude install ~nnxbmc-scripts -y &>> ~/setup/logs/xci-installer.log
            elif [ "$CUR_OS" = "jaunty" ]; then
                echo "25" | dialog --colors --title "\Z1[ INSTALLING XBMC ] ]\Zn" --gauge "  Please wait..." 6 70 0
                aptitude install xorg xinit -y &>> ~/setup/logs/xci-installer.log
                echo "30" | dialog --colors --title "\Z1[ INSTALLING XBMC ] ]\Zn" --gauge "  Please wait..." 6 70 0
                aptitude install x11-xserver-utils -y &>> ~/setup/logs/xci-installer.log
                echo "35" | dialog --colors --title "\Z1[ INSTALLING XBMC ] ]\Zn" --gauge "  Please wait..." 6 70 0
                aptitude install xbmc -y &>> ~/setup/logs/xci-installer.log
                echo "40" | dialog --colors --title "\Z1[ INSTALLING XBMC ] ]\Zn" --gauge "  Please wait..." 6 70 0
                aptitude install ~nxbmc-eventclients -y &>> ~/setup/logs/xci-installer.log
                echo "45" | dialog --colors --title "\Z1[ INSTALLING XBMC ] ]\Zn" --gauge "  Please wait..." 6 70 0
                aptitude install ~nxbmc-scripts -y &>> ~/setup/logs/xci-installer.log
            fi
# INSTALL GENERIC NVIDIA GRAPHIC DRIVERS 
                echo "50" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  Please wait..." 6 70 0
                aptitude install linux-headers-generic -f -y &>> ~/setup/logs/xci-installer.log
            if [ "$nvidiachoice" = "185" ]; then
                echo "55" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION: $nvidiachoice, Please wait..." 6 70 0
                aptitude install nvidia-glx-185 -f -y &>> ~/setup/logs/xci-installer.log
                echo "60" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION: $nvidiachoice, Please wait..." 6 70 0
                aptitude install nvidia-glx-185-dev -f -y &>> ~/setup/logs/xci-installer.log
echo "65" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
                aptitude install vdpauinfo -f -y &>> ~/setup/logs/xci-installer.log
                echo "67" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
                aptitude install libvdpau-dev -f -y &>> ~/setup/logs/xci-installer.log
                echo "68" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
                aptitude install libvdpau1 -f -y &>> ~/setup/logs/xci-installer.log
            elif [ "$nvidiachoice" = "190" ]; then
                echo "55" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION: $nvidiachoice, Please wait..." 6 70 0
                aptitude install nvidia-glx-190 -f -y &>> ~/setup/logs/xci-installer.log
                echo "60" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION: $nvidiachoice, Please wait..." 6 70 0
                aptitude install nvidia-glx-190-dev -f -y &>> ~/setup/logs/xci-installer.log
                echo "65" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
                aptitude install vdpauinfo -f -y &>> ~/setup/logs/xci-installer.log
                echo "67" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
                aptitude install libvdpau-dev -f -y &>> ~/setup/logs/xci-installer.log
                echo "68" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
                aptitude install libvdpau1 -f -y &>> ~/setup/logs/xci-installer.log
            elif [ "$nvidiachoice" = "195" ]; then
                echo "55" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION: $nvidiachoice, Please wait..." 6 70 0
                aptitude install nvidia-glx-195 -f -y &>> ~/setup/logs/xci-installer.log
                echo "60" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION: $nvidiachoice, Please wait..." 6 70 0
                aptitude install nvidia-glx-195-dev -f -y &>> ~/setup/logs/xci-installer.log
                echo "65" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
                aptitude install vdpauinfo -f -y &>> ~/setup/logs/xci-installer.log
                echo "67" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
                aptitude install libvdpau-dev -f -y &>> ~/setup/logs/xci-installer.log
                echo "68" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
                aptitude install libvdpau1 -f -y &>> ~/setup/logs/xci-installer.log
            elif [ "$nvidiachoice" = "256" ]; then
                echo "55" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION: $nvidiachoice, Please wait..." 6 70 0
                aptitude install nvidia-glx-256 -f -y &>> ~/setup/logs/xci-installer.log
                echo "60" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION: $nvidiachoice, Please wait..." 6 70 0
                aptitude install nvidia-glx-256-dev -f -y &>> ~/setup/logs/xci-installer.log
                echo "65" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
                aptitude install vdpauinfo -f -y &>> ~/setup/logs/xci-installer.log
                echo "67" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
                aptitude install libvdpau-dev -f -y &>> ~/setup/logs/xci-installer.log
                echo "68" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
                aptitude install libvdpau1 -f -y &>> ~/setup/logs/xci-installer.log            
            fi
            modprobe nvidia &>> ~/setup/logs/xci-installer.log
# GENERATE XORG.CONF 
            echo "70" | dialog --colors --title "\Z1[ CONFIGURING XORG ]\Zn" --gauge "  ADDING XORG TWEAKS! Please wait..." 6 70 0
            nvidia-xconfig -s --no-logo --force-generate &>> ~/setup/logs/xci-installer.log
# ADDING HWcursor fix 
            sed -i '37i\    Option         "HWCursor" "False"' /etc/X11/xorg.conf
# ENABLE 1080p 24Hz
            sed -i '38i\    Option         "ExactModeTimingsDVI" "TRUE"' /etc/X11/xorg.conf
            sed -i '52i\    Option         "FlatPanelProperties" "Scaling = Native"' /etc/X11/xorg.conf
            sed -i '53i\    Option         "DynamicTwinView" "False"' /etc/X11/xorg.conf
# Disable Composite for better H264 acceleration 
            sed -i '59i\ ' /etc/X11/xorg.conf
            sed -i '60i\Section "Extensions"' /etc/X11/xorg.conf
            sed -i '61i\    Option         "Composite" "Disable"' /etc/X11/xorg.conf
            sed -i '62i\EndSection' /etc/X11/xorg.conf
# INSTALL DNS LOOKUP 
# This allows SSH to use local domain names (XBMCLive.local)
            echo "72" | dialog --colors --title "\Z1[ INSTALLING DNS LOOK-UP! ]\Zn" --gauge "  Please wait..." 6 70 0
            aptitude install avahi-daemon -y &>> ~/setup/logs/xci-installer.log
# INSTALL SMBFS/NFS ]------------------------------------------------------------
# This allows SMB/NFS shares to be mounted in FSTAB
            if [ "$smbfsfilesystem" = "yes" -a "$nfsfilesystem" != "yes" ]; then
                echo "75" | dialog --colors --title "\Z1[ INSTALLING SMB/CIFS SHARE FILE SYSTEM ]\Zn" --gauge "  Please wait..." 6 70 0
                aptitude install smbfs smbclient libsmbclient -y &>> ~/setup/logs/xci-installer.log
            fi
            if [ "$nfsfilesystem" = "yes" -a "$smbfsfilesystem" != "yes" ]; then
                echo "75" | dialog --colors --title "\Z1[ INSTALLING NFS SHARE FILE SYSTEM ]\Zn" --gauge "  Please wait..." 6 70 0
                aptitude install nfs-common -y  &>> ~/setup/logs/xci-installer.log
            fi
            if [ "$nfsfilesystem" = "yes" -a "$smbfsfilesystem" = "yes" ]; then
                echo "75" | dialog --colors --title "\Z1[ INSTALLING SMB & NFS SHARE FILE SYSTEMS ]\Zn" --gauge "  Please wait..." 6 70 0
                aptitude install nfs-common smbfs smbclient libsmbclient -y &>> ~/setup/logs/xci-installer.log
            fi
        
# INSTALL XBMC Bootscreen 
            echo "78" | dialog --colors --title "\Z1[ INSTALLING BOOT SCREEN ]\Zn" --gauge "  Please wait..." 6 70 0
            aptitude install ~nusplash-theme-xbmc -y &>> ~/setup/logs/xci-installer.log
            if [ "$bootscrnchoice" = "black-silver" ]; then
                update-alternatives --set usplash-artwork.so /usr/lib/usplash/xbmc-splash-spinner-black-silver.so &>> ~/setup/logs/xci-installer.log
            elif [ "$bootscrnchoice" = "pulse" ]; then
                update-alternatives --set usplash-artwork.so /usr/lib/usplash/xbmc-splash-pulsating-logo.so &>> ~/setup/logs/xci-installer.log
            elif [ "$bootscrnchoice" = "black-spin" ]; then
                update-alternatives --set usplash-artwork.so /usr/lib/usplash/xbmc-splash-spinner-black.so &>> ~/setup/logs/xci-installer.log
            elif [ "$bootscrnchoice" = "blue-spin" ]; then
                update-alternatives --set usplash-artwork.so /usr/lib/usplash/xbmc-splash-spinner-spinner-blue.so &>> ~/setup/logs/xci-installer.log
            fi
            rm -f /etc/usplash.conf
            if [ "$CUR_OS" = "karmic" ]; then
                if [ "$scrnreschoice" = "1080p" ]; then
                    echo xres=1920 > /etc/usplash.conf
                    echo yres=1080 >> /etc/usplash.conf
                elif [ "$scrnreschoice" = "720p" ]; then
                    echo xres=1280 > /etc/usplash.conf
                    echo yres=720 >> /etc/usplash.conf
                elif [ "$scrnreschoice" = "1360" ]; then
                    echo xres=1360 > /etc/usplash.conf
                    echo yres=768 >> /etc/usplash.conf
                elif [ "$scrnreschoice" = "1024" ]; then
                    echo xres=1024 > /etc/usplash.conf
                    echo yres=768 >> /etc/usplash.conf
                fi
            elif [ "$CUR_OS" = "jaunty" ]; then
                if [ "$scrnreschoice" = "1080p" ]; then
                    echo xres=1920 > /etc/initramfs-tools/usplash.conf
                    echo yres=1080 >> /etc/initramfs-tools/usplash.conf
                elif [ "$scrnreschoice" = "720p" ]; then
                    echo xres=1280 > /etc/initramfs-tools/usplash.conf
                    echo yres=720 >> /etc/initramfs-tools/usplash.conf
                elif [ "$scrnreschoice" = "1360" ]; then
                    echo xres=1360 > /etc/initramfs-tools/usplash.conf
                    echo yres=768 >> /etc/initramfs-tools/usplash.conf
                elif [ "$scrnreschoice" = "1024" ]; then
                    echo xres=1024 > /etc/initramfs-tools/usplash.conf
                    echo yres=768 >> /etc/initramfs-tools/usplash.conf
                fi
            fi
            update-initramfs -u &>> ~/setup/logs/xci-installer.log
        
# INSTALL AND CONFIGURE ALSA SOUND 
            cd ~/setup
            if [ "$alsachoice" = "standard" ]; then
                echo "80" | dialog --colors --title "\Z1[ INSTALLING STANDARD ALSA ]\Zn" --gauge "  ALSA INSTALLING! Please wait..." 6 70 0
                aptitude install linux-sound-base -y &>> ~/setup/logs/xci-installer.log
                echo "87" | dialog --colors --title "\Z1[ INSTALLING STANDARD ALSA ]\Zn" --gauge "  INSTALLING ALSA DRIVERS! Please wait..." 6 70 0
                aptitude install alsa-base -y &>> ~/setup/logs/xci-installer.log
                echo "90" | dialog --colors --title "\Z1[ INSTALLING STANDARD ALSA ]\Zn" --gauge "  INSTALLING ALSA UTILITIES! Please wait..." 6 70 0
                aptitude install alsa-utils -y &>> ~/setup/logs/xci-installer.log
            elif [ "$alsachoice" = "1.0.22.1" ]; then
                cp /etc/apt/sources.list /etc/apt/sources.list backup &>> ~/setup/logs/xci-installer.log
                echo "80" | dialog --colors --title "\Z1[ INSTALLING 1.0.22.1 ALSA ]\Zn" --gauge "  ADDING ALSA PPA! Please wait..." 6 70 0
                add-apt-repository ppa:pgquiles/ppa &>> ~/setup/logs/xci-installer.log
                aptitude update -y &>> ~/setup/logs/xci-installer.log
                echo "84" | dialog --colors --title "\Z1[ INSTALLING 1.0.22.1 ALSA ]\Zn" --gauge "  INSTALLING ALSA! Please wait..." 6 70 0
                aptitude install linux-sound-base -y &>> ~/setup/logs/xci-installer.log
                echo "87" | dialog --colors --title "\Z1[ INSTALLING 1.0.22.1 ALSA ]\Zn" --gauge "  INSTALLING ALSA DRIVERS! Please wait..." 6 70 0
                aptitude install alsa-base -y &>> ~/setup/logs/xci-installer.log
                echo "90" | dialog --colors --title "\Z1[ INSTALLING 1.0.22.1 ALSA ]\Zn" --gauge "  INSTALLING ALSA UTILITIES! Please wait..." 6 70 0
                aptitude install alsa-utils -y &>> ~/setup/logs/xci-installer.log
                cp /etc/apt/sources.list-backup /etc/apt/sources.list &>> ~/setup/logs/xci-installer.log
            fi
            usermod -a -G audio xbmc &>> ~/setup/logs/xci-installer.log
        
# INSTALLING XBMC HELPERS 
            echo "92" | dialog --colors --title "\Z1[ INSTALLING XBMC HELPERS ]\Zn" --gauge "  Please wait..." 6 70 0
            aptitude install xbmc-live python-apt -y &>> ~/setup/logs/xci-installer.log
            mkdir /home/xbmc/.xbmc &>> ~/setup/logs/xci-installer.log
            mkdir /home/xbmc/.xbmc/userdata &>> ~/setup/logs/xci-installer.log
# INSTALL XBMC SVN Repo Installer --deprecated in 10.08 ok for this 9.11
            mkdir /home/xbmc/.xbmc/plugins/ &>> ~/setup/logs/xci-installer.log
            mkdir /home/xbmc/.xbmc/plugins/programs &>> ~/setup/logs/xci-installer.log
            cd /home/xbmc/.xbmc/plugins/programs
            wget http://xbmc-addons.googlecode.com/svn/packages/plugins/programs/SVN_Repo_Installer.zip &>> ~/setup/logs/xci-installer.log
            unzip -o SVN_Repo_Installer.zip &>> ~/setup/logs/xci-installer.log
            rm SVN_Repo_Installer.zip &>> ~/setup/logs/xci-installer.log
            chown -R xbmc:xbmc /home/xbmc &>> ~/setup/logs/xci-installer.log
# GRANT XBMC POWER ACCESS this allows xbmc to control power managment
            echo "95" | dialog --colors --title "\Z1[ CONFIGURING POWER MANAGEMENT ]\Zn" --gauge "  Please wait..." 6 70 0
            aptitude install pm-utils policykit -y &>> ~/setup/logs/xci-installer.log
            polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.suspend &>> ~/setup/logs/xci-installer.log
            polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.hibernate &>> ~/setup/logs/xci-installer.log
            polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.reboot &>> ~/setup/logs/xci-installer.log
            polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.shutdown &>> ~/setup/logs/xci-installer.log
            polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.reboot-multiple-sessions &>> ~/setup/logs/xci-installer.log
            polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.shutdown-multiple-sessions &>> ~/setup/logs/xci-installer.log
            if [ "$CUR_OS" = "karmic" ]; then
                    sed -i 's/xbmc=autostart,nodiskmount,setvolume loglevel=0/vga=788 xbmc=autostart,nodiskmount,setvolume loglevel=0 usbcore.autosuspend=-1/g' /etc/default/grub
                    update-grub &>> ~/setup/logs/xci-installer.log
            elif [ "$CUR_OS" = "jaunty" ]; then
                    sed -i 's/xbmc=autostart,nodiskmount,setvolume loglevel=0/xbmc=autostart,nodiskmount,setvolume loglevel=0 usbcore.autosuspend=-1/g' /boot/grub/menu.lst
            fi

# SETTINNG-UP WOL you can wake your system with a magic packet
            echo "96" | dialog --colors --title "\Z1[ CONFIGURING WAKE ON LAN ]\Zn" --gauge "  Please wait..." 6 70 0
            aptitude install ethtool
            echo '#!/bin/bash' > /etc/init.d/wakeonlanconfig
            echo 'ethtool -s eth0 wol g' >> /etc/init.d/wakeonlanconfig
            echo 'exit' >> /etc/init.d/wakeonlanconfig
            chmod a+x /etc/init.d/wakeonlanconfig &>> ~/setup/logs/xci-installer.log
            update-rc.d -f wakeonlanconfig defaults &>> ~/setup/logs/xci-installer.log
# FINAL SYSTEM UPGRADE 
            echo "97" | dialog --colors --title "\Z1[ INSTALLING SYSTEM UPDATES ]\Zn" --gauge "  Please wait..." 6 70 0
            if [ "$CUR_OS" = "karmic" ]; then
                    aptitude install ureadahead -y &>> ~/setup/logs/xci-installer.log
            elif [ "$CUR_OS" = "jaunty" ]; then
                    aptitude install sreadahead -y &>> ~/setup/logs/xci-installer.log
            fi
            aptitude update &>> ~/setup/logs/xci-installer.log
            case $(aptitude safe-upgrade -s -y | grep -i "grub") in
                *grub*) wget http://dl.dropbox.com/u/4953107/XCI/grub-input 2>>~/setup/logs/xci-installer.log; aptitude safe-upgrade -y <grub-input &>> ~/setup/logs/xci-installer.log; rm grub-input &>> ~/setup/logs/xci-installer.log;;
                *) aptitude safe-upgrade -y &>> ~/setup/logs/xci-installer.log;;
            esac
#            sed -i 's/#Banner/Banner/g' /etc/ssh/sshd_config
            echo "100" | dialog --sleep 1 --colors --title "\Z1[ INSTALLATION FINISHED ]\Zn" --gauge "  System will reboot now" 6 70 0
             reboot; logout;;
      1)
            break;;
      255)
            break;;
    esac
    done
    done
    done
    done
    done
    done
}

function Hardware_Menu(){
    while true;    do
    dialog  --clear --cancel-label "Go Back" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ HARDWARE SETUP MENU ]\Zn" \
            --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 18 50 6 \
            1 "nVidia Video Drivers" \
            2 "Sound Setup" \
            3 "Remote Controllers" \
            4 "Temperature Sensors" \
            5 "Wifi" \
            6 "Bluetooth" 2>/tmp/xci/hardwaremenu
     
    case $? in
      0)
        hardwaremenuitem=$(</tmp/xci/hardwaremenu)
        case $hardwaremenuitem in
            1) NVIDIA_Menu; break;;
            2) Sound_Menu; break;;
            3) Remotes_Menu; break;;
            4) Temp_Sensors_Menu; break;;
            5) WIFI_Setup; break;;
            6) Bluetooth_Setup; break;;
        esac;;
      1)
            break;;
      255)
            break;;
    esac
    done
}


function NVIDIA_Menu(){
    while true
    do
    nvidiareinstallchoice=""
    dialog  --clear  --cancel-label "Go Back" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION   Video Driver: $(grep -i "NVIDIA GLX Module" /var/log/Xorg.0.log | awk '{print $2,$5}')" \
            --colors --title "\Z4[ CHOOSE NVIDIA DRIVERS TO (RE)INSTALL ]\Zn" \
            --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 17 50 4 \
            1 "NVIDIA Display Driver 185 Default" \
            2 "NVIDIA Display Driver 190 Stable" \
            3 "NVIDIA Display Driver 195 New" \
            4 "NVIDIA Display Driver 256 Newer" 2>/tmp/xci/nvidiamenu
     
    case $? in
      0)
        nvidiareinstallmenuitem=$(</tmp/xci/nvidiamenu)
        case $nvidiareinstallmenuitem in
            1) nvidiareinstallchoice="Nvidia 185";;
            2) nvidiareinstallchoice="Nvidia 190";;
            3) nvidiareinstallchoice="Nvidia 195";;
            4) nvidiareinstallchoice="Nvidia 256";;
        esac;;
      1)
            Hardware_Menu; break;;
      255)
            Hardware_Menu; break;;
    esac

        if [ "$nvidiareinstallchoice" = "Nvidia 180" -o "$nvidiareinstallchoice" = "Nvidia 185" -o "$nvidiareinstallchoice" = "Nvidia 190" -o "$nvidiareinstallchoice" = "Nvidia 195" -o "$nvidiareinstallchoice" = "Nvidia 256" ]; then
            service xbmc-live stop &>> ~/setup/logs/xci-installer.log
            echo "5" | dialog --colors --title "\Z1[ INSTALLING REPOSITORY ]\Zn" --gauge "  NVIDIA PPA! Please wait..." 6 70 0
            add-apt-repository ppa:nvidia-vdpau/ppa &>> ~/setup/logs/xci-video-change.log
            echo "10" | dialog --colors --title "\Z1[ REMOVING OLD DRIVERS ]\Zn" --gauge "  Please wait..." 6 70 0
            aptitude purge ~nnvidia -f -y &>> ~/setup/logs/xci-video-change.log
            echo "30" | dialog --colors --title "\Z1[ REMOVING OLD DRIVERS ]\Zn" --gauge "  Please wait..." 6 70 0
            aptitude purge ~nvdpau -f -y &>> ~/setup/logs/xci-video-change.log
        if [ "$nvidiareinstallchoice" = "Nvidia 185" ]; then
            echo "60" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION:$nvidiareinstallchoice! Please wait..." 6 70 0
            aptitude install nvidia-glx-185 -f -y &>> ~/setup/logs/xci-video-change.log
            echo "80" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION:$nvidiareinstallchoice! Please wait..." 6 70 0
            aptitude install nvidia-glx-185-dev -f -y &>> ~/setup/logs/xci-video-change.log
            echo "90" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION:$nvidiareinstallchoice! Please wait..." 6 70 0
            aptitude install nvidia-185-libvdpau -f -y &>> ~/setup/logs/xci-video-change.log
            echo "92" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
            aptitude install libvdpau-dev -f -y &>> ~/setup/logs/xci-installer.log
            echo "98" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
        elif [ "$nvidiareinstallchoice" = "Nvidia 190" ]; then
            echo "60" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION:$nvidiareinstallchoice! Please wait..." 6 70 0
            aptitude install nvidia-glx-190 -f -y &>> ~/setup/logs/xci-video-change.log
            echo "80" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION:$nvidiareinstallchoice! Please wait..." 6 70 0
            aptitude install nvidia-glx-190-dev -f -y &>> ~/setup/logs/xci-video-change.log
            echo "90" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION:$nvidiareinstallchoice! Please wait..." 6 70 0
            aptitude install vdpauinfo -f -y &>> ~/setup/logs/xci-video-change.log
            echo "92" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
            aptitude install libvdpau-dev -f -y &>> ~/setup/logs/xci-installer.log
            echo "98" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
            aptitude install libvdpau1 -f -y &>> ~/setup/logs/xci-installer.log
        elif [ "$nvidiareinstallchoice" = "Nvidia 195" ]; then
            echo "60" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION:$nvidiareinstallchoice! Please wait..." 6 70 0
            aptitude install nvidia-glx-195 -f -y &>> ~/setup/logs/xci-video-change.log
            echo "80" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION:$nvidiareinstallchoice! Please wait..." 6 70 0
            aptitude install nvidia-glx-195-dev -f -y &>> ~/setup/logs/xci-video-change.log
            echo "90" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION:$nvidiareinstallchoice! Please wait..." 6 70 0
            aptitude install vdpauinfo -f -y &>> ~/setup/logs/xci-video-change.log
            echo "92" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
            aptitude install libvdpau-dev -f -y &>> ~/setup/logs/xci-installer.log
            echo "98" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
            aptitude install libvdpau1 -f -y &>> ~/setup/logs/xci-installer.log
              elif [ "$nvidiareinstallchoice" = "Nvidia 256" ]; then
                     echo "60" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION: $nvidiachoice, Please wait..." 6 70 0
                     aptitude install nvidia-glx-256 -f -y &>> ~/setup/logs/xci-installer.log
                     echo "80" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION: $nvidiachoice, Please wait..." 6 70 0
                     aptitude install nvidia-glx-256-dev -f -y &>> ~/setup/logs/xci-installer.log
                     echo "90" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
                     aptitude install vdpauinfo -f -y &>> ~/setup/logs/xci-installer.log
                     echo "92" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
                     aptitude install libvdpau-dev -f -y &>> ~/setup/logs/xci-installer.log
            echo "98" | dialog --colors --title "\Z1[ INSTALLING NVIDIA DRIVERS ]\Zn" --gauge "  SETTING UP VDPAU, Please wait..." 6 70 0
            aptitude install libvdpau1 -f -y &>> ~/setup/logs/xci-installer.log

        fi
        echo "100" | dialog --sleep 1 --colors --title "\Z1[ INSTALLED NVIDIA DRIVERS ]\Zn" --gauge "  NVIDIA DRIVER VERSION:$nvidiareinstallchoice Installed!" 6 70 0
        reboot &>> ~/setup/logs/xci-video-change.log
    fi
    done
}

##### HDMI SOUND INSTALL SCRIPT #####
function Sound_Menu(){
    while true
    do
    soundchoice=""
    dialog  --clear  --cancel-label "Go Back" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ SOUND SETUP OPTIONS ]\Zn" \
            --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 17 50 5 \
            1 "Enable HDMI Audio" \
            2 "Enable HDMI & Optical Audio" \
            3 "Enable USB Audio" \
            4 "Enable 5.1 Audio" \
            5 "Reset Audio" 2>/tmp/xci/hdmisoundmenu
    case $? in
      0)
        soundmenuitem=$(</tmp/xci/hdmisoundmenu)
        case $soundmenuitem in
            1) soundchoice=install_hdmi;;
            2) soundchoice=install_hdmi-optical;;
            3) soundchoice=install_usb;;
            4) soundchoice=install_PCM;;
            5) soundchoice=reset;;
        esac;;
      1)
            Hardware_Menu; break;;
      255)
            Hardware_Menu; break;;
    esac

    if [ "$soundchoice" = "install_PCM" ]; then
        dialog --colors --title "\Z1[ 5.1 CHANNEL AUDIO SETUP ]\Zn" --msgbox "\n\Z1            THIS FUNCTION IS BETA.\Zn\n\nThis may not work, though not likely a chance exists. \Z1USE AT YOUR OWN DISCRETION.\Zn\n\nThis will install \Z1alsa 1.0.22.1\Zn and \Z1nvidia drivers 256\Zn" 13 50
            service xbmc-live stop &>> ~/setup/logs/xci-sound.log
            echo "0" | dialog --colors --title "\Z1[ SETTING UP 5.1 AUDIO ]\Zn" --gauge '  Removing ALSA! Please wait...' 6 70
            aptitude purge linux-sound-base alsa-base alsa-utils -y &>> ~/setup/logs/xci-sound.log
            echo "10" | dialog --colors --title "\Z1[ SETTING UP 5.1 AUDIO ]\Zn" --gauge "  Removing nVidia Drivers! Please wait..." 6 70 0
            aptitude purge ~nnvidia -f -y &>> ~/setup/logs/xci-video-change.log
            echo "1f" | dialog --colors --title "\Z1[ SETTING UP 5.1 AUDIO ]\Zn" --gauge "  Removing nVidia Drivers! Please wait..." 6 70 0
            aptitude purge ~nvdpau -f -y &>> ~/setup/logs/xci-video-change.log
            echo "16" | dialog --colors --title "\Z1[ SETTING UP 5.1 AUDIO ]\Zn" --gauge "  Installing nVidia Drivers! Please wait..." 6 70 0
            aptitude install nvidia-glx-256 -f -y &>> ~/setup/logs/xci-video-change.log
            echo "80" | dialog --colors --title "\Z1[ SETTING UP 5.1 AUDIO ]\Zn" --gauge "  ADDING ALSA PPA! Please wait..." 6 70 0
            cp /etc/apt/sources.list /etc/apt/sources.list-backup &>> ~/setup/logs/xci-sound.log
            echo "81" | dialog --colors --title "\Z1[ SETTING UP 5.1 AUDIO ]\Zn" --gauge "  ADDING ALSA PPA! Please wait..." 6 70 0
            add-apt-repository ppa:pgquiles/ppa &>> ~/setup/logs/xci-sound.log
            aptitude update -y &>> ~/setup/logs/xci-installer.log
            echo "84" | dialog --colors --title "\Z1[ SETTING UP 5.1 AUDIO ]\Zn" --gauge "  INSTALLING ALSA 1.0.22.1! Please wait..." 6 70 0
            aptitude install linux-sound-base -y &>> ~/setup/logs/xci-sound.log
            echo "87" | dialog --colors --title "\Z1[ INSTALLING 1.0.22.1 ALSA ]\Zn" --gauge "  INSTALLING ALSA 1.0.22.1! Please wait..." 6 70 0
            aptitude install alsa-base -y &>> ~/setup/logs/xci-sound.log
            echo "90" | dialog --colors --title "\Z1[ INSTALLING 1.0.22.1 ALSA ]\Zn" --gauge "  INSTALLING ALSA 1.0.22.1! Please wait..." 6 70 0
            aptitude install alsa-utils -y &>> ~/setup/logs/xci-sound.log
            echo "18" | dialog --colors --title "\Z1[ SETTING UP 5.1 PCM ]\Zn" --gauge "  Installing nVidia Drivers! Please wait..." 6 70 0
            aptitude install nvidia-glx-256-dev -f -y &>> ~/setup/logs/xci-video-change.log
            echo "25" | dialog --colors --title "\Z1[ SETTING UP 5.1 PCM ]\Zn" --gauge "  Installing nVidia Drivers! Please wait..." 6 70 0
            aptitude install libvdpau1 -f -y &>> ~/setup/logs/xci-video-change.log
            echo "26" | dialog --colors --title "\Z1[ SETTING UP 5.1 PCM ]\Zn" --gauge "  Installing nVidia Drivers! Please wait..." 6 70 0
            aptitude install libvdpau-dev -f -y &>> ~/setup/logs/xci-video-change.log
            echo "27" | dialog --colors --title "\Z1[ SETTING UP 5.1 PCM ]\Zn" --gauge "  Installing nVidia Drivers! Please wait..." 6 70 0
            echo "92" | dialog --sleep 1 --colors --title "\Z1[ CONFIGURING 5.1 PCM setup ]\Zn" --gauge '  Please wait' 6 70
            cd $HOME/setup &>> ~/setup/logs/xci-sound.log
            cp /etc/apt/sources.list-backup /etc/apt/sources.list &>> ~/setup/logs/xci-sound.log
            cp /etc/asound.conf /etc/asound.conf-backup &>> ~/setup/logs/xci-sound.log            
            echo "94" | dialog --sleep 1 --colors --title "\Z1[ CONFIGURING 5.1 PCM setup ]\Zn" --gauge '  Please wait' 6 70
            wget http://dl.dropbox.com/u/4325533/XCI/Sound/asound.conf &>> ~/setup/logs/xci-sound.log
            mv ~/setup/asound.conf /etc/asound.conf; rm -f ~/setup/asound.conf
            echo "96" | dialog --sleep 1 --colors --title "\Z1[ CONFIGURING 5.1 PCM setup ]\Zn" --gauge '  Please wait' 6 70
            wget http://dl.dropbox.com/u/4325533/XCI/Sound/HDA-Intel.conf &>> ~/setup/logs/xci-sound.log
            cp /usr/share/alsa/cards/HDA-Intel.conf /usr/share/alsa/cards/HDA-Intel.conf-backup
            echo "98" | dialog --sleep 1 --colors --title "\Z1[ CONFIGURING 5.1 PCM setup ]\Zn" --gauge '  Please wait' 6 70
            mv ~/setup/HDA-Intel.conf /usr/share/alsa/cards/HDA-Intel.conf; rm -f /setup/HDA-Intel.conf
            echo "100" | dialog --sleep 1 --colors --title "\Z1[ COMPLETED 5.1 PCM setup ]\Zn" --gauge '  Please wait' 6 70
             reboot
    elif [ "$soundchoice" = "install_hdmi" ]; then
#    if [ "$soundchoice" = "install_hdmi" ]; then
        dialog --colors --title "\Z1[ CONFIGURING HDMI AUDIO ]\Zn" --infobox "          Please Wait..." 3 40
        cd ~/setup
        rm -f ~/.asoundrc &>> ~/setup/logs/xci-sound.log
        rm -f /etc/asound.conf &>> ~/setup/logs/xci-sound.log
        touch /etc/asound.conf
        echo 'pcm.!default {' > /etc/asound.conf
        echo ' type plug' >> /etc/asound.conf
        echo '  slave {' >> /etc/asound.conf
        echo '   pcm "hdmi"' >> /etc/asound.conf
        echo '  }' >> /etc/asound.conf
        echo '}' >> /etc/asound.conf
        chown xbmc:xbmc /etc/asound.conf &>> ~/setup/logs/xci-sound.log
        sed -i "s/<ac3passthrough>.*</<ac3passthrough>true</" /home/xbmc/.xbmc/userdata/guisettings.xml
        sed -i "s/<audiodevice>.*</<audiodevice>alsa:plug:hdmi</" /home/xbmc/.xbmc/userdata/guisettings.xml
        sed -i "s/<passthroughdevice>.*</<passthroughdevice>alsa:hdmi</" /home/xbmc/.xbmc/userdata/guisettings.xml
        sed -i "s/<mode>0</<mode>1</" /home/xbmc/.xbmc/userdata/guisettings.xml
        service xbmc-live stop &>> ~/setup/logs/xci-sound.log; sleep 3; service xbmc-live start &>> ~/setup/logs/xci-sound.log
    elif [ "$soundchoice" = "install_hdmi-optical" ]; then
        dialog --colors --title "\Z1[ CONFIGURING HDMI AUDIO ]\Zn" --infobox "          Please Wait..." 3 40
        cd ~/setup
        rm -f ~/.asoundrc &>> ~/setup/logs/xci-sound.log
        rm -f /etc/asound.conf &>> ~/setup/logs/xci-sound.log
        touch /etc/asoundrc.conf
        echo 'pcm.!default {' > /etc/asound.conf
        echo ' type plug' >> /etc/asound.conf
        echo '  slave {' >> /etc/asound.conf
        echo '   pcm "both"' >> /etc/asound.conf
        echo '  }' >> /etc/asound.conf
        echo '}' >> /etc/asound.conf
        echo '' >> /etc/asound.conf
        echo 'pcm.both {' >> /etc/asound.conf
        echo ' type route' >> /etc/asound.conf
        echo '  slave {' >> /etc/asound.conf
        echo '   pcm multi' >> /etc/asound.conf
        echo '   channels 6' >> /etc/asound.conf
        echo '  }' >> /etc/asound.conf
        echo ' ttable.0.0 1.0' >> /etc/asound.conf
        echo ' ttable.1.1 1.0' >> /etc/asound.conf
        echo ' ttable.0.2 1.0' >> /etc/asound.conf
        echo ' ttable.1.3 1.0' >> /etc/asound.conf
        echo ' ttable.0.4 1.0' >> /etc/asound.conf
        echo ' ttable.1.5 1.0' >> /etc/asound.conf
        echo '}' >> /etc/asound.conf
        echo '' >> /etc/asound.conf
        echo 'pcm.multi {' >> /etc/asound.conf
        echo ' type multi' >> /etc/asound.conf
        echo '  slaves.a {' >> /etc/asound.conf
        echo '   pcm "tv"' >> /etc/asound.conf
        echo '   channels 2' >> /etc/asound.conf
        echo '  }' >> /etc/asound.conf
        echo '  slaves.b {' >> /etc/asound.conf
        echo '  pcm "receiver"' >> /etc/asound.conf
        echo '  channels 2' >> /etc/asound.conf
        echo '  }' >> /etc/asound.conf
        echo ' bindings.0.slave a' >> /etc/asound.conf
        echo ' bindings.0.channel 0' >> /etc/asound.conf
        echo ' bindings.1.slave a' >> /etc/asound.conf
        echo ' bindings.1.channel 1' >> /etc/asound.conf
        echo ' bindings.2.slave b' >> /etc/asound.conf
        echo ' bindings.2.channel 0' >> /etc/asound.conf
        echo ' bindings.3.slave b' >> /etc/asound.conf
        echo ' bindings.3.channel 1' >> /etc/asound.conf
        echo '}' >> /etc/asound.conf
        echo '' >> /etc/asound.conf
        echo 'pcm.tv {' >> /etc/asound.conf
        echo ' type hw' >> /etc/asound.conf
        echo ' card 0' >> /etc/asound.conf
        echo ' device 3' >> /etc/asound.conf
        echo ' channels 2' >> /etc/asound.conf
        echo '}' >> /etc/asound.conf
        echo '' >> /etc/asound.conf
        echo 'pcm.receiver {' >> /etc/asound.conf
        echo ' type hw' >> /etc/asound.conf
        echo ' card 0' >> /etc/asound.conf
        echo ' device 1' >> /etc/asound.conf
        echo ' channels 2' >> /etc/asound.conf
        echo '}' >> /etc/asound.conf
        sed -i "s/<ac3passthrough>.*</<ac3passthrough>true</" /home/xbmc/.xbmc/userdata/guisettings.xml
        sed -i "s/<audiodevice>.*</<audiodevice>alsa:plug:both</" /home/xbmc/.xbmc/userdata/guisettings.xml
        sed -i "s/<passthroughdevice>.*</<passthroughdevice>alsa:iec958</" /home/xbmc/.xbmc/userdata/guisettings.xml
        sed -i "s/<mode>0</<mode>1</" /home/xbmc/.xbmc/userdata/guisettings.xml
        service xbmc-live stop &>> ~/setup/logs/xci-sound.log; sleep 3; service xbmc-live start &>> ~/setup/logs/xci-sound.log
    elif [ "$soundchoice" = "install_usb" ]; then
        dialog --colors --title "\Z1[ CONFIGURING HDMI AUDIO ]\Zn" --infobox "          Please Wait..." 3 40
        cd ~/setup
        rm -f ~/.asoundrc &>> ~/setup/logs/xci-sound.log
        rm -f /etc/asound.conf &>> ~/setup/logs/xci-sound.log
        touch /etc/asound.conf
        echo 'pcm.!default {' > /etc/asound.conf
        echo ' type plug' >> /etc/asound.conf
        echo '  slave {' >> /etc/asound.conf
        echo '   pcm "iec958"' >> /etc/asound.conf
        echo '  }' >> /etc/asound.conf
        echo '}' >> /etc/asound.conf
        sed -i 's/snd-card-0/snd_usb_audio/g' /etc/modprobe.d/alsa-base.conf
        sed -i 's/options snd-usb-audio index=-2/# options snd-usb-audio index=-2/g' /etc/modprobe.d/alsa-base.conf
        sed -i 's/options snd-usb-usx2y index=-2/# options snd-usb-usx2y index=-2/g' /etc/modprobe.d/alsa-base.conf
        echo default-sample-rate = 48000 >> /etc/pulse/daemon.conf
        sed -i "s/<ac3passthrough>.*</<ac3passthrough>true</" /home/xbmc/.xbmc/userdata/guisettings.xml
        sed -i "s/<audiodevice>.*</<audiodevice>alsa:plug:iec958</" /home/xbmc/.xbmc/userdata/guisettings.xml
        sed -i "s/<passthroughdevice>.*</<passthroughdevice>alsa:iec958</" /home/xbmc/.xbmc/userdata/guisettings.xml
        sed -i "s/<mode>0</<mode>1</" /home/xbmc/.xbmc/userdata/guisettings.xml
        service xbmc-live stop &>> ~/setup/logs/xci-sound.log; sleep 3; service xbmc-live start &>> ~/setup/logs/xci-sound.log
    elif [ "$soundchoice" = "reset" ]; then
        echo "10" | dialog --colors --title "\Z1[ AUDIO RESET ]\Zn" --gauge '  RESETTING AUDIO! Please wait...' 6 70
        rm -f ~/.asoundrc &>> ~/setup/logs/xci-sound.log
        service xbmc-live stop &>> ~/setup/logs/xci-sound.log
        echo "15" | dialog --colors --title "\Z1[ AUDIO RESET ]\Zn" --gauge '  RESETTING AUDIO! Please wait...' 6 70
        rm -f /etc/asound.conf &>> ~/setup/logs/xci-sound.log
        echo "20" | dialog --colors --title "\Z1[ AUDIO RESET ]\Zn" --gauge '  RESETTING AUDIO! Please wait...' 6 70
        cp /etc/asound.conf-backup /etc/asound.conf &>> ~/setup/logs/xci-sound.log
        cp /usr/share/alsa/cards/HDA-Intel.conf-backup /usr/share/alsa/cards/HDA-Intel.conf &>> ~/setup/logs/xci-sound.log
        echo "40" | dialog --colors --title "\Z1[ AUDIO RESET ]\Zn" --gauge '  RESETTING AUDIO! Please wait...' 6 70
        sed -i "s/<ac3passthrough>.*</<ac3passthrough>false</" /home/xbmc/.xbmc/userdata/guisettings.xml &>> ~/setup/logs/xci-sound.log
        sed -i "s/<audiodevice>.*</<audiodevice>alsa:plug:default</" /home/xbmc/.xbmc/userdata/guisettings.xml &>> ~/setup/logs/xci-sound.log
        sed -i "s/<passthroughdevice>.*</<passthroughdevice>alsa:iec958</" /home/xbmc/.xbmc/userdata/guisettings.xml &>> ~/setup/logs/xci-sound.log
        sed -i "s/<mode>0</<mode>1</" /home/xbmc/.xbmc/userdata/guisettings.xml &>> ~/setup/logs/xci-sound.log
        service xbmc-live start &>> ~/setup/logs/xci-sound.log
        echo "100" | dialog --sleep 1 --colors --title "\Z1[ FINISHED RESETTING AUDIO ]\Zn" --gauge '  System will now restart' 6 70
        reboot  
        exit
    fi
    done
}

function Remotes_Menu(){
    while true
    do
    remotechoice=""
    dialog  --clear --cancel-label "Go Back" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ REMOTE CONTROLLER SETUP ]\Zn" \
            --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 16 50 5 \
            1 "ASRock 330HT/BD Remote" \
            2 "Windows Media Center Remote" \
        3 "Sony BT Remote" \
        4 "XBOX Remote"  2>/tmp/xci/remotesmenu
     
    case $? in
      0)
        remotesmenuitem=$(</tmp/xci/remotesmenu)
        case $remotesmenuitem in
            1) remotechoice=asrockremote;;
            2) remotechoice=MSMCremote;;
            3) remotechoice=sonyremote;;
            4) remotechoice=xboxremote;;

        esac;;
      1)
            Hardware_Menu; break;;
      255)
            Hardware_Menu; break;;
    esac

# Fix remote compatibility with kernels greater than 2.6.31-20
    if [ "$remotechoice" = "asrockremote" -a "$(dmidecode -t 2 | grep -i "Product Name:" | awk '{print $3}')" != "FMCP7A-ION" ]; then
        if [ "$CUR_OS" = "karmic" ]; then
            cd ~/setup
            if [ "$(uname -r)" != "2.6.31-20-generic" ]; then
                dialog --colors --title "\Z1[ INFORMATION ]\Zn" --msgbox "\nYour system seems to be running Kernel\Z1 "$(uname -r)"\Zn, compatibility with Asrock 330 HT remote & receiver with newer kernels is now going to take place.\n\nPress \Z1OK\Zn to continue... " 11 54
                echo "0" | dialog --colors --title "\Z1[ REPAIRING DRIVER COMPATIBILITY ]\Zn" --gauge "  Please Wait..." 6 70
                service xbmc-live stop &>> ~/setup/logs/xci-remote.log
                debconf-set-selections lirc_none.seed &>> ~/setup/logs/xci-remote.log
                aptitude purge ~nlirc -y &>> ~/setup/logs/xci-remote.log
                debconf-set-selections lirc_none.seed &>> ~/setup/logs/xci-remote.log
                echo "5" | dialog --colors --title "\Z1[ REPAIRING DRIVER COMPATIBILITY ]\Zn" --gauge "  Please Wait..." 6 70
                aptitude install lirc-modules-source -y -q &>> ~/setup/logs/xci-remote.log
                cd $HOME/setup/ &>> ~/setup/logs/xci-remote.log
                aptitude install linux-source -y -q &>> ~/setup/logs/xci-remote.log
                echo "10" | dialog --colors --title "\Z1[ REPAIRING DRIVER COMPATIBILITY ]\Zn" --gauge "  Please Wait..." 6 70
                wget http://dl.dropbox.com/u/4325533/XCI/Remote/lirc_none.seed &>> ~/setup/logs/xci-remote.log
                wget http://dl.dropbox.com/u/4325533/XCI/Remote/lirc_asrock.seed &>> ~/setup/logs/xci-remote.log
                echo "15" | dialog --colors --title "\Z1[ REPAIRING DRIVER COMPATIBILITY ]\Zn" --gauge "  Please Wait..." 6 70
                echo "20" | dialog --colors --title "\Z1[ REPAIRING DRIVER COMPATIBILITY ]\Zn" --gauge "  Please Wait..." 6 70
                wget http://dl.dropbox.com/u/4325533/XCI/lirc-nct677x-src-1.0.4-ubuntu9.10.deb &>> ~/setup/logs/xci-remote.log
                echo "40" | dialog --colors --title "\Z1[ REPAIRING DRIVER COMPATIBILITY ]\Zn" --gauge "  Please Wait..." 6 70
                dpkg -i lirc-nct677x-src-1.0.4-ubuntu9.10.deb &>> ~/setup/logs/xci-remote.log
                echo "60" | dialog --colors --title "\Z1[ REPAIRING DRIVER COMPATIBILITY]\Zn" --gauge "  Please Wait..." 6 70
                dkms add -m lirc-nct677x-src -v 1.0.4-ubuntu9.10 &>> ~/setup/logs/xci-remote.log
                echo "70" | dialog --colors --title "\Z1[ REPAIRING DRIVER COMPATIBILITY]\Zn" --gauge "  Please Wait..." 6 70
                dkms build -m lirc-nct677x-src -v 1.0.4-ubuntu9.10 &>> ~/setup/logs/xci-remote.log
                echo "80" | dialog --colors --title "\Z1[ REPAIRING DRIVER COMPATIBILITY]\Zn" --gauge "  Please Wait..." 6 70
                dkms install -m lirc-nct677x-src -v 1.0.4-ubuntu9.10 &>> ~/setup/logs/xci-remote.log
                echo "90" | dialog --colors --title "\Z1[ REPAIRING DRIVER COMPATIBILITY]\Zn" --gauge "  Please Wait..." 6 70
                rm -f lirc-nct677x-src-1.0.4-ubuntu9.10.deb
                echo "92" | dialog --colors --title "\Z1[ REPAIRING DRIVER COMPATIBILITY]\Zn" --gauge "  Please Wait..." 6 70
                wget http://dl.dropbox.com/u/4325533/XCI/Remote/IR_9.10_V1.0.4.zip &>> ~/setup/logs/xci-remote.log
                echo "55" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
                unzip -o "IR_9.10_V1.0.4.zip" &>> ~/setup/logs/xci-remote.log
                echo "60" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
                echo "95" | dialog --colors --title "\Z1[ REPAIRING DRIVER COMPATIBILITY]\Zn" --gauge "  Please Wait..." 6 70
                aptitude install lirc -y -q2 &>> ~/setup/logs/xci-remote.log
                echo "98" | dialog --colors --title "\Z1[ REPAIRING DRIVER COMPATIBILITY]\Zn" --gauge "  Please Wait..." 6 70
                echo "99" | dialog --colors --title "\Z1[ REPAIRING DRIVER COMPATIBILITY]\Zn" --gauge "  Please Wait..." 6 70
                debconf-set-selections lirc_asrock.seed &>> ~/setup/logs/xci-remote.log
                if [ "$OSBIT" = "i686" ]; then
                DEBIAN_FRONTEND=noninteractive dpkg -i lirc-nct677x-1.0.4-ubuntu9.10.deb &>> ~/setup/logs/xci-remote.log
                elif [ "$OSBIT" = "x86_64" ]; then
                DEBIAN_FRONTEND=noninteractive dpkg -i lirc-nct677x-x64-1.0.4-ubuntu9.10.deb &>> ~/setup/logs/xci-remote.log
                fi 
                echo "100" | dialog --sleep 3 --colors --title "\Z1[ REPAIRING DRIVER COMPATIBILITY ]\Zn" --gauge "  Finished..." 6 70
                dialog --colors --title "\Z1[ INFORMATION ]\Zn" --msgbox "\nCompatibility has been restored, your HTPC will now reboot, once it has fully restarted, if remote doesnt work, please reinstall the remote drivers again." 10 50
                chmod 744 /usr/share/lirc/remotes/lirc_wb677
                rm -f ~/setup/lirc_none.seed* &>> ~/setup/logs/xci-remote.log
                rm -f ~/setup/lirc_asrock.seed* &>> ~/setup/logs/xci-remote.log
                rm -f ~/setup/IR_9.10_V1.0.4.zip* &>> ~/setup/logs/xci-remote.log
                rm -f ~/setup/lirc-nct677x* &>> ~/setup/logs/xci-remote.log
                rm -f ~/setup/readme.pdf &>> ~/setup/logs/xci-remote.log
                reboot &>> ~/setup/logs/xci-remote.log
                exit 1 &>> ~/setup/logs/xci-remote.log
            fi
# Asrock HT system remote configuration
            echo "0" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
            service xbmc-live stop &>> ~/setup/logs/xci-remote.log
            echo "5" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
            wget http://dl.dropbox.com/u/4325533/XCI/Remote/lirc_none.seed &>> ~/setup/logs/xci-remote.log
            wget http://dl.dropbox.com/u/4325533/XCI/Remote/lirc_asrock.seed &>> ~/setup/logs/xci-remote.log
            echo "7" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
            debconf-set-selections lirc_none.seed &>> ~/setup/logs/xci-remote.log
            aptitude purge ~nlirc -y -q &>> ~/setup/logs/xci-remote.log
            echo "15" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
            debconf-set-selections lirc_none.seed &>> ~/setup/logs/xci-remote.log
            echo "20" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
            aptitude install lirc -y -q2 &>> ~/setup/logs/xci-remote.log
            echo "50" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
            wget http://dl.dropbox.com/u/4325533/XCI/Remote/IR_9.10_V1.0.4.zip &>> ~/setup/logs/xci-remote.log
            echo "55" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
            unzip -o "IR_9.10_V1.0.4.zip" &>> ~/setup/logs/xci-remote.log
            echo "60" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
            debconf-set-selections lirc_asrock.seed &>> ~/setup/logs/xci-remote.log
            echo "65" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
            if [ "$OSBIT" = "i686" ]; then
            DEBIAN_FRONTEND=noninteractive dpkg -i lirc-nct677x-1.0.4-ubuntu9.10.deb &>> ~/setup/logs/xci-remote.log
            elif [ "$OSBIT" = "x86_64" ]; then
            DEBIAN_FRONTEND=noninteractive dpkg -i lirc-nct677x-x64-1.0.4-ubuntu9.10.deb &>> ~/setup/logs/xci-remote.log
            fi 
            echo "95" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
            chmod 744 /usr/share/lirc/remotes/lirc_wb677
            rm -f ~/setup/lirc_none.seed* &>> ~/setup/logs/xci-remote.log
            rm -f ~/setup/lirc_asrock.seed* &>> ~/setup/logs/xci-remote.log
            rm -f ~/setup/IR_9.10_V1.0.4.zip* &>> ~/setup/logs/xci-remote.log
            rm -f ~/setup/lirc-nct677x* &>> ~/setup/logs/xci-remote.log
            rm -f ~/setup/readme.pdf &>> ~/setup/logs/xci-remote.log
        elif [ "$CUR_OS" = "jaunty" ]; then
            dialog --colors --title "\Z1[ INFORMATION ]\Zn" --msgbox "  \n     No Drivers Available for Jaunty..." 7 50
        fi
        dialog --colors --title "\Z4[ CUSTOM KEYMAP SETUP ]"  --yesno "\n Would you like to install custom remote keymaps?" 7 55
        case $? in
            0)
                dialog --colors --title "\Z1[ INSTALLING CUSTOM REMOTE KEYMAPS ]\Zn" --infobox "              Please Wait..." 3 45
                rm -f /home/xbmc/.xbmc/userdata/Lircmap.xml; rm -f /home/xbmc/.xbmc/userdata/keymaps/remote.xml
                cd /home/xbmc/.xbmc/userdata ; wget http://dl.dropbox.com/u/4325533/XCI/Remote/Lircmap.xml &>> ~/setup/logs/xci-remote.log
                cd /home/xbmc/.xbmc/userdata/keymaps ; wget http://dl.dropbox.com/u/4325533/XCI/Remote/remote.xml &>> ~/setup/logs/xci-remote.log
                chown -R xbmc:xbmc /home/xbmc &>> ~/setup/logs/xci-installer.log ;;
            1)
                ;;
            255)
                ;;
        esac
# MCE system remote configuration
    elif [ "$remotechoice" = "MSMCremote" ]; then
        dialog --colors --title "\Z1[ IMPORTANT INFORMATION ]\Zn" --msgbox "\nIf your using the \Z1ASUS AT3N7A-I\Zn motherboard, Please plug your \Z1USB IR Dongle\Zn in \Z4TOP USB port\Zn on the back of your Motherboard, or the Remote will not be able to wake up your system! " 11 50
        echo "0" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
        cd ~/setup
        service xbmc-live stop &>> ~/setup/logs/xci-remote.log
        echo "5" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
        wget http://dl.dropbox.com/u/4325533/XCI/Remote/lirc_none.seed &>> ~/setup/logs/xci-remote.log
        wget http://dl.dropbox.com/u/4325533/XCI/Remote/lirc_mce.seed &>> ~/setup/logs/xci-remote.log
        echo "7" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
        debconf-set-selections lirc_none.seed
        aptitude purge ~nlirc -y -q &>> ~/setup/logs/xci-remote.log
        echo "15" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
        debconf-set-selections lirc_mce.seed
        echo "30" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
        aptitude install lirc -y -q &>> ~/setup/logs/xci-remote.log
        echo "95" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
        # cp ~/setup/10-lirc.sh /etc/pm/sleep.d/10-lirc.sh
        # cp ~/setup/01lirc_module /etc/pm/config.d/01lirc_module
        # chmod 755 /etc/pm/sleep.d/10-lirc.sh
        # chmod 755 /etc/pm/config.d/01lirc_module
        # cp custom-actions.pkla /var/lib/polkit-1/localauthority/50-local.d/custom-actions.pkla
# Enable remote wakeup
        # sed -i 's/xbmc=autostart,nodiskmount,setvolume loglevel=0/xbmc=autostart,nodiskmount,setvolume loglevel=0,usbcore.autosuspend=-1/g' /boot/grub/menu.lst
        echo USB0> /proc/acpi/wakeup
        # echo USB2> /proc/acpi/wakeup
        sed -i '14i\echo USB0> /proc/acpi/wakeup' /etc/rc.local
        # sed -i '15i\echo USB2> /proc/acpi/wakeup' /etc/rc.local
        sed -i '16i\echo "rc.local has completed sucessfully." >> /tmp/resume.log' /etc/rc.local
        rm -f ~/setup/lirc_mce.seed* &>> ~/setup/logs/xci-remote.log
        rm -f ~/setup/lirc_none.seed* &>> ~/setup/logs/xci-remote.log
# PS3 system remote configuration
    elif [ "$remotechoice" = "sonyremote" ]; then
        cd ~/setup
        echo "0" | dialog --colors --title "\Z1[ INSTALLING PS3 REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
        add-apt-repository ppa:kitlaan/ppa &>> ~/setup/logs/xci-remote.log
        echo "20" | dialog --colors --title "\Z1[ INSTALLING PS3 REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
        aptitude install bluez -y &>> ~/setup/logs/xci-remote.log
        echo "25" | dialog --colors --title "\Z1[ INSTALLING PS3 REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
        aptitude install python-dbus -y &>> ~/setup/logs/xci-remote.log
        echo "30" | dialog --colors --title "\Z1[ INSTALLING PS3 REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
        aptitude install python-gobject -y &>> ~/setup/logs/xci-remote.log
        modprobe uinput
        echo uinput >> /etc/modules
        echo "75" | dialog --colors --title "\Z1[ INSTALLING PS3 REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
             wget http://dl.dropbox.com/u/4325533/XCI/Remote/ps3_pair.tar.gz &>> ~/setup/logs/xci-remote.log
          tar -xzvf ps3_pair.tar.gz &>> ~/setup/logs/xci-remote.log
        echo "80" | dialog --sleep 1 --colors --title "\Z1[ INSTALLING PS3 REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
        dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "\n \Z1Hold\Zn the \Z1ENTER\Zn and \Z4START\Zn key on remote while scan is in progress." 6 50          
        wget http://dl.dropbox.com/u/4325533/XCI/Remote/ps3-input &>> ~/setup/logs/xci-remote.log
        python ps3_pair.py <ps3-input &>> ~/setup/logs/xci-remote.log
        if [ "$(python ps3_pair.py --list | grep "mote" | awk {'print $1'})" = "" ]; then
            while [ "$(python ps3_pair.py --list | grep 'mote' | awk {'print $1'})" = "" ]; do
                dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "\nNo Sony BD Remote Found, trying again \Z1Hold\Zn the \Z1ENTER\Zn and \Z4START\Zn key on remote while scan is in progress." 6 50          
                python ps3_pair.py <ps3-input &>> ~/setup/logs/xci-remote.log
            done
        fi
        wget http://dl.dropbox.com/u/4325533/XCI/Remote/ps3remote.config &>> ~/setup/logs/xci-remote.log
        echo "[$(python ps3_pair.py --list | grep "mote" | awk {'print $1'})]" >> /etc/bluetooth/input.conf
        cat ps3remote.config >> /etc/bluetooth/input.conf 
        rm -f ~/setup/ps3-input* &>> ~/setup/logs/xci-remote.log
        rm -f ~/setup/ps3_pair.tar.gz* &>> ~/setup/logs/xci-remote.log
        rm -f ~/setup/ps3remote.config* &>> ~/setup/logs/xci-remote.log
        dialog --sleep 2 --colors --title "\Z1[ PS3 REMOTE INSTALLED ]\Zn" --infobox "\nSony BD Remote Found!" 5 30
# xbox system remote configuration
    elif [ "$remotechoice" = "xboxremote" ]; then
        cd ~/setup
        echo "0" | dialog --colors --title "\Z1[ INSTALLING XBOX REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
        service xbmc-live stop &>> ~/setup/logs/xci-remote.log
        echo "20" | dialog --colors --title "\Z1[ INSTALLING XBOX REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
        wget http://dl.dropbox.com/u/4325533/XCI/Remote/lirc_none.seed &>> ~/setup/logs/xci-remote.log
        echo "40" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
        debconf-set-selections lirc_none.seed &>> ~/setup/logs/xci-remote.log
        aptitude purge ~nlirc -y -q &>> ~/setup/logs/xci-remote.log
        echo "60" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
        debconf-set-selections lirc_none.seed &>> ~/setup/logs/xci-remote.log
        aptitude install lirc -y -q2 &>> ~/setup/logs/xci-remote.log
        rm -f ~/setup/lirc_none.seed &>> ~/setup/logs/xci-remote.log
        echo "80" | dialog --colors --title "\Z1[ INSTALLING SYSTEM REMOTE ]\Zn" --gauge "  Please Wait..." 6 70
        echo "# LIRCD configuration file for Xbox DVD Kit" >> /etc/lirc/lircd.conf
        echo "# brand: Microsoft" >> /etc/lirc/lircd.conf
        echo "# model: Xbox DVD Remote" >> /etc/lirc/lircd.conf
        echo "# supported devices: Xbox DVD Remote via xpad-ir driver" >> /etc/lirc/lircd.conf
        echo  >> /etc/lirc/lircd.conf
        echo "begin remote" >> /etc/lirc/lircd.conf
        echo  >> /etc/lirc/lircd.conf
        echo "name XboxDVDDongle" >> /etc/lirc/lircd.conf
        echo "bits 8" >> /etc/lirc/lircd.conf
        echo  >> /etc/lirc/lircd.conf
        echo "begin codes" >> /etc/lirc/lircd.conf
        echo  >> /etc/lirc/lircd.conf
        echo "SELECT 0x0b" >> /etc/lirc/lircd.conf
        echo "UP 0xa6" >> /etc/lirc/lircd.conf
        echo "DOWN 0xa7" >> /etc/lirc/lircd.conf
        echo "RIGHT 0xa8" >> /etc/lirc/lircd.conf
        echo "LEFT 0xa9" >> /etc/lirc/lircd.conf
        echo "INFO 0xc3" >> /etc/lirc/lircd.conf
        echo  >> /etc/lirc/lircd.conf
        echo "9 0xc6" >> /etc/lirc/lircd.conf
        echo "8 0xc7" >> /etc/lirc/lircd.conf
        echo "7 0xc8" >> /etc/lirc/lircd.conf
        echo "6 0xc9" >> /etc/lirc/lircd.conf
        echo "5 0xca" >> /etc/lirc/lircd.conf
        echo "4 0xcb" >> /etc/lirc/lircd.conf
        echo "3 0xcc" >> /etc/lirc/lircd.conf
        echo "2 0xcd" >> /etc/lirc/lircd.conf
        echo "1 0xce" >> /etc/lirc/lircd.conf
        echo "0 0xcf" >> /etc/lirc/lircd.conf
        echo  >> /etc/lirc/lircd.conf
        echo "DISPLAY 0xd5" >> /etc/lirc/lircd.conf
        echo "BACK 0xd8" >> /etc/lirc/lircd.conf
        echo "SKIP- 0xdd" >> /etc/lirc/lircd.conf
        echo "SKIP+ 0xdf" >> /etc/lirc/lircd.conf
        echo "STOP 0xe0" >> /etc/lirc/lircd.conf
        echo "REVERSE 0xe2" >> /etc/lirc/lircd.conf
        echo "FORWARD 0xe3" >> /etc/lirc/lircd.conf
        echo "TITLE 0xe5" >> /etc/lirc/lircd.conf
        echo "PAUSE 0xe6" >> /etc/lirc/lircd.conf
        echo "PLAY 0xea" >> /etc/lirc/lircd.conf
        echo "MENU 0xf7" >> /etc/lirc/lircd.conf
        echo  >> /etc/lirc/lircd.conf
        echo "end codes" >> /etc/lirc/lircd.conf
        echo  >> /etc/lirc/lircd.conf
        echo "end remote" >> /etc/lirc/lircd.conf
    fi
        echo "100" | dialog --sleep 3 --colors --title "\Z1[ INSTALLATION FINISHED ]\Zn" --gauge "  XBMC will now restart..." 6 70
        service xbmc-live start &>> ~/setup/logs/xci-remote.log
    done
}

# Temperature sensors menu
# Install sensors applications
function Temp_Sensors_Menu(){
    while true
    do
    tempsensorchoice=""
    dialog  --clear  --cancel-label "Go Back" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ CHOOSE CPU DRIVER TO INSTALL ]\Zn" \
            --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\nPlease choose an item:" 15 46 10 \
            1 "Coretemp Driver (SAFE)" \
            2 "W83627EHF Driver (EXPERIMENTAL)" 2>/tmp/xci/tempsensormenu

    case $? in
      0)
        tempsensormenuitem=$(</tmp/xci/tempsensormenu)
        case $tempsensormenuitem in
            1) tempsensorchoice=coretemp;;
            2) tempsensorchoice=W83627EHF;;
        esac;;
      1)
            Hardware_Menu; break;;
      255)
            Hardware_Menu; break;;
    esac


    if [ "$tempsensorchoice" = "coretemp" ]; then
        echo "0" | dialog --colors --title "\Z1[ INSTALLING CPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        aptitude install lm-sensors -y &>> ~/setup/logs/xci-temp.log
        echo "5" | dialog --colors --title "\Z1[ INSTALLING CPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        aptitude install linux-source -y &>> ~/setup/logs/xci-temp.log
        echo "10" | dialog --colors --title "\Z1[ INSTALLING CPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        aptitude install build-essential -y &>> ~/setup/logs/xci-temp.log
        cd /usr/src
        echo "15" | dialog --colors --title "\Z1[ INSTALLING CPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        wget http://dl.dropbox.com/u/4325533/XCI/Temp-sensors/coretemp.patch &>> ~/setup/logs/xci-temp.log
        echo "20" | dialog --colors --title "\Z1[ INSTALLING CPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        pv -e linux-source-$(uname -r | awk -F'-' '{print $1}').tar.bz2 | tar xjf - 2>>~/setup/logs/xci-temp.log
        echo "40" | dialog --colors --title "\Z1[ INSTALLING CPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        cd linux-source-$(uname -r | awk -F'-' '{print $1}') 
        patch -p1 < ../coretemp.patch &>> ~/setup/logs/xci-temp.log
        echo "45" | dialog --colors --title "\Z1[ INSTALLING CPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        make -j4 -C /lib/modules/$(uname -r)/build M=/usr/src/linux-source-$(uname -r | awk -F'-' '{print $1}')/drivers/hwmon/ modules &>> ~/setup/logs/xci-temp.log
        echo "50" | dialog --colors --title "\Z1[ INSTALLING CPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        cp /usr/src/linux-source-$(uname -r | awk -F'-' '{print $1}')/drivers/hwmon/coretemp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon/coretemp.ko &>> ~/setup/logs/xci-temp.log
        cd /usr/sbin/
        rm -f /usr/sbin/sensors-detect
        wget http://dl.dropbox.com/u/4325533/XCI/Temp-sensors/sensors-detect &>> ~/setup/logs/xci-temp.log
        wget http://dl.dropbox.com/u/4325533/XCI/Temp-Sensors/sensors-input &>> ~/setup/logs/xci-temp.log
        chmod 755 /usr/sbin/sensors-detect
        echo "60" | dialog --colors --title "\Z1[ INSTALLING CPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        sensors-detect <sensors-input &>> ~/setup/logs/xci-temp.log
        rm -f /usr/sbin/sensors-input
        echo "70" | dialog --colors --title "\Z1[ INSTALLING CPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        chmod 666 /etc/modules
        echo coretemp >> /etc/modules
        modprobe coretemp
        chmod 644 /etc/modules
        service lm-sensors start &>> ~/setup/logs/xci-temp.log
        sensors -s &>> ~/setup/logs/xci-temp.log
# Install GPU sensor nvclock    
        echo "75" | dialog --colors --title "\Z1[ INSTALLING GPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        aptitude install cvs automake  -y &>> ~/setup/logs/xci-temp.log
        echo "80" | dialog --colors --title "\Z1[ INSTALLING GPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        cd /usr/local/src
        cvs -z3 -d:pserver:anonymous@nvclock.cvs.sourceforge.net:/cvsroot/nvclock co -P nvclock &>> ~/setup/logs/xci-temp.log
        echo "85" | dialog --colors --title "\Z1[ INSTALLING GPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        cd nvclock
        sh autogen.sh; ./configure --disable-nvcontrol &>> ~/setup/logs/xci-temp.log; make &>> ~/setup/logs/xci-temp.log; make install &>> ~/setup/logs/xci-temp.log
        echo "95" | dialog --colors --title "\Z1[ INSTALLING HDD SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        wget http://dl.dropbox.com/u/4325533/XCI/Temp-sensors/hddtemp.input &>> ~/setup/logs/xci-temp.log
        debconf-set-selections hddtemp.input
        aptitude install hddtemp  -y -f -q | pv -e -l -s 24 >11 2>>~/setup/logs/xci-temp.log
        rm -f hddtemp.input &>> ~/setup/logs/xci-temp.log
        chmod u+s /usr/sbin/hddtemp
# Setup advancedsettings.xml CPU & GPU temperature values
        echo "98" | dialog --colors --title "\Z1[ SETTING-UP XBMC INFORMATION MENU ]\Zn" --gauge "  Please wait..." 6 70 0
        echo "andy" >> /home/xbmc/.xbmc/userdata/advancedsettings.xml
        sed -i '/cputempcommand/d' /home/xbmc/.xbmc/userdata/advancedsettings.xml &>> ~/setup/logs/xci-temp.log
        sed -i '/gputempcommand/d' /home/xbmc/.xbmc/userdata/advancedsettings.xml &>> ~/setup/logs/xci-temp.log
        sed -i '/hddtempcommand/d' /home/xbmc/.xbmc/userdata/advancedsettings.xml &>> ~/setup/logs/xci-temp.log
        sed -i '/advancedsettings/d' /home/xbmc/.xbmc/userdata/advancedsettings.xml &>> ~/setup/logs/xci-temp.log
        sed -i '1i\<advancedsettings>' /home/xbmc/.xbmc/userdata/advancedsettings.xml
        wget http://dl.dropbox.com/u/4325533/XCI/Temp-sensors/advancedsettings-coretemp &>> ~/setup/logs/xci-temp.log
        cat advancedsettings-coretemp >> /home/xbmc/.xbmc/userdata/advancedsettings.xml
        rm -f advancedsettings-coretemp &>> ~/setup/logs/xci-temp.log
        sed -i '/andy/d' /home/xbmc/.xbmc/userdata/advancedsettings.xml &>> ~/setup/logs/xci-temp.log
        echo "</advancedsettings>" >> /home/xbmc/.xbmc/userdata/advancedsettings.xml
        chown xbmc:xbmc /home/xbmc/.xbmc/userdata/advancedsettings.xml &>> ~/setup/logs/xci-temp.log
        echo "100" | dialog --sleep 3 --colors --title "\Z1[ TEMPERATURE SENSORS INSTALLED ]\Zn" --gauge "  XBMC will now restart..." 6 70 0
        service xbmc-live stop &>> ~/setup/logs/xci-temp.log; sleep 3; service xbmc-live start &>> ~/setup/logs/xci-temp.log
    elif [ "$tempsensorchoice" = "W83627EHF" -a "$(dmidecode -t 2 | grep -i "Product Name:" | awk '{print $3}')" != "FMCP7A-ION" ]; then
        echo "0" | dialog --colors --title "\Z1[ INSTALLING CPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        aptitude install lm-sensors -y &>> ~/setup/logs/xci-temp.log
        echo "40" | dialog --colors --title "\Z1[ INSTALLING CPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        cd /usr/sbin/
        rm -f /usr/sbin/sensors-detect
        wget http://dl.dropbox.com/u/4325533/XCI/Temp-sensors/sensors-detect &>> ~/setup/logs/xci-temp.log
        wget http://dl.dropbox.com/u/4325533/XCI/Temp-sensors/sensors-input &>> ~/setup/logs/xci-temp.log
        echo "60" | dialog --colors --title "\Z1[ INSTALLING CPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        chmod 755 /usr/sbin/sensors-detect
        wget http://dl.dropbox.com/u/4325533/XCI/Temp-sensors/sensors3.conf &>> ~/setup/logs/xci-temp.log
        echo "60" | dialog --colors --title "\Z1[ INSTALLING CPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        mv -f sensors3.conf /etc/sensors3.conf
        dialog --colors --title "\Z1[ INSTALLING CPU SENSORS! ]\Zn" --msgbox "\nPlease answer YES (Y/y) to \Z4ALL\Zn the following questions and press \Z1ENTER\Zn at the end followed by YES (Y/y)" 9 50
        sensors-detect <sensors-input &>> ~/setup/logs/xci-temp.log
        echo "70" | dialog --colors --title "\Z1[ INSTALLING CPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        chmod 666 /etc/modules
        if [ "$CUR_OS" = "karmic" ]; then
            echo "w83627ehf force_id=0xa510" >> /etc/modules
            modprobe w83627ehf force_id=0xa510
        elif [ "$CUR_OS" = "jaunty" ]; then
            echo "w83627ehf force_id=0x8850" >> /etc/modules
            modprobe w83627ehf force_id=0x8850
        fi
        chmod 644 /etc/modules
        service lm-sensors start &>> ~/setup/logs/xci-temp.log
        sensors -s &>> ~/setup/logs/xci-temp.log
# Install GPU sensor nvclock
        echo "75" | dialog --colors --title "\Z1[ INSTALLING GPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        aptitude install cvs automake  -y &>> ~/setup/logs/xci-temp.log
        echo "80" | dialog --colors --title "\Z1[ INSTALLING GPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        cd /usr/local/src
        cvs -z3 -d:pserver:anonymous@nvclock.cvs.sourceforge.net:/cvsroot/nvclock co -P nvclock &>> ~/setup/logs/xci-temp.log
        echo "85" | dialog --colors --title "\Z1[ INSTALLING GPU SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        cd nvclock
        sh autogen.sh; ./configure --disable-nvcontrol &>> ~/setup/logs/xci-temp.log; make &>> ~/setup/logs/xci-temp.log; make install &>> ~/setup/logs/xci-temp.log
        echo "95" | dialog --colors --title "\Z1[ INSTALLING HDD SENSORS ]\Zn" --gauge "  Please wait..." 6 70 0
        wget http://dl.dropbox.com/u/4325533/XCI/Temp-sensors/hddtemp.input &>> ~/setup/logs/xci-temp.log
        debconf-set-selections hddtemp.input
        aptitude install hddtemp  -y -f -q | pv -e -l -s 24 >11 2>>~/setup/logs/xci-temp.log
        rm -f hddtemp.input &>> ~/setup/logs/xci-temp.log
        chmod u+s /usr/sbin/hddtemp
# Setup advancedsettings.xml cpu & gpu values
        echo "98" | dialog --colors --title "\Z1[ SETTING-UP XBMC INFORMATION MENU ]\Zn" --gauge "  Please wait..." 6 70 0
        echo "andy" >> /home/xbmc/.xbmc/userdata/advancedsettings.xml
        sed -i '/cputempcommand/d' /home/xbmc/.xbmc/userdata/advancedsettings.xml &>> ~/setup/logs/xci-temp.log
        sed -i '/gputempcommand/d' /home/xbmc/.xbmc/userdata/advancedsettings.xml &>> ~/setup/logs/xci-temp.log
        sed -i '/hddtempcommand/d' /home/xbmc/.xbmc/userdata/advancedsettings.xml &>> ~/setup/logs/xci-temp.log
        sed -i '/advancedsettings/d' /home/xbmc/.xbmc/userdata/advancedsettings.xml &>> ~/setup/logs/xci-temp.log
        sed -i '1i\<advancedsettings>' /home/xbmc/.xbmc/userdata/advancedsettings.xml
        wget http://dl.dropbox.com/u/4325533/XCI/Temp-sensors/advancedsettings-w83627ehf &>> ~/setup/logs/xci-temp.log
        cat advancedsettings-w83627ehf >> /home/xbmc/.xbmc/userdata/advancedsettings.xml
        rm -f advancedsettings-w83627ehf &>> ~/setup/logs/xci-temp.log
        sed -i '/andy/d' /home/xbmc/.xbmc/userdata/advancedsettings.xml &>> ~/setup/logs/xci-temp.log
        echo "</advancedsettings>" >> /home/xbmc/.xbmc/userdata/advancedsettings.xml
        chown xbmc:xbmc /home/xbmc/.xbmc/userdata/advancedsettings.xml &>> ~/setup/logs/xci-temp.log
        echo "100" | dialog --sleep 3 --colors --title "\Z1[ TEMP SENSORS INSTALLED ]\Zn" --gauge "  XBMC will now restart..." 6 70 0
        service xbmc-live stop &>> ~/setup/logs/xci-temp.log; sleep 3; service xbmc-live start &>> ~/setup/logs/xci-temp.log
    elif [ "$tempsensorchoice" = "W83627EHF" -a "$(dmidecode -t2 | grep -i "Product Name:" | awk '{print $3}')" = "FMCP7A-ION" -o "$tempsensorchoice" = "W83627EHF" -a "$(dmidecode -t2 | grep -i "Product Name:" | awk '{print $3}')" = "FMCP7A-ION" ]; then
        dialog --colors --title "\Z1[ INFORMATION ]\Zn" --msgbox '\nYour hardware is not compatible with this option at this time!' 8 40
    fi
    done
}


function WIFI_Setup(){
    while true
    do
# display wifi setup menu add drivers and prompt users for AP & access key
    networkchoice=""
    dialog  --clear --cancel-label "Go Back" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ NETWORK SETUP ]\Zn" \
            --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 15 45 3 \
            1 "Enable Wifi" \
            2 "Disable Wifi" 2>/tmp/xci/networkmenu
     
    case $? in
      0)
        networkmenuitem=$(</tmp/xci/networkmenu)
        case $networkmenuitem in
            1) networkchoice=wifi;;
            2) networkchoice=lan;;
        esac;;
      1)
            Hardware_Menu; break;;
      255)
            Hardware_Menu; break;;
    esac

    if [ "$networkchoice" = "wifi" ]; then
        echo "0" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  INSTALLING REQUIRED TOOLS! Please wait..." 6 70 0 
        echo "5" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  INSTALLING REQUIRED TOOLS! Please wait..." 6 70 0
        if [ "$(dpkg -s "wireless-tools" | grep -i "Status:" | awk '{print $4}')" != "installed" ]; then
            dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "  INSTALLING REQUIRED TOOLS! Please wait..." 3 50
            aptitude install wireless-tools -y &>> ~/setup/logs/xci-wlan.log
        fi
        if [ "$(dpkg -s "linux-backports-modules-`uname -r`" | grep -i "Status:" | awk '{print $4}')" != "installed" ]; then
            dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "  INSTALLING REQUIRED TOOLS! Please wait..." 3 50
            aptitude install linux-backports-modules-`uname -r` -y -q &>> ~/setup/logs/xci-wlan.log
        fi
        if [ "$(dpkg -s "linux-backports-modules-wireless-karmic" | grep -i "Status:" | awk '{print $4}')" != "installed" ]; then
            dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "  INSTALLING REQUIRED TOOLS! Please wait..." 3 50
            aptitude install linux-backports-modules-wireless-karmic -y -q &>> ~/setup/logs/xci-wlan.log
        fi  
        if [ "$(dpkg -s "wpasupplicant" | grep -i "Status:" | awk '{print $4}')" != "installed" ]; then
            dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "  INSTALLING SECURITY TOOLS! Please wait..."/ 3 50
            aptitude install wpasupplicant -y &>> ~/setup/logs/xci-wlan.log
        fi  
        
        sed -i '/auto eth0/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/iface eth0 inet dhcp/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/# Wireless/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/auto wlan0/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/iface wlan0 inet dhcp/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wireless-essid/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wireless-key/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wpa-ssid/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wpa-ap-scan/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wpa-proto/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wpa-pairwise/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wpa-group/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wpa-key-mgmt/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wpa-psk/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wireless-channel/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wireless-mode/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log

        echo "# Wireless" >>/etc/network/interfaces
        echo "auto wlan0" >>/etc/network/interfaces
        echo "iface wlan0 inet dhcp" >>/etc/network/interfaces
        
        ifconfig wlan0 up &>> ~/setup/logs/xci-wlan.log; sleep 1
        echo "10" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        iwlist wlan0 scan >~/setup/WLAN_List.log

        echo "20" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanssid1=$(cat ~/setup/WLAN_List.log | grep "ESSID:" | awk -F\" 'NR==1 {print $(NF-1)}')
        wlanssid2=$(cat ~/setup/WLAN_List.log | grep "ESSID:" | awk -F\" 'NR==2 {print $(NF-1)}')
        wlanssid3=$(cat ~/setup/WLAN_List.log | grep "ESSID:" | awk -F\" 'NR==3 {print $(NF-1)}')
        wlanssid4=$(cat ~/setup/WLAN_List.log | grep "ESSID:" | awk -F\" 'NR==4 {print $(NF-1)}')
        wlanssid5=$(cat ~/setup/WLAN_List.log | grep "ESSID:" | awk -F\" 'NR==5 {print $(NF-1)}')
        wlanssid6=$(cat ~/setup/WLAN_List.log | grep "ESSID:" | awk -F\" 'NR==6 {print $(NF-1)}')
        wlanssid7=$(cat ~/setup/WLAN_List.log | grep "ESSID:" | awk -F\" 'NR==7 {print $(NF-1)}')
        wlanssid8=$(cat ~/setup/WLAN_List.log | grep "ESSID:" | awk -F\" 'NR==8 {print $(NF-1)}')
        wlanssid9=$(cat ~/setup/WLAN_List.log | grep "ESSID:" | awk -F\" 'NR==9 {print $(NF-1)}')
        
        echo "28" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanchannel1=$(cat ~/setup/WLAN_List.log | grep "Channel:" | awk 'BEGIN { FS = ":" } ; NR==1 {print $2}')
        echo "32" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanchannel2=$(cat ~/setup/WLAN_List.log | grep "Channel:" | awk 'BEGIN { FS = ":" } ; NR==2{print $2}')
        echo "36" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanchannel3=$(cat ~/setup/WLAN_List.log | grep "Channel:" | awk 'BEGIN { FS = ":" } ; NR==3 {print $2}')
        echo "40" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanchannel4=$(cat ~/setup/WLAN_List.log | grep "Channel:" | awk 'BEGIN { FS = ":" } ; NR==4 {print $2}')
        echo "44" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanchannel5=$(cat ~/setup/WLAN_List.log | grep "Channel:" | awk 'BEGIN { FS = ":" } ; NR==5 {print $2}')
        echo "48" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanchannel6=$(cat ~/setup/WLAN_List.log | grep "Channel:" | awk 'BEGIN { FS = ":" } ; NR==6 {print $2}')
        echo "52" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanchannel7=$(cat ~/setup/WLAN_List.log | grep "Channel:" | awk 'BEGIN { FS = ":" } ; NR==7 {print $2}')
        echo "56" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanchannel8=$(cat ~/setup/WLAN_List.log | grep "Channel:" | awk 'BEGIN { FS = ":" } ; NR==8 {print $2}')
        echo "60" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanchannel9=$(cat ~/setup/WLAN_List.log | grep "Channel:" | awk 'BEGIN { FS = ":" } ; NR==9 {print $2}')
        
        echo "64" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanenc1=$(cat ~/setup/WLAN_List.log | grep "Authentication Suites (1)" | awk 'BEGIN { FS = ": " } ; NR==1 {print $2}')
        echo "68" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanenc2=$(cat ~/setup/WLAN_List.log | grep "Authentication Suites (1)" | awk 'BEGIN { FS = ": " } ; NR==2 {print $2}')
        echo "72" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanenc3=$(cat ~/setup/WLAN_List.log | grep "Authentication Suites (1)" | awk 'BEGIN { FS = ": " } ; NR==3 {print $2}')
        echo "76" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanenc4=$(cat ~/setup/WLAN_List.log | grep "Authentication Suites (1)" | awk 'BEGIN { FS = ": " } ; NR==4 {print $2}')
        echo "80" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanenc5=$(cat ~/setup/WLAN_List.log | grep "Authentication Suites (1)" | awk 'BEGIN { FS = ": " } ; NR==5 {print $2}')
        echo "84" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanenc6=$(cat ~/setup/WLAN_List.log | grep "Authentication Suites (1)" | awk 'BEGIN { FS = ": " } ; NR==6 {print $2}')
        echo "88" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanenc7=$(cat ~/setup/WLAN_List.log | grep "Authentication Suites (1)" | awk 'BEGIN { FS = ": " } ; NR==7 {print $2}')
        echo "92" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanenc8=$(cat ~/setup/WLAN_List.log | grep "Authentication Suites (1)" | awk 'BEGIN { FS = ": " } ; NR==8 {print $2}')
        echo "96" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0
        wlanenc9=$(cat ~/setup/WLAN_List.log | grep "Authentication Suites (1)" | awk 'BEGIN { FS = ": " } ; NR==9 {print $2}')
        echo "100" | dialog --colors --title "\Z1[ SETTING UP WIRELESS NETWORK ]\Zn" --gauge "  SCANNING FOR NETWORKS! Please wait..." 6 70 0

        while true
        do
        dialog  --clear  --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
                --colors --title "\Z4[ WIRELESS NETWORK SETUP ]\Zn" \
                --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose your Wireless Network:" 21 50 9 \
                1 "$wlanssid1" \
                2 "$wlanssid2" \
                3 "$wlanssid3" \
                4 "$wlanssid4" \
                5 "$wlanssid5" \
                6 "$wlanssid6" \
                7 "$wlanssid7" \
                8 "$wlanssid8" \
                9 "$wlanssid9" 2>/tmp/xci/wlanssid
         
        ssidmenuitem=$(</tmp/xci/wlanssid)
         
        case $ssidmenuitem in
            1) wlanssid="$wlanssid1"; wlanchannel="$wlanchannel1"; wlanenc="$wlanenc1"; break;;
            2) wlanssid="$wlanssid2"; wlanchannel="$wlanchannel2"; wlanenc="$wlanenc2"; break;;
            3) wlanssid="$wlanssid3"; wlanchannel="$wlanchannel3"; wlanenc="$wlanenc3"; break;;
            4) wlanssid="$wlanssid4"; wlanchannel="$wlanchannel4"; wlanenc="$wlanenc4"; break;;
            5) wlanssid="$wlanssid5"; wlanchannel="$wlanchannel5"; wlanenc="$wlanenc5"; break;;
            6) wlanssid="$wlanssid6"; wlanchannel="$wlanchannel6"; wlanenc="$wlanenc6"; break;;
            7) wlanssid="$wlanssid7"; wlanchannel="$wlanchannel7"; wlanenc="$wlanenc7"; break;;
            8) wlanssid="$wlanssid8"; wlanchannel="$wlanchannel8"; wlanenc="$wlanenc8"; break;;
            9) wlanssid="$wlanssid9"; wlanchannel="$wlanchannel9"; wlanenc="$wlanenc9"; break;;
        esac
        done
            dialog  --clear --backtitle "XBMC XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
                    --colors --title "\Z4[ WIRELESS NETWORK SETUP ]\Zn" \
                    --inputbox " Enter your network KEY" 0 0 2>/tmp/xci/wlankey
            wlankeyitem=$(</tmp/xci/wlankey)
# make decision 
            case $? in
              0)
                ;;
              1)
                ;;
              255)
                ;;
            esac

            if [ "$wlanenc" == "PSK" ]; then 
                echo "wpa-ssid         $wlanssid" >>/etc/network/interfaces
                echo "wpa-ap-scan      1" >>/etc/network/interfaces
                echo "wpa-proto        RSN WPA" >>/etc/network/interfaces
                echo "wpa-pairwise     CCMP TKIP" >>/etc/network/interfaces
                echo "wpa-group        CCMP TKIP" >>/etc/network/interfaces
                echo "wpa-key-mgmt     WPA-PSK" >>/etc/network/interfaces
                echo "wpa-psk          $wlankeyitem" >>/etc/network/interfaces
                echo "wireless-channel $wlanchannel" >>/etc/network/interfaces
                echo "wireless-mode    managed" >>/etc/network/interfaces
                ifconfig wlan0 up &>> ~/setup/logs/xci-wlan.log
            else
                echo "wireless-essid   $wlanssid" >>/etc/network/interfaces
                echo "wireless-key     $wlankeyitem" >>/etc/network/interfaces
                echo "wireless-channel $wlanchannel" >>/etc/network/interfaces
                echo "wireless-mode    managed" >>/etc/network/interfaces
                sed -i 's/auto eth0/#auto eth0/g' /etc/network/interfaces
                sed -i 's/iface eth0 inet dhcp/#iface eth0 inet dhcp/g' /etc/network/interfaces
                ifconfig wlan0 up &>> ~/setup/logs/xci-wlan.log
            fi  
            rm -fr >~/setup/WLAN_List.log
            dialog --sleep 3 --colors --title "\Z1[ WIRELESS NETWORK SETUP ]\Zn" --msgbox "\n    Setup has completed! System will now restart! " 7 60
             reboot  
    elif [ "$networkchoice" = "lan" ]; then
        echo "0" | dialog --colors --title "\Z1[ SETTING UP WIRED NETWORK! ]\Zn" --gauge "  Please wait..." 6 70 0
        sed -i '/auto eth0/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/iface eth0 inet dhcp/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/# Wireless/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/auto wlan0/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/iface wlan0 inet dhcp/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wireless-essid/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wireless-key/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wpa-ssid/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wpa-ap-scan/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wpa-proto/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wpa-pairwise/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wpa-group/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wpa-key-mgmt/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wpa-psk/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wireless-channel/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        sed -i '/wireless-mode/d' /etc/network/interfaces &>> ~/setup/logs/xci-wlan.log
        echo "auto eth0" >>/etc/network/interfaces
        echo "iface eth0 inet dhcp" >>/etc/network/interfaces
        echo "50" | dialog --colors --title "\Z1[ SETTING UP WIRED NETWORK ]\Zn" --gauge "  Please wait..." 6 70 0
        ifconfig eth0 up &>> ~/setup/logs/xci-wlan.log
        echo "100" | dialog --sleep 1 --colors --title "\Z1[ SETTING UP WIRED NETWORK ]\Zn" --gauge "  Please wait..." 6 70 0
        dialog --sleep 3 --colors --title "\Z1[ ETHERNET NETWORK IS SETUP ]\Zn" --msgbox "\n    Setup has completed! System will now restart! " 7 60
         reboot
    fi
    done
}

function Bluetooth_Setup(){
    while true
    do
    bluetoothinstallchoice=""
    dialog  --clear  --cancel-label "Go Back" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ CHOOSE BLUETHOOTH MODULE ]\Zn" \
            --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 16 50 3 \
            1 "AT3N7A-I Onboard Dongle" 2>/tmp/xci/bluetoothmenu
#            2 "add function" \
#            3 "add function" 2>/tmp/xci/bluetoothmenu
     
    case $? in
      0)
        bluetoothinstallmenuitem=$(</tmp/xci/bluetoothmenu)
        case $bluetoothinstallmenuitem in
            1) bluetoothinstallchoice="AT3N7A-I";;
#            2) bluetoothinstallchoice="dongle b";;
#            3) bluetoothinstallchoice="dongle c";;
        esac;;
      1)
            Hardware_Menu; break;;
      255)
            Hardware_Menu; break;;
    esac

    if [ "$bluetoothinstallchoice" = "AT3N7A-I" ]; then
        echo "0" | dialog --colors --title "\Z1[ INSTALLING BLUETOOTH MODULE ]\Zn" --gauge "  INSTALLING REQUIRED TOOLS! Please wait..." 6 70 0
        cd ~/setup
        aptitude install linux-source -y &>> ~/setup/logs/xci-bluetooth.log
        echo "30" | dialog --colors --title "\Z1[ INSTALLING BLUETOOTH MODULE ]\Zn" --gauge "  INSTALLING REQUIRED TOOLS! Please wait..." 6 70 0
        aptitude install build-essential -y &>> ~/setup/logs/xci-bluetooth.log
        echo "40" | dialog --colors --title "\Z1[ INSTALLING BLUETOOTH MODULE ]\Zn" --gauge "  DOWNLOADING REQUIRED FILES! Please wait..." 6 70 0
        wget http://dl.dropbox.com/u/4325533/XCI/Remote/ath3k.tar.bz2 &>> ~/setup/logs/xci-bluetooth.log
        echo "50" | dialog --colors --title "\Z1[ INSTALLING BLUETOOTH MODULE ]\Zn" --gauge "  DOWNLOADING REQUIRED FILES! Please wait..." 6 70 0
        tar -xjvf ath3k.tar.bz2 &>> ~/setup/logs/xci-bluetooth.log
        echo "60" | dialog --colors --title "\Z1[ INSTALLING BLUETOOTH MODULE ]\Zn" --gauge "  DOWNLOADING REQUIRED FILES! Please wait..." 6 70 0
        wget http://dl.dropbox.com/u/4325533/XCI/Remote/ath3k-1.fw &>> ~/setup/logs/xci-bluetooth.log
        echo "70" | dialog --colors --title "\Z1[ INSTALLING BLUETOOTH MODULE ]\Zn" --gauge "  DOWNLOADING REQUIRED FILES! Please wait..." 6 70 0
        mv -f ath3k-1.fw /lib/firmware/ath3k-1.fw &>> ~/setup/logs/xci-bluetooth.log
        echo "80" | dialog --colors --title "\Z1[ INSTALLING BLUETOOTH MODULE ]\Zn" --gauge "  COMPILING SYSTEM MODULE! Please wait..." 6 70 0
        cd ath3k
        make &>> ~/setup/logs/xci-bluetooth.log
        echo "90" | dialog --colors --title "\Z1[ INSTALLING BLUETOOTH MODULE ]\Zn" --gauge "  COMPILING SYSTEM MODULE! Please wait..." 6 70 0
        make install &>> ~/setup/logs/xci-bluetooth.log
        if [ ! -e /lib/modules/`uname -r`/kernel/drivers/bluetooth/ath3k.ko ]; then
        mv ath3k.ko /lib/modules/`uname -r`/kernel/drivers/bluetooth/ath3k.ko &>> ~/setup/logs/xci-bluetooth.log
        fi
        depmod -a &>> ~/setup/logs/xci-bluetooth.log
        chmod 666 /etc/modules
        echo ath3k >> /etc/modules
        chmod 644 /etc/modules
        modprobe ath3k &>> ~/setup/logs/xci-bluetooth.log
        cd ~/setup
        rm -rf ath3k*
        echo "100" | dialog --sleep 1 --colors --title "\Z1[ BLUETOOTH MODULE INSTALLED ]\Zn" --gauge "  System will reboot in now" 6 70 0
         reboot; exit 1
    fi
    done
}

function Backup_Restore_Menu(){
    while true
    do
### display menu ###
    dialog  --clear --cancel-label "Go Back" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ BACKUP/RESTORE MENU ]\Zn" \
            --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 14 45 5 \
            1 "Backup" \
            2 "Restore" 2>/tmp/xci/backuprestoremainmenu
     
    case $? in
      0)
        backuprestoremainmenuitem=$(</tmp/xci/backuprestoremainmenu)
        case $backuprestoremainmenuitem in
            1) Backup_Script;;
            2) Restore_Script;;
        esac;;
      1)
            break;;
      255)
            break;;
    esac
    done
}

function Mount_Script(){
    if [ -e /home/xbmc/.xbmc/userdata/sources.xml ]; then
        mountdef="/home/xbmc/.xbmc/userdata/sources.xml"
    elif [ -e ~/setup/sources.xml ]; then
        cp ~/setup/sources.xml /tmp/xci/sources.xml
        mountdef="/tmp/xci/sources.xml"
    else
        dialog --colors --title "\Z1[ INFORMATION! ]\Zn" --msgbox "\nFile \Z1sources.xml\Zn NOT found! The script Backup & Restore option relies on \Z1userdata/sources.xml\Zn to mount your SMB shares! \n\nIf you have performed a full backup using the script please copy from your backup location the \Z1sources.xml\Zn\nto the \Z1userdata\Zn folder or to \Z1~/setup\Zn folder.\n\nAlternatively you can recreate the \Z1sources.xml\Zn using XBMC.\n\nOnly then the script will be able to Backup or Restore your previous data back up's." 19 60
        break
    fi    
    
    df -h >/tmp/xci/mounts 2>>~/setup/logs/xci-backup.log
    sed -i '/udev/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
    sed -i '/none/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
    sed -i ':a;N;$!ba;s/\n                   / /g' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log

    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z4[ BACKUP/RESTORE MENU ]\Zn" --inputbox " Enter your \Z4Username\Zn" 8 50 2>/tmp/xci/username
    case $? in
      0)
        username="$(</tmp/xci/username)";;
      1)
        break;;
    esac

    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z4[ BACKUP/RESTORE MENU ]\Zn" --passwordbox " Enter your \Z4Password\Zn" 8 50 2>/tmp/xci/password
    case $? in
      0)
        password="$(</tmp/xci/password)";;
      1)
        break;;
    esac

    rm -f /tmp/xci/username &>> ~/setup/logs/xci-backup.log
    rm -f /tmp/xci/password &>> ~/setup/logs/xci-backup.log

    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Scanning for Mounts! Please wait..." 3 50
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==1')" != "" ]; then 
        case $(cat /tmp/xci/mounts | awk '{print $1}') in
            *$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==1')*);;
            *) mkdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==1') &>> ~/setup/logs/xci-backup.log
                mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==1' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==1')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                while [ "$(df -h | grep -i "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==1' | sed 's/smb://g')")" = "" ] ; do 
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --inputbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==1' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Username\Zn" 9 50 2>/tmp/xci/username
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --passwordbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==1' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Password\Zn" 9 50 2>/tmp/xci/password
                    username="$(</tmp/xci/username)"
                    password="$(</tmp/xci/password)"
                    mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==1' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==1')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                done
        esac
    fi
    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Scanning for Mounts! Please wait..." 3 50
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==2')" != "" ]; then 
        case $(cat /tmp/xci/mounts | awk '{print $1}') in
            *$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==2')*);;
            *) mkdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==2') &>> ~/setup/logs/xci-backup.log
                mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==2' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==2')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                while [ "$(df -h | grep -i "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==2' | sed 's/smb://g')")" = "" ] ; do 
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --inputbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==2' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Username\Zn" 9 50 2>/tmp/xci/username
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --passwordbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==2' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Password\Zn" 9 50 2>/tmp/xci/password
                    username="$(</tmp/xci/username)"
                    password="$(</tmp/xci/password)"
                    mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==2' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==2')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                done
        esac
    fi
    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Scanning for Mounts! Please wait..." 3 50
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==3')" != "" ]; then 
        case $(cat /tmp/xci/mounts | awk '{print $1}') in
            *$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==3')*);;
            *) mkdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==3') &>> ~/setup/logs/xci-backup.log
                mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==3' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==3')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                while [ df | grep -i "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | sed 's/smb://g')" = "" ] ; do 
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --inputbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==3' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Username\Zn" 9 50 2>/tmp/xci/username
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --passwordbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==3' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Password\Z1" 9 50 2>/tmp/xci/password
                    username="$(</tmp/xci/username)"
                    password="$(</tmp/xci/password)"
                    mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==3' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==3')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                done
        esac
    fi
    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Scanning for Mounts! Please wait..." 3 50
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==4')" != "" ]; then 
        case $(cat /tmp/xci/mounts | awk '{print $1}') in
            *$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==4')*);;
            *) mkdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==4') &>> ~/setup/logs/xci-backup.log
                mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==4' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==4')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                while [ "$(df -h | grep -i "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==4' | sed 's/smb://g')")" = "" ] ; do 
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --inputbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==4' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Username\Zn" 9 50 2>/tmp/xci/username
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --passwordbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==4' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Password\Zn" 9 50 2>/tmp/xci/password
                    username="$(</tmp/xci/username)"
                    password="$(</tmp/xci/password)"
                    mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==4' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==4')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                done
        esac
    fi
    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Scanning for Mounts! Please wait..." 3 50
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==5')" != "" ]; then 
        case $(cat /tmp/xci/mounts | awk '{print $1}') in
            *$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==5')*);;
            *) mkdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==5') &>> ~/setup/logs/xci-backup.log
                mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==5' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==5')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                while [ "$(df -h | grep -i "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==5' | sed 's/smb://g')")" = "" ] ; do 
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --inputbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==5' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Username\Zn" 9 50 2>/tmp/xci/username
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --passwordbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==5' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Password\Zn" 9 50 2>/tmp/xci/password
                    username="$(</tmp/xci/username)"
                    password="$(</tmp/xci/password)"
                    mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==5' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==5')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                done
        esac
    fi
    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Scanning for Mounts! Please wait..." 3 50
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==6')" != "" ]; then 
        case $(cat /tmp/xci/mounts | awk '{print $1}') in
            *$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==6')*);;
            *) mkdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==6') &>> ~/setup/logs/xci-backup.log
                mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==6' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==6')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                while [ "$(df -h | grep -i "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==6' | sed 's/smb://g')")" = "" ] ; do 
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --inputbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==6' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Username\Zn" 9 50 2>/tmp/xci/username
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --passwordbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==6' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Password\Zn" 9 50 2>/tmp/xci/password
                    username="$(</tmp/xci/username)"
                    password="$(</tmp/xci/password)"
                    mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==6' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==6')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                done
        esac
    fi
    dialog --colors --title "\Z1[ INFORMATION1 ]\Zn" --infobox "     Scanning for Mounts! Please wait..." 3 50
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==7')" != "" ]; then 
        case $(cat /tmp/xci/mounts | awk '{print $1}') in
            *$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==7')*);;
            *) mkdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==7') &>> ~/setup/logs/xci-backup.log
                mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==7' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==7')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                while [ "$(df -h | grep -i "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==7' | sed 's/smb://g')")" = "" ] ; do 
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --inputbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==7' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Username\Zn" 9 50 2>/tmp/xci/username
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --passwordbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==7' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Password\Zn" 9 50 2>/tmp/xci/password
                    username="$(</tmp/xci/username)"
                    password="$(</tmp/xci/password)"
                    mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==7' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==7')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                done
        esac
    fi
    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Scanning for Mounts! Please wait..." 3 50
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==8')" != "" ]; then 
        case $(cat /tmp/xci/mounts | awk '{print $1}') in
            *$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==8')*);;
            *) mkdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==8') &>> ~/setup/logs/xci-backup.log
                mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==8' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==8')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                while [ "$(df -h | grep -i "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==8' | sed 's/smb://g')")" = "" ] ; do 
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --inputbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==8' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Username\Zn" 9 50 2>/tmp/xci/username
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --passwordbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==8' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Password\Zn" 9 50 2>/tmp/xci/password
                    username="$(</tmp/xci/username)"
                    password="$(</tmp/xci/password)"
                    mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==8' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==8')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                done
        esac
    fi
    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Scanning for Mounts! Please wait..." 3 50
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==9')" != "" ]; then 
        case $(cat /tmp/xci/mounts | awk '{print $1}') in
            *$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==9')*);;
            *) mkdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==9') &>> ~/setup/logs/xci-backup.log
                mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==9' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==9')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                while [ "$(df -h | grep -i "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==9' | sed 's/smb://g')")" = "" ] ; do 
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --inputbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==9' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Username\Zn" 9 50 2>/tmp/xci/username
                    dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z1[ USERNAME OR PASSWORD INCORRECT ]\Zn" --passwordbox "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==9' | sed 's/smb://g'),\nPlease Try Again, Enter your \Z4Password\Zn" 9 50 2>/tmp/xci/password
                    username="$(</tmp/xci/username)"
                    password="$(</tmp/xci/password)"
                    mount -t cifs $(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==9' | sed 's/smb://g') /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==9')/ -o username=$username,password="$password" &>> ~/setup/logs/xci-backup.log
                done
        esac
    fi

    df -h >/tmp/xci/mounts 2>>~/setup/logs/xci-backup.log
    sed -i '/udev/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
    sed -i '/none/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
    sed -i '1d' /tmp/xci/mounts
    sed -i ':a;N;$!ba;s/\n                   / /g' /tmp/xci/mounts
    
}

function Unmount_Script(){
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==1')" != "" ]; then 
        while true ; do 
            case $(cat /tmp/xci/mounts | awk '{print $1}') in
                *$(cat $(echo $mountdef) | grep -i "SMB:" | sed 's/smb://g' | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==1')*)
                    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Unmounting your shares, Please wait..." 3 50
                    umount.cifs -l /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==1') &>> ~/setup/logs/xci-backup.log
                    rmdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==1') &>> ~/setup/logs/xci-backup.log
                    df -h >/tmp/xci/mounts 2>>~/setup/logs/xci-backup.log
                    sed -i '/udev/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '/none/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '1d' /tmp/xci/mounts
                    sed -i ':a;N;$!ba;s/\n                   / /g' /tmp/xci/mounts;;
                *) break;;
            esac
        done
    fi    
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==2')" != "" ]; then 
        while true ; do 
            case $(cat /tmp/xci/mounts | awk '{print $1}') in
                *$(cat $(echo $mountdef) | grep -i "SMB:" | sed 's/smb://g' | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==2')*)
                    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Unmounting your shares, Please wait..." 3 50
                    umount.cifs -l /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==2') &>> ~/setup/logs/xci-backup.log
                    sleep 1
                    rmdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==2') &>> ~/setup/logs/xci-backup.log
                    df -h >/tmp/xci/mounts 2>>~/setup/logs/xci-backup.log
                    sed -i '/udev/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '/none/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '1d' /tmp/xci/mounts
                    sed -i ':a;N;$!ba;s/\n                   / /g' /tmp/xci/mounts;;
                *) break;;
            esac
        done
    fi
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==3')" != "" ]; then 
        while true ; do 
            case $(cat /tmp/xci/mounts | awk '{print $1}') in
                *$(cat $(echo $mountdef) | grep -i "SMB:" | sed 's/smb://g' | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==3')*)
                    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Unmounting your shares, Please wait..." 3 50
                    umount.cifs -l /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==3') &>> ~/setup/logs/xci-backup.log
                    sleep 1
                    rmdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==3') &>> ~/setup/logs/xci-backup.log
                    df -h >/tmp/xci/mounts 2>>~/setup/logs/xci-backup.log
                    sed -i '/udev/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '/none/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '1d' /tmp/xci/mounts
                    sed -i ':a;N;$!ba;s/\n                   / /g' /tmp/xci/mounts;;
                *) break;;
            esac
        done
    fi
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==4')" != "" ]; then 
        while true ; do 
            case $(cat /tmp/xci/mounts | awk '{print $1}') in
                *$(cat $(echo $mountdef) | grep -i "SMB:" | sed 's/smb://g' | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==4')*)
                    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Unmounting your shares, Please wait..." 3 50
                    umount.cifs -l /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==4') &>> ~/setup/logs/xci-backup.log
                    sleep 1
                    rmdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==4') &>> ~/setup/logs/xci-backup.log
                    df -h >/tmp/xci/mounts 2>>~/setup/logs/xci-backup.log
                    sed -i '/udev/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '/none/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '1d' /tmp/xci/mounts
                    sed -i ':a;N;$!ba;s/\n                   / /g' /tmp/xci/mounts;;
                *) break;;
            esac
        done
    fi
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==5')" != "" ]; then 
        while true ; do 
            case $(cat /tmp/xci/mounts | awk '{print $1}') in
                *$(cat $(echo $mountdef) | grep -i "SMB:" | sed 's/smb://g' | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==5')*)
                    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Unmounting your shares, Please wait..." 3 50
                    umount.cifs -l /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==5') &>> ~/setup/logs/xci-backup.log
                    sleep 1
                    rmdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==5') &>> ~/setup/logs/xci-backup.log
                    df -h >/tmp/xci/mounts 2>>~/setup/logs/xci-backup.log
                    sed -i '/udev/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '/none/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '1d' /tmp/xci/mounts
                    sed -i ':a;N;$!ba;s/\n                   / /g' /tmp/xci/mounts;;
                *) break;;
            esac
        done
    fi
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==6')" != "" ]; then 
        while true ; do 
            case $(cat /tmp/xci/mounts | awk '{print $1}') in
                *$(cat $(echo $mountdef) | grep -i "SMB:" | sed 's/smb://g' | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==6')*)
                    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Unmounting your shares, Please wait..." 3 50
                    umount.cifs -l /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==6') &>> ~/setup/logs/xci-backup.log
                    sleep 1
                    rmdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==6') &>> ~/setup/logs/xci-backup.log
                    df -h >/tmp/xci/mounts 2>>~/setup/logs/xci-backup.log
                    sed -i '/udev/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '/none/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '1d' /tmp/xci/mounts
                    sed -i ':a;N;$!ba;s/\n                   / /g' /tmp/xci/mounts;;
                *) break;;
            esac
        done
    fi
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==7')" != "" ]; then 
        while true ; do 
            case $(cat /tmp/xci/mounts | awk '{print $1}') in
                *$(cat $(echo $mountdef) | grep -i "SMB:" | sed 's/smb://g' | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==7')*)
                    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Unmounting your shares, Please wait..." 3 50
                    umount.cifs -l /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==7') &>> ~/setup/logs/xci-backup.log
                    sleep 1
                    rmdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==7') &>> ~/setup/logs/xci-backup.log
                    df -h >/tmp/xci/mounts 2>>~/setup/logs/xci-backup.log
                    sed -i '/udev/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '/none/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '1d' /tmp/xci/mounts
                    sed -i ':a;N;$!ba;s/\n                   / /g' /tmp/xci/mounts;;
                *) break;;
            esac
        done
    fi
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==8')" != "" ]; then 
        while true ; do 
            case $(cat /tmp/xci/mounts | awk '{print $1}') in
                *$(cat $(echo $mountdef) | grep -i "SMB:" | sed 's/smb://g' | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==8')*)
                    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Unmounting your shares, Please wait..." 3 50
                    umount.cifs -l /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==8') &>> ~/setup/logs/xci-backup.log
                    sleep 1
                    rmdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==8') &>> ~/setup/logs/xci-backup.log
                    df -h >/tmp/xci/mounts 2>>~/setup/logs/xci-backup.log
                    sed -i '/udev/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '/none/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '1d' /tmp/xci/mounts
                    sed -i ':a;N;$!ba;s/\n                   / /g' /tmp/xci/mounts;;
                *) break;;
            esac
        done
    fi
    if [ "$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==9')" != "" ]; then 
        while true ; do 
            case $(cat /tmp/xci/mounts | awk '{print $1}') in
                *$(cat $(echo $mountdef) | grep -i "SMB:" | sed 's/smb://g' | awk  -F'[<|>]' '/path/{print $3}' | awk 'NR==9')*)
                    dialog --colors --title "\Z1[ INFORMATION ]\Zn" --infobox "     Unmounting your shares, Please wait..." 3 50
                    umount.cifs -l /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[<|>]' '/path/{print $3}'| sed 's/smb://g' | awk 'BEGIN { FS = "/" } ; {print $4}' | awk 'NR==9') &>> ~/setup/logs/xci-backup.log
                    sleep 1
                    rmdir /media/$(cat $(echo $mountdef) | grep -i "SMB:" | awk  -F'[/]' '/path/{print $4}' | awk 'NR==9') &>> ~/setup/logs/xci-backup.log
                    df -h >/tmp/xci/mounts 2>>~/setup/logs/xci-backup.log
                    sed -i '/udev/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '/none/d' /tmp/xci/mounts &>> ~/setup/logs/xci-backup.log
                    sed -i '1d' /tmp/xci/mounts
                    sed -i ':a;N;$!ba;s/\n                   / /g' /tmp/xci/mounts;;
                *) break;;
            esac
        done
    fi

}

function Backup_Script(){
    ##--[ BACKUP PROMPT ]---------------------------------------------------------------

    if [ ! -e $(echo $APPLOC)/setup/sources.xml ]; then
        cp /home/xbmc/.xbmc/userdata/sources.xml $(echo $APPLOC)/setup &>> ~/setup/logs/xci-backup.log
    fi
    
    while true ;do
        backupxbmc="no"
        backupmedia="no"
        dialog  --clear --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
                --colors --title "\Z4[ BACKUP MENU ]\Zn" \
                --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 14 45 5 \
                1 "XBMC Settings" \
                2 "Local Media" 2>/tmp/xci/backupmenu
    
        case $? in
          0)
            backupmenuitem=$(</tmp/xci/backupmenu)
            case $backupmenuitem in
                1) backupxbmc="yes";;
                2) backupmedia="yes";;
            esac;;
          1)
            break;;
          255)
            break;;
        esac
    
    while true ; do
        if [ "$backupxbmc" = "yes" ]; then 
            backupxbmcdata="no"
            backupuserdata="no"
            backupuplugins="no"
            backupuscripts="no"
            backupuskins="no"
            foldername="none"
            dialog  --clear --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
                    --colors --title "\Z4[ BACKUP MENU ]\Zn" \
                    --checklist "\nPlease select what you wish to backup\nPress Space to (de)select an item:" 14 46 10 \
                    1 "Full Backup" ON \
                    2 "Userdata Only" OFF \
                    3 "Plugins Only" OFF \
                    4 "Scripts Only" OFF \
                    5 "Skins Only" OFF 2>/tmp/xci/xbmcbackupmenu
        
            case $? in
              0)
                xbmcbackupmenuitem=$(</tmp/xci/xbmcbackupmenu)
                case $xbmcbackupmenuitem in
                    *1*) backupxbmcdata="yes";;&
                    *2*) backupuserdata="yes";;&
                    *3*) backupuplugins="yes";;&
                    *4*) backupuscripts="yes";;&
                    *5*) backupuskins="yes";;
                esac;;
              1)
                break;;
              255)
                break;;
            esac
        elif [ "$backupmedia" = "yes" ]; then 
            backupmusic="no"
            backupvideos="no"
            foldername="none"
            dialog  --clear --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
                    --colors --title "\Z4[ BACKUP MENU ]\Zn" \
                    --checklist "\nPlease select what you wish to backup\nPress Space to (de)select an item:" 14 46 10 \
                    1 "Music Folder" ON \
                    2 "Videos Folder" ON 2>/tmp/xci/mediabackupmenu
        
            case $? in
              0)
                mediabackupmenuitem=$(</tmp/xci/mediabackupmenu)
                case $mediabackupmenuitem in
                    *1*) backupmusic="yes";;&
                    *2*) backupvideos="yes";;
                esac;;
              1)
                break;;
              255)
                break;;
            esac
        fi
    
    Mount_Script

    dialog  --clear  --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ BACKUP MENU ]\Zn" \
            --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose a destination Drive:" 21 50 9 \
            1 "$(cat /tmp/xci/mounts | awk 'NR==1 {print $1}')" \
            2 "$(cat /tmp/xci/mounts | awk 'NR==2 {print $1}')" \
            3 "$(cat /tmp/xci/mounts | awk 'NR==3 {print $1}')" \
            4 "$(cat /tmp/xci/mounts | awk 'NR==4 {print $1}')" \
            5 "$(cat /tmp/xci/mounts | awk 'NR==5 {print $1}')" \
            6 "$(cat /tmp/xci/mounts | awk 'NR==6 {print $1}')" \
            7 "$(cat /tmp/xci/mounts | awk 'NR==7 {print $1}')" \
            8 "$(cat /tmp/xci/mounts | awk 'NR==8 {print $1}')" \
            9 "$(cat /tmp/xci/mounts | awk 'NR==9 {print $1}')" 2>/tmp/xci/mountschoice
     
    mountsmenuitem=$(</tmp/xci/mountschoice)
     
    case $mountsmenuitem in
        1) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==1 {print $6}')";cd $(echo $mountpiont);;
        2) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==2 {print $6}')";cd $(echo $mountpiont);;
        3) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==3 {print $6}')";cd $(echo $mountpiont);;
        4) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==4 {print $6}')";cd $(echo $mountpiont);;
        5) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==5 {print $6}')";cd $(echo $mountpiont);;
        6) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==6 {print $6}')";cd $(echo $mountpiont);;
        7) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==7 {print $6}')";cd $(echo $mountpiont);;
        8) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==8 {print $6}')";cd $(echo $mountpiont);;
        9) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==9 {print $6}')";cd $(echo $mountpiont);;
    esac

    while [ "$(ls -l | grep -i "drw" | awk 'NR==1 {print $8}')" != "" -a  "$(ls -l | awk '{print $8}'| grep -i "xbmc")" = "" -a  "$(ls -l | awk '{print $8}'| grep -i "Media")" = "" ] ; do
        dialog  --clear  --help-button --help-label "Current Folder" --cancel-label "New Folder" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
                --colors --title "\Z4[ BACKUP MENU ]\Zn" \
                --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose a destination folder:" 21 50 9 \
                1 "$(ls -l | grep -i "drw" | awk 'NR==1 {print $8}')" \
                2 "$(ls -l | grep -i "drw" | awk 'NR==2 {print $8}')" \
                3 "$(ls -l | grep -i "drw" | awk 'NR==3 {print $8}')" \
                4 "$(ls -l | grep -i "drw" | awk 'NR==4 {print $8}')" \
                5 "$(ls -l | grep -i "drw" | awk 'NR==5 {print $8}')" \
                6 "$(ls -l | grep -i "drw" | awk 'NR==6 {print $8}')" \
                7 "$(ls -l | grep -i "drw" | awk 'NR==7 {print $8}')" \
                8 "$(ls -l | grep -i "drw" | awk 'NR==8 {print $8}')" \
                9 "$(ls -l | grep -i "drw" | awk 'NR==9 {print $8}')" 2>/tmp/xci/folderchoice
         
        case $? in
            0)
                foldermenuitem=$(</tmp/xci/folderchoice)
                case $foldermenuitem in
                    1) foldername="$(ls -l | grep -i "drw" | awk 'NR==1 {print $8}')";cd $(echo $foldername);;
                    2) foldername="$(ls -l | grep -i "drw" | awk 'NR==2 {print $8}')";cd $(echo $foldername);;
                    3) foldername="$(ls -l | grep -i "drw" | awk 'NR==3 {print $8}')";cd $(echo $foldername);;
                    4) foldername="$(ls -l | grep -i "drw" | awk 'NR==4 {print $8}')";cd $(echo $foldername);;
                    5) foldername="$(ls -l | grep -i "drw" | awk 'NR==5 {print $8}')";cd $(echo $foldername);;
                    6) foldername="$(ls -l | grep -i "drw" | awk 'NR==6 {print $8}')";cd $(echo $foldername);;
                    7) foldername="$(ls -l | grep -i "drw" | awk 'NR==7 {print $8}')";cd $(echo $foldername);;
                    8) foldername="$(ls -l | grep -i "drw" | awk 'NR==8 {print $8}')";cd $(echo $foldername);;
                    9) foldername="$(ls -l | grep -i "drw" | awk 'NR==9 {print $8}')";cd $(echo $foldername);;
                esac;;
            1)
                dialog  --clear --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --colors --title "\Z4[ NEW FOLDER ]\Zn" --inputbox " Enter folder name:" 8 50 2>/tmp/xci/foldername
                foldername="$(</tmp/xci/foldername)"
                mkdir $(echo $foldername) &>> ~/setup/logs/xci-backup.log;;
            2)
                break;;
        esac
    done

    destination="$(pwd)"
    echo $destination >/tmp/xci/restoresource
    mkdir $(echo "$destination")/xbmc &>> ~/setup/logs/xci-backup.log
    mkdir $(echo "$destination")/Media &>> ~/setup/logs/xci-backup.log
    
    if [ "$backupxbmcdata" = "yes" ]; then
        if [ "$backupuserdata" != "yes" -o "$backupuplugins" != "yes" -o "$backupuscripts" != "yes" -o "$backupuskins" != "yes" ]; then
            cd /home/xbmc/.xbmc
            #(tar cvf - . 2>>~/setup/logs/xci-backup.log | pv -n -s `du -sb . | awk '{ print $1 }'` | gzip > $(echo "$destination")/XBMC_Folder-$(date +%d-%m-%Y_%H-%M-%S).taz.gz) 2>&1 | dialog --colors --title "\Z1[ BACKUP OPERATION PROGRESS ]\Zn" --gauge '  Full Backup' 6 60
            (rsync -avz /home/xbmc/.xbmc/ $(echo "$destination")/xbmc/ | pv -n -l -s `rsync -navz /home/xbmc/.xbmc/ $(echo "$destination")/xbmc/ | wc -l` >>~/setup/logs/xci-backup.log) 2>&1 | dialog --colors --title "\Z1[ BACKUP OPERATION PROGRESS ]\Zn" --gauge '  Full Backup' 6 60
            sleep 1
            echo "100" | dialog --colors --title "\Z1[ BACKUP COMPLETE ]\Zn" --gauge '  Full Backup' 6 60
            sleep 1
        else
        dialog --colors --title "\Z1[ INFORMATION ]\Zn" --msgbox "\nInvalid selection! When \Z4FULL BACKUP\Zn option is selected no other choices are required! " 8 60
        fi
    fi
    if [ "$backupxbmcdata" != "yes" ]; then
        if [ "$backupuserdata" = "yes" ]; then
            #(tar cvf - . 2>>~/setup/logs/xci-backup.log | pv -n -s `du -sb . | awk '{ print $1 }'` | gzip > $(echo "$destination")/Userdata_Folder-$(date +%d-%m-%Y_%H-%M-%S).taz.gz) 2>&1 | dialog --colors --title "\Z1[ BACKUP OPERATION PROGRESS ]\Zn" --gauge '  Userdata' 6 60
            (rsync -avz /home/xbmc/.xbmc/userdata $(echo "$destination")/xbmc/userdata | pv -n -l -s `rsync -navz /home/xbmc/.xbmc/userdata $(echo "$destination")/xbmc/userdata | wc -l` >>~/setup/logs/xci-backup.log) 2>&1 | dialog --colors --title "\Z1[ BACKUP OPERATION PROGRESS ]\Zn" --gauge '  Userdata Backup' 6 60
            sleep 1
            echo "100" | dialog --sleep 1 --colors --title "\Z1[ BACKUP COMPLETE ]\Zn" --gauge '  Userdata' 6 60
        fi
        if [ "$backupuplugins" = "yes" ]; then
            #(tar cvf - . 2>>~/setup/logs/xci-backup.log | pv -n -s `du -sb . | awk '{ print $1 }'` | gzip > $(echo "$destination")/Plugins_Folder-$(date +%d-%m-%Y_%H-%M-%S).taz.gz) 2>&1 | dialog --colors --title "\Z1[ BACKUP OPERATION PROGRESS ]\Zn" --gauge '  Plugins' 6 60
            (rsync -avz /home/xbmc/.xbmc/plugins $(echo "$destination")/xbmc/plugins | pv -n -l -s `rsync -navz /home/xbmc/.xbmc/plugins $(echo "$destination")/xbmc/plugins | wc -l` >>~/setup/logs/xci-backup.log) 2>&1 | dialog --colors --title "\Z1[ BACKUP OPERATION PROGRESS ]\Zn" --gauge '  Plugins Backup' 6 60
            sleep 1
            echo "100" | dialog --sleep 1 --colors --title "\Z1[ BACKUP COMPLETE ]\Zn" --gauge '  Plugins' 6 60
        fi
        if [ "$backupuscripts" = "yes" ]; then
            #(tar cvf - . 2>>~/setup/logs/xci-backup.log | pv -n -s `du -sb . | awk '{ print $1 }'` | gzip > $(echo "$destination")/Scripts_Folder-$(date +%d-%m-%Y_%H-%M-%S).taz.gz) 2>&1 | dialog --colors --title "\Z1[ BACKUP OPERATION PROGRESS ]\Zn" --gauge '  Scripts' 6 60
            (rsync -avz /home/xbmc/.xbmc/scripts $(echo "$destination")/xbmc/scripts | pv -n -l -s `rsync -navz /home/xbmc/.xbmc/scripts $(echo "$destination")/xbmc/scripts | wc -l` >>~/setup/logs/xci-backup.log) 2>&1 | dialog --colors --title "\Z1[ BACKUP OPERATION PROGRESS ]\Zn" --gauge '  Scripts Backup' 6 60
            sleep 1
            echo "100" | dialog --sleep 1 --colors --title "\Z1[ BACKUP COMPLETE ]\Zn" --gauge '  Scripts' 6 60
        fi
        if [ "$backupuskins" = "yes" ]; then
            #(tar cvf - . 2>>~/setup/logs/xci-backup.log | pv -n -s `du -sb . | awk '{ print $1 }'` | gzip > $(echo "$destination")/Skins_Folder-$(date +%d-%m-%Y_%H-%M-%S).taz.gz) 2>&1 | dialog --colors --title "\Z1[ BACKUP OPERATION PROGRESS ]\Zn" --gauge '  Skins' 6 60
            (rsync -avz /home/xbmc/.xbmc/skin $(echo "$destination")/xbmc/skin | pv -n -l -s `rsync -navz /home/xbmc/.xbmc/skin $(echo "$destination")/xbmc/skin | wc -l` >>~/setup/logs/xci-backup.log) 2>&1 | dialog --colors --title "\Z1[ BACKUP OPERATION PROGRESS ]\Zn" --gauge '  Skins Backup' 6 60
            sleep 1
            echo "100" | dialog --sleep 1 --colors --title "\Z1[ BACKUP COMPLETE ]\Zn" --gauge '  Skins' 6 60
        fi
    fi
    if [ "$backupmusic" = "yes" ]; then
        #(tar cvf - . 2>>~/setup/logs/xci-backup.log | pv -n -s `du -sb . | awk '{ print $1 }'` | gzip > $(echo "$destination")/Userdata_Folder-$(date +%d-%m-%Y_%H-%M-%S).taz.gz) 2>&1 | dialog --colors --title "\Z1[ BACKUP OPERATION PROGRESS ]\Zn" --gauge '  Userdata' 6 60
        (rsync -avz /home/xbmc/Music/ $(echo "$destination")/Media/Music | pv -n -l -s `rsync -navz /home/xbmc/Music/ $(echo "$destination")/Media/Music | wc -l` >>~/setup/logs/xci-backup.log) 2>&1 | dialog --colors --title "\Z1[ BACKUP OPERATION PROGRESS ]\Zn" --gauge '  Music Backp' 6 60
        sleep 1
        echo "100" | dialog --sleep 1 --colors --title "\Z1[ BACKUP COMPLETE ]\Zn" --gauge '  Music' 6 60
    fi
    if [ "$backupvideos" = "yes" ]; then
        #(tar cvf - . 2>>~/setup/logs/xci-backup.log | pv -n -s `du -sb . | awk '{ print $1 }'` | gzip > $(echo "$destination")/Plugins_Folder-$(date +%d-%m-%Y_%H-%M-%S).taz.gz) 2>&1 | dialog --colors --title "\Z1[ BACKUP OPERATION PROGRESS ]\Zn" --gauge '  Plugins' 6 60
        (rsync -avz /home/xbmc/Videos/ $(echo "$destination")/Media/Videos | pv -n -l -s `rsync -navz /home/xbmc/Videos/ $(echo "$destination")/Media/Videos | wc -l` >>~/setup/logs/xci-backup.log) 2>&1 | dialog --colors --title "\Z1[ BACKUP OPERATION PROGRESS ]\Zn" --gauge '  Videos Backup' 6 60
        sleep 1
        echo "100" | dialog --sleep 1 --colors --title "\Z1[ BACKUP COMPLETE ]\Zn" --gauge '  Videos' 6 60
    fi

    chown -R xbmc:xbmc /home/xbmc &>> ~/setup/logs/xci-backup.log
    Unmount_Script
    
    done
    done
}

function Restore_Script(){
    ##--[ BACKUP PROMPT ]---------------------------------------------------------------

    while true ;do
        restorexbmc="no"
        restoremedia="no"
        dialog  --clear --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
                --colors --title "\Z4[ RESTORE MENU ]\Zn" \
                --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 14 45 5 \
                1 "XBMC Settings" \
                2 "Local Media" 2>/tmp/xci/restoremenu
    
        case $? in
          0)
            restoremenuitem=$(</tmp/xci/restoremenu)
            case $restoremenuitem in
                1) restorexbmc="yes";;
                2) restoremedia="yes";;
            esac;;
          1)
            break;;
          255)
            break;;
        esac

    while true ; do
        if [ "$restorexbmc" = "yes" ]; then 
            restorexbmcdata="no"
            restoreuserdata="no"
            restoreplugins="no"
            restorescripts="no"
            restoreskins="no"
            foldername="none"
            dialog  --clear --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
                    --colors --title "\Z4[ RESTORE MENU ]\Zn" \
                    --checklist "\nPlease select what you wish to restore\nPress space to (de)select an item:" 14 46 10 \
                    1 "Full Restore" ON \
                    2 "Userdata Only" OFF \
                    3 "Plugins Only" OFF \
                    4 "Scripts Only" OFF \
                    5 "Skins Only" OFF 2>/tmp/xci/restoremenu
        
            case $? in
              0)
                restoremenuitem=$(</tmp/xci/restoremenu)
                case $restoremenuitem in
                    *1*) restorexbmcdata="yes";;&
                    *2*) restoreuserdata="yes";;&
                    *3*) restoreplugins="yes";;&
                    *4*) restorescripts="yes";;&
                    *5*) restoreskins="yes";;
                esac;;
              1)
                break;;
              255)
                break;;
            esac
    
        elif [ "$restoremedia" = "yes" ]; then 
            restoremusic="no"
            restorevideos="no"
            foldername="none"
            dialog  --clear --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
                    --colors --title "\Z4[ RESTORE MENU ]\Zn" \
                    --checklist "\nPlease select what you wish to restore\nPress Space to (de)select an item:" 14 46 10 \
                    1 "Music Folder" ON \
                    2 "Videos Folder" ON 2>/tmp/xci/mediarestoremenu
            case $? in
              0)
                mediarestoremenuitem=$(</tmp/xci/mediarestoremenu)
                case $mediarestoremenuitem in
                    *1*) restoremusic="yes";;&
                    *2*) restorevideos="yes";;
                esac;;
              1)
                break;;
              255)
                break;;
            esac
        fi

    Mount_Script

    dialog  --clear  --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ RESTORE MENU ]\Zn" \
            --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose your source Drive:" 21 50 9 \
            1 "$(cat /tmp/xci/mounts | awk 'NR==1 {print $1}')" \
            2 "$(cat /tmp/xci/mounts | awk 'NR==2 {print $1}')" \
            3 "$(cat /tmp/xci/mounts | awk 'NR==3 {print $1}')" \
            4 "$(cat /tmp/xci/mounts | awk 'NR==4 {print $1}')" \
            5 "$(cat /tmp/xci/mounts | awk 'NR==5 {print $1}')" \
            6 "$(cat /tmp/xci/mounts | awk 'NR==6 {print $1}')" \
            7 "$(cat /tmp/xci/mounts | awk 'NR==7 {print $1}')" \
            8 "$(cat /tmp/xci/mounts | awk 'NR==8 {print $1}')" \
            9 "$(cat /tmp/xci/mounts | awk 'NR==9 {print $1}')" 2>/tmp/xci/mountschoice
     
    mountsmenuitem=$(</tmp/xci/mountschoice)
     
    case $mountsmenuitem in
        1) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==1 {print $6}')";cd $(echo $mountpiont);;
        2) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==2 {print $6}')";cd $(echo $mountpiont);;
        3) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==3 {print $6}')";cd $(echo $mountpiont);;
        4) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==4 {print $6}')";cd $(echo $mountpiont);;
        5) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==5 {print $6}')";cd $(echo $mountpiont);;
        6) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==6 {print $6}')";cd $(echo $mountpiont);;
        7) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==7 {print $6}')";cd $(echo $mountpiont);;
        8) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==8 {print $6}')";cd $(echo $mountpiont);;
        9) mountpiont="$(cat /tmp/xci/mounts | awk 'NR==9 {print $6}')";cd $(echo $mountpiont);;
    esac

    while [ "$(ls -l | awk '{print $8}'| grep -i "xbmc")" = "" -o "$(ls -l | awk '{print $8}'| grep -i "Media")" = "" ] ; do
        dialog  --clear  --no-cancel --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
                --colors --title "\Z4[ RESTORE MENU ]\Zn" \
                --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose your source folder:" 21 50 9 \
                1 "$(ls -l | grep -i "drw" | awk 'NR==1 {print $8}')" \
                2 "$(ls -l | grep -i "drw" | awk 'NR==2 {print $8}')" \
                3 "$(ls -l | grep -i "drw" | awk 'NR==3 {print $8}')" \
                4 "$(ls -l | grep -i "drw" | awk 'NR==4 {print $8}')" \
                5 "$(ls -l | grep -i "drw" | awk 'NR==5 {print $8}')" \
                6 "$(ls -l | grep -i "drw" | awk 'NR==6 {print $8}')" \
                7 "$(ls -l | grep -i "drw" | awk 'NR==7 {print $8}')" \
                8 "$(ls -l | grep -i "drw" | awk 'NR==8 {print $8}')" \
                9 "$(ls -l | grep -i "drw" | awk 'NR==9 {print $8}')" 2>/tmp/xci/folderchoice
         
        case $? in
          0)
                foldermenuitem=$(</tmp/xci/folderchoice)
                case $foldermenuitem in
                    1) foldername="$(ls -l | grep -i "drw" | awk 'NR==1 {print $8}')";cd $(echo $foldername);;
                    2) foldername="$(ls -l | grep -i "drw" | awk 'NR==2 {print $8}')";cd $(echo $foldername);;
                    3) foldername="$(ls -l | grep -i "drw" | awk 'NR==3 {print $8}')";cd $(echo $foldername);;
                    4) foldername="$(ls -l | grep -i "drw" | awk 'NR==4 {print $8}')";cd $(echo $foldername);;
                    5) foldername="$(ls -l | grep -i "drw" | awk 'NR==5 {print $8}')";cd $(echo $foldername);;
                    6) foldername="$(ls -l | grep -i "drw" | awk 'NR==6 {print $8}')";cd $(echo $foldername);;
                    7) foldername="$(ls -l | grep -i "drw" | awk 'NR==7 {print $8}')";cd $(echo $foldername);;
                    8) foldername="$(ls -l | grep -i "drw" | awk 'NR==8 {print $8}')";cd $(echo $foldername);;
                    9) foldername="$(ls -l | grep -i "drw" | awk 'NR==9 {print $8}')";cd $(echo $foldername);;
                esac;;
        esac
    done

    restoresource="$(pwd)"
    mkdir /home/xbmc/.xbmc/ &>> ~/setup/logs/xci-backup.log
    
    if [ "$restorexbmcdata" = "yes" ]; then
        if [ "$restoreuserdata" != "yes" -o "$restoreplugins" != "yes" -o "$restorescripts" != "yes" -o "$restoreskins" != "yes" ]; then
            #(tar cvf - . 2>>~/setup/logs/xci-restore.log | pv -n -s `du -sb . | awk '{ print $1 }'` | gzip > $(echo "$destination")/XBMC_Folder-$(date +%d-%m-%Y_%H-%M-%S).taz.gz) 2>&1 | dialog --colors --title "\Z1[ RESTORE OPERATION PROGRESS ]\Zn" --gauge '  Full restore' 6 60
            (rsync -avz $(echo "$restoresource")/xbmc/ /home/xbmc/.xbmc/ | pv -n -l -s `rsync -navz $(echo "$restoresource")/xbmc/ /home/xbmc/.xbmc/ | wc -l` >>~/setup/logs/xci-backup.log) 2>&1 | dialog --colors --title "\Z1[ RESTORE OPERATION PROGRESS ]\Zn" --gauge '  Full Restore' 6 60
            sleep 1
            echo "100" | dialog --sleep 1 --colors --title "\Z1[ RESTORE COMPLETE ]\Zn" --gauge '  Full Restore' 6 60
        else
        dialog --colors --title "\Z1[ INFORMATION! ]\Zn" --msgbox "Invalid selection! When \Z1FULL RESTORE\Zn option is selected no other choices are required! " 6 60
        fi
    fi

    if [ "$restorexbmcdata" != "yes" ]; then
        if [ "$restoreuserdata" = "yes" ]; then
            #(tar cvf - . 2>>~/setup/logs/xci-restore.log | pv -n -s `du -sb . | awk '{ print $1 }'` | gzip > $(echo "$destination")/Userdata_Folder-$(date +%d-%m-%Y_%H-%M-%S).taz.gz) 2>&1 | dialog --colors --title "\Z1[ RESTORE OPERATION PROGRESS ]\Zn" --gauge '  Userdata' 6 60
            (rsync -avz $(echo "$restoresource")/xbmc/userdata/ /home/xbmc/.xbmc/userdata | pv -n -l -s `rsync -navz $(echo "$restoresource")/xbmc/userdata/ /home/xbmc/.xbmc/userdata | wc -l` >>~/setup/logs/xci-backup.log) 2>&1 | dialog --colors --title "\Z1[ RESTORE OPERATION PROGRESS ]\Zn" --gauge '  Userdata Restore' 6 60
            sleep 1
            echo "100" | dialog --sleep 1 --colors --title "\Z4[ RESTORE COMPLETE ]\Zn" --gauge '  Userdata' 6 60
        fi
        if [ "$restoreplugins" = "yes" ]; then
            #(tar cvf - . 2>>~/setup/logs/xci-restore.log | pv -n -s `du -sb . | awk '{ print $1 }'` | gzip > $(echo "$destination")/Plugins_Folder-$(date +%d-%m-%Y_%H-%M-%S).taz.gz) 2>&1 | dialog --colors --title "\Z1[ RESTORE OPERATION PROGRESS ]\Zn" --gauge '  Plugins' 6 60
            (rsync -avz $(echo "$restoresource")/xbmc/plugins/ /home/xbmc/.xbmc/plugins | pv -n -l -s `rsync -navz $(echo "$restoresource")/xbmc/userdata/ /home/xbmc/.xbmc/plugins | wc -l` >>~/setup/logs/xci-backup.log) 2>&1 | dialog --colors --title "\Z1[ RESTORE OPERATION PROGRESS ]\Zn" --gauge '  Plugins Restore' 6 60
            sleep 1
            echo "100" | dialog --sleep 1 --colors --title "\Z1[ RESTORE COMPLETE ]\Zn" --gauge '  Plugins' 6 60
        fi
        if [ "$restorescripts" = "yes" ]; then
            #(tar cvf - . 2>>~/setup/logs/xci-restore.log | pv -n -s `du -sb . | awk '{ print $1 }'` | gzip > $(echo "$destination")/Scripts_Folder-$(date +%d-%m-%Y_%H-%M-%S).taz.gz) 2>&1 | dialog --colors --title "\Z1[ RESTORE OPERATION PROGRESS ]\Zn" --gauge '  Scripts' 6 60
            (rsync -avz $(echo "$restoresource")/xbmc/scripts/ /home/xbmc/.xbmc/scripts | pv -n -l -s `rsync -navz $(echo "$restoresource")/xbmc/userdata/ /home/xbmc/.xbmc/scripts | wc -l` >>~/setup/logs/xci-backup.log) 2>&1 | dialog --colors --title "\Z1[ RESTORE OPERATION PROGRESS ]\Zn" --gauge '  Scripts Restore' 6 60
            sleep 1
            echo "100" | dialog --sleep 1 --colors --title "\Z1[ RESTORE COMPLETE ]\Zn" --gauge '  Scripts' 6 60
        fi
        if [ "$restoreskins" = "yes" ]; then
            #(tar cvf - . 2>>~/setup/logs/xci-restore.log | pv -n -s `du -sb . | awk '{ print $1 }'` | gzip > $(echo "$destination")/Skins_Folder-$(date +%d-%m-%Y_%H-%M-%S).taz.gz) 2>&1 | dialog --colors --title "\Z1[ RESTORE OPERATION PROGRESS ]\Zn" --gauge '  Skins' 6 60
            (rsync -avz $(echo "$restoresource")/xbmc/skin/ /home/xbmc/.xbmc/skin | pv -n -l -s `rsync -navz $(echo "$restoresource")/xbmc/userdata/ /home/xbmc/.xbmc/skin | wc -l` >>~/setup/logs/xci-backup.log) 2>&1 | dialog --colors --title "\Z1[ RESTORE OPERATION PROGRESS ]\Zn" --gauge '  Skins Restore' 6 60
            sleep 1
            echo "100" | dialog --sleep 1 --colors --title "\Z1[ RESTORE COMPLETE ]\Zn" --gauge '  Skins' 6 60
        fi
    fi
    if [ "$restoremusic" = "yes" ]; then
        (rsync -avz $(echo "$restoresource")/Media/Music/ /home/xbmc/Music | pv -n -l -s `rsync -navz $(echo "$(echo "$restoresource")/Media/Music/ /home/xbmc/Music | wc -l` >>~/setup/logs/xci-backup.log) 2>&1 | dialog --colors --title "\Z1[ RESTORE OPERATION PROGRESS ]\Zn" --gauge '  Music Restore' 6 60
        sleep 1
        echo "100" | dialog --sleep 1 --colors --title "\Z1[ RESTORE COMPLETE ]\Zn" --gauge '  Music' 6 60
    fi
    if [ "$restorevideos" = "yes" ]; then
        (rsync -avz $(echo "$restoresource")/Media/Videos/ /home/xbmc/Videos | pv -n -l -s `rsync -navz $(echo "$(echo "$restoresource")/Media/Videos/ /home/xbmc/Videos | wc -l` >>~/setup/logs/xci-backup.log) 2>&1 | dialog --colors --title "\Z1[ RESTORE OPERATION PROGRESS ]\Zn" --gauge '  Videos Restore' 6 60
        sleep 1
        echo "100" | dialog --sleep 1 --colors --title "\Z1[ RESTORE COMPLETE ]\Zn" --gauge '  Videos' 6 60
    fi
    
    Unmount_Script
    
    done
    done
}

function XBMC_Options_Menu(){
    while true
    do
    ### display main menu ###
    dialog  --cancel-label "Go Back" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ XBMC SETUP OPTIONS ]\Zn" \
            --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 18 45 6 \
            1 "Change Boot Screen" \
            2 "Setup XBMC to use SVN PPA" \
            3 "Revert XBMC to use Stable 9.11" \
            4 "Setup/Compile/Update SVN" \
            5 "Setup BluRay Playback" \
            6 "Setup Display for 1080P 23.976 Hz" 2>/tmp/xci/xbmcoptionmenu
     
    case $? in
      0)
        xbmcoptionsmenuitem=$(</tmp/xci/xbmcoptionmenu)
        case $xbmcoptionsmenuitem in
            1) Change_Boot_Screen_Menu;;
            2) Setup_SVN_PPA_Install;;
            3) Setup_SVN_PPA_Remove;;
            4) Build_SVN_Menu;;
            5) Setup_BluRay_Playback;;
            6) Setup_24p;;
        esac;;
      1)
            break;;
      255)
            break;;
    esac
    done
}

function Change_Boot_Screen_Menu(){
    while true
    do
    changebootscrnchoice=""
# Usplash selection menu
    dialog  --clear --cancel-label "Go Back" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ BOOT SCREEN SETUP ]\Zn" \
            --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 16 45 4 \
            1 "Black & Silver" \
            2 "Pulsating Logo" \
            3 "Spinner Black" \
            4 "Spinner Blue" 2>/tmp/xci/changebootscreenmenu
     
    case $? in
      0)
        changebootscreenmenuitem=$(</tmp/xci/changebootscreenmenu)
        case $changebootscreenmenuitem in
            1) changebootscrnchoice="Black & Silver";;
            2) changebootscrnchoice="Pulsating Logo";;
            3) changebootscrnchoice="Spinner Black";;
            4) changebootscrnchoice="Spinner Blue";;
        esac;;
      1)
            break;;
      255)
            break;;
    esac

    echo "0" | dialog --colors --title "\Z1[ CHANGING BOOT SCREEN ]\Zn" --gauge "  Please wait..." 6 70 0
    aptitude install ~nusplash-theme-xbmc -y &>> ~/setup/logs/xci-bootscreen.log
    echo "25" | dialog --colors --title "\Z1[ CHANGING BOOT SCREEN ]\Zn" --gauge "  Please wait..." 6 70 0
    if [ "$changebootscrnchoice" = "Black & Silver" ]; then
        update-alternatives --set usplash-artwork.so /usr/lib/usplash/xbmc-splash-spinner-black-silver.so &>> ~/setup/logs/xci-bootscreen.log
    elif [ "$changebootscrnchoice" = "Pulsating Logo" ]; then
        update-alternatives --set usplash-artwork.so /usr/lib/usplash/xbmc-splash-pulsating-logo.so &>> ~/setup/logs/xci-bootscreen.log
    elif [ "$changebootscrnchoice" = "Spinner Black" ]; then
        update-alternatives --set usplash-artwork.so /usr/lib/usplash/xbmc-splash-spinner-black.so &>> ~/setup/logs/xci-bootscreen.log
    elif [ "$changebootscrnchoice" = "Spinner Blue" ]; then
        update-alternatives --set usplash-artwork.so /usr/lib/usplash/xbmc-splash-spinner-spinner-blue.so &>> ~/setup/logs/xci-bootscreen.log
    fi
    echo "75" | dialog --colors --title "\Z1[ CHANGING BOOT SCREEN ]\Zn" --gauge "  Please wait..." 6 70 0
    update-initramfs -u &>> ~/setup/logs/xci-bootscreen.log
    echo "100" | dialog --sleep 3 --colors --title "\Z1[ CHANGING BOOT SCREEN ]\Zn" --gauge "  Boot screen setup complete! Boot screen set to $changebootscrnchoice" 6 70 0
    done
}

# add SVN PPA repositories
function Setup_SVN_PPA_Install(){
    dialog --colors --title "\Z1[ CONFIRMATION ]\Zn"  --yesno " XBMC-Live 9.11 must be previously Installed! \n Has this been completed?" 6 52
    case $? in
      0)
        service xbmc-live stop &>> ~/setup/logs/xci-svn-ppa-setup.log
        if [ "$CUR_OS" = "karmic" ]; then
            echo "10" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR SVN PPA ]\Zn" --gauge "  ADDING XBMC SVN REPOSITORY! Please wait..." 6 70 0
            add-apt-repository ppa:team-xbmc-svn/ppa &>> ~/setup/logs/xci-svn-ppa-setup.log
            echo deb http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu karmic main >> /etc/apt/sources.list.d/team-xbmc-svn-ppa-karmic.list
            echo deb-src http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu karmic main >> /etc/apt/sources.list.d/team-xbmc-svn-ppa-karmic.list
        elif [ "$CUR_OS" = "jaunty" ]; then
            echo "10" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR SVN PPA! ]\Zn" --gauge "  ADDING XBMC SVN REPOSITORY! Please wait..." 6 70 0
            echo '#' XBMC Repositories >> /etc/apt/sources.list
            echo deb http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu jaunty main >> /etc/apt/sources.list
            echo deb-src http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu jaunty main >> /etc/apt/sources.list
            apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 64234534 &>> ~/setup/logs/xci-svn-ppa-setup.log
        fi
        echo "25" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR SVN PPA ]\Zn" --gauge "  CHECKING FOR XBMC UPDATES! Please wait..." 6 70 0
        aptitude update &>> ~/setup/logs/xci-svn-ppa-setup.log
        echo "50" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR SVN PPA ]\Zn" --gauge "  UPDATING SVN! Please wait..." 6 70 0
        case $(aptitude safe-upgrade -s -y | grep -i "grub") in
            *grub*) aptitude safe-upgrade -y -q 2>>~/setup/logs/xci-svn-ppa-setup.log;;
            *) aptitude safe-upgrade -y -q &>> ~/setup/logs/xci-svn-ppa-setup.log;;
        esac
        aptitude install libcurl3 -y &>> ~/setup/logs/xci-svn-ppa-setup.log
        wget http://dl.dropbox.com/u/4325533/XCI/custom-actions.pkla &>> ~/setup/logs/xci-svn-ppa-setup.log
        mv -f custom-actions.pkla /var/lib/polkit-1/localauthority/50-local.d/custom-actions.pkla
        echo "100" | dialog --colors --title "\Z1[ XBMC NOW SETUP FOR SVN PPA ]\Zn" --gauge "  XBMC will now restart! " 6 70 0;;
      1)
        ;;
      255)
        ;;
    esac
}

##### SVN PPA REMOVAL SCRIPT #####
function Setup_SVN_PPA_Remove(){
    dialog --colors --title "\Z1[ CONFIRMATION ]\Zn"  --yesno " XBMC SVN PPA must be previously Installed! \n Has this been completed?" 6 52
    case $? in
      0)
        service xbmc-live stop &>> ~/setup/logs/xci-svn-ppa-remove.log
        echo "0" | dialog --colors --title "\Z1[ REVERTING XBMC TO STABLE 9.11 ]\Zn" --gauge "  REMOVING XBMC SVN REPOSITORY! Please wait..." 6 70 0
        rm -f /etc/apt/sources.list.d/team-xbmc-svn-ppa-karmic.list* &>> ~/setup/logs/xci-svn-ppa-remove.log
        echo "10" | dialog --colors --title "\Z1[ REVERTING XBMC TO STABLE 9.11 ]\Zn" --gauge "  REINSTALLING XBMC! Please wait..." 6 70 0
        aptitude install xbmc=1:9.11-karmic1 -y &>> ~/setup/logs/xci-svn-ppa-remove.log
        echo "40" | dialog --colors --title "\Z1[ REVERTING XBMC TO STABLE 9.11 ]\Zn" --gauge "  REINSTALLING XBMC! Please wait..." 6 70 0
        aptitude install ~nxbmc-eventclients -y &>> ~/setup/logs/xci-svn-ppa-remove.log
        echo "50" | dialog --colors --title "\Z1[ REVERTING XBMC TO STABLE 9.11 ]\Zn" --gauge "  REINSTALLING XBMC! Please wait..." 6 70 0
        aptitude install ~nxbmc-scripts -y &>> ~/setup/logs/xci-svn-ppa-remove.log
        echo "60" | dialog --colors --title "\Z1[ REVERTING XBMC TO STABLE 9.11 ]\Zn" --gauge "  REINSTALLING XBMC HELPERS! Please wait..." 6 70 0
        aptitude install xbmc-live python-apt -y &>> ~/setup/logs/xci-svn-ppa-remove.log
        echo "90" | dialog --colors --title "\Z1[ REVERTING XBMC TO STABLE 9.11 ]\Zn" --gauge "  CONFIGURING POWER MANAGEMENT! Please wait..." 6 70 0
        aptitude install pm-utils policykit devicekit-power devicekit-disks -y &>> ~/setup/logs/xci-svn-ppa-remove.log
        polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.suspend &>> ~/setup/logs/xci-svn-ppa-remove.log
        polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.hibernate &>> ~/setup/logs/xci-svn-ppa-remove.log
        polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.reboot &>> ~/setup/logs/xci-svn-ppa-remove.log
        polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.shutdown &>> ~/setup/logs/xci-svn-ppa-remove.log
        polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.reboot-multiple-sessions &>> ~/setup/logs/xci-svn-ppa-remove.log
        polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.shutdown-multiple-sessions &>> ~/setup/logs/xci-svn-ppa-remove.log
        aptitude install libcurl3 -y &>> ~/setup/logs/xci-svn-ppa-setup.log
        #wget http://dl.dropbox.com/u/4325533/XCI/custom-actions.pkla &>> ~/setup/logs/xci-svn-ppa-setup.log
        #mv -f custom-actions.pkla /var/lib/polkit-1/localauthority/50-local.d/custom-actions.pkla
        echo "100" | dialog --sleep 1 --colors --title "\Z1[ REVERTED XBMC TO STANDARD 9.11 ]\Zn" --gauge "  XBMC will now restart!" 6 70 0
         ;;
      1)
        ;;
      255)
        ;;
    esac
}


# build svn menu
function Build_SVN_Menu(){
    while true
    do
    dialog  --clear --cancel-label "Go Back" --backtitle "XBMC Live Setup for $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ COMPILE SVN TRUNK  ]\Zn" \
            --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 14 45 4 \
            1 "Setup Build Environment & Install" \
            2 "Update & Install" 2>/tmp/xci/buildsvnmenu
     
    case $? in
      0)
        buildsvnmenuitem=$(</tmp/xci/buildsvnmenu)
        case $buildsvnmenuitem in
            1)     dialog --colors --title "\Z1[ CONFIRMATION ]\Zn"  --yesno "XBMC 9.11 Must be previously Installed to continue\n\nPlease Note the following Procedure can take 1 - 2 Hours to Complete! \n\nDo You Want to Continue (y/n)" 11 44
                if [ $? = 0 ]; then
                    service xbmc-live stop &>> ~/setup/logs/xci-svn-build.log
                    echo "1" | dialog --colors --title "\Z1[ SETTING-UP SYSTEM FOR SVN BUILDING ]\Zn" --gauge "  PREPARING! Please wait..." 6 70 0
                    cp /etc/apt/sources.list /etc/apt/sources.list-backup &>> ~/setup/logs/xci-svn-build.log
                    echo "5" | dialog --colors --title "\Z1[ SETTING-UP SYSTEM FOR SVN BUILDING ]\Zn" --gauge "  PREPARING! Please wait..." 6 70 0
                    add-apt-repository ppa:team-xbmc-svn/ppa &>> ~/setup/logs/xci-svn-build.log
                    echo "6" | dialog --colors --title "\Z1[ SETTING-UP SYSTEM FOR SVN BUILDING ]\Zn" --gauge "  PREPARING! Please wait..." 6 70 0
                    add-apt-repository ppa:team-xbmc/ppa &>> ~/setup/logs/xci-svn-build.log
                    echo "10" | dialog --colors --title "\Z1[ SETTING-UP SYSTEM FOR SVN BUILDING ]\Zn" --gauge "  PREPARING! Please wait..." 6 70 0
                    echo deb http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu karmic main >> /etc/apt/sources.list &>> ~/setup/logs/xci-svn-build.log
                    echo deb-src http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu karmic main >> /etc/apt/sources.list &>> ~/setup/logs/xci-svn-build.log
                    echo "11" | dialog --colors --title "\Z1[ SETTING-UP SYSTEM FOR SVN BUILDING ]\Zn" --gauge "  PREPARING! Please wait..." 6 70 0
                    aptitude autoclean -y &>> ~/setup/logs/xci-svn-build.log
                    echo "12" | dialog --colors --title "\Z1[ SETTING-UP SYSTEM FOR SVN BUILDING ]\Zn" --gauge "  INSTALLING REQUIRED TOOLS! Please wait..." 6 70 0
                    aptitude update -y &>> ~/setup/logs/xci-svn-build.log
                    echo "13" | dialog --colors --title "\Z1[ SETTING-UP SYSTEM FOR SVN BUILDING ]\Zn" --gauge "  INSTALLING REQUIRED TOOLS! Please wait..." 6 70 0
                    aptitude install ccache libvdpau-dev debhelper zip subversion make g++ gcc gawk pmountlibtool nasm automake cmake gperf gettext unzip bison libsdl-dev libsdl-image1.2-dev libsdl-gfx1.2-dev libsdl-mixer1.2-dev libfribidi-dev liblzo2-dev libfreetype6-dev libsqlite3-dev libogg-dev libasound-dev python-sqlite libglew-dev libcurl3 libcurl4-openssl-dev x11proto-xinerama-dev libxinerama-dev libxrandr-dev libxrender-dev libmad0-dev libogg-dev libvorbisenc2 libsmbclient-dev libmysqlclient-dev libpcre3-dev libdbus-1-dev libhal-dev libhal-storage-dev libjasper-dev libfontconfig-dev libbz2-dev libboost-dev libfaac-dev libenca-dev libxt-dev libxtst-dev libxmu-dev libpng-dev libjpeg-dev libpulse-dev mesa-utils libcdio-dev libsamplerate-dev libmms-dev libmpeg3-dev libfaad-dev libflac-dev libiso9660-dev libass-dev libssl-dev fp-compiler gdc libwavpack-dev libmpeg2-4-dev libmicrohttpd-dev libmodplug-dev -y -q &>> ~/setup/logs/xci-svn-build.log
                    echo "14" | dialog --colors --title "\Z1[ SETTING-UP SYSTEM FOR SVN BUILDING ]\Zn" --gauge "  DOWNLOADING SVN! This will take some time! Please wait..." 6 70 0
                    apt-get build-dep xbmc -y &>> ~/setup/logs/xci-svn-build.log
                    echo "15" | dialog --colors --title "\Z1[ SETTING-UP SYSTEM FOR SVN BUILDING ]\Zn" --gauge "  DOWNLOADING SVN! This will take some time! Please wait..." 6 70 0        
                    cp /etc/apt/sources.list-backup /etc/apt/sources.list &>> ~/setup/logs/xci-svn-build.log
                    echo "16" | dialog --colors --title "\Z1[ SETTING-UP SYSTEM FOR SVN BUILDING ]\Zn" --gauge "  DOWNLOADING SVN! This will take some time! Please wait..." 6 70 0        
                    rm -r -f /etc/apt/sources.list-backup &>> ~/setup/logs/xci-svn-build.log
                    cd $HOME/setup
                    ((svn checkout https://xbmc.svn.sourceforge.net/svnroot/xbmc/trunk/ xbmc-svn 2>&1) | pv -e -l -s 19878 12>>~/setup/logs/xci-svn-build.log) 2>&1 | dialog --colors --title "\Z1[ SETTING-UP SYSTEM FOR SVN BUILDING ]\Zn" --gauge '  DOWNLOADING SVN! This will take some time! Please wait...' 6 70                
                    cd $HOME/setup/xbmc-svn
                    ((./bootstrap 2>&1 ; ./configure 2>&1 ; make -j4 2>&1) | pv -n -l -s 9858 12>>~/setup/logs/xci-svn-build.log) 2>&1 | dialog --colors --title "\Z1[ SETTING-UP SYSTEM FOR SVN BUILDING ]\Zn" --gauge '  COMPILING SVN! This will take some time! Please wait...' 6 70
                    echo "85" | dialog --colors --title "\Z1[ SETTING-UP SYSTEM FOR SVN BUILDING ]\Zn" --gauge "  INSTALLING SVN! Please wait..." 6 70 0
                    make install &>> ~/setup/logs/xci-svn-build.log
                    echo "90" | dialog --colors --title "\Z1[ SETTING-UP SYSTEM FOR SVN BUILDING! ]\Zn" --gauge "  INSTALLING SVN! Please wait..." 6 70 0
                    rm -r /usr/share/xbmc &>> ~/setup/logs/xci-svn-build.log
                    mv /usr/local/share/xbmc /usr/share/ &>> ~/setup/logs/xci-svn-build.log
                    make install &>> ~/setup/logs/xci-svn-build.log
                    echo "95" | dialog --colors --title "\Z1[ SETTING-UP SYSTEM FOR SVN BUILDING ]\Zn" --gauge "  IINSTALLING SVN! Please wait..." 6 70 0
                    wget http://dl.dropbox.com/u/4325533/XCI/custom-actions.pkla &>> ~/setup/logs/xci-svn-build.log
                    mv -f custom-actions.pkla /var/lib/polkit-1/localauthority/50-local.d/custom-actions.pkla
                    echo "100" | dialog --sleep 3 --colors --title "\Z1[ FINISHED BUILDING SVN ]\Zn" --gauge "  XBMC will now restart! " 6 70 0
                    service xbmc-live start &>> ~/setup/logs/xci-svn-build.log
                fi ;;
            2)     dialog --colors --title "\Z1[ CONFIRMATION ]\Zn"  --yesno "XBMC 9.11 Must be previously installed to continue\n\nPlease note the following procedure can take 1 hour to complete! \n\nDo You Want to Continue (y/n)" 11 44
                if [ $? = 0 ]; then
# XBMC SVN System Update
                    echo "0" | dialog --colors --title "\Z1[ UPDATING THE SVN BUILD ]\Zn" --gauge "  Please wait..." 6 70 0
                    service xbmc-live stop &>> ~/setup/logs/xci-svn-update.log
                    echo "2" | dialog --colors --title "\Z1[ UPDATING THE SVN BUILD ]\Zn" --gauge "  DDWNLOADING UPDATES! Please wait..." 6 70 0
                    cd $HOME/setup/xbmc-svn
                    svn up &>> ~/setup/logs/xci-svn-update.log
                    ((make clean 2>&1 ; ./bootstrap 2>&1 ; ./configure 2>&1 ; make -j4 2>&1) | pv -n -l -s 9858 12>>~/setup/logs/xci-svn-update.error.log) 2>&1 | dialog --colors --title "\Z1[ SETTING-UP SYSTEM FOR SVN BUILDING! ]\Zn" --gauge '  COMPILING SVN! This will take some time! Please wait...' 6 70
                    echo "80" | dialog --colors --title "\Z1[ UPDATING THE SVN BUILD ]\Zn" --gauge "  INSTALLING UPDATED SVN! Please wait..." 6 70 0
                    make install &>> ~/setup/logs/xci-svn-update.log
                    echo "90" | dialog --colors --title "\Z1[ UPDATING THE SVN BUILD ]\Zn" --gauge "  INSTALLING UPDATED SVN! Please wait..." 6 70 0
                    rm -f -r /usr/share/xbmc
                    mv /usr/local/share/xbmc /usr/share/
                    echo "95" | dialog --colors --title "\Z1[ UPDATING THE SVN BUILD! ]\Zn" --gauge "  INSTALLING UPDATED SVN! Please wait..." 6 70 0
                    make install &>> ~/setup/logs/xci-svn-update.log
                    echo "100" | dialog --sleep 3 --colors --title "\Z1[ UPDATING THE SVN BUILD ]\Zn" --gauge "  FININSHED UPDATING SVN BUILD! " 6 70 0
                    service xbmc-live start &>> ~/setup/logs/xci-svn-update.log
                fi ;;
        esac;;
      1)
            break;;
      255)
            break;;
    esac
    done
}

function Setup_BluRay_Playback(){
    echo "0" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR BLURAY PLAYBACK ]\Zn" --gauge "  INSTALLING REQUIRED TOOLS! Please wait..." 6 70 0
    aptitude install build-essential -y -q2 &>> ~/setup/logs/xci-bluray-playback.log
    echo "5" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR BLURAY PLAYBACK ]\Zn" --gauge "  INSTALLING REQUIRED TOOLS! Please wait..." 6 70 0
    aptitude install libc6-dev -y -q2 &>> ~/setup/logs/xci-bluray-playback.log
    echo "10" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR BLURAY PLAYBACK ]\Zn" --gauge "  INSTALLING REQUIRED TOOLS! Please wait..." 6 70 0
    aptitude install libssl-dev -y -q2 &>> ~/setup/logs/xci-bluray-playback.log
    echo "15" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR BLURAY PLAYBACK ]\Zn" --gauge "  INSTALLING REQUIRED TOOLS! Please wait..." 6 70 0
    aptitude install libgl1-mesa-dev -y -q2 &>> ~/setup/logs/xci-bluray-playback.log
    echo "20" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR BLURAY PLAYBACK ]\Zn" --gauge "  INSTALLING REQUIRED TOOLS! Please wait..." 6 70 0
    aptitude install libqt4-dev -y -q2 &>> ~/setup/logs/xci-bluray-playback.log
    echo "25" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR BLURAY PLAYBACK ]\Zn" --gauge "  INSTALLING REQUIRED TOOLS! Please wait..." 6 70 0
    wget http://dl.dropbox.com/u/4325533/XCI/Bluray/makemkv_v1.5.6_beta_bin.tar.gz &>> ~/setup/logs/xci-bluray-playback.log
    echo "30" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR BLURAY PLAYBACK ]\Zn" --gauge "  DOWNLOADING REQUIREMENTS ! Please wait..." 6 70 0
    wget http://dl.dropbox.com/u/4325533/XCI/Bluray/makemkv_v1.5.6_beta_oss.tar.gz &>> ~/setup/logs/xci-bluray-playback.log
    echo "30" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR BLURAY PLAYBACK ]\Zn" --gauge "  EXTRACTING! Please wait..." 6 70 0
    tar xzf makemkv_v1.5.6_beta_bin.tar.gz &>> ~/setup/logs/xci-bluray-playback.log
    echo "35" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR BLURAY PLAYBACK ]\Zn" --gauge "  EXTRACTING! Please wait..." 6 70 0
    tar xzf makemkv_v1.5.6_beta_oss.tar.gz &>> ~/setup/logs/xci-bluray-playback.log
    cd makemkv_v1.5.6_beta_oss
    echo "40" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR BLURAY PLAYBACK ]\Zn" --gauge "  BUILDING APPLICATION! THIS CAN TAKE A WHILE! Please wait..." 6 70 0
    make -f -j4 makefile.linux &>> ~/setup/logs/xci-bluray-playback.log
    echo "70" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR BLURAY PLAYBACK ]\Zn" --gauge "  INSTALLING APPLICATION! Please wait..." 6 70 0
    make -f makefile.linux install &>> ~/setup/logs/xci-bluray-playback.log
    cd ../makemkv_v1.5.6_beta_bin
    echo "75" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR BLURAY PLAYBACK ]\Zn" --gauge "  INSTALLING APPLICATION! Please wait..." 6 70 0
    sed -i '/ask_eula.sh/d' makefile.linux &>> ~/setup/logs/xci-bluray-playback.log
    echo "77" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR BLURAY PLAYBACK ]\Zn" --gauge "  INSTALLING APPLICATION Please wait..." 6 70 0
    make -f makefile.linux &>> ~/setup/logs/xci-bluray-playback.log
    make -f makefile.linux install &>> ~/setup/logs/xci-bluray-playback.log
    echo "90" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR BLURAY PLAYBACK ]\Zn" --gauge "  INSTALLING PLUGIN! Please wait..." 6 70 0
    wget http://dl.dropbox.com/u/4325533/XCI/Bluray/BluRay-plugin.tar.gz &>> ~/setup/logs/xci-bluray-playback.log
    echo "90" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR BLURAY PLAYBACK ]\Zn" --gauge "  INSTALLING PLUGIN! Please wait..." 6 70 0
    tar xzf BluRay-plugin.tar.gz
    echo "95" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR BLURAY PLAYBACK ]\Zn" --gauge "  INSTALLING PLUGIN! Please wait..." 6 70 0
    mv -f BluRay /home/xbmc/.xbmc/plugins/video
    chown -R xbmc:xbmc /home/xbmc/.xbmc/plugins/video/BluRay
    cd ..
    rm -fr BluRay-plugin.tar.gz
    rm -fr makemkv_v1.5.6*
    echo "100" | dialog --sleep 3 --colors --title "\Z1[ SETTING-UP XBMC FOR BLURAY PLAYBACK ]\Zn" --gauge "  BLURAY PLAYBACK SET-UP COMPLETE! " 6 70 0
}


function Setup_24p(){
    echo "0" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR 1080P 23.976 Hz ]\Zn" --gauge "  BACKING UP OLD CONFIG! Please wait..." 6 70 0
    if [ ! "$DISPLAY" = "" ]; then echo "Run in a TTY. Press CTRL-ALT-F1"; exit; fi
    [ -d "$HOME/old" ] \
     || mkdir "$HOME/old"  &>> ~/setup/logs/xci-video-change.log
    [ ! -f "$HOME/old/xorg.conf" ] && [ -f /etc/X11/xorg.conf ] && cp /etc/X11/xorg.conf "$HOME/old" &>> ~/setup/logs/xci-video-change.log
    [ ! -f "$HOME/old/.nvidia-settings-rc" ] && [ -f $HOME/.nvidia-settings-rc ] && cp "$HOME/.nvidia-settings-rc" "$HOME/old" &>> ~/setup/logs/xci-video-change.log
    [ ! -f "$HOME/old/guisettings.xml" ] && cp "$HOME/.xbmc/userdata/guisettings.xml" "$HOME/old"  &>> ~/setup/logs/xci-video-change.log
    
    echo "20" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR 1080P 23.976 Hz ]\Zn" --gauge "  CREATING NEW CONFIG! Please wait..." 6 70 0
# 2/6 Applying Xorg settings
    echo 'Section "Device"' > /etc/X11/xorg.conf
    echo '    Identifier   "nvidia"' >> /etc/X11/xorg.conf
    echo '    Driver       "nvidia"' >> /etc/X11/xorg.conf
    echo '    Option       "NoLogo"              "true"' >> /etc/X11/xorg.conf
    echo '    Option       "DynamicTwinView"     "false"' >> /etc/X11/xorg.conf
    echo '    Option       "FlatPanelProperties" "Scaling = Native"' >> /etc/X11/xorg.conf
    echo '    Option       "ModeValidation"      "NoVesaModes, NoXServerModes, NoVertRefreshCheck, NoHorizSyncCheck"' >> /etc/X11/xorg.conf
    echo '    Option       "ModeDebug"           "true"' >> /etc/X11/xorg.conf
    echo '    Option       "HWCursor"            "false"' >> /etc/X11/xorg.conf
    echo 'EndSection' >> /etc/X11/xorg.conf
    echo '' >> /etc/X11/xorg.conf
    echo 'Section "Screen"' >> /etc/X11/xorg.conf
    echo '    Identifier   "Screen0"' >> /etc/X11/xorg.conf
    echo '    Device       "Device0"' >> /etc/X11/xorg.conf
    echo '    Monitor      "Monitor0"' >> /etc/X11/xorg.conf
    echo '    DefaultDepth 24' >> /etc/X11/xorg.conf
    echo '    SubSection   "Display"' >> /etc/X11/xorg.conf
    echo '          Modes  "1920x1080_60" "1280x720_60" "1360x768_60" "1024x768_60"' >> /etc/X11/xorg.conf
    echo '    EndSubSection' >> /etc/X11/xorg.conf
    echo 'EndSection' >> /etc/X11/xorg.conf
    echo '' >> /etc/X11/xorg.conf
    echo 'Section "Extensions"' >> /etc/X11/xorg.conf
    echo '    Option       "Composite"           "false"' >> /etc/X11/xorg.conf
    echo 'EndSection' >> /etc/X11/xorg.conf
    echo '' >> /etc/X11/xorg.conf
    
    echo "40" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR 1080P 23.976 Hz ]\Zn" --gauge "  DETECTING VIDEO MODES! Please wait..." 6 70 0
# 3/6 Restarting Xorg to find available modes
    service xbmc-live stop &>> ~/setup/logs/xci-video-change.log
    sleep 5
    service xbmc-live start &>> ~/setup/logs/xci-video-change.log
    sleep 5

    videovendor="$(sed -n '/ (GPU-0)/p' /var/log/Xorg.0.log | awk '{print $6}')"
    videomodel="$(sed -n '/Connected display device(s) on/p' /var/log/Xorg.0.log | awk '{print $10}')"
    monitorvendor="$(sed -n '/Manufacturer/p' /var/log/Xorg.0.log | awk '{print $8}')"
    monitormodel="$(sed -n '/Monitor Name/p' /var/log/Xorg.0.log | awk '{print $9,$10}')"
    connecteddisplay="$(sed -n '/Assigned Display Device:/p' /var/log/Xorg.0.log | awk '{print $9}')"
    sed -i '5i\    VendorName   "'$videovendor'"' /etc/X11/xorg.conf
    sed -i '6i\    BoardName    "'$videomodel'"' /etc/X11/xorg.conf
    sed -i '7i\    Option       "ConnectedMonitor"    "'$connecteddisplay'"' /etc/X11/xorg.conf
    sed -i 's/   VendorName    "Default"/   VendorName    "'$monitorvendor'"' /etc/default/grub
    sed -i 's/   ModelName     "Default"/   ModelName     "'$monitormodel'"' /etc/default/grub
    echo 'Section "Monitor"' >> /etc/X11/xorg.conf
    echo '   Identifier    "Monitor0"' >> /etc/X11/xorg.conf
    echo '   VendorName    "'$monitorvendor'"' >> /etc/X11/xorg.conf
    echo '   ModelName     "'$monitormodel'"' >> /etc/X11/xorg.conf
    echo '   Option        "DPMS"' >> /etc/X11/xorg.conf
       echo 'EndSection' >> /etc/X11/xorg.conf
    echo '' >> /etc/X11/xorg.conf
    
# 4/6 Adding 23.97Hz and 59.94Hz to xorg.conf
    echo "60" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR 1080P 23.976 Hz ]\Zn" --gauge "  CONFIGURING XORG! Please wait..." 6 70 0
    modes="$(sed -n '/- Modes/,/- End/p' /var/log/Xorg.0.log | sed 's/.*(0)://g' | awk '/CEA-861B Format (32|31|16)/{printf $1 " "}')"
    sed -n 's/(from: EDID)//g;/- Modes/,/- End/p' /var/log/Xorg.0.log | cut -c32- | sed 's/^/# /g' >>/etc/X11/xorg.conf
    [ "$modes" = "" ] ||sed -i "s/Modes  \".*/Modes $modes/g" /etc/X11/xorg.conf

# 5/6 Applying NVIDIA settings
    echo "80" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR 1080P 23.976 Hz ]\Zn" --gauge "  CONFIGURING XORG! Please wait..." 6 70 0
#    if [ -f /usr/lib/libgtk-x11-2.0.so.0 ]; then
#        sleep 5
#        export DISPLAY=:0
#        nvidia-settings -a "SyncToVBlank=1" -a "AllowFlipping=1" -a "FSAAAppControlled=1" -a "OpenGLImageSettings=3" -a "LogAniso=0" -a "GPUScaling=1,1" &>> ~/setup/logs/xci-video-change.log
#        sleep 5
#        nvidia-settings -r &>> ~/setup/logs/xci-video-change.log
#        sleep 5
#    fi

    echo '#' > /home/xbmc/.nvidia-settings-rc
    echo '# /home/xbmc/.nvidia-settings-rc' >> /home/xbmc/.nvidia-settings-rc
    echo '#' >> /home/xbmc/.nvidia-settings-rc
    echo '# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility' >> /home/xbmc/.nvidia-settings-rc
    echo '# Generated on Mon Mar 15 15:28:09 2010' >> /home/xbmc/.nvidia-settings-rc
    echo '#' >> /home/xbmc/.nvidia-settings-rc
    echo '' >> /home/xbmc/.nvidia-settings-rc
    echo '# ConfigProperties:' >> /home/xbmc/.nvidia-settings-rc
    echo '' >> /home/xbmc/.nvidia-settings-rc
    echo 'RcFileLocale = C' >> /home/xbmc/.nvidia-settings-rc
    echo 'ToolTips = Yes' >> /home/xbmc/.nvidia-settings-rc
    echo 'DisplayStatusBar = Yes' >> /home/xbmc/.nvidia-settings-rc
    echo 'SliderTextEntries = Yes' >> /home/xbmc/.nvidia-settings-rc
    echo 'IncludeDisplayNameInConfigFile = No' >> /home/xbmc/.nvidia-settings-rc
    echo 'ShowQuitDialog = Yes' >> /home/xbmc/.nvidia-settings-rc
    echo '' >> /home/xbmc/.nvidia-settings-rc
    echo '# Attributes:' >> /home/xbmc/.nvidia-settings-rc
    echo '' >> /home/xbmc/.nvidia-settings-rc
    echo '0/SyncToVBlank=1' >> /home/xbmc/.nvidia-settings-rc
    echo '0/LogAniso=0' >> /home/xbmc/.nvidia-settings-rc
    echo '0/FSAA=0' >> /home/xbmc/.nvidia-settings-rc
    echo '0/TextureSharpen=0' >> /home/xbmc/.nvidia-settings-rc
    echo '0/AllowFlipping=1' >> /home/xbmc/.nvidia-settings-rc
    echo '0/FSAAAppControlled=1' >> /home/xbmc/.nvidia-settings-rc
    echo '0/LogAnisoAppControlled=1' >> /home/xbmc/.nvidia-settings-rc
    echo '0/OpenGLImageSettings=3' >> /home/xbmc/.nvidia-settings-rc
    echo '0/FSAAAppEnhanced=0' >> /home/xbmc/.nvidia-settings-rc
    echo '0/RedBrightness=0.000000' >> /home/xbmc/.nvidia-settings-rc
    echo '0/GreenBrightness=0.000000' >> /home/xbmc/.nvidia-settings-rc
    echo '0/BlueBrightness=0.000000' >> /home/xbmc/.nvidia-settings-rc
    echo '0/RedContrast=0.000000' >> /home/xbmc/.nvidia-settings-rc
    echo '0/GreenContrast=0.000000' >> /home/xbmc/.nvidia-settings-rc
    echo '0/BlueContrast=0.000000' >> /home/xbmc/.nvidia-settings-rc
    echo '0/Gamma=1.20000' >> /home/xbmc/.nvidia-settings-rc
    echo '0/DigitalVibrance['$connecteddisplay']=0' >> /home/xbmc/.nvidia-settings-rc
    echo '0/GPUScaling['$connecteddisplay']=65537' >> /home/xbmc/.nvidia-settings-rc
    echo '0/XVideoTextureBrightness=0' >> /home/xbmc/.nvidia-settings-rc
    echo '0/XVideoTextureContrast=0' >> /home/xbmc/.nvidia-settings-rc
    echo '0/XVideoTextureHue=0' >> /home/xbmc/.nvidia-settings-rc
    echo '0/XVideoTextureSaturation=0' >> /home/xbmc/.nvidia-settings-rc
    echo '0/XVideoTextureSyncToVBlank=1' >> /home/xbmc/.nvidia-settings-rc
    echo '0/XVideoSyncToDisplay=65536' >> /home/xbmc/.nvidia-settings-rc

    sed -i '/nvidia-settings/d' /usr/bin/runXBMC
    sed -i '52i\    echo "/usr/bin/nvidia-settings --load-config-only" >>  /home/$xbmcUser/.xsession' /usr/bin/runXBMC
    chown xbmc:xbmc /home/xbmc/.nvidia-settings-rc
    
    # 6/6 Applying XBMC settings
    echo "90" | dialog --colors --title "\Z1[ SETTING-UP XBMC FOR 1080P 23.976 Hz ]\Zn" --gauge "  CONFIGURING XBMC! Please wait..." 6 70 0
    f="/home/xbmc/.xbmc/userdata/guisettings.xml"
    v="usedisplayasclock";    sed -i "s/<$v>.*</<$v>true</" $f
    v="synctype";        sed -i "s/<$v>.*</<$v>2</" $f
    v="adjustrefreshrate";    sed -i "s/<$v>.*</<$v>true</" $f
    v="rendermethod";    sed -i "s/<$v>.*</<$v>4</" $f
    v="vsync";        sed -i "s/<$v>.*</<$v>2</" $f
    v="usepbo";        sed -i "s/<$v>.*</<$v>true</" $f
    chown xbmc:xbmc /home/xbmc/.xbmc/userdata/guisettings.xml
    echo "100" | dialog --sleep 1 --colors --title "\Z1[ FINISHED DETECTING TV ]\Zn" --gauge "  System will reboot now" 6 70
    reboot  
    exit
}


function System_Update(){
    service xbmc-live stop &>> ~/setup/logs/xci-system-upgrade.log
    echo "0" | dialog --colors --title "\Z1[ CHECKING FOR UPDATES ]\Zn" --gauge "  DOWNLOADING UPDATES! Please wait..." 6 70 0
    aptitude update -y &>> ~/setup/logs/xci-system-upgrade.log
    echo "50" | dialog --colors --title "\Z1[ INSTALLING UPDATES ]\Zn" --gauge "  INSTALLING UPDATES! Please wait..." 6 70 0
    case $(aptitude safe-upgrade -s -y | grep -i "grub") in
        *grub*) aptitude safe-upgrade -y -q 2>>~/setup/logs/xci-system-upgrade.log;;
        *) aptitude safe-upgrade -y -q &>> ~/setup/logs/xci-system-upgrade.log;;
    esac
    dialog --colors --title "\Z1[ FINISHED UPDATING ]\Zn" --msgbox "\n  SYSTEM going down for reboot..." 7 40
    reboot
    break
}
function System_Upgrade(){
    service xbmc-live stop &>> ~/setup/logs/xci-system-upgrade.log
    echo "0" | dialog --colors --title "\Z1[ CHECKING FOR UPGRADES ]\Zn" --gauge "  Please wait..." 6 70 0
    aptitude update -y &>> ~/setup/logs/xci-system-upgrade.log
    echo "50" | dialog --colors --title "\Z1[ INSTALLING UPGRADES ]\Zn" --gauge "  Please wait..." 6 70 0
    case $(aptitude full-upgrade -s -y | grep -i "grub") in
        *grub*) aptitude full-upgrade -y -q 2>>~/setup/logs/xci-system-upgrade.log;;
        *) aptitude full-upgrade -y -q &>> ~/setup/logs/xci-system-upgrade.log;;
    esac
    dialog --colors --title "\Z1[ FINISHED UPGRADING ]\Zn" --msgbox "\n  SYSTEM going down for reboot..." 7 40
    reboot  
    exit
}

function Support(){
    dialog --colors --title "\Z1[ CONFIRMATION ]\Zn"  --yesno " \n You're about to upload your logs to\n \Z4http://xbmc-installer.pastebin.ca\Zn\n\n Are you sure?" 10 44

    if [ $? = 0 ]; then
        cd ~/setup/logs
        if [ -e xci-installer.log ]; then
        echo "0" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-installer.log" 6 60 0
        installer=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca xci-installer.log)
        else
        echo "0" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-installer.log not found, skipping..." 6 60 0
        fi
        if [ -e xci-video-change.log ]; then
        echo "6" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-video-change.log" 6 60 0
        videochangeinstaller=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca xci-video-change.log)
        else
        echo "6" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-video-change.log not found, skipping..." 6 60 0
        fi
        if [ -e xci-sound.log ]; then
        echo "12" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-sound.log" 6 60 0
        soundinstaller=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca xci-sound.log)
        else
        echo "12" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-sound.log not found, skipping..." 6 60 0
        fi
        if [ -e xci-remote.log ]; then
        echo "19" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-remote.log" 6 60 0
        remoteinstaller=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca xci-remote.log)
        else
        echo "19" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-remote.log not found, skipping..." 6 60 0
        fi
        if [ -e xci-temp.log ]; then
        echo "25" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-temp.log" 6 60 0
        tempinstaller=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca xci-temp.log)
        else
        echo "25" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-temp.log not found, skipping..." 6 60 0
        fi
        if [ -e xci-bootscreen.log ]; then
        echo "31" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-bootscreen.log" 6 60 0
        bootscreeninstaller=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca xci-bootscreen.log)
        else
        echo "31" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-bootscreen.log not found, skipping..." 6 60 0
        fi
        if [ -e xci-svn-ppa-setup.log ]; then
        echo "37" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-svn-ppa-setup.log" 6 60 0
        svnppainstaller=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca xci-svn-ppa-setup.log)
        else
        echo "37" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-svn-ppa-setup.log not found, skipping..." 6 60 0
        fi
        if [ -e xci-bluray-playback.log ]; then
        echo "44" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-bluray-playback.log" 6 60 0
        blurayplaybackinstaller=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca xci-bluray-playback.log)
        else
        echo "44" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-bluray-playback.log not found, skipping..." 6 60 0
        fi
        if [ -e xci-svn-build.log ]; then
        echo "50" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-svn-build.log" 6 60 0
        svnbuildinstaller=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca xci-svn-build.log)
        else
        echo "50" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-svn-build.log not found, skipping..." 6 60 0
        fi
        if [ -e xci-svn-update.log ]; then
        echo "56" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-svn-update.log" 6 60 0
        svnupdateinstaller=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca xci-svn-update.log)
        else
        echo "56" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-svn-update.log not found, skipping..." 6 60 0
        fi
        if [ -e xci-system-update.log ]; then
        echo "62" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-system-update.log" 6 60 0
        systempupdateinstaller=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca xci-system-update.log)
        else
        echo "62" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-system-update.log not found, skipping..." 6 60 0
        fi
        if [ -e xci-system-upgrade.log ]; then
        echo "68" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-system-upgrade.log" 6 60 0
        systemupgradeinstaller=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca xci-system-upgrade.log)
        else
        echo "68" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-system-upgrade.log not found, skipping..." 6 60 0
        fi
        if [ -e xci-bluetooth.log ]; then
        echo "75" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-bluetooth.log, this one might take a while! " 6 60 0
        bluetooth=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca xci-bluetooth.log)
        else
        echo "75" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-bluetooth.log not found, skipping" 6 60 0
        fi
        if [ -e xci-addons.log ]; then
        echo "76" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-addons.log, please wait" 6 60 0
        addons=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca xci-addons.log)
        else
        echo "76" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xci-addons.log not found, skipping" 6 60 0
        fi
        if [ -e /home/xbmc/.xbmc/temp/xbmc.log ]; then
        echo "81" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xbmc-debug.log" 6 60 0
        xbmcdebug=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca /home/xbmc/.xbmc/temp/xbmc.log)
        else
        echo "81" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  xbmc-debug.log not found, skipping..." 6 60 0
        fi
        if [ -e /var/log/aptitude ]; then
        echo "87" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  aptitude.log" 6 60 0
        aptitude=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca /var/log/aptitude)
        else
        echo "87" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  aptitude.log not found, skipping..." 6 60 0
        fi
        if [ -e /var/log/dpkg.log ]; then
        echo "94" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  dpkg.log, this one might take a while! " 6 60 0
        dpkg=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca /var/log/dpkg.log)
        else
        echo "94" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  dpkg.log not found, skipping" 6 60 0
        fi
        if [ -e /var/log/messages ]; then
        echo "100" | dialog --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  messages.log, this one might take a while! " 6 60 0
        messages=$(pastebinit -a xci -f bash -b http://xbmc-installer.pastebin.ca /var/log/messages)
        else
        echo "100" | dialog --sleep 1 --colors --title "\Z1[ UPLOADING LOGS ]\Zn" --gauge "  messages.log not found, skipping" 6 60 0
        fi

        rm -f ~/setup/Support.txt &>/dev/null
        touch ~/setup/Support.txt &>/dev/null
        echo "xci-installer.log = $installer" >~/setup/Support.txt
        echo "xci-video-change.log = $videochangeinstaller" >>~/setup/Support.txt
        echo "xci-sound.log = $soundinstaller" >>~/setup/Support.txt
        echo "xci-remote.log = $remoteinstaller" >>~/setup/Support.txt
        echo "xci-temp.log = $tempinstaller" >>~/setup/Support.txt
        echo "xci-bluetooth.log = $bluetooth" >>~/setup/Support.txt
        echo "xci-bootscreen.log = $bootscreeninstaller" >>~/setup/Support.txt
        echo "xci-svn-ppa-setup.log = $svnppainstaller" >>~/setup/Support.txt
        echo "xci-bluray-playback.log = $blurayplaybackinstaller" >>~/setup/Support.txt
        echo "xci-svn-build.log = $svnbuildinstaller" >>~/setup/Support.txt
        echo "xci-svn-update.log = $svnupdateinstaller" >>~/setup/Support.txt
        echo "xci-system-update.log = $systempupdateinstaller" >>~/setup/Support.txt
        echo "xci-system-upgrade.log = $systemupgradeinstaller" >>~/setup/Support.txt
        echo "xci-debug.log = $xbmcdebug" >>~/setup/Support.txt
        echo "aptitude.log = $aptitude" >>~/setup/Support.txt
        echo "dpkg.log = $dpkg" >>~/setup/Support.txt
        echo "messages.log = $messages" >>~/setup/Support.txt
        echo "xci-addons.log = $addons" >>~/setup/Support.txt
        
        dialog --colors --title "\Z1[ INFORMATION ]\Zn" --msgbox " \nYour logs have been uploaded to\n\Z4http://xbmc-installer.pastebin.ca\Zn\n\nPlease post the contents \Z1(copy and paste)\Zn of the next screen into XBMC-Installer Thread for support help! " 11 57
        clear
        cat ~/setup/Support.txt 
        echo
        echo -e '\E[1;32m\033[1mPress any key to continue!\033[0m'
        read -n1 any_key
    fi
}

function Addons_Menu(){
    while true
    do
    soundchoice=""
    dialog  --clear  --cancel-label "Go Back" --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" \
            --colors --title "\Z4[ SOFTWARE ADD-ONS ]\Zn" \
            --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 14 50 4 \
            1 "Sabnzbd+ Client" \
        2 "Vsftpd FTP Server" 2>/tmp/xci/addonsmenu
    case $? in
      0)
        addonsmenuitem=$(</tmp/xci/addonsmenu)
        case $addonsmenuitem in
            1) addons=install_sabnzbd;;
            2) addons=install_vsftpd;;
        esac;;
      1)
            break;;
      255)
            break;;
    esac

    if [ "$addons" = "install_sabnzbd" ]; then
        echo "0" | dialog --colors --title "\Z1[ INSTALLING Sabnzbd+ ]\Zn" --gauge "  Please wait..." 6 70 0
        aptitude update &>> ~/setup/logs/xci-addons.log
        echo "35" | dialog --colors --title "\Z1[ INSTALLING Sabnzbd+ ]\Zn" --gauge "  Please wait..." 6 70 0
        sudo aptitude --with-recommends install sabnzbdplus -y -q &>> ~/setup/logs/xci-addons.log
        echo "80" | dialog --colors --title "\Z1[ INSTALLING Sabnzbd+ ]\Zn" --gauge "  Configuring Sabnzbd+, Please wait..." 6 70 0
        sed -i '/USER=/d' /etc/default/sabnzbdplus
        sed -i '12i\USER=xbmc' /etc/default/sabnzbdplus
        sed -i '/HOST=/d' /etc/default/sabnzbdplus
        sed -i '20i\HOST=0.0.0.0' /etc/default/sabnzbdplus
        sed -i '/PORT=/d' /etc/default/sabnzbdplus
        sed -i '21i\HOST=9000' /etc/default/sabnzbdplus
        dialog  --clear --colors --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --title "\Z4[ INSTALL SUMMARY ]\Zn" --msgbox "\nYou can access the SABnzbplus webpage on \Z1http://$(ifconfig  | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'):9000\Zn in any web browser." 9 45
        echo "100" | dialog --sleep 1 --colors --title "\Z1[ INSTALLED Sabnzbd+ ]\Zn" --gauge "  Sabnzbd+ will restart now" 6 70 0
        /etc/init.d/sabnzbdplus restart &>> ~/setup/logs/xci-addons.log

    elif [ "$addons" = "install_vsftpd" ]; then
        echo "0" | dialog --colors --title "\Z1[ INSTALLING Vsftpd FTP Server ]\Zn" --gauge "  Please wait..." 6 70 0
        aptitude install vsftpd -y &>> ~/setup/logs/xci-addons.log
        echo "10" | dialog --colors --title "\Z1[ INSTALLING Vsftpd FTP Server ]\Zn" --gauge "  Please wait..." 6 70 0
        cp /etc/vsftpd.conf /etc/vsftpd.conf-backup; rm -f /etc/vsftpd.conf; touch /etc/vsftpd.conf  &>> ~/setup/logs/xci-addons.log
        echo "15" | dialog --colors --title "\Z1[ INSTALLING Vsftpd FTP Server ]\Zn" --gauge "  Configuring Vsftpd, Please wait..." 6 70 0
        echo 'listen=YES' >> /etc/vsftpd.conf
        echo 'pasv_min_port=49152' >> /etc/vsftpd.conf
        echo 'pasv_max_port=65535' >> /etc/vsftpd.conf
        echo 'pasv_promiscuous=YES' >> /etc/vsftpd.conf
        echo 'local_max_rate=0' >> /etc/vsftpd.conf
        echo 'local_enable=YES' >> /etc/vsftpd.conf
        echo 'write_enable=YES' >> /etc/vsftpd.conf
        echo 'local_umask=077' >> /etc/vsftpd.conf
        echo 'dirmessage_enable=YES' >> /etc/vsftpd.conf
        echo 'use_localtime=YES' >> /etc/vsftpd.conf
        echo 'xferlog_enable=YES' >> /etc/vsftpd.conf
        echo 'connect_from_port_20=YES' >> /etc/vsftpd.conf
        echo 'port_enable=NO' >> /etc/vsftpd.conf
        echo 'chown_uploads=YES' >> /etc/vsftpd.conf
        echo 'chown_username=xbmc' >> /etc/vsftpd.conf
        echo 'ftpd_banner=Welcome to XBMC FTP Server' >> /etc/vsftpd.conf
        echo 'chroot_local_user=NO' >> /etc/vsftpd.conf
        echo 'secure_chroot_dir=/var/run/vsftpd/empty' >> /etc/vsftpd.conf
        echo 'pam_service_name=vsftpd' >> /etc/vsftpd.conf
        echo 'rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem' >> /etc/vsftpd.conf
        echo 'async_abor_enable=YES' >> /etc/vsftpd.conf
        echo 'anon_mkdir_write_enable=NO' >> /etc/vsftpd.conf
        echo 'anon_other_write_enable=NO' >> /etc/vsftpd.conf
        echo 'force_dot_files=YES' >> /etc/vsftpd.conf
        echo 'tcp_wrappers=YES' >> /etc/vsftpd.conf
        echo 'cmds_allowed=ABOR,APPE,CWD,DELE,HELP,LIST,MDTM,MKD,NLST,PASS,PASV,PWD,QUIT,RETR,RMD,RNFR,RNTO,SIZE,STOR,TYPE,USER' >> /etc/vsftpd.conf
        echo 'xferlog_file=/root/setup/log/xferlog' >> /etc/vsftpd.conf
        echo 'vsftpd_log_file=/root/setup/log/vsftpd.log' >> /etc/vsftpd.conf
        dialog  --clear --colors --backtitle "XBMC LIVE SETUP FOR $CUR_KER Ver: $VERSION" --title "\Z4[ INSTALL SUMMARY ]\Zn" --msgbox "\nYou can access the Vsftpd on \Z1http://$(ifconfig  | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'):21\Zn Username is xbmc and whatever your paswword is." 9 45
        echo "100" | dialog --sleep 1 --colors --title "\Z1[ INSTALLED Vsftpd ]\Zn" --gauge "  Vsftpd will restart now" 6 70 0
        /etc/init.d/vsftpd restart &>> ~/setup/logs/xci-addons.log
    fi
    done
}

while true
do
### display main menu ###
dialog  --clear --help-button --help-label "License" --cancel-label "Exit" --backtitle "XBMC LIVE SETUP FOR $(uname -a | awk '{print $1,$3,$12}') - Ver: $VERSION" \
        --colors --title "\Z4[ MAIN - MENU ]\Zn" \
        --menu "\n You can use the UP/DOWN arrow keys,\n the No. of the choice as a hot key,\n to choose an option.\n\n Please choose an item:" 20 45 10 \
        1 "Install XBMC-Live 9.11" \
        2 "Hardware Setup Options" \
        3 "Backup/Restore" \
        4 "XBMC Setup Options" \
        5 "Software Add-ons" \
        6 "System Update" \
        7 "Full System Upgrade" \
        L "Upload Install Logs" 2>/tmp/xci/mainmenu
 
    case $? in
      0)
        mainmenuitem=$(</tmp/xci/mainmenu)
        case $mainmenuitem in
            1) Main_Install;;
            2) Hardware_Menu;;
            3) Backup_Restore_Menu;;
            4) XBMC_Options_Menu;;
            5) Addons_Menu;;
            6) System_Update;;
            7) System_Upgrade;;
            L) Support;;
        esac;;
    1)
        clear; echo -e '\E[1;32mHope you enjoyed using XBMC Complete Installer, bye!'; sleep 1; reset; break;;
    2)
        dialog --colors --title "\Z4[ XCI GPL LICENSE ]\Zn" --textbox ~/XCI_License.GPL 22 76;;
    esac
done

## If temp files found, delete em
rm -fr /tmp/xci &>/dev/null
```[/LEFT]

---

### Post by X3lectric on 2010-07-13
bump

---

### Post by X3lectric on 2010-07-14
bump

please anyone?

---

### Post by sinnadyr on 2010-07-28
I sure wish people would respond to this thread... Having a problem where my nvidia-drivers wont work with your script, if people would have helped you with this it could have been the most awesome ever! (next to xbmc ofcource;))

---

### Post by X3lectric on 2010-07-28
If you have** full desktop it wont work ever this script is meant for minimal kamic install** and I made sure all drivers and script work to date. all tested and triple tested.

It results in flawless install and config any bugs are down to xbmc atm. 

and this is not a support thread either. see my sig

---

