---
title: "jsymphonic errors during database updating"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by geetriv on 2013-10-20
I have Ubuntu Precise and I have installed jsymphonic. It starts up without any problem, when I try to add or delete any files from the walkman, I get a notice that old database cannot be deleted. Various dat files could not be created. I get the following output in the log file: 
 ```

20 Oct 2013 15:13:36 [INFO]    org.danizmax.jsymphonic.gui.JSymphonicWindow:<init> : Initializing JSymphonic...
20 Oct 2013 15:13:36 [INFO]    org.danizmax.jsymphonic.gui.device.DeviceManager:mountDevice : Mounting the device "PLAYER"
20 Oct 2013 15:13:36 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Initializing database path
20 Oct 2013 15:13:36 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Selected database path is /media/PLAYER/OMGAUDIO
20 Oct 2013 15:13:36 [INFO]    org.danizmax.jsymphonic.gui.JSymphonicWindow:<init> : JSymphonic is ready!
20 Oct 2013 15:13:37 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Initializing database path
20 Oct 2013 15:13:37 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Selected database path is /media/PLAYER/OMGAUDIO
20 Oct 2013 15:13:37 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Initializing database path
20 Oct 2013 15:13:37 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Selected database path is /media/PLAYER/OMGAUDIO
20 Oct 2013 15:13:37 [INFO]    org.danizmax.jsymphonic.gui.device.DeviceManager:refreshDeviceTree : Refreshing the device tree
20 Oct 2013 15:13:43 [FINE]    org.danizmax.jsymphonic.gui.device.DeviceManager:scheduleTrackDeletion : John Coltrane - Summertime
20 Oct 2013 15:13:43 [FINE]    org.danizmax.jsymphonic.gui.device.DeviceManager:scheduleTrackDeletion : John Coltrane - But Not For Me
20 Oct 2013 15:13:43 [FINE]    org.danizmax.jsymphonic.gui.device.DeviceManager:scheduleTrackDeletion : John Coltrane - Everytime We Say Goodbye
20 Oct 2013 15:13:43 [FINE]    org.danizmax.jsymphonic.gui.device.DeviceManager:scheduleTrackDeletion : John Coltrane - My Favorite Things
20 Oct 2013 15:13:43 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Initializing database path
20 Oct 2013 15:13:43 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Selected database path is /media/PLAYER/OMGAUDIO
20 Oct 2013 15:13:43 [INFO]    org.danizmax.jsymphonic.gui.device.DeviceManager:refreshDeviceTree : Refreshing the device tree
20 Oct 2013 15:13:45 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:applyChangesInThread : Exportation started.
20 Oct 2013 15:13:45 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:applyChanges : decodeThread has started
20 Oct 2013 15:13:45 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:applyChangesInThread : Deleting files started.
20 Oct 2013 15:13:45 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:decodeTitlesInThread : decodeThread has finished
20 Oct 2013 15:13:45 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:applyChanges : encodeThread has started
20 Oct 2013 15:13:46 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:encodeTitlesInThread : encodeThread has finished
20 Oct 2013 15:13:46 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:applyChangesInThread : Import files started.
20 Oct 2013 15:13:46 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:applyChangesInThread : Writing database started.
20 Oct 2013 15:13:46 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:applyChangesInThread : Writing database finished.
20 Oct 2013 15:13:46 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Initializing database path
20 Oct 2013 15:13:46 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:initSourcePath : Selected database path is /media/PLAYER/OMGAUDIO
20 Oct 2013 15:13:46 [INFO]    org.danizmax.jsymphonic.gui.device.DeviceManager:refreshDeviceTree : Refreshing the device tree
20 Oct 2013 15:13:46 [INFO]    org.naurd.media.jsymphonic.device.sony.nw.NWGeneric:applyChangesInThread : transferThread has finished

```
No mp3 files have been added or removed. The walkman is  NW-E005F. I find that I am not allowed to make any alterations to the contents of the OMGAUDIO file. Any suggestions?

---

### Post by tgalati4 on 2013-10-20
What version of JSymphonic are you running?  Do you have the correct Sony device selected (Generation 5, NW-E00X)?

I presume that you are running JSymphonic from your walkman by navigating to the root directory of the walkman and double-clicking on jsymphonic.

I do not see any errors in the output so something subtle is going on.  Did you erase all the music on the player first before installing jsymphonic?  It's possible that there are entries in the existing (Sony proprietary) database that jsymphonic won't delete--by design.

Go into Windows and SonicStage and delete all of the old music first.  If you can't stand that agony, then you can just delete all of the files and directories in OMGAUDIO and try rerunning JSymphonic from the root location of the walkman.  That should create a new database and then you can dump your music into the device using drag&drop.

Finally, you can check for bad blocks on your player with the following:

```
sudo badblocks /dev/sdb1
```

It will take a while.

---

### Post by whitesmith on 2013-10-20
Hello and welcome! Try playing some of the files through Rhythmbox or similar. If there's no problem I think your walkman is defective. Wine is another fallback. Good luck.

---

### Post by geetriv on 2013-10-20
```




Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00091676

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   964378623   482188288   83  Linux
/dev/sda2       964380670   976771071     6195201    5  Extended
/dev/sda5       964380672   976771071     6195200   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 2038 MB, 2038171648 bytes
32 heads, 32 sectors/track, 971 cylinders, total 995201 sectors
Units = sectors of 1 * 2048 = 2048 bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          45      994303     1988518    6  FAT16


```

---

### Post by geetriv on 2013-10-20
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00091676

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   964378623   482188288   83  Linux
/dev/sda2       964380670   976771071     6195201    5  Extended
/dev/sda5       964380672   976771071     6195200   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 2038 MB, 2038171648 bytes
32 heads, 32 sectors/track, 971 cylinders, total 995201 sectors
Units = sectors of 1 * 2048 = 2048 bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          45      994303     1988518    6  FAT16

---

### Post by geetriv on 2013-10-20
Problem solved. After a bit of googling I ran the following, unmounting and remounting the player now as rw: 
 ```
sudo mount -o remount,rw '/media/PLAYER' -t vfat 
```
 Specifying the type as noted from a glance at the devices listed in the system monitor. Now I can add and remove music.

---

