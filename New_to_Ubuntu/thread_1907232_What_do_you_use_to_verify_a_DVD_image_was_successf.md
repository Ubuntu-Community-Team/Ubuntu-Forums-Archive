---
title: "What do you use to verify a DVD image was successfully burned to optical disc?"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by rocksockdoc on 2012-01-11
My laptop doesn't even have an optical drive so I'm just getting used to DVD burning.

It turns out to be pretty simple (using "Brasero Disc Burner, or the default "Write to Disc" program) ... but ... where is the 'VERIFY' button.

Having burned DVD discs in the past on Windows, it would be reassuring to run a verification step.

What does one use to verify that a disc image was successfully burned to an optical DVD disc?

---

### Post by uRock on 2012-01-11
Open the disk with Movie Player, if it is a movie, or open it by double clicking the icon and using the file browser.

---

### Post by Jahid65 on 2012-01-11
Don't know about brasero, but K3b has the option to verify disc after burning

---

### Post by mastablasta on 2012-01-11
did someone say verify burned image? : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by prshah on 2012-01-11
> **rocksockdoc said:**
> It turns out to be pretty simple (using "Brasero Disc Burner, or the default "Write to Disc" program) ... but ... where is the 'VERIFY' button.

use Tools-Verify Integrity in Brasero. If you have an MD5 available, then the integrity check will be fast and more accurate; otherwise, it is just basically a readability check.

You can also use DVDisaster (it's in the Software Center) to check readability of the burned disc, and optionally, validity too if the original disc is available.

By default, verification is automatically enabled in Brasero, and you should have a verification process if you watch the progress text carefully.

---

### Post by rocksockdoc on 2012-01-11
> **Jahid65 said:**
> Don't know about brasero, but K3b has the option to verify disc after burning

It's not a simple button click in Brasero ... 

> **prshah said:**
> use Tools-Verify Integrity in Brasero. If you have an MD5 available

I see that. Now all I need to do is figure out how to make the MD5 file & we're set.

> **prshah said:**
> You can also use DVDisaster ... to check... validity too if the original disc is available.

I'm going from an ISO image file on the hard disk to the DVD image on the optical disc - but this additional hint will be useful if/when I go from optical disc to optical disc. Thanks.

> **prshah said:**
> By default, verification is automatically enabled in Brasero, and you should have a verification process if you watch the progress text carefully.

I must be missing something. Brasero has a "Tools->Check Integrity" option, but it requires a pre-existing MD5 file AFAIK.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210646&stc=1&d=1326307941[/IMG]

So, I think, based on the advice given, I just need to read the referenced file & perhaps google for how best to create that necessary MD5 file of the ISO image on the hard disk.

---

### Post by Telengard C64 on 2012-01-11
[_check the CD against the official MD5 hash code from the command line_](http://kubuntuforums.net/forums/index.php?topic=3106270.0).

Also worth mentioning is that Ubuntu install discs have an option on the boot menu to check the disc for defects.

If you don't have an MD5SUM for the image then you can try the burning program's built-in verification, as already mentioned.

---

### Post by rocksockdoc on 2012-01-11
> **mastablasta said:**
> did someone say verify burned image? : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Following those directions to create the MD5 file of the iso image ... 

I ran the following on the ISO file and will burn to disk and try to use Brasero's Verify command:
```
$ md5sum movie.iso > movie.md5
$ cat movie.md5
REPORTS:
c524367686cde89571695c024a4add7f movie.iso
```Unfortunately, based purely on this statement below from the reference above, this might not actually work:
> "*However this will almost NEVER be the same hash as the iso image that  was burned to the disk, because this command includes the empty space at  the end of the disk, which changes the hash. So you must check [I]only* the part of the disk that was on the iso. "[/I]So, I'll also try the second suggested method:
```
$ ls -l movie.iso  
REPORTS:
-rwxrwxrwx 1 a a 3105759232 2012-01-11 07:16 movie.iso
$ dd if=./movie.iso bs=2048 count=3105759232 | md5sum > movie.md5
REPORTS:
1516484+0 records in
1516484+0 records out
3105759232 bytes (3.1 GB) copied, 77.2532 s, 40.2 MB/s
$ cat movie.md5
REPORTS:
c524367686cde89571695c024a4add7f  -
```I'll let you know if either of these two methods works to create the necessary MD5 file that Brasero Tools->Check Integrity requires.

It may be important (to Brasero) to note the two MD5 files are slightly different:
> **1st MD5 file: **
c524367686cde89571695c024a4add7f movie.iso
**2nd MD5 file: **
c524367686cde89571695c024a4add7f  -

---

### Post by mastablasta on 2012-01-11
> **rocksockdoc said:**
> 

It may be important (to Brasero) to note the two MD5 files are slightly different:

i must be blind and it's late but i don't see the difference...
this is the *thing* you are trying to have the same:
c524367686cde89571695c024a4add7f
c524367686cde89571695c024a4add7f

they seem the same to me...

---

### Post by rocksockdoc on 2012-01-11
> **mastablasta said:**
> they seem the same to me...

I understand what you are saying.

The MD5 hash is the same, I agree.

The only difference is in the text strings AFTER the MD5 hash.

Since Brasero asks not for the number but for the entire file, I wasn't sure if Brasero would simply omit this extraneous (conflicting) information.

Unfortunately, the verification process using these two files failed (just now) ... but at the moment, the failure doesn't seem to be due to the format of the files.

> **Telengard C64 said:**
> [_check the CD against the official MD5 hash code from the command line_]("http://kubuntuforums.net/forums/index.php?topic=3106270.0").

I think I'm close ... but there is some kind of 'permission' problem when I point Brasero to the two recently-generated MD5 files:

```
$ ls -l
REPORTS:
-rwxrwxrwx ... movie.md5
-rwxrwxrwx ... movie.md5b
```This is what Brasero reports when I point it to the just-burned DVD optical disc and to the MD5 file generated off the iso image on hard disk:
> The file integrity check could not be performed.
You do not have the required permissions to use this drive.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210648&stc=1&d=1326311812[/IMG]

I'm the only user of the equipment so I don't understand how/why I don't have permissions to use the drive.

Any hints?

---

### Post by rocksockdoc on 2012-01-12
> **rocksockdoc said:**
> Brasero: "The file integrity check cannot be performed. You do not have the required permissions to use this drive"

Googling, it seems that Brasero is very buggy in its MD5 checking:
-[ Bug #87082: Brasero Check disc Integrity how to know if it worked?]("https://answers.launchpad.net/ubuntu/+source/brasero/+question/87082")
- [Bug #224126: brasero does not check integrity]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/224126")
- [Bug #16922 Brasero Cannot Check Integrity]("http://defect.opensolaris.org/bz/show_bug.cgi?id=16922")
etc.

And, even more to the point:
- [Bug #511302 "You do not have the required permissions to use this drive."]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/511302")
- [**     [COLOR=#980101][B][ubuntu]**[/COLOR] Brasero says I don't have permission...[/B]]("http://ubuntuforums.org/showthread.php?t=1523682")
- **[[B]Bug 505582**]("https://bugzilla.redhat.com/show_bug.cgi?id=505582") [/B][Brasero doesn't have the necessary rights to check the checksum of a burned ....         ]("https://bugzilla.redhat.com/show_bug.cgi?id=505582")
etc.

In those bug reports, the developer of Brasero implicates the Ubuntu "wodim", whatever that is.

So, I generated a log file to gather more data about the Ubuntu wodim bug:
```

$ brasero --brasero-burn-debug --brasero-media-debug &> brasero-debug.txt

```Here is an excerpt of that (rather long) Brasero log file:
> BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... giving up.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: WARNING: /dev/sr0 seems to be mounted!
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom: Device or resource busy. Cannot open '/dev/sr0'. Cannot open SCSI driver.
BraseroBurn: (at burn-job.c:113) BraseroReadom called brasero_job_error
BraseroBurn: (at burn-job.c:1140) BraseroReadom finished with an error
BraseroBurn: (at burn-job.c:1174) BraseroReadom asked to stop because of an error
        error           = 4
        message = "**You do not have the required permissions to use this drive**"
BraseroBurn: (at burn-task.c:182) stopping BraseroReadom
BraseroBurn: (at burn-job.c:906) BraseroReadom stopping
BraseroBurn: (at burn-process.c:709) BraseroReadom got killed
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom: For possible targets try '**wodim** -scanbus'. Make sure you are root.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom: For possible transport specifiers try '**wodim** dev=help'.
...
Apparently this so-called 'wodim' bug in Ubuntu hasn't been fixed in a while.

The workaround to this Ubuntu bug, from the developer, is to remove the thing called 'wodim' but I don't understand his instructions:
> Jörg Schilling                                                  2009-07-03 11:34:29 EDT
The fork called wodim is full of well known bugs and
one of the bugs is that is is unable to access non-maiden
media under most circumstances.

For this reason, I recomend you to upgrade to the official
software from:

cdecord.berlios.de
see:
[ftp://ftp.berlios.de/pub/cdrecord/alpha/](ftp://ftp.berlios.de/pub/cdrecord/alpha/)

make sure to manually remove all programs from the fork
so brasero will use the original software.Again and again, the developer blames the Ubuntu "wodim" ...
> Jörg Schilling                                                  2010-01-22 04:49:12 EST
It is a well known fact that there are more than
100 well known bugs in wodim/cdrkit and that no 
maintenance effort is put into this fork. All
known problems with wodim/cdrkit go away if you
upgrade to recent original software.Not all people think this Ubuntu wodim bug is the main culprit though:

For example, from bug report**[[B] 505582**]("https://bugzilla.redhat.com/show_bug.cgi?id=505582") [/B]above:
> ... the problem is that the CD is automatically mounted when Brasero finishes burning. 
Then brasero tries to access it to verify but fails as drive is already used by another program. 

When I disabled automount in nautilus section of gconf the problem went away. 


---

### Post by rocksockdoc on 2012-01-12
It looks like lots of people on Ubuntu have encountered this Ubuntu bug:
[- [Ubuntu Bug 511302] "You do not have the required permissions to use    this drive."]("https://lists.ubuntu.com/archives/ubuntu-burning/2010-January/012485.html")
- [Ubuntu 10.10 - Brasero won't check disk]("http://boardreader.com/thread/Ubuntu_10_10_Brasero_wont_check_disk_8a2asX1axv.html")
- [https://bugs.launchpad.net/bugs/511302](https://bugs.launchpad.net/bugs/511302)
etc.

Since I have this problem well documented, may I ask how I would file my very first Ubuntu bug report?

```

BraseroBurn: (at burn-basics.c:234) Initializing Brasero-burn 2.30.2
BraseroMedia: (at brasero-media.c:533) Initializing Brasero-media 2.30.2
BraseroMedia: (at brasero-medium-monitor.c:657) Probing drives and media
BraseroMedia: (at brasero-medium-monitor.c:662) Found 3 drives
BraseroMedia: (at brasero-medium-monitor.c:378) Testing drive /dev/sda
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:184) No handle: Permission denied
BraseroMedia: (at brasero-medium-monitor.c:378) Testing drive /dev/sdb
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:184) No handle: Permission denied
BraseroMedia: (at brasero-medium-monitor.c:378) Testing drive /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-medium-monitor.c:387) Drive is optical
BraseroMedia: (at brasero-drive.c:1456) Initializing drive /dev/sr0 from device
BraseroMedia: (at brasero-drive.c:1111) Setting GDrive 0x823c4c8
BraseroMedia: (at brasero-drive.c:1327) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at brasero-drive.c:1042) Still initializing the drive properties
BraseroMedia: (at brasero-medium-monitor.c:678) Found 3 volumes
BraseroMedia: (at brasero-medium-monitor.c:378) Testing drive /dev/sda1
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:184) No handle: Permission denied
BraseroMedia: (at brasero-medium-monitor.c:378) Testing drive /dev/sdb1
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:184) No handle: Permission denied
BraseroBurn: (at burn-plugin-manager.c:440) opening plugin directory /usr/lib/brasero/plugins
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-readcd.so
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:1380) Device ready
BraseroMedia: (at brasero-drive.c:1201) Checking supported profiles
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:439) Created new caps Image CLONE 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD ROM closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD ROM closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:439) Created new caps Image BIN 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data 
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"readcd" could not be found in the path
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-mkisofs.so
BraseroMedia: (at brasero-drive.c:1212) Dectected medium is 0x11
BraseroMedia: (at brasero-drive.c:1419) Drive caps are 63
BraseroMedia: (at brasero-drive.c:890) Probing new medium
BraseroMedia: (at brasero-medium.c:3018) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-medium.c:3041) Open () succeeded
BraseroMedia: (at brasero-medium.c:3077) Device ready
BraseroMedia: (at brasero-medium.c:2896) Initializing information for medium in PIONEER DVD-RW  DVR-107D
BraseroMedia: (at brasero-medium.c:2343) Retrieving media profile
BraseroMedia: (at brasero-medium.c:1508) Retrieving media available speeds
BraseroMedia: (at brasero-medium.c:1331) Retrieving speed (Get Performance)
BraseroMedia: (at scsi-get-performance.c:129) Unaligned data (56) setting to max (2048)
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"mkisofs" is a symbolic link pointing to another program
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-cdda2wav.so
BraseroMedia: (at brasero-medium.c:1346) Successfully retrieved a header: size 56, address 0x83a8e78
BraseroMedia: (at brasero-medium.c:1350) Updated header size = 56
BraseroMedia: (at brasero-medium.c:1363) Got 3 descriptor(s)
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 0, address = 0x83a8e80
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 5540
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 1, address = 0x83a8e90
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 2770
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 2, address = 0x83a8ea0
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 1385
BraseroMedia: (at brasero-medium.c:1393) Maximum Speed (mmc3) 5540
BraseroMedia: (at brasero-medium.c:1009) Checking incremental and simulate feature
BraseroMedia: (at scsi-get-configuration.c:127) Unaligned data (20) setting to max (65530)
BraseroMedia: (at scsi-get-configuration.c:162) Sizes mismatch asked 65530 / received 20
BraseroMedia: (at brasero-medium.c:1024) Incremental feature is supported
BraseroMedia: (at brasero-medium.c:1027) Checking (DVD-R(W) simulate)
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with audio 
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"cdda2wav" could not be found in the path
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-cdrecord.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW Metadata Information format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:439) Created new caps Image CUE 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data with audio 
BraseroMedia: (at brasero-medium.c:1043) SAO feature is supported
BraseroMedia: (at brasero-medium.c:1053) Medium can be blanked
BraseroMedia: (at brasero-medium.c:1128) Tested simulation 1 1, burnfree 1
BraseroMedia: (at brasero-medium.c:2261) Retrieving media status
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"cdrecord" is a symbolic link pointing to another program
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-burn-uri.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN CUE CDRDAO CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:439) Created new caps Image CDRDAO 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF SYMLINK Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at burn-plugin.c:1268) Module CD/DVD Creator Folder has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-vob.so
BraseroMedia: (at brasero-medium.c:2209) DVD id 0
BraseroMedia: (at brasero-medium.c:2225) Empty media
BraseroMedia: (at brasero-medium.c:2231) First open track 1
BraseroMedia: (at brasero-medium.c:1869) Retrieving NWA and leadout information
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio MP2 VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW MP2 AC3 Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW MP2 AC3 Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED VIDEO UNDEFINED format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio MP2 VCD Video DVD format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW MP2 AC3 format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW MP2 AC3 
BraseroMedia: (at brasero-medium.c:1938) Next Writable Address is 0
BraseroMedia: (at brasero-medium.c:1945) Free blocks 2297888
BraseroMedia: (at brasero-medium.c:1962) Leadout: start = 0 size = 2297888
BraseroMedia: (at brasero-medium.c:2948) media is DVD - (sequential) W blank 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-checksum.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at burn-plugin.c:1268) Module Image Checksum has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-readom.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-transcode.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW RAW (little endian)Metadata Information format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW RAW (little endian)Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio DTS WAV Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW RAW (little endian)format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW RAW (little endian)
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio DTS WAV format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio DTS WAV 
BraseroBurn: (at burn-plugin.c:1268) Module transcode has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-dvdrwformat.so
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD DL RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD DL RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD DL RW closed with data 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-cdrdao.so
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CDRDAO format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE CDRDAO format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data with audio 
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"toc2cue" could not be found in the path
"cdrdao" could not be found in the path
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-normalize.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED DTS WAV Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED DTS WAV format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED DTS WAV 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-dvdcss.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL ROM closed protected with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD ROM closed protected with data 
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"libdvdcss.so.2" could not be found
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-growisofs.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL POW W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD POW W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL SRM W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD SRM W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (jump) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD RAM RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD RAM RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL POW W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL POW W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD POW W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD POW W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL SRM W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL SRM W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD SRM W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD SRM W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD RAM RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (jump) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (jump) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD RAM RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW closed with data 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-vcdimager.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio MP2 44100 VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio MP2 44100 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio MP2 44100 VCD Video DVD format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio MP2 44100 VCD Video DVD 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-dvdauthor.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW MP2 AC3 Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF VIDEO 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW MP2 AC3 format accepts files 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-checksum-file.so
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF SYMLINK Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at burn-plugin.c:1268) Module File Checksum has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-wodim.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW Metadata Information format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data with audio 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-local-track.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN CUE CDRDAO CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF SYMLINK Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at burn-plugin.c:1268) Module File Downloader has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-audio2cue.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW Metadata Information format accepts files pipe 
BraseroBurn: (at burn-plugin.c:1268) Module audio2cue has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-genisoimage.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at burn-plugin-manager.c:157) Getting list of plugins to be loaded
BraseroBurn: (at burn-plugin.c:331) Plugin genisoimage is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. genisoimage is active
BraseroBurn: (at burn-plugin.c:331) Plugin audio2cue is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. audio2cue is active
BraseroBurn: (at burn-plugin.c:331) Plugin File Downloader is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Downloader active
BraseroBurn: (at burn-plugin.c:331) Plugin wodim is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. wodim is active
BraseroBurn: (at burn-plugin.c:331) Plugin File Checksum is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Checksum active
BraseroBurn: (at burn-plugin.c:331) Plugin dvdauthor is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdauthor is active
BraseroBurn: (at burn-plugin.c:331) Plugin vcdimager is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. vcdimager is active
BraseroBurn: (at burn-plugin.c:331) Plugin growisofs is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. growisofs is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdcss is inactive
BraseroBurn: (at burn-plugin.c:331) Plugin Normalize is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Normalize active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrdao is inactive
BraseroBurn: (at burn-plugin.c:331) Plugin dvd+rw-format is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvd+rw-format is active
BraseroBurn: (at burn-plugin.c:331) Plugin transcode is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode is active
BraseroBurn: (at burn-plugin.c:331) Plugin readom is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readom is active
BraseroBurn: (at burn-plugin.c:331) Plugin Image Checksum is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Image Checksum active
BraseroBurn: (at burn-plugin.c:331) Plugin transcode2vob is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode2vob is active
BraseroBurn: (at burn-plugin.c:331) Plugin CD/DVD Creator Folder is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. CD/DVD Creator Folder is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrecord is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdda2wav is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. mkisofs is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readcd is inactive
BraseroBurn: (at burn-plugin-manager.c:241) Watching GConf plugin key
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc DVD DL - (jump) W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc BD SRM W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc BD DL SRM W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc BD POW W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc BD DL POW W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD RAM RW blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD RAM RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD DL - (jump) W blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD DL + W blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc BD SRM W blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc BD DL SRM W blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc BD POW W blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc BD DL POW W blank 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD ROM closed protected with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD DL ROM closed protected with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD DL - (sequential) W blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD - (restricted) RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD DL + RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD RW blank Unformatted 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD DL RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD DL RW blank Unformatted 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD DL RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 24 links pointing to Disc CD RW blank 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc CD RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc CD RW closed with audio 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc CD RW closed with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc CD RW appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc CD RW appendable with audio 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc CD RW appendable with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 23 links pointing to Disc CD W blank 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD W closed with audio 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD W closed with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc CD W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc CD W appendable with audio 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc CD W appendable with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD ROM closed with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD ROM closed with audio 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD ROM closed with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD ROM closed with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD + RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD + RW blank Unformatted 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD + RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD + W blank 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD + W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD + W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD - (sequential) RW blank 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD - (sequential) W blank 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD - (sequential) W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD DL ROM closed with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD DL + RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD DL + W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc DVD DL + W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 4 links pointing to Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio DTS WAV format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED DTS WAV format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Audio RAW format accepts files pipe 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED VIDEO UNDEFINED format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Audio MP2 VCD Video DVD format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio MP2 44100 VCD Video DVD format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Audio RAW MP2 AC3 format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio DTS WAV Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED DTS WAV Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Audio RAW Metadata Information format accepts pipe 
BraseroBurn: (at burn-basics.c:205) Created 7 links pointing to Audio RAW Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Audio MP2 VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio MP2 44100 VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Audio RAW MP2 AC3 Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Audio RAW RAW (little endian)format accepts files pipe 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Audio RAW RAW (little endian)Metadata Information format accepts files pipe 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 25 links pointing to Image BIN format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 25 links pointing to Image BIN format accepts pipe 
BraseroBurn: (at burn-basics.c:205) Created 21 links pointing to Image CUE format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 15 links pointing to Image CLONE format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 15 links pointing to Image CDRDAO format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Data ISO UDF VIDEO 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Data ISO UDF SYMLINK Level 3 JOLIET VIDEO DEEP 
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroBurn: (at burn-plugin-manager.c:157) Getting list of plugins to be loaded
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. genisoimage is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. audio2cue is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Downloader active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. wodim is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdauthor is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. vcdimager is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. growisofs is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdcss is inactive
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Normalize active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrdao is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvd+rw-format is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readom is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Image Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode2vob is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. CD/DVD Creator Folder is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrecord is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdda2wav is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. mkisofs is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readcd is inactive
BraseroBurn: (at burn-plugin-manager.c:241) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:157) Getting list of plugins to be loaded
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. genisoimage is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. audio2cue is active
BraseroBu
(brasero:10464): GConf-CRITICAL **: gconf_client_set_string: assertion `val != NULL' failed
rn: (at burn-plugin-manager.c:233) Setting plugin File Downloader active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. wodim is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdauthor is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. vcdimager is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. growisofs is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdcss is inactive
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Normalize active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrdao is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvd+rw-format is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readom is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Image Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode2vob is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. CD/DVD Creator Folder is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrecord is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdda2wav is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. mkisofs is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readcd is inactive
BraseroBurn: (at burn-plugin-manager.c:241) Watching GConf plugin key
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroBurn: (at brasero-session.c:2392) Cleaning session
BraseroBurn: (at brasero-track-image.c:198) Image nor toc were set
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:815) No media
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroBurn: (at brasero-track-image.c:198) Image nor toc were set
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, burnproof, no tmp file, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Image 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:1623) FLAGS: not supported
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:258) Searching plugins
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc DVD - (sequential) W blank 
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroBurn: (at burn-basics.c:443) checking media caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-track-image.c:198) Image nor toc were set
BraseroBurn: (at brasero-track-image.c:198) Image nor toc were set
BraseroBurn: (at brasero-track-image.c:198) Image nor toc were set
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroBurn: (at burn-basics.c:443) checking media caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, burnproof, no tmp file, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, burnproof, no tmp file, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Image 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:1623) FLAGS: not supported
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:258) Searching plugins
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:1075) Checking support for session. Ouput is  Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:1076) and input is Image BIN 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 5 links): Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 2 links): Data ISO UDF VIDEO 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio RAW MP2 AC3 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio RAW MP2 AC3 Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-session.c:1098) Session supported Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:308) Testing blanking caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:258) Searching plugins
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-session.c:2037) Available space on medium 2297888
BraseroBurn: (at brasero-session-cfg.c:968) Session size 1308258/Disc size 2297888
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroBurn: (at burn-basics.c:443) checking media caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, burnproof, no tmp file, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, burnproof, no tmp file, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Image BIN 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:258) Searching plugins
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory no tmp file, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Image BIN 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): no tmp file, 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:258) Searching plugins
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory no tmp file, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Image BIN 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): burnproof, no tmp file, 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:258) Searching plugins
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory no tmp file, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Image BIN 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): burnproof, no tmp file, 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:258) Searching plugins
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory no tmp file, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Image BIN 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): eject, no grace, burnproof, no tmp file, check size, 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:258) Searching plugins
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory no tmp file, 
BraseroBurn: (at brasero-caps-session.c:1075) Checking support for session. Ouput is  Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:1076) and input is Image BIN 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 5 links): Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 2 links): Data ISO UDF VIDEO 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio RAW MP2 AC3 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio RAW MP2 AC3 Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-session.c:1098) Session supported Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-session.c:2235) Session starting:
BraseroBurn: (at brasero-session.c:2240) Input    = Image BIN 
BraseroBurn: (at brasero-session.c:2241) flags    = eject, no grace, burnproof, no tmp file, check size, 
BraseroBurn: (at brasero-session.c:2283) media type    = Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-session.c:2284) speed    = 5540000
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroMedia: (at brasero-volume.c:197) Mount point is (null)
BraseroBurn: (at brasero-burn.c:798) Media inserted is Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:1075) Checking support for session. Ouput is  Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:1076) and input is Image BIN 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 5 links): Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 2 links): Data ISO UDF VIDEO 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio RAW MP2 AC3 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio RAW MP2 AC3 Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-session.c:1098) Session supported Disc DVD - (sequential) W blank 
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:527) Device locked
BraseroBurn: (at brasero-burn.c:1741) Checking session consistency
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Image BIN 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:258) Searching plugins
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory no tmp file, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Image BIN 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): check size, 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:258) Searching plugins
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory no tmp file, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Image BIN 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:258) Searching plugins
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory no tmp file, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Image BIN 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): eject, no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:258) Searching plugins
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory no tmp file, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Image BIN 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): eject, no grace, burnproof, check size, 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:258) Searching plugins
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory no tmp file, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Image BIN 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): eject, no grace, burnproof, no tmp file, check size, 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:258) Searching plugins
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory no tmp file, 
BraseroBurn: (at brasero-burn.c:1839) Flags after checking = eject, no grace, burnproof, no tmp file, check size, 
BraseroBurn: (at brasero-caps-session.c:1075) Checking support for session. Ouput is  Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:1076) and input is Image BIN 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 5 links): Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 2 links): Data ISO UDF VIDEO 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio RAW MP2 AC3 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio RAW MP2 AC3 Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-session.c:1098) Session supported Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-burn.c:674) Creating recording/imaging task Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-burn.c:684) Input set = Image BIN 
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Image BIN 
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Image BIN 
BraseroBurn: (at brasero-caps-burn.c:440) Trying growisofs with a priority of 7
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Image BIN 
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:423) No links found
BraseroBurn: (at brasero-caps-burn.c:440) Trying growisofs with a priority of 7
BraseroBurn: (at brasero-caps-burn.c:580) Adding modifiers (position 1) (3 modifiers available) for Image BIN format accepts files 
BraseroBurn: (at brasero-caps-burn.c:623) Image Checksum (modifier) added to task
BraseroBurn: (at brasero-caps-burn.c:625) IO type Image BIN 
BraseroBurn: (at brasero-caps-burn.c:623) File Downloader (modifier) added to task
BraseroBurn: (at brasero-caps-burn.c:625) IO type Image BIN 
BraseroBurn: (at brasero-caps-burn.c:623) CD/DVD Creator Folder (modifier) added to task
BraseroBurn: (at brasero-caps-burn.c:625) IO type Image BIN 
BraseroBurn: (at brasero-caps-burn.c:818) New task
BraseroBurn: (at brasero-caps-burn.c:828) growisofs added to task
BraseroBurn: (at brasero-caps-burn.c:829) input Image BIN 
BraseroBurn: (at brasero-caps-burn.c:830) output Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-burn.c:2074) 4 tasks to perform
BraseroBurn: (at burn-task.c:600) Starting fake task (2)
BraseroBurn: (at burn-task-ctx.c:159) Setting current track (1 tracks)
BraseroBurn: (at burn-task.c:336) ::activate method BraseroBurnURI
BraseroBurn: (at burn-job.c:352) no ::activate method BraseroBurnURI
BraseroBurn: (at burn-task.c:293) ::start method BraseroBurnURI
BraseroBurn: (at burn-job.c:1433) BraseroBurnURI called brasero_job_get_action
BraseroBurn: (at burn-job.c:1433) BraseroBurnURI called brasero_job_get_action
BraseroBurn: (at burn-job.c:1925) BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurn: (at burn-task-ctx.c:607) Task output modified 0 blocks 0 bytes
BraseroBurn: (at burn-task.c:628) current track skipped
BraseroBurn: (at burn-task-ctx.c:357) No next track to process
BraseroBurn: (at burn-task.c:182) stopping BraseroBurnURI
BraseroBurn: (at burn-job.c:906) BraseroBurnURI stopping
BraseroBurn: (at burn-task.c:190) stopped BraseroBurnURI
BraseroBurn: (at brasero-burn.c:2202) Burning from 0 to 0
BraseroBurn: (at burn-task.c:600) Starting normal task (0)
BraseroBurn: (at burn-task-ctx.c:159) Setting current track (1 tracks)
BraseroBurn: (at burn-task.c:336) ::activate method BraseroBurnURI
BraseroBurn: (at burn-job.c:352) no ::activate method BraseroBurnURI
BraseroBurn: (at burn-task.c:293) ::start method BraseroBurnURI
BraseroBurn: (at burn-job.c:1433) BraseroBurnURI called brasero_job_get_action
BraseroBurn: (at burn-job.c:1790) BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurn: (at burn-job.c:659) BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_9G6P7V.bin toc = none
BraseroBurn: (at burn-job.c:511) ext3/ext4 filesystem detected
BraseroBurn: (at burn-job.c:1790) BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurn: (at burn-job.c:530) Volume size 3184558080, output size 0
BraseroBurn: (at burn-job.c:1433) BraseroBurnURI called brasero_job_get_action
BraseroBurn: (at burn-job.c:1270) BraseroBurnURI called brasero_job_get_current_track
BraseroBurn: (at burn-uri.c:655) BraseroBurnURI no burn:// URI found
BraseroBurn: (at burn-task.c:628) current track skipped
BraseroBurn: (at burn-task-ctx.c:357) No next track to process
BraseroBurn: (at burn-task.c:182) stopping BraseroBurnURI
BraseroBurn: (at burn-job.c:906) BraseroBurnURI stopping
BraseroBurn: (at burn-task.c:190) stopped BraseroBurnURI
BraseroBurn: (at burn-task.c:600) Starting fake task (2)
BraseroBurn: (at burn-task-ctx.c:159) Setting current track (1 tracks)
BraseroBurn: (at burn-task.c:336) ::activate method BraseroLocalTrack
BraseroBurn: (at burn-job.c:352) no ::activate method BraseroLocalTrack
BraseroBurn: (at burn-task.c:293) ::start method BraseroLocalTrack
BraseroBurn: (at burn-job.c:1433) BraseroLocalTrack called brasero_job_get_action
BraseroBurn: (at burn-job.c:1433) BraseroLocalTrack called brasero_job_get_action
BraseroBurn: (at burn-job.c:1925) BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroBurn: (at burn-task-ctx.c:607) Task output modified 0 blocks 0 bytes
BraseroBurn: (at burn-task.c:628) current track skipped
BraseroBurn: (at burn-task-ctx.c:357) No next track to process
BraseroBurn: (at burn-task.c:182) stopping BraseroLocalTrack
BraseroBurn: (at burn-job.c:906) BraseroLocalTrack stopping
BraseroBurn: (at burn-task.c:190) stopped BraseroLocalTrack
BraseroBurn: (at brasero-burn.c:2202) Burning from 0 to 0
BraseroBurn: (at burn-task.c:600) Starting normal task (0)
BraseroBurn: (at burn-task-ctx.c:159) Setting current track (1 tracks)
BraseroBurn: (at burn-task.c:336) ::activate method BraseroLocalTrack
BraseroBurn: (at burn-job.c:352) no ::activate method BraseroLocalTrack
BraseroBurn: (at burn-task.c:293) ::start method BraseroLocalTrack
BraseroBurn: (at burn-job.c:1433) BraseroLocalTrack called brasero_job_get_action
BraseroBurn: (at burn-job.c:1790) BraseroLocalTrack called brasero_job_get_session_output_size
BraseroBurn: (at burn-job.c:659) BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_H56P7V.bin toc = none
BraseroBurn: (at burn-job.c:511) ext3/ext4 filesystem detected
BraseroBurn: (at burn-job.c:1790) BraseroLocalTrack called brasero_job_get_session_output_size
BraseroBurn: (at burn-job.c:530) Volume size 3184558080, output size 0
BraseroBurn: (at burn-job.c:1433) BraseroLocalTrack called brasero_job_get_action
BraseroBurn: (at burn-job.c:1270) BraseroLocalTrack called brasero_job_get_current_track
BraseroBurn: (at burn-local-image.c:777) BraseroLocalTrack no remote URIs
BraseroBurn: (at burn-task.c:628) current track skipped
BraseroBurn: (at burn-task-ctx.c:357) No next track to process
BraseroBurn: (at burn-task.c:182) stopping BraseroLocalTrack
BraseroBurn: (at burn-job.c:906) BraseroLocalTrack stopping
BraseroBurn: (at burn-task.c:190) stopped BraseroLocalTrack
BraseroBurn: (at burn-task.c:600) Starting fake task (2)
BraseroBurn: (at burn-task-ctx.c:159) Setting current track (1 tracks)
BraseroBurn: (at burn-task.c:336) ::activate method BraseroChecksumImage
BraseroBurn: (at burn-job.c:1270) BraseroChecksumImage called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:1377) BraseroChecksumImage called brasero_job_get_flags
BraseroBurn: (at burn-task.c:293) ::start method BraseroChecksumImage
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:1190) BraseroChecksumImage called brasero_job_get_fd_in
BraseroBurn: (at burn-job.c:1925) BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroBurn: (at burn-task-ctx.c:607) Task output modified 0 blocks 0 bytes
BraseroBurn: (at burn-task.c:628) current track skipped
BraseroBurn: (at burn-task-ctx.c:357) No next track to process
BraseroBurn: (at burn-task.c:182) stopping BraseroChecksumImage
BraseroBurn: (at burn-job.c:906) BraseroChecksumImage stopping
BraseroBurn: (at burn-task.c:190) stopped BraseroChecksumImage
BraseroBurn: (at brasero-burn.c:2202) Burning from 0 to 0
BraseroBurn: (at burn-task.c:600) Starting normal task (0)
BraseroBurn: (at burn-task-ctx.c:159) Setting current track (1 tracks)
BraseroBurn: (at burn-task.c:336) ::activate method BraseroChecksumImage
BraseroBurn: (at burn-job.c:1270) BraseroChecksumImage called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-checksum-image.c:687) BraseroChecksumImage There is a checksum already 0
BraseroBurn: (at burn-task.c:522) ::start skipped for BraseroChecksumImage
BraseroBurn: (at burn-task.c:619) Task skipped
BraseroBurn: (at burn-task.c:600) Starting fake task (2)
BraseroBurn: (at burn-task-ctx.c:159) Setting current track (1 tracks)
BraseroBurn: (at burn-task.c:336) ::activate method BraseroGrowisofs
BraseroBurn: (at burn-job.c:352) no ::activate method BraseroGrowisofs
BraseroBurn: (at burn-task.c:293) ::start method BraseroGrowisofs
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-process.c:129) BraseroGrowisofs getting varg
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1270) BraseroGrowisofs called brasero_job_get_current_track
BraseroBurn: (at burn-process.c:142) BraseroGrowisofs got varg:
BraseroBurn: (at burn-job.c:258) BraseroGrowisofs deactivating
BraseroBurn: (at burn-task.c:556) BraseroGrowisofs doesn't support action
BraseroBurn: (at burn-task.c:479) Trying to set a default output size
BraseroBurn: (at burn-task.c:496) Got a default image or stream track length 1308258
BraseroBurn: (at burn-task-ctx.c:607) Task output modified 1308258 blocks 2679312384 bytes
BraseroBurn: (at burn-task.c:628) current track skipped
BraseroBurn: (at burn-task-ctx.c:357) No next track to process
BraseroBurn: (at burn-task.c:177) BraseroGrowisofs already stopped
BraseroBurn: (at brasero-burn.c:2202) Burning from 0 to 1308258
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroMedia: (at brasero-volume.c:197) Mount point is (null)
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroBurn: (at burn-task.c:600) Starting normal task (0)
BraseroBurn: (at burn-task-ctx.c:159) Setting current track (1 tracks)
BraseroBurn: (at burn-task.c:336) ::activate method BraseroGrowisofs
BraseroBurn: (at burn-job.c:352) no ::activate method BraseroGrowisofs
BraseroBurn: (at burn-task.c:293) ::start method BraseroGrowisofs
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-process.c:129) BraseroGrowisofs getting varg
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1377) BraseroGrowisofs called brasero_job_get_flags
BraseroBurn: (at burn-job.c:1634) BraseroGrowisofs called brasero_job_get_speed
BraseroBurn: (at burn-job.c:1501) BraseroGrowisofs called brasero_job_get_device
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1790) BraseroGrowisofs called brasero_job_get_session_output_size
BraseroBurn: (at burn-job.c:1270) BraseroGrowisofs called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1190) BraseroGrowisofs called brasero_job_get_fd_in
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:142) BraseroGrowisofs got varg:
BraseroBurn: (at burn-process.c:146)     growisofs
BraseroBurn: (at burn-process.c:146)     -use-the-force-luke=notray
BraseroBurn: (at burn-process.c:146)     -use-the-force-luke=4gms
BraseroBurn: (at burn-process.c:146)     -dvd-compat
BraseroBurn: (at burn-process.c:146)     -speed=4
BraseroBurn: (at burn-process.c:146)     -use-the-force-luke=tracksize:1308258
BraseroBurn: (at burn-process.c:146)     -use-the-force-luke=tty
BraseroBurn: (at burn-process.c:146)     -Z
BraseroBurn: (at burn-process.c:146)     /dev/sr0=/media/My Passport/movies/iso_images/movie/movie.iso
BraseroBurn: (at burn-process.c:626) BraseroGrowisofs Launching command
BraseroBurn: (at burn-job.c:1312) BraseroGrowisofs called brasero_job_get_fd_out
BraseroBurn: (at burn-task.c:442) entering loop
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout: Executing 'builtin_dd if=/media/My Passport/movies/iso_images/movie/movie.iso of=/dev/sr0 obs=32k seek=0'
BraseroBurn: (at burn-job.c:1988) BraseroGrowisofs called brasero_job_set_dangerous
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 4.1x1352KBps.
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:    12845056/2679312384 ( 0.5%) @2.4x, remaining 13:50 RBU 100.0% UBU   2.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:    31358976/2679312384 ( 1.2%) @4.0x, remaining 11:15 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:    49840128/2679312384 ( 1.9%) @4.0x, remaining 9:40 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:    68288512/2679312384 ( 2.5%) @4.0x, remaining 8:55 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:    86769664/2679312384 ( 3.2%) @4.0x, remaining 8:57 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   105283584/2679312384 ( 3.9%) @4.0x, remaining 8:33 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   123764736/2679312384 ( 4.6%) @4.0x, remaining 8:15 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   142245888/2679312384 ( 5.3%) @4.0x, remaining 8:19 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   160727040/2679312384 ( 6.0%) @4.0x, remaining 8:05 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   179208192/2679312384 ( 6.7%) @4.0x, remaining 7:54 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   197689344/2679312384 ( 7.4%) @4.0x, remaining 7:57 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   216170496/2679312384 ( 8.1%) @4.0x, remaining 7:47 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   234651648/2679312384 ( 8.8%) @4.0x, remaining 7:38 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   253132800/2679312384 ( 9.4%) @4.0x, remaining 7:40 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   271613952/2679312384 (10.1%) @4.0x, remaining 7:32 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   290095104/2679312384 (10.8%) @4.0x, remaining 7:24 RBU 100.0% UBU  95.9%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   308576256/2679312384 (11.5%) @4.0x, remaining 7:25 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   327057408/2679312384 (12.2%) @4.0x, remaining 7:18 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   345538560/2679312384 (12.9%) @4.0x, remaining 7:12 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   364052480/2679312384 (13.6%) @4.0x, remaining 7:12 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   382533632/2679312384 (14.3%) @4.0x, remaining 7:06 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   401014784/2679312384 (15.0%) @4.0x, remaining 7:00 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   419495936/2679312384 (15.7%) @4.0x, remaining 7:00 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   437977088/2679312384 (16.3%) @4.0x, remaining 6:54 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   456458240/2679312384 (17.0%) @4.0x, remaining 6:49 RBU 100.0% UBU  95.9%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   474939392/2679312384 (17.7%) @4.0x, remaining 6:48 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   493420544/2679312384 (18.4%) @4.0x, remaining 6:43 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   511901696/2679312384 (19.1%) @4.0x, remaining 6:37 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   530415616/2679312384 (19.8%) @4.0x, remaining 6:37 RBU  99.9% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   548896768/2679312384 (20.5%) @4.0x, remaining 6:32 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   567345152/2679312384 (21.2%) @4.0x, remaining 6:27 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   585826304/2679312384 (21.9%) @4.0x, remaining 6:25 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   604340224/2679312384 (22.6%) @4.0x, remaining 6:21 RBU 100.0% UBU  95.9%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   622788608/2679312384 (23.2%) @4.0x, remaining 6:16 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   641302528/2679312384 (23.9%) @4.0x, remaining 6:14 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   659783680/2679312384 (24.6%) @4.0x, remaining 6:10 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   678264832/2679312384 (25.3%) @4.0x, remaining 6:05 RBU 100.0% UBU  95.9%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   696745984/2679312384 (26.0%) @4.0x, remaining 6:04 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   715227136/2679312384 (26.7%) @4.0x, remaining 5:59 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   733708288/2679312384 (27.4%) @4.0x, remaining 5:55 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   752189440/2679312384 (28.1%) @4.0x, remaining 5:53 RBU 100.0% UBU  95.9%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   770670592/2679312384 (28.8%) @4.0x, remaining 5:49 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   789184512/2679312384 (29.5%) @4.0x, remaining 5:44 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   807665664/2679312384 (30.1%) @4.0x, remaining 5:42 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   826146816/2679312384 (30.8%) @4.0x, remaining 5:38 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   844627968/2679312384 (31.5%) @4.0x, remaining 5:34 RBU 100.0% UBU  93.9%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   863109120/2679312384 (32.2%) @4.0x, remaining 5:32 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   881590272/2679312384 (32.9%) @4.0x, remaining 5:28 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   900071424/2679312384 (33.6%) @4.0x, remaining 5:24 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   918552576/2679312384 (34.3%) @4.0x, remaining 5:22 RBU 100.0% UBU  95.9%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   937033728/2679312384 (35.0%) @4.0x, remaining 5:17 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   955514880/2679312384 (35.7%) @4.0x, remaining 5:13 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   973996032/2679312384 (36.4%) @4.0x, remaining 5:11 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:   992477184/2679312384 (37.0%) @4.0x, remaining 5:07 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1010958336/2679312384 (37.7%) @4.0x, remaining 5:03 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1029439488/2679312384 (38.4%) @4.0x, remaining 5:01 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1047920640/2679312384 (39.1%) @4.0x, remaining 4:57 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1066434560/2679312384 (39.8%) @4.0x, remaining 4:53 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1084915712/2679312384 (40.5%) @4.0x, remaining 4:50 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1103396864/2679312384 (41.2%) @4.0x, remaining 4:47 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1121878016/2679312384 (41.9%) @4.0x, remaining 4:43 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1140359168/2679312384 (42.6%) @4.0x, remaining 4:40 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1158840320/2679312384 (43.3%) @4.0x, remaining 4:36 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1177321472/2679312384 (43.9%) @4.0x, remaining 4:33 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1195802624/2679312384 (44.6%) @4.0x, remaining 4:30 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1214283776/2679312384 (45.3%) @4.0x, remaining 4:26 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1232797696/2679312384 (46.0%) @4.0x, remaining 4:22 RBU  99.9% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1251278848/2679312384 (46.7%) @4.0x, remaining 4:20 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1269760000/2679312384 (47.4%) @4.0x, remaining 4:16 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1288241152/2679312384 (48.1%) @4.0x, remaining 4:13 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1306722304/2679312384 (48.8%) @4.0x, remaining 4:09 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1325203456/2679312384 (49.5%) @4.0x, remaining 4:06 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1343684608/2679312384 (50.2%) @4.0x, remaining 4:03 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1362165760/2679312384 (50.8%) @4.0x, remaining 3:59 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1380646912/2679312384 (51.5%) @4.0x, remaining 3:56 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1399160832/2679312384 (52.2%) @4.0x, remaining 3:53 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1417641984/2679312384 (52.9%) @4.0x, remaining 3:49 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1436123136/2679312384 (53.6%) @4.0x, remaining 3:45 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1454604288/2679312384 (54.3%) @4.0x, remaining 3:43 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1473085440/2679312384 (55.0%) @4.0x, remaining 3:39 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1491566592/2679312384 (55.7%) @4.0x, remaining 3:35 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1510047744/2679312384 (56.4%) @4.0x, remaining 3:32 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1528528896/2679312384 (57.0%) @4.0x, remaining 3:29 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1547010048/2679312384 (57.7%) @4.0x, remaining 3:25 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1565491200/2679312384 (58.4%) @4.0x, remaining 3:22 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1583972352/2679312384 (59.1%) @4.0x, remaining 3:19 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1602453504/2679312384 (59.8%) @4.0x, remaining 3:15 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1620934656/2679312384 (60.5%) @4.0x, remaining 3:12 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1639415808/2679312384 (61.2%) @4.0x, remaining 3:09 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1657896960/2679312384 (61.9%) @4.0x, remaining 3:05 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1676410880/2679312384 (62.6%) @4.0x, remaining 3:02 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1694859264/2679312384 (63.3%) @4.0x, remaining 2:58 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1713340416/2679312384 (63.9%) @4.0x, remaining 2:55 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1731854336/2679312384 (64.6%) @4.0x, remaining 2:52 RBU 100.0% UBU  95.9%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1750335488/2679312384 (65.3%) @4.0x, remaining 2:48 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1768816640/2679312384 (66.0%) @4.0x, remaining 2:45 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1787297792/2679312384 (66.7%) @4.0x, remaining 2:42 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1805778944/2679312384 (67.4%) @4.0x, remaining 2:38 RBU 100.0% UBU  95.9%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1824260096/2679312384 (68.1%) @4.0x, remaining 2:35 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1842741248/2679312384 (68.8%) @4.0x, remaining 2:32 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1861222400/2679312384 (69.5%) @4.0x, remaining 2:28 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1879703552/2679312384 (70.2%) @4.0x, remaining 2:25 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1898184704/2679312384 (70.8%) @4.0x, remaining 2:21 RBU 100.0% UBU  95.9%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1916665856/2679312384 (71.5%) @4.0x, remaining 2:18 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1935147008/2679312384 (72.2%) @4.0x, remaining 2:14 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1953628160/2679312384 (72.9%) @4.0x, remaining 2:11 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1972109312/2679312384 (73.6%) @4.0x, remaining 2:08 RBU 100.0% UBU  95.9%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  1990590464/2679312384 (74.3%) @4.0x, remaining 2:04 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2009071616/2679312384 (75.0%) @4.0x, remaining 2:01 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2027552768/2679312384 (75.7%) @4.0x, remaining 1:58 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2046033920/2679312384 (76.4%) @4.0x, remaining 1:54 RBU 100.0% UBU  95.9%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2064515072/2679312384 (77.1%) @4.0x, remaining 1:51 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2082996224/2679312384 (77.7%) @4.0x, remaining 1:48 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2101477376/2679312384 (78.4%) @4.0x, remaining 1:44 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2119958528/2679312384 (79.1%) @4.0x, remaining 1:41 RBU 100.0% UBU  95.9%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2138439680/2679312384 (79.8%) @4.0x, remaining 1:38 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2156953600/2679312384 (80.5%) @4.0x, remaining 1:34 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2175434752/2679312384 (81.2%) @4.0x, remaining 1:31 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2193883136/2679312384 (81.9%) @4.0x, remaining 1:28 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2212364288/2679312384 (82.6%) @4.0x, remaining 1:24 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2230878208/2679312384 (83.3%) @4.0x, remaining 1:21 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2249359360/2679312384 (84.0%) @4.0x, remaining 1:17 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2267840512/2679312384 (84.6%) @4.0x, remaining 1:14 RBU  99.9% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2286321664/2679312384 (85.3%) @4.0x, remaining 1:11 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2304802816/2679312384 (86.0%) @4.0x, remaining 1:07 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2323283968/2679312384 (86.7%) @4.0x, remaining 1:04 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2341765120/2679312384 (87.4%) @4.0x, remaining 1:01 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2360246272/2679312384 (88.1%) @4.0x, remaining 0:57 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2378760192/2679312384 (88.8%) @4.0x, remaining 0:54 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2397208576/2679312384 (89.5%) @4.0x, remaining 0:51 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2415689728/2679312384 (90.2%) @4.0x, remaining 0:47 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2434170880/2679312384 (90.9%) @4.0x, remaining 0:44 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2452652032/2679312384 (91.5%) @4.0x, remaining 0:41 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2471133184/2679312384 (92.2%) @4.0x, remaining 0:37 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2489614336/2679312384 (92.9%) @4.0x, remaining 0:34 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2508128256/2679312384 (93.6%) @4.0x, remaining 0:31 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2526609408/2679312384 (94.3%) @4.0x, remaining 0:27 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2545090560/2679312384 (95.0%) @4.0x, remaining 0:24 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2563571712/2679312384 (95.7%) @4.0x, remaining 0:20 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2582052864/2679312384 (96.4%) @4.0x, remaining 0:17 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2600534016/2679312384 (97.1%) @4.0x, remaining 0:14 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2619015168/2679312384 (97.7%) @4.0x, remaining 0:10 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2637496320/2679312384 (98.4%) @4.0x, remaining 0:07 RBU 100.0% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stdout:  2655977472/2679312384 (99.1%) @4.0x, remaining 0:04 RBU  69.6% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-pro
(brasero:10464): GConf-CRITICAL **: gconf_client_set_string: assertion `val != NULL' failed
cess.c:417) BraseroGrowisofs stdout:  2674491392/2679312384 (99.8%) @4.0x, remaining 0:00 RBU  14.5% UBU  98.0%
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stderr: /dev/sr0: flushing cache
BraseroBurn: (at burn-job.c:1861) BraseroGrowisofs called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stderr: /dev/sr0: updating RMA
BraseroBurn: (at burn-process.c:417) BraseroGrowisofs stderr: /dev/sr0: closing disc
BraseroBurn: (at burn-process.c:450) BraseroGrowisofs stderr: HUP
BraseroBurn: (at burn-process.c:450) BraseroGrowisofs stdout: HUP
BraseroBurn: (at burn-process.c:301) BraseroGrowisofs process finished with status 0
BraseroBurn: (at burn-job.c:1018) BraseroGrowisofs Finished successfully session
BraseroBurn: (at burn-task.c:182) stopping BraseroGrowisofs
BraseroBurn: (at burn-job.c:906) BraseroGrowisofs stopping
BraseroBurn: (at burn-job.c:1284) BraseroGrowisofs called brasero_job_get_done_tracks
BraseroBurn: (at burn-job.c:1312) BraseroGrowisofs called brasero_job_get_fd_out
BraseroBurn: (at burn-job.c:1433) BraseroGrowisofs called brasero_job_get_action
BraseroBurn: (at burn-task.c:190) stopped BraseroGrowisofs
BraseroBurn: (at burn-task.c:448) got out of loop
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:567) Device unlocked
BraseroBurn: (at brasero-burn.c:389) Ejecting drive/medium
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroMedia: (at brasero-volume.c:197) Mount point is (null)
BraseroBurn: (at brasero-burn.c:440) Retrying ejection
BraseroMedia: (at brasero-drive.c:280) Trying to eject drive
BraseroMedia: (at brasero-gio-operation.c:111) Waiting for end of async operation
BraseroMedia: (at brasero-drive.c:1075) Waiting for next unlocking of the drive to probe
BraseroMedia: (at brasero-drive.c:1052) Setting new probe
BraseroMedia: (at brasero-drive.c:952) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at brasero-medium-monitor.c:639) Drive removal signal
BraseroMedia: (at brasero-medium-monitor.c:588) Found device to remove
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-medium-monitor.c:612) Volume removal signal
BraseroMedia: (at brasero-drive.c:983) No medium inserted
BraseroMedia: (at brasero-drive.c:903) Medium removed
BraseroMedia: (at brasero-medium-monitor.c:477) GDrive addition signal
BraseroMedia: (at brasero-medium-monitor.c:442) Added signal was emitted but the drive is in the removal list. Updating GDrive associated object.
BraseroMedia: (at brasero-drive.c:1111) Setting GDrive 0x8977150
BraseroMedia: (at brasero-drive.c:1052) Setting new probe
BraseroMedia: (at brasero-drive.c:952) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:983) No medium inserted
BraseroBurn: (at brasero-burn.c:2845) Session successfully finished
BraseroBurn: (at brasero-session.c:2392) Cleaning session
BraseroBurn: (at brasero-session.c:2369) Cleaning /tmp/brasero_tmp_H56P7V.bin
BraseroBurn: (at brasero-session.c:2369) Cleaning /tmp/brasero_tmp_9G6P7V.bin
BraseroMedia: (at brasero-drive.c:1088) GDrive changed
BraseroMedia: (at brasero-drive.c:1052) Setting new probe
BraseroMedia: (at brasero-drive.c:952) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:1013) Medium inserted
BraseroMedia: (at brasero-drive.c:890) Probing new medium
BraseroMedia: (at brasero-medium-monitor.c:639) Drive removal signal
BraseroMedia: (at brasero-medium-monitor.c:588) Found device to remove
BraseroMedia: (at brasero-medium.c:3018) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-medium.c:3041) Open () succeeded
BraseroMedia: (at brasero-medium.c:3077) Device ready
BraseroMedia: (at brasero-medium.c:2896) Initializing information for medium in PIONEER DVD-RW  DVR-107D
BraseroMedia: (at brasero-medium.c:2343) Retrieving media profile
BraseroMedia: (at brasero-medium.c:1508) Retrieving media available speeds
BraseroMedia: (at brasero-medium.c:1331) Retrieving speed (Get Performance)
BraseroMedia: (at scsi-get-performance.c:129) Unaligned data (56) setting to max (2048)
BraseroMedia: (at brasero-medium.c:1346) Successfully retrieved a header: size 56, address 0x8514500
BraseroMedia: (at brasero-medium.c:1350) Updated header size = 56
BraseroMedia: (at brasero-medium.c:1363) Got 3 descriptor(s)
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 0, address = 0x8514508
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 5540
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 1, address = 0x8514518
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 2770
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 2, address = 0x8514528
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 1385
BraseroMedia: (at brasero-medium.c:1393) Maximum Speed (mmc3) 5540
BraseroMedia: (at brasero-medium.c:1009) Checking incremental and simulate feature
BraseroMedia: (at scsi-get-configuration.c:127) Unaligned data (20) setting to max (65530)
BraseroMedia: (at scsi-get-configuration.c:162) Sizes mismatch asked 65530 / received 20
BraseroMedia: (at brasero-medium.c:1024) Incremental feature is not supported
BraseroMedia: (at brasero-medium.c:1027) Checking (DVD-R(W) simulate)
BraseroMedia: (at brasero-medium-monitor.c:477) GDrive addition signal
BraseroMedia: (at brasero-medium-monitor.c:442) Added signal was emitted but the drive is in the removal list. Updating GDrive associated object.
BraseroMedia: (at brasero-drive.c:1111) Setting GDrive 0x8820a48
BraseroMedia: (at brasero-drive.c:1052) Setting new probe
BraseroMedia: (at brasero-medium.c:1043) SAO feature is not supported
BraseroMedia: (at brasero-medium.c:1053) Medium can be blanked
BraseroMedia: (at brasero-medium.c:1128) Tested simulation 1 1, burnfree 1
BraseroMedia: (at brasero-medium.c:2261) Retrieving media status
BraseroMedia: (at brasero-drive.c:952) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:1013) Medium inserted
BraseroMedia: (at brasero-medium.c:2209) DVD id 28489
BraseroMedia: (at brasero-medium.c:2321) Closed media
BraseroMedia: (at brasero-medium.c:2028) Reading Toc
BraseroMedia: (at brasero-medium.c:2068) 2 track(s) found
BraseroMedia: (at brasero-medium.c:1651) Retrieving track information for 1
BraseroMedia: (at brasero-medium.c:1761) Track 1 (session 1): type = 1 start = 0 size = 1308272
BraseroMedia: (at brasero-medium.c:2076) Leadout reached 1308272
BraseroMedia: (at brasero-medium.c:2587) Testing for Css encrypted media
BraseroMedia: (at brasero-medium-monitor.c:492) GVolume addition signal
BraseroMedia: (at brasero-medium-monitor.c:500) Existing GDrive skipping
BraseroMedia: (at brasero-medium.c:2948) media is DVD ROM closed with data 
BraseroMedia: (at brasero-drive.c:886) Already a medium. Skipping
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroBurn: (at brasero-burn.c:2257) Starting to check track integrity
BraseroBurn: (at brasero-caps-burn.c:878) Creating checksuming task with input Disc DVD ROM closed with data 
BraseroBurn: (at brasero-caps-burn.c:931) Trying link to Image BIN 
BraseroBurn: (at brasero-ca
** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_current_track


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_action


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_flags


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_action


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage creating input


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_action


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_a
** (br
** (brasero:10464): WARNING **: Some log data could not be w
** (br
** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job
** (brasero:10464):
** (brasero:10464): WARNING **: Some log data c
** (brasero:10464):
** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroC
** (brasero:10464): WARNING **: Some log data could
** (brasero:104
** (brasero:10464): WARNING **: Some log data could
** (brasero:10464): WARNING **: Some log data couldn't be wr
** (brasero:10464): WARNING **: Some log data could not be writte
*
** (brasero:10464): WARNING **: Some log data couldn't be written
** (brasero:10464): WARNING **: Some log data couldn'
** (brasero:10464): WARNING **: Some log data could not be writt
**
** (brasero:10464): WARNING **: Some log data couldn't be writte
(brasero:10464): GLib-GObject-CRITICAL **: g_value_get_uint64: assertion `G_VALUE_HOLDS_UINT64 (value)' failed

