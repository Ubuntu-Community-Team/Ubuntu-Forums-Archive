---
title: "cannot play dvds"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by taith on 2008-05-19
hey again!

when i put in a movie dvd, it cannot play it... i get an error from totem

An error occured
Could not read from resource.

the dvd itself mounts, allowing me to view the files, but i can neither play, nor copy(brasero) the movie...

any ideas?

i'm using hardy, if that affects anything...?

---

### Post by Ryadt on 2008-05-19
hi..try installing vlc..
sudo apt-get vlc

---

### Post by taith on 2008-05-19
vlc is installed, when telling it to load the disc, the program just closes, no error

---

### Post by Maestro23 on 2008-05-19
Check out this Multimedia Guide.  Should help.

[http://ubuntuforums.org/showthread.php?t=766683&highlight=medibuntu+repository](http://ubuntuforums.org/showthread.php?t=766683&highlight=medibuntu+repository)

---

### Post by muted1987 on 2008-05-19
you need to install the restricted extras to be able to play dvds i believe 

type sudo apt-get install linux-restriced-modules in terminal

---

### Post by philinux on 2008-05-19
Install ubuntu-restricted-extras. And this click the medibuntu link in my signature below.

---

### Post by om1 on 2008-05-19
medibuntu.org

---

### Post by taith on 2008-05-19
the restricted, medibuntu, libdvdcss2, libdvdread3, libdvdnav4 were already installed... still getting that error :(

---

### Post by mc4man on 2008-05-19
open vlc from the terminal, try to play disk and post error messages

---

### Post by taith on 2008-05-19
vlc dvd://
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: ZATOICHI
libdvdnav: DVD Serial Number: 316168B9
libdvdnav: DVD Title (Alternative): ZATOICHI
libdvdnav: Unable to find map file '/home/taith/.dvdnav/ZATOICHI.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000149
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000019b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00009d75
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000ab80
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000abb9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0000ac2f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0000ac68
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00095971
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000959aa
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00140c28
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00140c61
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00220c21
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00220c5a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0022d791
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0022d7ca
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0
libdvdnav: ifoRead_PGCI_UT failed - CRASHING!!!
vlc: vm.c:210: ifoOpenNewVTSI: Assertion `0' failed.
Aborted

---

### Post by taith on 2008-05-19
not sure if its important, but its doing this for every dvd movie i have, on more then one computer, with the same errors...

---

### Post by mc4man on 2008-05-19
the first thing to ck. is that you have a region set on drive, if you know it's set then ignore this (in your case region 1), if not install regionset and with a _dvd in the drive run_ regionset. here is ex. of a set drive
```
doug@doug-desktop:~$ regionset 
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET     [COLOR="Red"]<-[/COLOR]
vendor resets available: 4
user controlled changes resets available: 
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]: n
```If it wasn't set then set it, clear the .dvdcss folder and try vlc again. If it was set answer no and clear the .dvdcss folder and try vlc
Note ; everytime you try something new it's good to go into home dir., find .dvdcss (hidden) and delete all the folders inside, this eliminates possibility of corrupted decryption keys.

---

### Post by taith on 2008-05-19
regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.

---

### Post by mc4man on 2008-05-19
you must have a dvd in the drive, if you have 2 dvd drives then specify drive
ex. regionset /dev/scd0  (or /dev/scd1, or /dev/hdc - ect.)

---

### Post by SunnyRabbiera on 2008-05-19
you said that this is on other computers right?
are they all linux PC's or you have some windows PC's?

---

### Post by taith on 2008-05-19
they are all ubuntu latest w/ all updates

the dvd is in the only dvd drive in the computer.

---

### Post by mc4man on 2008-05-19
try regionset again - wait till the dvd mounts ie. you can see icon on desktop

---

### Post by taith on 2008-05-19
the dvd is mounting, it does show on the desktop, and i'm still getting the same regionset error

---

### Post by stchman on 2008-05-19
> **taith said:**
> hey again!

when i put in a movie dvd, it cannot play it... i get an error from totem

An error occured
Could not read from resource.

the dvd itself mounts, allowing me to view the files, but i can neither play, nor copy(brasero) the movie...

any ideas?

i'm using hardy, if that affects anything...?

I can play DVDs perfectly.  Try this.

First:
[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

Second:
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

### Post by SunnyRabbiera on 2008-05-19
are you using AMD 64's on these computers?

---

### Post by taith on 2008-05-19
> are you using AMD 64's on these computers? 
this computer yes, other computers no

> I can play DVDs perfectly. Try this.

First:
[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

Second:
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)
seeing as even brasero cannot identify the disk, or regionset, i'm sure its not a codex problem...

---

### Post by SunnyRabbiera on 2008-05-19
Yes, it might very well be the DVD's.
how recent are these DVD's? I know some more modern disks use funky coding.

---

### Post by mc4man on 2008-05-19
I gotta go - your error is typical of having no region set and or corrupted keys in .dvdcss
If your region has been set then it's a moot point trying to run regionset, if it hasn't you'll have to one way or the other.
try regionset /dev/dvd1

---

### Post by taith on 2008-05-19
> Yes, it might very well be the DVD's.
how recent are these DVD's? I know some more modern disks use funky coding. 

as old as back to 7-10 years ago... perhaps some older :)

---

### Post by SunnyRabbiera on 2008-05-19
alright, but what studio are these from?
can you list the movies you have for us?
I know its a bit to ask, but I do know some titles can give linux issues.

---

### Post by taith on 2008-05-19
haha that'd be a longs story... +200 movies... um... for some... xmen 1-3, man from snowy river, sister act, zatoichi...... are the movies i've tried sofar...

as far as studios... dreamworks, disney, mgm, paramount, imperia, columbia pictures.......

---

### Post by SunnyRabbiera on 2008-05-19
Huh, this actually sounds like a very odd issue then.
What about the DVD players you have?
Do you keep them clean?
How old are them?

---

### Post by taith on 2008-05-19
agreed... very odd issue
we have a dvd player(for the tv)... which can play the dvds perfectly...
the dvds themselves are in mint condition...

---

### Post by SunnyRabbiera on 2008-05-19
and the ones in your computers are fine too correct?
I am running a checklist here you see, to assess what is going on here.

---

### Post by taith on 2008-05-19
of course...the one in the computer works correctly too(data)... aside from not being able play movies...

one of which is an LG burner, other is a HP lightscribe

---

### Post by SunnyRabbiera on 2008-05-19
any idea about the brand of the dvd player in your computer?
sorry for asking so many questions, I am just trying to see whats up here... if possible.

---

### Post by yogo on 2008-05-19
> **SunnyRabbiera said:**
> any idea about the brand of the dvd player in your computer?
sorry for asking so many questions, I am just trying to see whats up here... if possible.

Thats where I was heading after reading here, my guess is a non main stream writer like an xyz brand.

Get a new writer is it is an off brand writer, you can pick up Lite-ons for less than 25 with free shipping, and I have never had a problem with a lite-on drive.

---

### Post by mc4man on 2008-05-19
what could fill in some info gaps is with a dvd in the drive run
```
sudo lshw -C disk
```

---

### Post by taith on 2008-05-19
sudo lshw -C disk
  *-disk:0                
       description: ATA Disk
       product: ST3160023AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 8.05
       serial: 5JS2QE3Y
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=f52bcf0e
  *-disk:1
       description: ATA Disk
       product: ST31000340AS
       vendor: Seagate
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: SD04
       serial: 5QJ017DN
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0002e346
  *-cdrom
       description: DVD-RAM writer
       product: HL-DT-STDVD-RAM GSA-H55N
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 1.02
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: mode=udma4 status=ready
     *-medium
          physical id: 0
          logical name: /dev/hda

---

### Post by mc4man on 2008-05-19
Hate to keep harping on region thing but it really is the first thing you should resolve (if possible)
with the dvd mounted try regionset /dev/hda if no good try sudo regionset /dev/hda
did you do an upgrade or a fresh install?

---

### Post by taith on 2008-05-19
i did a fresh install :)

also, the regionset worked this time, however, brasero still cannot copy the cd(dvd to dvd or to .iso)... and vlc is the only player that can play any dvds :(

---

### Post by mc4man on 2008-05-19
what other player are you trying

---

### Post by taith on 2008-05-19
any/all movie player, mplayer, konquer...

---

### Post by mc4man on 2008-05-19
Did you clip the output from lshw -C disk?
should've asked earlier - what ver. of ubuntu are you using ?
look in filesystem -> /dev and see if there are any links named dvd, cdrom, cdrw and sr0, if so r.click and ck. target in properties
----------------------------------------------------------
post info from above 1st
most players default to /dev/dvd to play from - you can adjust in the players preferences to /dev/hda or make a link in /dev linking /dev/hda
something like sudo ln -s /dev/hda /dev/dvd
another option would be to switch your dvd drive to /dev/scd0

---

### Post by crjackson on 2008-05-19
> **taith said:**
> hey again!

when i put in a movie dvd, it cannot play it... i get an error from totem

An error occured
Could not read from resource.

the dvd itself mounts, allowing me to view the files, but i can neither play, nor copy(brasero) the movie...

any ideas?

i'm using hardy, if that affects anything...?


Try this...

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Hardy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

---

### Post by Sinkingships7 on 2008-05-19
I didn't thoroughly read the previous posts, so I apologize if this suggestion has already been offered.

First, make sure you have all of the proper gstreamer plugins installed. If you don't this will do it:
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
```

Then, to be able to play DVD's you have to do this:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Hope that helps.

---

