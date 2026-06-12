---
title: "[SOLVED] cant play dvds"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-30
ive installed all kinds of libdvdcss's etc and i still cant play dvd's
what can i do????????????????????????????????????????????????????????

---

### Post by tuxxy on 2008-07-30
Did you install the ubuntu-restricted-extras package? This should enable codecs for DVD playbback and MP3 amongst other things,
```

sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Potatoj316 on 2008-07-30
i would sugest reading this
[http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands](http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands)

---

### Post by rixtr66 on 2008-07-30
yes i have done both i installed restricted extras as well,dvd wont work in vlc either
:confused:

---

### Post by Potatoj316 on 2008-07-30
you did tell vlc to open disk from the file menu right?  also just want to make sure, you have a DVD drive, right?  (no a CD drive is not the same thing as a DVD drive, but one can be both)

---

### Post by rixtr66 on 2008-07-30
yes i have a dvd.r

---

### Post by rixtr66 on 2008-07-30
i also tried to turn on the dma on my dvd player but that didnt work

---

### Post by mc4man on 2008-07-30
You can get some decent info by running this in a terminal _with the dvd in the drive_. Will show the device name and links of your drive and how and where the dvd is mounted
```
sudo lshw -C disk
```

---

### Post by rixtr66 on 2008-07-30
rick@ubuntu-studio:~$ sudo lshw -C disk
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD-RAM UJ-840S
       vendor: MATSHITA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 1.00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted
  *-disk
       description: ATA Disk
       product: Hitachi HTS54258
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: BBBO
       serial: 080114BB0B00WFC1TPJC
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000d8a1f
  *-disk
       description: SCSI Disk
       product: 2500BEV External
       vendor: WD
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: 1.05
       serial: WD-WXH308610987
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4 signature=5b6ac646
rick@ubuntu-studio:~$

---

### Post by billgoldberg on 2008-07-30
> **Potatoj316 said:**
> i would sugest reading this
[http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands](http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands)

I have it in one command in the codecs link in my sig, and it installs all codecs, not just dvd playback.

---

### Post by t0p on 2008-07-30
The package ubuntu-restricted-extras doesn't enable playback of encrypted dvds.  For that, you need **libdvdcss2** from the Medibuntu repository.

---

### Post by mc4man on 2008-07-30
Has a region been set on that drive?
Note that with most drives and especially matshita drives a region must be set. In the case of matshita drives you can only playback disks from the same region that drive has been set to.
_Do Not change regions_ just to view a disk or you'll quickly end up with a locked drive

To ck. if region has been set install regionset and with a dvd in the drive run regionset from the terminal. Post results and where (what region) you live

related threads concerning region setting and matshita drives

[http://ubuntuforums.org/showthread.php?p=5319006#post5319006](http://ubuntuforums.org/showthread.php?p=5319006#post5319006)

[http://ubuntuforums.org/showthread.php?p=5413407#post5413407](http://ubuntuforums.org/showthread.php?p=5413407#post5413407)


edit; for example here's a drive I just installed with no region set. Now because liteon's are very 'liberal' I can playback commercial dvds without a region being set. Disk navigation is slightly borked so I'll set a region (I'm in N. America so I'll choose 1)

```
doug@doug-desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:1
New mask: 0xFFFFFFFE, correct? [y/n]:y
Region code set successfully!
```

After setting it looks as such
```
doug@doug-desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET [COLOR="Red"] <-[/COLOR]
vendor resets available: 4
user controlled changes resets available: 4  [COLOR="Red"]<-[/COLOR]
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:n

