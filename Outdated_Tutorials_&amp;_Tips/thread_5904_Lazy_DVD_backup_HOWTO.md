---
title: "Lazy DVD backup HOWTO"
date: 2004-11-23
forum: Outdated Tutorials &amp; Tips
---

### Post by regeya on 2004-11-23
This HOWTO was inspired by this link:  [http://www.gurtlush.org.uk/article.php?story=20040522135306118](http://www.gurtlush.org.uk/article.php?story=20040522135306118) 

I have a couple of DVDs that have started going bad already.  You know, the infamous problem of cheaply mass-produced DVDs to meet the demand, blah blah blah.  I'm not about to give these studios **more** money when chances are the new disks will be just as cheap, and my DVD-ROM drive seems to be able to read the discs just fine.  

As a U.S. citizen I'm legally allowed to make one backup.  Check your local laws before doing this.

Also, as this is the **lazy** howto, the easiest (actually, the only method that worked well for me) was DVD Shrink, hence the Wine and WinesetupTK requirements.  While I get a dirty feeling running Win32 programs under Linux, for now it works fine and since I'm not having to run Windows, I don't feel nearly as bad about it as I might otherwise. :D   It's my intention to find a trouble-free way to backup menus, stills, etc. in a straightforward way, as soon as I know how.  At that time, I intend to update this HOWTO.

You'll need the following.  You need to install bleeding-edge versions of these programs, so beware--make sure you know how to add Hoary sources, and how to pin, before you even attempt this.  I've seen guides elsewhere, and can add info about my setup when I get home and get a look at my setup.  Also, I'm assuming familiarity with Wine and DVDShrink.  Finally, I'm assuming NTSC.  Here's the software:

[list]
[*]dvdbackup
[*]wine and winesetuptk
[*]DVD Shrink (Windows program, sorry)
[*]k3b
[/list] 

Here's what you need to do.
[list=1]
[*]Create a directory to back up your DVD to.
[*]Run: dvdbackup -M -i/path/to/dvd/drive -o/path/to/folder
[*]run: wine /path/to/dvdshrink/executable.exe z:/path/to/folder/here/VIDEO_TS.IFO
[*]Choose your settings carefully.  There are a number of guides around.
[*]Open the folder you chose as the destination directory, and find the VIDEO_TS folder.  Example:  If you chose to save the DIME_NTSC folder to C:\ then the DIME_NTSC folder will be in ~/.wine/fake_windows (assuming you haven't changed your default Wine settings.)
[*]Start k3b
[*]Start a new Video DVD project
[*]Double-click on the VIDEO_TS folder on k3b
[*]Drag the files from the VIDEO_TS folder to k3b
[*]Put in a blank and click the Burn button :D
[/list]

---

### Post by jdodson on 2004-11-23
please dont post howtos with windows software as a prerequisite.  finding gnu/linux alternatives is part of the process of becoming free.  plus this is not a windows forum, it is a ubuntu forum.

---

### Post by regeya on 2004-11-23
[QUOTE=jdodson]please dont post howtos with windows software as a prerequisite.  finding gnu/linux alternatives is part of the process of becoming free.  plus this is not a windows forum, it is a ubuntu forum.[/QUOTE]

We're all in this together, eh?

I'll agree that it's preferable to use Free Software to closed-source, though as I pointed out in the Subject line this is the *Lazy* DVD Backup HOWTO.   :smile:   If you'll notice, I used Wine, and I'll point out that Wine is in the Universe repository.  Unless you'd like to claim that Universe isn't part of Ubuntu, I'll kindly thank you to not accuse me of being completely off-topic.  WINE is not Windows (and also, as the acronym implies, WINE Is Not and Emulator :D); it is merely a Free implementation of Windows that we keep around to run disagreeable non-Free software on.

Not all the world is Free.  Should I quit my job because they won't use Scribus and The GIMP in place of QuarkXPress and Photoshop?  The idealist in me thinks yes, but the realist in me realizes that I'd be hard-pressed (sadly, I agree) to find a job where I don't run into proprietary software that I'm forced to use.

DVD Shrink just happened to be a Free Beer solution that'd run under Linux nicely and popped out a beautiful set of VOBs ready to burn via k3b.  At some point I hope to write a Python script to automate the Free Software tools that're available.  If something already exists to pull data out of a 9.8MB DVD data set, features, stills, menus and all, and can shrink everything down in a reasonable time, someone let me know and I'll not bother investigating this avenue.  Everything I've found is poorly documented (and where it is documented, tends to be documented in German, which I find difficult to read) and tends to be out of sync with the current set of tools.

As soon as I find a nice, straightforward, reliable backup plan that doesn't involve non-Free software, I'll post my results.  Again, sorry for offending you, but please, let's keep a little perspective.  I used a Free Beer Windows progam running on top of WINE for one stage.  That doesn't constitute covering a Windows-only solution, in my mind, especially since I also used dvdbackup to dump the image to harddrive and k3b to burn the resulting image to DVD-R!  [-X

BTW, I'll be adding this link to the parent post, since it supplied most the information: [http://www.gurtlush.org.uk/article.php?story=20040522135306118](http://www.gurtlush.org.uk/article.php?story=20040522135306118)

---

### Post by khad on 2004-11-23
Indeed. In fact, I just got off the phone with a friend to whom I was lamenting my dual-boot situation. I believe my exact words were: "I wish that someone would come up with something like DVD Shrink for Linux so I could be rid of Windows."

Now I have one more reason to not go back. I think that makes a strong case for leaving this post (and others like it) on display.

Sure, it seems a bit more like a hack than a solution. But I would rather use a hack in Linux than a solution in Windows. If it weren't for reading regeya's post, I would have one more reason to stay tethered to Windows. Here's to cutting the cord!

khad

---

### Post by jdodson on 2004-11-24
> **regeya]We're all in this together, eh?

I'll agree that it's preferable to use Free Software to closed-source, though as I pointed out in the Subject line this is the *Lazy* DVD Backup HOWTO.   :smile:   If you'll notice, I used Wine, and I'll point out that Wine is in the Universe repository.  Unless you'd like to claim that Universe isn't part of Ubuntu, I'll kindly thank you to not accuse me of being completely off-topic.  WINE is not Windows (and also, as the acronym implies, WINE Is Not and Emulator :D) said:**
> http://www.gurtlush.org.uk/article.php?story=20040522135306118[/URL]

no offense taken.  i understand that in the current state of the software world somethings cannot be done with free software.  however, there are plenty of alternatives to dvd shrink available in the community, i only have a minute or two until i have to logout, when i return i will post on them.

---

### Post by regeya on 2004-11-24
[QUOTE=jdodson]no offense taken.  i understand that in the current state of the software world somethings cannot be done with free software.  however, there are plenty of alternatives to dvd shrink available in the community, i only have a minute or two until i have to logout, when i return i will post on them.[/QUOTE]

That's lovely.  Thank you.  I've been looking around, but everything I find a.) only grabs one title and either a.) just re-quantizes or b.) spends a couple of days using mpeg2enc.  lxdvdrip apparently is a lovely solution but by golly I just couldn't get it to do anything but barf error messages.   :cry: 

