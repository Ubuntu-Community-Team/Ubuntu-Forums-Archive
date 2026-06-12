---
title: "Bash scripts for imaging, restoring GPT laptop hard drives using usb external drive"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by pursuvant on 2013-05-17
Took delivery of a System 76 laptop last week with SSD partitioned GPT - first order of business was buiding scripts to backup and restore the laptop drive (imaging). Was not so easy, i found all the pieces from others, but still took time to build out & test working scripts. Output of bash script to image is three files (1) the image file of entire disk (compressed), (2) SGDISK utility based backup of the GPT Partition Table, and (3) Info text file listing GPT partition information for easy reference

Below is the script that performs imaging. If there is interest i will post the companion script for restoring as well. Hope this helps others new to linux, of course no warranty expressed or implied...

save bash script below to a file i.e "v2.gazp8.backp.image.sh"
========================
#!/bin/bash -ux

# 
# GPT DRIVE CREATE BACKUP IMAGE ON EXTERNAL USB DRIVE 

# External drive is mounted as "/media/gmill/COOLMAX", ntfs file system
# USB jumpdrive would work equally well, but needs formatted with a file system supporting large files
#
# Notes:
# boot from unbuntu live cd
# connect to internet
# update system date time to current time in the live ubuntu session
# do not mount any partitions on the drive that will be imaged
#
# Want to view progress during image? open a NEW terminal window, pgrep -l '^dd$'  to get the PID, then
# sudo watch -n 60 kill -USR1 <pid>
#
# Future enhancements - load pv and use it to visuallyreport progress during imaging...
# 

# Stamp all the operations with the same local timestamp...
NOW=$(date +"%Y%m%d.%H%M%S")

#Destination directory for this image on COOLMAX (must already exist)
GIMGDIR="_SYS76/GAZP8"

# Destination file for this gpt partition table only image...
GPTBKUPFILE="$NOW.gazp8.sda.sgdisk.gpt"

# Destination file for the complete hard drive image, zipped up...
GIMGFILE="$NOW.gazp8.sda.img.tar.gz"

# Blocksize for run...
BLOCKSIZE="1024K"

echo
echo "BACKUP DRIVE IMAGE TO FILE"
echo
echo "Install gdisk support into the ubuntu live cd session"
echo

# install gdisk into the ubuntu live cd session
sudo apt-get install gdisk
if [ $? -ne 0 ]; then
{
    echo "ERROR! on command <sudo apt-get install gdisk>. Aborting script";
    exit 1;
}
fi
echo
echo "Support for gdisk has been installed into the ubuntu live cd session"
echo



# Echo run variables...
echo
echo "NOW: ${NOW}"
echo "GIMGDIR: ${GIMGDIR}"
echo "GPTBKUPFILE: ${GPTBKUPFILE}"
echo "GIMGFILE: ${GIMGFILE}"
echo "BLOCSIZE: ${BLOCKSIZE}"

#
# validate the existing hard drive GPT Partition Table for any errors, before backing it up...
# if the drive has issues, the backup will abort to allow the drive to be repaired
#

# display partition information
sudo parted /dev/sda 'print'
if [ $? -ne 0 ]; then
{
    echo "ERROR! on command <sudo parted /dev/sda>. Aborting script";
    exit 1;
}
fi

# check the existing file system on the DATA partition(s) (NOTE - do not check boot or linux-swap partitions)
# i.e. "sda2" is the only data partition check performed (below)
sudo fsck /dev/sda2
if [ $? -ne 0 ]; then
{
    echo "ERROR! on command <sudo fsck /dev/sda2>. Aborting script";
    exit 1;
}
fi

# if you have another DATA partition (i.e. a separate data partition for /home) uncomment below
# and provide the next partiion to be checked (i.e. below, it checks partition "sda3")
# sudo fsck /dev/sda3
# if [ $? -ne 0 ]; then
# {
#     echo "ERROR! on command <sudo fsck /dev/sda3>. Aborting script";
#     exit 1;
# }
# fi

# validate the GPT partition table using sgdisk
sudo sgdisk -v /dev/sda
if [ $? -ne 0 ]; then
{
    echo "ERROR! on command <sudo sgdisk -v /dev/sda>. Aborting script";
    exit 1;
}
fi

# If you get here the existing hard drive to be backed up is clean...
# start backup by exporting the GPT Partition Table (only) to file
sudo sgdisk -b /media/ubuntu/COOLMAX/$GIMGDIR/$GPTBKUPFILE /dev/sda
if [ $? -ne 0 ]; then
{
    echo "ERROR! on command <sudo sgdisk -b>. Aborting script";
    exit 1;
}
fi