(brasero:10464): GLib-GObject-CRITICAL **: g_value_get_uint64: assertion `G_VALUE_HOLDS_UINT64 (value)' failed

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumIm
** (brasero:10464): WARNING **: Some log data cou
** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: 
** (brasero:10464): WARNING **: Some log data couldn't b
** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: Br
** (brasero:10464): WARNING **: Some log data co
** (brasero:10464): WARNING **: Some log data could not be writ
** 
** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_fd_out


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_fd_in


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_fd_out


** (brasero:10464): WARNING **: Some log data could not be written
 brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:440) Trying readom with a priority of 1
BraseroBurn: (at brasero-caps-burn.c:1021) readom added to task
BraseroBurn: (at burn-task.c:600) Starting normal task (3)
BraseroBurn: (at burn-task-ctx.c:159) Setting current track (1 tracks)
BraseroBurn: (at burn-task.c:336) ::activate method BraseroReadom
BraseroBurn: (at burn-job.c:352) no ::activate method BraseroReadom
BraseroBurn: (at burn-task.c:336) ::activate method BraseroChecksumImage
BraseroBurn: (at burn-job.c:1270) BraseroChecksumImage called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:1377) BraseroChecksumImage called brasero_job_get_flags
BraseroBurn: (at burn-task.c:293) ::start method BraseroChecksumImage
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:758) BraseroChecksumImage creating input
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-task.c:293) ::start method BraseroReadom
BraseroBurn: (at burn-job.c:1433) BraseroReadom called brasero_job_get_action
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:753) BraseroReadom linked to BraseroChecksumImage
BraseroBurn: (at burn-job.c:1270) BraseroChecksumImage called brasero_job_get_current_track
BraseroBurn: (at burn-process.c:129) BraseroReadom getting varg
BraseroBurn: (at burn-job.c:1861) BraseroChecksumImage called brasero_job_set_current_action
BraseroBurn: (at burn-job.c:1433) BraseroReadom called brasero_job_get_action
BraseroBurn: (at burn-job.c:1270) BraseroChecksumImage called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1270) BraseroReadom called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1190) BraseroChecksumImage called brasero_job_get_fd_in
BraseroBurn: (at burn-job.c:1419) BraseroReadom called brasero_job_get_output_type
BraseroBurn: (at burn-job.c:1270) BraseroReadom called brasero_job_get_current_track
BraseroBurn: (at burn-checksum-image.c:256) BraseroChecksumImage Starting checksum generation live (size = 0)
BraseroBurn: (at burn-job.c:1419) BraseroReadom called brasero_job_get_output_type
BraseroBurn: (at burn-job.c:1243) BraseroChecksumImage called brasero_job_set_nonblocking
BraseroBurn: (at burn-readom.c:225) BraseroReadom reading last track from sector 0 to 1308272
BraseroBurn: (at burn-job.c:1190) BraseroChecksumImage called brasero_job_get_fd_in

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_set_use_average_rate


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom got varg:


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written:     readom


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written:     dev=/dev/sr0


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written:     -nocorr


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written:     -noerror


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written:     -sectors=0-1308272


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written:     -f=-


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom Launching command


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: ** (brasero:10595): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_fd_in


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: ** (brasero:10595): WARNING **: Some log data could not be written


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: ** (brasero:10595): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_fd_out


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: ** (brasero:10595): WARNING **: Some log data could not be written


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... giving up.


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: WARNING: /dev/sr0 seems to be mounted!


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: readom: Device or resource busy. Cannot open '/dev/sr0'. Cannot open SCSI driver.


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_error


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom finished with an error


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom asked to stop because of an error
    error        = 4
    message    = "You do not have the required permissions to use this drive"


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stopping


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom got killed


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: readom: For possible targets try 'wodim -scanbus'. Make sure you are root.


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: readom: For possible transport specifiers try 'wodim dev=help'.


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom disconnecting BraseroReadom from BraseroChecksumImage


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage stopping


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage closing connection for BraseroChecksumImage


** (brasero:10464): WARNING **: Some log data could not be written
BraseroBurn: (at burn-job.c:1312) BraseroReadom called brasero_job_get_fd_out
BraseroBurn: (at burn-job.c:1312) BraseroChecksumImage called brasero_job_get_fd_out
BraseroBurn: (at burn-job.c:1974) BraseroReadom called brasero_job_set_use_average_rate
BraseroBurn: (at burn-job.c:1190) BraseroChecksumImage called brasero_job_get_fd_in
BraseroBurn: (at burn-process.c:142) BraseroReadom got varg:
BraseroBurn: (at burn-job.c:1312) BraseroChecksumImage called brasero_job_get_fd_out
BraseroBurn: (at burn-process.c:146)     readom
BraseroBurn: (at burn-process.c:146)     dev=/dev/sr0
BraseroBurn: (at burn-process.c:146)     -nocorr
BraseroBurn: (at burn-process.c:146)     -noerror
BraseroBurn: (at burn-process.c:146)     -sectors=0-1308272
BraseroBurn: (at burn-process.c:146)     -f=-
BraseroBurn: (at burn-process.c:626) BraseroReadom Launching command
BraseroBurn: (at burn-task.c:442) entering loop
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: ** (brasero:10595): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_fd_in
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: ** (brasero:10595): WARNING **: Some log data could not be written
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: ** (brasero:10595): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_fd_out
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: ** (brasero:10595): WARNING **: Some log data could not be written
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... giving up.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: WARNING: /dev/sr0 seems to be mounted!
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom: Device or resource busy. Cannot open '/dev/sr0'. Cannot open SCSI driver.
BraseroBurn: (at burn-job.c:1138) BraseroReadom called brasero_job_error
BraseroBurn: (at burn-job.c:1140) BraseroReadom finished with an error
BraseroBurn: (at burn-job.c:1174) BraseroReadom asked to stop because of an error
    error        = 4
    message    = "You do not have the required permissions to use this drive"
BraseroBurn: (at burn-task.c:182) stopping BraseroReadom
BraseroBurn: (at burn-job.c:906) BraseroReadom stopping
BraseroBurn: (at burn-process.c:709) BraseroReadom got killed
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom: For possible targets try 'wodim -scanbus'. Make sure you are root.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom: For possible transport specifiers try 'wodim dev=help'.
BraseroBurn: (at burn-job.c:862) BraseroReadom disconnecting BraseroReadom from BraseroChecksumImage
BraseroBurn: (at burn-task.c:190) stopped BraseroReadom
BraseroBurn: (at burn-task.c:182) stopping BraseroChecksumImage
BraseroBurn: (at burn-job.c:906) BraseroChecksumImage stopping
BraseroBurn: (at burn-job.c:881) BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroBurn: (at burn-task.c:190) stopped BraseroChecksumImage
BraseroBurn: (at burn-task.c:448) got out of loop
BraseroBurn: (at burn-task.c:177)
(brasero:10464): GConf-CRITICAL **: gconf_client_set_string: assertion `val != NULL' failed
 BraseroReadom already stopped
