---
title: "Mounting ZEN Stone Plus"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by laurielegit on 2008-11-19
I've just bought a new Zen stone and naturally, I want to put some music on it. When I plug it into my Ubuntu desktop it comes up as a USB stick that will not mount. If anyone can show me how to mount it I would appreciate that a lot. Also being able to connect it to Amarok would be very useful.
By the way, I am using Ubuntu 8.10 and this is a 4gb Stone, previously used with windows.

---

### Post by Tom.Servo on 2008-11-19
Are you able to mount any other external USB drives, such as a USB flash drive?

---

### Post by laurielegit on 2008-11-19
Yes, I can mount my ipod correctly.

---

### Post by Tom.Servo on 2008-11-19
Ok found this on a search:
[I][B]
"I've also bought a Zen Stone and tried connecting it to Ubuntu Feisty powered laptop. At first it didn't get recognized. I had to reset the device (using the mini reset button), after that it mounted automatically just like any external USB drive.
FYI, you can use whatever directories you like, no need for the MUSIC folder... there's a button to skip folder and play next -> you can sort music by albums, artist, etc."[/B][/I]

and/or this:

[I][B]"1. Plug it in and let it be discovered as a device on the system. (found but not mounted)
Remember the device path that the system creates for you /dev/sd??
For this example lets use /dev/sdh1
Note: At this stage if you have Amarok running, Amarok may pop up a screen to let you know that it has detected a device. However if you try to connect to the device Amarok will provide you with a message saying "Cannot to connect to the device".

2. Mount the Stone player rw available to which users (uid) or user group (gid) you want. I couldnt get this to work from the command line.
So I put this into my "/etc/fstab" file.
The options I chose where:
/dev/sdh1 /mnt/stone vfat noatime,auto,users,uid=1000,gid=100,umask=007 0 0
Note: I have included both uid and gid in my example but you may not need both if you dont desire.

3. Open a terminal and execute
sudo mount -a
to mount your player.

Note: I got this solution from a similar problem I had with SD cards mounting read only (ro).
I could never work out how to get this command to work correctly from the command line, as it kept mounting the device with "root" as the owner and the Stone player read only.
Sometimes its just best to stick to what you know.

4. Go into the Amarok settings --> Configure Amarok --> Media Devices
You will see a list of devices including your /dev/sd??.
For the plugin option (next to your device) choose : "Generic media player".
Note: I tried the other plugin options with no success.

5. Click on the cogs next to the plugin options to enter the "Configure device settings"
Change the Song Location to something like
/%artist_%album_%track_%title.%filetype
Basically you dont want to create subdirectories (subfolders) as I believe the Stone player simply wont find them. So you want to put all files under "/" (your first directory).
I use the %artist_%album_%track_%title.%filetype format to keep all my files seperated. But play around with this and see what you like.
Following the example your resulting "Example Song Location" should be something like this
"/mnt/stone/The One Artist_Some Album_01_Some Title.mp3"
Click OK to close the window.
Edit: I later discovered that you can create one level folders under "/" and use the Folder Skip button on your Stone player to change folders. So you play around with the Song Location setting and create different folders for each album.

6. Click Apply. Note: At this stage my Stone player was detected by Amarok and connected without request, this may not happen for everyone.
Click Ok to close the window.

If your device has not automatically connected.
In the main Amarok window click on the Devices tab. From the top of the window select Generic Audio Player /dev/sd?? and then click on the connect option. Now you can transfer your music using Amarok.

7. When your done, disconnect in Amarok. Then from the desktop, select your player icon and chose "safely remove" or umount via a terminal."[/B][/I]

---

### Post by laurielegit on 2008-11-19
Neither of these things work. I cannot mount my stone. *That* is the bottom line. Can anyone give me a step by step guide to manually mounting my stone.

---

### Post by laurielegit on 2008-11-19
More info. sudo fdisk -l returns the following:

```
laurie@Edgar:~$ sudo fdisk -l
[sudo] password for laurie: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05740573

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12158    97659103+  83  Linux
/dev/sda2           12159       38913   214909537+   5  Extended
/dev/sda5           38165       38913     6016311   82  Linux swap / Solaris
/dev/sda6           12159       18237    48829504+  83  Linux
/dev/sda7           18238       19210     7815591   83  Linux
/dev/sda8           19211       19222       96358+  83  Linux

Partition table entries are not in disk order
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 7952 MB, 7952142336 bytes
217 heads, 32 sectors/track, 279 cylinders
Units = cylinders of 6944 * 4096 = 28442624 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         280     7765508    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 32)
Partition 1 has different physical/logical endings:
     phys=(120, 216, 32) logical=(279, 126, 32)

Unable to read /dev/sdc
laurie@Edgar:~$ 

```

I think /dev/sdc is my stone as sdb1 is my ipod and the rest is my internal hard drive.

---

### Post by Tom.Servo on 2008-11-19
> **laurielegit said:**
> Neither of these things work. I cannot mount my stone. *That* is the bottom line. Can anyone give me a step by step guide to manually mounting my stone.

Wow. Sorry for trying to help. The guide(to an extent) I copied and pasted has helped me with misbehaving MP3 players in the past. Especially those with MTP/MSC differences. But anyway, good luck with your bottom line.

---

### Post by olejorgen on 2008-11-19
Strange.. my Zen Stone Plus 4GB mounts fine.
```

sudo mount /dev/sdc1 /mnt/zen -o uid=ole

```
is what I do. (unless I have automounter active)

Replace sdc1 with whatever the device node is.

```

Unable to read /dev/sdc
```
That's doesn't sound good. Are you sure it mounts cleanly in windows? (now)

You could try to reset the Stone. It sould be a small "pen button" somewhere that does it.

---

### Post by laurielegit on 2008-11-19
> **olejorgen said:**
> Strange.. my Zen Stone Plus 4GB mounts fine.
```

sudo mount /dev/sdc1 /mnt/zen -o uid=ole

```
is what I do. (unless I have automounter active)

Replace sdc1 with whatever the device node is.

```

Unable to read /dev/sdc
```
That's doesn't sound good. Are you sure it mounts cleanly in windows? (now)

You could try to reset the Stone. It sould be a small "pen button" somewhere that does it.

I've tried resetting it a cople of times, and I will try it with my windows machine next time I get the chance. Thanks for the help though. In my /media folder there is no entry for the stone.

---

