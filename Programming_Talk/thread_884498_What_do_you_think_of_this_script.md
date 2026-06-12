---
title: "What do you think of this script ???"
date: 2008-08-09
forum: Programming Talk
---

### Post by HunterThomson on 2008-08-09
What do you think of this script or the one attached for use with any computer???


```
#!/bin/bash
#
# Shell script to make a USB Tumb Drive for Flashing BIOS on a Lenovo Ideapad Y510. This script needs to me owned and run as ROOT with the "sudo command"
# i.e.  sudo usbbiosflasher
# 
# Name this script usbbiosflasher and save it to the ~/home directory.
# Then run the command-  chown root:root usbbiosflasher
# Then run the command-  chmod 755 usbbiosflasher
# Then copy the script to the directory /usr/bin.
# Run this comand to do that- sudo cp ~/usbbiosflasher /usr/bin  
#
# Download the FreeDOS.gz and the 06CN29WW.ROM files and save them to your /home directory
# You can get the FreeDOS.gz file fome this link
# [http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz](http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz)
# You can get the 06CN29WW.ROM file from this link
# [http://ubuntuforums.org/attachment.p...0&d=1216648756](http://ubuntuforums.org/attachment.p...0&d=1216648756)
# 
# You also must have the program "mbr" installed
# You can install the mbr program by running this comand in the shell on Ubuntu
# sudo apt-get install mbr
# In Arch Linux you have to get it from Aur
#
# First you will need to know a few things...
#
# You will also need to know the Mount Point i.e. /media/disk.
# You can find these by using the df -T comand. 
# Run   df -T  in the shell. Then plug in the USB Thumb Drive and run the  df -T  comand agin.
# The new listing is the USB Thumb Dirve.
# Also check to make sure the File System tipe is vFAT or FAT16 or FAT32. 
# If it is not use gparted to format it to FAT32.
# I am farly certen that all USB Thumb drive come formated with FAT file system out of the BOX.
# You may want to fromat it anyway just to make sure.
#
#

# The next comand will make a directory for you to put the .ROM file and the FreeDOS files into.
mkdir ~/usbbiosfiles

echo "Interactive Shell Script to Make a USB Thumb Drive for Flashing BIOS On a Lenovo Ideapad Y510"
echo ""
echo "This program made the directory ~/usbbiosfiles for you to put needed files into"
echo ""
echo "First you will need to know a few things and download the new BIOS .ROM file and a vertion of FreeDOS..."
echo ""
echo "Download the BIOS .ROM file by copying the URL below into your Web Broser. Make sure to save it to the ~/usbbiosfiles directory."
echo ""
echo "http://ubuntuforums.org/attachment.php?attachmentid=78460&d=1216648756"
echo ""
echo "This BIOS .ROM file is up to date as of Aug 8th 2008 if there is a new BIOS Vertion out or if you don't have a Y510 you can just copy the .ROM file you need to use to the same direcotry it use it instead. The script will still work as long as the .ROM file is compressed as a .tar.bz2."
echo ""
echo "Download the FreeDOS OS we need form the link below. Make sure to save it to the ~/usbbiosfiles directory"
echo ""
echo "http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz"
echo ""
echo "You will need to know the Mount Point of the USB Drive i.e. /media/xxx. You will also need to make sure the File System type is vFAT, FAT16 or FAT32. With the USB Thumb Drive unpluged, Open another shell and run the comand  df -T  Then plug in the USB Thumb Drive and run the comand df -T one more time. The new device listed is the USB Thumb Drive. Note the Mount Point (i.e. /media/xxx) and the File system Type (i.e. vFAT)... If the File System type is not vFAT, FAT16 or FAT32 you will need to fromat it with gparted. You may want to format the USB Thumb Drive anyway just to make sure. In any case delete all files and directorys on the USB drive before you go any ferther with this program."

# The next two comands set the variables. DEVX for the path /dev/xxx and MOUNTX for the mount point /media/xxx
# printf "What is the path the USB Thumb Drive is mounted on i.e. /dev/sdb1?"
# read DEVX
printf "After completeing the instructions above...Enter the Mount Point of the USB Thumb Drive i.e. /media/xxx?"
read MOUNTX

install-mbr --enable A1 --partition 1 --force --timeout 0 $MOUNTX && tar xjvf ~/usbbiosfiles/*.tar.bz2 && gunzip ~/usbbiosfiles/FDOEM.144.gz && mkdir ~/usbbiosfiles/fdoem144 && modprobe loop && mount -o loop FDOEM.144 ~/usbbiosfiles/fdoem144 && cp ~/usbbiosfiles/fdoem144/* $MOUNTX && cp ~/usbbiosfiles/*.ROM $MOUNTX && sync && umount ~/usbbiosfiles/fdoem144

echo "Success :) You made a USB Thumb Drive that you can update your BIOS with"
echo ""
echo "Write down these instructions"
echo "Now leave the USB Thumb Drive pluged into your computer and Reboot. When the Lenovo Logo POST screen appears hit F2 to enter the CMOS setup utility. Go over to BOOT tab and go down to HardDrive (Not Boot Order) then select the USB Thumb Drive as the 1st hard drve. Then F10 and yes to save changes. Your compter will reboot agin. Then when the Lenovo Logo POST Screen appers on reboot hit F4 to enter the BIOS FLASHING program. The USB Thumb Drive will be seen as the C: drive in the list on the Left, Select it. Then select the .ROM file in the list on the Right and start the BIOS FLASH. (NOTE: Your hart may stop beating... This is normal) Pray to any God you know of and your computer should restart just like normal. Hit F2 and the BIOS will now stay it is 06CN29WW. You will need to set the boot order to the way you like it and other things if you need to because they have been changed to the default."
```