Thanks again, jdodson.

---

### Post by jdodson on 2004-11-24
[QUOTE=regeya]That's lovely.  Thank you.  I've been looking around, but everything I find a.) only grabs one title and either a.) just re-quantizes or b.) spends a couple of days using mpeg2enc.  lxdvdrip apparently is a lovely solution but by golly I just couldn't get it to do anything but barf error messages.   :cry: 

Thanks again, jdodson.[/QUOTE]


cool, i was having some of those problems as well, however i found a program that could snag the DVD and then change it into whatever format you wish.  the name of the program is dvd::rip and the link is here: [http://www.exit1.org/dvdrip/](http://www.exit1.org/dvdrip/)  

hopefully that wasnt one of the programs that gave you troubles.  dvd rip is available from the mallriat repositories.  i really hope that helps.

---

### Post by zenwhen on 2004-11-24
I use DVDshrink as well with vobcopy to rip the DVD.

For me, dvd::rip never wanted to make the needed MPEG2 vobs. I'll switch to something free (as in speech) for this task when something free does the job better.

If someone would care to prove me wrong and post an actual HOWTO that does not involve Windows software  and lets me back up DVD's to my DVD+R's, I would be happy as can be.

---

### Post by jdodson on 2004-11-25
what about using something like ff2mpeg?

---

### Post by regeya on 2004-11-27
[QUOTE=jdodson]what about using something like ff2mpeg?[/QUOTE]

Or here's a question: has anyone tried ripping a DVD (via dvdbackup), dumping the data from the VOB files, requantizing/re-encoding, rebuilding the VOBs, and using those in place of the original VOBs?  Would it work, or do you need new .BUP and .IFO files?

Also, does anyone know if ffmpeg can do 2-pass VBR DVD-friendly MPEG2 streams?

---

### Post by jdodson on 2004-11-29
[QUOTE=regeya]Also, does anyone know if ffmpeg can do 2-pass VBR DVD-friendly MPEG2 streams?[/QUOTE]

ffmpeg has this functionality, check the site for more info:

[http://ffmpeg.sourceforge.net/index.php](http://ffmpeg.sourceforge.net/index.php)

---

### Post by wallijonn on 2005-01-15
regeya,

DVDShrink doesn't detect the DVDdrive, while burn:/// and k3b do. Is there anything I should know?


jdodson,

dvdrip has a libvorbis0 conflict with k3b even after I installed libvorbis0-compat_1.orc3-0woody3_i386.deb

Do you have dvdrip & k3b installed?

---

### Post by NoIBnds on 2005-05-22
How about an ALL LINUX Solution to  the DVD Copy problem: It is available and easier then all the other steps for the Wnblows DVDShrink & Wine,  and pretty quick also. Thanks to OZZZY. I found this and it works on my machine with MEPIS 3.3.1 


[http://ozzzy.dhis.org/index.php?DVDShrink](http://ozzzy.dhis.org/index.php?DVDShrink)

Make sure the below items are on your system-- all obtainable from Synaptic--(with Mepis)
Needed:
Transcode
DVDAuthor
MJPegTools
SubTitleRipper
Gocr
DVD+RW_Tools
Mkisofs
LibGtk2-Perl

 AND Most Important OZZZY's DVDShrink – From the link below: 

[http://prdownloads.sourceforge.net/dvdshrink/dvdshrink-2.6.0.pre5-1mdk.tar.gz?download](http://prdownloads.sourceforge.net/dvdshrink/dvdshrink-2.6.0.pre5-1mdk.tar.gz?download)

The Directions are for Mepis but can be adjusted to fit UBUNTU, I am not that good in UBUNTU (Yet) but thought you might try this program.

 Save the downloaded tar file to a folder, then Extract it (untar it) then from the Console - CD into the folder that contains the INSTALL.SH of the extracted file. Then ./install.sh when it is all done!!
 Create 2 folders in your Home Folder 1 called DVDBase and 1 called DVDISO.(or whatever YOU want to name them)
 Open the Menu Editor and create a new menu item under Multimedia (or wherever you want) and as the command to start the program “/usr/bin/xdvdshrink.pl” (without the Quotes). The DVDShrink program will open and then you need to configure it.
  Press the configure button and change the Reader Device to your DVD Reader (Mine is /dev/cdrom1) then the burner device (mine is /dev/cdrom). Then point the base working directory to the  base folder you made /home/dvdbase, then the ISO folder /home/dvdiso. Enter the Konsole you  want to use, and the DVD Burner speed. Check whatever boxes are appropriate for you. The hit save!!
   Put your DVD Movie in your Reader and a Blank DVD+R in the DVDWriter I set it to Autoburn—Shrink—and Delete Working files-- Hit the get from DVD to get Title-Video and Audio streams-- The HIT THE START COPY Button. It will rip—shrink and BURN all from LINUX (without any WINE or any K3B). When you are done you have an “Archival” Copy of your movie.

---

### Post by dolson on 2005-06-15
[QUOTE=NoIBnds]How about an ALL LINUX Solution to  the DVD Copy problem: It is available and easier then all the other steps for the Wnblows DVDShrink & Wine,  and pretty quick also. Thanks to OZZZY. I found this and it works on my machine with MEPIS 3.3.1 


[http://ozzzy.dhis.org/index.php?DVDShrink](http://ozzzy.dhis.org/index.php?DVDShrink)

Make sure the below items are on your system-- all obtainable from Synaptic--(with Mepis)
Needed:
Transcode
DVDAuthor
MJPegTools
SubTitleRipper
Gocr
DVD+RW_Tools
Mkisofs
LibGtk2-Perl

 AND Most Important OZZZY's DVDShrink – From the link below: 

[http://prdownloads.sourceforge.net/dvdshrink/dvdshrink-2.6.0.pre5-1mdk.tar.gz?download](http://prdownloads.sourceforge.net/dvdshrink/dvdshrink-2.6.0.pre5-1mdk.tar.gz?download)

The Directions are for Mepis but can be adjusted to fit UBUNTU, I am not that good in UBUNTU (Yet) but thought you might try this program.

 Save the downloaded tar file to a folder, then Extract it (untar it) then from the Console - CD into the folder that contains the INSTALL.SH of the extracted file. Then ./install.sh when it is all done!!
 Create 2 folders in your Home Folder 1 called DVDBase and 1 called DVDISO.(or whatever YOU want to name them)
 Open the Menu Editor and create a new menu item under Multimedia (or wherever you want) and as the command to start the program “/usr/bin/xdvdshrink.pl” (without the Quotes). The DVDShrink program will open and then you need to configure it.
  Press the configure button and change the Reader Device to your DVD Reader (Mine is /dev/cdrom1) then the burner device (mine is /dev/cdrom). Then point the base working directory to the  base folder you made /home/dvdbase, then the ISO folder /home/dvdiso. Enter the Konsole you  want to use, and the DVD Burner speed. Check whatever boxes are appropriate for you. The hit save!!
   Put your DVD Movie in your Reader and a Blank DVD+R in the DVDWriter I set it to Autoburn—Shrink—and Delete Working files-- Hit the get from DVD to get Title-Video and Audio streams-- The HIT THE START COPY Button. It will rip—shrink and BURN all from LINUX (without any WINE or any K3B). When you are done you have an “Archival” Copy of your movie.[/QUOTE]


This doesn't actually copy everything on the DVD. DVDShrink for Windows does. As much as I hate to have to install Wine, I think there are no other options at this time. Well, I could dual boot, but then I'm going to need a Windows license.

---

### Post by szatyor on 2005-11-28
I've installed DVDshrink according to this post, but try&#237;ng to backup my dvd I get this message:
[B]/usr/bin
/usr/bin/dvdsfunctions: line 1141: syntax error near unexpected token `then'
/usr/bin/dvdsfunctions: line 1141: `   while [ $ATEST -gt 0 ]; then'
Message:[/B]

What shuol I do, or can I uninstall the program?

---

### Post by reedlaw on 2005-11-28
I would like to backup my DVDs to hard disk using a high-quality compression format.  I am thinking of using Ogg/Theora compression via Thoggen.  Does anyone that has any experience with this like to comment on the quality, or give any pointers?  Thoggen lets you choose between a fixed size (eg the size of a CD) or a quality setting.  The default quality is 16, but it goes up to 63.  If no one responds I will do some tests myself and get back with the results.  I would also like to see this method compared with DVD Shrink.

---

### Post by johnswb on 2008-06-09
> **szatyor said:**
> I've installed DVDshrink according to this post, but tryíng to backup my dvd I get this message:
[B]/usr/bin
/usr/bin/dvdsfunctions: line 1141: syntax error near unexpected token `then'
/usr/bin/dvdsfunctions: line 1141: `   while [ $ATEST -gt 0 ]; then'
Message:[/B]

What shuol I do, or can I uninstall the program?

I was getting the same thing until I installed version 2.6.1 [xDVDSHrink]("http://downloads.sourceforge.net/dvdshrink/dvdshrink-2.6.1-10mdk.tar.gz?modtime=1178280240&big_mirror=0"). After that it seems to be working.  I can't give a 100% as of yet seeing that I am replying to this during my first try.  I will post my results once it is complete.

---

### Post by johnswb on 2008-06-09
grrrr here are my results

________________________________________________________

   DVDShrink 2.6.1 - May 04, 2007
   Rick Saunders (ozzzy1@gmail.com)
________________________________________________________

   INFORMATION

   Project:                                  MOVIE
   File cleanup?                             No
   Auto-burn?                                No, ISO only.
   Save ISO with burn?                       No
   DVD Title:                                2
   Audio channel:                            0
   Subtitle channel:                         None

   PROGRESS   Rip started at 21:13:06

   DVDSHrink Function                        Status    Elapsed

   Reading the chapter list                  Done!    [00:00:00]
   Ripping Title                             Working!Error!
tcextract: no process killed

   DVDShrink has failed!
   Error:
      -> tccat reported an error copying title!
   Command run:
      -> nice -n +19 tccat -i /dev/cdrom1 -T 2,-1 -L 2> /home/DvDBase/MOVIE/tccatdebug.txt | tee /tmp/videofifo /tmp/audiofifo >/dev/null 2> /dev/null

   Check all your files etc. If it appears that the problem is
   ephemeral restart the script with 'dvdshrink --restart'

   End of command output
   ---------------------------------------

Read failed for block 533019
Read failed for block 603792
Read failed for 188 blocks at 1048487
Read failed for 114 blocks at 1187973
Read failed for block 1270689

---

### Post by chaanakya_chiraag on 2010-04-01
I just use dd like so:
```
dd if=/dev/dvd of=/home/chaanakya/video.iso
```
seems to work on a DVD Thoggen failed to rip.

---

