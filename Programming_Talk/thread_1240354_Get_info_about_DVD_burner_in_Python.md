---
title: "Get info about DVD burner in Python"
date: 2009-08-14
forum: Programming Talk
---

### Post by Nevon on 2009-08-14
I'm currently rewriting an application that I made to burn Xbox 360 isos (really just a front-end to growisofs) in Python, and giving it a proper GUI. However, right now I'm kind of stuck, trying to get information about the user's optical media. 

First of all I need to be able to list all optical devices with writing capabilities. Then I would need to find out whether or not the devices have any discs in them. Lastly I would need to find out what kind of discs are in the devices. 

I've been googling for the last half-hour or so, but I can't come up with anything. Is there a simple way to solve this?

---

### Post by jeffathehutt on 2009-08-14
I know it doesn't directly answer your question, but you might get some ideas from the source code for [recorder.]("http://code.google.com/p/recorder/") ([http://code.google.com/p/recorder/](http://code.google.com/p/recorder/))  It is a frontend to growisofs written in python.  You might be able to see how that program does it.  Hope that helps a bit.

---

### Post by Nevon on 2009-08-15
> **jeffathehutt said:**
> I know it doesn't directly answer your question, but you might get some ideas from the source code for [recorder.]("http://code.google.com/p/recorder/") ([http://code.google.com/p/recorder/](http://code.google.com/p/recorder/))  It is a frontend to growisofs written in python.  You might be able to see how that program does it.  Hope that helps a bit.

Checked it out, but it turns out that program gets any info about the drive from the user - so for me it's useless. However, I did check out wodim, and it seems you can use:
```
wodim --devices
```to get a list of drives, looking something like this:
> wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'	rwrw-- : 'Optiarc' 'DVD RW AD-7590S'
-------------------------------------------------------------------------
Now the question is, how do I get information about the drive - like maximum write speed, what discs it can handle, etc. As well as information about the disc inside?

Basically I want the same sort of functionality that Brasero has. See the picture for an idea.

[img]http://i26.tinypic.com/wn47n.png[/img]

And here's BoxBlaze in it's current form:

[img]http://i27.tinypic.com/2wn713r.png[/img]

Of course I could try to see what Brasero is doing, but first of all it's pretty darn big. And secondly, it's not written in Python.

---

### Post by Nevon on 2009-08-15
Hey! Now we're talking! Wodim can do more than you'd think.

