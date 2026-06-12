---
title: "HOWTO:  XTRS - TRS-80 Model 1, 3, &amp; 4 Emulator"
date: 2010-10-06
forum: Outdated Tutorials &amp; Tips
---

### Post by lkraemer on 2010-10-06
**HOWTO: XTRS - TRS-80 Model 1, 3, & 4 Emulator**

This HOWTO: will guide you through the process of downloading, compiling,
and getting Tim Mann's XTRS - Radio Shack Model 1, 3, & 4 EMULATOR running in Ubuntu 10.04 LTS.

If you wish to Download the Source, and Compile XTRS the following steps will assist you in doing that because the
latest version of XTRS is not in the repo's.  If you download the source and compile, you will not get the Documentation
with the source.  I installed the version in the repo's and copied that documentation to a flash drive.
It is located at:  /usr/share/doc/xtrs

[B]If you choose to install xtrs from the repositories, versus compiling the latest version.......
just proceed to the SETUP FOR RUNNING XTRS: Section below.[/B]


**PREWORK:**
1. Download the Source code for Version 4.9D from Tim's Website.
[http://www.tim-mann.org/xtrs.html](http://www.tim-mann.org/xtrs.html)
I chose to download the xtrs-4.9d.zip file.  You could also have
chosen the tar.gz file.  Extract the xtrs-4.9d folder to your xtrs
subdirectory.  (ROM Files were not included!)


**INSTALL REQUIRED SOFTWARE FOR COMPILE:**
Typically you need to install build-essential and the headers for the
kernel you are running, if you are going to compile code.
```

uname -r

```
will tell you the kernel you are currently running.
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
will install the software needed to compile your code.


**TYPICAL COMPILE STEPS: (from within your source directory)**
```

./configure
make clean
make
sudo make install

```
"make clean" won't remove anything on the first compile, but will clean up
on a successive compile.

You can also use checkinstall to build a deb file.
REF:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)


**COMPILE xtrs ver 4.9D FROM SOURCE:**

1.  Use Synaptics to install the following Library Files needed for the Compile:
```

libxext-dev
libreadline-dev

```
NOTE: You may also need libxt-dev 

2.  Create a needed subdirectory:
Create the subdirectory man1 located immediately under /man with 755 permissions.
/usr/local/share/man/man1/
drwxr-xr-x  3 root root  4096 2010-10-05 22:02 man


3.  Compile & Install (no configure file exists, and no errors from compile assumed......mine worked fine):
```

make clean
make
sudo make install

```

**SETUP FOR RUNNING XTRS:**

1.  Remove any previous Symbolic linked files (if any):
```

cd ~/xtrs
sudo rm disk4-0
sudo rm disk4-1    #AS NEEDED
sudo rm disk4-2    #AS NEEDED
sudo rm disk4-3    #AS NEEDED

```

NOTE: 
Model 1 files will be disk1-0, disk1-1, disk1-2, disk1-3
Model 3 files will be disk3-0, disk3-1, disk3-2, disk3-3
Model 4 files will be disk4-0, disk4-1, disk4-2, disk4-3
And real hardware drives can be used via Symbolic linking.

2. Copy Model I, Model III, Model 4, and Model 4P ROM image files to /usr/local/lib/xtrs
```

cd ~/xtrs
sudo cp level2.rom /usr/local/lib/xtrs/level2rom.hex      #(Original Filename was level2.rom)
sudo cp model3.rom /usr/local/lib/xtrs/romimage.m3        #(Original Filename was model3.rom)
sudo cp model4.rom /usr/local/lib/xtrs/romimage.m4        #(Original Filename was model4.rom)
sudo cp model4p.rom /usr/local/lib/xtrs/romimage.m4p      #(Original Filename was model4p.rom)

```
These files need Permissions as shown
> 
-rwxr-xr-x 1 root staff 14336 Jul 10 03:51 romimage.m4
-rwxr-xr-x 1 root staff   504 Jul 10 03:34 romimage.m4p
-rwxr-xr-x 1 root staff 14336 Jul 10 03:32 romimage.m3
-rwxr-xr-x 1 root staff 12288 Jul 10 03:31 level2rom.hex


3.  Locate the .DSK or .DMK (NEWDOS, DOSPLUS, LDOS, TRSDOS, ULTRADOS, MULTIDOS, or MONTEZUMA MICRO CP/M) OS files you will use:
(If you are using Montezuma Micro 2.31 CP/M, use mkdisk to reset the write protect attribute of the file, so you can use CONFIG to change the Drive Parameters and save the settings.  If you don't change the file to unprotected, you won't be able to save the parameters so the settings won't survive a reboot.)
```

mkdisk -u -k filename.dmk
mkdisk -u -k MMCPM231.DSK

```

4.  Create the Symbolic Links to the files you will use, and to real TRS-80 Model 1, 3, or 4 Drives:
```

ln -s /home/larry/xtrs/Mmcpm231/MMCPM231.DSK disk4-0
ln -s /home/larry/xtrs/Mmcpm231/MMTOOLS.DSK disk4-1
ln -s /dev/fd0 disk4-2              #THESE ARE REAL FLOPPY DRIVES
ln -s /dev/fd1 disk4-3              #THESE ARE REAL FLOPPY DRIVES

```

5.  Run xtrs (adjust keystretch down to around 500 from 4000 to prevent multiple keystrokes depending on how fast your Host system is running):
```

/usr/local/bin/xtrs -keystretch 400 -autodelay -model 4 -romfile ~/xtrs/ROMS/model4.rom -diskdir .

```

Use the F8 Function Key to EXIT the Emulator.
Use the F11 Function Key for HELP on the Emulator.

6.  There is a man page with lots more information located at:
[http://manpages.ubuntu.com/manpages/lucid/man1/xtrs.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/xtrs.1.html)

7.  Now you have the full running Radio Shack OS of your choice available, assuming you know
how to operate the Old Radio Shack Model 1, 3, 4, & 4P Computers.

8. Copy the saved xtrs-usr-share-doc folder from the flash drive to /usr/share/doc/xtrs


ENJOY!

THANK YOU TO TIM MANN AND ALL WHO CONTRIBUTED!

lkraemer
07-30-2011

---

