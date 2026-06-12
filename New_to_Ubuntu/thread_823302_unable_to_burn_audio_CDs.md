---
title: "unable to burn audio CDs"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by rockerphil on 2008-06-09
ok, i've been racking my brain for almost 3 weeks trying to figure this out. first a bit of info on the system. i'm running a minimulist install built from the Ubuntu 7.10 minimal ISO from which i installed a CLI and then installed the x windows system (xorg) Fluxbox as my window manager, ROX as my filer and of course Firefox as my browser. well now to the problem. i recently replaced my ancient CD ROM drive with an IDE-CD R/RW 4x4x32 drive, and i can burn data disks (distros and things of the like) but i can't seem to get it to burn audio CDs. k3b says it doesn't support mp3 formats, Brasero doesn't detect the blank CD and Gnomebaker will only let me put 4 or 5 tracks on the list before telling me that the next file is too large to fit on the rest of the medium. any suggestions guys? oh, and i'm not afraid to use the terminal. thanks in advance


Phil

---

### Post by cariboo on 2008-06-09
If you install libk3b2-extracodecs you will be able to burn all the music cd's you want with k3b.

Jim

---

### Post by rockerphil on 2008-06-09
ok, i can now handle mp3s with k3b. but when i try to burn an audio CD i get this debugging output


System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
IDE-CD R/RW 4x4x32 C18a (/dev/scd0, /dev/sg1) [CD-R, CD-RW, CD-ROM] [Error] [TAO, RAW, RAW/R16]

Used versions
-----------------------
cdrdao: 1.2.2

cdrdao
-----------------------
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty
Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.
Using libscg version 'ubuntu-0.8ubuntu1'
/dev/scd0: IDE-CD R/RW 4x4x32 Rev: C18a
Using driver: Generic SCSI-3/MMC (raw writing) - Version 2.0 (options 0x0000)
Starting write at speed 2...
Process can be aborted with QUIT signal (usually CTRL-\).
WARNING: Cannot write CD-TEXT data because the 96 byte raw P-W sub-channel data mode is not supported.
WARNING: Ignored because of --force option.
Using 16 byte P-Q sub-channel data mode.
Executing power calibration...
Power calibration successful.
WARNING: No super user permission to setup real time scheduling.
Writing lead-in and gap...
ERROR: Write data failed.
ERROR: Writing failed.

cdrdao command:
-----------------------
/usr/bin/cdrdao write --device /dev/scd0 --speed 2 -n -v 2 --force --eject --remote 32 /tmp/kde-phil/k3b_audio_0_.toc

---

### Post by andrew.46 on 2008-06-11
Hi,

Perhaps eliminate the gui and test from the command line:

[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

   Andrew

---

