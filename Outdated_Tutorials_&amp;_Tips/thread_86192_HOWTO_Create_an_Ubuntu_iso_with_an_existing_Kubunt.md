---
title: "HOWTO: Create an Ubuntu iso with an existing Kubuntu one (or viceversa) using Jigdo."
date: 2005-11-04
forum: Outdated Tutorials &amp; Tips
---

### Post by bored2k on 2005-11-04
I am no Jigdo guru, just now I learned how to make it work and decided to post this little howto so others who didn't know just like me can do the same. Thanks to it, instead of downloading about 600mb, I only had to get about 30mb.
> Jigdo addresses all the problems with the other methods of obtaining Debian ISO images:

* Unlike downloading the entire ISO image, it can take an outdated CD (or a loop mounted outdated ISO image), download only the files that have changed since the CD (or ISO image) was created and create a new updated ISO. Very similar to how you use cvs to update source code.
In other words, it can pick up already downloaded files and use them in the process of creating a new image, saving you from the pain of downloading an entire image all over again. Why download the Ubuntu disc when you have its base in your Kubuntu one (and viceversa)? Hello jigdo.

```
 sudo apt-get install jigdo-file 
```
* Insert your (K)ubuntu disc.
* Go to your download site and copy the link for the jigdo file you want ([example]("http://us.releases.ubuntu.com/releases/5.10/ubuntu-5.10-install-i386.jigdo")).
* ```
jigdo-lite
```
* This is what you will now get (for this example, I'm using the 386 install jigdo file, building from a Kubuntu disc and my deb archives):
```

Jigsaw Download "lite"
Copyright (C) 2001-2004  |  jigdo@
Richard Atterer          |  atterer.net
Getting mirror information from /etc/apt/sources.list

-----------------------------------------------------------------
To resume a half-finished download, enter name of .jigdo file.
To start a new download, enter URL of .jigdo file.
You can also enter several URLs/filenames, separated with spaces,
or enumerate in {}, e.g. `http://server/cd-{1_NONUS,2,3}.jigdo'
jigdo: 
```Here, paste the link of your .jigdo file
```
http://us.releases.ubuntu.com/releases/5.10/ubuntu-5.10-install-i386.jigd o

Not downloading .jigdo file - `ubuntu-5.10-install-i386.jigdo' already present

-----------------------------------------------------------------
Images offered by `http://us.releases.ubuntu.com/releases/5.10/ubuntu-5.10-insta ll-i386.jigdo':
  1: 'Ubuntu 5.10 "Breezy Badger" - Release i386' (ubuntu-5.10-install-i386.iso)

Further information about `ubuntu-5.10-install-i386.iso':
Generated on Wed, 12 Oct 2005 17:25:40 +0100

-----------------------------------------------------------------
If you already have a previous version of the CD you are
downloading, jigdo can re-use files on the old CD that are also
present in the new image, and you do not need to download them
again. Mount the old CD ROM and enter the path it is mounted under
(e.g. `/mnt/cdrom').
Alternatively, just press enter if you want to start downloading
the remaining files.
```
Here, just enter your CD-ROM mount point (check that in /etc/fstab; by default /media/cdrom0).After checking the entire disc (may take a few minutes), this prompt will appear:
```
Found 1308 of the 1754 files required by the template
Copied input files to temporary file `ubuntu-5.10-install-i386.iso.tmp' - repeat command and supply 
more files to continue

```446 files are missing (not bad!). To get some more, we will now use our archives. So when asked for a new directory to scan (just like the previous one), put this line:```

/var/cache/apt/archives
```In my case, I had a lot of files so here's what I got:
```
Found **220** of the 446 files required by the template
Copied input files to temporary file `ubuntu-5.10-install-i386.iso.tmp' - repeat command and supply 
more files to continue
``` Down to 220. I had no more files so I just pressed enter (twice) and it downloaded the remaining files and built the cd image.

Note: Jigdo also works wonders for building daily images out of builds, but ATM, I don't think none of us feel the need for daily Dapper images.

---

### Post by supriyadisw on 2006-09-01
Thanks for the tutorial. How to create jigdo file ourself? Can we do this? Thank a bunch

Gud lak

---

### Post by kurian on 2006-09-03
Do you know how to create a xubuntu alternate cd using a kubuntu live cd................


OR to create a xubuntu live cd using kubuntu live cd................

please post a quick reply.........

---

### Post by danderson3 on 2006-09-03
just follow the instructions.  I don't think it matters
what CD you start with.

---

### Post by kurian on 2006-09-04
hi, iam new to linux ..........


Can any one please tell me where i will get the jigdo file for 
"xubuntu live cd" .........................

Can any one can help me......................?????
Will be really thankful......................

---

### Post by danderson3 on 2006-09-04
I don't see a jigdo file for i386 6.0.6.1 desktop :-(

---

### Post by kurian on 2006-09-04
hi , could anyone mail me the jigdo file and jigdo template for the xubuntu desktop live cd (for intelx86 pc).........I have heard that its easy to make one if you are having a xubuntu desktop live cd and jigdo tools with you................



Do anyone know how to create a Xubuntu cd using a kubuntu live cd and xubuntu packages..............

---