---

### Post by ghostdog74 on 2008-08-09
you can make it such that the script automatically downloads the necessary libraries/software that it uses and save the user the trouble.

---

### Post by HunterThomson on 2008-08-09
I am trying to use wget to download the .ROM file and FreeDOS but I just can't get it to folow the link....:confused:

---

### Post by ghostdog74 on 2008-08-09
> **HunterThomson said:**
> I am trying to use wget to download the .ROM file and FreeDOS but I just can't get it to folow the link....:confused:

how are you calling it. show it.

---

### Post by HunterThomson on 2008-08-09
> **ghostdog74 said:**
> how are you calling it. show it.

I try it in ways like this...

wget -r -l5 -np [http://ubuntuforums.org/attachment.php?attachmentid=78460&d=1216648756](http://ubuntuforums.org/attachment.php?attachmentid=78460&d=1216648756)

or 

wget -r -l5 -np -A.BIN -R.html [http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz](http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz)

---

### Post by ghostdog74 on 2008-08-09
what is wrong with
```

wget  http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz

```?

---

### Post by HunterThomson on 2008-08-09
> **ghostdog74 said:**
> what is wrong with
```

wget  http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz

```?

](*,)

I knew I was doing something stupid... Thankyou
I will post the new script after adding that in...

```
wget http://ubuntuforums.org/attachment.php?attachmentid=78460&d=1216648756
```

Dosn't work though.... It just donloads this file "attachment.php?attachmentid=78460"

How do I get it to download the real file???

---

### Post by HunterThomson on 2008-08-09
```
#!/bin/bash
#
# Shell script to make a USB Tumb Drive for Flashing BIOS on a Lenovo Ideapad Y510. This script needs to me owned and run as ROOT with the "sudo command"
# i.e.  sudo usbbiosflasher
# 
# Name this script usbbiosflasher and save it to the ~/home directory.
# Then run the command-  chown root:root usbbiosflasher
# Then run the command-  chmod 755 usbbiosflasher
# Then copy the script to the directory /usr/bin.
# Run this comand to do that- sudo cp ~/usbbiosflasher /usr/bin  
#
# Download the 06CN29WW.ROM file and save it to the ~/usbbiosfiles directory the script makes when prompted.
# You can get the 06CN29WW.ROM file from this link
# [http://ubuntuforums.org/attachment.p...0&d=1216648756](http://ubuntuforums.org/attachment.p...0&d=1216648756)
# 
# You also must have the program "mbr" installed
# You can install the mbr program by running this comand in the shell on Ubuntu
# sudo apt-get install mbr
# In Arch Linux you have to get it from Aur
#
# First you will need to know a few things...
#
# You will also need to know the Mount Point i.e. /media/disk.
# You can find these by using the df -T comand. 
# Run   df -T  in the shell. Then plug in the USB Thumb Drive and run the  df -T  comand agin.
# The new listing is the USB Thumb Dirve.
# Also check to make sure the File System tipe is vFAT or FAT16 or FAT32. 
# If it is not use gparted to format it to FAT32.
# I am farly certen that all USB Thumb drive come formated with FAT file system out of the BOX.
# You may want to fromat it anyway just to make sure.
#
#

# The next comand will make a directory for you to put the .ROM file and the FreeDOS files into.
mkdir ~/usbbiosfiles

echo "Interactive Shell Script to Make a USB Thumb Drive for Flashing BIOS On a Lenovo Ideapad Y510"
echo ""
echo "This program made the directory ~/usbbiosfiles for you to put needed files into"
echo ""

printf "What is your username?"
read NAMEX

chown $NAMEX ~/usbbiosfiles

echo ""
echo "First you will need to know a few things and download the new BIOS .ROM file..."
echo ""
echo "Download the BIOS .ROM file by copying the URL below into your Web Broser. Make sure to save it to the ~/usbbiosfiles directory."
echo ""
echo "http://ubuntuforums.org/attachment.php?attachmentid=78460&d=1216648756"
echo ""
echo "This BIOS .ROM file is up to date as of Aug 8th 2008 if there is a new BIOS Vertion out or if you don't have a Y510 you can just copy the .ROM file you need to use to the same direcotry it use it instead. The script will still work as long as the .ROM file is compressed as a .tar.bz2."
echo ""

printf "Hit the Enter key after you have done that"
read WAIT

# echo "Download the FreeDOS OS we need form the link below. Make sure to save it to the ~/usbbiosfiles directory"
# echo ""
# echo "http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz"
# echo ""

cd ~/usbbiosfiles
wget  [http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz](http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz)

echo "You will need to know the Mount Point i.e. /media/disk and the /dev Path i.e. /dev/sdb1. You will also need to make sure the File System type is vFAT, FAT16 or FAT32. With the USB Thumb Drive unpluged, Open another shell and run the comand  df -T  Then plug in the USB Thumb Drive and run the comand df -T one more time. The new device listed is the USB Thumb Drive. Note the Mount Point (i.e. /media/disk) The /dev Path (i.e. /dev/sdb1) and the File system Type (i.e. vFAT)... If the File System type is not vFAT, FAT16 or FAT32 you will need to fromat it with gparted. You may want to format the USB Thumb Drive anyway just to make sure. In any case delete all files and directorys on the USB drive before you go any ferther with this program."

# The next two comands set the variables. DEVX for the path /dev/xxx and MOUNTX for the mount point /media/xxx

printf "Enter the path the USB Thumb Drive is mounted on i.e. /dev/sdb1?"
read DEVX
printf "What is the Mount Point of the USB Thumb Drive i.e. /media/disk?"
read MOUNTX

install-mbr --enable A1 --partition 1 --force --timeout 0 $DEVX && cd ~/usbbiosfiles && tar xjvf ~/usbbiosfiles/*.tar.bz2 && gunzip ~/usbbiosfiles/FDOEM.144.gz && mkdir ~/usbbiosfiles/fdoem144 && modprobe loop && mount -o loop ~/usbbiosfiles/FDOEM.144 ~/usbbiosfiles/fdoem144 && cp ~/usbbiosfiles/fdoem144/* $MOUNTX && cp ~/usbbiosfiles/*.ROM $MOUNTX && sync && umount ~/usbbiosfiles/fdoem144

echo "If you see no errors then...Success :) You made a USB Thumb Drive that you can update your BIOS with"
echo ""
echo "Write down these instructions"
echo "Now leave the USB Thumb Drive pluged into your computer and Reboot. When the Lenovo Logo POST screen appears hit F2 to enter the CMOS setup utility. Go over to BOOT tab and go down to HardDrive (Not Boot Order) then select the USB Thumb Drive as the 1st hard drve. Then F10 and yes to save changes. Your compter will reboot agin. Then when the Lenovo Logo POST Screen appers on reboot hit F4 to enter the BIOS FLASHING program. The USB Thumb Drive will be seen as the C: drive in the list on the Left, Select it. Then select the .ROM file in the list on the Right and start the BIOS FLASH. (NOTE: Your hart may stop beating... This is normal) Pray to any God you know of and your computer should restart just like normal. Hit F2 and the BIOS will now stay it is 06CN29WW. You will need to set the boot order to the way you like it and other things if you need to because they have been changed to the default."
```

