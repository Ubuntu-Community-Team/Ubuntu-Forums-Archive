---
title: "OziExplorer GPS Software"
date: 2006-07-07
forum: Outdated Tutorials &amp; Tips
---

### Post by ruiruas on 2006-07-07
Hi,
I succeeded in making OziExplorer work, apparently with all features... Full Procedure:

1.Install "Wine" (I followed the instructions in the "ubuntu user documentation" to get the latest version):
First, in Synaptic, add the following repository 

      deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

Then, reload, update, and install wine
When you first run wine, it will create a .wine directory in you home dir. Inside it, will be a "drive_c" that simulates the windows environment.

2. copy the file "oziexp_setup. exe" to ~/.wine
I tried but it didn't run from another location.

3. In the terminal, change to the ".wine" directory, where oziexp_setup.exe is (~/.wine/)

3. Run the ozi installation file with wine. In the terminal, type:

      wine oziexp_setup.exe

The setup will install Oziexplorer under ~/.wine/drive_c/OziExplorer/
(if you have any trouble here with permissions, try running wine with "sudo". type: "sudo wine oziexp_setup.exe")
The program won't run just yet...

Thanks to Stephen B, in the "WineHQ" (on Tuesday November 8th 2005) the initial crash problem is solved:
Under ~/.wine/drive_c/OziExplorer/, edit the file "oziexp.ini", adding the following lines (It disables the tooltips at the start):

      [Help]
      Show Start=0
      Getting Started=0

4. Now it works! (at least it should...)
We just have to setup the gps... Apparently, serial comunication works fine, but I can't guarantee it because my GPS connects through USB.
If your GPS connects through serial COM, you must only remember that in linux, COM1=/dev/ttyS0, COM2=/dev/ttyS1, etc.
In the case of USB connection, I use a "Garmin GPS60". Gamin drivers are already built into Ubuntu kernel, so Linux should recognize the device.
After connecting the GPS, run "dmesg" to find out: you should see lines like these:
.....
[17193444.360000] usb 1-3: new full speed USB device using ohci_hcd and address 4
[17193444.560000] garmin_gps 1-3:1.0: Garmin GPS usb/tty converter detected
[17193444.560000] usb 1-3: Garmin GPS usb/tty converter now attached to ttyUSB0
.....

The problem is OziExplorer doesn't recognize "/dev/...", so we can get around the problem making a "sym link" from "COM to USB". I chose COM3 to avoid interference with other things (COM3=/dev/ttyS2).
In the terminal, type:

      sudo ln -sb /dev/ttyUSB0 /dev/ttyS2

(the "b" option makes a backup copy of ttyS2 in case you want to "get back")
After that, you must start Oziexplorer by typing: 

      wine ~/.wine/drive_c/OziExplorer/OziExp.exe

In "Ozi", go to the menu "File" > "Configuration" > "GPS" and choose your GPS make and model.
Then, under "COM" choose COM3, leave the "Garmin USB" or other UNCHECKED (this way, the software "thinks" the GPS is under COM3...)
SAVE the configuration and exit.

6. ITS DONE!!! By now, you must be able to comunicate to and from the GPS, and have Oziexplorer working just fine!

I hope this will help someone...

---