BraseroBurn: (at burn-task.c:177) BraseroChecksumImage already stopped
BraseroBurn: (at brasero-session.c:2392) Cleaning session
BraseroMedia: (at brasero-drive.c:1088) GDrive changed
BraseroMedia: (at brasero-drive.c:1052) Setting new probe
BraseroMedia: (at brasero-drive.c:952) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-medium-monitor.c:639) Drive removal signal
BraseroMedia: (at brasero-medium-monitor.c:588) Found device to remove
BraseroMedia: (at brasero-drive.c:983) No medium inserted
BraseroMedia: (at brasero-medium-monitor.c:612) Volume removal signal
BraseroMedia: (at brasero-drive.c:903) Medium removed
BraseroMedia: (at brasero-medium-monitor.c:477) GDrive addition signal
BraseroMedia: (at brasero-medium-monitor.c:442) Added signal was emitted but the drive is in the removal list. Updating GDrive associated object.
BraseroMedia: (at brasero-drive.c:1111) Setting GDrive 0x8977270
BraseroMedia: (at brasero-drive.c:1052) Setting new probe
BraseroMedia: (at brasero-drive.c:952) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:983) No medium inserted
BraseroMedia: (at brasero-drive.c:1088) GDrive changed
BraseroMedia: (at brasero-drive.c:1052) Setting new probe
BraseroMedia: (at brasero-medium-monitor.c:639) Drive removal signal
BraseroMedia: (at brasero-medium-monitor.c:588) Found device to remove
BraseroMedia: (at brasero-medium-monitor.c:477) GDrive addition signal
BraseroMedia: (at brasero-medium-monitor.c:442) Added signal was emitted but the drive is in the removal list. Updating GDrive associated object.
BraseroMedia: (at brasero-drive.c:1111) Setting GDrive 0x8977150
BraseroMedia: (at brasero-drive.c:1048) Ongoing probe
BraseroMedia: (at brasero-drive.c:952) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:975) Open () cancelled
BraseroMedia: (at brasero-drive.c:1052) Setting new probe
BraseroMedia: (at brasero-medium-monitor.c:492) GVolume addition signal
BraseroMedia: (at brasero-medium-monitor.c:500) Existing GDrive skipping
BraseroMedia: (at brasero-drive.c:952) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:1013) Medium inserted
BraseroMedia: (at brasero-drive.c:890) Probing new medium
BraseroMedia: (at brasero-medium.c:3018) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-medium.c:3041) Open () succeeded
BraseroMedia: (at brasero-medium.c:3077) Device ready
BraseroMedia: (at brasero-medium.c:2896) Initializing information for medium in PIONEER DVD-RW  DVR-107D
BraseroMedia: (at brasero-medium.c:2343) Retrieving media profile
BraseroMedia: (at brasero-medium.c:1508) Retrieving media available speeds
BraseroMedia: (at brasero-medium.c:1331) Retrieving speed (Get Performance)
BraseroMedia: (at scsi-get-performance.c:129) Unaligned data (56) setting to max (2048)
BraseroMedia: (at brasero-medium.c:1346) Successfully retrieved a header: size 56, address 0x84a9300
BraseroMedia: (at brasero-medium.c:1350) Updated header size = 56
BraseroMedia: (at brasero-medium.c:1363) Got 3 descriptor(s)
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 0, address = 0x84a9308
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 5540
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 1, address = 0x84a9318
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 2770
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 2, address = 0x84a9328
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 1385
BraseroMedia: (at brasero-medium.c:1393) Maximum Speed (mmc3) 5540
BraseroMedia: (at brasero-medium.c:1009) Checking incremental and simulate feature
BraseroMedia: (at scsi-get-configuration.c:127) Unaligned data (20) setting to max (65530)
BraseroMedia: (at scsi-get-configuration.c:162) Sizes mismatch asked 65530 / received 20
BraseroMedia: (at brasero-medium.c:1024) Incremental feature is not supported
BraseroMedia: (at brasero-medium.c:1027) Checking (DVD-R(W) simulate)
BraseroMedia: (at brasero-medium.c:1043) SAO feature is not supported
BraseroMedia: (at brasero-medium.c:1053) Medium can be blanked
BraseroMedia: (at brasero-medium.c:1128) Tested simulation 1 1, burnfree 1
BraseroMedia: (at brasero-medium.c:2261) Retrieving media status
BraseroMedia: (at brasero-medium.c:2209) DVD id 28489
BraseroMedia: (at brasero-medium.c:2321) Closed media
BraseroMedia: (at brasero-medium.c:2028) Reading Toc
BraseroMedia: (at brasero-medium.c:2068) 2 track(s) found
BraseroMedia: (at brasero-medium.c:1651) Retrieving track information for 1
BraseroMedia: (at brasero-medium.c:1761) Track 1 (session 1): type = 1 start = 0 size = 1308272
BraseroMedia: (at brasero-medium.c:2076) Leadout reached 1308272
BraseroMedia: (at brasero-medium.c:2587) Testing for Css encrypted media
BraseroMedia: (at brasero-medium.c:2948) media is DVD ROM closed with data 
BraseroMedia: (at brasero-drive.c:1088) GDrive changed
BraseroMedia: (at brasero-drive.c:1052) Setting new probe
BraseroMedia: (at brasero-drive.c:952) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at brasero-medium-monitor.c:639) Drive removal signal
BraseroMedia: (at brasero-medium-monitor.c:588) Found device to remove
BraseroMedia: (at brasero-medium-monitor.c:612) Volume removal signal
BraseroMedia: (at brasero-medium-monitor.c:477) GDrive addition signal
BraseroMedia: (at brasero-medium-monitor.c:442) Added signal was emitted but the drive is in the removal list. Updating GDrive associated object.
BraseroMedia: (at brasero-drive.c:1111) Setting GDrive 0x8977198
BraseroMedia: (at brasero-drive.c:1048) Ongoing probe
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:975) Open () cancelled
BraseroMedia: (at brasero-drive.c:1052) Setting new probe
BraseroMedia: (at brasero-drive.c:952) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:983) No medium inserted
BraseroMedia: (at brasero-drive.c:903) Medium removed
BraseroMedia: (at brasero-volume.c:455) Finalizing Volume object
BraseroMedia: (at brasero-medium.c:3151) Finalizing Medium object
BraseroMedia: (at brasero-drive.c:1088) GDrive changed
BraseroMedia: (at brasero-drive.c:1052) Setting new probe
BraseroMedia: (at brasero-drive.c:952) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:1013) Medium inserted
BraseroMedia: (at brasero-drive.c:890) Probing new medium
BraseroMedia: (at brasero-medium-monitor.c:639) Drive removal signal
BraseroMedia: (at brasero-medium-monitor.c:588) Found device to remove
BraseroMedia: (at brasero-medium.c:3018) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-medium.c:3041) Open () succeeded
BraseroMedia: (at brasero-medium.c:3077) Device ready
BraseroMedia: (at brasero-medium.c:2896) Initializing information for medium in PIONEER DVD-RW  DVR-107D
BraseroMedia: (at brasero-medium.c:2343) Retrieving media profile
BraseroMedia: (at brasero-medium.c:1508) Retrieving media available speeds
BraseroMedia: (at brasero-medium.c:1331) Retrieving speed (Get Performance)
BraseroMedia: (at brasero-medium-monitor.c:477) GDrive addition signal
BraseroMedia: (at brasero-medium-monitor.c:442) Added signal was emitted but the drive is in the removal list. Updating GDrive associated object.
BraseroMedia: (at brasero-drive.c:1111) Setting GDrive 0x8977270
BraseroMedia: (at brasero-drive.c:1052) Setting new probe
BraseroMedia: (at scsi-get-performance.c:129) Unaligned data (56) setting to max (2048)
BraseroMedia: (at brasero-medium.c:1346) Successfully retrieved a header: size 56, address 0x890e6e8
BraseroMedia: (at brasero-medium.c:1350) Updated header size = 56
BraseroMedia: (at brasero-medium.c:1363) Got 3 descriptor(s)
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 0, address = 0x890e6f0
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 5540
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 1, address = 0x890e700
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 2770
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 2, address = 0x890e710
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 1385
BraseroMedia: (at brasero-medium.c:1393) Maximum Speed (mmc3) 5540
BraseroMedia: (at brasero-medium.c:1009) Checking incremental and simulate feature
BraseroMedia: (at brasero-drive.c:952) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-get-configuration.c:127) Unaligned data (20) setting to max (65530)
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at scsi-get-configuration.c:162) Sizes mismatch asked 65530 / received 20
BraseroMedia: (at brasero-medium.c:1024) Incremental feature is not supported
BraseroMedia: (at brasero-medium.c:1027) Checking (DVD-R(W) simulate)
BraseroMedia: (at brasero-drive.c:1013) Medium inserted
BraseroMedia: (at brasero-medium-monitor.c:492) GVolume addition signal
BraseroMedia: (at brasero-medium-monitor.c:500) Existing GDrive skipping
BraseroMedia: (at brasero-medium.c:1043) SAO feature is not supported
BraseroMedia: (at brasero-medium.c:1053) Medium can be blanked
BraseroMedia: (at brasero-medium.c:1128) Tested simulation 1 1, burnfree 1
BraseroMedia: (at brasero-medium.c:2261) Retrieving media status
BraseroMedia: (at brasero-medium.c:2209) DVD id 28489
BraseroMedia: (at brasero-medium.c:2321) Closed media
BraseroMedia: (at brasero-medium.c:2028) Reading Toc
BraseroMedia: (at brasero-medium.c:2068) 2 track(s) found
BraseroMedia: (at brasero-medium.c:1651) Retrieving track information for 1
BraseroMedia: (at brasero-medium.c:1761) Track 1 (session 1): type = 1 start = 0 size = 1308272
BraseroMedia: (at brasero-medium.c:2076) Leadout reached 1308272
BraseroMedia: (at brasero-medium.c:2587) Testing for Css encrypted media
BraseroMedia: (at brasero-medium.c:2948) media is DVD ROM closed with data 
BraseroMedia: (at brasero-drive.c:886) Already a medium. Skipping
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroBurn: (at brasero-burn.c:2257) Starting to check track integrity
BraseroBurn: (at brasero-caps-burn.c:878) Creating checksuming task with input Disc DVD ROM closed with data 
BraseroBurn: (at brasero-caps-burn.c:931) Trying link to Image BIN 
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Image BIN 
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Disc DVD ROM closed with data 
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-
** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_current_track


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_action


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_flags


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_action


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage creating input


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_action


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_a
** (br
** (brasero:10464): WARNING **: Some log data could not be w
** (br
** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job
** (brasero:10464):
** (brasero:10464): WARNING **: Some log data c
** (brasero:10464):
** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroC
** (brasero:10464): WARNING **: Some log data could
** (brasero:104
** (brasero:10464): WARNING **: Some log data could
** (brasero:10464): WARNING **: Some log data couldn't be wr
** (brasero:10464): WARNING **: Some log data could not be writte
*
** (brasero:10464): WARNING **: Some log data couldn't be written
** (brasero:10464): WARNING **: Some log data couldn'
** (brasero:10464): WARNING **: Some log data could not be writt
**
** (brasero:10464): WARNING **: Some log data couldn't be writte
(brasero:10464): GLib-GObject-CRITICAL **: g_value_g
** (brasero:10464): WARNING **: Some log data could not be
(brasero
** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_ge
** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage Starting checksum generation live (size = 0)


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_set_nonblocking


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_fd_in


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_fd_out


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_fd_in


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_fd_out


** (brasero:10464): WARNING **: Some log data could not be written
* (brasero:10464): WARNING **: Some log data couldn't be written:     dev=/dev/sr0


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written:     -nocorr


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written:     -noerror


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written:     -sectors=0-1308272


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written:     -f=-


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom Launching command


** (brasero:10464): WARNING **: Some log data could not be written
caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:440) Trying readom with a priority of 1
BraseroBurn: (at brasero-caps-burn.c:1021) readom added to task
BraseroBurn: (at burn-task.c:600) Starting normal task (3)
BraseroBurn: (at burn-task-ctx.c:159) Setting current track (1 tracks)
BraseroBurn: (at burn-task.c:336) ::activate method BraseroReadom
BraseroBurn: (at burn-job.c:352) no ::activate method BraseroReadom
BraseroBurn: (at burn-task.c:336) ::activate method BraseroChecksumImage
BraseroBurn: (at burn-job.c:1270) BraseroChecksumImage called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:1377) BraseroChecksumImage called brasero_job_get_flags
BraseroBurn: (at burn-task.c:293) ::start method BraseroChecksumImage
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:758) BraseroChecksumImage creating input
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-task.c:293) ::start method BraseroReadom
BraseroBurn: (at burn-job.c:1433) BraseroReadom called brasero_job_get_action
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:753) BraseroReadom linked to BraseroChecksumImage
BraseroBurn: (at burn-job.c:1270) BraseroChecksumImage called brasero_job_get_current_track
BraseroBurn: (at burn-process.c:129) BraseroReadom getting varg
BraseroBurn: (at burn-job.c:1861) BraseroChecksumImage called brasero_job_set_current_action
BraseroBurn: (at burn-job.c:1433) BraseroReadom called brasero_job_get_action
BraseroBurn: (at burn-job.c:1270) BraseroChecksumImage called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1270) BraseroReadom called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1190) BraseroChecksumImage called brasero_job_get_fd_in
BraseroBurn: (at burn-job.c:1419) BraseroReadom called brasero_job_get_output_type
BraseroBurn: (at burn-job.c:1270) BraseroReadom called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1419) BraseroReadom called brasero_job_get_output_type
BraseroBurn: (at burn-readom.c:225) BraseroReadom reading last track from sector 0 to 1308272
BraseroBurn: (at burn-job.c:1312) BraseroReadom called brasero_job_get_fd_out
BraseroBurn: (at burn-job.c:1974) BraseroReadom called brasero_job_set_use_average_rate
BraseroBurn: (at burn-checksum-image.c:256) BraseroChecksumImage Starting checksum generation live (size = 0)
BraseroBurn: (at burn-process.c:142) BraseroReadom got varg:
BraseroBurn: (at burn-job.c:1243) BraseroChecksumImage called brasero_job_set_nonblocking
BraseroBurn: (at burn-process.c:146)     readom
BraseroBurn: (at burn-job.c:1190) BraseroChecksumImage called brasero_job_get_fd_in
BraseroBurn: (at burn-process.c:146)     dev=/dev/sr0
BraseroBurn: (at burn-job.c:1312) BraseroChecksumImage called brasero_job_get_fd_out
BraseroBurn: (at burn-process.c:146)     -nocorr
BraseroBurn: (at burn-job.c:1190) BraseroChecksumImage called brasero_job_get_fd_in
BraseroBurn: (at burn-process.c:146)     -noerror
BraseroBurn: (at burn-job.c:1312) BraseroChecksumImage called brasero_job_get_fd_out
BraseroBurn: (at burn-process.c:146)     -sectors=0-1308272
BraseroBurn: (at burn-process.c:146)     -f=-
BraseroBurn: (at burn-process.c:626) BraseroReadom Launching command
BraseroBurn: (at burn-job.c:1190) BraseroReadom called brasero_job_get_fd_in
BraseroBurn: (at burn-job.c:1312) BraseroReadom called b
** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: ** (brasero:10710): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_fd_in