---

### Post by ghostdog74 on 2008-08-09
> **HunterThomson said:**
> ](*,)

I knew I was doing something stupid... Thankyou
I will post the new script after adding that in...

```
wget http://ubuntuforums.org/attachment.php?attachmentid=78460&d=1216648756
```

Dosn't work though.... It just donloads this file "attachment.php?attachmentid=78460"

How do I get it to download the real file???

just rename it.

---

### Post by HunterThomson on 2008-08-09
> **ghostdog74 said:**
> just rename it.

Owe so the "attachment" file is the .ROM file? 

Owe... It is.... both have the same file size at lest... 565.6kB.

So check out the script now. I am going to add some error checking stuff next....

```
#!/bin/bash
#
# Shell script to make a USB Tumb Drive for Flashing BIOS on a Lenovo Ideapad Y510. This script needs to me owned and run as ROOT with the "sudo command"
# i.e.  sudo usbbiosflasher
# 
# Name/Rename this script usbbiosflasher and save it to the ~/home directory.
# Then run the command-  chown root:root usbbiosflasher
# Then run the command-  chmod 755 usbbiosflasher
# Then copy the script to the directory /usr/bin.
# Run this comand to do that- sudo cp ~/usbbiosflasher /usr/bin  
#
# You also must have the program "mbr" installed
# You can install the mbr program by running this comand in the shell on Ubuntu
# sudo apt-get install mbr
# In Arch Linux you have to get it from Aur
#
# First you will need to know a few things...
#
# You will also need to know the Mount Point i.e. /media/disk and the /dev path i.e. /dev/sdb1.
# You can find these by using the df -T comand. 
# Run   df -T  in the shell. Then plug in the USB Thumb Drive and run the  df -T  comand agin.
# The new listing is the USB Thumb Dirve.
# Also check to make sure the File System tipe is vFAT or FAT16 or FAT32. 
# If it is not use gparted to format it to FAT32.
# I am farly certen that all USB Thumb drive come formated with FAT file system out of the BOX.
# You may want to fromat it anyway just to make sure.
#
#

# The next comand will make a directory for you to put needed files into.
mkdir ~/usbbiosfiles

echo "Interactive Shell Script to Make a USB Thumb Drive for Flashing BIOS On a Lenovo Ideapad Y510"
echo ""
echo "You will need to have the program   mbr   installed"
echo "If you are on Ubuntu Linux you can retreve it form the repositories"
echo "If you are on Arch Linux you will need to get it from the Aur repositories"
echo "Open anuther shell and do that now..."
echo ""
printf "Hit Enter after you have done that"
read WAIT1

echo ""
echo "This program made the directory ~/usbbiosfiles to put needed files into"
echo ""

printf "What is your username?"
read NAMEX

chown $NAMEX ~/usbbiosfiles

#echo ""
# echo "You will need to download the new BIOS .ROM file..."
# echo ""
# echo "Download the BIOS .ROM file by copying the URL below into your Web Broser. Make sure to save it to the ~/usbbiosfiles directory."
# echo ""
# echo "http://ubuntuforums.org/attachment.php?attachmentid=78460&d=1216648756"
# echo ""
# echo "This BIOS .ROM file is up to date as of Aug 8th 2008 if there is a new BIOS Vertion out or if you don't have a Y510 you can just copy the .ROM file you need to use to the same direcotry it use it instead. The script will still work as long as the .ROM file is compressed as a .tar.bz2."
# echo ""

# printf "Hit the Enter key after you have done that"
# read WAIT2

# echo "Download the FreeDOS OS we need form the link below. Make sure to save it to the ~/usbbiosfiles directory"
# echo ""
# echo "http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz"
# echo ""

# The next two comands will get the FreeDOS file and the .ROM file.
cd ~/usbbiosfiles
wget  http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz

cd ~/usbbiosfiles
wget http://ubuntuforums.org/attachment.php?attachmentid=78460&d=1216648756

# The next comand will name the .ROM file to the corecct name.
mv ~/usbbiosfiles/attachment.php?attachmentid=78460 ~/usbbiosfiles/06CN29WW.bios.update.tar.bz2


echo ""
echo "You will need to know the Mount Point i.e. /media/disk and the /dev Path i.e. /dev/sdb1. You will also need to make sure the File System type is vFAT, FAT16 or FAT32. With the USB Thumb Drive unpluged, Open another shell and run the comand  df -T  Then plug in the USB Thumb Drive and run the comand df -T one more time. The new device listed is the USB Thumb Drive. Note the Mount Point (i.e. /media/disk) The /dev Path (i.e. /dev/sdb1) and the File system Type (i.e. vFAT)... If the File System type is not vFAT, FAT16 or FAT32 you will need to fromat it with gparted. You may want to format the USB Thumb Drive anyway just to make sure. In any case delete all files and directorys on the USB drive before you go any ferther with this program."

# The next two comands set the variables. DEVX for the path /dev/xxx and MOUNTX for the mount point /media/xxx

printf "Enter the /dev path the USB Thumb Drive is mounted on i.e. /dev/sdb1?"
read DEVX
printf "What is the Mount Point of the USB Thumb Drive i.e. /media/disk?"
read MOUNTX

install-mbr --enable A1 --partition 1 --force --timeout 0 $DEVX && cd ~/usbbiosfiles && tar xjvf ~/usbbiosfiles/*.tar.bz2 && gunzip ~/usbbiosfiles/FDOEM.144.gz && mkdir ~/usbbiosfiles/fdoem144 && modprobe loop && mount -o loop ~/usbbiosfiles/FDOEM.144 ~/usbbiosfiles/fdoem144 && cp ~/usbbiosfiles/fdoem144/* $MOUNTX && cp ~/usbbiosfiles/*.ROM $MOUNTX && sync && umount ~/usbbiosfiles/fdoem144

echo "If you see no errors then...Success :) You made a USB Thumb Drive that you can update your BIOS with"
echo ""

printf "Hit Enter to continue"
read WAIT3

echo ""
echo "Go get a pen and paper to write down these instructions"

printf "Hit Enter after you have done that"
read WAIT4

echo "Now leave the USB Thumb Drive pluged into your computer and Reboot. When the Lenovo Logo POST screen appears hit F2 to enter the CMOS setup utility. Go over to BOOT tab and go down to HardDrive (Not Boot Order) then select the USB Thumb Drive as the 1st hard drve. Then F10 and yes to save changes. Your compter will reboot agin. Then when the Lenovo Logo POST Screen appers on reboot hit F4 to enter the BIOS FLASHING program. The USB Thumb Drive will be seen as the C: drive in the list on the Left, Select it. Then select the .ROM file in the list on the Right and start the BIOS FLASH. (NOTE: Your hart may stop beating... This is normal) Pray to any God you know of and your computer should restart just like normal. Hit F2 and the BIOS will now stay it is 06CN29WW. You will need to set the boot order to the way you like it and other things if you need to because they have been changed to the default."
```

