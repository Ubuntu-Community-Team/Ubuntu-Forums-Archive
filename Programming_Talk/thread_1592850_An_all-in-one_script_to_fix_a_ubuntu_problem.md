---
title: "An all-in-one script to fix a ubuntu problem"
date: 2010-10-11
forum: Programming Talk
---

### Post by linux18 on 2010-10-11
I haven't been in the forums in a while due to college classes, but I spent the last 5 hours on this 400 line shell script for use in case of some emergency situation ( the "AHH! I can't log in" type situation ) This script is like taking a chainsaw to a toothpick breaking competition or setting your house on fire to heat a cup of tea - effective, but overkill and possibly dangerous. I'm just in the final tweaking stages now and could use some input. Here is the script, it works on all architectures and flavors of ubuntu and id ten times longer than I originally expected it to be.

```
 #!/bin/bash
#
#
#       ubuntu emergency script
#       
#       Copyright 2010 seth <seth@seth-laptop>
#       
#       This program is free software; you can redistribute it and/or modify
#       it under the terms of the GNU General Public License as published by
#       the Free Software Foundation; either version 2 of the License, or
#       (at your option) any later version.
#       
#       This program is distributed in the hope that it will be useful,
#       but WITHOUT ANY WARRANTY; without even the implied warranty of
#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#       GNU General Public License for more details.
#       
#       You should have received a copy of the GNU General Public License
#       along with this program; if not, write to the Free Software
#       Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
#       MA 02110-1301, USA.



#------INTRO------#
NOW=$(date +"%b-%d-%y")
clear
cd /home/$USER/
echo "_____________Ubuntu Emergency Script________________"
echo
echo "So, you broke Ubuntu? No worries it's just software."
echo
echo "Even if it looks bad now, It can always be fixed!"
echo
echo  
echo "Lets get started..."
echo
echo "        1 - Fix synaptic issues"
echo "        2 - Free disk space"
echo "        3 - Purge orphaned libraries"
echo "        4 - Purge unused locales" 
echo "        5 - Backup home directory"
echo "        6 - Nuke all config files"
echo "        7 - Restore Desktop"
echo "        8 - Get output for forums"
echo
read -p "Enter a number: " MAIN_CHOICE
#------/INTRO-----#



#------OPTION 1------# 
if [ $MAIN_CHOICE = "1" ]
    then
    clear
    echo "Syaptic can be a hassle, but we do need to use it."
    echo "Here are my commands for repairing synaptic:"
    echo 
    echo "sudo killall synaptic; sudo killall aptitude; "
    echo "sudo killall software-center; sudo rm /var/lib/dpkg/lock; "
    echo "sudo rm /var/cache/apt/archives/lock; "
    echo "sudo rm /var/lib/apt/lists/partial/*; "
    echo "sudo rm /var/cache/apt/*.bin; sudo chmod 755 /usr/bin/dpkg; "
    echo "sudo dpkg --purge \$(dpkg -l |grep  ^rc |awk '{print $2}' | "
    echo "tr '\012' ' '); sudo aptitude clean; sudo apt-get autoclean; "
    echo "sudo apt-get update; sudo apt-get upgrade dpkg synaptic; "
    echo "sudo apt-get autoremove; sudo apt-get -f install; sudo "
    echo "aptitude -f install; sudo apt-get --fix-broken upgrade"
    echo
    read -p "Accept this solution(y/n)? " Y_N_DIALOGUE_A
    if [ $Y_N_DIALOGUE_A = "y" ]
        then
        sudo killall synaptic; sudo killall aptitude; sudo killall software-center; sudo rm /var/lib/dpkg/lock; \
        sudo rm /var/cache/apt/archives/lock; sudo rm /var/lib/apt/lists/partial/*; sudo rm /var/cache/apt/*.bin; \
        sudo chmod 755 /usr/bin/dpkg; sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' '); \
        sudo aptitude clean; sudo apt-get autoclean; sudo apt-get update; sudo sudo apt-get upgrade dpkg synaptic; \
        sudo apt-get autoremove; sudo apt-get -f install; sudo aptitude -f install; sudo apt-get --fix-broken upgrade
    fi
fi
#-------OPTION 1-----#



#------OPTION 2------#
if [ $MAIN_CHOICE = "2" ]
    then
    clear
    echo "Sometimes the disks get low on space, that's unfortunate."
    echo "Here are my commands for freeing up disk space:"
    echo
    echo "sudo rm -rf /usr/src/*; sudo rm /var/log/*.gz; "
    echo "sudo rm /var/log/*/*.gz; sudo rm \$(sudo du /var/log/* -h | "
    echo "grep "M"); sudo rm \$(sudo du /var/log/* -h | grep "G"); "
    echo "sudo aptitude clean; sudo apt-get autoremove; sudo apt-get "
    echo "autoclean; sudo rm -rf /root/.cache; sudo rm -rf /root\ "
    echo "/.thumbnails; sudo rm -rf /root/.local/share; sudo rm -rf "
    echo ".local/share; sudo rm -f .cache; sudo rm -rf .thumbnails "
    echo 
    read -p "Accept this solution(y/n)? " Y_N_DIALOGUE_B
    if [ $Y_N_DIALOGUE_B = "y" ]
        then
        sudo rm -rf /usr/src/*; sudo rm /var/log/*.gz; sudo rm /var/log/*/*.gz; \
        sudo rm $(sudo du /var/log/* -h | grep "M"); sudo rm $(sudo du /var/log/* -h | grep "G"); \
        sudo aptitude clean; sudo apt-get autoremove; sudo apt-get autoclean; sudo rm -rf /root/.cache; \
        sudo rm -rf /root/.thumbnails; sudo rm -rf /root/.local/share; sudo rm -rf .local/share; \
        sudo rm -rf .cache; sudo rm -rf .thumbnails
    fi
fi
#-------OPTION 2-----#



#------OPTION 3------#
if [ $MAIN_CHOICE = "3" ]
    then
    clear
    echo "Orphaned libraries take up space for nothing,"
    echo "and removing them is easy. Here are my commands"
    echo "for dealing with orphaned packages: "
    echo
    echo "sudo apt-get update; sudo apt-get install deborphan && "
    echo "for i in {1..5}; do sudo apt-get purge \$(deborphan); done"
    echo 
    read -p "Accept this solution(y/n)? " Y_N_DIALOGUE_C
    if [ $Y_N_DIALOGUE_C = "y" ]
        then
        sudo apt-get update; sudo apt-get install deborphan; for i in {1..5}; do \
        sudo apt-get purge $(deborphan); done
    fi
fi
#-------OPTION 3-----#



#------OPTION 4------#
if [ $MAIN_CHOICE = "4" ]
    then
    clear
    echo "Purging unused locales can save a lot of disk space."
    echo "Here are my commands for purging locales"
    echo 
    echo "sudo apt-get update; sudo apt-get install localepurge; "
    echo "sudo localepurge; locale-gen"
    echo
    read -p "Accept this solution(y/n)? " Y_N_DIALOGUE_D
    if [ $Y_N_DIALOGUE_D = "y" ]
        then
        sudo apt-get update; sudo apt-get install localepurge; sudo localepurge; sudo locale-gen
    fi
fi
#-------OPTION 4-----#



#------OPTION 5------#
if [ $MAIN_CHOICE = "5" ]
    then
    clear
    echo "Just can't seem to fix your installation? Oh well,"
    echo "reinstallation is easy enough. Here are your choices"
    echo "for backing up the system:"
    echo
    echo "        1 - Tarball     (.tar.bz2)"
    echo "        2 - lzma        (.tar.lzma)"
    echo "        3 - zip        (.zip)"
    echo "        4 - squashfs    (.squashfs)"
    echo
    read -p "Which method do you prefer: " COMPRESSION_METHOD
    if [ $COMPRESSION_METHOD = "1" ]
        then
        clear
        echo "A tarball is the most common way to store compressed"
        echo "data in *nix operating systems and is always a good"
        echo "choice. Almost every distro supports the format"
        echo 
        read -p "Tarball your home directory(y/n)? " Y_N_DIALOGUE_E
        if [ $Y_N_DIALOGUE_E = "y" ]
            then
            BACKUP_TITLE_A="BACKUP-$NOW-Tarball"
            mkdir $BACKUP_TITLE_A
            tar --bzip2 -c -p -S -v -f $BACKUP_TITLE_A.tar.bz2 /home/$USER/*
        fi
    fi
    if [ $COMPRESSION_METHOD = "2" ]
        then
        clear
        echo "lzma is for faster computers, it has great compression"
        echo "and great suppport and it's available by default in most"
        echo "distributions."
        echo
        read -p "lzma compress your home directory(y/n)? " Y_N_DIALOGUE_F
        if [ $Y_N_DIALOGUE_F = "y" ]
            then
            BACKUP_TITLE_B="BACKUP-$NOW-lzma"
            tar --lzma -c -p -S -v -f $BACKUP_TITLE_B.tar.lzma /home/$USER/*
        fi
    fi
    if [ $COMPRESSION_METHOD = "3" ]
        then
        clear
        echo "zip is a cross-platform solution for file backup and is"
        echo "supported by most linux distributions, windows and mac by"
        echo "default."
        echo
        read -p "zip your home directory(y/n)? " Y_N_DIALOGUE_G
        if [ $Y_N_DIALOGUE_G = "y" ]
            then
            BACKUP_TITLE_C="BACKUP-$NOW-zip"
            zip -v -X -r -T $BACKUP_TITLE_C /home/$USER/*
        fi
    fi
    if [ $COMPRESSION_METHOD = "4" ]
        then
        clear
        echo "Squashfs is a fast compression method for large directories"
        echo "its not a default utility, but is available in the repositories"
        echo "Squashfs may require an apt-get operation"
        echo
        read -p "squashfs your home directory(y/n)? " Y_N_DIALOGUE_H
        if [ $Y_N_DIALOGUE_H = "y" ]
            then
            sudo aptitude install squashfs-tools
            BACKUP_TITLE_D="BACKUP-$NOW-zip"
            mksquashfs Pictures /home/$USER/* $BACKUP_TITLE_D.squashfs -info
        fi
    fi
fi
#------OPTION 5------#
            
            
            
#------OPTION 6------#
if [ $MAIN_CHOICE = "6" ]
    then
    clear
    echo "When something is wrong with a file or program deleting the"
    echo "configuration file is a good idea. When many things fail at"
    echo "the same time, purging the current configuration may be a"
    echo "good idea, but it's more like using a nuke on one person."
    echo "this will delete your browser bookmarks, theme, locale"
    echo "settings, hidden files and more!"
    echo
    read -p "Purge all configuration files(y/n)? " Y_N_DIALOGUE_I
    if [ $Y_N_DIALOGUE_I = "y" ]
        then
        cd /home/$USER/    
        sudo rm -vrf .*
    fi
fi
#------OPTION 6------#



#------OPTION 7------#
if [ $MAIN_CHOICE = "7" ]
    then
    clear
    echo "Maybe purging configuration files isn't enough to fix the"
    echo "problem and your stuck without a GUI. If you tried purging the"
    echo "config files and fixing broken dependancies, this is one last"
    echo "thing that you can do before backing up and reinstalling."
    echo "Restoring the desktop takes time, and may require several"
    echo "hundred megabytes of packages to be downloaded. This will also"
    echo "delete your theme, hidden files, most settings, bookmarks and"
    echo "more! If you still want to, here are your desktop choices:"
    echo
    echo "            1 - Lubuntu"
    echo "            2 - Xubuntu"
    echo "            3 - Ubuntu"
    echo "            4 - Kubuntu"
    echo
    read -p "Which Desktop Environment do you have: " DESKTOP_ENVIRONMENT
    if [ $DESKTOP_ENVIRONMENT = "1" ]
        then
        cd /home/$USER/    
        sudo apt-get purge openbox pcmanfm lxpanel leafpad lxappearance lxinput lxsession-edit lxshortcut gpicview \
                           lxterminal lxmusic lxsession xscreensaver xfce4-taskmanager lxdm lxde*
        sudo dpkg-reconfigure -a                   
        sudo rm -vrf .config
        sudo rm -vrf /root/*
        sudo apt-get install lubuntu-desktop
        sudo aptitude -f install
        sudo reboot
    fi
    if [ $DESKTOP_ENVIRONMENT = "2" ]
        then
        cd /home/$USER/    
        sudo apt-get purge xfrun4 xfterm4 xflock4 xfmountdev4 xfbrowser4 startxfce4 xfhelp4 xfdesktop thunar mousepad \
                           xfwm4 xfce* xubuntu*
        sudo dpkg-reconfigure -a                   
        sudo rm -vrf .config
        sudo rm -vrf /root/*
        sudo apt-get install xubuntu-desktop
        sudo aptitude -f install
        sudo reboot
    fi
    if [ $DESKTOP_ENVIRONMENT = "3" ]
        then
        cd /
        sudo apt-get purge ubuntu*
        cd /home/$USER/
        sudo dpkg-reconfigure -a                   
        sudo rm -vrf .config
        sudo rm -vrf /root/*
        sudo apt-get install ubuntu-desktop
        sudo aptitude -f install
        sudo reboot
    fi    
    if    [ $DESKTOP_ENVIRONMENT = "4" ]
        then
        cd /home/$USER/
        sudo apt-get purge kwin kicker kscreensaver kubuntu* 
        sudo dpkg-reconfigure -a                   
        sudo rm -vrf .config
        sudo rm -vrf /root/*
        sudo apt-get install kbuntu-desktop
        sudo aptitude -f install
        sudo reboot
    fi    
fi
#------OPTION 7------#



#------OPTION 8------#
if [ $MAIN_CHOICE = "8" ]
    then
    clear
    echo "Need to post your problem in the Ubuntu Forums? You should be"
    echo "prepared! Posting relevent information will solve your problem"
    echo "faster and this script has a few options:"
    echo
    echo "            1 - video problem"
    echo "            2 - partition problem"
    echo "            3 - boot problem"
    echo
    read -p "What's your problem? " YOUR_PROBLEM
    if [ $YOUR_PROBLEM = "1" ]
        then
        OUTPUT_A="VIDEO-$NOW-Problem"
        touch $OUTPUT_A
        echo "Linux18's GPL'd UbuntuEmergencyScript video problem debugger Version 1" | tee $OUTPUT_A
        echo >> $OUTPUT_A
        echo "Gathering Data..."
        echo "uname -a:" >> $OUTPUT_A
        uname -a >> $OUTPUT_A
        echo >> $OUTPUT_A
        echo "lspci | grep 'VGA':" >> $OUTPUT_A
        lspci | grep "VGA" >> $OUTPUT_A
        echo >> $OUTPUT_A
        echo "cat xorg.conf:" >> $OUTPUT_A
        cat /etc/X11/xorg.conf >> $OUTPUT_A
        echo >> $OUTPUT_A
        echo "the rest of lspci:" >> $OUTPUT_A
        lspci >> $OUTPUT_A
        echo "DONE! your diagnostic information is in the file " $OUTPUT_A 
        read -p "Press any key to continue..." DUMMY_VALUE
    fi
    if [ $YOUR_PROBLEM = "2" ]
        then
        OUTPUT_B="PARTITION-$NOW-Problem"
        echo "Linux18's GPL'd UbuntuEmergencyScript partition problem debugger Version 1" | tee $OUTPUT_B
        echo >> $OUTPUT_B
        echo "Gathering Data..."
        echo "uname -a:" >> $OUTPUT_B
        uname -a >> $OUTPUT_B
        echo >> $OUTPUT_B
        echo "sudo parted -l:" >> $OUTPUT_B
        sudo parted -l | tee -a $OUTPUT_B
        echo >> $OUTPUT_B
        echo "df: " >> $OUTPUT_B
        df >> $OUTPUT_B
        echo "DONE! your diagnostic information is in the file " $OUTPUT_B
        read -p "Press any key to continue..." DUMMY_VALUE 
    fi
    if [ $YOUR_PROBLEM = "3" ]
        then
        OUTPUT_C="BOOT-$NOW-Problem"
        echo "Linux18's GPL'd UbuntuEmergencyScript boot problem debugger Version 1" | tee $OUTPUT_C
        echo >> $OUTPUT_C
        echo "Gathering Data..."
        echo "uname -a:" >> $OUTPUT_C
        uname -a >> $OUTPUT_C
        echo >> $OUTPUT_C
        echo "sudo parted -l:" >> $OUTPUT_C
        sudo parted -l | tee -a $OUTPUT_C
        echo >> $OUTPUT_C
        echo "cat /boot/grub/grub.cfg:" >> $OUTPUT_C
        cat /boot/grub/grub.cfg >> $OUTPUT_C
        echo "DONE! your diagnostic information is in the file " $OUTPUT_C 
        read -p "Press any key to continue..." DUMMY_VALUE
    fi
fi
#------OPTION 8------#



#------THE END------#
clear
echo "I hope you enjoyed the script!"
echo
read -p "Press any key to close this terminal" DUMMY_VALUE
exit
#------THE END------#
        
         
```The only extra things I want to include is lovinglinux's flash-aid shell script ( with his permission ) and that fancy boot up script by someone who's name eludes me at the moment. So, what do you think?

EDIT: I'm going to sleep, so dont expect a quick response from me

---