** (brasero:10464): WARNING **: Some log data could not be written
caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:440) Trying readom with a priority of 1
BraseroBurn: (at brasero-caps-burn.c:1021) readom added to task
BraseroBurn: (at burn-task.c:600) Starting normal task (3)
BraseroBurn: (at burn-task-ctx.c:159) Setting current track (1 tracks)
BraseroBurn: (at burn-task.c:336) ::activate method BraseroReadom
BraseroBurn: (at burn-job.c:352) no ::activate method BraseroReadom
BraseroBurn: (at burn-task.c:336) ::activate method BraseroChecksumImage
BraseroBurn: (at burn-job.c:1270) BraseroChecksumImage called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:1377) BraseroChecksumImage called brasero_job_get_flags
BraseroBurn: (at burn-task.c:293) ::start method BraseroChecksumImage
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:758) BraseroChecksumImage creating input
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-task.c:293) ::start method BraseroReadom
BraseroBurn: (at burn-job.c:1433) BraseroReadom called brasero_job_get_action
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:753) BraseroReadom linked to BraseroChecksumImage
BraseroBurn: (at burn-job.c:1270) BraseroChecksumImage called brasero_job_get_current_track
BraseroBurn: (at burn-process.c:129) BraseroReadom getting varg
BraseroBurn: (at burn-job.c:1861) BraseroChecksumImage called brasero_job_set_current_action
BraseroBurn: (at burn-job.c:1433) BraseroReadom called brasero_job_get_action
BraseroBurn: (at burn-job.c:1270) BraseroChecksumImage called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1270) BraseroReadom called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1190) BraseroChecksumImage called brasero_job_get_fd_in
BraseroBurn: (at burn-job.c:1419) BraseroReadom called brasero_job_get_output_type
BraseroBurn: (at burn-job.c:1270) BraseroReadom called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1419) BraseroReadom called brasero_job_get_output_type
BraseroBurn: (at burn-readom.c:225) BraseroReadom reading last track from sector 0 to 1308272
BraseroBurn: (at burn-job.c:1312) BraseroReadom called brasero_job_get_fd_out
BraseroBurn: (at burn-job.c:1974) BraseroReadom called brasero_job_set_use_average_rate
BraseroBurn: (at burn-checksum-image.c:256) BraseroChecksumImage Starting checksum generation live (size = 0)
BraseroBurn: (at burn-process.c:142) BraseroReadom got varg:
BraseroBurn: (at burn-job.c:1243) BraseroChecksumImage called brasero_job_set_nonblocking
BraseroBurn: (at burn-process.c:146)     readom
BraseroBurn: (at burn-job.c:1190) BraseroChecksumImage called brasero_job_get_fd_in
BraseroBurn: (at burn-process.c:146)     dev=/dev/sr0
BraseroBurn: (at burn-job.c:1312) BraseroChecksumImage called brasero_job_get_fd_out
BraseroBurn: (at burn-process.c:146)     -nocorr
BraseroBurn: (at burn-job.c:1190) BraseroChecksumImage called brasero_job_get_fd_in
BraseroBurn: (at burn-process.c:146)     -noerror
BraseroBurn: (at burn-job.c:1312) BraseroChecksumImage called brasero_job_get_fd_out
BraseroBurn: (at burn-process.c:146)     -sectors=0-1308272
BraseroBurn: (at burn-process.c:146)     -f=-
BraseroBurn: (at burn-process.c:626) BraseroReadom Launching command
BraseroBurn: (at burn-task.c:442) entering loop
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-pro
** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: ** (brasero:10710): WARNING **: Some log data could not be written


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: ** (brasero:10710): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_fd_out


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: ** (brasero:10710): WARNING **: Some log data could not be written


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... giving up.


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: WARNING: /dev/sr0 seems to be mounted!


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: readom: Device or resource busy. Cannot open '/dev/sr0'. Cannot open SCSI driver.


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_error


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom finished with an error


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom asked to stop because of an error
    error        = 4
    message    = "You do not have the required permissions to use this drive"


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stopping


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom got killed


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: readom: For possible targets try 'wodim -scanbus'. Make sure you are root.


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom stderr: readom: For possible transport specifiers try 'wodim dev=help'.


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroReadom disconnecting BraseroReadom from BraseroChecksumImage


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage stopping