---

### Post by geirha on 2008-08-09
```
wget http://ubuntuforums.org/attachment.php?attachmentid=78460&d=1216648756
```
This line is probably giving you some troubles. The & symbol is used in bash to send a process to the background, so that wget line is actually running two commands. 

```

wget http://ubuntuforums.org/attachment.php?attachmentid=78460 &
d=1216648756  

```
You probably don't intend to have a variable named d with a value of 1216648756. Make sure to quote the URLs you give wget, so the & will be treated as a regular character.
```

wget "http://ubuntuforums.org/attachment.php?attachmentid=78460&d=1216648756"

```

---

### Post by HunterThomson on 2008-08-09
Ya I am having a hell of a time with symbols and words used in bash trying to do other things when all I want to do is print something on the screen.... How do tell bash that not to do anyting about some symbol or word....

Here is snap shot of the script now...
```

#!/bin/bash
#
# Shell script to make a USB Tumb Drive for Flashing BIOS on a Lenovo Ideapad Y510. This script needs to me owned and run as ROOT with the "sudo command"
# i.e.  sudo usbbiosflasher
# 
# Name/Rename this script usbbiosflasher and save it to the ~/home directory.
# Then run the command-  chown root:root usbbiosflasher
# Then run the command-  chmod 755 usbbiosflasher
# Then copy the script to the directory /usr/bin.
# Run this comand to do that- sudo cp ~/usbbiosflasher /usr/bin  
#
# You also must have the program "mbr" installed
# You can install the mbr program by running this comand in the shell on Ubuntu
# sudo apt-get install mbr
# In Arch Linux you have to get it from Aur
#
# First you will need to know a few things...
#
# You will also need to know the Mount Point i.e. /media/disk and the /dev path i.e. /dev/sdb1.
# You can find these by using the df -T comand. 
# Run   df -T  in the shell. Then plug in the USB Thumb Drive and run the  df -T  comand agin.
# The new listing is the USB Thumb Dirve.
# Also check to make sure the File System tipe is vFAT or FAT16 or FAT32. 
# If it is not use gparted to format it to FAT32.
# I am farly certen that all USB Thumb drive come formated with FAT file system out of the BOX.
# You may want to fromat it anyway just to make sure.
#
#


# Seting up...
DEBUGQ= "would you like to exit now?(y/n)"

PART1= "You will need to know the Mount Point i.e. /media/disk and the /dev Path i.e. /dev/sdb1. You will also need to make sure the File System type is vFAT, FAT16 or FAT32. With the USB Thumb Drive unpluged, Open another shell and run the comand  df -T  Then plug in the USB Thumb Drive and run the comand df -T one more time. The new device listed is the USB Thumb Drive. Note the Mount Point (i.e. /media/disk) The /dev Path (i.e. /dev/sdb1) and the File system Type (i.e. vFAT)... If the File System type is not vFAT, FAT16 or FAT32 you will need to fromat it with gparted. You may want to format the USB Thumb Drive anyway just to make sure. In any case delete all files and directorys on the USB drive before you go any ferther with this program."

PART1Q= "Enter the /dev path the USB Thumb Drive is mounted on i.e. /dev/sdb1?"

PART2Q= "What is the Mount Point of the USB Thumb Drive i.e. /media/disk?"

PART3= "Now leave the USB Thumb Drive pluged into your computer and Reboot. When the Lenovo Logo POST screen appears hit F2 to enter the CMOS setup utility. Go over to BOOT tab and go down to HardDrive (Not Boot Order) then select the USB Thumb Drive as the 1st hard drve. Then F10 and yes to save changes. Your compter will reboot agin. Then when the Lenovo Logo POST Screen appers on reboot hit F4 to enter the BIOS FLASHING program. The USB Thumb Drive will be seen as the C: drive in the list on the Left, Select it. Then select the .ROM file in the list on the Right and start the BIOS FLASH. (NOTE: Your hart may stop beating... This is normal) Pray to any God you know of and your computer should restart just like normal. Hit F2 and the BIOS will now stay it is 06CN29WW. You will need to set the boot order to the way you like it and other things if you need to because they have been changed to the default."

echo "Interactive Shell Script to Make a USB Thumb Drive for Flashing BIOS On a Lenovo Ideapad Y510"
echo ""
echo "You will need to have the program   mbr   installed"
echo "If you are on Ubuntu Linux you can retreve it form the repositories"
echo "If you are on Arch Linux you will need to get it from the Aur repositories"
echo "Open anuther shell and do that now..."
echo ""

verify="n"
while [ "$verify" != y ]
do
    printf "Do you have mbr installed? (yes/no)"
    read AN1
    printf "You answered... $AN1 I have installed mbr. Is this correct? (y/n)"
    read verify
done

echo ""

if [ "$AN1" == "no" ]
then
    echo "Install mbr now. Then run this scrip agin"
    exit
else
    echo "contunuing script"
fi

echo ""

printf "$DEBUGQ"
read DEBUG

if [ "$DEBUG" == "y" ]
then
    echo "Ending program now"
    exit
fi

echo ""

# The next comand will make a directory for you to put needed files into.
mkdir ~/usbbiosfiles

# The next two comands will get the FreeDOS file and the .ROM file.
cd ~/usbbiosfiles
wget  http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz

cd ~/usbbiosfiles
wget http://ubuntuforums.org/attachment.php?attachmentid=78460&d=1216648756

# The next comand will name the .ROM file to the corecct name.
mv ~/usbbiosfiles/attachment.php?attachmentid=78460 ~/usbbiosfiles/06CN29WW.bios.update.tar.bz2

echo ""

# The next two comands set the variables. DEVX for the path /dev/xxx and MOUNTX for the mount point /media/xxx
verify="n"
while [ "$verify" != y ]
do
    echo "$PART1"
    printf "$PART1Q"
    read DEVX
    echo "You entered $DEVX.  Is this correct? y or n"
    read verify
done 

echo ""

printf "$DEBUGQ"
read DEBUG

if [ "$DEBUG" == "y" ]
then
    echo "Ending program now"
    exit
fi

verify="n"
while [ "$verify" != y ]
do
    printf "$PART2Q"
    read MOUNTX
    echo "You entered $MOUNTX.  Is this correct? y or n"
    read verify
done 

echo ""

printf "$DEBUGQ"
read DEBUG

if [ "$DEBUG" == "y" ]
then
    echo "Ending program now"
    exit
fi

install-mbr --enable A1 --partition 1 --force --timeout 0 $DEVX && cd ~/usbbiosfiles && tar xjvf ~/usbbiosfiles/*.tar.bz2 && gunzip ~/usbbiosfiles/FDOEM.144.gz && mkdir ~/usbbiosfiles/fdoem144 && modprobe loop && mount -o loop ~/usbbiosfiles/FDOEM.144 ~/usbbiosfiles/fdoem144 && cp ~/usbbiosfiles/fdoem144/* $MOUNTX && cp ~/usbbiosfiles/*.ROM $MOUNTX && sync && umount ~/usbbiosfiles/fdoem144

verify="n"
while [ "$verify" != y ]
do
    printf "Do you see any errors? yes or no"
    read AN2
    printf "You answered... $AN2 There are errors. Is this correct? y or n"
    read verify
done

echo ""

if [ "$AN2" == "yes" ]
then
    echo "removeing files... Reformat the USB Stick to FAT32 with gparted and fix the problem and run this script agin"
    rm -r ~/usbbiosfiles
    exit
else
    echo "Go get a pen and paper to write down these instructions"

printf "Then hit the Enter to continue"
read WAIT4

echo "$PART3"
fi
echo ""
echo "End of script"
```

