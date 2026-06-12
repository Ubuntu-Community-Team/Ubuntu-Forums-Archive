---
title: "Ubuntu 11.10 not recognizing CD-Rs"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by Kelvari on 2011-11-19
I was able to burn a few CD-Rs, but then Brasero (and even Ubuntu itself) stopped recognizing the fact that there was a blank CD-R in the drive.

I have rebooted the system twice to try to fix it with no avail.

Going off of previous threads regarding this topic (or similar), I have the output from the following commands:

```
$ wodim -prcap
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-4163B'
Revision       : 'A101'
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
  Does not read R-W subcode information
  Does read raw P-W subcode data from lead in
  Does return CD media catalog number
  Does return CD ISRC information
  Does support C2 error pointers
  Does not deliver composite A/V data

  Does play audio CDs
  Number of volume control levels: 256
  Does support individual volume control setting for each channel
  Does support independent mute setting for each channel
  Does not support digital output on port 1
  Does not support digital output on port 2

  Loading mechanism type: tray
  Does support ejection of CD via START/STOP command
  Does not lock media on power up via prevent jumper
  Does allow media to be locked in the drive via PREVENT/ALLOW command
  Is currently in a media-locked state
  Does not support changing side of disk
  Does not have load-empty-slot-in-changer feature
  Does not support Individual Disk Present feature

  Maximum read  speed:  7056 kB/s (CD  40x, DVD  5x)
  Current read  speed:  7056 kB/s (CD  40x, DVD  5x)
  Maximum write speed:  7056 kB/s (CD  40x, DVD  5x)
  Current write speed:  7056 kB/s (CD  40x, DVD  5x)
  Rotational control selected: CLV/PCAV
  Buffer size in KB: 2048
  Copy management revision supported: 1
  Number of supported write speeds: 6
  Write speed # 0:  7056 kB/s CLV/PCAV (CD  40x, DVD  5x)
  Write speed # 1:  5645 kB/s CLV/PCAV (CD  32x, DVD  4x)
  Write speed # 2:  4234 kB/s CLV/PCAV (CD  24x, DVD  3x)
  Write speed # 3:  2822 kB/s CLV/PCAV (CD  16x, DVD  2x)
  Write speed # 4:  1411 kB/s CLV/PCAV (CD   8x, DVD  1x)
  Write speed # 5:   706 kB/s CLV/PCAV (CD   4x, DVD  0x)

Supported CD-RW media types according to MMC-4 feature 0x37:
  Does write multi speed       CD-RW media
  Does write high  speed       CD-RW media
  Does write ultra high speed  CD-RW media
  Does write ultra high speed+ CD-RW media

```
```
$ sudo lshw -C disk
  *-cdrom                 
       description: DVD-RAM writer
       product: DVDRAM GSA-4163B
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: A101
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

```

Any help at all would be appreciated.

---

### Post by Kelvari on 2011-11-20
In case anyone stumbles across this thread in the future, here's how things worked out (borrowing a recommendation from XKCD here)

I wound up using a LiveUSB to finish burning the CDs that I had to burn. I just tried a blank CD-R, and the system recognized it, so I guess that that had something to do with 'fixing' the problem that I had.

Any idea as to what happened, or why it wound up getting fixed?

---

