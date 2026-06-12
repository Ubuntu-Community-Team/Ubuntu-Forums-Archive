---
title: "HOWTO: TRS-80 Model 1, 3, &amp;4 Emulator - Ubuntu"
date: 2010-09-06
forum: Outdated Tutorials &amp; Tips
---

### Post by lkraemer on 2010-09-06
[B]This HOWTO: will guide you through the process of getting David Keil's
TRS80 (Model3 & 4) or TRS81 (Model 1) EMULATOR running in Ubuntu 10.04
under DOSBox.[/B]

**PREWORK:**
**1.  Purchase the EMULATOR and have it in the mail before proceeding.**
The EMULATOR is provided by, and purchased for $10.00 from:
David Keil 
P.O. Box 143 
Alma Center, WI 54611

It is well worth the modest price he is asking......
David's website is no longer in service.

**2.  Install DOSBox via Synaptics Package Manager**
You will need to install Dosbox in Ubuntu by using Synaptics or apt-get.

REF:
[http://www.dosbox.com](http://www.dosbox.com)
[http://dosbox.sourceforge.net/wiki](http://dosbox.sourceforge.net/wiki)


**3. Copy the complete EMULATOR subdirectory from CDR to your /home/loginuser directory**
Copy the complete folder **TRSDOS** from the CDR to /home/loginuser


**4. DOSBox - Command Summary**
The following commands can be used in DOSBbox:
intro
intro mount
intro cdrom
intro special
help
help /all

CNTL F11 Slow down Emulation - Decrease DOSBox Cycles
CNTL F12 Speed up Emulation - Increase DOSBox Cycles
ALT-ENTER go FULL Screen & Back

There are several special commands that are shown on the help screens.


**5. TRS80 - Command Summary**
The following three commands apply ONLY to Montezuma Micro CP/M:
F1 does a DIR A:
F2 does a DIR B:
F3 does a DIR M:

F5 key brings up the 'Configuration Screen'.
Shift F5 key will shell to DOS.

F6 key toggles 1, 2, 4, 8 MHZ
Shift F6 Locks the Speed at the current setting.

F7 key will save a snapshot of the TRS-80 system.
Shift F7 key will load a snapshot of the TRS-80 system allowing you to
continue running a TRS-80 program after exiting the emulator. Like a save game feature.

Added ability to load & execute /CMD files directly from a PC directory
use Shift F7 to bring up "load Snapshot" window then use F1 to toggle
load /CMD options

F9 will bring up the virtual drive status screen. From this screen you
can insert, remove and change virtual disks.
Shift F9 selects virtual hard disk selection screen.

In the virtual drive selection screens have changed.
   Pushing INSERT now brings up a window for entry of a path+filename of a
      virtual disk to be mounted in the currently selected drive.
   Pushing ENTER brings up the point & shoot screen for selecting a virtual disk to be mounted in the currently selected drive. (same as before)
   Pushing the numbers 0-3 now selects the corresponding drive.
   Pushing Shift-Tab selects the previous drive.

F10 Reset Emulator (Same as CNTL C in CP/M)
Shift F10 now exits even if CPU is stopped.

F11 now selects virtual cassette selection screen.
Shift F11 selects audio/wave cassette selection screen.

F12 stops & single steps Z80 CPU.
Shift F12 stops and restarts Z80 CPU.


**6. Testing DOSBox commands and methods.**
Let's use this example as a guide for the commands we will need to
use to mount and unmount the directory.

I had several recipes that were saved in C:\pw\2_LDK\Cookin on an
old Dos machine. I copied the complete C:\pw folder to /home/larry/C:/.
This folder will be mounted as C: Drive in DOSBox so the EXE, COM, or BAT
files can be executed. To mount your C: drive, you will use the mount
command to mount the Linux folder as c and then change to Drive C:\> and
execute your old DOS Program.

I executed DOSBox from the Ubuntu menu.

Start DOSBox via:
APPLICATIONS -> GAMES -> DOSBox

When the dosbox window opened I typed the following to mount a SUBDIRECTORY as Drive C.  So, when I change to Drive C,
I am really pointing at /home/larry/pw

DOSBox positions you at Drive z:
```

mount c ~/C:
C:
dir/p
cd pw
pw

```

From within pw I just used a normal program exit.

Before you can unmount the drive you must change back to drive z:
then you can issue the unmount command.
To UNMOUNT C: and exit DOSBOX use the following commands:
```

z:
mount -u c
exit

```


Locate the .DSK or .DMK (NEWDOS, DOSPLUS, LDOS, TRSDOS, ULTRADOS, MULTIDOS, or MONTEZUMA MICRO CP/M) OS files you will use:
(If you are using Montezuma Micro 2.31 CP/M, use Tim Mann's mkdisk to reset the write protect attribute of the file, so you
can use CONFIG to change the Drive Parameters and save the settings. If you don't change the file to unprotected, you won't
be able to save the parameters so the settings won't survive a reboot.  If you are using Newdos and want to use the Pdrive
command you will also need to use Tim's mkdisk to allow the Pdrive command to write the changes.
TYPICAL Pdrive commands are:
pdrive,0                   //This will display the current settings
pdrive,0,1=4,a             //This will change Drive 1 to displayed Drive 4 settings and make it effective immediately
pdrive,0,1=2,a             //This will change Drive 1 to displayed Drive 2 settings and make it effective immediately
These parameters allow you to read a Model 1 Floppy in a TRS-80 Model III or Model 4)
```

mkdisk -u -k filename.dmk
mkdisk -u -k MMCPM231.DSK
mkdisk -u -k ND80-M1.DSK

```


**7. Running TRS80 (Model 3 & Model 4 Emulator) or TRS81 (Model 1 Emulator)**
Start DOSBox via:
APPLICATIONS -> GAMES -> DOSBox

DOSBox will come up and you will be on Drive z:
(Type the following commands adjusting for the specific Emulator.) 
```

mount c TRSDOS
c:
dir /p
trs80 MMCPM321.DSK

```
(I copied the Monetzuma Micro CP/M DSK file into the TRSDOS subdirectory.  You could have just used
trs80, and then immediately used F9 to select the Drive, and the OS used on that drive, and then used F10
to read the Disk's information and reset the Emulator.)
Use CNTL F12 to increase cycles to around 9K or 10K so the "DIR B:" command in CP/M, or the "DIR :0"
command in TRSDOS acts like a real TRS-80 Model 4.

Montezuma Micro ver 2.3.1 will come up running.

MY OH MY, Formatting a disk takes about 30 seconds, and booting up is less than 30 seconds.........
That was the good ole days....and the CPU speeds were 2 MHZ with 64 or 128 Meg RAM. WOW!

Use F9 to configure another DSK file to view in Drive :1
Use F10 to RESET the System

Use PIP to transfer a couple of files to Drive M:.  (pip destdrive:=sourcedrive:filename.*)
```

pip m:=a:mdm730*.*

```
F1 does a DIR A:
F2 does a DIR B:
F3 does a DIR M:

F5 key brings up the 'Configuration Screen'.
Shift F5 key will shell to DOS.

F6 key toggles 1, 2, 4, 8 MHZ
Shift F6 Locks the Speed at the current setting.

F7 key will save a snapshot of the TRS-80 system.
Shift F7 key will load a snapshot of the TRS-80 system allowing you to
continue running a TRS-80 program after exiting the emulator. Like a save game feature.

Added ability to load & execute /CMD files directly from a PC directory
Use Shift F7 to bring up "load Snapshot" window then use F1 to toggle
load /CMD options

F9 will bring up the virtual drive status screen. From this screen you
can insert, remove and change virtual disks.
Shift F9 now selects virtual hard disk selection screen.

In the virtual drive selection screens have changed.
   Pushing INSERT now brings up a window for entry of a path+filename of a
      virtual disk to be mounted in the currently selected drive.
   Pushing ENTER brings up the point & shoot screen for selecting a virtual
      disk to be mounted in the currently selected drive. (same as before)
   Pushing the numbers 0-3 now selects the corresponding drive.
   Pushing Shift-Tab selects the previous drive.

F10 Reset Emulator (Same as CNTL C in CP/M)
Shift F10 now exits even if CPU is stopped.

F11 now selects virtual cassette selection screen.
Shift F11 selects audio/wave cassette selection screen.

F12 stops & single steps Z80 CPU.
Shift F12 stops and restarts Z80 CPU.

So, the whole world of CP/M, TRSDOS, LDOS, NEWDOS along with all the others is now
available for your work or play.  Be sure to check out DUP, and CONFIG, in Montezuma Micro CP/M
and all the other nice utilities from the CP/M and TRSDOS Days back in the 1980's.
With Config you can read and write almost any format available at that time.  

When you are finished with the Emulator use SHIFT F10 to exit.  Then you need to
unmount the subdirectory and exit the Terminal Window.  Here are the commands
```

z:
mount -u c
exit

```
If DOSBox doesn't terminate properly, open another Terminal Window and use the top
command to find the DOSBox process ID Number.  Assume 4790.  Use CNTL C to stop the
top command and then use kill -9 4790 to terminate DOSBox.
```

top

```
CNTL C
```

kill -9 4790

```


**HOW TO COPY THOSE OLD 5.25" FLOPPY'S USING THE CATWEASEL PCI CARD:**
The Catweasel MK4 PLUS is a multi-format floppy disk controller PCI Card that can
be plugged into a spare PCI slot, and used from a Terminal Window in Ubuntu.
I plugged mine in my Desktop running 8.04.4 LTS.

**CATWEASEL FEATURES:**
Read/write real Amiga floppy disk's on a Windows PC
Use a real Amiga keyboard on a PC
Use a real Amiga mouse/joystick on PC
Ideal for WinUAE and Amiga Forever - transfer all your Amiga floppies over to the PC
Empty SID chip socket for realistic C64 sound emulation

**Third Party Support**
Catweasel MK4 drivers for classic Amiga available:
Multidisk V3.65 uses OpenPCI to access the controller through the Prometheus PCI Busboard.
Third party driver support for Linux 2.6 also available
Third party driver support for AmigaOS 4.1 now also available (limited)
Third party driver support for AROS now also available

I purchased my Catweasel from:
[http://amigakit.leamancomputing.com/catalog/product_info.php?products_id=842](http://amigakit.leamancomputing.com/catalog/product_info.php?products_id=842)

Tim Mann has a nice website with support for the CP/M and TRS-80 Floppy Disks at:
[http://www.tim-mann.org/trs80.html](http://www.tim-mann.org/trs80.html)
[http://www.tim-mann.org/catweasel.html](http://www.tim-mann.org/catweasel.html)

From Tim's website you can download his Catweasel Floppy Read/Write Tools, version 4.4 
cw2dmk-4.4.zip or cw2dmk-4.4.tar.gz and extract the folder containing his files for
version 4.4.

**LINUX:**
From within my Desktop running Ubuntu 8.04, I just opened a Terminal Window, and used the following commands:
```

cd ~
cd cw2dmk-4.4
sudo ./cw2dmk -v1 trstst01.dmk
sudo ./cw2dmk -v1 trstst02.dmk
sudo ./cw2dmk -v1 trststxx.dmk

```to copy the TRS-80 floppy disks to the DMK image format that is used by most Emulators.

**WINDOWS:**
There are Windows Drivers on the Catweasel CDR along with other Software, but I haven't
looked into that so far.

**WARNING - UNAPPROVED METHOD:**
One CAUTION here is that if your Floppy Disk's are 25+ years old as mine were, the
Oxide coating on most of the floppy's are ready to fail, and you may ruin them by trying
to read them.  (You may find that a tiny bit of Alcohol placed on a cotton swab will
totally remove all the Oxide coating from the platter making then unreadable, so DON'T
try Alcohol as a cleaner or lubricant for your floppy's.)  Also, the inner lining of the
old Floppy's have lost their lubricating ability by becoming dry over the years, and this
causes DRAG on the heads as the platter tries to spin so the read heads can recover the data.
I chose use a lubricant from KANO LABS in Nashville, TN called Aerosol "SiliKroil" to lubricate
my floppy's. I was able to recover about 85% of the disks using this TOTALLY UNAPPROVED method.
I ruined the first 4-5 disks by trying to read them.  A costly ERROR!
[http://www.kanolabs.com](http://www.kanolabs.com)
SiliKroil is an Industrial Penetrating Lubricant that works wonders, and doesn't remove
the Oxide coating as Alcohol and Silicone does.  Alcohol can be used to clean the Floppy
Drives read heads as usual. 

**COPYING AMPRO DS/DD DISKS - Using a real bootable Ampro system**
Since I had the Catweasel installed, and I had 26 Ampro disks in a mix-n-match of
SS/DS & DS/DD, I wanted to try and save all the information from these 5.25" disks.
I read each disk several times with my Catweasel card making multiple attempts
at good reads.  Examples for Disk #8 are:
```

sudo ./cw2dmk ADSDD008.DMK
sudo ./cw2dmk ADSDDa08.DMK
sudo ./cw2dmk ADSDDb08.DMK
sudo ./cw2dmk ADSDDc08.DMK
sudo ./cw2dmk ADSDDd08.DMK

```
This gave me an option of trying more than once at recovering the files as the multiple
reads found different sectors bad for successive sequential reads.  A step that was very
valuable as I proceeded.

Since I had a System that contained two 5.25" TEAC 360K drives, I booted my Ampro SS/DD CP/M
system disk and used AMPRODSK to FORMAT a FRESH DS/DD Disk, and used SYSGEN to copy the System.
Next I used NSWEEP to copy all the files.  Now I have a good bootable DS/DD Boot SYSTEM Disk.
Next I used Catweasel to WRITE my first Disk 08 Image (ADSDD008.DMK) to a fresh Floppy with:
```

sudo ./dmk2cw ADSDD008.DMK

```
I inserted that disk in my Drive after running NSWEEP.  NSWEEP was used to LOG the New Disk,
and to copy it to my PURGED DS/DD CP/M Disk.  If the file copying had bad sectors for specific
File Names, I made a note of those errors for attempt #2 by using ADSDDa08.DMK, then a third
attempt using ADSDDb08.DMK........etc.

When all the files were successfully copied I used my Catweasel to create a new Image of this disk,
renaming it ADSDD008.DMK with:
```

sudo ./cw2dmk ADSDD008.DMK

```
  
Then, I just repeated the process for the 26 Disks I had saved...........
Unfortunately, Disks 1, 2, &3 were ruined in the process, but gave me the UNAPPROVED
METHOD noted above.

When all the disks had been gone through I burned a DVD of all the Images, with each disks'
images in a separate folder just in case I needed to try and recover a file at a later date.

This method should also work for you on any CP/M System, such as Kaypro II or IV, Ampro,
TRS-80 Model 1, 3, & 4, or by using Virtual Disks in an Emulator.


**WANT TO USE 3.5" DRIVES WITH YOUR OLD COMPUTER - SEE THE ATTACHED PDF's!**

 
**PM** me if you have questions, or need help.

lk

---

