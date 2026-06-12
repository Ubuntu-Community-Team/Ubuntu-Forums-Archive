---
title: "How to create a DVD-Video image under Linux with mkisofs"
date: 2006-01-21
forum: Outdated Tutorials &amp; Tips
---

### Post by joselin on 2006-01-21
How to create a DVD-Video image under Linux with mkisofs


Prerequisites:
--------------

Prerequisite is that you have a valid VIDEO_TS/AUDIO_TS structure with valid VOB, BUP and IFO files. If any of those files are not up to the spec of the DVD-Video specification the burned video will not play in a stand alone player. This document is not how to rip a DVD or author a DVD it's about the image and burning part of the DVD-Video making. 

The  VIDEO_TS/AUDIO_TS can look something like this if you do a ls -lR in the top directory.

```
.:
total 16
drwxr-xr-x    4 root     root         4096 Jan 22 18:45 .
dr-xr-xr-x    4 root     root         4096 Jan 22 19:08 ..
dr-x------    2 root     root         4096 Jan 22 16:34 AUDIO_TS
dr-x------    2 root     root         4096 Jan 22 18:58 VIDEO_TS

./AUDIO_TS:
total 8
dr-x------    2 root     root         4096 Jan 22 16:34 .
dr-x------    4 root     root         4096 Jan 22 18:45 ..

./VIDEO_TS:
total 4051408
dr-x------    2 root     root         4096 Jan 22 18:58 .
dr-x------    4 root     root         4096 Jan 22 18:45 ..
-r--------    1 root     root        12288 Jan 22 16:47 VIDEO_TS.BUP
-r--------    1 root     root       159744 Jan 22 16:34 VIDEO_TS.VOB
-r--------    1 root     root        71680 Jan 22 16:47 VTS_01_0.BUP
-r--------    1 root     root        71680 Jan 22 16:47 VTS_01_0.IFO
-r--------    1 root     root       159744 Jan 22 16:34 VTS_01_0.VOB
-r--------    1 root     root     1073565696 Jan 22 16:47 VTS_01_1.VOB
-r--------    1 root     root     1073565696 Jan 22 16:47 VTS_01_2.VOB
-r--------    1 root     root     1073565696 Jan 22 16:47 VTS_01_3.VOB
-r--------    1 root     root     1073565696 Jan 22 16:47 VTS_01_4.VOB
-r--------    1 root     root     923359232 Jan 22 16:47 VTS_01_5.VOB
```

It's important that you have both the AUDIO_TS and VIDEO_TS directory even if shouldn't make a difference if the AUDIO_TS one is missing. Some player simply refuse to play the disk if there is no AUDIO_TS directory. You must have all file names in UPPER CASE, all files should have the 400 permission and directories should have 500 permission. I don't know how important the latter once are but it's always nice to be on the safe side.



DVD-Video physical layout:
--------------------------

In order to make a valid DVD-Video image the files in the image has to ordered in a specific physical order. It's important the the first file on the disk is the VIDEO_TS.IFO file. The DVD player will seek the VIDEO_TS.IFO and from it get the information on which sectors the other files start and end 

The physical layout must follow the roules in the VIDEO_TS.IFO, and the VTS_XX_0.IFO files. E.g if the VIDEO_TS.IFO specifies that VTS_01_0.IFO starts at sector 345 (offset from VIDEO_TS.IFO) it must do so. There are similar "rules" in all the IFO files.

It's also imperative that VTS_XX_1.VOB comes before VTS_XX_2.VOB sector wise. A stand alone DVD player doesn't have a clue about individual VOB files and plays them in one chunk starting at sector X and end at sector Y.

The file order is as follows in our case:

```
VIDEO_TS.IFO
VIDEO_TS.BUP
VTS_01_0.IFO
VTS_01_0.VOB
VTS_01_1.VOB
VTS_01_2.VOB
VTS_01_3.VOB
VTS_01_4.VOB
VTS_01_5.VOB
VTS_01_0.BUP
```

If your DVD-Video would contain more than one "vob" set it could looks like this (In this case we had a VIDEO_TS.VOB menu VOBS are optional hence you may not have a VTS_XX_0.VOB)

```
VIDEO_TS.IFO
VIDEO_TS.VOB
VIDEO_TS.BUP
VTS_01_0.IFO
VTS_01_0.VOB
VTS_01_1.VOB
VTS_01_2.VOB
VTS_01_3.VOB
VTS_01_4.VOB
VTS_01_0.BUP
VTS_02_0.IFO
VTS_02_0.VOB
VTS_02_1.VOB
VTS_02_2.VOB
VTS_02_3.VOB
VTS_02_4.VOB
VTS_02_0.BUP
```



Controlling the physical layout of the iso/udf image:
-----------------------------------------------------

To be able to control the physical layout of the iso/udf DVD-Video image you will need the 1.11a27 alpha/beta of mkisofs it includes the latest patches that enables 
mkisofs to parse the IFO files and extract the information how to layout the DVD-Video file structure. Mkisofs - allready has capability to sort the files so you don't need to do anything besides using the right switch :). 