** (brasero:10464): WARNING **: Some log data could not be written

** (brasero:10464): WARNING **: Some log data couldn't be written: BraseroChecksumImage closing connection for BraseroChecksumImage


** (brasero:10464): WARNING **: Some log data could not be written

(brasero:10464): GConf-CRITICAL **: gconf_client_set_string: assertion `val != NULL' failed
cess.c:417) BraseroReadom stderr: ** (brasero:10710): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_fd_in
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: ** (brasero:10710): WARNING **: Some log data could not be written
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: ** (brasero:10710): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_fd_out
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: ** (brasero:10710): WARNING **: Some log data could not be written
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... giving up.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: WARNING: /dev/sr0 seems to be mounted!
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom: Device or resource busy. Cannot open '/dev/sr0'. Cannot open SCSI driver.
BraseroBurn: (at burn-job.c:1138) BraseroReadom called brasero_job_error
BraseroBurn: (at burn-job.c:1140) BraseroReadom finished with an error
BraseroBurn: (at burn-job.c:1174) BraseroReadom asked to stop because of an error
    error        = 4
    message    = "You do not have the required permissions to use this drive"
BraseroBurn: (at burn-task.c:182) stopping BraseroReadom
BraseroBurn: (at burn-job.c:906) BraseroReadom stopping
BraseroBurn: (at burn-process.c:709) BraseroReadom got killed
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom: For possible targets try 'wodim -scanbus'. Make sure you are root.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom: For possible transport specifiers try 'wodim dev=help'.
BraseroBurn: (at burn-job.c:862) BraseroReadom disconnecting BraseroReadom from BraseroChecksumImage
BraseroBurn: (at burn-task.c:190) stopped BraseroReadom
BraseroBurn: (at burn-task.c:182) stopping BraseroChecksumImage
BraseroBurn: (at burn-job.c:906) BraseroChecksumImage stopping
BraseroBurn: (at burn-job.c:881) BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroBurn: (at burn-task.c:190) stopped BraseroChecksumImage
BraseroBurn: (at burn-task.c:448) got out of loop
BraseroBurn: (at burn-task.c:177) BraseroReadom already stopped
BraseroBurn: (at burn-task.c:177) BraseroChecksumImage already stopped
BraseroBurn: (at brasero-session.c:2392) Cleaning session


```