```

---

### Post by rixtr66 on 2008-07-30
ok i tried both methods and still cant play dvd's in xine it says the codes are too old??how do i set my dma i cant find the web site i used for that
rick

---

### Post by rixtr66 on 2008-07-30
rick@ubuntu-studio:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 2, mask=0xFD

Would you like to change the region setting of your drive? [y/n]:n
rick@ubuntu-studio:~$

---

### Post by mc4man on 2008-07-30
And what is the region of the dvd?
Open vlc from a terminal and then try to open disk, post errors

to _check_ on dma setting run ```
sudo hdparm -I /dev/scd0
```

---

### Post by rixtr66 on 2008-07-30
i dont know how to open vlc in a terminal

---

### Post by rixtr66 on 2008-07-30
rick@ubuntu-studio:~$ sudo hdparm -I /dev/scd0

/dev/scd0:

ATAPI CD-ROM, with removable media
	Model Number:       MATSHITADVD-RAM UJ-840S                 
	Serial Number:      
	Firmware Revision:  1.00    
Standards:
	Likely used CD-ROM ATAPI-1
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
Capabilities:
	LBA, IORDY(can be disabled)
	DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 *udma2 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=240ns  IORDY flow control=120ns
HW reset results:
	CBLID- below Vih
	Device num = 1
rick@ubuntu-studio:~$ sudo hdparm -I /dev/scd0

how do i change the dma setting?and how do iknow what region to set i live in maine.
rick

---

### Post by mc4man on 2008-07-30
> DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 *udma2  it's set at udma2 - nothing to change, your fine there.
post vlc output from terminal
If your trying to play a disk from any region other than 2 with that drive it's not going to happen.
If it's a region2 disk a solution should be easy based on error in terminal

edit : missed
Open a terminal and just type vlc and press enter

---

### Post by rixtr66 on 2008-07-30
oh,oh i changed regions,now what?

---

### Post by sdowney717 on 2008-07-30
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support)

this lets you play DVD's
The liddvdcss2 is what you must have.
The key for medibuntu on that site is wrong, dont use it.

This site shows you how to setup medibuntu repository
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by rixtr66 on 2008-07-30
the region is set on 1 and heres the output from vlc:VLC media player 0.8.6e Janus
[00000289] netsync interface error: master address not specified
libdvdread: Invalid title IFO (VTS_02_0.IFO).
[00000296] dvdread demuxer error: read failed for block 68743
[00000283] main playlist: nothing to play

---

### Post by mc4man on 2008-07-30
from earlier post
> Do Not change regions just to view a disk or you'll quickly end up with a locked drive

_Just stop doing anything for a moment._

What is the region of the majority of the disks you have and watch?

---

### Post by rixtr66 on 2008-07-30
if you mean by region wherei am i live in maine
rick

---

### Post by mc4man on 2008-07-30
Good, then leave it at the present setting (region 1) and _never change again._
Go to system -> administration -> software sources -> third party and see if medibuntu is listed and checked  see screenshot
_If so run_ 
```
sudo aptitude purge vlc libdvdcss2
```
followed by
```
sudo aptitude install vlc libdvdcss2 ubuntu-restricted-extras
``` in the terminal 

If not post back

---

### Post by rixtr66 on 2008-07-30
thank you very much ive been at this for hours!!!
rick

---

### Post by bsmith1051 on 2008-07-30
so what was the key?  (It's "Solved", right?)  Was it purging, then reinstalling vlc etc?

---

### Post by rixtr66 on 2008-07-30
it was acombination of luck with the region switch and the re doing of the repositories,as well as the last bit,i also now have every codec known to man:)
rick

---

### Post by mc4man on 2008-07-30
there were probably 2 issues
First the drive was set to region2 and he was attempting to play region 1 disk. While that's not an issue (region mismatch) with most drives, most matshita drives _absolutely will not allow access to encrypted sectors when there is a region mismatch - period. _ The exception is the rare desktop model and _some_ matshita's in macs.
[http://forum.rpc1.org/viewtopic.php?t=43012](http://forum.rpc1.org/viewtopic.php?t=43012)

some further explaination of mat[COLOR="Red"]****[/COLOR]a drives in links in earlier post, an interesting one
[http://club.cdfreaks.com/637240-post2.html](http://club.cdfreaks.com/637240-post2.html)

the purge and install was to eliminate any potential corruption of or to make sure everything needed was installed.
This is what I do from fresh setups, never fails
[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)

---

