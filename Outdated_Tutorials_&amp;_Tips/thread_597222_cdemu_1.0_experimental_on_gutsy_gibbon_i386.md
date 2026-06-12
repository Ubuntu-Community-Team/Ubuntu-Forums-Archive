---
title: "cdemu 1.0 experimental on gutsy gibbon i386"
date: 2007-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by dpurple77 on 2007-10-30
Hi there everybody! 

This is my first tutorial because its the first time i needed something and nobody got to doing it for me first. I hope it helps some people that are having trouble with it... 

This is about compiling from source cdemu 1.0 on gutsy gibbon i386 and installing nautlius scripts with some nice scripts to automount the images, so when you right click on an image you get a menu to mount it and it appears on the desktop. This tutorial is meant for beginners so there is a lot of details. It also supposes that we are using a fresh install of gutsy. Here goes....

 First we edit our sources file  

```
sudo nano /etc/apt/sources.list
```

Uncomment everything that starts with deb and comment everything that start with deb-src and also the entry about the cd. Uncomment means delete the # in front of the line and comment means insert a # in front of the line. ( I told you it was going to be for beginners :)  )

Next we update the system, upgrade it, install some tools for compiling, our kernel headers, and some libraries we need to compile everything. so just run these...

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential linux-headers-`uname -r`
sudo apt-get install libglib2.0-dev libsndfile1-dev libsysfs-dev libdbus-glib-1-dev libdaemon-dev python-gtk2-dev libgettext-ruby-util libgettext-ruby1.8 gettext irb1.8 libmono-dev zenity
```

I like to work on my desktop so i can see everything without too much stuff open. So fire up a terminal and go ...

```

cd Desktop/
mkdir cdemu
cd cdemu/
```

We just created a temp folder called cdemu on the desktop so we can work in it. Now to download the source files...
```

wget http://www.kabelkaos.net/cdemu/experimental/libmirage-1.0.0.tar.gz
wget http://www.kabelkaos.net/cdemu/experimental/cdemu-daemon-1.0.0.tar.gz
wget http://www.kabelkaos.net/cdemu/experimental/cdemu-module-1.00.tar.bz2
wget http://www.kabelkaos.net/cdemu/experimental/cdemu-client-1.0.0.tar.gz
wget http://www.kabelkaos.net/cdemu/experimental/gcdemu-1.0.0.tar.gz
```

After we get everything its time for the fun part. Compile everything . Lets do it one at a time...

We untar the file, go into the directory created, run the configure script with some switch, run make to compile, and run sudo make install to install. Easy, right?

```

tar zxvf libmirage-1.0.0.tar.gz 
cd libmirage-1.0.0/
./configure --libdir=/usr/lib
make
sudo make install
```

We can check everything went ok by running 

```
ls -l /usr/lib/ | grep libmirage
```

We must get something like 
```

drwxr-xr-x 2 root root    4096 2007-10-30 14:16 libmirage
-rw-r--r-- 1 root root  592852 2007-10-30 14:16 libmirage.a
-rwxr-xr-x 1 root root     966 2007-10-30 14:16 libmirage.la
lrwxrwxrwx 1 root root      18 2007-10-30 14:16 libmirage.so -> libmirage.so.0.0.0
lrwxrwxrwx 1 root root      18 2007-10-30 14:16 libmirage.so.0 -> libmirage.so.0.0.0
-rwxr-xr-x 1 root root  409528 2007-10-30 14:16 libmirage.so.0.0.0
```

On to the next.. We get out of the directory , untar, go into the created directory and so on...

```

cd ..
tar jxvf cdemu-module-1.00.tar.bz2 
cd cdemu-module-1.00/
make
sudo make install
```

Next we insert the module on the kernel

```
sudo modprobe cdemu
```

and check with 

```
lsmod | grep cdemu
```

which gives something like 
```

cdemu                 33804  0 
cdrom                  37536  2 cdemu,sr_mod
```

On to the next... Its more or less the same, get out, untar, go in, configure, make , install.

```
cd ..
tar zxvf cdemu-daemon-1.0.0.tar.gz 
cd cdemu-daemon-1.0.0/
./configure --sysconfdir=/etc 
make
sudo make install
```

Now we need to restart the daemon so all the devices get created on the restart

```
sudo /etc/init.d/cdemu-daemon restart
```

and you should get something like 

```

