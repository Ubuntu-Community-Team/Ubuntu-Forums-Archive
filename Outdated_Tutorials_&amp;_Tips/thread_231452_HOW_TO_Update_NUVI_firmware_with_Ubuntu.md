---
title: "HOW TO: Update NUVI firmware with Ubuntu"
date: 2006-08-07
forum: Outdated Tutorials &amp; Tips
---

### Post by mgmiller on 2006-08-07
This is my first How To, please be kind.

I have a NUVI 350 that I just love.  I use it hiking, biking, boating and in my car and even use it as an MP3 player when bike riding.  Garmin periodically issues updates for the firmware that gives increased functions and fixes bugs.  It is designed to be updated from windows, but with a little setup work, updates just fine with Ubuntu.

[B][U]**Note:  (3 December, 2006) read the end of this post for newest info on nuvi update software & WINE
[/U][/B]
Hardware you will need:
1) A NUVI model with SD card slot (I'm not sure which models have them, mine is a 350, check yours to be sure.)

2) A formatted SD card with at least 40 MB free space on it.  It doesn't have to be empty, just needs the free space.  It is just a standard fat16 formatted card.  Format it in your camera or a friends camera or bring it to the store where they display digital cameras and stick it in one and format it.  You can also format it from the SD card reader in Ubuntu, but I don't know the exact commands. I have a Canon camera that formats it in a few seconds, so I don't need to. 

