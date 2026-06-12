---
title: "pmount external hdd / usb a 027 umask instead of 077"
date: 2007-03-17
forum: Outdated Tutorials &amp; Tips
---

### Post by jasonpell on 2007-03-17
This is for Edgy and provides a set of instructions to recompile pmount to enable a 027 umask for vfat and ntfs partitions.  It involves making two very minor changes to a c file and recompiling.  The recompiled pmount is then suid and installed over the top of /usr/bin/pmount

I wanted to allow all users of the same primary group as the person who mounted the partition to be able to access this partition.  I have a situation where I have another user connecting to my PC remotely for a gnome session.

The instructions are not very verbose, 

# ensure your ubuntu can compile stuff
sudo apt-get install build-essential

# ensure the dependencies for pmount are installed
sudo apt-get build-dep pmount

# download the source of pmount
apt-get source pmount

# change into the pmount source directory and run configure to generate make files.
cd pmount-0.9.13
./configure

# now need to make that small change to the fs.c to change the UMASK for vfat and ntfs - this will enable group level access to the partition.
cd src

# so edit the file and do the changes...
vi fs.c

Modify the following lines:
{ "vfat", "nosuid,nodev,user,quiet,shortname=mixed", 1, "077", 1 },
{ "ntfs", "nosuid,nodev,user", 1, "077", 1 },

To be:

{ "vfat", "nosuid,nodev,user,quiet,shortname=mixed", 1, "027", 1 },
{ "ntfs", "nosuid,nodev,user", 1, "027", 1 },

# back to the main directory where we will do the make.
cd ..

make

# back to source to suid the new pmount and copy over old /usr/bin/pmount
cd src

sudo chown root.plugdev pmount
sudo chmod u+s pmount
sudo cp /usr/bin/pmount /usr/bin/pmount.old
sudo cp pmount /usr/bin

That should do it, any subsequent hot plugged devices that are VFAT or NTFS will be mounted to the /media mount point with the appropriate permissions, as per this example;

jason@localhost:~$ ls -la /media
drwxrwxr-x 11 root  plugdev  4096 2007-03-17 15:00 .
drwxr-xr-x 21 root  root     4096 2007-03-04 01:52 ..
lrwxrwxrwx  1 root  root        6 2007-03-04 00:51 cdrom -> cdrom0
drwxr-xr-x  2 root  root     4096 2007-03-04 00:51 cdrom0
dr-xr-x---  1 jason users    4096 2007-03-01 01:24 EXTERNAL_HDD2
lrwxrwxrwx  1 root  root        7 2007-03-04 00:51 floppy -> floppy0
drwxr-xr-x  2 root  root     4096 2007-03-04 00:51 floppy0
dr-xr-x---  1 jason users   16384 2007-03-15 22:02 Ghost Torquay
dr-xr-x---  1 jason users   12288 2007-03-15 22:02 laptopghost
dr-xr-x---  1 jason users    8192 2007-03-15 22:02 My Docs Backup
drwxr-x---  9 jason users    3072 1970-01-01 10:00 usbdisk-2

You can test the change yourself by using the pmount-hal command as such:

pmount-hal /dev/XXXXX

Where XXXXX is a device name, such as sda1

I hope this is helpful to some people - i myself have found it extremely useful - and I do not believe its a security issue, as its read -only.

---

