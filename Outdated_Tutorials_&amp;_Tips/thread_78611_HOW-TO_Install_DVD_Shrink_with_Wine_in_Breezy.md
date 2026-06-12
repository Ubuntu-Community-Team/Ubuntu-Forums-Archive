---
title: "HOW-TO: Install DVD Shrink with Wine in Breezy"
date: 2005-10-18
forum: Outdated Tutorials &amp; Tips
---

### Post by manicka on 2005-10-18
This how-to will install DVD shrink with the new beta version of wine (0.9) from WineHQ. The version of Wine that comes with breezy will install DVD Shrink but will not analyse your original dvd's properly. As always check the relevant copyright laws for your country re backup of DVD's.

I'm assuming that you already have libdvdcss2 installed so that you can play your retail dvd's. If not follow the how-to here

[http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs+easy](http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs+easy)


**Installing Wine**

The new Beta (0.9) release is now valiable at WineHQ and fixes a major bug with the preview window in DVD Shrink. Please use the WineHQ deb in preference to the version that comes with breezy  -

Run
```
sudo gedit /etc/apt/sources.list
```

add these two lines two your souces.list

```
deb http://wine.sourceforge.net/apt binary/
deb-src http://wine.sourceforge.net/apt source/
```

now update and install wine

```
sudo apt-get update
sudo apt-get install wine
```

**Configuring Wine**

```
alt-f2
winecfg
```

This will setup your wine directories  in ~/ and start the winecfg control panel

Once the winecfg control panel starts, go to the 'Drives' tab and allow it to autodetect your drive setup, by clicking on the 'Auto Detect' button. Close winecfg

N.B. some users have found that DVD Shrink is not detecting their drives properly. This advice from [fergus]("http://ubuntuforums.org/member.php?u=18711") may help:

*By default, when you add a drive to wine it thinks its a hard drive and not a cd-rom. Try going into winecfg and to the devices tab. Then enable the Advanced options and select your dvd drive. It might be listed as a hard drive, change that to cd-rom and then DVD Shrink should pick it up.*

**Further advice.**

[I]Recently I did a fresk wine install by deleting my wine directory and then recreating my wine directory and installing dvd shrink again. I to ran into the 'drive not being detected' problem. A solution which worked was to download and install the latest version of [winetools]("http://www.von-thadden.de/Joachim/WineTools/") and use this to setup my basic wine configuration instead (after installation use the command '/usr/local/winetools/wt0.9jo' instead of 'wt' to start winetools). I would suggest using Winetools to create the fake windows directory, install arial font, install dcom98.exe and Microsoft Foundation Classes 4x. Winetools will also install IE6sp1 but I would not recommend installing this piece of junk. 

IE6 will also mess up the way that dvd shrink runs (surrounding screen turns black) if ie6 is installed as well, so do yourself a favour and give it a miss. Once you have created a base setup using Winetools, you should be able to install dvdshrink as per the rest of this how-to.... enjoy [/I]

**Installing DVD Shrink**

Download the DVD Shrink installer. The current version is 3.2.015 and you'll need to do a Google search (try DVD Shrink download) to find it, as the main site no longer carries links to the installer.

In a terminal in the directory that you downloaded DVd Shrink to, run the command 

```
wine dvdshrink32setup.exe
``` (or whatever the exe file is called)

Follow the installer instructions to install. At the end of the installation uncheck the box that asks to run DVD Shrink now.

when the installer is finished run

```
alt-f2
winecfg
```

This will start the winecfg panel again as we have to configure it to run DVD Shrink properly

In the Applications tab window click on 'Add application'

Navigate your way into Program Files-->DVD Shrink and find 'DVD Shrink 32.exe'

highlight this file and click on the open button.

This will now take you back to the Applications Tab window and DVD Shrink should appear in the list in that window.

Highlight DVD Shrink then go down to the Windows Version box and choose 'Windows XP' from the drop down menu.

Click on the 'Apply' button then OK to exit winecfg.

**Starting and Using DVD Shrink**

The installer should have created an icon on your desktop. You can use this to start DVD Shrink or type the following command in a terminal

wine "C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe"

You can also use this command to make an entry in the Gnome menus with Smeg/Alacarte


Enjoy!

------------------------------------------------------------------------------------

