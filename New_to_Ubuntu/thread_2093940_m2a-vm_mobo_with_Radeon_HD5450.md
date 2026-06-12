---
title: "m2a-vm mobo with Radeon HD5450"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by finechap on 2012-12-12
(Asus) **m2a-vm motherboard with (VTX) Radeon HD5450 graphics** card
Do they work together for Win7 64bit and Ubuntu 12.10 64bit Quantal?

Answer YES but it can be very difficult if done the wrong way!
For the following exposition you will have to forgive any small or large technical knowledge errors, in favour of the final goal.

**Mobo**
The m2a-vm mobo is a cracker from 2007, which takes socket AM2+ CPU's. It has an integrated graphics Radeon X1200 on-board and uses DDR2 RAM. It also has a PCIe x16 (and x1) graphics socket for future [now current] use.

**Irrelevant stuff**
Sadly after buying and then fiddling about with the new graphics card, I noticed that I could have upgraded my graphics by just increasing the amount of memory used by the X1200 to 512MB – too late now though! This is not so obvious because the default mobo setting for graphics memory is AUTO, which then has a tendency to choose 128 or 256MB rather than a more useful 512MB.

**Graphics card**
The radeon hd5450 has DDR3 RAM and I chose the monster with 2GB! It uses a PCIe x16 connection and is specifically for version 2.1 of PCI Express. It comes with a set up CD.
Any PCIe x16 fitting can be used in a x1 fitting [and vice versa], if the socket allows this, because the electronics adjust themselves accordingly. The numbers 16 and 1 refer to the number of (twin) data lanes (or differential signalling pairs) available.
Using a graphics card in a x1 socket is IMHO a waste of effort.

**Irrelevant stuff**
Versions 1 and 2.0 are completely compatible but version 2.1 is not, because of a potential power requirement difference. Luckily this is not too much of a practical problem for the HD5450 because it is a low power unit without a fan – just a heat-sink. There is a slight problem with the DDR3 RAM requiring lower voltages but this can be catered for safely, evidently.

Like the change in disk drive data connections from PARALELL ATA to SERIAL ATA, the old SERIAL AGP [Accelerated Graphics Port] has been replaced by the new PARALELL PCIe connections. This improves the speed of data transmission in itself. Other improvements are achieved by multiplying the connections to 16 pairs, which are simultaneously bi-directional. Further improvements are achieved by the 16 connections into the computer transport being fixed SERIAL logical interconnects; i.e. combining the advantages of both systems.
While the maximum throughput of the data lanes has increased from version 1.0 to 2.1, this makes no practical difference to our graphics card because of the large number of available lanes. Using anything less than an x16 connection would be a big mistake: also as it happens the performance of this graphics card in our version 1.0 slot will miss its possible version 2.1 maximum by an unimpressive 5% (apparently).

**My initial problem**
My mobo was on an earlier bios version from 2009 - no. 2302,  when version no. 5001 from 2010 is required.
The reason that I did not go to no. 5001 previously, is that it has this description “1&#65294; Beta Bios for Supporting AM3 CPUs”. So I wrongly assumed that I would be better off with the AM2 version.
You must change to the latest version.

**Win7**
I dual boot Windows 7 64 bit so I was able to download all sorts of wonderful ASUS software, for updating everything. The major item being ASUS Update V7.17.17 for Windows XP 32bit/XP 64bit/Vista 32bit/Vista 64bit/7 32bit/7 this is a very useful piece of kit to collect and/or update the bios.
I used the ASUS update mechanism to update the mobo. I also downloaded all the other available driver updates to update all other drivers except the VGA driver. This is because we are still running on the on-board graphics, until we fit the new card. I updated the chipset by extracting the relevant files and them running them. This is best done as an Administrator.
I restarted the computer using on-board graphics but then switched to the new card. I had to plug into the D-sub connector because the DVI connector was not working. The graphics were the usual whole grain tiny screen type, found on unconfigured cards. I input the CD which came with the card and ran the whole update.
Unfortunately the update does not work on the unconfigured screens until you change the screen size to 1024 x 768. You have to do this on the main screen, with a right click, otherwise it is impossible to reach the required “Next” button on the update screens!
There are one or two re-starts required before the process is complete.
*Voilà* it is complete and fully functioning. If you are a perfectionist you can update the drivers, using the Device Manager functions.