# store the GPT drive geometry to text file for quick reference
sudo gdisk -l /dev/sda > /media/ubuntu/COOLMAX/$GIMGDIR/$GPTBKUPFILE.info
if [ $? -ne 0 ]; then
{
    echo "ERROR! on command <sudo sgdisk -b>. Aborting script";
    exit 1;
}
fi

echo
echo
echo "Imaging has begun... You will see a completion message (or error message) once image has finished"
echo "BE PATIENT - imaging takes time depending on speed of your USB connection"
echo
echo "To view progress of the imaging process, do the following"
echo "Open a new terminal window. Run the following (below)"
echo
echo "ubuntu@ubuntu:~$ pgrep -l '^dd$'"
echo "6282 dd    <-- this is the example response returned from pgrep"
echo "ubuntu@ubuntu:~$ sudo watch -n 60 kill -USR1 6282"
echo
echo "Now will see every 60 seconds, an update of the progress of the drive imaging"
echo 
echo "Drive is being imaged now..."
echo "Use CTRL-C to interrupt imaging"
echo

# Image drive to file located on the external usb drive...
sudo dd if=/dev/sda bs=$BLOCKSIZE | gzip -c > /media/ubuntu/COOLMAX/$GIMGDIR/$GIMGFILE
if [ $? -ne 0 ]; then
{
    echo "ERROR! on command <sudo sgdisk -b>. Aborting script";
    exit 1;
}
fi

echo "Normal successful completion of imaging script <v2.gazp8.backup.image.sh>"

---

### Post by oldfred on 2013-05-17
See also this thread where pursuvant     had a couple of issues restoring dd copied drive. So even if not running script it can be done. (Just for reference.).

 Restore full drive dd backup - resync gpt partition tables and fsck 