---

### Post by rocksockdoc on 2012-01-12
This Ubuntu report of the wodim bug suggests changing system permission:
- [Re: BURN TO CD NOT WORKING! Help PLEASE!]("http://ubuntuforums.org/showthread.php?t=1898174&highlight=required+permissions+drive+brasero")

> **nmyrick said:**
> 
     Run the following commands in terminal:
    sudo chmod 4711 /usr/bin/cdrdao
     sudo chmod 4711 /usr/bin/wodim
     sudo chmod 0755 /usr/bin/growisofs
 
 These commands change the default CD/DVD drive access permissions for the plugins cdrdao, wodim, and growisofs

You may also need to give yourself super user access to your CD/DVD drive. To do that, enter the following command in your terminal.

sudo chmod 666 /dev/sr0

(/dev/sr0 is the location of the CD/DVD drive and may differ in some situations, especially if you are using a CD/DVD drive that is connected by USB)

I have found with Ubuntu 10.04, if you require this access for  successful burns, this needs to be done every time you mount a writable  disk. 

Yes, this means if you are copying a disk, you need to do it in five steps.  

1. create the iso image on your hard drive
2. eject the copied disk  
3. insert the burnable disk.  
4. enter the above command in the terminal 
5. burn the iso image to your disk.

You can't just right click and choose Copy Disk, it won't work. Unfortunately, Ubuntu re-assigns the permissions to 660 every time you mount a new disk.

You also need to install Ubuntu Restricted Extras, if you haven't done so already.


---

### Post by rocksockdoc on 2012-01-12
Following the workaround to the Ubuntu wodim bug described above, I tried this:
```
$ ls -l /usr/bin/cdrdao
-rwxr-xr-x 1 root root 596884 2010-03-10 22:19 /usr/bin/cdrdao

$ ls -l /usr/bin/wodim
-rwxr-xr-x 1 root root 371208 2010-03-19 12:43 /usr/bin/wodim

$ ls -l /usr/bin/growisofs
-rwxr-xr-x 1 root root 83764 2009-12-05 13:41 /usr/bin/growisofs

$ sudo chmod 4711 /usr/bin/cdrdao
$ sudo chmod 4711 /usr/bin/wodim
$ sudo chmod 0755 /usr/bin/growisofs

$ ls -l /usr/bin/cdrdao
-rws--x--x 1 root root 596884 2010-03-10 22:19 /usr/bin/cdrdao

$ ls -l /usr/bin/wodim
-rws--x--x 1 root root 371208 2010-03-19 12:43 /usr/bin/wodim

$ ls -l /usr/bin/growisofs
-rwxr-xr-x 1 root root 83764 2009-12-05 13:41 /usr/bin/growisofs

```But, those permission changes alone were NOT enough to overcome the Ubuntu wodim bug:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210672&stc=1&d=1326346766[/IMG]

Here is the resultant Brasero log file:
```
 
BraseroBurn: (at burn-basics.c:233) Initializing Brasero-burn 2.30.2
BraseroMedia: (at brasero-media.c:533) Initializing Brasero-media 2.30.2
BraseroMedia: (at brasero-medium-monitor.c:657) Probing drives and media
BraseroMedia: (at brasero-medium-monitor.c:662) Found 3 drives
BraseroMedia: (at brasero-medium-monitor.c:378) Testing drive /dev/sda
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:184) No handle: Permission denied
BraseroMedia: (at brasero-medium-monitor.c:378) Testing drive /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-medium-monitor.c:387) Drive is optical
BraseroMedia: (at brasero-drive.c:1456) Initializing drive /dev/sr0 from device
BraseroMedia: (at brasero-drive.c:1111) Setting GDrive 0x91fc4c8
BraseroMedia: (at brasero-drive.c:1327) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at brasero-drive.c:1042) Still initializing the drive properties
BraseroMedia: (at brasero-medium-monitor.c:378) Testing drive /dev/sdb
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:184) No handle: Permission denied
BraseroMedia: (at brasero-medium-monitor.c:678) Found 3 volumes
BraseroMedia: (at brasero-medium-monitor.c:378) Testing drive /dev/sda1
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:184) No handle: Permission denied
BraseroMedia: (at brasero-medium-monitor.c:378) Testing drive /dev/sdb1
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:184) No handle: Permission denied
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroBurn: (at burn-plugin-manager.c:440) opening plugin directory /usr/lib/brasero/plugins
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-readcd.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:439) Created new caps Image CLONE 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD ROM closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD ROM closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:439) Created new caps Image BIN 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data 
BraseroMedia: (at brasero-drive.c:1380) Device ready
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"readcd" could not be found in the path
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-mkisofs.so
BraseroMedia: (at brasero-drive.c:1201) Checking supported profiles
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"mkisofs" is a symbolic link pointing to another program
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-cdda2wav.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with audio 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-cdrecord.so
BraseroMedia: (at brasero-drive.c:1212) Dectected medium is 0x10
BraseroMedia: (at brasero-drive.c:1419) Drive caps are 63
BraseroMedia: (at brasero-drive.c:890) Probing new medium
BraseroMedia: (at brasero-medium.c:3018) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW Metadata Information format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:439) Created new caps Image CUE 
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-medium.c:3041) Open () succeeded
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data with audio 
BraseroMedia: (at brasero-medium.c:3077) Device ready
BraseroMedia: (at brasero-medium.c:2896) Initializing information for medium in PIONEER DVD-RW  DVR-107D
BraseroMedia: (at brasero-medium.c:2343) Retrieving media profile
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"cdrecord" is a symbolic link pointing to another program
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-burn-uri.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN CUE CDRDAO CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:439) Created new caps Image CDRDAO 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF SYMLINK Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at burn-plugin.c:1268) Module CD/DVD Creator Folder has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-vob.so
BraseroMedia: (at brasero-medium.c:1508) Retrieving media available speeds
BraseroMedia: (at brasero-medium.c:1331) Retrieving speed (Get Performance)
BraseroMedia: (at scsi-get-performance.c:129) Unaligned data (56) setting to max (2048)
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio MP2 VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW MP2 AC3 Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW MP2 AC3 Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED VIDEO UNDEFINED format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio MP2 VCD Video DVD format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW MP2 AC3 format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW MP2 AC3 
BraseroMedia: (at brasero-medium.c:1346) Successfully retrieved a header: size 56, address 0x936a528
BraseroMedia: (at brasero-medium.c:1350) Updated header size = 56
BraseroMedia: (at brasero-medium.c:1363) Got 3 descriptor(s)
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 0, address = 0x936a530
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 5540
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 1, address = 0x936a540
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 2770
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 2, address = 0x936a550
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 1385
BraseroMedia: (at brasero-medium.c:1393) Maximum Speed (mmc3) 5540
BraseroMedia: (at brasero-medium.c:1009) Checking incremental and simulate feature
BraseroMedia: (at scsi-get-configuration.c:127) Unaligned data (20) setting to max (65530)
BraseroMedia: (at scsi-get-configuration.c:162) Sizes mismatch asked 65530 / received 20
BraseroMedia: (at brasero-medium.c:1024) Incremental feature is not supported
BraseroMedia: (at brasero-medium.c:1027) Checking (DVD-R(W) simulate)
BraseroMedia: (at brasero-medium.c:1043) SAO feature is not supported
BraseroMedia: (at brasero-medium.c:1053) Medium can be blanked
BraseroMedia: (at brasero-medium.c:1128) Tested simulation 1 1, burnfree 1
BraseroMedia: (at brasero-medium.c:2261) Retrieving media status
BraseroMedia: (at brasero-medium.c:2209) DVD id 28489
BraseroMedia: (at brasero-medium.c:2321) Closed media
BraseroMedia: (at brasero-medium.c:2028) Reading Toc
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-checksum.so
BraseroMedia: (at brasero-medium.c:2068) 2 track(s) found
BraseroMedia: (at brasero-medium.c:1651) Retrieving track information for 1
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at burn-plugin.c:1268) Module Image Checksum has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-readom.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data 
BraseroMedia: (at brasero-medium.c:1761) Track 1 (session 1): type = 1 start = 0 size = 1308272
BraseroMedia: (at brasero-medium.c:2076) Leadout reached 1308272
BraseroMedia: (at brasero-medium.c:2587) Testing for Css encrypted media
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-transcode.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW RAW (little endian)Metadata Information format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW RAW (little endian)Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio DTS WAV Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW RAW (little endian)format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW RAW (little endian)
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio DTS WAV format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio DTS WAV 
BraseroBurn: (at burn-plugin.c:1268) Module transcode has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-dvdrwformat.so
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD DL RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD DL RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD DL RW closed with data 
BraseroMedia: (at brasero-medium.c:2948) media is DVD ROM closed with data 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-cdrdao.so
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CDRDAO format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE CDRDAO format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data with audio 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-normalize.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED DTS WAV Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED DTS WAV format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED DTS WAV 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-dvdcss.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL ROM closed protected with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD ROM closed protected with data 
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"libdvdcss.so.2" could not be found
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-growisofs.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL POW W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD POW W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL SRM W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD SRM W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (jump) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD RAM RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD RAM RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL POW W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL POW W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD POW W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD POW W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL SRM W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL SRM W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD SRM W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD SRM W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD RAM RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (jump) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (jump) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD RAM RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW closed with data 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-vcdimager.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio MP2 44100 VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio MP2 44100 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio MP2 44100 VCD Video DVD format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio MP2 44100 VCD Video DVD 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-dvdauthor.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW MP2 AC3 Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF VIDEO 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW MP2 AC3 format accepts files 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-checksum-file.so
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF SYMLINK Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at burn-plugin.c:1268) Module File Checksum has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-wodim.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW Metadata Information format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data with audio 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-local-track.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN CUE CDRDAO CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF SYMLINK Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at burn-plugin.c:1268) Module File Downloader has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-audio2cue.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW Metadata Information format accepts files pipe 
BraseroBurn: (at burn-plugin.c:1268) Module audio2cue has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-genisoimage.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at burn-plugin-manager.c:157) Getting list of plugins to be loaded
BraseroBurn: (at burn-plugin.c:331) Plugin genisoimage is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. genisoimage is active
BraseroBurn: (at burn-plugin.c:331) Plugin audio2cue is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. audio2cue is active
BraseroBurn: (at burn-plugin.c:331) Plugin File Downloader is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Downloader active
BraseroBurn: (at burn-plugin.c:331) Plugin wodim is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. wodim is active
BraseroBurn: (at burn-plugin.c:331) Plugin File Checksum is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Checksum active
BraseroBurn: (at burn-plugin.c:331) Plugin dvdauthor is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdauthor is active
BraseroBurn: (at burn-plugin.c:331) Plugin vcdimager is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. vcdimager is active
BraseroBurn: (at burn-plugin.c:331) Plugin growisofs is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. growisofs is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdcss is inactive
BraseroBurn: (at burn-plugin.c:331) Plugin Normalize is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Normalize active
BraseroBurn: (at burn-plugin.c:331) Plugin cdrdao is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrdao is active
BraseroBurn: (at burn-plugin.c:331) Plugin dvd+rw-format is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvd+rw-format is active
BraseroBurn: (at burn-plugin.c:331) Plugin transcode is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode is active
BraseroBurn: (at burn-plugin.c:331) Plugin readom is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readom is active
BraseroBurn: (at burn-plugin.c:331) Plugin Image Checksum is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Image Checksum active
BraseroBurn: (at burn-plugin.c:331) Plugin transcode2vob is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode2vob is active
BraseroBurn: (at burn-plugin.c:331) Plugin CD/DVD Creator Folder is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. CD/DVD Creator Folder is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrecord is inactive
BraseroBurn: (at burn-plugin.c:331) Plugin cdda2wav is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdda2wav is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. mkisofs is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readcd is inactive
BraseroBurn: (at burn-plugin-manager.c:241) Watching GConf plugin key
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc DVD DL - (jump) W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc BD SRM W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc BD DL SRM W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc BD POW W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc BD DL POW W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD RAM RW blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD RAM RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD DL - (jump) W blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD DL + W blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc BD SRM W blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc BD DL SRM W blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc BD POW W blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc BD DL POW W blank 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD ROM closed protected with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD DL ROM closed protected with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD DL - (sequential) W blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD - (restricted) RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD DL + RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD RW blank Unformatted 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD DL RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD DL RW blank Unformatted 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD DL RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 24 links pointing to Disc CD RW blank 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc CD RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc CD RW closed with audio 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc CD RW closed with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc CD RW appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc CD RW appendable with audio 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc CD RW appendable with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 23 links pointing to Disc CD W blank 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD W closed with audio 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD W closed with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc CD W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc CD W appendable with audio 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc CD W appendable with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD ROM closed with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD ROM closed with audio 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD ROM closed with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD ROM closed with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD + RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD + RW blank Unformatted 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD + RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD + W blank 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD + W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD + W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD - (sequential) RW blank 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD - (sequential) W blank 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD - (sequential) W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD DL ROM closed with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD DL + RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD DL + W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc DVD DL + W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 4 links pointing to Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio DTS WAV format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED DTS WAV format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Audio RAW format accepts files pipe 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED VIDEO UNDEFINED format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Audio MP2 VCD Video DVD format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio MP2 44100 VCD Video DVD format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Audio RAW MP2 AC3 format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio DTS WAV Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED DTS WAV Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Audio RAW Metadata Information format accepts pipe 
BraseroBurn: (at burn-basics.c:205) Created 7 links pointing to Audio RAW Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Audio MP2 VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio MP2 44100 VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Audio RAW MP2 AC3 Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Audio RAW RAW (little endian)format accepts files pipe 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Audio RAW RAW (little endian)Metadata Information format accepts files pipe 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 25 links pointing to Image BIN format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 25 links pointing to Image BIN format accepts pipe 
BraseroBurn: (at burn-basics.c:205) Created 21 links pointing to Image CUE format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 15 links pointing to Image CLONE format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 15 links pointing to Image CDRDAO format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Data ISO UDF VIDEO 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Data ISO UDF SYMLINK Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at burn-plugin-manager.c:157) Getting list of plugins to be loaded
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. genisoimage is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. audio2cue is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Downloader active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. wodim is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdauthor is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. vcdimager is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. growisofs is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdcss is inactive
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Normalize active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrdao is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvd+rw-format is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readom is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Image Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode2vob is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. CD/DVD Creator Folder is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrecord is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdda2wav is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. mkisofs is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readcd is inactive
BraseroBurn: (at burn-plugin-manager.c:241) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:157) Getting list of plugins to be loaded
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. genisoimage is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. audio2cue is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Downloader active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. wodim is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdauthor is activ
** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_current_track


** (brasero:11384): WARNING **: Some log data could not be written
e
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. vcdimager is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. growisofs is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdcss is inactive
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Normalize active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrdao is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvd+rw-format is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readom is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Image Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode2vob is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. CD/DVD Creator Folder is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrecord is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdda2wav is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. mkisofs is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readcd is inactive
BraseroBurn: (at burn-plugin-manager.c:241) Watching GConf plugin key
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sda1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sdb1
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroBurn: (at brasero-burn.c:2257) Starting to check track integrity
BraseroBurn: (at brasero-caps-burn.c:878) Creating checksuming task with input Disc DVD ROM closed with data 
BraseroBurn: (at brasero-caps-burn.c:931) Trying link to Image BIN 
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Image BIN 
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Disc DVD ROM closed with data 
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:440) Trying readom with a priority of 1
BraseroBurn: (at brasero-caps-burn.c:1021) readom added to task
BraseroBurn: (at burn-task.c:600) Starting normal task (3)
BraseroBurn: (at burn-task-ctx.c:159) Setting current track (1 tracks)
BraseroBurn: (at burn-task.c:336) ::activate method BraseroReadom
BraseroBurn: (at burn-job.c:352) no ::activate method BraseroReadom
BraseroBurn: (at burn-task.c:336) ::activate method BraseroChecksumImage
BraseroBurn: (at burn-job.c:1270) BraseroChecksumImage called brasero_job_get_c
** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_action


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_flags


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_action


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroChecksumImage creating input


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_action


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_a
** (br
** (brasero:11384): WARNING **: Some log data could not be w
** (br
** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job
** (brasero:11384):
** (brasero:11384): WARNING **: Some log data c
** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom getting varg


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_action


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_current_track


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_output_type


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_current_track


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_output_type


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom reading last track from sector 0 to 1308272
*
** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_fd_out


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_set_use_average_rate


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom got varg:


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written:     readom


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written:     dev=/dev/sr0


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written:     -nocorr


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written:     -noerror


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written:     -sectors=0-1308272


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written:     -f=-


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom Launching command


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: ** (brasero:11401): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_fd_in


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: ** (brasero:11401): WARNING **: Some log data could not be written


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: ** (brasero:11401): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_fd_out


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: ** (brasero:11401): WARNING **: Some log data could not be written


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.


** (brasero:11384): WARNING **: Some log data could not be written
urrent_track
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:1377) BraseroChecksumImage called brasero_job_get_flags
BraseroBurn: (at burn-task.c:293) ::start method BraseroChecksumImage
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:758) BraseroChecksumImage creating input
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-task.c:293) ::start method BraseroReadom
BraseroBurn: (at burn-job.c:1433) BraseroReadom called brasero_job_get_action
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:753) BraseroReadom linked to BraseroChecksumImage
BraseroBurn: (at burn-job.c:1270) BraseroChecksumImage called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1861) BraseroChecksumImage called brasero_job_set_current_action
BraseroBurn: (at burn-process.c:129) BraseroReadom getting varg
BraseroBurn: (at burn-job.c:1270) BraseroChecksumImage called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1433) BraseroReadom called brasero_job_get_action
BraseroBurn: (at burn-job.c:1190) BraseroChecksumImage called brasero_job_get_fd_in
BraseroBurn: (at burn-job.c:1270) BraseroReadom called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1419) BraseroReadom called brasero_job_get_output_type
BraseroBurn: (at burn-checksum-image.c:256) BraseroChecksumImage Starting checksum generation live (size = 0)
BraseroBurn: (at burn-job.c:1270) BraseroReadom called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1419) BraseroReadom called brasero_job_get_output_type
BraseroBurn: (at burn-job.c:1243) BraseroChecksumImage called brasero_job_set_nonblocking
BraseroBurn: (at burn-readom.c:225) BraseroReadom reading last track from sector 0 to 1308272
BraseroBurn: (at burn-job.c:1190) BraseroChecksumImage called brasero_job_get_fd_in
BraseroBurn: (at burn-job.c:1312) BraseroReadom called brasero_job_get_fd_out
BraseroBurn: (at burn-job.c:1312) BraseroChecksumImage called brasero_job_get_fd_out
BraseroBurn: (at burn-job.c:1974) BraseroReadom called brasero_job_set_use_average_rate
BraseroBurn: (at burn-job.c:1190) BraseroChecksumImage called brasero_job_get_fd_in
BraseroBurn: (at burn-process.c:142) BraseroReadom got varg:
BraseroBurn: (at burn-job.c:1312) BraseroChecksumImage called brasero_job_get_fd_out
BraseroBurn: (at burn-process.c:146)     readom
BraseroBurn: (at burn-process.c:146)     dev=/dev/sr0
BraseroBurn: (at burn-process.c:146)     -nocorr
BraseroBurn: (at burn-process.c:146)     -noerror
BraseroBurn: (at burn-process.c:146)     -sectors=0-1308272
BraseroBurn: (at burn-process.c:146)     -f=-
BraseroBurn: (at burn-process.c:626) BraseroReadom Launching command
BraseroBurn: (at burn-task.c:442) entering loop
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: ** (brasero:11401): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_fd_in
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: ** (brasero:11401): WARNING **: Some log data could not be written
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: ** (brasero:11401): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_fd_out
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: ** (brasero:11401): WARNING **: Some log data could not be written
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclu
** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... giving up.


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: WARNING: /dev/sr0 seems to be mounted!


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: readom: Device or resource busy. Cannot open '/dev/sr0'. Cannot open SCSI driver.


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_error


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom finished with an error


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom asked to stop because of an error
    error        = 4
    message    = "You do not have the required permissions to use this drive"


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stopping


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom got killed


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: readom: For possible targets try 'wodim -scanbus'. Make sure you are root.


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom stderr: readom: For possible transport specifiers try 'wodim dev=help'.


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroReadom disconnecting BraseroReadom from BraseroChecksumImage


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroChecksumImage stopping


** (brasero:11384): WARNING **: Some log data could not be written

** (brasero:11384): WARNING **: Some log data couldn't be written: BraseroChecksumImage closing connection for BraseroChecksumImage


** (brasero:11384): WARNING **: Some log data could not be written

(brasero:11384): GConf-CRITICAL **: gconf_client_set_string: assertion `val != NULL' failed
sively (Device or resource busy)... retrying in 1 second.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... giving up.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: WARNING: /dev/sr0 seems to be mounted!
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom: Device or resource busy. Cannot open '/dev/sr0'. Cannot open SCSI driver.
BraseroBurn: (at burn-job.c:1138) BraseroReadom called brasero_job_error
BraseroBurn: (at burn-job.c:1140) BraseroReadom finished with an error
BraseroBurn: (at burn-job.c:1174) BraseroReadom asked to stop because of an error
    error        = 4
    message    = "You do not have the required permissions to use this drive"