To get more information about the drive itself (like burn speeds and such), you can do (remember, I got the device mount point from "wodim --devices":
```
nevon@loltop:$ **wodim -prcap dev=/dev/scd0**
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'Optiarc '
Identification : 'DVD RW AD-7590S '
Revision       : '1.00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.

Drive capabilities, per MMC-3 page 2A:

  Does read CD-R media
  Does write CD-R media
  Does read CD-RW media
  Does write CD-RW media
  Does read DVD-ROM media
  Does read DVD-R media
  Does write DVD-R media
  Does read DVD-RAM media
  Does write DVD-RAM media
  Does support test writing

  Does read Mode 2 Form 1 blocks
  Does read Mode 2 Form 2 blocks
  Does read digital audio blocks
  Does restart non-streamed digital audio reads accurately
  Does support Buffer-Underrun-Free recording
  Does read multi-session CDs
  Does read fixed-packet CD media using Method 2
  Does not read CD bar code
  Does read R-W subcode information
  Does not return R-W subcode de-interleaved and error-corrected
  Does read raw P-W subcode data from lead in
  Does return CD media catalog number
  Does return CD ISRC information
  Does support C2 error pointers
  Does not deliver composite A/V data

  Does play audio CDs
  Number of volume control levels: 0
  Does not support individual volume control setting for each channel
  Does not support independent mute setting for each channel
  Does not support digital output on port 1
  Does not support digital output on port 2

  Loading mechanism type: tray
  Does support ejection of CD via START/STOP command
  Does not lock media on power up via prevent jumper
  Does allow media to be locked in the drive via PREVENT/ALLOW command
  Is not currently in a media-locked state
  Does not support changing side of disk
  Does not have load-empty-slot-in-changer feature
  Does not support Individual Disk Present feature

  Maximum read  speed:  8310 kB/s (CD  47x, DVD  6x)
  Current read  speed:  8310 kB/s (CD  47x, DVD  6x)
  Maximum write speed:  8310 kB/s (CD  47x, DVD  6x)
  Current write speed:  8310 kB/s (CD  47x, DVD  6x)
  Rotational control selected: CLV/PCAV
  Buffer size in KB: 2048
  Copy management revision supported: 1
  Number of supported write speeds: 3
  Write speed # 0:  8310 kB/s CLV/PCAV (CD  47x, DVD  6x)
  Write speed # 1:  5540 kB/s CLV/PCAV (CD  31x, DVD  4x)
  Write speed # 2:  3324 kB/s CLV/PCAV (CD  18x, DVD  2x)

Supported CD-RW media types according to MMC-4 feature 0x37:
  Does write multi speed       CD-RW media
  Does write high  speed       CD-RW media
  Does write ultra high speed  CD-RW media
  Does write ultra high speed+ CD-RW media
```

And to get information about the media inside, I just do:
```
nevon@loltop:$ dvd+rw-mediainfo /dev/scd0
INQUIRY:                [Optiarc ][DVD RW AD-7590S ][1.00]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         2Bh, DVD+R Double Layer
 Media ID:              MKM/003
 Current Write Speed:   6.0x1385=8310KB/s
 Write Speed #0:        6.0x1385=8310KB/s
 Write Speed #1:        4.0x1385=5540KB/s
 Write Speed #2:        2.4x1385=3324KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     2.4x1385=3324KB/s@[0 -> 393215]
                        4.0x1385=5540KB/s@[393216 -> 1114111]
                        6.0x1385=8310KB/s@[1114112 -> 4173824]
 Speed Descriptor#0:    00/4173824 R@6.0x1385=8310KB/s W@6.0x1385=8310KB/s
 Speed Descriptor#1:    00/4173824 R@6.0x1385=8310KB/s W@4.0x1385=5540KB/s
 Speed Descriptor#2:    00/4173824 R@6.0x1385=8310KB/s W@2.4x1385=3324KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2086912*2KB=4273995776
DVD+R DOUBLE LAYER BOUNDARY INFORMATION:
 L0 Data Zone Capacity: 2086912*2KB, can still be set
READ DISC INFORMATION:
 Disc status:           blank
 Number of Sessions:    1
 State of Last Session: empty
 "Next" Track:          1
 Number of Tracks:      1
READ TRACK INFORMATION[#1]:
 Track State:           blank
 Track Start Address:   0*2KB
 Next Writable Address: 0*2KB
 Free Blocks:           4173824*2KB
 Track Size:            4173824*2KB
 ROM Compatibility LBA: 0
READ CAPACITY:          0*2048=0
```

Now I just need to parse this. Too bad I suck at regular expressions. Anyone with mad regexp skills who would like to help me? First I need to get the device mount point as well as the name. That is, everything inside ''s in the output of wodim --devices.

Next would be to find out whether or not the burner supports burning of dual layer discs, but it doesn't seem like wodim checks for that.

At least I can check for supported drive speeds. Basically, this is what I need:
```
Number of supported write speeds: 3
  Write speed # 0:  8310 kB/s CLV/PCAV (CD  47x, DVD  6x)
  Write speed # 1:  5540 kB/s CLV/PCAV (CD  31x, DVD  4x)
  Write speed # 2:  3324 kB/s CLV/PCAV (CD  18x, DVD  2x)
```
Or well, I really just need the numbers before kB/s. 

Last of all we have the output of dvd+rw-mediainfo /dev/scd0 where I'm only looking for "DVD+R Double Layer" after "Mounted Media:", and "Disc status:           blank". If it's already been used, it should say "appendable" or something other than "blank".

---

