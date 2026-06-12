---
title: "Sorry, DVD Playback help needed."
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Russ[] on 2008-08-13
K....

```
russell@russell-desktop:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: AN05_D2
libdvdnav: DVD Serial Number: 34C76E1B
libdvdnav: DVD Title (Alternative): AN05_D2
libdvdnav: Unable to find map file '/home/russell/.dvdnav/AN05_D2.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000148
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00012604
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00023312
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00035f21
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0009019f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00343b1a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x00343b1a)!!
libdvdread: Elapsed time 27
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00346582
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_1.VOB (0x00346582)!!
libdvdread: Elapsed time 28
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00388b2c
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_1.VOB (0x00388b2c)!!
libdvdread: Elapsed time 29
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003cd9e3
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x003cd9e3)!!
libdvdread: Elapsed time 30
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003dac56
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_1.VOB (0x003dac56)!!
libdvdread: Elapsed time 29
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003ec98d
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_10_1.VOB (0x003ec98d)!!
libdvdread: Elapsed time 27
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003f029e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_11_1.VOB (0x003f029e)!!
libdvdread: Elapsed time 29
libdvdread: Found 11 VTS's
libdvdread: Elapsed time 200
[00000349] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
```


```
russell@russell-desktop:~$ sudo lshw -C disk
  *-cdrom:0               
       description: DVD reader
       product: DVD-ROM GD-2000
       vendor: COMPAQ
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 0056
       capabilities: removable audio dvd
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
```

```
russell@russell-desktop:~$ sudo regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.
```

What's going on here I'm searching and confused?

---

### Post by noobuntu35 on 2008-08-13
It's looking for a directory thats not there.
Unable to find map file '/home/russell/.dvdnav/AN05_D2.map'<---- from your print out
the good news is your DVD drive is there and mounted ready to use try a different Mediaplayer
[like this one here ]("http://xinehq.de/")it'ss a link to xine which is an easy to use DVD Media player. Check your Synaptic for versions installed with your distro, main menu> System> Admin> Synaptic then look for the multimedia section there will be a Media player there that will work with your Distro.

---

### Post by Russ[] on 2008-08-13
I've tried several other media players and now gxine as well and none are working, it seems as if they are all looking in the wrong place for my dvd drive.


There's a /home/russell/.dvdcss directory but no .dvdnav.

---

### Post by noobuntu35 on 2008-08-13
> **'Russ[] said:**
> I've tried several other media players and now gxine as well and none are working, it seems as if they are all looking in the wrong place for my dvd drive.


There's a /home/russell/.dvdcss directory but no .dvdnav.

 /usr/lib/nautilus-cd-burner/list_cddrives
what does the print out from this give you?

---

### Post by Russ[] on 2008-08-13
I tried another dvd and it didn't work, I didn't check the errors on it I just grabbed this to make sure it wasn't that dvd.

```

russell@russell-desktop:~$ /usr/lib/nautilus-cd-burner/list_cddrives

** (process:8317): WARNING **: No property volume.disc.capacity on device with id /org/freedesktop/Hal/devices/volume_label_AN05_D2

Drive:
  name:			DVD-ROM GD-2000
  device:		/dev/scd1
  door:			closed
  type:			DVD-R, DVD-RW, DVD+R, DVD+R DL, DVD+RW, CD, DVD
  is mounted:		TRUE
  max read speed:	3528 KiB/s (CD 23.5x, DVD 2.6x)
  max write speed:	0 KiB/s (CD 0.0x, DVD 0.0x)
  write speeds:		
Media:
  label:		'AN05_D2'
  type:			Unknown Media (has-data)
  is writable:		FALSE
  is appendable:	FALSE
  capacity:		Could not be determined
  size:			31987.98 MiB
---
Drive:
  name:			CD-R/RW SW-248F
  device:		/dev/scd0
  door:			open
  type:			CD-R, CD-RW, CD
  is mounted:		FALSE
  max read speed:	8467 KiB/s (CD 56.4x, DVD 6.2x)
  max write speed:	0 KiB/s (CD 0.0x, DVD 0.0x)
  write speeds:		
Media:
  label:		''
  type:			Couldn't open media
  is writable:		FALSE
  is appendable:	FALSE
  capacity:		Could not be determined
  size:			Could not be determined

```

---

### Post by noobuntu35 on 2008-08-13
No property volume.disc.capacity on device with id /org/freedesktop/Hal/devices/volume_label_AN05_D2

what happens if you try another dvd it looks as though this drive isn't working with this disc are you running a dual boot and does it run in windows (or other os?) what happens when you put another disk in?

run the same command as before with a new dvd in the drive

---

### Post by Russ[] on 2008-08-13
Yup tried it with another dvd and the same thing. No dual booting either. 

Bad DVD Drive?

---

### Post by noobuntu35 on 2008-08-13
can you hear it running?

---

### Post by noobuntu35 on 2008-08-13
check all your cables

---

### Post by Russ[] on 2008-08-13
Yah it's making some noise, and it get's the name of the movie and all of that. 

It's not making noise like when my 52x cd drive is spinning though.

---

### Post by noobuntu35 on 2008-08-13
/usr/lib/nautilus-cd-burner/list_cddrives
run this again and give the print out

---

### Post by Russ[] on 2008-08-13
ok so now after checking all of the connections and a reboot if I run vlc from the terminal it works. The only thing I did was play aroudn with where it links the mounted drive to.

However. If I right click on the icon for it on the desktop and click play, it does not work. And...

```
russell@russell-desktop:~$ /usr/lib/nautilus-cd-burner/list_cddrives

** (process:6188): WARNING **: No property volume.disc.capacity on device with id /org/freedesktop/Hal/devices/volume_label_OFFICE_SPACE_SE_4X3

Drive:
  name:			DVD-ROM GD-2000
  device:		/dev/scd1
  door:			closed
  type:			DVD-R, DVD-RW, DVD+R, DVD+R DL, DVD+RW, CD, DVD
  is mounted:		FALSE
  max read speed:	3528 KiB/s (CD 23.5x, DVD 2.6x)
  max write speed:	0 KiB/s (CD 0.0x, DVD 0.0x)
  write speeds:		
Media:
  label:		'OFFICE_SPACE_SE_4X3'
  type:			Unknown Media (has-data)
  is writable:		FALSE
  is appendable:	FALSE
  capacity:		Could not be determined
  size:			7620.12 MiB
---
Drive:
  name:			CD-R/RW SW-248F
  device:		/dev/scd0
  door:			open
  type:			CD-R, CD-RW, CD
  is mounted:		FALSE
  max read speed:	8467 KiB/s (CD 56.4x, DVD 6.2x)
  max write speed:	0 KiB/s (CD 0.0x, DVD 0.0x)
  write speeds:		
Media:
  label:		''
  type:			Couldn't open media
  is writable:		FALSE
  is appendable:	FALSE
  capacity:		Could not be determined
  size:			Could not be determined
---

```

---

### Post by noobuntu35 on 2008-08-13
run  mount -t udf or mount -t iso9660 
to remount the drive and try again with the DVD
 run this and post the output cat /etc/fstab

---

### Post by noobuntu35 on 2008-08-15
Have you fixed this yet? if so then please mark this thread as solved

---

