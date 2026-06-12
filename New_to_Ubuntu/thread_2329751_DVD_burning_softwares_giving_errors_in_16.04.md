---
title: "DVD burning softwares giving errors in 16.04"
date: 2016-07-04
forum: New to Ubuntu
---

### Post by crip720 on 2016-07-04
I have been trying to burn AVI files to DVD in Ubuntu 16.04, as a data disk.  K3B gives an error of cannot estimate image size, it did work for a couple of months.  xfburn says it cannot do multi session burn, and brasero says not enough space on blank DVD, brasero did work for one disk.  Have been burning DVDs since 10.04 with no problems.  Is the simple CD/DVD burner software that 10.04 used still available?  Do not need any thing fancy, but would like something that works.  Have only had these problems with 16.04.  I am using an external Samsung DVD writer/reader plugged into a USB hub and outlet bar(since 14.04).  Have done apt-get remove and apt-get clean, but have not rebooted yet. Root and Home partitions less than 30% full.  Is there a reason that 16.04 is having problems with burning software, or is it just me?  Thank you for your help.  It was a clean install of 16.04.

---

### Post by scdbackup on 2016-07-05
Hi,

i am the developer of libburn, which works underneath Xfburn.

From your report it is hard to tell why the GUI programs refuse on you.
Given the fact that Xfburn complained about "multi session", it might be
that the DVD was not blank but already written and still appendable.

Further it would be interesting to know in what wrapping you want to
burn the AVI files onto the DVD. Ready for a DVD player (i.e. UDF
filesystem and VIDEO_TS directory) or just to be mountable and then 
accessible by AVI player software (e.g. ISO 9660 filesystem).

Information about drives and media can be obtained by program runs
in a shell terminal.

This should list all recognizable and not exclusively reserved drives
(i.e. not mounted and not in use by a burn program):
```

xorriso -devices

```

This gives information about the first drive and the medium that is inserted.
Put in your burn candidate DVD before executing:
```

xorriso -outdev /dev/sr0 -toc

```

Maybe i can tell more if you show me the text lines reported by both
commands.

Have a nice day :)

Thomas

---

### Post by crip720 on 2016-07-05
First output is : ```
 -dev '/dev/sr0' rwrw-- :  'TSSTcorp' 'CDDVDW SE-S084F' and the second output is : Drive current: -outdev '/dev/sr0'
Media current: DVD+R
Media status : is written , is appendable
Drive current: -outdev '/dev/sr0'
Drive type   : vendor 'TSSTcorp' product 'CDDVDW SE-S084F' revision 'TS00'
Drive id     : 'R8AF6GXB500424  '
Media current: DVD+R
Media product: CMC_MAG/M01/48 , CMC Magnetics Corporation
Media status : is written , is appendable
Media blocks : 1 readable , 36416 writable , 2295104 overall
TOC layout   : Idx ,  sbsector ,       Size , Volume Id
xorriso : SORRY : Cannot obtain Table Of Content
xorriso : NOTE : Tolerated problem event of severity 'SORRY'
xorriso : NOTE : -return_with SORRY 32 triggered by problem severity SORRY.   This is with a disk that brasero tried to burn.  A new blank disk gives this output: Drive current: -outdev '/dev/sr0'
Media current: DVD+R
Media status : is written , is appendable
Media summary: 5 sessions, 359728 data blocks,  703m data, 3760m free
Drive current: -outdev '/dev/sr0'
Drive type   : vendor 'TSSTcorp' product 'CDDVDW SE-S084F' revision 'TS00'
Drive id     : 'R8AF6GXB500424  '
Media current: DVD+R
Media product: CMC_MAG/M01/48 , CMC Magnetics Corporation
Media status : is written , is appendable
Media blocks : 367920 readable , 1925136 writable , 2295104 overall
TOC layout   : Idx ,  sbsector ,       Size , Volume Id
Other session:   1 ,         0 ,     65264s , 
Other session:   2 ,     67312 ,    150736s , 
Other session:   3 ,    220096 ,    139920s , 
Other session:   4 ,    362064 ,       304s , 
Other session:   5 ,    364416 ,      3504s , 
Media summary: 5 sessions, 359728 data blocks,  703m data, 3760m free
Media nwa    : 369968s. 
``` I have rebooted, and have also changed to direct usb connection to the laptop.  Have also tried to burn with brasero on 14.04, but gave the same not enough space on disk error.  Could I have a few bad disks or bad DVD writer?  I am trying to burn TV series onto DVD, direct burn with no conversion, just drag and drop files to burner software.  It was first time using xfburn, so I might have done something wrong.  I have just tried Ubuntu's 'write to disk' for an iso, and it seems to be working.