**Linux**
Available software is slightly restricted for sole Linux users. Unless you can fix the card using a dual boot OS, as above, you will have to follow the following instructions.
 You will need BIOS 5001 from the BIOS section, also BIOS flash tool from the Utilities section. Both of these items are available from the asus website for the mobo.
Now go here:- [http://ubuntuforums.org/showthread.php?t=1574359]("http://ubuntuforums.org/showthread.php?t=1574359")
Make sure that you read all the information on the various posts.
Once you have done all your updating you will be ready to fit the new card. Check the BIOS set up points in the “Important Things to bear in mind” and start your “new” system.
Once your Linux is sorted, you can decide to use the standard graphics driver, or go to the latest version of fglrx, from the repositories or from ATI/AMD.
I personally recommend staying with the resident graphics; there always seems to be on-going maintenance for an fglrx (Catalyst) system.

**Important Things to bear in mind**

[LIST]
[*]Originally the newly set up card may only operate on the D-sub output [a.k.a. VGA output]. Once fully set up it will also be operating on the DVI and HDMI outputs. If you have no screen display, try swapping the plug to the other set of outputs before panicking.
[*]To get into the BIOS set up screen, you need to press the delete key, as soon as the computer boots up and shows the initial screen.
[*]If you are unsure as to how to set any BIOS parameters, then take the default option. Also F5 for all defaults can be used, and then save the changes.
[*]There are 6 bios settings headings: Main, Advanced, Power, Boot, Tools and Exit. We are only concerned with Advanced and Power, although Exit is also used to exit.
[*]Advanced heading, option Chipset: UMA Frame Buffer Size option must be changed to Auto. This is necessary because it decides the amount of RAM used by the on-board graphics.
[*]This amount will change from 128MB, or similar, to 0MB once the mobo changes graphics from on-board to the new card. As mentioned if not using the new card you can change this amount to a fixed amount of 512MB, to get decent graphics performance.
[*]Advanced heading, option Onboard Device Configuration: Primary Display Adapter option must be changed to PCIEx – at all times.
[*]This is so because it will be ignored until there is a functioning PCIEx card installed and ready to use. Since we are changing from a functioning on-board to a new card, it is difficult to know when the new card has been correctly configured.
[*]Without correct configuration the new card will display nothing, whether the monitor is plugged into it or not. With correct configuration the on-board will display nothing, as a result.
[*]Power heading, option APM Configuration: Restore on AC Power Loss must be Power-Off, if you don't want the computer to start without pressing the power button.
[*]Power heading, option Hardware Monitor: Q-fan Controller must be Enabled, if you don't want the computer case fans to attempt to take off.
[*]Exit heading, remember to Save Changes.
[/LIST]

[I]That's better
Release 12.10 (Quantal) 64-bit
Kernel Linux 3.5.0-19-generic
GNOME 3.6.0[/I]

---

### Post by finechap on 2012-12-22
I recently updated to the **kernel 3.5.0-21**, although I don't think that it's relevant.

Since my Win7 was looking good with its AMD/ATI drivers, I decided to update the Linux kernel with the AMD drivers from the AMD/ATI website, as instructed.
**fglrx** version 12.10(AMD version no.) installed properly but when I rebooted, UNITY had disappeared and the driver was not working properly at all. It had in fact reverted to the very basic VESA driver.
This is apparently something to do with the new X server version. Also apparently the Beta version of AMD driver 12.11 works but I will not be bothering until things get back to normal!?

***Luckily*** if you find yourself in the same situation as me, you can very easily revert to the standard Open Source driver [ATI/Radeon] as follows:-

[LIST]
[*]Get the System Settings screen after clicking the top right settings icon.
[*]Select Software Sources and Additional Drivers tab.
[*]Select the AMD/ATI dispaly driver wrapper option and Apply Changes
[*]Logout and back in again
[/LIST]


That's better - what a kerfuffle though.
Release 12.10 (Quantal) 64-bit
Kernel Linux 3.5.0-21-generic
GNOME 3.6.0

---