Making the image with mkisofs:
------------------------------

Now when we have made the sort file we are ready to burn the image. Let say that we have the top of our AUDIO_TS/VIDEO_TS structure under /DVD_PROJECTS/HOMEDVD/ an example session of mkisofs would be like this.

```
$ cd /DVD_PROJECTS/HOMEDVD/
$ ls -R
.:
.  ..  AUDIO_TS  VIDEO_TS

./AUDIO_TS:
.  ..

./VIDEO_TS:
.   VIDEO_TS.BUP  VIDEO_TS.VOB  VTS_01_0.IFO  VTS_01_1.VOB  VTS_01_3.VOB
..  VIDEO_TS.IFO  VTS_01_0.BUP  VTS_01_0.VOB  VTS_01_2.VOB  VTS_01_4.VOB
```

#######################################################################
# Now we know that every thing is correct and we can make the image!
#######################################################################

```
$ cd /
$ mkisofs -dvd-video -o /DVD_PROJECTS/homedvd.img /DVD_PROJECTS/HOMEDVD/ 
  0.25% done, estimate finish Tue Jan 22 19:14:54 2002
  0.49% done, estimate finish Tue Jan 22 19:11:33 2002
[SNIP]
 99.80% done, estimate finish Tue Jan 22 19:12:21 2002
Total translation table size: 0
Total rockridge attributes bytes: 0
Total directory bytes: 4096
Path table size(bytes): 42
Max brk space used 4000
2024016 extents written (3953 Mb)
$
```


Verifying the image with isoinfo:
---------------------------------

It's always a good idea to verify the image before we burn it. 


```
$ isoinfo -i homedvd.img -l

Directory listing of /
d---------   0    0    0            2048 Feb  9 2002 [    277]  .
d---------   0    0    0            2048 Feb  9 2002 [    277]  ..
d---------   0    0    0            2048 Feb  9 2002 [    278]  VIDEO_TS

Directory listing of /VIDEO_TS/
d---------   0    0    0            2048 Feb  9 2002 [    278]  .
d---------   0    0    0            2048 Feb  9 2002 [    277]  ..
----------   0    0    0            8192 Feb  9 2002 [    311]  VIDEO_TS.BUP;1
----------   0    0    0            8192 Feb  9 2002 [    279]  VIDEO_TS.IFO;1
----------   0    0    0           86016 Feb  9 2002 [2136055]  VTS_01_0.BUP;1
----------   0    0    0           86016 Feb  9 2002 [    343]  VTS_01_0.IFO;1
----------   0    0    0         4345856 Feb  9 2002 [    407]  VTS_01_0.VOB;1
----------   0    0    0      1073739776 Feb  9 2002 [   2551]  VTS_01_1.VOB;1
----------   0    0    0      1073739776 Feb  9 2002 [ 526838]  VTS_01_2.VOB;1
----------   0    0    0      1073739776 Feb  9 2002 [1051125]  VTS_01_3.VOB;1
----------   0    0    0      1073739776 Feb  9 2002 [1575412]  VTS_01_4.VOB;1
----------   0    0    0        74405888 Feb  9 2002 [2099699]  VTS_01_5.VOB;1
```

It's the numbers between the brackets that we are interested in. It tells us the
start sector of each file. VIDEO_TS.IFO must have the lowest sector number of
all files! 

```
[    279]  VIDEO_TS.IFO
[    311]  VIDEO_TS.BUP
[    343]  VTS_01_0.IFO
[    407]  VTS_01_0.VOB
[   2551]  VTS_01_1.VOB
[ 526838]  VTS_01_2.VOB
[1051125]  VTS_01_3.VOB
[1575412]  VTS_01_4.VOB
[2099699]  VTS_01_5.VOB
[2136055]  VTS_01_0.BUP
```

Now do the same on your original DVD-Video (I'm asuming that you are doing a backup). The important thing here is to do a "original-VIDEO_TS.IFO-startsector - copy-VIDEO_TS.IFO-startsector" and note down the diff between the files. Now repete the same calculation for each of the files. The diff should be the same for all file pairs.

Now you can burn your image with your favourite software.

---

### Post by olivierp on 2006-11-21
When copying a "howto", please have the decency to at list list your sources. I happen to have local copies of the 2 pages where this is explained.
Have a look here: [http://web.archive.org/web/20060329122624/http://dvd.chevelless230.com/index.html](http://web.archive.org/web/20060329122624/http://dvd.chevelless230.com/index.html)
and here if you want even older versions:
[http://web.archive.org/web/*/http://dvd.chevelless230.com/index.html](http://web.archive.org/web/*/http://dvd.chevelless230.com/index.html)

---

### Post by joselin on 2007-04-24
I had done it if I had known it once I did it. Anyway, apologies for that. I receive the howto in a mail (without any reference) after looking something like that for a long time.

Please accept my apologies again.

Regards.

---

### Post by hihihi on 2008-06-04
thanks for posting this, its not easy in a quick search in an urge for quick solution

---