* Stopping CDEmu daemon  
* Killing daemon...                                                     [ OK ] 
* Removing kernel module...                                     [ OK ] 
	                                                                         [ OK ]
* Starting CDEmu daemon  
* Inserting kernel module...                                       [ OK ] 
* Waiting for nodes to get created...                        [ OK ] 
* Starting daemon...                                                  [ OK ] 
	                                                                          [ OK ]
```

Lets check for the devices with 

```
ls -l /dev/cde*
```

which should give something like 

```
			
brw-rw---- 1 root floppy 254, 0 2007-10-30 14:21 /dev/cdemu0
brw-rw---- 1 root floppy 254, 1 2007-10-30 14:21 /dev/cdemu1
brw-rw---- 1 root floppy 254, 2 2007-10-30 14:21 /dev/cdemu2
brw-rw---- 1 root floppy 254, 3 2007-10-30 14:21 /dev/cdemu3
brw-rw---- 1 root floppy 254, 4 2007-10-30 14:21 /dev/cdemu4
brw-rw---- 1 root floppy 254, 5 2007-10-30 14:21 /dev/cdemu5
brw-rw---- 1 root floppy 254, 6 2007-10-30 14:21 /dev/cdemu6
brw-rw---- 1 root floppy 254, 7 2007-10-30 14:21 /dev/cdemu7
crw-rw---- 1 root root   254, 0 2007-10-30 14:21 /dev/cdemu_ctl0
crw-rw---- 1 root root   254, 1 2007-10-30 14:21 /dev/cdemu_ctl1
crw-rw---- 1 root root   254, 2 2007-10-30 14:21 /dev/cdemu_ctl2
crw-rw---- 1 root root   254, 3 2007-10-30 14:21 /dev/cdemu_ctl3
crw-rw---- 1 root root   254, 4 2007-10-30 14:21 /dev/cdemu_ctl4
crw-rw---- 1 root root   254, 5 2007-10-30 14:21 /dev/cdemu_ctl5
crw-rw---- 1 root root   254, 6 2007-10-30 14:21 /dev/cdemu_ctl6
crw-rw---- 1 root root   254, 7 2007-10-30 14:21 /dev/cdemu_ctl7
```

And last but not least, the client in axactly the same way, out , untar, in and so on..

```
cd ..
tar zxvf cdemu-client-1.0.0.tar.gz 
cd cdemu-client-1.0.0/
./configure
make
sudo make install

```

We can check with 

```
cdemu status
``` 

which gives something like 
```

Devices status:
DEV   LOADED     TYPE       FILENAME
0     0          N/A        N/A
1     0          N/A        N/A
2     0          N/A        N/A
3     0          N/A        N/A
4     0          N/A        N/A
5     0          N/A        N/A
6     0          N/A        N/A
7     0          N/A        N/A
```
Thats all for cdemu. You can now use it with the command line client but since i guess you are as lazy as myself lets go on a little more shall we? We shall install nautilus actions which  is a nautilus addon for the right click and create two scripts to take care for us the mounting of any images. lets do it  First install nautilus scripts.

```
sudo apt-get install nautilus-scripts
```

Then either go to [http://www.grumz.net/?q=node/307](http://www.grumz.net/?q=node/307) and download everything or stick around and do it by hand. 
We need two scripts which we will install in /bin. So, 

```
gksu gedit /bin/Image-mount
```

and paste all the following which is a script made by Amnon82 on grumz.net hacked by me to reflect the changes made to cdemu 1.0

```
#!/bin/bash
# (C) 2006 AMSOFT - Version 6.10.28-5.00
# Mount CD images
# Get filename extension and make it lower-case
EXT=`echo $1 | sed -e 's/.*\.//'`
EXT_LOW=`echo $EXT | tr 'A-Z' 'a-z'`
# Main
if [ $EXT_LOW == "cue" -o $EXT_LOW == "iso" -o $EXT_LOW == "mds" -o $EXT_LOW == "ccd" -o $EXT_LOW == "nrg" ]; then
# Find a free DEV to mount
DEV=$((`cdemu status | cut -f 6 -d " " | grep 0 -n -m 1 | cut -c 1`-3))
if [ $DEV -lt "0" ]; then
zenity --info --text "You can not mount any more images."; exit 1
fi
# Only allow mounting an image once
FILE="`basename $1`"
MOUNTED="`cdemu status | grep "$FILE" | cut -f18 -d " "`"
IMAGEMOUNTED="`basename $MOUNTED`"
DEVMOUNTED="`cdemu status | grep "$FILE" | cut -f1 -d " " | sed -e 's@:@@'`"
if [ $IMAGEMOUNTED == $FILE ]; then
zenity --info --text "Image already mounted on cdemu$DEVMOUNTED."; exit 1
fi
# DEV needs to be between 0 and 7