[http://ubuntuforums.org/showthread.php?t=2145563](http://ubuntuforums.org/showthread.php?t=2145563)

---

### Post by pursuvant on 2013-05-18
Two scripts are used for the restore, the first script after it executes requires a reboot, before continuing with the second restore script. Both scripts are below...




save as .sh file (i.e. "v2.gazp8.restore.image.pre.sh")
============================
#!/bin/bash -ux

# 
# GPT DRIVE RESTORE BACKUP IMAGE FROM EXTERNAL USB DRIVE 

# External drive is mounted as "/media/gmill/COOLMAX", ntfs file system
# USB jumpdrive would work equally well, but needs formatted with a file system supporting large files
#
# Notes:
# boot from unbuntu live cd
# connect to internet
# do not mount any partitions on the drive that will be restored
#
# Want to view progress during image? open a NEW terminal window, pgrep -l '^dd$'  to get the PID, then
# sudo watch -n 60 kill -USR1 <pid>
#
# Future enhancements - load pv and use it to visuallyreport progress during imaging...
# 

# Destination directory for this image
GIMGDIR="_SYS76/GAZP8"

echo
echo "RESTORE DRIVE GPT PARTITION TABLE FROM SGDISK BACKUP FILE"
echo
echo "Install gdisk support into the ubuntu live cd session"
echo

# install gdisk into the ubuntu live cd session
sudo apt-get install gdisk
if [ $? -ne 0 ]; then
{
    echo "ERROR! on command <sudo apt-get install gdisk>. Aborting script";
    exit 1;
}
fi
echo
echo "Support for gdisk has been installed into the ubuntu live cd session"
echo

# let user identify the backup GPT file using the Date.Time component of the image file to be restored
# start by showing user a list of files in the backup directory, that can be chosen for restore
echo "show user list of files from the backup files directory"
echo
ls /media/ubuntu/COOLMAX/$GIMGDIR/
echo

# get user input to identify the backup GPT file to be restored
echo "Backup files of the GPT Partition Table available for restore have file names beginning with <date.time>"
echo "Enter <date.time> component of GPT backup file to be restored: "
read fdt
GPTBKUPFILE="$fdt.gazp8.sda.sgdisk.gpt"

echo "GIMGDIR: ${GIMGDIR}"
echo "GPTBKUPFILE: ${GPTBKUPFILE}"

# restore the GPT Partition Table
sudo sgdisk -l /media/ubuntu/COOLMAX/$GIMGDIR/$GPTBKUPFILE /dev/sda
if [ $? -ne 0 ]; then
{
    echo "ERROR! on command <sudo sgdisk -l>. Aborting script";
    exit 1;
}
fi

# sgdisk will give a warning the live cd kernal is still using the old partion table
# and new GPT table will not take over until next boot, so reboot the ubuntu live cd to continue
echo
echo "Normal successful completion of script <v2.gazp8.restore.image.pre.sh>."
echo "Reboot Ubuntu live cd, and continue restore image process with script <v2.gazp8.restore.image.sh>"
============================================


save as .sh file (i.e. "v2.gazp8.restore.image.sh")
============================================
#!/bin/bash -ux

# 
# GPT DRIVE RESTORE BACKUP IMAGE FROM EXTERNAL USB DRIVE 

# External drive is mounted as "/media/gmill/COOLMAX", ntfs file system
# USB jumpdrive would work equally well, but needs formatted with a file system supporting large files
#
# Notes:
# boot from unbuntu live cd
# connect to internet
# do not mount any partitions on the drive that will be restored
#
# Want to view progress during image? open a NEW terminal window, pgrep -l '^dd$'  to get the PID, then
# sudo watch -n 60 kill -USR1 <pid>
#
# Future enhancements - load pv and use it to visuallyreport progress during imaging...
# 

#Destination directory for this image
GIMGDIR="_SYS76/GAZP8"

echo
echo "RESTORE DRIVE FROM BACKUP IMAGE FILE"
echo
echo "Install gdisk support into the ubuntu live cd session"
echo

# install gdisk into the ubuntu live cd session
sudo apt-get install gdisk
if [ $? -ne 0 ]; then
{
    echo "ERROR! on command <sudo apt-get install gdisk>. Aborting script";
    exit 1;
}
fi
echo
echo "Support for gdisk has been installed into the ubuntu live cd session"
echo

echo 
echo "show user list of files from the backup files directory"
echo
ls /media/ubuntu/COOLMAX/$GIMGDIR/
echo

# Collect user input, for the Date.Time identifying the image file to be restored
echo
echo "Enter the <date.time> component of image file to be restored: "
read fdt
GIMGFILE="$fdt.gazp8.sda.img.tar.gz"

# Blocksize for run...
BLOCKSIZE="1024K"

# Echo run variables...
echo
echo "GIMGDIR: ${GIMGDIR}"
echo "GIMGFILE: ${GIMGFILE}"
echo "BLOCSIZE: ${BLOCKSIZE}"

#
# validate the existing hard drive GPT Partition Table for any errors, before restoring data...
# if the drive has issues, the backup will abort to allow the drive to be repaired
#

# display partition information
sudo parted /dev/sda 'print'
if [ $? -ne 0 ]; then
{
    echo "ERROR! on command <sudo parted /dev/sda>. Aborting script";
    exit 1;
}
fi

# check the existing file system on the DATA partition(s) (NOTE - do not check boot or linux-swap partitions)
# i.e. "sda2" is the only data partition check performed (below)
sudo fsck /dev/sda2
if [ $? -ne 0 ]; then
{
    echo "ERROR! on command <sudo fsck /dev/sda2>. Aborting script";
    exit 1;
}
fi

# validate the GPT partition table using sgdisk
sudo sgdisk -v /dev/sda
if [ $? -ne 0 ]; then
{
    echo "ERROR! on command <sudo sgdisk -v /dev/sda>. Aborting script";
    exit 1;
}
fi

echo
echo
echo "Restore of image has begun... You will see a completion message (or error message) once image has finished"
echo "BE PATIENT - restoring an image takes time depending on speed of your USB connection"
echo
echo "To view progress of the restore process, do the following"
echo "Open a new terminal window. Run the following (below)"
echo
echo "ubuntu@ubuntu:~$ pgrep -l '^dd$'"
echo "6282 dd    <-- this is the example response returned from pgrep"
echo "ubuntu@ubuntu:~$ sudo watch -n 60 kill -USR1 6282"
echo
echo "Now will see every 60 seconds, an update of the progress of the restore"
echo 
echo "Drive is being restored now..."
echo
echo "DO NOT INTERRUPT THE RESTORE THAT IS UNDERWAY"
echo

# RESTORE THE DRIVE FROM THE IMAGE...
# Restore drive from the image file on external USB drive...
sudo gunzip -c /media/ubuntu/COOLMAX/$GIMGDIR/$GIMGFILE | sudo dd of=/dev/sda bs=$BLOCKSIZE 

echo
echo "image restored"
echo "check the restored disk file system is valid"
echo

# check all is well with the restored file system
# check the file system on the DATA partition(s) (NOTE - do not check boot or linux-swap partitions)
# i.e. "sda2" is the only data partition check performed (below)
sudo fsck /dev/sda2
if [ $? -ne 0 ]; then
{
    echo "ERROR! on command <sudo fsck /dev/sda2>. Aborting script";
    exit 1;
}
fi

# validate the GPT partition table remains valid using sgdisk
sudo sgdisk -v /dev/sda
if [ $? -ne 0 ]; then
{
    echo "ERROR! on command <sudo sgdisk -v /dev/sda>. Aborting script";
    exit 1;
}
fi

# list the GPT partition table info
sudo gdisk -l /dev/sda
if [ $? -ne 0 ]; then
{
    echo "ERROR! on command <sudo gdisk -l /dev/sda>. Aborting script";
    exit 1;
}
fi

echo "Normal successful completion of restore image script <v2.gazp8.restore.image.sh>"

---