BraseroBurn: (at burn-task.c:182) stopping BraseroReadom
BraseroBurn: (at burn-job.c:906) BraseroReadom stopping
BraseroBurn: (at burn-process.c:709) BraseroReadom got killed
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom: For possible targets try 'wodim -scanbus'. Make sure you are root.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom: For possible transport specifiers try 'wodim dev=help'.
BraseroBurn: (at burn-job.c:862) BraseroReadom disconnecting BraseroReadom from BraseroChecksumImage
BraseroBurn: (at burn-task.c:190) stopped BraseroReadom
BraseroBurn: (at burn-task.c:182) stopping BraseroChecksumImage
BraseroBurn: (at burn-job.c:906) BraseroChecksumImage stopping
BraseroBurn: (at burn-job.c:881) BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroBurn: (at burn-task.c:190) stopped BraseroChecksumImage
BraseroBurn: (at burn-task.c:448) got out of loop
BraseroBurn: (at burn-task.c:177) BraseroReadom already stopped
BraseroBurn: (at burn-task.c:177) BraseroChecksumImage already stopped
BraseroBurn: (at brasero-session.c:2392) Cleaning session


```

---

### Post by rocksockdoc on 2012-01-12
Since that first workaround attempt failed to get around this Ubuntu wodim bug, I'm going to try the second suggested workaround procedure:

1. With the Panasonic USB DVD burner attached to my Lenovo X61 tablet PC on Ubuntu 10.04, I rebooted (with the recently burned DVD video disc in the DVD disc drive).

2. Upon booting, DVDVideo popped up stating: You have just inserted a Video DVD. Choose what applications to launch.

3. Since I didn't ask for that message, nor do I wish to play the video DVD, I simply pressed the DVD Video "cancel" button.

4. I checked the permissions of /dev/sr0:
```
$ ls -l /dev/sr0
WHICH REPORTED:
brw-rw----+ 1 root cdrom 11, 0 2012-01-11 21:51 /dev/sr0
```4. I changed the permission on /dev/sr0 & doublechecked:
```
$ sudo chmod 666 /dev/sr0
$ ls -l /dev/sr0
NOW REPORTED:
brw-rw-rw-+ 1 root cdrom 11, 0 2012-01-11 21:51 /dev/sr0
```Note: /dev/sr0 is the location of the USB CD/DVD drive 
5. Then, I started Brasero 2.30.2 (multiple ways, here's just one attempt):
```
$ brasero --brasero-burn-debug --brasero-media-debug &> brasero-debug.txt
```6. In Brasero 2.30.2, I pressed "Tools->Check Integrity..." and selected the "movie.iso" and "movie.md5" files (after checking "[x]Use an MD5 file to check the disc").

7. The result was the same as before:
```
"The file integrity check cannot be performed. 
You do not have the required permissions to use this drive"
```8. Here is the log file:
```