if [ $DEV -ge "0" -a $DEV -le 7 ]; then
cdemu load $DEV "$1" &&
mount "/media/cdemu${DEV}" &&
gnome-open "/media/cdemu${DEV}"
fi
# If directory is empty, then release cdemu
if [ "$(ls -A /media/cdemu${DEV})" ]; then
echo
else
cdemu unload $DEV
fi
else zenity --info --text "Selected file is no image."; exit 1
fi
```

Save and exit and lets go for the unmount script

```
gksu gedit /bin/Image-unmount
```

where you paste 
```

#!/bin/bash
# (C) 2006 AMSOFT - Version 6.10.28-5.00
# Unmount CD images
# Get filename extension and make it lower-case
EXT=`echo $1 | sed -e 's/.*\.//'`
EXT_LOW=`echo $EXT | tr 'A-Z' 'a-z'`
# Main
if [ $EXT_LOW == "cue" -o $EXT_LOW == "iso" -o $EXT_LOW == "mds" -o $EXT_LOW == "ccd" -o $EXT_LOW == "nrg" ]; then
# Get the cdemu device-number
DEV="`cdemu status | grep "$1" | cut -f1 -d " " | sed -e 's@:@@'`"
# Unmount
umount "/media/cdemu${DEV}"
# Release cdemu
if [ $DEV -ge "0" -a $DEV -le 7 ]; then
cdemu unload $DEV
fi
else zenity --info --text "Selected file is no image."; exit 1
fi
```

Save and exit. Now for the final touch, the scripts to import to nautilus actions to do all the work for us. These are a little long... :)

```
gedit mount-image.schemas
```

and paste the following 
```

<?xml version="1.0" encoding="UTF-8"?>
<gconfschemafile>
  <schemalist>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/label</key>
      <applyto>/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/label</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <default>Mount Image</default>
        <short>The label of the menu item</short>
        <long>The label of the menu item that will appear in the Nautilus popup menu when the selection matches the appearance condition settings</long>
      </locale>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/tooltip</key>
      <applyto>/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/tooltip</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <default></default>
        <short>The tooltip of the menu item</short>
        <long>The tooltip of the menu item that will appear in the Nautilus statusbar when the user points to the Nautilus popup menu item with his/her mouse</long>
      </locale>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/icon</key>
      <applyto>/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/icon</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <short>The icon of the menu item</short>
        <long>The icon of the menu item that will appear next to the label in the Nautilus popup menu when the selection matches the appearance conditions settings</long>
      </locale>
      <default>gtk-cdrom</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/path</key>
      <applyto>/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/path</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <short>The path of the command</short>
        <long>The path of the command to start when the user select the menu item in the Nautilus popup menu</long>
      </locale>
      <default>/bin/Image-mount</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/parameters</key>
      <applyto>/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/parameters</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <short>The parameters of the command</short>
        <long>The parameters of the command to start when the user selects the menu item in the Nautilus popup menu.

The parameters can contain some special tokens which are replaced by Nautilus information before starting the command:

%d: base folder of the selected file(s)
%f: the name of the selected file or the first one if many are selected
%m: space-separated list of the basenames of the selected file(s)/folder(s)
%M: space-separated list of the selected file(s)/folder(s), with their full paths
%u: GnomeVFS URI
%s: scheme of the GnomeVFS URI
%h: hostname of the GnomeVFS URI
%U: username of the :%s/GnomeVFS URI
%%: a percent sign</long>
      </locale>
      <default>%M</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/basenames</key>
      <applyto>/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/basenames</applyto>
      <owner>nautilus-actions</owner>
      <type>list</type>
      <list_type>string</list_type>
      <locale name="C">
        <short>The list of pattern to match the selected file(s)/folder(s)</short>
        <long>A list of strings with joker '*' or '?' to match the name of the selected file(s)/folder(s). Each selected items must match at least one of the filename patterns for the action to appear</long>
      </locale>
      <default>[*.cue,*.CUE,*.iso,*.ISO,*.mds,*.MDS,*.ccd,*.CCD,*.nrg,*.NRG]</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/matchcase</key>
      <applyto>/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/matchcase</applyto>
      <owner>nautilus-actions</owner>
      <type>bool</type>
      <locale name="C">
        <short>'true' if the filename patterns have to be case sensitive, 'false' otherwise</short>
        <long>If you need to match a filename in a case-sensitive manner, set this key to 'true'. If you also want, for example '*.jpg' to match 'photo.JPG', set 'false'</long>
      </locale>
      <default>true</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/mimetypes</key>
      <applyto>/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/mimetypes</applyto>
      <owner>nautilus-actions</owner>
      <type>list</type>
      <list_type>string</list_type>
      <locale name="C">
        <short>The list of patterns to match the mimetypes of the selected file(s)</short>
        <long>A list of strings with joker '*' or '?' to match the mimetypes of the selected file(s). Each selected items must match at least one of the mimetype patterns for the action to appear</long>
      </locale>
      <default>[*/*]</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/isfile</key>
      <applyto>/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/isfile</applyto>
      <owner>nautilus-actions</owner>
      <type>bool</type>
      <locale name="C">
        <short>'true' if the selection can have files, 'false' otherwise</short>
        <long>This setting is tied in with the 'isdir' setting. The valid combinations are:

isfile=TRUE and isdir=FALSE: the selection may hold only files
isfile=FALSE and isdir=TRUE: the selection may hold only folders
isfile=TRUE and isdir=TRUE': the selection may hold both files and folders
isfile=FALSE and isdir=FALSE: this is an invalid combination (your configuration will never appear)</long>
      </locale>
      <default>true</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/isdir</key>
      <applyto>/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/isdir</applyto>
      <owner>nautilus-actions</owner>
      <type>bool</type>
      <locale name="C">
        <short>'true' if the selection can have folders, 'false' otherwise</short>
        <long>This setting is tied in with the 'isfile' setting. The valid combinations are:

isfile=TRUE and isdir=FALSE: the selection may hold only files
isfile=FALSE and isdir=TRUE: the selection may hold only folders
isfile=TRUE and isdir=TRUE': the selection may hold both files and folders
isfile=FALSE and isdir=FALSE: this is an invalid combination (your configuration will never appear)</long>
      </locale>
      <default>false</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/accept-multiple-files</key>
      <applyto>/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/accept-multiple-files</applyto>
      <owner>nautilus-actions</owner>
      <type>bool</type>
      <locale name="C">
        <short>'true' if the selection can have several items, 'false' otherwise</short>
        <long>If you need one or more files or folders to be selected, set this key to 'true'. If you want just one file or folder, set 'false'</long>
      </locale>
      <default>false</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/schemes</key>
      <applyto>/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/schemes</applyto>
      <owner>nautilus-actions</owner>
      <type>list</type>
      <list_type>string</list_type>
      <locale name="C">
        <short>The list of GnomeVFS schemes where the selected files should be located</short>
        <long>Defines the list of valid GnomeVFS schemes to be matched against the selected items. The GnomeVFS scheme is the protocol used to access the files. The keyword to use is the one used in the GnomeVFS URI.

Examples of GnomeVFS URI include: 
file:///tmp/foo.txt
sftp:///root@test.example.net/tmp/foo.txt

The most common schemes are:

'file': local files
'sftp': files accessed via SSH
'ftp': files accessed via FTP
'smb': files accessed via Samba (Windows share)
'dav': files accessed via WebDav

All GnomeVFS schemes used by Nautilus can be used here.</long>
      </locale>
      <default>[file]</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/version</key>
      <applyto>/apps/nautilus-actions/configurations/b09ff09f-52c7-4d9e-99b2-04e462144bdf/version</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <short>The version of the configuration format</short>
        <long>The version of the configuration format that will be used to manage backward compatibility</long>
      </locale>
      <default>1.1</default>
    </schema>
  </schemalist>
</gconfschemafile>
```


Save and exit and last

```
gedit unmount-image.schemas
```

and paste the following 
```

<?xml version="1.0" encoding="UTF-8"?>
<gconfschemafile>
  <schemalist>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/label</key>
      <applyto>/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/label</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <default>UnMount Image</default>
        <short>The label of the menu item</short>
        <long>The label of the menu item that will appear in the Nautilus popup menu when the selection matches the appearance condition settings</long>
      </locale>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/tooltip</key>
      <applyto>/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/tooltip</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <default></default>
        <short>The tooltip of the menu item</short>
        <long>The tooltip of the menu item that will appear in the Nautilus statusbar when the user points to the Nautilus popup menu item with his/her mouse</long>
      </locale>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/icon</key>
      <applyto>/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/icon</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <short>The icon of the menu item</short>
        <long>The icon of the menu item that will appear next to the label in the Nautilus popup menu when the selection matches the appearance conditions settings</long>
      </locale>
      <default>gtk-stop</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/path</key>
      <applyto>/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/path</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <short>The path of the command</short>
        <long>The path of the command to start when the user select the menu item in the Nautilus popup menu</long>
      </locale>
      <default>/bin/Image-unmount</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/parameters</key>
      <applyto>/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/parameters</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <short>The parameters of the command</short>
        <long>The parameters of the command to start when the user selects the menu item in the Nautilus popup menu.

The parameters can contain some special tokens which are replaced by Nautilus information before starting the command:

%d: base folder of the selected file(s)
%f: the name of the selected file or the first one if many are selected
%m: space-separated list of the basenames of the selected file(s)/folder(s)
%M: space-separated list of the selected file(s)/folder(s), with their full paths
%u: GnomeVFS URI
%s: scheme of the GnomeVFS URI
%h: hostname of the GnomeVFS URI
%U: username of the :%s/GnomeVFS URI
%%: a percent sign</long>
      </locale>
      <default>%f</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/basenames</key>
      <applyto>/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/basenames</applyto>
      <owner>nautilus-actions</owner>
      <type>list</type>
      <list_type>string</list_type>
      <locale name="C">
        <short>The list of pattern to match the selected file(s)/folder(s)</short>
        <long>A list of strings with joker '*' or '?' to match the name of the selected file(s)/folder(s). Each selected items must match at least one of the filename patterns for the action to appear</long>
      </locale>
      <default>[*.cue,*.CUE,*.iso,*.ISO,*.mds,*.MDS,*.ccd,*.CCD,*.nrg,*.NRG]</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/matchcase</key>
      <applyto>/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/matchcase</applyto>
      <owner>nautilus-actions</owner>
      <type>bool</type>
      <locale name="C">
        <short>'true' if the filename patterns have to be case sensitive, 'false' otherwise</short>
        <long>If you need to match a filename in a case-sensitive manner, set this key to 'true'. If you also want, for example '*.jpg' to match 'photo.JPG', set 'false'</long>
      </locale>
      <default>true</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/mimetypes</key>
      <applyto>/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/mimetypes</applyto>
      <owner>nautilus-actions</owner>
      <type>list</type>
      <list_type>string</list_type>
      <locale name="C">
        <short>The list of patterns to match the mimetypes of the selected file(s)</short>
        <long>A list of strings with joker '*' or '?' to match the mimetypes of the selected file(s). Each selected items must match at least one of the mimetype patterns for the action to appear</long>
      </locale>
      <default>[*/*]</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/isfile</key>
      <applyto>/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/isfile</applyto>
      <owner>nautilus-actions</owner>
      <type>bool</type>
      <locale name="C">
        <short>'true' if the selection can have files, 'false' otherwise</short>
        <long>This setting is tied in with the 'isdir' setting. The valid combinations are:

isfile=TRUE and isdir=FALSE: the selection may hold only files
isfile=FALSE and isdir=TRUE: the selection may hold only folders
isfile=TRUE and isdir=TRUE': the selection may hold both files and folders
isfile=FALSE and isdir=FALSE: this is an invalid combination (your configuration will never appear)</long>
      </locale>
      <default>true</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/isdir</key>
      <applyto>/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/isdir</applyto>
      <owner>nautilus-actions</owner>
      <type>bool</type>
      <locale name="C">
        <short>'true' if the selection can have folders, 'false' otherwise</short>
        <long>This setting is tied in with the 'isfile' setting. The valid combinations are:

isfile=TRUE and isdir=FALSE: the selection may hold only files
isfile=FALSE and isdir=TRUE: the selection may hold only folders
isfile=TRUE and isdir=TRUE': the selection may hold both files and folders
isfile=FALSE and isdir=FALSE: this is an invalid combination (your configuration will never appear)</long>
      </locale>
      <default>false</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/accept-multiple-files</key>
      <applyto>/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/accept-multiple-files</applyto>
      <owner>nautilus-actions</owner>
      <type>bool</type>
      <locale name="C">
        <short>'true' if the selection can have several items, 'false' otherwise</short>
        <long>If you need one or more files or folders to be selected, set this key to 'true'. If you want just one file or folder, set 'false'</long>
      </locale>
      <default>false</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/schemes</key>
      <applyto>/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/schemes</applyto>
      <owner>nautilus-actions</owner>
      <type>list</type>
      <list_type>string</list_type>
      <locale name="C">
        <short>The list of GnomeVFS schemes where the selected files should be located</short>
        <long>Defines the list of valid GnomeVFS schemes to be matched against the selected items. The GnomeVFS scheme is the protocol used to access the files. The keyword to use is the one used in the GnomeVFS URI.