---

### Post by geirha on 2008-08-09
> **HunterThomson said:**
> Ya I am having a hell of a time with symbols and words used in bash trying to do other things when all I want to do is print something on the screen.... How do tell bash that not to do anyting about some symbol or word....


You put quotes around it, either soft-quotes "" or hard-quotes ''. Or you escape it with a \.

The following two examples should both download the same file.
```
wget "http://ubuntuforums.org/attachment.php?attachmentid=78460&d=1216648756" # Quoted with soft-quotes
wget http://ubuntuforums.org/attachment.php?attachmentid=78460\&d=1216648756 # Escaped

```

Not sure if that will work for people that has not authenticated at the ubuntuforums though. I think you need to be authenticated to download attachments.

---

### Post by HunterThomson on 2008-08-09
> **geirha said:**
> You put quotes around it, either soft-quotes "" or hard-quotes ''. Or you escape it with a \.

The following two examples should both download the same file.
```
wget "http://ubuntuforums.org/attachment.php?attachmentid=78460&d=1216648756" # Quoted with soft-quotes
wget http://ubuntuforums.org/attachment.php?attachmentid=78460\&d=1216648756 # Escaped

```

Not sure if that will work for people that has not authenticated at the ubuntuforums though. I think you need to be authenticated to download attachments.


