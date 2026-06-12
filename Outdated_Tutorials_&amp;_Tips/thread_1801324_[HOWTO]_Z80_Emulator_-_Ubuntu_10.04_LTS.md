---
title: "[HOWTO] Z80 Emulator - Ubuntu 10.04 LTS"
date: 2011-07-10
forum: Outdated Tutorials &amp; Tips
---

### Post by lkraemer on 2011-07-10
**HOWTO: Z80 Emulator - Ubuntu 10.04 LTS**

This HOWTO: will guide you through the process of getting MYZ80 by Simeon Cran running
on Ubuntu 10.04 under DOSBox.

**PREWORK:**
1. Locate the myz80.zip and extract the contents to a folder named Z80-Sim.
   [http://www.z80.de/myz80.zip](http://www.z80.de/myz80.zip)

2. Install DOSBox via Synaptics Package Manager

**REF:**
[http://www.dosbox.com](http://www.dosbox.com)
[http://dosbox.sourceforge.net/wiki](http://dosbox.sourceforge.net/wiki)

3. Read the Documentation in the Z80-Sim Subdirectory.

4. DOSBox - Command Summary
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


5. Testing DOSBox commands and methods.
Let's use this example as a guide for the commands we will need to use to mount
and unmount the directory.

I had several recipes that were saved in C:\pw\2_LDK\Cookin on an old Dos machine.
I copied the complete C:\pw folder to /home/larry/C:/.  This folder will be mounted
as C: Drive in DOSBox so the EXE, COM, or BAT files can be executed. To mount your C:
drive, you will use the mount command to mount the Linux folder as c and then change
to Drive C:\> and execute your old DOS Program.

I executed DOSBox from the Debian menu.

Start DOSBox via:
APPLICATIONS -> GAMES -> DOSBox

When the dosbox window opened I typed the following to mount a SUBDIRECTORY as Drive C.
So, when I change to Drive C, I am really pointing at /home/larry/pw

DOSBox positions you at Drive z:

```

    mount c ~/C:
    C:
    dir/p
    cd pw
    pw

```

From within pw I just used a normal program exit.

Before you can unmount the drive you must change back to drive z: then you can issue
the unmount command.  To UNMOUNT C: and exit DOSBOX use the following commands:

```

    z:
    mount -u c
    exit

```


6. Running Z80 Emulator
Start DOSBox via:
APPLICATIONS -> GAMES -> DOSBox

DOSBox will come up and you will be on Drive z:
(Type the following commands adjusting for the specific Emulator.)

```

    mount c ~/path/to/Z80-Sim
    c:
    dir /p
    myz80

```

There are two commands (IMPORT.COM & EXPORTCOM) that allow you to import and export files
into the DSK images.  I wanted to use Nulu12 and Nsweep because those were not included.
I found the files on the Internet, but I needed to extract them from a LBR file.
That led to a search for UNARC16.ARK.  I found the file and finally found instructions
about just renaming it to UNARC16.COM, and then executing the file since it was a
Self Extracting type file.  That allowed me to extract Nulu12 and Nsweep from some of
the ARC type files.  Then I just imported Nsweep.com and Nulu12.com into the Z80 Emulator.
That allowed me to search more LBR files, including the myz80com.lbr file.

Other Z80 CP/M Commands:
```

dir
dir B:
user 1
dir B:
user 2
dir C:
user 0
dir
CNTL C is used to reload the Disk Directory

```

So, the whole world of CP/M is now available for your work or play.  Be sure to check out all
the other nice utilities from the CP/M Days back in the 1980's.


When you are finished with the Emulator use EXIT to exit. Then you need to unmount the
subdirectory and exit the Terminal Window. Here are the commands.

```

    z:
    mount -u c
    exit

```


If your Terminal should hang, you can do the following to stop the process and close the Terminal.
```

top
CNTL C

```

Look for the Process number associated with DosBox. Assume 6545.  Use the following command to
Terminate the Process.

```

kill -9 6545

```


**REF: for CP/M Archives**
[http://z80cpu.eu/mirrors/oak.oakland.edu/](http://z80cpu.eu/mirrors/oak.oakland.edu/)


**OTHER VALUABLE REFERENCES:**
HOWTO: Use DOSBox - Ubuntu
HOWTO: TRS-80 Model 1, 3, & 4 Emulator - Ubuntu
HOWTO: XTRS - TRS-80 Model 1, 3, & 4 Emulator - Ubuntu 


Larry

---