Examples of GnomeVFS URI include: 
file:///tmp/foo.txt
sftp:///root@test.example.net/tmp/foo.txt

The most common schemes are:

'file': local files
'sftp': files accessed via SSH
'ftp': files accessed via FTP
'smb': files accessed via Samba (Windows share)
'dav': files accessed via WebDav

All GnomeVFS schemes used by Nautilus can be used here.</long>
      </locale>
      <default>[file]</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/version</key>
      <applyto>/apps/nautilus-actions/configurations/5d004e97-1e47-430f-b77c-5f6ef3417954/version</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <short>The version of the configuration format</short>
        <long>The version of the configuration format that will be used to manage backward compatibility</long>
      </locale>
      <default>1.1</default>
    </schema>
  </schemalist>
</gconfschemafile>
```

Thats it.! Just import the schemas into nautilus actions from System>Preferences>Nautilus Actions Configuration>Import and you are golden. Now when you right click on an image file you get a menu to mount the image . After you are done you right click on the file again and select unmount the image and thats all there is to it.Have a nice time with it.:)

---

### Post by mndzmyst on 2007-12-09
I just tried your tutorial and finally got cdemu installed correctly, at least I thought until I tried to mount an image. It keeps telling me that the image is already mounted. Any ideas why???


::EDIT::

Nevermind, I found out the path could not contain spaces. Also I had to modify the script as it would not make cdemu directories. Here is what I added (in red)

For Image-mount


if [ $DEV -ge "0" -a $DEV -le 7 ]; then
cdemu load $DEV "$1" &&
[COLOR="Red"]foo=`gksudo -u root -k -m "enter your password for root terminal access" /bin/echo "got r00t?"`
sudo mkdir "/media/cdemu${DEV}" &&[/COLOR]
mount "/media/cdemu${DEV}" &&
gnome-open "/media/cdemu${DEV}"

For Image-unmount

# Unmount
[COLOR="Red"]foo=`gksudo -u root -k -m "enter your password for root terminal access" /bin/echo "got r00t?"`[/COLOR]
umount "/media/cdemu${DEV}"
[COLOR="Red"]sudo rmdir "/media/cdemu${DEV}"[/COLOR]

I figured it out from adamkane's scripts found in the third post here [http://ubuntuforums.org/showthread.php?t=149963](http://ubuntuforums.org/showthread.php?t=149963)

Now if only I can get the applet to work:confused:

---

### Post by francky_51 on 2007-12-10
I read this how-to yesterday evening and I saw that the most important was missing :
You have to create the mounting point in /media 
So in a terminal :
```

