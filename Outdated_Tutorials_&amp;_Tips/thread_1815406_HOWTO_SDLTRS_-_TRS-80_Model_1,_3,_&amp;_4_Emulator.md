---
title: "HOWTO: SDLTRS - TRS-80 Model 1, 3, &amp; 4 Emulator - Ubuntu"
date: 2011-07-31
forum: Outdated Tutorials &amp; Tips
---

### Post by lkraemer on 2011-07-31
**HOWTO: SDLTRS - TRS-80 Model 1, 3, & 4 Emulator for Linux**

This HOWTO: will guide you through the process of downloading, compiling, and getting
SDLTRS - Radio Shack Model 1, 3, & 4 EMULATOR running in Ubuntu 10.04.3 LTS.


**PREWORK:**
Download the Source code for Version 1.1.0 from Mark Grebe's site.
[http://sdltrs.sourceforge.net/index.html](http://sdltrs.sourceforge.net/index.html)
Extract the mg-sdltrs_110_Linux.tar.gz file to your sdltrs_1_1_0 subdirectory.  (ROM Files were not included!)

At this point you need to check any Physical Floppy drives connected to your computer.  Be sure to set
the drive type correctly in your PC's BIOS.  Linux and sdltrs rely on this information to know how fast
your drives are spinning and hence what data rate to use when reading and writing.


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
"make clean" won't remove anything on the first compile, but will clean up on a successive compile.
It also removes the Bin file from the source subdirectory.


**COMPILE sdltrs FROM SOURCE:**

1.  Use Synaptics to install the following Library Files needed for the Compile:
```

libsdl1.2-dev

```
NOTE: For Ubuntu 8.04 LTS I also had to install libxt-dev 

2.  Compile & Install (no configure file exists, and no errors from compile assumed......mine worked fine):
```

make clean
make

```


**SETUP FOR RUNNING sdltrs:**

1.  Remove any previous Symbolic linked files (if any):
```

cd ~/sdltrs_1_1_0/src/linux
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

2. Copy Model I, Model III, Model 4, and Model 4P ROM image files to ~/sdltrs_1_1_0/src/linux/
```

cd ~/sdktrs_1_1_0/src/linux
sudo cp ~/pathto/level2.rom ~/sdltrs_1_1_0/src/linux/level2rom.hex      #(Original Filename was level2.rom)
sudo cp ~/pathto/model3.rom ~/sdltrs_1_1_0/src/linux/romimage.m3        #(Original Filename was model3.rom)
sudo cp ~/pathto/model4.rom ~/sdltrs_1_1_0/src/linux/romimage.m4        #(Original Filename was model4.rom)
sudo cp ~/pathto/model4p.rom ~/sdltrs_1_1_0/src/linux/romimage.m4p      #(Original Filename was model4p.rom)

```

3.  Locate the .DSK or .DMK (NEWDOS, DOSPLUS, LDOS, TRSDOS, ULTRADOS, MULTIDOS, or MONTEZUMA MICRO CP/M) OS files you will use:
(If you are using Montezuma Micro 2.31 CP/M, you may use mkdisk to reset the write protect attribute of the file, so you can use CONFIG
to change the Drive Parameters and save the settings.  If you don't change the file to unprotected, you may not be able to save the
parameters so the settings won't survive a reboot.)  NOTE:  mkdisk is included in Tim Mann's xtrs.
```

mkdisk -u -k filename.dmk
mkdisk -u -k MMCPM231.DSK

```

4.  Create the Symbolic Links to the files you will use, and to real TRS-80 Model 1, 3, or 4 Internal/External Drives:
```

ln -s ~/sdltrs_1_1_0/src/linux/MMCPM231.DSK disk4-0
ln -s ~/xtrs/Mmcpm231/MMTOOLS.DSK disk4-1
ln -s /dev/fd0 disk4-2              #THESE ARE REAL FLOPPY DRIVES
ln -s /dev/fd1 disk4-3              #THESE ARE REAL FLOPPY DRIVES

```
NOTE: (You don't need to use Symbolic links if you aren't going to be using Real Floppy Drives.  Likewise, you can skip
this step totally if you want to set up sdltrs from the text GUI.)

5.  Run sdltrs (adjust keystretch down to around 500 from 4000 to prevent multiple keystrokes depending on how fast your Host system is running):
(NOTE: I disabled the Serial Port to stop the errors with the -serial switch)
```

~/sdltrs_1_1_0/src/linux/sdltrs -keystretch 400 -serial "" -autodelay -model 4 -diskdir .
#./sdltrs -keystretch 400 -serial "" -autodelay -model 4 -romfile model4.rom -sizemap 5,5,5,5,5,5,5,5 -stepmap 1,1,1,1,1,1,1,1 -turborate 2 -diskdir .

```

Use the F7 Function Key to Setup the Virtual & Floppy Drives.
Use the F8 Function Key to EXIT the Emulator.
Use the F11 Function Key for Turbo Mode on the Emulator.  This allows the emulator to run faster than a real TRS80.
By default, when on, the emulator runs 5 times the speed of a normal TRS80, however, the rate is adjustable through the text GUI,
or command line/configuration file options.


Once the Emulator starts, use F7 to Double check the Model is Model 4, Disk Drive Step is Single and the Size as 5" for
all eight drives.  Select the Image, or Symbolic Link for each Disk Image or Real Floppy Drive.  In a Terminal Window,
if the Symbolic Links are BLACK with RED Text, that device is DISABLED or DOES NOT EXIST.

Verify that the keystretch is set for ~400, or whatever your system requires..

If these configuration settings should persist, then save the Configuration and Emulator Settings.

F10 Will boot these New Settings.

6.  Once the Montezuma Micro CP/M system boots, immediately execute CONFIG to set the Floppy drives parameters,
equal to what the Emulator has selected, which should also match your BIOS settings.

7.  There is a man page with lots more information located at:
[http://manpages.ubuntu.com/manpages/lucid/man1/xtrs.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/xtrs.1.html)
[http://sdltrs.sourceforge.net/docs/index.html](http://sdltrs.sourceforge.net/docs/index.html)

8.  Now you have the full running Radio Shack OS of your choice available, assuming you know how to operate the
Old Radio Shack Model 1, 3, 4, & 4P Computers.

9. I have found and corrected a couple of problems in the source code, and the HTML Documentation.  See Attached file!

10. NOTE: The CNTL C feature of CP/M has now been changed to the ESC key.


ENJOY!

THANK YOU TO MARK GREBE, TIM MANN, AND ALL WHO CONTRIBUTED!

lkraemer
07-30-2011

---