Edit: added to the wiki
[https://wiki.ubuntu.com/dvdshrink](https://wiki.ubuntu.com/dvdshrink)

Also available at the [Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/Main_Page")

---

### Post by MetalMusicAddict on 2005-10-18
I get this after I "autodetect" my drives.

```
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system" is not accessible.
Warning: could not find DOS drive for current working directory '/home/mma', starting in the Windows directory.

```
I even had a [thread]("http://www.ubuntuforums.org/showthread.php?t=76537") about it.

---

### Post by manicka on 2005-10-18
Try renaming your .wine folder then rebuilding it again when you start wine/winecfg.

---

### Post by MetalMusicAddict on 2005-10-19
[QUOTE=manicka]Try renaming your .wine folder then rebuilding it again when you start wine/winecfg.[/QUOTE]
Your a God among men. ;)

---

### Post by BLTicklemonster on 2005-10-26
sudo apt-get update
sudo install dvdbackup


=


bill@ubuntumonster:~$ sudo apt-get update
Password:
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Fetched 50.9kB in 1s (31.7kB/s)
Reading package lists... Done
bill@ubuntumonster:~$ sudo install dvdbackup
install: too few arguments
Try `install --help' for more information.



now what?


and sudo apt-get dvdbackup 

=

bill@ubuntumonster:~$ sudo apt-get dvdbackup
E: Invalid operation dvdbackup

---

### Post by evs on 2005-10-26
[QUOTE=BLTicklemonster]sudo apt-get update
sudo install dvdbackup

...

now what?

[/QUOTE]

should be 
```
sudo apt-get update
sudo apt-get install dvdbackup
```

---

### Post by bionnaki on 2005-10-27
excellent! works great!

---

### Post by BLTicklemonster on 2005-10-27
bill@ubuntumonster:~$ dvdbackup -i /dev/dvd -o /home/bill/ -M
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading


argh. I have 2 drives. slave is the reader.

---

### Post by manicka on 2005-10-30
Yeah!, preview bug fixed in beta release of Wine

How-to updated here and on wiki :)

---

### Post by BLTicklemonster on 2005-11-01
Okay, just went through it again, and dvdshrink is working just the way it did in windows, it is encoding right now, I hope it will burn once done.

Only problem is with dvd decrypter. I get this when I run it:

[img]http://www.hawkwinds.com/tickle/dvdcrypter.jpg[/img]

It won't detect any drives! 

But seeing as how dvdshrink looks like it's working, that may not be a problem.

---

### Post by manicka on 2005-11-02
In winecfg set the windows version to nt4.0 for dvd decypter and see if that makes a difference

---

### Post by hda on 2005-11-02
Hi!
I followed the instructions step by step and DVDshrink installed properly. But when using 'Open Disc' I get a selection box showing 'Select DVD drive' which is empty.

When I try to open it manually by using 'Open Files' and selecting the DVD Drive I get an error box saying 'Failed to read file "d:\VIDEO_TS\VIDEO_TS.VOB". That file exists though in Nautilus the filenames are lowercase.

Any suggestions?

_hda_

---

### Post by manicka on 2005-11-02
did you get winecfg to detect  your drives?

Is DVD shrink set to run as Windows XP in winecfg?

---

### Post by hda on 2005-11-02
[QUOTE=manicka]did you get winecfg to detect  your drives?

Is DVD shrink set to run as Windows XP in winecfg?[/QUOTE]

yes and yes.

winecfg mapped /media/cdrom0 to drive letter D:. Also tried different settings for dvdshrink.exe with no success.

---

### Post by BLTicklemonster on 2005-11-02
me too me too

---

### Post by BLTicklemonster on 2005-11-02
BTW, I got dvdshrink to work as far as it will encode the dvd and put it on c:\name of movie, but it won't burn it. I have use nero unchecked. Now what do I use to burn it.

---

### Post by PhilR on 2005-11-02
[QUOTE=BLTicklemonster]BTW, I got dvdshrink to work as far as it will encode the dvd and put it on c:\name of movie, but it won't burn it. I have use nero unchecked. Now what do I use to burn it.[/QUOTE]
If you have the compressed and encoded files on your HD then you should be able to burn them with K3b or Gnomebaker (I'm assuming, I only have K3B)

---

### Post by fut21 on 2005-11-02
When i install wine 0.9 in SUSE 10 everything works (cd/dvd drives) with dvdshrink and dvddecrypter. So how come it dont work in ubuntu ??

---

### Post by MBro on 2005-11-02
I have the exact same problems, even with nt4

No drives detect in decrypter

---

### Post by manicka on 2005-11-03
[QUOTE=BLTicklemonster]BTW, I got dvdshrink to work as far as it will encode the dvd and put it on c:\name of movie, but it won't burn it. I have use nero unchecked. Now what do I use to burn it.[/QUOTE]

I usually use dvd shrink to encode to an iso image then burn it with nautilus' built in burner or k3b

---

### Post by manicka on 2005-11-03
[QUOTE=fut21]When i install wine 0.9 in SUSE 10 everything works (cd/dvd drives) with dvdshrink and dvddecrypter. So how come it dont work in ubuntu ??[/QUOTE]

they work fine for me. What's the problems you are havoing

---

### Post by manicka on 2005-11-03
[QUOTE=MBro]I have the exact same problems, even with nt4

No drives detect in decrypter[/QUOTE]

Try starting dvd dceypter with a dvd already in the drive. Try quitting and starting a few times. 

I only installed dvd decrypter out of interest. dvdbackup is a native command line app that will do just as good a job.
[B]
To install dvdbackup[/B]

```
sudo apt-get update
sudo install dvdbackup
```

This command in a terminal will backup your dvd to your home drive. Be patient, it takes a while (about 10 mins for me).

dvdbackup -i /dev/dvd -o /home/yourusername/ -M

---

### Post by bionnaki on 2005-11-03
dvdbackup works great.

---

### Post by manicka on 2005-11-03
This How-To is also available at the [Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/Main_Page")

---

### Post by BLTicklemonster on 2005-11-03
Okay. Finally found a dbd burner in linux that was made by someone who understood ease of operation! K3b just loaded up and went at it.


(lol I kept trying to load up k3d, and was like wow, a 3d dvd!!! doh)

---

### Post by awtomlinson on 2005-11-03
i followed the dvd shrink installation guide to the letter, and wine won't allow dvdshrink to see my dvd or cd drives, even though they appear in the winecfg setup gui.  i completed the following, to no avail:

1.  completely removed the previous version of wine
2.  installed the wine beta from the sourceforge deb repository
3.  deleted my old .wine folder
4.  ran winecfg and installed dvdshrink.  again, dvd and cd drive appeared in winecfg
5.  closed dvdshrink and ran winecfg again.

i have tried setting the os in wine to both winxp and nt 4.0 for dvdshrink.  also, i tried dvddecrypter, and the same issue occurs, no dvd or cd drives appear.  i have noticed that there is no config file in wine like there used to be.  can anyone please help?  i must have my dvdshrink, i'm tired of booting into windows to make dvd copies!!

---

### Post by swhit on 2005-11-03
DVD Shrink doesn't need to see your drives if you use an image of the dvd you want to copy. Here's what I do, and it has yet to fail for me.

-----Needed software-----

From synaptic, install wine and dvdbackup.
Need to get libdvdcss from somewhere, search the forums.
Need to get DVD Shrink from somewhere, search the forums.
mkisofs and growisofs should already be installed from the default ubuntu installation.

----Install DVD Shrink using Ubuntu wine-------

unzip dvdshrink32setup.zip
chmod +x dvdshrink32setup.exe
wine ./dvdshrink32setup.exe

Follow the directions from the setup, installing DVD Shrink where ever you desire.

----Directions for copying a DVD----------------

Rip the movie from the DVD:

dvdbackup -M -i/dev/dvd -o/my/dvd/backup/dir/

Make a .img file from it:

mkisofs -dvd-video -o movie.img /my/dvd/backup/dir/NAME_OF_MOVIE/

To use DVD Shrink to compress the movie, go to the directory where DVD Shrink is installed:

wine ./"DVD Shrink 3.2.exe"

Choose "Open Disc Image" under the "File" menu and open movie.img that you just made. Compress or re-author the full dvd as normal. DVD Shrink will make the new DVD file set, i.e. the AUDIO_TS and VIDEO_TS folders, in the following directory:

~/.wine/drive_c/NAME_OF_MOVIE

where ~ is your home directory.

Next, make a .img file from the compressed movie:

mkisofs -dvd-video -o compressed_movie.img ~/.wine/drive_c/NAME_OF_MOVIE

again, ~ is your home directory.

Then burn the compressed dvd image using growisofs:

growisofs -dvd-compat -Z /dev/dvd=./compressed_movie.img

---------End of Directions-------------

I hope this works for everyone. It does the job for me.

cheers.

---

### Post by awtomlinson on 2005-11-03
i understand, but this kind of defeats the purpose of dvdshrink.  i need it to be my one stop dvd shrinking/ripping application.  this worked like a charm in warty and hoary, and people have gotten it to work in breezy.  how can i make dvdshrink, or wine for that matter, detect my dvd and/or cd drives?  again, the drives appear when using winecfg.

---

### Post by manicka on 2005-11-03
[QUOTE=awtomlinson]i understand, but this kind of defeats the purpose of dvdshrink.  i need it to be my one stop dvd shrinking/ripping application.  this worked like a charm in warty and hoary, and people have gotten it to work in breezy.  how can i make dvdshrink, or wine for that matter, detect my dvd and/or cd drives?  again, the drives appear when using winecfg.[/QUOTE]
I wish I knew how to help on this one. Your previous post outlines all the steps I would have recommended to fix the problem.
The only thing I can think of is, are you using the most recent release of dvd shrink?

---

### Post by awtomlinson on 2005-11-03
almost positive that i'm using the current version.  i will check when i get home.

---

### Post by awtomlinson on 2005-11-03
by the way, what is the latest version of dvdshrink?

---

### Post by Neo40 on 2005-11-03
Hi,

I have 2 problems. First,  like some people here, dvd shrink don't see my dvd drives when I click "open disk":

hdc: HL-DT-ST DVDRAM GSA-4163B, ATAPI CD/DVD-ROM drive
hdd: HL-DT-STDVD-ROM GDR8163B, ATAPI CD/DVD-ROM drive

However, if I go to File->Open...->then I browse to /media/cdrom0 it works. So, its not big deal...

My second problem is I can't see the preview. I only get a black screen.

Thanks for your help

---

### Post by awtomlinson on 2005-11-04
i have the solution to dvdshrink not recognizing my dvd or cd drives.  in winecfg, even though the drive mapping will appear, you must select the drive, then click Show Advanced.  Then, under Type, ensure it is set to CD-ROM.  even though winecfg mapped the drive as /media/cdrom0, its type was defaulted to local hard drive.  everything works great now.

---

### Post by fut21 on 2005-11-04
Nice you trick also works with dvddecrypter. Thanks:)

---

### Post by manicka on 2005-11-04
[QUOTE=awtomlinson]i have the solution to dvdshrink not recognizing my dvd or cd drives.  in winecfg, even though the drive mapping will appear, you must select the drive, then click Show Advanced.  Then, under Type, ensure it is set to CD-ROM.  even though winecfg mapped the drive as /media/cdrom0, its type was defaulted to local hard drive.  everything works great now.[/QUOTE]

Good work, I'll add this to the how-to :)

---

### Post by BLTicklemonster on 2005-11-04
[QUOTE=fut21]Nice you trick also works with dvddecrypter. Thanks:)[/QUOTE]
schweet!

---

### Post by awtomlinson on 2005-11-04
with dvddecrypter, i had to set the file system to nt 4.0.  winxp would not detect the drives.

---

### Post by bionnaki on 2005-11-04
dvddecrypter still is not detected my drives...

when I select "cdrom" in advanced, I will click apply & then ok.
but this setting is not saved when I open winecfg again & check.

---

### Post by fut21 on 2005-11-05
[QUOTE=bionnaki]dvddecrypter still is not detected my drives...

when I select "cdrom" in advanced, I will click apply & then ok.
but this setting is not saved when I open winecfg again & check.[/QUOTE]

Note that dvddecrypter should be set with nt4.0 and NOT winXP option.

---

### Post by Neo40 on 2005-11-14
Hi,

When I insert a dvd movie and launch dvd shrink, I can see  the directories like main, extras, etc...If I want to move up in the directories for instance, then dvd shrink does not responding and I have to kill it. I tried many times with the same behavior. Is it just me with this problem?
Also, how long it should take to backup a movie? Actually, dvdshrink is backing the movie "saw" for now 20 minutes and I have only 28% done. It shows me its rate at 900 kb/s and it says 1 hour 26 min remaining!! My cpu is 1.2 Ghz. Is it normal?

Thanks for your help

EDIT: Found solution to my problem: I deleted my ~/.wine directory and re-installed wine. Works fine now. But how long it should take to backup a movie?

---

### Post by carney1979 on 2005-11-15
If you want to copy DVD's natively under Linux, then look at xDVDShrink. The link to the home page is [http://dvdshrink.sourceforge.net/]("http://dvdshrink.sourceforge.net/")

I've tried copying one dvd and this program seems to copy only the feature, not the menus or extras.

The ripped DVD is compressed to fit a normal (not dual layered) DVD and picture quality is excellent.

The programmer is a Mandrake kind of guy, but he provides a tarball along with the Mandrake rpm versions that is already built and has an install script.

You will be told during installation if you need any unmet dependencies. In my case, I was only missing DVDAuthor and gocr. Both are in universe/multiverse.

There is both a commandline version, and a gui frontend to the commandline version. The gui frontend is the file named xdvdshrink.pl.

I'm only suggesting this alternative for those who would prefer a native Linux open source alternative to backing up their private DVD collection.

This program should NOT be used to copy DVD's that you do not own. :(

David

<ADDED INFO>

I just tried a second DVD and the copying process failed. Just be aware that your mileage may vary with this solution.

---

### Post by escobar on 2005-11-16
[QUOTE=carney1979]If you want to copy DVD's natively under Linux, then look at xDVDShrink. The link to the home page is [http://dvdshrink.sourceforge.net/]("http://dvdshrink.sourceforge.net/")

I've tried copying one dvd and this program seems to copy only the feature, not the menus or extras.

The ripped DVD is compressed to fit a normal (not dual layered) DVD and picture quality is excellent.

The programmer is a Mandrake kind of guy, but he provides a tarball along with the Mandrake rpm versions that is already built and has an install script.

You will be told during installation if you need any unmet dependencies. In my case, I was only missing DVDAuthor and gocr. Both are in universe/multiverse.

There is both a commandline version, and a gui frontend to the commandline version. The gui frontend is the file named xdvdshrink.pl.

I'm only suggesting this alternative for those who would prefer a native Linux open source alternative to backing up their private DVD collection.

This program should NOT be used to copy DVD's that you do not own. :(

David

<ADDED INFO>

I just tried a second DVD and the copying process failed. Just be aware that your mileage may vary with this solution.[/QUOTE]


I used this and it does work well. Is there an app that will get the feature and all the extras as well? Rather than mess around with wine, I would rather use all native apps if possible.

---

### Post by carney1979 on 2005-11-17
I know of no native Linux apps that will get the whole DVD.

I have a dual-layered DVD writer and I can back up a movie using native Linux software available in the Ubuntu archives, but during playback, the DVD freezes about midway through the movie and won't go further. :(

David

---

### Post by escobar on 2005-11-18
[QUOTE=carney1979]I know of no native Linux apps that will get the whole DVD.

I have a dual-layered DVD writer and I can back up a movie using native Linux software available in the Ubuntu archives, but during playback, the DVD freezes about midway through the movie and won't go further. :(

David[/QUOTE]


Well back to doing it in Windows....thanks anyway.

---

### Post by manicka on 2005-11-18
[QUOTE=escobar]Well back to doing it in Windows....thanks anyway.[/QUOTE]
If your happy to run it in Windows then why not Wine?

---

### Post by escobar on 2005-11-18
[QUOTE=manicka]If your happy to run it in Windows then why not Wine?[/QUOTE]


DVD Shrink doesn't work properly, I get the same issue where it won't see my DVD drive. Attempting to manually search and open it results in an error, I forget what it says (I'm at work). Judging by the above posts, I don't believe this can be resolved right now. What I was referring to is xDVDShrink that does in fact work fine. I just wanted something that could get the extras off the disc as well. Since no one knows of any native apps that will do so, I'll go back to backing up my DVD's using DVDShrink in Windows.

---

### Post by manicka on 2005-11-18
[QUOTE=escobar]DVD Shrink doesn't work properly, I get the same issue where it won't see my DVD drive. Attempting to manually search and open it results in an error, I forget what it says (I'm at work). Judging by the above posts, I don't believe this can be resolved right now. What I was referring to is xDVDShrink that does in fact work fine. I just wanted something that could get the extras off the disc as well. Since no one knows of any native apps that will do so, I'll go back to backing up my DVD's using DVDShrink in Windows.[/QUOTE]
Yes, that seems to be an error that some are encountering. I can't explain it as it doesn't happen to me. Some people have had success with manually setting the drive to be a cdrom as autodetect sometimes picks it up as a hard drive.

---

### Post by carney1979 on 2005-11-19
The best way I've found to rip the "whole DVD" using Linux apps combined with Windows apps using Wine, is to first rip the disk with vobcopy, make an iso image with mkisofs, shrink it with Wine/dvdshrink, then burn it with growisofs.

PLEASE NOTE THAT THIS PROCEDURE MAY BE ILLEGAL IN SOME COUNTRIES. THIS INFO IS **NOT** INTENDED TO AID IN PIRACY OF DVD MOVIES, BUT FOR MAKING LEGAL FAIR USE BACKUPS OF MOVIES THAT ARE LEGALLY OWNED BY THE INDIVIDUAL.

This procedure assumes the user is using Gnome with Ubuntu Linux and the DVD movie disk has been inserted into the DVD drive, and any movie playing programs that may autostart have been exited.

It also assumes the user has installed the following packages:

vobcopy
dvd+rw-tools
mkisofs

Please substitute your username anytime you see **user**. Also, substitute a movie name *without* spaces anytime you see **movie**.

First, create a folder named dvd in your home directory, open a Gnome-terminal, then do this:

vobcopy /media/cdrom0 -l -n 1 -O . -t moviename

It will take several minutes for the movie to copy, then do this to make an ISO image of the movie you just ripped:

mkisofs -dvd-video -udf /home/**user**/dvd/**movie** > /home/**user**/dvd/**movie**.iso

Then start dvdshrink using Wine and go to File >> Open Disc Image and cruise to the just ripped 8 gig + image and open it. 

After dvdshrink has analyzed the DVD image, hit the backup button and make sure to tell dvd shrink to save the movie as an iso image.

This will take some time. 

When dvdshrink is done, exit it. then go back to your Gnome-terminal and go to /home/**user**/dvd and do this:

growisofs -dvd-compat -Z /dev/dvd=/home/**user**/dvd/**movie**.iso

Eject the disk and you're done.

David

---

### Post by manicka on 2005-11-19
Yes, I was using a similar method before with dvdbackup as the breezy version of wine didn't allow dvd shrink to preview discs properly. This has been fixed in the 0.9 release of wine and I haven't found this sort of approach necessary. This however, would be handy if you are still experiencing difficulty getting dvd shrink to recognise your dvd drive.

---

### Post by utterlyjaded on 2005-11-20
I think I may have an answer to why it won't recignise the dvd drive in dvdshrink.  First I tried to slove it by going to the advanced options in the winecfg GUI and selecting cd-rom, but it still would not find the drive in dvdshrink.  I figured that you need to maunally enter in the cd-rom location in the path.  
The path i have is /media/cdrom
After I put that in it found it and i am ripping as we speak :smile:

---

### Post by ackattack on 2005-11-22
I've had no problems using DVD Shrink under wine.  It detects the disk without problem.  I don't find it necessary to save as an .iso, I just save as VIDEO_TS and AUDIO_TS folders, then change to the saved directory and run
```

growisofs -dvd-compat -Z /dev/hdd -dvd-video .
```

you need to have the dvdrw tools installed.

---

### Post by aethiolas on 2005-11-23
I managed to get the entire setup up and working perfect at one point.  Had gorgeous previews and everything it was wonderful.  Then I decided to reformat my box(b/c I was trying something else, not related to this).  Now I can't even get it to open ANYTHING.  When I go in and set the drives and click apply, then ok, nothing gets saved!  The application is gone when I add it and the drive is gone!  Tried apt-get remove wine and reinstall but same issue.  Anyone got any ideas?

---

### Post by remick182 on 2005-11-23
[QUOTE=bionnaki]dvddecrypter still is not detected my drives...

when I select "cdrom" in advanced, I will click apply & then ok.
but this setting is not saved when I open winecfg again & check.[/QUOTE]

I'm having the same issue.  I went into winecfg and manually changed my dvd rw to "cd rom", but once I run DVD Decrypter, it fails on an error stating,
[COLOR="Red"]E 20:48:41 DeviceIoControl(IOCTL_STORAGE_QUERY_PROPERTY) Failed! - Device: '\\.\F:'
E 20:48:41 Reason: Invalid parameter[/COLOR]
but it recognizes my cd rw.  Then, it reverts the location of my dvd rw back to "local hard drive".

I am using WinNT 4.0 as the OS, and DVD Shrink works great.  Is there any other way to burn dvd's w/o encoding them?  Or is there another program that can decode them upon burning them?

---

### Post by manicka on 2005-11-24
[QUOTE=utterlyjaded]I think I may have an answer to why it won't recignise the dvd drive in dvdshrink.  First I tried to slove it by going to the advanced options in the winecfg GUI and selecting cd-rom, but it still would not find the drive in dvdshrink.  I figured that you need to maunally enter in the cd-rom location in the path.  
The path i have is /media/cdrom
After I put that in it found it and i am ripping as we speak :smile:[/QUOTE]

I have also found that using the current version of winetools (0.90) to create the base setup can solve this problem as well. Method has been added to the how-to at post 1.

---

### Post by shewbox on 2005-12-02
I have DVD Srink and Wine installed, but I'm getting this problem when trying to open discs:

Whenever I try to open a DVD, I get a box that says DVD Shrink cannot open the disc unless I set a region.  Even if I select a region, I get an error message that says: Copy Protection Error, Not Ready.  Clicking open DVD again, brings me to the region select window again, regardless of selecting a region before.

---

### Post by mravljica on 2005-12-27
Hmmm, I have read entire topic but still I can't get dvddecrypter to find my dvd drive. I have the following error:
--------------------
I 23:47:53 DVD Decrypter Version 3.5.4.0 started!
I 23:47:53 Microsoft Windows NT Workstation 4.0 (4.0, Build 1381 : Service Pack 6a)
I 23:47:53 Initialising SPTI...
I 23:47:54 Searching for SCSI / ATAPI devices...
E 23:47:54 DeviceIoControl(IOCTL_STORAGE_QUERY_PROPERTY) Failed! - Device: '\\.\D:'
E 23:47:54 Reason: Invalid parameter
W 23:47:57 No devices detected!
-------------------

BTW, DVD Shrink works without any problems.

What am I missing here?

Regards,
Sasa

---

### Post by manicka on 2005-12-29
[QUOTE=mravljica]Hmmm, I have read entire topic but still I can't get dvddecrypter to find my dvd drive. I have the following error:
[/QUOTE]

I have the same error, but I find dvddecrypter an unnecessary program as dvdbackup combined with other native linux programs do a better job.

---

### Post by NCLife on 2005-12-31
mmh, while trying to dl wine, this message came..

Err [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ wine 0.9.4-winehq-1
  Error reading from server. Remote end closed connection
Failed to fetch [http://wine.sourceforge.net/apt/binary/wine_0.9.4-winehq-1_i386.deb](http://wine.sourceforge.net/apt/binary/wine_0.9.4-winehq-1_i386.deb)  Error reading from server. Remote end closed connection
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
 
 am i doing something wrong?

---

### Post by PapaWiskas on 2006-01-01
I got a question....in Windows DVDShrink would give an code of some sort in the Decryption status area....but in Linux it says the disc I have in is "Not Encrypted" during the intial scan of the disc in dvdshrink.
Is this normal....I dont want to waste doing a disc if it is not truly decrypting it....I am used to it saying that it is.
Can anyone confirm what I should be seeing when running this program.  
Also when I go to the ReAuthor....I cant see anything under compression settings,....and even during the default entire disc area...it lists the sound files as 43 MB in size....its like the displays are all messed up or something....I am not used to it behaving this way...
Because if I can get this to work....I will NEVER EVER RETURN TO THE REALM OF MICRO#@@!....

Thank you.

---

### Post by manicka on 2006-01-01
[QUOTE=NCLife]mmh, while trying to dl wine, this message came..

Err [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ wine 0.9.4-winehq-1
  Error reading from server. Remote end closed connection
Failed to fetch [http://wine.sourceforge.net/apt/binary/wine_0.9.4-winehq-1_i386.deb](http://wine.sourceforge.net/apt/binary/wine_0.9.4-winehq-1_i386.deb)  Error reading from server. Remote end closed connection
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
 
 am i doing something wrong?[/QUOTE]

the WineHQ repo is a bit flakey at times. Just keep trying, eventually it will get the whole thing and install it

---

### Post by manicka on 2006-01-01
[QUOTE=PapaWiskas]
Can anyone confirm what I should be seeing when running this program.  
Also when I go to the ReAuthor....I cant see anything under compression settings,....and even during the default entire disc area...it lists the sound files as 43 MB in size....its like the displays are all messed up or something....I am not used to it behaving this way...
Because if I can get this to work....I will NEVER EVER RETURN TO THE REALM OF MICRO#@@!....

Thank you.[/QUOTE]

hmm, I've never seen that happen before. I think you'll find that the discs are decrypted just like in windows. It is after all a windows program and should do the job exactly the same way.

---

### Post by buildid on 2006-01-01
have tested xdvdshrink , it works wel for me ......subs are not working well unfortunatly

---

### Post by marty922 on 2006-01-05
I've managed to get DVDShrink running.  However, it seems to be taking ages to decode a DVD ~90mins.  In Windows, it would average about 30 mins.

Does anyone have any ideas?

Cheers,

Marty

---

### Post by superm1 on 2006-01-05
[QUOTE=marty922]I've managed to get DVDShrink running.  However, it seems to be taking ages to decode a DVD ~90mins.  In Windows, it would average about 30 mins.

Does anyone have any ideas?

Cheers,

Marty[/QUOTE]
Did you rip to HD prior to doing the decoding in DVD srhink?

---

### Post by marty922 on 2006-01-05
[QUOTE=superm1]Did you rip to HD prior to doing the decoding in DVD srhink?[/QUOTE]

No, I decoded from the drive as I used to do in Windows.  

I've read somewhere about enabling DMA on cd/dvd drives.  Is this likely to help, or should I just rip to HD first?  If so, can you point me in the right direction for ripping a DVD to HD?

Cheers,

Marty

---

### Post by marty922 on 2006-01-05
[QUOTE=marty922]No, I decoded from the drive as I used to do in Windows.  

I've read somewhere about enabling DMA on cd/dvd drives.  Is this likely to help, or should I just rip to HD first? [/QUOTE]

It's probably poor form to answer your own question, but if anyone else is having a similar problem...

I've set the DMA for ROM and writer and all is well.. back to 30 mins for shrinking.

Cheers,

Marty

---

### Post by jeepmanjr on 2006-01-06
I've tried DVDShrink on several distros using either wine or CrossOver Pro.  They've all been pretty hit or miss.  You have to make sure you have ALL of the supporting plugins installed or you'll be banging your head against the wall in no time.

I had DVDShrink installed in Breezy using CrossOver and it fired up and recognized my drives.  It would start encoding at respectible speeds, then gradually slow down to a crawl.  I spent way too much time on it and eventually uninstalled.  I need to take a look at some alternatives.  Besides, installing a 32-bit program on Linux kinda defeats the whole purpose of the thing doesn't it?  ;) 

:cool:  Mike

---

### Post by regeya on 2006-01-15
[QUOTE=awtomlinson]i understand, but this kind of defeats the purpose of dvdshrink.  i need it to be my one stop dvd shrinking/ripping application.  this worked like a charm in warty and hoary, and people have gotten it to work in breezy.  how can i make dvdshrink, or wine for that matter, detect my dvd and/or cd drives?  again, the drives appear when using winecfg.[/QUOTE]

I honestly don't mean to be disrespectful, but I call B.S.  I had enough trouble figuring out what to do in the Warty days (but then again, I'm not the brightest bulb in the box) that I wrote a HOWTO on the subject.  I was also warned on this very forum to not write HOWTOs about Windows and/or non-Free software, but that's another story.  I find it hard to believe that anyone installed it out of the box without checking their Wine config and got it working, Nero plugin and all.

There's another comment in this thread above yours that outlines a foolproof method that I've been using since Warty.  It works well.  It's not a one-stop shop, but it works and works nearly flawlessly.  It must be said that DVDShrink is a Windows program, and, as such, runs best on Windows.

---

### Post by Thanatos10 on 2006-01-16
When trying to install DVDShrink I get the error:
Setup was unable to create the directory "C:\windows\temp\is-F225E.tmp"
Error 5: Access denied  

What am I doing wrong?  I'd really like to get DVDShrink working as it works great for me in windows.

Thanks for any help.

---

### Post by Dr Gonzo on 2006-01-16
[QUOTE=Thanatos10]When trying to install DVDShrink I get the error:
Setup was unable to create the directory "C:\windows\temp\is-F225E.tmp"
Error 5: Access denied  

What am I doing wrong?  I'd really like to get DVDShrink working as it works great for me in windows.

Thanks for any help.[/QUOTE]
I'd guess you configured wine as root.  Try ```
sudo chown -R <yourusername>:users /home/<yourusername>/.wine
```

---

### Post by Thanatos10 on 2006-01-16
Thanks Dr. Gonzo, that did the trick.  Wish I knew more about permissions and chown.

---

### Post by Neo40 on 2006-01-21
Hi,

I got a strange problem and I think it is with Ubuntu. Well, I did a backup with dvd shrink and burned the movie. I can watch the movie on my home system video just fine. But if I put the dvd on my pc, I get a message saying:

Totem could not play 'file:///dev/hdd'
There is no plugin to handle this movie.

And if I put the original dvd then totem will work!
I also tried to use gxine instead totem and won't help. Gxine gives me this error message:

xine engine failed to start.
No demuxer found - stream format not recognised.

Anyone can help me?
Thanks!

---

### Post by Kieffer87 on 2006-01-21
[QUOTE=awtomlinson]i have the solution to dvdshrink not recognizing my dvd or cd drives.  in winecfg, even though the drive mapping will appear, you must select the drive, then click Show Advanced.  Then, under Type, ensure it is set to CD-ROM.  even though winecfg mapped the drive as /media/cdrom0, its type was defaulted to local hard drive.  everything works great now.[/QUOTE]
Thank You Very much!

---

### Post by ianmacgregor on 2006-10-29
> **bionnaki said:**
> dvdbackup works great.

Yes, it does, but dvdbackup doesn't shrink a DVD9 to fit on a DVD5 disk.

---

### Post by nikopol on 2006-11-04
DVDshrink is amazingly slow under Wine (with DMA on) but runs really fast under Windows (24 hour vs. 20 mins). I'm not sure if it's an issue with DVDshrink or Wine though. How would I go about finding a solution to this problem. 

I know there are other alternatives under Linux which I do use but for some reason k9copy doesn't seem to make DVDs that are as universally playable as DVDshrink does.

---

### Post by hamil on 2007-04-21
Hello guys,

I have succesfully compiled WINE from source, as there is some faults with the prepacked deb for Ubuntu. WINE was installed with:
CFLAGS=-fno-stack-protector ./configure
So now I do have working 0.9.35 installed on my machine. I am able to run all my other applications, but DVD shrink is giving me some headaches...

It was installed together with DVD decrypter, as suggested in this thread, but when I do try to start DVD shrink, I am flooded with error-messages:
```

fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
err:ole:CoGetClassObject class {07b65360-c445-11ce-afde-00aa006c14f4} not registered
err:ole:CoGetClassObject no class object {07b65360-c445-11ce-afde-00aa006c14f4} could be created for context 0x1
err:quartz:GraphBuilder_Connect Unable to create filter (80040154), trying next one
err:ole:CoGetClassObject class {e30629d1-27e5-11ce-875d-00608cb78066} not registered
err:ole:CoGetClassObject no class object {e30629d1-27e5-11ce-875d-00608cb78066} could be created for context 0x1
err:quartz:GraphBuilder_Connect Unable to create filter (80040154), trying next one

```

Until it ends in a seg fault
```
err:seh:setup_exception stack overflow 4 bytes in thread 0009 eip b7da1949 esp 00230ffc stack 0x231000-0x340000
Segmentation fault (core dumped)
```

At first I did belive that it could be something wrong with the setup file I tested, but I have now installed DVD shrink with setup files from multiple locations. As an last try, I also installed winetools, to see if I was able to get it to work with their automated installation, but DVD shrink was removed from winetools aalso ....

Ideas to what is happening, and why?

---

### Post by discmaster on 2007-05-31
Hi hamil,

That is pretty much the result I am getting with shrink as well. Have you made any progress?

---