OK.... My testscrip is working with \ added and the "'s arount the wget "URL".

No I tried it... you don't need to be log into ubuntuforums first... That would have sucked...

---

### Post by HunterThomson on 2008-08-09
OK :)

It is all working now.... Here is a copy of the working script...

```
#!/bin/bash
#
# Shell script to make a USB Tumb Drive for Flashing BIOS on a Lenovo Ideapad Y510. 
# This script needs to me owned and run as ROOT with the "sudo command"
# i.e.  sudo usbbiosflasher
#
# If you have anyideas send me a PM on ubuntufourms.org  my user name is HunterThomson 
# Name/Rename this script usbbiosflasher and save it to the ~/home directory.
# Then run the command-  chown root:root usbbiosflasher
# Then run the command-  chmod 755 usbbiosflasher
# Then copy the script to the directory /usr/bin.
# Run this comand to do that- sudo cp ~/usbbiosflasher /usr/bin  
#
# You also must have the program "mbr" installed
# You can install the mbr program by running this comand in the shell on Ubuntu
# sudo apt-get install mbr
# In Arch Linux you have to get it from Aur
#
# First you will need to know a few things...
#
# You will also need to know the Mount Point i.e. /media/disk and the /dev path i.e. /dev/sdb1.
# You can find these by using the df -T comand. 
# Run   df -T  in the shell. Then plug in the USB Thumb Drive and run the  df -T  comand agin.
# The new listing is the USB Thumb Dirve.
# Also check to make sure the File System tipe is vFAT or FAT16 or FAT32. 
# If it is not use gparted to format it to FAT32.
# I am farly certen that all USB Thumb drives come formated with FAT file system out of the BOX.
# You may want to fromat it anyway just to make sure.
#
#
#
#

echo "Interactive Shell Script to Make a USB Thumb Drive \for Flashing BIOS On a Lenovo Ideapad Y510"
echo ""
echo "You will need to have the program   mbr   installed"
echo "If you are on Ubuntu Linux you can retreve it form the repositories"
echo "If you are on Arch Linux you will need to get it from the Aur repository"
echo "Open anuther shell and \do that now..."
echo ""

verify="n"
while [ "$verify" != y ]
do
    printf "Do you have mbr installed... yes or no?"
    read AN1
    echo ""
    printf "You answered... $AN1 I have installed mbr. Is this correct... y or n?"
    read verify
done

echo ""

if [ "$AN1" == "no" ]
then
    echo "Install mbr now. Then run this script agin"
    exit
else
    echo "contunuing script"
fi

echo ""

# The next comand will make a directory to put needed files into. Note this file and everything init will be owned by root.
mkdir ~/usbbiosfiles

# The next two comands will get the FreeDOS file and the .ROM file.
cd ~/usbbiosfiles
wget  http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz

cd ~/usbbiosfiles
wget "http://ubuntuforums.org/attachment.php?attachmentid=78460&d=1216648756"

# The next comand will name the .ROM file to the right name.
mv ~/usbbiosfiles/attachment.php?attachmentid=78460\&d=1216648756 ~/usbbiosfiles/06CN29WW.bios.update.tar.bz2

echo ""

# The next two comands set the variables. DEVX for the path i.e. /dev/xxx and MOUNTX for the mount point i.e. /media/xxx
verify="n"
while [ "$verify" != y ]
do
    echo "You will need to know the Mount Point and the dev Path. You will also need to \make sure the File System \type is vFAT, FAT16 or FAT32." 
    echo ""
    echo "With the USB Thumb Drive unpluged, Open another shell and run the comand  df -T  Then plug \in the USB Thumb Drive and run the comand df -T one \more time. The new device listed is the USB Thumb Drive. Note the Mount Point and The dev Path and the File system Type i.e. vFAT... If the File System \type is not vFAT, FAT16 or FAT32 you will need to fromat it with gparted. You may want to format the USB Thumb Drive anyway just to \make sure. In any \case delete all files and directorys on the USB drive before you go any ferther with this program."
    echo ""
    printf "Enter the dev path the USB Thumb Drive is at?"
    read DEVX
    echo ""
    echo "Are you sure $DEVX is the dev path of the USB Thumb Drive... y or n?"
    read verify
done 

echo ""

verify="n"
while [ "$verify" != y ]
do
    printf "What is the Mount Point of the USB Thumb Drive?"
    read MOUNTX
    echo ""
    echo "Are you sure $MOUNTX is the Mount Point of the USB Drive... y or n?"
    read verify
done 

echo ""

install-mbr --enable A1 --partition 1 --force --timeout 0 $DEVX && cd ~/usbbiosfiles && tar xjf ~/usbbiosfiles/*.tar.bz2 && gunzip ~/usbbiosfiles/FDOEM.144.gz && mkdir ~/usbbiosfiles/fdoem144 && modprobe loop && sleep 5 && mount -o loop ~/usbbiosfiles/FDOEM.144 ~/usbbiosfiles/fdoem144 && cp ~/usbbiosfiles/fdoem144/* $MOUNTX && cp ~/usbbiosfiles/*.ROM $MOUNTX && sync && umount ~/usbbiosfiles/fdoem144

verify="n"
while [ "$verify" != y ]
do
    printf "Do you see any errors... yes or no?"
    read AN2
    echo ""
    printf "You answered... $AN2 to errors. Is this correct... y or n?"
    read verify
done

echo ""

if [ "$AN2" == "yes" ]
then
    echo "removeing files... Reformat the USB Stick to FAT32 with gparted and fix the problem and run this script agin"
    rm -r ~/usbbiosfiles
    exit
else
    echo "Go get a pen and paper to write down these instructions"

printf "Then hit the Enter to continue"
read WAIT
echo ""
echo "Now leave the USB Thumb Drive pluged into your computer and Reboot. When the Lenovo Logo POST screen appears hit F2 to enter the CMOS setup utility. Go over to BOOT tab and go down to HardDrive \(Not Boot Order) \then \select the USB Thumb Drive as the 1st hard drve. Then F10 and yes to save changes. Your compter will reboot agin. Then when the Lenovo Logo POST Screen appers on reboot hit F4 to enter the BIOS FLASHING program. The USB Thumb Drive will be seen as the C drive \in the list on the Left, Select it. Then \select the .ROM \file \in the list on the Right and start the BIOS FLASH. \(NOTE Your hart may stop beating... This is normal) Pray to any God you know of and your computer should restart just like normal. Hit F2 and the BIOS will now stay it is 06CN29WW. You will need to \set the boot order to the way you like it and other things \if you need to because they have been changed to the default."
fi
echo ""
echo "End of script"
```