---

### Post by wildmanne39 on 2016-07-05
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by X-RED_Tech on 2016-07-05
It shows several sessions already.  
Are you sure you didn't close the last one?
And assuming it isn't closed, are you sure you aren't adding more than 3760MB?

```
[COLOR=#000000][FONT=&quot]Media summary: **5 sessions**, 359728 data blocks,  703m data, **3760m free**[/FONT][/COLOR]
```

---

### Post by crip720 on 2016-07-05
The last section was done with a new blank disk, never been used before and without any burning software open or used.  Did use the disk after to burn an iso with Ubuntu's 'write to disk' and the DVD writer has burned the iso to disk.  The disk are label for 4.7GBs.  Thank you Wild Man for fixing my response.

---

### Post by X-RED_Tech on 2016-07-05
Actually it's 4.38GB (or GiB, not sure...) and no, the report you posted is about a DVD+R with multiple sessions:

```
(...)
Media current: DVD+R
Media product: CMC_MAG/M01/48 , CMC Magnetics Corporation
Media status : is written , is appendable
Media blocks : 367920 readable , 1925136 writable , 2295104 overall
TOC layout   : Idx ,  sbsector ,       Size , Volume Id
[B]Other session:   1 ,         0 ,     65264s , 
Other session:   2 ,     67312 ,    150736s , 
Other session:   3 ,    220096 ,    139920s , 
Other session:   4 ,    362064 ,       304s , 
Other session:   5 ,    364416 ,      3504s , 
Media summary: 5 sessions[/B], 359728 data blocks,  703m data, 3760m free 
Media nwa    : 369968s.[COLOR=#222222][FONT=Verdana]
```

You may have not switched media as you think you did and tried to burn more than the available space in the already used disc[/FONT][/COLOR]

---

### Post by crip720 on 2016-07-05
I have open up a new DVD package and everything is working right.  Using brasreo right now, will test k3b next time   The last DVDs in the old package must have been bad, I hope.  I ran the code again with new disk and the important stuff came up with zeros.  Will mark this thread solved.  Does anyone know any way to test blank DVDs or do I have to run xorriso to check them?  I did switch the disk and used the last one on the spindle.  Thank you for your help.

---

### Post by mc4man on 2016-07-06
That media, CMC_MAG/M01/48, is [average at best]("http://club.myce.com/f76/cmc-magnetics-dvd-r-85868/index12.html") with noticeable variation depending on brand. I've always found best to spend a little more for top quality.  (Taiyo Yuden - made in japan,  for dvd-5 disks is very good.
Also  pancake packing can have x% of dud disks, generally higher on larger packs, ie. 50,  100 or more

---

### Post by scdbackup on 2016-07-06
Hi,

as was stated by others meanwhile, both media are reported by the
drive to be already written and not yet closed. So this explains why
Xfburn talks of "multi session".

The first medium is obviously damaged, because libburn cannot get
info about the existing sessions and tracks.
```

Media status : is written , is appendable
Media blocks : 1 readable , 36416 writable , 2295104 overall
TOC layout   : Idx ,  sbsector ,       Size , Volume Id
xorriso : SORRY : Cannot obtain Table Of Content

```
The numbers of 1 readable blocks and 36416 writable blocks could
indicate that a burn session was prepared but not completely written.

We could examine the particular reasons for these statements by letting
libburn report its SCSI transactions. The following command would give
lengthy text output and catch a copy of it in file "xorriso.log":
```

xorriso -scsi_log on -outdev /dev/sr0 -toc 2>&1 | tee -i xorriso.log

```
But given the fact that newly bought media work well, i do not urge
to do so. (Unless there is enough technical curiosity on your side.)

The second medium reports to be already written, too. But here the
5 sessions appear to be completly written:
```

Media blocks : 367920 readable , 1925136 writable , 2295104 overall
TOC layout   : Idx ,  sbsector ,       Size , Volume Id
...
Other session:   5 ,    364416 ,      3504s ,

```
364416 + 3504 = 367920.
The data are not recognized as ISO 9660 filesystems. So no "Volume Id"
is reported.

The reported state of the second media would be ok for adding more data.
xorriso in its native mode will refuse to add a session to a non-blank
medium from which it could not read a previously stored ISO 9660.
But xorriso -as cdrecord, or cdrecord itself, or cdrskin, should at least
try to put data onto the medium. An ISO 9660 image for this purpose
would have to be prepared for an offset of 369968 blocks because of
```

Media nwa    : 369968s

```
This preparation would be done by mkisofs-ish option ```
-C 0,369968
```.
But again, if it's just about some bad media, there is few practical
use in trying this stunt.

Have a nice day :)

Thomas

---