sudo mkdir /media/cdemu0
sudo mkdir /media/cdemu1
sudo mkdir /media/cdemu2
sudo mkdir /media/cdemu3
sudo mkdir /media/cdemu4
sudo mkdir /media/cdemu5
sudo mkdir /media/cdemu6
sudo mkdir /media/cdemu7
```

Then add cdemu devices to your /etc/fstab

**gksu gedit /etc/fstab**

```
/dev/cdemu0	/media/cdemu0	iso9660		ro,user,noauto			0	0
/dev/cdemu1	/media/cdemu1	iso9660		ro,user,noauto			0	0
/dev/cdemu2	/media/cdemu2	iso9660		ro,user,noauto			0	0
/dev/cdemu3	/media/cdemu3	iso9660		ro,user,noauto			0	0
/dev/cdemu4	/media/cdemu4	iso9660		ro,user,noauto			0	0
/dev/cdemu5	/media/cdemu5	iso9660		ro,user,noauto			0	0
/dev/cdemu6	/media/cdemu6	iso9660		ro,user,noauto			0	0
/dev/cdemu7	/media/cdemu7	iso9660		ro,user,noauto			0	0
```

To finish reboot the computer.

I also compiled the gnome applet "gcdemu"

```
tar zxvf gcdemu-1.0.0.tar.gz 
cd gcdemu-1.0.0
./configure --prefix=/usr
make
sudo make install

