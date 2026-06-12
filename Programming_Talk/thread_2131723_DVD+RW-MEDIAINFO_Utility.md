---
title: "DVD+RW-MEDIAINFO Utility"
date: 2013-04-02
forum: Programming Talk
---

### Post by RaHorakhty on 2013-04-02
I cannot find any detailed man info regarding the output of DVD+RW-MEDIAINFO DVD cmd.  I want to convert the size info into GB using grep and bc. Here's what it generates when a blank DVD is inserted:

```
INQUIRY:                [TSSTcorp][DVD+-RW TS-L632H][D400]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         1Bh, DVD+R
 Current Write Speed:   8.0x1385=11080KB/s
 Write Speed #0:        8.0x1385=11080KB/s
 Write Speed #1:        6.0x1385=8310KB/s
 Write Speed #2:        4.0x1385=5540KB/s
 Write Speed #3:        3.0x1385=4155KB/s
 Write Speed #4:        3.0x1385=4155KB/s
 Write Speed #5:        3.0x1385=4155KB/s
 Write Speed #6:        3.0x1385=4155KB/s
 Write Speed #7:        3.0x1385=4155KB/s
 Write Speed #8:        3.0x1385=4155KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     8.0x1385=11080KB/s@[0 -> 2295104]
 Speed Descriptor#0:    00/2295103 R@8.0x1385=11080KB/s W@8.0x1385=11080KB/s
 Speed Descriptor#1:    00/2295103 R@8.0x1385=11080KB/s W@6.0x1385=8310KB/s
 Speed Descriptor#2:    00/2295103 R@8.0x1385=11080KB/s W@4.0x1385=5540KB/s
 Speed Descriptor#3:    00/2295103 R@8.0x1385=11080KB/s W@3.0x1385=4155KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Media ID:              SONY/D21
 Legacy lead-out at:    2295104*2KB=4700372992
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
 Free Blocks:           2295104*2KB
 Track Size:            2295104*2KB
READ CAPACITY:          0*2048=0

```
DVD+RW-MEDIAINFO DVD | GREP "Free Blocks:" returns Free Blocks:           2295104*2KB.  Whats the best way to display it as 4GB.  I know theres 1024MB in Gig. But whats with the *2KB.  The [documentation]("http://fy.chalmers.se/~appro/linux/DVD+RW/") I found is too much to digest.  Any suggestions or references?

---

### Post by ofnuts on 2013-04-02
2295104*2KB=4482.625MB=4.377GB (assuming we are really talking about KiB/MiB/GiB)

---

### Post by RaHorakhty on 2013-04-04
That makes sense.  I don't see how it can hold more than 4.3GB.  When I execute the cmd on a DVD that I burned yrs ago, I get strange results.  According to Nautilus the DVD holds 4.6GB, more than the 4.3GB cap. Here's the ouput:

```
INQUIRY:                [TSSTcorp][DVD+-RW TS-L632H][D400]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         1Bh, DVD+R
 Media ID:              SONY/D21
 Current Write Speed:   8.0x1385=11080KB/s
 Write Speed #0:        8.0x1385=11080KB/s
 Write Speed #1:        6.0x1385=8310KB/s
 Write Speed #2:        4.0x1385=5540KB/s
 Write Speed #3:        3.0x1385=4155KB/s
 Write Speed #4:        3.0x1385=4155KB/s
 Write Speed #5:        3.0x1385=4155KB/s
 Write Speed #6:        3.0x1385=4155KB/s
 Write Speed #7:        3.0x1385=4155KB/s
 Write Speed #8:        3.0x1385=4155KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     8.0x1385=11080KB/s@[0 -> 2295104]
 Speed Descriptor#0:    00/2295103 R@8.0x1385=11080KB/s W@8.0x1385=11080KB/s
 Speed Descriptor#1:    00/2295103 R@8.0x1385=11080KB/s W@6.0x1385=8310KB/s
 Speed Descriptor#2:    00/2295103 R@8.0x1385=11080KB/s W@4.0x1385=5540KB/s
 Speed Descriptor#3:    00/2295103 R@8.0x1385=11080KB/s W@3.0x1385=4155KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2242464*2KB=4592566272
READ DISC INFORMATION:
 Disc status:           complete
 Number of Sessions:    1
 State of Last Session: complete
 Number of Tracks:      1
READ TRACK INFORMATION[#1]:
 Track State:           invisible
 Track Start Address:   0*2KB
 Free Blocks:           0*2KB
 Track Size:            2242464*2KB
FABRICATED TOC:
 Track#1  :             17@0
 Track#AA :             17@2242464
 Multi-session Info:    #1@0
READ CAPACITY:          2242464*2048=4592566272
joe@name-comp-000:/dev$ dvd+rw-mediainfo dvd
INQUIRY:                [TSSTcorp][DVD+-RW TS-L632H][D400]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         1Bh, DVD+R
 Media ID:              SONY/D21
 Current Write Speed:   8.0x1385=11080KB/s
 Write Speed #0:        8.0x1385=11080KB/s
 Write Speed #1:        6.0x1385=8310KB/s
 Write Speed #2:        4.0x1385=5540KB/s
 Write Speed #3:        3.0x1385=4155KB/s
 Write Speed #4:        3.0x1385=4155KB/s
 Write Speed #5:        3.0x1385=4155KB/s
 Write Speed #6:        3.0x1385=4155KB/s
 Write Speed #7:        3.0x1385=4155KB/s
 Write Speed #8:        3.0x1385=4155KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     8.0x1385=11080KB/s@[0 -> 2295104]
 Speed Descriptor#0:    00/2295103 R@8.0x1385=11080KB/s W@8.0x1385=11080KB/s
 Speed Descriptor#1:    00/2295103 R@8.0x1385=11080KB/s W@6.0x1385=8310KB/s
 Speed Descriptor#2:    00/2295103 R@8.0x1385=11080KB/s W@4.0x1385=5540KB/s
 Speed Descriptor#3:    00/2295103 R@8.0x1385=11080KB/s W@3.0x1385=4155KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2242464*2KB=4592566272
READ DISC INFORMATION:
 Disc status:           complete
 Number of Sessions:    1
 State of Last Session: complete
 Number of Tracks:      1
READ TRACK INFORMATION[#1]:
 Track State:           invisible
 Track Start Address:   0*2KB
 Free Blocks:           0*2KB
 Track Size:            2242464*2KB
FABRICATED TOC:
 Track#1  :             17@0
 Track#AA :             17@2242464
 Multi-session Info:    #1@0
READ CAPACITY:          2242464*2048=4592566272

```
How can I extract the amount of used space on a DVD w/out writing a script?  Is there another function in Bash?

---

### Post by ofnuts on 2013-04-04
The 'df' command will tell you how much space is used on a DVD if it's mounted.

---

### Post by RaHorakhty on 2013-04-06
@ofnuts  Thanks for the info. I'll look into df.  The 4.6GB was caused by whats known has "overburning."  Wonder how all this works on Blueray blanks...lol...

---