---

### Post by HunterThomson on 2008-08-10
OK :)
Now I have added some error checking :)

Do you know of a better way to check for errors or is this a good way to do it?

I just thought of a way to do it with commands that I know....

```
#!/bin/bash
#
# Shell script to make a USB Tumb Drive for Flashing BIOS on a Lenovo Ideapad Y510. 
# This script needs to me owned and run as ROOT with the "sudo command"
# i.e.  sudo usbbiosflasher
#
# If you have anyideas send me a PM on ubuntufourms.org  my user name is HunterThomson 
# Name/Rename this script usbbiosflasher and save it to the ~/home directory.
# Then run the command-  chown root:root usbbiosflasher
# Then run the command-  chmod 755 usbbiosflasher
# Then copy the script to the directory /usr/bin.
# Run this comand to do that- sudo cp ~/usbbiosflasher /usr/bin  
#
# You also must have the program "mbr" installed
# You can install the mbr program by running this comand in the shell on Ubuntu
# sudo apt-get install mbr
# In Arch Linux you have to get it from Aur
#
# First you will need to know a few things...
#
# You will also need to know the Mount Point i.e. /media/disk and the /dev path i.e. /dev/sdb1.
# You can find these by using the df -T comand. 
# Run   df -T  in the shell. Then plug in the USB Thumb Drive and run the  df -T  comand agin.
# The new listing is the USB Thumb Dirve.
# Also check to make sure the File System tipe is vFAT or FAT16 or FAT32. 
# If it is not use gparted to format it to FAT32.
# I am farly certen that all USB Thumb drives come formated with FAT file system out of the BOX.
# You may want to fromat it anyway just to make sure.
#
#
#
#

echo "Interactive Shell Script to Make a USB Thumb Drive \for Flashing BIOS On a Lenovo Ideapad Y510"
echo ""
echo "You will need to have the program   mbr   installed"
echo "If you are on Ubuntu Linux you can retreve it form the repositories"
echo "If you are on Arch Linux you will need to get it from the Aur repository"
echo "Open anuther shell and \do that now..."
echo ""

verify="n"
while [ "$verify" != y ]
do
    printf "Do you have mbr installed... yes or no?"
    read AN1
    echo ""
    printf "You answered... $AN1 I have installed mbr. Is this correct... y or n?"
    read verify
done

echo ""

if [ "$AN1" == "no" ]
then
    echo "Install mbr now. Then run this script agin"
    exit
else
    echo "contunuing script"
fi

echo ""

# The next comand will make a directory to put needed files into. Note this file and everything init will be owned by root.
mkdir ~/usbbiosfiles &&  check1="yes"

if [ "$check1" = "yes" ]
then
    echo "Made directory usbbiosfiles... OK"
else
    echo "Could not \make directory usbbiosfiles"
    echo "look above \for \info"
    echo "Fix the problem and run this scrip agin"
    exit
fi

# The next two comands will get the FreeDOS file and the .ROM file.
cd ~/usbbiosfiles && checka="yes"

if [ "$checka" = "yes" ]
then
    echo "Changing to the usbbiosfiles directory... OK"
else
    echo "Could not Change to the usbbiosfiles directory"
    echo "look above \for \info"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
fi


wget  "http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz" && check2="yes"

if [ "$check2" = "yes" ]
then
    echo "Download of FreeDOS... OK"
else
    echo "Could not Download FreeDOS"
    echo "look above \for \info"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
fi

wget "http://ubuntuforums.org/attachment.php?attachmentid=78460&d=1216648756" && check3="yes"

if [ "$check3" = "yes" ]
then
    echo "Download of the BIOS.ROM \file... OK"
else
    echo "Could not Downlad the BIOS.ROM \file"
    echo "look above \for \info"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
fi

# The next comand will name the .ROM file to the right name.
mv ~/usbbiosfiles/attachment.php?attachmentid=78460\&d=1216648756 ~/usbbiosfiles/06CN29WW.bios.update.tar.bz2 && check4="yes"

if [ "$check4" = "yes" ]
then
    echo "Renameing of the BIOS.ROM \file... OK"
else
    echo "Could not rename the BIOS.ROM \file"
    echo "look above \for \info"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
fi

echo ""

# The next two comands set the variables. DEVX for the path i.e. /dev/xxx and MOUNTX for the mount point i.e. /media/xxx
verify="n"
while [ "$verify" != y ]
do
    echo "You will need to know the Mount Point and the dev Path. You will also need to \make sure the File System \type is vFAT, FAT16 or FAT32." 
    echo ""
    echo "With the USB Thumb Drive unpluged, Open another shell and run the comand  df -T  Then plug \in the USB Thumb Drive and run the comand df -T one \more time. The new device listed is the USB Thumb Drive. Note the Mount Point and The dev Path and the File system Type i.e. vFAT... If the File System \type is not vFAT, FAT16 or FAT32 you will need to fromat it with gparted. You may want to format the USB Thumb Drive anyway just to \make sure. In any \case delete all files and directorys on the USB drive before you go any ferther with this program."
    echo ""
    printf "Enter the dev path the USB Thumb Drive is at?"
    read DEVX
    echo ""
    echo "Are you sure $DEVX is the dev path of the USB Thumb Drive... y or n?"
    read verify
done 

echo ""

verify="n"
while [ "$verify" != y ]
do
    printf "What is the Mount Point of the USB Thumb Drive?"
    read MOUNTX
    echo ""
    echo "Are you sure $MOUNTX is the Mount Point of the USB Drive... y or n?"
    read verify
done 

echo ""

install-mbr --enable A1 --partition 1 --force --timeout 0 $DEVX && check5="yes"

if [ "$check5" = "yes" ]
then
    echo "Installing MBR on USB Thumb Dirve... OK"
else
    echo "Could not install MBR on USB Thumb Drive"
    echo "look above \for \info"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
fi

tar xjf ~/usbbiosfiles/*.tar.bz2 && check7="yes"

if [ "$check7" = "yes" ]
then
    echo "Unpacking BIOS.ROM file... OK"
else
    echo "Could not unpack BIOS.ROM file"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
fi

gunzip ~/usbbiosfiles/FDOEM.144.gz && check8="yes"

if [ "$check8" = "yes" ]
then
    echo "Unpacking FreeDOS files... OK"
else
    echo "Could not unpack FreeDOS files"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
fi

mkdir ~/usbbiosfiles/fdoem144 && check9="yes"

if [ "$check9" = "yes" ]
then
    echo "Made directory fdoem144 in direcoty usbbiosfiles... OK"
    echo ""
    echo "Going to \sleep \for 5secs"
else
    echo "Could not make directory fdoem144 in usbbiosfiles directory"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
fi

modprobe loop && sleep 5 && check0="yes"

if [ "$check0" = "yes" ]
then
    echo "Modprobeing loop... OK"
else
    echo "Could not \modprobe loop"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
fi

mount -o loop ~/usbbiosfiles/FDOEM.144 ~/usbbiosfiles/fdoem144 && check10="yes"

if [ "$check10" = "yes" ]
then
    echo "Mounting FreeDOS on the fdoem144 directory... OK"
else
    echo "Could not \mount FreeDOS on the fdoem144 directory"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
fi

cp ~/usbbiosfiles/fdoem144/* $MOUNTX && check11="yes"

if [ "$check11" = "yes" ]
then
    echo "Copying FreeDOS files to $MOUNTX... OK"
else
    echo "Could not copy FreeDOS files to $MOUNTX"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
fi

cp ~/usbbiosfiles/*.ROM $MOUNTX && check12="yes"

if [ "$check12" = "yes" ]
then
    echo "Copying BIOS.ROM files to $MOUNTX... OK"
else
    echo "Could not copy BIOS.ROM files to $MOUNTX"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
fi

sync && check13="yes"

if [ "$check13" = "yes" ]
then
    echo "Runing the syncing command... OK"
else
    echo "Could not run the syncing command"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
fi

umount ~/usbbiosfiles/fdoem144 && check14="yes"

if [ "$check14" = "yes" ]
then
    echo "Unmounting of FreeDOS... OK"
else
    echo "Could not unmount FreeDOS"
    echo "Look above for errors or problems reported and fix the problem"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this script agin"
    rm -r ~/usbbiosfiles
    exit
fi

verify="n"
while [ "$verify" != y ]
do
    printf "Do you see any errors... yes or no?"
    read AN2
    echo ""
    printf "You answered... $AN2 to errors. Is this correct... y or n?"
    read verify
done

echo ""

if [ "$AN2" == "yes" ]
then
    echo "Prosses Check Repoted... Error"
    echo "Look above for errors or problems reported and fix the problem"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this script agin"
    rm -r ~/usbbiosfiles
    exit
else
    echo "Success"
    echo "I did a lot of error checking too and didnt find anything"
    echo ""
    echo "Go get a pen and paper to write down these instructions"

printf "Then hit the Enter to continue"
read WAIT
echo ""
echo "Now leave the USB Thumb Drive pluged into your computer and Reboot. When the Lenovo Logo POST screen appears hit F2 to enter the CMOS setup utility. Go over to BOOT tab and go down to HardDrive \(Not Boot Order) \then \select the USB Thumb Drive as the 1st hard drve. Then F10 and yes to save changes. Your compter will reboot agin. Then when the Lenovo Logo POST Screen appers on reboot hit F4 to enter the BIOS FLASHING program. The USB Thumb Drive will be seen as the C drive \in the list on the Left, Select it. Then \select the .ROM \file \in the list on the Right and start the BIOS FLASH. \(NOTE Your hart may stop beating... This is normal) Pray to any God you know of and your computer should restart just like normal. Hit F2 and the BIOS will now stay it is 06CN29WW. You will need to \set the boot order to the way you like it and other things \if you need to because they have been changed to the default."
fi
echo ""
echo "End of script"
```

---