```


This applet is not very useful (in my opinion) as you can just load an image file and not mount it automatically.
You will also not be able to umount an image mount with the nautilus script.

I hope my post will be helpful (and my english not too bad :) )

---

### Post by mndzmyst on 2007-12-10
That is definitely another way to get it accomplished, yet I thought it cleaner for beginners to just change the script. But thanx for the tip on gcdemu, saved me who knows how much time =D> ... and your english is fine.... Have you by chance figured out how to umount from the folder on the desktop, instead of the original folder?

---

### Post by francky_51 on 2007-12-10
> Have you by chance figured out how to umount from the folder on the desktop, instead of the original folder?
For me, it works from the desktop without doing anything else.

---

### Post by francky_51 on 2007-12-10
I also configure cdemu-daemon to start automatically

```
cd /etc/init.d
sudo update-rc.d -f cdemu-daemon defaults 
```

---

### Post by mndzmyst on 2007-12-10
What I should have asked was how to make it appear in my nautilus-actions. The unmount script is looking for extensions, yet when it mounts, the link on my desktop only contains the basename. If i use the regular unmount volume choice it will unmount but not unload from cdemu.

---

### Post by komuta on 2007-12-12
Hi

Thanks for your tutorial. I installed everything (except the nautilus script), but encounter an error when mounting an iso. I think the problem is :

ubuntu:~$ cdemu supported-images
Supported image types:
ubuntu:~$ 

There seems to be a problem with the detection of supported images types. I tried to look up in details, and all image formats are supported as libmirage plugins, in /usr/lib/libmirage, but for some unknown reasons cdemu-daemon fails to find them. Did I miss something ??

---

### Post by XVampireX on 2007-12-12
Hey I just followed the tutorial, and although it shows the devices and everything enabled and working... I can't mount anything, I tried mounting some iso's/bin/cues but nothing worked, not even with the gcdemu as it returns some hal/dbus related error.

It may help debugging if I would add that doing /bin/Mount-image will return this:
serge@serge-desktop:~$ /bin/Image-mount
/bin/Image-mount: line 8: [: too many arguments

Thanks. Actually I was looking for a good image mounting application like daemon tools...

---

### Post by XVampireX on 2007-12-12
Hey I just followed the tutorial, and although it shows the devices and everything enabled and working... I can't mount anything, I tried mounting some iso's/bin/cues but nothing worked, not even with the gcdemu as it returns some hal/dbus related error.

It may help debugging if I would add that doing /bin/Mount-image will return this:
serge@serge-desktop:~$ /bin/Image-mount
/bin/Image-mount: line 8: [: too many arguments

Thanks. Actually I was looking for a good image mounting application like daemon tools...

EDIT: I fixed it, it's working now... :) Just need to add the root part else is fine

---

### Post by Rigrig on 2008-02-13
Seems some things have changed with cdemu 1.0.0, took me some time to get this working, with some modifications:

*) The daemon now seems to listen on the system bus by default, changed all calls to cdemu accordingly

*) I always have the places pane open so I only use the mount script, and use the eject menu from the places pane. Also because of this I don't have it open a new window with the mounted cd anymore, I just select the CD from the places pane.

*) It now works with filenames that contain spaces 

*) I set it up so it works with 3 devices, somehow cdemud wouldn't load properly when I tried to use more devices.

Steps I took:
1) Go to [cdemu.sourceforge.net](http://cdemu.sourceforge.net/), and follow the link to binary packages on the left, until you get to the download page, there select "Packages - Ubuntu 7.10", and download all 5 debs (you can skip gcdemu if you don't want the applet)

2) Install all downloaded .deb files, the easiest way is to open a terminal window, cd to the place where you downloaded them, and issue a```
sudo dpkg -i *.deb
```

3) Edit /etc/default/cdemu-daemon to create the number of devices you want:```
sudo gedit /etc/default/cdemu-daemon
``` and change line #5 to ```
DEVICES=3
```
(Somehow my cdemu-daemon wouldn't load properly with more devices)

4) Make the cdemu daemon auto-start, and load it now:
```
sudo update-rc.d cdemu-daemon defaults
sudo /etc/init.d/cdemu-daemon restart
```

5) Create mountpoints for the images:
```
sudo mkdir /media/cdemu0
sudo mkdir /media/cdemu1
sudo mkdir /media/cdemu2
```

6) Create fstab entries for cdemu, so you won't need to be root in order to mount images:
```
sudo gedit /etc/fstab
```
Then add the following lines to the end:
```
# CDemu 
/dev/scd0	/media/cdemu0	iso9660		ro,user,noauto			0	0
/dev/scd1	/media/cdemu1	iso9660		ro,user,noauto			0	0
/dev/scd2	/media/cdemu2	iso9660		ro,user,noauto			0	0
```

7) Create the script to mount images:
```
sudo gedit /bin/Image-mount
```
paste in the following:
```
#!/bin/bash
# (C) 2006 AMSOFT - Version 6.10.28-5.00
# Mount CD images
# Get filename extension and make it lower-case
EXT=`echo $1 | sed -e 's/.*\.//'`
EXT_LOW=`echo $EXT | tr 'A-Z' 'a-z'`
# Main
if [ $EXT_LOW == "cue" -o $EXT_LOW == "iso" -o $EXT_LOW == "mds" -o $EXT_LOW == "ccd" -o $EXT_LOW == "nrg" ]; then
  # Find a free DEV to mount
  DEV=$((`cdemu -b system status | cut -f 6 -d " " | grep 0 -n -m 1 | cut -c 1`-3))
  if [ $DEV -lt "0" ]; then
    zenity --error --text "You can not mount any more images."; exit 1
  fi
  # Only allow mounting an image once
  FILE="`basename \"$1\"`"
  MOUNTED="`cdemu -b system status | grep \"$FILE\" | cut -f 18- -d " "`"
  IMAGEMOUNTED="`basename $MOUNTED`"
  DEVMOUNTED="`cdemu -b system status | grep \"$FILE\" | cut -f1 -d " " | sed -e 's@:@@'`"
  if [ $IMAGEMOUNTED == $FILE ]; then
    zenity --info --text "'${FILE}' is already mounted on 'cdemu$DEVMOUNTED'."; exit 1
  fi

  # DEV needs to be between 0 and 2
  if [ $DEV -ge "0" -a $DEV -le 2 ]; then
    cdemu -b system load $DEV "$1" &&
    mount "/media/cdemu${DEV}" # && gnome-open "/media/cdemu${DEV}"
    # Uncomment (by removing '#' from) last part of previous line to open mounted cd in new window
  fi
  # If directory is empty, then release cdemu
  if ! [ "$(ls -A /media/cdemu${DEV})" ]; then
    cdemu -b system unload $DEV
  fi
else
  zenity --info --text "'${FILE}' is not a CD image."; exit 1
fi
```
then make it executable:
```
sudo chmod +x /bin/Image-mount
```

8) Create and load the *image-mount.schemas* file as described by dpurple77

Now you're ready to go, to mount a CD image just right-click it and select 'Mount Image' from the menu, the cd will show up in the places pane (F9 to toggle showing the pane, use the menu to select places)
To unmount select the CD in the places pane, right-click and select 'Eject'

---

### Post by cszikszoy on 2008-03-05
Thanks so much Rigrig!

I spent a good hour debugging the original Nautilus Actions script for cdemu mounting.  I got about half way through editing it myself, until I found out that someone else did it already!

Thanks again.

---