3) a Card reader for your Ubuntu computer that can read and write SD cards. (internal or external, it doesn't matter.)

In order to get the update file into a usable format, you can do it 2 ways, using wine or from a command line.  I already had wine installed because I needed it for work related compatibility and found it "just worked" for this process.  So first I will discuss a wine install and use for this purpose.  If you don't want to bother with wine, see the **2nd way** below.

**First Way** (using wine)
Next you will need to install wine.  You could probably use the wine from the dapper repositories, but I chose to use the latest wine direct from the 
winehq repos.

First, back up your sources.list
```
sudo cp /etc/apt/sources.list sources.backup
```

Then edit sources.list
```
sudo gedit /etc/apt/sources.list
```

and add the following 3 lines:

**For dapper:**

```
## The wine sources
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
```


**For Edgy:**

```
## The wine sources
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main
```

Save the file in gedit.

As an aside, more info on adding wine sources to ubuntu can be found here:  [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

Next, update your apt and install wine
```
sudo apt-get update
sudo apt-get install wine
```

Or, using the GUI, just run syaptic package manager and tell it to reload (you may have to do this twice), then search for wine.

This should keep your wine updated to the latest release from winehq.

Note: I have not needed to install winetools, (a seperate package installation), it seems to work well without them.

After wine is installed, from the keyboard hit alt F2 and in the dialog box type winecfg.  After a few seconds the wine configuration window will appear.  In the Applications tab, make sure Default Settings is high lighted and at the bottom, where it says Windows Version, select Windows XP.  Click apply and OK.  Close the window.

The wine install creates a hidden directory called .wine in your home directory.  In my case it's /home/marty/.wine  Inside that will be other files and directories, the most interesting one being drive_c.  This is where stuff gets installed to.

A quick tip, navigate to the ~/.wine/drive_c directory in nautilus and then click  bookmarks > add bookmark.  This will put a quick way to get to the drive_c in your Places menu.
 
(.wine like all directories in linux that start with . is a hidden directory.
In order to see your hidden directories in nautilus hit ctrl h,  when you're done hit ctrl h again to rehide them.)

**This is the end of the wine portion, both methods contiue below**

Finally, we are ready to start working with our NUVI.  Just plug in the USB cable that it came with and it should mount and open a window showing its contents.  (This does not use wine, Ubuntu can read and write to the NUVI natively without problems).
If you have firmware older than build 330, you will need to back up your saved addresses and stuff.  It's in the Garmin/Waypoints directory in the NUVI and is called waypoints.gpx.  It's probably a good idea to back this file up anyway from time to time, in case something happens.  Just drag it from your nuvi to a convenient spot on your hard drive (see last tip below).  To restore it, just drag it back to the garmin/waypoints directory, overwriting anything that might be there.

After you have backed up your waypoints file, eject the NUVI from the icon on your desktop, unplug the USB cable and turn it off.

Next, you will download the nuvi update from Garmins web site. [http://www.garmin.com/support/blosp.jsp](http://www.garmin.com/support/blosp.jsp)  and select your model nuvi from the list.

Once you are on the download page make sure you (**don't use Update Unit Software with WebUpdater ** just take the selection from **Unit Software** and again make sure it's the right one for your model NUVI, they may have a few choices for different models listed. 

Download the .exe file to your desktop or anywhere convenient.

**1st Way using wine** (**Make sure to read **updated info for the wine method below)** :mrgreen: 
Just double click it to run it.  It may take a few seconds for wine to wake up, be patient.  You will not have to interact at all with wine, it is invisible in the background. 

The application will open a window and try to find your NUVI, it will fail to detect your NUVI.  That's ok, just exit the program.  It has extracted all the files you need to your .wine/drive_c directory. In my computer it's at: /home/marty/.wine/drive_c/Garmin

This is where the earlier tip about creating the bookmark in your Places menu comes in handy.  
Click on it to go to drive_c, within this directory you will find a Garmin directory, within it is a directory with the name nuvi.  Inside that will be a directory with the number of the update, the current one is 430. Within that directory you will find some files and another directory named nuvi.  Within that directory is a directory named Garmin.  This is the directory that you copy to the SD card. Copy the entire directory, not just the files within it.  The SD card does not have to be blank, it can have other stuff on it, just make sure the Garmin directory is on the root of the SD card.
[B]
2nd way using command line[/B] (Thanks to tlau for this tip)
Create a directory in a convenient location.  It doesn't matter what its name is.  Drop the file you downloaded from the garmin website into that directory.  Open a terminal, navigate to the directory you put the downloaded file into and type unzip filename.exe  
For example, for the 380 update for a nuvi 350 you would type ```
unzip nuvi350_380.exe

```
Several files and 1 directory called nuvi will be created.  Within that directory is a directory named Garmin.  This is the directory that you copy to the SD card. Copy the entire Garmin directory, not just the files within it.  The SD card does not have to be blank, it can have other stuff on it, just make sure the Garmin directory is on the root of the SD card.

Finally, the actual update!
Eject the card from the desktop icon and insert it in the NUVI.
Start the NUVI.  After a bit it will detect the new update and ask if you want to upgrade.  Be patient, it takes a few mins to do the update, the screen may blank or look weird, but it will settle down with the new firmware after a bit.  
Remove the SD card.
That's it.

If you need to, copy the waypoints.gpx file back from your hard drive to the nuvi Garmin/Waypoints directory

For future updates, using wine, you just download the update, double click it, close the app, go to the drive_c/Garmin directory and find the newest update which will be in its own folder based on the name of the update (for example, mine has nuvi350_320 and nuvi350_330 and nuvi350_360 directories, navigate to the garmin directory as above and copy it to the SD card. Start the NUVI with the SD card and tell it yes to the upgrade.

For future updates using command line, just follow the command line instructions again.  

Last tip:
I backup my waypoints.gpx file to the drive_c/Garmin directory so it's easy to find.

Hope this helps, gotta love that NUVI!
[B][U]
**Updated info for the wine method.[/U][/B] :mrgreen: 

If you are using the wine method to update your Nuvi, it just got a lot easier for subsequent updates.  Under the newest version of wine as of 3 December, 2006, in Edgy (don't know about Dapper), you should insert your SD card in your reader and let it mount.  Then run the executable you downloaded from the Garmin web site.  It will correctly identify the SD card and copy the needed files to it and to the Garmin directory in your drive_c directory under wine.  You don't have to do anything else.  Just exit the program, unmount the SD card and stick it in your Nuvi and start it up.  It doesn't get much easier than this!!  (Actually, it might.)  I just tried it with the nuvi connected via USB and the Garmin update software seemed to find the nuvi, identifying it as "nuvi storage device K:" and transfered the software to it.  The only thing that didn't seem to work was the graphic that moves as the files are transfered.  So be patient till it says it's finished. This graphic does work when copying to the SD card. You should also note, I tried this after I had already updated using the SD card method, but it seemed to overwrite that update and on startup, the Nuvi displayed grahics indicating it was updating its internal software.  As an aside, the updates are now very small, averaging around 4 MB, so I have been using a 32 MB SD card I had laying around.

---

### Post by tlau on 2006-08-17
The updater I just downloaded (v3.80) is just a self-extracting zipfile, so you shouldn't need to use Wine to extract the contents.  Just try "unzip nuvi350_380.exe" from a command line.

---

### Post by mgmiller on 2006-08-19
Good point.  I use wine for a lot of other things and it just works for extracting these files.  If you don't need wine, unzipping from terminal works fine too.  The rest of the howto about which directory to copy to the sd card and starting the nuvi with the card inserted is still valid.

---

### Post by mgmiller on 2006-08-28
Based on the tip from tlau, I have updated the HOWTO, to include both wine and command line instructions.  I knew the file was a self extracting zip file, so first I tried using archive manager to look at it, which told me it was unsupported.  I didn't realize we had unzip available from the command line.  Thanks again, tlau.

---

### Post by gcbzzzz on 2008-12-29
to format under ubuntu:

```
$ mount
[...]
/dev/sdc on /media/sdcard type [...]
[...]
```

note: if the mount command already show "type vfat" then you don't need to do anything.

if it shows anything else, note the first part of the line and use on the next commands. mine is "/dev/sdc" your last letter will probably vary.

```
$ umount /dev/sdc
$ sudo mkfs.vfat /dev/sdc
```

---

### Post by kevinm3574 on 2009-06-15
FWIW, you can also just mount the Nuvi as a filesystem to your Linux distro and then copy the .gcd file from the unzip'd update executable directly to <mountpoint>/Garmin and then restart the Garmin.  No need to use the SD card at all.

Kevin

---

### Post by mo7ard on 2009-06-21
Thanks mate, worked with Garmin nuvi 660 :)

First I installed WINE, then I connected the GPS unit, and last I ran the Unit Update File (downloaded from Garmins Support Website). The software recognized the unit as drive D, and made the update all by itself... checked the version in the end and... UPDATED!! :D

---

### Post by frustschieber on 2009-09-08
in console typing "unzip .... .exe" works, but no diredtory is produced. only updater.exe .txt and *.rgn file. none goes with wine.

---

### Post by gcbzzzz on 2011-04-14
Have a problem. my Garmin fried. Now i'm using a chinese one that came with windows mobile 5 and run Garmin XT.

I can use the same maps data i've bought for my old dead garmin.

but the problem is that garmin XT is recoknized via the SD card.

When i try to run the update, the garmin software has no clue that drive E: is a memory card... **how can i force wine to say that some drive is a memory card?**

---

