---
title: "new CD burner will burn distros but not audio discs"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by rockerphil on 2008-06-02
ok. first off here's what i'm running. i installed a minimal desktop environment from the minimal Ubuntu 7.1 Gutsy Gibson CD by first installing a CLI then instaling the x windows system with "sudo apt-get install xorg" then makin the IceWM my window manager with "sudo apt-get instal icewm" thus creating a graphical user interface for my desktop. well i've pretty much got my "custom OS" as i call it set up. except for one problem. i recently replaced my ancient CD ROM drive with an IDE CD R/RW 4x4x32 drive. well i can burn ISO files just fine through any of the major burning programs, but i can't burn audio CDs for my car (an old a$$ 98 astrovan) when i try to burn an audio CD through my fave burning app it acts like it's starting to burn, it'll get to where it says it's 11% done with burning the first track, and then i get this debugging output


System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
IDE-CD R/RW 4x4x32 C18a (/dev/scd0, ) [CD-R, CD-RW, CD-ROM] [Error] [TAO, RAW, RAW/R16]

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
Starting write at speed 4...
Process can be aborted with QUIT signal (usually CTRL-\).
Using 16 byte P-Q sub-channel data mode.
Executing power calibration...
Power calibration successful.
WARNING: No super user permission to setup real time scheduling.
Writing lead-in and gap...
Wrote 1 of 25 MB.
Wrote 2 of 25 MB.
Wrote 3 of 25 MB.
Wrote 4 of 25 MB.
Wrote 5 of 25 MB.
Wrote 6 of 25 MB.
Wrote 7 of 25 MB.
Wrote 8 of 25 MB.
Wrote 9 of 25 MB.
Wrote 10 of 25 MB.
Wrote 11 of 25 MB.
Wrote 12 of 25 MB.
Wrote 13 of 25 MB.
Wrote 14 of 25 MB.
Wrote 15 of 25 MB.
Wrote 16 of 25 MB.
Wrote 17 of 25 MB.
Wrote 18 of 25 MB.
Wrote 19 of 25 MB.
Wrote 20 of 25 MB.
Wrote 21 of 25 MB.
Wrote 22 of 25 MB.
Wrote 23 of 25 MB.
Wrote 24 of 25 MB.
Wrote 25 of 25 MB.
Writing track 01 (mode AUDIO/AUDIO )...
Wrote 1 of 775 MB (Buffers 100%  98%).
Wrote 2 of 775 MB (Buffers 100%  98%).
Wrote 3 of 775 MB (Buffers 100%  98%).
ERROR: Write data failed.
ERROR: Writing failed - buffer under run?
ERROR: Writing failed.

cdrdao command:
-----------------------
/usr/bin/cdrdao write --device /dev/scd0 --speed 4 -n -v 2 --force --eject --remote 31 /tmp/kde-phil/k3b_audio_0_.toc

and just so you know i'm burning this in k3b with the mp3 plugin


can anyone help me on this? cus i'm lost

---

### Post by rockerphil on 2008-06-02
bumpin this back up, i could really use some help on this guys, i've been workin on this problem for 2 weeks now

---

### Post by HunterThomson on 2008-06-02
what burning program are you using?

---

### Post by rockerphil on 2008-06-02
k3b

---

### Post by mcduck on 2008-06-02
Have you tried with some other burning app? Give Brasero or Gnomebaker a try..

---

### Post by HunterThomson on 2008-06-02
Ya what troubleshooting have you done? Try running a BackTrack3 on USB and then burning an cd in k3b in that OS i.e. there is no problem with the hardware.... If the hardware is fine you mite try changing settings... Then make sure you have all the dependence.

---

### Post by cariboo on 2008-06-02
Check the burn speed. If its set for automatic, change it to 2X, that should get you something more than a coaster.

Jim

---

### Post by rockerphil on 2008-06-02
ok, first off, i've tried all of the major burning software, and i've got them isntalled, do you want the error messages for Breasre, k3b and gnomebaker? cus i'll post them. and secondly, i've met all dependencies. and i've tried setting burn speed to the minimum

---

### Post by HunterThomson on 2008-06-02
> **rockerphil said:**
> ok, first off, i've tried all of the major burning software, and i've got them isntalled, do you want the error messages for Breasre, k3b and gnomebaker? cus i'll post them. and secondly, i've met all dependencies. and i've tried setting burn speed to the minimum

Try using a different OS like BackTrack3 Linux on a USB drive....

That BT3 USB is a really good thing to have sitting next to your computer I use it all the time:)

---

### Post by rockerphil on 2008-06-02
i can't boot from a USB device, any other suggestions?

---

### Post by rockerphil on 2008-06-02
did i find a problem that the Ubuntu forums can't solve?

---

### Post by billgoldberg on 2008-06-02
I doubt it, the right people just have to read it.

I'm not one of them.

---

### Post by rockerphil on 2008-06-02
ok, sorry bout the late response, but i decided to go to sleep rather than chunk my only PC out a window. so i'm gonna bump this back up and see if i cn get this problem solved

---

### Post by andrew.46 on 2008-06-03
Hi:

I can sense some frustration here:

> **rockerphil said:**
> ok, sorry bout the late response, but i decided to go to sleep rather than chunk my only PC out a window. so i'm gonna bump this back up and see if i cn get this problem solved

Can I suggest, if your PC has not actually gone through the window, that you try cdrdao itself rather than through k3b? I have done some work on this:

[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

which may prove useful. The error message that you quoted speaks of buffer under-run and you will find that this is easily adjusted on the command line with --buffers or in the cdrdao.conf file by adjusting write_buffers and write_speed. Mind you the settings I give on this page should be adequate.

I have always found cdrdao to be a very robust program but I don't believe this is always true of k3b.

         Andrew

---

### Post by Ptero-4 on 2008-06-12
the cdrtools (or cdrkit) command does have IIRC an option to turn on the buffer-underrun prevention (in your k3b log it seems like the feature was off).

---

### Post by hyper_ch on 2008-06-12
did you try to write the cd first as image to your harddisk? Does that work?

---