BraseroBurn: (at burn-basics.c:233) Initializing Brasero-burn 2.30.2
BraseroMedia: (at brasero-media.c:533) Initializing Brasero-media 2.30.2
BraseroMedia: (at brasero-medium-monitor.c:657) Probing drives and media
BraseroMedia: (at brasero-medium-monitor.c:662) Found 3 drives
BraseroMedia: (at brasero-medium-monitor.c:378) Testing drive /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-medium-monitor.c:387) Drive is optical
BraseroMedia: (at brasero-drive.c:1456) Initializing drive /dev/sr0 from device
BraseroMedia: (at brasero-drive.c:1111) Setting GDrive 0x828a4c8
BraseroMedia: (at brasero-drive.c:1327) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at brasero-drive.c:1042) Still initializing the drive properties
BraseroMedia: (at brasero-medium-monitor.c:378) Testing drive /dev/sdb
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:184) No handle: Permission denied
BraseroMedia: (at brasero-medium-monitor.c:378) Testing drive /dev/sda
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:184) No handle: Permission denied
BraseroMedia: (at brasero-medium-monitor.c:678) Found 3 volumes
BraseroMedia: (at brasero-medium-monitor.c:378) Testing drive /dev/sda1
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:184) No handle: Permission denied
BraseroMedia: (at brasero-medium-monitor.c:378) Testing drive /dev/sdb1
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:184) No handle: Permission denied
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroBurn: (at burn-plugin-manager.c:440) opening plugin directory /usr/lib/brasero/plugins
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-readcd.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:439) Created new caps Image CLONE 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD ROM closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD ROM closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:439) Created new caps Image BIN 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data 
BraseroMedia: (at brasero-drive.c:1380) Device ready
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"readcd" could not be found in the path
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-mkisofs.so
BraseroMedia: (at brasero-drive.c:1201) Checking supported profiles
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"mkisofs" is a symbolic link pointing to another program
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-cdda2wav.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with audio 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-cdrecord.so
BraseroMedia: (at brasero-drive.c:1212) Dectected medium is 0x10
BraseroMedia: (at brasero-drive.c:1419) Drive caps are 63
BraseroMedia: (at brasero-drive.c:890) Probing new medium
BraseroMedia: (at brasero-medium.c:3018) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW Metadata Information format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:439) Created new caps Image CUE 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data with audio 
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"cdrecord" is a symbolic link pointing to another program
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-burn-uri.so
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-medium.c:3041) Open () succeeded
BraseroMedia: (at brasero-medium.c:3077) Device ready
BraseroMedia: (at brasero-medium.c:2896) Initializing information for medium in PIONEER DVD-RW  DVR-107D
BraseroMedia: (at brasero-medium.c:2343) Retrieving media profile
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN CUE CDRDAO CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:439) Created new caps Image CDRDAO 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF SYMLINK Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at burn-plugin.c:1268) Module CD/DVD Creator Folder has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-vob.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio MP2 VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW MP2 AC3 Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW MP2 AC3 Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED VIDEO UNDEFINED format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio MP2 VCD Video DVD format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW MP2 AC3 format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW MP2 AC3 
BraseroMedia: (at brasero-medium.c:1508) Retrieving media available speeds
BraseroMedia: (at brasero-medium.c:1331) Retrieving speed (Get Performance)
BraseroMedia: (at scsi-get-performance.c:129) Unaligned data (56) setting to max (2048)
BraseroMedia: (at brasero-medium.c:1346) Successfully retrieved a header: size 56, address 0x83fd018
BraseroMedia: (at brasero-medium.c:1350) Updated header size = 56
BraseroMedia: (at brasero-medium.c:1363) Got 3 descriptor(s)
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 0, address = 0x83fd020
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 5540
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 1, address = 0x83fd030
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 2770
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 2, address = 0x83fd040
BraseroMedia: (at brasero-medium.c:1384) RD = 1385 / WRT = 1385
BraseroMedia: (at brasero-medium.c:1393) Maximum Speed (mmc3) 5540
BraseroMedia: (at brasero-medium.c:1009) Checking incremental and simulate feature
BraseroMedia: (at scsi-get-configuration.c:127) Unaligned data (20) setting to max (65530)
BraseroMedia: (at scsi-get-configuration.c:162) Sizes mismatch asked 65530 / received 20
BraseroMedia: (at brasero-medium.c:1024) Incremental feature is not supported
BraseroMedia: (at brasero-medium.c:1027) Checking (DVD-R(W) simulate)
BraseroMedia: (at brasero-medium.c:1043) SAO feature is not supported
BraseroMedia: (at brasero-medium.c:1053) Medium can be blanked
BraseroMedia: (at brasero-medium.c:1128) Tested simulation 1 1, burnfree 1
BraseroMedia: (at brasero-medium.c:2261) Retrieving media status
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-checksum.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at burn-plugin.c:1268) Module Image Checksum has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-readom.so
BraseroMedia: (at brasero-medium.c:2209) DVD id 28489
BraseroMedia: (at brasero-medium.c:2321) Closed media
BraseroMedia: (at brasero-medium.c:2028) Reading Toc
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-transcode.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW RAW (little endian)Metadata Information format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW RAW (little endian)Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio DTS WAV Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW RAW (little endian)format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW RAW (little endian)
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio DTS WAV format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio DTS WAV 
BraseroBurn: (at burn-plugin.c:1268) Module transcode has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-dvdrwformat.so
BraseroMedia: (at brasero-medium.c:2068) 2 track(s) found
BraseroMedia: (at brasero-medium.c:1651) Retrieving track information for 1
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD DL RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD DL RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD DL RW closed with data 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-cdrdao.so
BraseroMedia: (at brasero-medium.c:1761) Track 1 (session 1): type = 1 start = 0 size = 1308272
BraseroMedia: (at brasero-medium.c:2076) Leadout reached 1308272
BraseroMedia: (at brasero-medium.c:2587) Testing for Css encrypted media
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CDRDAO format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE CDRDAO format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data with audio 
BraseroMedia: (at brasero-medium.c:2948) media is DVD ROM closed with data 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-normalize.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED DTS WAV Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED DTS WAV format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED DTS WAV 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-dvdcss.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL ROM closed protected with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD ROM closed protected with data 
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"libdvdcss.so.2" could not be found
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-growisofs.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL POW W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD POW W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL SRM W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD SRM W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (jump) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD RAM RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD RAM RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL POW W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL POW W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD POW W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD POW W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL SRM W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL SRM W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD SRM W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD SRM W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD RAM RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (jump) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (jump) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD RAM RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW closed with data 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-vcdimager.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio MP2 44100 VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio MP2 44100 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio MP2 44100 VCD Video DVD format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio MP2 44100 VCD Video DVD 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-dvdauthor.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW MP2 AC3 Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF VIDEO 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW MP2 AC3 format accepts files 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-checksum-file.so
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF SYMLINK Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at burn-plugin.c:1268) Module File Checksum has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-wodim.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW Metadata Information format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data with audio 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-local-track.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN CUE CDRDAO CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF SYMLINK Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at burn-plugin.c:1268) Module File Downloader has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-audio2cue.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW Metadata Information format accepts files pipe 
BraseroBurn: (at burn-plugin.c:1268) Module audio2cue has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-genisoimage.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at burn-plugin-manager.c:157) Getting list of plugins to be loaded
BraseroBurn: (at burn-plugin.c:331) Plugin genisoimage is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. genisoimage is active
BraseroBurn: (at burn-plugin.c:331) Plugin audio2cue is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. audio2cue is active
BraseroBurn: (at burn-plugin.c:331) Plugin File Downloader is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Downloader active
BraseroBurn: (at burn-plugin.c:331) Plugin wodim is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. wodim is active
BraseroBurn: (at burn-plugin.c:331) Plugin File Checksum is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Checksum active
BraseroBurn: (at burn-plugin.c:331) Plugin dvdauthor is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdauthor is active
BraseroBurn: (at burn-plugin.c:331) Plugin vcdimager is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. vcdimager is active
BraseroBurn: (at burn-plugin.c:331) Plugin growisofs is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. growisofs is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdcss is inactive
BraseroBurn: (at burn-plugin.c:331) Plugin Normalize is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Normalize active
BraseroBurn: (at burn-plugin.c:331) Plugin cdrdao is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrdao is active
BraseroBurn: (at burn-plugin.c:331) Plugin dvd+rw-format is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvd+rw-format is active
BraseroBurn: (at burn-plugin.c:331) Plugin transcode is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode is active
BraseroBurn: (at burn-plugin.c:331) Plugin readom is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readom is active
BraseroBurn: (at burn-plugin.c:331) Plugin Image Checksum is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Image Checksum active
BraseroBurn: (at burn-plugin.c:331) Plugin transcode2vob is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode2vob is active
BraseroBurn: (at burn-plugin.c:331) Plugin CD/DVD Creator Folder is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. CD/DVD Creator Folder is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrecord is inactive
BraseroBurn: (at burn-plugin.c:331) Plugin cdda2wav is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdda2wav is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. mkisofs is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readcd is inactive
BraseroBurn: (at burn-plugin-manager.c:241) Watching GConf plugin key
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc DVD DL - (jump) W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc BD SRM W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc BD DL SRM W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc BD POW W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc BD DL POW W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD RAM RW blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD RAM RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD DL - (jump) W blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD DL + W blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc BD SRM W blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc BD DL SRM W blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc BD POW W blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc BD DL POW W blank 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD ROM closed protected with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD DL ROM closed protected with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD DL - (sequential) W blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD - (restricted) RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD DL + RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD RW blank Unformatted 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD DL RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD DL RW blank Unformatted 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD DL RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 24 links pointing to Disc CD RW blank 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc CD RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc CD RW closed with audio 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc CD RW closed with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc CD RW appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc CD RW appendable with audio 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc CD RW appendable with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 23 links pointing to Disc CD W blank 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD W closed with audio 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD W closed with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc CD W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc CD W appendable with audio 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc CD W appendable with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD ROM closed with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD ROM closed with audio 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD ROM closed with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD ROM closed with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD + RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD + RW blank Unformatted 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD + RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD + W blank 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD + W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD + W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD - (sequential) RW blank 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD - (sequential) W blank 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD - (sequential) W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD DL ROM closed with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD DL + RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD DL + W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc DVD DL + W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 4 links pointing to Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio DTS WAV format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED DTS WAV format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Audio RAW format accepts files pipe 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED VIDEO UNDEFINED format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Audio MP2 VCD Video DVD format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio MP2 44100 VCD Video DVD format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Audio RAW MP2 AC3 format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio DTS WAV Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED DTS WAV Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Audio RAW Metadata Information format accepts pipe 
BraseroBurn: (at burn-basics.c:205) Created 7 links pointing to Audio RAW Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Audio MP2 VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio MP2 44100 VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Audio RAW MP2 AC3 Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Audio RAW RAW (little endian)format accepts files pipe 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Audio RAW RAW (little endian)Metadata Information format accepts files pipe 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 25 links pointing to Image BIN format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 25 links pointing to Image BIN format accepts pipe 
BraseroBurn: (at burn-basics.c:205) Created 21 links pointing to Image CUE format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 15 links pointing to Image CLONE format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 15 links pointing to Image CDRDAO format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Data ISO UDF VIDEO 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Data ISO UDF SYMLINK Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at burn-plugin-manager.c:157) Getting list of plugins to be loaded
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. genisoimage is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. audio2cue is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Downloader active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. wodim is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdauthor is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. vcdimager is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. growisofs is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdcss is inactive
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Normalize active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrdao is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvd+rw-format is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readom is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Image Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode2vob is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. CD/DVD Creator Folder is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrecord is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdda2wav is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. mkisofs is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readcd is inactive
BraseroBurn: (at burn-plugin-manager.c:241) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:157) Getting list of plugins to be loaded
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. genisoimage is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. audio2cue is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Downloader active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. wodim is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdauthor is activ
** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_current_track


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_action


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_flags


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_action


** (brasero:1811): WARNING **: Some log data could not be written
e
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. vcdimager is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. growisofs is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdcss is inactive
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Normalize active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrdao is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvd+rw-format is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readom is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Image Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode2vob is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. CD/DVD Creator Folder is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrecord is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdda2wav is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. mkisofs is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readcd is inactive
BraseroBurn: (at burn-plugin-manager.c:241) Watching GConf plugin key
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroBurn: (at brasero-burn.c:2257) Starting to check track integrity
BraseroBurn: (at brasero-caps-burn.c:878) Creating checksuming task with input Disc DVD ROM closed with data 
BraseroBurn: (at brasero-caps-burn.c:931) Trying link to Image BIN 
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Image BIN 
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Disc DVD ROM closed with data 
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:440) Trying readom with a priority of 1
BraseroBurn: (at brasero-caps-burn.c:1021) readom added to task
BraseroBurn: (at burn-task.c:600) Starting normal task (3)
BraseroBurn: (at burn-task-ctx.c:159) Setting current track (1 tracks)
BraseroBurn: (at burn-task.c:336) ::activate method BraseroReadom
BraseroBurn: (at burn-job.c:352) no ::activate method BraseroReadom
BraseroBurn: (at burn-task.c:336) ::activate method BraseroChecksumImage
BraseroBurn: (at burn-job.c:1270) BraseroChecksumImage called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:1377) BraseroChecksumImage called brasero_job_get_flags
BraseroBurn: (at burn-task.c:293) ::start method BraseroChecksumImage

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroChecksumImage creating input


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_action


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_action


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom linked to BraseroChecksumImage


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom getting varg


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_action


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_current_track


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_output_type


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_current_track


** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroChecksumImage Starting checksum generation live (size = 0)


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_set_nonblocking


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_fd_in


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_fd_out


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_fd_in


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroChecksumImage called brasero_job_get_fd_out


** (brasero:1811): WARNING **: Some log data could not be written
WARNING **: Some log data couldn't be written:     dev=/dev/sr0


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written:     -nocorr


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written:     -noerror


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written:     -sectors=0-1308272


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written:     -f=-


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom Launching command


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: ** (brasero:1827): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_fd_in


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: ** (brasero:1827): WARNING **: Some log data could not be written


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: ** (brasero:1827): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_fd_out


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: 


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: ** (brasero:1827): WARNING **: Some log data could not be written


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.


** (brasero:1811): WARNING **: Some log data could not be written
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:758) BraseroChecksumImage creating input
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-task.c:293) ::start method BraseroReadom
BraseroBurn: (at burn-job.c:1433) BraseroReadom called brasero_job_get_action
BraseroBurn: (at burn-job.c:1433) BraseroChecksumImage called brasero_job_get_action
BraseroBurn: (at burn-job.c:753) BraseroReadom linked to BraseroChecksumImage
BraseroBurn: (at burn-job.c:1270) BraseroChecksumImage called brasero_job_get_current_track
BraseroBurn: (at burn-process.c:129) BraseroReadom getting varg
BraseroBurn: (at burn-job.c:1861) BraseroChecksumImage called brasero_job_set_current_action
BraseroBurn: (at burn-job.c:1433) BraseroReadom called brasero_job_get_action
BraseroBurn: (at burn-job.c:1270) BraseroChecksumImage called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1270) BraseroReadom called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1190) BraseroChecksumImage called brasero_job_get_fd_in
BraseroBurn: (at burn-job.c:1419) BraseroReadom called brasero_job_get_output_type
BraseroBurn: (at burn-job.c:1270) BraseroReadom called brasero_job_get_current_track
BraseroBurn: (at burn-job.c:1419) BraseroReadom called brasero_job_get_output_type
BraseroBurn: (at burn-checksum-image.c:256) BraseroChecksumImage Starting checksum generation live (size = 0)
BraseroBurn: (at burn-readom.c:225) BraseroReadom reading last track from sector 0 to 1308272
BraseroBurn: (at burn-job.c:1243) BraseroChecksumImage called brasero_job_set_nonblocking
BraseroBurn: (at burn-job.c:1312) BraseroReadom called brasero_job_get_fd_out
BraseroBurn: (at burn-job.c:1190) BraseroChecksumImage called brasero_job_get_fd_in
BraseroBurn: (at burn-job.c:1974) BraseroReadom called brasero_job_set_use_average_rate
BraseroBurn: (at burn-job.c:1312) BraseroChecksumImage called brasero_job_get_fd_out
BraseroBurn: (at burn-process.c:142) BraseroReadom got varg:
BraseroBurn: (at burn-job.c:1190) BraseroChecksumImage called brasero_job_get_fd_in
BraseroBurn: (at burn-process.c:146)     readom
BraseroBurn: (at burn-job.c:1312) BraseroChecksumImage called brasero_job_get_fd_out
BraseroBurn: (at burn-process.c:146)     dev=/dev/sr0
BraseroBurn: (at burn-process.c:146)     -nocorr
BraseroBurn: (at burn-process.c:146)     -noerror
BraseroBurn: (at burn-process.c:146)     -sectors=0-1308272
BraseroBurn: (at burn-process.c:146)     -f=-
BraseroBurn: (at burn-process.c:626) BraseroReadom Launching command
BraseroBurn: (at burn-task.c:442) entering loop
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: ** (brasero:1827): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_fd_in
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: ** (brasero:1827): WARNING **: Some log data could not be written
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: ** (brasero:1827): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_get_fd_out
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: 
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: ** (brasero:1827): WARNING **: Some log data could not be written
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
BraseroBurn: (at burn-process.c:417) BraseroRe
** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... giving up.


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: WARNING: /dev/sr0 seems to be mounted!


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: readom: Device or resource busy. Cannot open '/dev/sr0'. Cannot open SCSI driver.


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom called brasero_job_error


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom finished with an error


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom asked to stop because of an error
    error        = 4
    message    = "You do not have the required permissions to use this drive"


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stopping


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom got killed


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: readom: For possible targets try 'wodim -scanbus'. Make sure you are root.


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom stderr: readom: For possible transport specifiers try 'wodim dev=help'.


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroReadom disconnecting BraseroReadom from BraseroChecksumImage


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroChecksumImage stopping


** (brasero:1811): WARNING **: Some log data could not be written

** (brasero:1811): WARNING **: Some log data couldn't be written: BraseroChecksumImage closing connection for BraseroChecksumImage


** (brasero:1811): WARNING **: Some log data could not be written

(brasero:1811): GConf-CRITICAL **: gconf_client_set_string: assertion `val != NULL' failed
adom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying to open /dev/sr0 exclusively (Device or resource busy)... giving up.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: WARNING: /dev/sr0 seems to be mounted!
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom: Device or resource busy. Cannot open '/dev/sr0'. Cannot open SCSI driver.
BraseroBurn: (at burn-job.c:1138) BraseroReadom called brasero_job_error
BraseroBurn: (at burn-job.c:1140) BraseroReadom finished with an error
BraseroBurn: (at burn-job.c:1174) BraseroReadom asked to stop because of an error
    error        = 4
    message    = "You do not have the required permissions to use this drive"
BraseroBurn: (at burn-task.c:182) stopping BraseroReadom
BraseroBurn: (at burn-job.c:906) BraseroReadom stopping
BraseroBurn: (at burn-process.c:709) BraseroReadom got killed
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom: For possible targets try 'wodim -scanbus'. Make sure you are root.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom: For possible transport specifiers try 'wodim dev=help'.
BraseroBurn: (at burn-job.c:862) BraseroReadom disconnecting BraseroReadom from BraseroChecksumImage
BraseroBurn: (at burn-task.c:190) stopped BraseroReadom
BraseroBurn: (at burn-task.c:182) stopping BraseroChecksumImage
BraseroBurn: (at burn-job.c:906) BraseroChecksumImage stopping
BraseroBurn: (at burn-job.c:881) BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroBurn: (at burn-task.c:190) stopped BraseroChecksumImage
BraseroBurn: (at burn-task.c:448) got out of loop
BraseroBurn: (at burn-task.c:177) BraseroReadom already stopped
BraseroBurn: (at burn-task.c:177) BraseroChecksumImage already stopped
BraseroBurn: (at brasero-session.c:2392) Cleaning session


```

---

### Post by rocksockdoc on 2012-01-12
Well, I've run out of things to try.

Because of this Ubuntu bug, Brasero is incapable of verifying a burn.

So, I'll start exploring the other disc-burning tools for that feature:
```
$ sudo apt-get install k3b gnomebaker 
```

Unless you have ideas for working around this Ubuntu bug?

---

### Post by Telengard C64 on 2012-01-12
I don't know how to fix Brasero, but I have a thought for an alternate solution. If you have an ISO file and a disc which you burned from it, then it should be possible to mount both simultaneously and perform an binary compare. As they are both just files, I suggest:

```
CMP(1)                           User Commands                          CMP(1)

NAME
       cmp - compare two files byte by byte

```

**_EDIT_**
I have not tried this. You may have to do it with the disc inserted, but *unmounted*.

---

### Post by mastablasta on 2012-01-12
meh, just use k3b :-P

---

### Post by rocksockdoc on 2012-01-12
Unfortunately, I don't know enough about Ubuntu to make use of the Brasero developer's suggested solution, which is to patch Ubuntu using this URL:

[LIST]
[*][ftp://ftp.berlios.de/pub/cdrecord/alpha/](ftp://ftp.berlios.de/pub/cdrecord/alpha/)
[/LIST]
But, I would like to try some of the other suggested workarounds, one of which is to prevent mounting of the CD/DVD burner in the first place.

 [quote=from bug report 505582 above]
... the problem is that the CD is automatically mounted when Brasero finishes burning. Then brasero tries to access it to verify but fails as drive is already used by another program. 
 
When I disabled automount in nautilus section of gconf the problem went away.
[/quote]

I'll google how to **temporarily** disable automount & report back if I can figure how how.

EDIT: I'll start here once I understand what the tutorial is saying:
- [B]HOWTO: [Disable automounting of portable media and manually control automounting]("http://ubuntuforums.org/showthread.php?t=1256795&highlight=disable+automount+nautilus+gconf")

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210695&stc=1&d=1326387767[/IMG]
[/B]

---

