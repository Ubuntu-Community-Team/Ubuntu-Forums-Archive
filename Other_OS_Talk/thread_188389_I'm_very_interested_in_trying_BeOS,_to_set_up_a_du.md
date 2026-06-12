---
title: "I'm very interested in trying BeOS, to set up a dual boot to my Ubuntu or XPsp2 box.."
date: 2006-06-04
forum: Other OS Talk
---

### Post by RAV TUX on 2006-06-04
I want to try BeOS, and I need a little help since they don't have an ISO.

Here is the download page for BeOS [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]Developer edition

[http://www.beosonline.com/?page=download]("http://www.beosonline.com/?page=download")

Here is detailed instruction on how to burn the developer OS

[http://www.beosonline.com/?page=open_docs&nr=3]("http://www.beosonline.com/?page=open_docs&nr=3")

I downloaded both the boot image and main image and merged the two zip files by dragging and dropping but I have know idea how to make this a burnable image...

I am using WinZip on XPsp2 since I don't have a burner on my Ubuntu 6.06 box.

___________________________________________

Here are detailed how to's:

[/SIZE][/FONT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][**Support**]("http://www.beosonline.com/?page=support") > **Guides & Documentation**[/SIZE][/FONT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]**How to burn the Developer Edition with 2 Tracks on Windows or BeOS**[/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]Information: 

BeOS Developer Edition Zip (please decompress the zip files before you like to burn) The images are created with 2048 Bytes per Sector. 

Boot Image 
For all cpus (Athlon XP, Pentium 4, VIA usw.)  
Datei: deved_1_1_boot.img.zip Gr&#31204;e: 675.723 Bytes 
unpacked: deved_1_1_floppy.img 

Main Image 
For all cpus (Athlon XP, Pentium 4, VIA usw.)  
Datei: deved_1_1_main.img.zip Gr&#31204;e: 197.741.422 Bytes 
unpacked: image.be 

CueSheet: 

We have made cuesheet for the Developer Edition so up now you can use this for burnig cd with CDRWIN, FireBurner or Nero Burning Rom (new builds include cuesheet support) under windows. We tested it with CDRWIN 4.0a: 

FILE "deved_1_1_floppy.img" BINARY 
  TRACK 01 MODE1/2048 
    INDEX 01 00:00:00 
    POSTGAP 00:02:00 
FILE "image.be" BINARY 
  TRACK 02 MODE1/2048 
    INDEX 01 00:00:00 
    POSTGAP 00:02:00 

**With BeOS:** 

The Develop Edition consists two files, the "Boot Image" (it is not a Bootdisk-Image!) and the "Main Image". Both images must be burned on the CD (2 tracks). Open your CDBurner and add every Images in order "Boot" than "Main" with "Add Data Track" and klick to burn. Thats all. 
Already you have a boot CD with the new Release! Here the steps: 

To create a BOOTABLE BeOS CD from within BeOS: 

1. Get BeOS 5 Developer Edition from one of these mirrors if you didn't do that yet. Mirror 1 etc 
2. Extract deved_1_1_boot.img.zip and deved_1_1_main.img.zip to the samefolder. 
3. Fire up CDBurner. Make sure your CD-R drive is selected in the drop-down box at bottom-left. 
5. From the "Disc" menu, choose "Add Data Track" and select the file "deved_1_1_floppy.img". 
6. From the "Disc" menu, choose "Add Data Track" again and select the file "image.be". 
7. Click "Burn Now". 

The CD is now bootable! If CDBurner keeps failing on you, try Melt. It's available from Bebits. 
Remember, you need to set your BIOS to boot from CD-ROM before the CD will actually boot. 

NOTE: 
Some older CDrom readers can't read 700 MB CD-R's properly so you might encounter problems with that, just to be on the safe side and for compability reasons use a 650 MB CD-R 

**With Windows:** 

Look also the URL: [http://504.gravity24hr.com/]("http://504.gravity24hr.com/") 

WinOnCD:  

1. Open WinOnCD 
2. Under the column labeled "other" select TRACK-image.  
3. Doubleclick on TRACK-image 
4. In the new window press browse. 
5. Select the BeOS boot image. You also must change the file type to "all files". Otherwise, you will not see the files in the window. 
6. Click OK once (there are still some remaining adjustments to be made). 
7. Select Project from the main menu, then --> object to insert. 
8. Again, select TRACK image, and choose to insert it afterthe first image. 
9. Repeat as with the previous image: Doubleclick on TRACK image - - > browse. 
10. Select the Main BeOS image and click OK once. 
11. Finally, click on CD (Button at the bottom left hand corner) and on then on writing. The CD should be locked, not multi-session. 

Nero CD Burn:  

1. Save the CueSheet provided above and rename the file as deved.cue The cuesheet will attempt to burn the image "deved_1_1_floppy.img" and "image.be" 
2. The CueSheet must be saved in the same location as the 2 images 
3. Under Nero Burning Rom, select File -> Burn Image 
4. Open the deved_10.cue file 
5. In the new window, make sure to select "Disc-At-Once" as the Write Method 
6. Click on Write Button to start the burn process 

**Linux/Unix** 

cdrecord  

The command with multisession: 
cdrecord -v speed=4 dev=0,4,0 -multi deved_1_1_floppy.img 
on dev and speed use your own settings. Now put the CD in the burner and burn the second image with the command: 
cdrecord -v speed=4 dev=0,4,0 image.be 

Without multisession: 
cdrecord dev=0,1,0 speed=4 -eject -v -data deved_1_1_floppy.img image.be  

**Mac** 

Toast 4.2 
1. Select format "Disk Image" 
2. Click on the DATA Button, then find and select the "boot image". 
3. Finally, repeat the previous step, and select the "main image". 
4. Select burn with the following settings: pregap 0, postgap 0, sector size 2048 
5. Burn the cd, and you're finished. 

**Thanks to:** 

Adrian Sanabria (adrian@afsthumper.com) 
Goro TechBG (goro@techbg.com) 
John Eckert (johnboy@gmx.de) 
Wolfgang Oblasser (wolfgang@wasser.stc.obl.at) 
Firehawk (firehawk0000@web.de)  
Ted (Ted@3rd-rock.net) 
and all helped user [IMG]http://www.beosonline.com/images/smilies/smile1.gif[/IMG][/SIZE][/FONT]



_____________________________________________________



also check out the open source project of BeOS



Haiku



[http://haiku-os.org/learn.php]("http://haiku-os.org/learn.php")



_____________________________________________________

Thanks in advance.












.

---

### Post by RAV TUX on 2006-06-04
I am highly tempted to just buy Zeta 1.2.

but I wish I could try it out first.

does anybody here have experience with Zeta?

[http://www.yellowtab.com/](http://www.yellowtab.com/)

---

### Post by RAV TUX on 2006-06-04
[quote=yozef]I am highly tempted to just buy Zeta 1.2.

but I wish I could try it out first.

does anybody here have experience with Zeta?

[http://www.yellowtab.com/]("http://www.yellowtab.com/")[/quote]

I spoke too soon Zeta 1.1 Live CD is available for free download:

[http://download.freenet.de/archiv_z/zeta_live-cd_7560.html](http://download.freenet.de/archiv_z/zeta_live-cd_7560.html)

(downloading now)

---

### Post by RAV TUX on 2006-06-04
[quote=yozef]I spoke too soon Zeta 1.1 Live CD is available for free download:

[http://download.freenet.de/archiv_z/zeta_live-cd_7560.html]("http://download.freenet.de/archiv_z/zeta_live-cd_7560.html")

(downloading now)[/quote]

Ok even though this is a zip file I figured out how to compress it and create an ISO image. I'm burning Zeta 1.1 Live CD now...:p

---

### Post by RAV TUX on 2006-06-04
> **yozef]I want to try BeOS, and I need a little help since they don't have an ISO.

Here is the download page for BeOS [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]Developer edition

[http://www.beosonline.com/?page=download]("http://www.beosonline.com/?page=download")

Here is detailed instruction on how to burn the developer OS

[http://www.beosonline.com/?page=open_docs&nr=3]("http://www.beosonline.com/?page=open_docs&nr=3")

I downloaded both the boot image and main image and merged the two zip files by dragging and dropping but I have know idea how to make this a burnable image...

I am using WinZip on XPsp2 since I don't have a burner on my Ubuntu 6.06 box.

___________________________________________

Here are detailed how to's:

[/SIZE][/FONT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][**Support**]("http://www.beosonline.com/?page=support") > **Guides & Documentation**[/SIZE][/FONT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]**How to burn the Developer Edition with 2 Tracks on Windows or BeOS**[/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]Information: 

BeOS Developer Edition Zip (please decompress the zip files before you like to burn) The images are created with 2048 Bytes per Sector. 

Boot Image 
For all cpus (Athlon XP, Pentium 4, VIA usw.)  
Datei: deved_1_1_boot.img.zip Gr&#31204 said:**
> http://504.gravity24hr.com/[/URL] 

WinOnCD:  

1. Open WinOnCD 
2. Under the column labeled "other" select TRACK-image.  
3. Doubleclick on TRACK-image 
4. In the new window press browse. 
5. Select the BeOS boot image. You also must change the file type to "all files". Otherwise, you will not see the files in the window. 
6. Click OK once (there are still some remaining adjustments to be made). 
7. Select Project from the main menu, then --> object to insert. 
8. Again, select TRACK image, and choose to insert it afterthe first image. 
9. Repeat as with the previous image: Doubleclick on TRACK image - - > browse. 
10. Select the Main BeOS image and click OK once. 
11. Finally, click on CD (Button at the bottom left hand corner) and on then on writing. The CD should be locked, not multi-session. 

Nero CD Burn:  

1. Save the CueSheet provided above and rename the file as deved.cue The cuesheet will attempt to burn the image "deved_1_1_floppy.img" and "image.be" 
2. The CueSheet must be saved in the same location as the 2 images 
3. Under Nero Burning Rom, select File -> Burn Image 
4. Open the deved_10.cue file 
5. In the new window, make sure to select "Disc-At-Once" as the Write Method 
6. Click on Write Button to start the burn process 

**Linux/Unix** 

cdrecord  

The command with multisession: 
cdrecord -v speed=4 dev=0,4,0 -multi deved_1_1_floppy.img 
on dev and speed use your own settings. Now put the CD in the burner and burn the second image with the command: 
cdrecord -v speed=4 dev=0,4,0 image.be 

Without multisession: 
cdrecord dev=0,1,0 speed=4 -eject -v -data deved_1_1_floppy.img image.be  

**Mac** 

Toast 4.2 
1. Select format "Disk Image" 
2. Click on the DATA Button, then find and select the "boot image". 
3. Finally, repeat the previous step, and select the "main image". 
4. Select burn with the following settings: pregap 0, postgap 0, sector size 2048 
5. Burn the cd, and you're finished. 

**Thanks to:** 

Adrian Sanabria (adrian@afsthumper.com) 
Goro TechBG (goro@techbg.com) 
John Eckert (johnboy@gmx.de) 
Wolfgang Oblasser (wolfgang@wasser.stc.obl.at) 
Firehawk (firehawk0000@web.de)  
Ted (Ted@3rd-rock.net) 
and all helped user [IMG]http://www.beosonline.com/images/smilies/smile1.gif[/IMG][/SIZE][/FONT]



_____________________________________________________



also check out the open source project of BeOS



Haiku



[http://haiku-os.org/learn.php]("http://haiku-os.org/learn.php")



_____________________________________________________

Thanks in advance.












. 
good news and bad news....the good news I figured out how to merge and compress BeOS Developer Edition to an ISO image and I have a hot out of the oven burned CD.

but I have to redownload Zeta 1.1 Live CD in learning how to do this whole process I think I made a mistake on that one....so I am redownloading and recompressing and reburning.



wish me luck...

---

### Post by Iandefor on 2006-06-04
Meh, BeOS is sort of fun, but it really isn't that great.

---

### Post by psychicdragon on 2006-06-04
6 years ago when I first saw the BeOS it blew my mind. I fooled around with it for quite a while and even used it as my main OS. GNU/linux wasn't usable at all back then.

Now, most of the feature that made the BeOS so great have found their way to other OSes and the apps feel old and hardware support is really lacking.

If you've never seen it though it's worth a download. Just pretend it's still the 90's and it will knock your socks off. :KS

---

### Post by PatrickMay16 on 2006-06-04
I tried to use BeOS back in 2003. Hardware support wasn't so good, and I couldn't find good replacements for applications I had been using in Windows (for some, none at all). You should certainly take a look at BeOS, but you probably won't find it very useful.

Also, these links might help:
[http://www.bebits.com/](http://www.bebits.com/)
[http://www.bebits.com/app/2680](http://www.bebits.com/app/2680)

---

### Post by RAV TUX on 2006-06-04
It's a lot of fun to check out other OS's, Other Linux Distros, BSD's, BeOS, etc. It's always good to know what is out there and where everybody is progressing.

It's all a part of being OS aware.

It's good to see what is conceptionally being worked on and what is consumer ready.

Ubuntu is leading the market in alternates to Windows and Apple.


It's good to be apart of this dynamic progression in technology.




.

---

### Post by init1 on 2007-08-08
> **RAV TUX said:**
> It's a lot of fun to check out other OS's, Other Linux Distros, BSD's, BeOS, etc. It's always good to know what is out there and where everybody is progressing.

It's all a part of being OS aware.

It's good to see what is conceptionally being worked on and what is consumer ready.

Ubuntu is leading the market in alternates to Windows and Apple.


It's good to be apart of this dynamic progression in technology.




.
Right. I haven't tried BeOS, but I do have the Haiku image.It runs fine in Qemu. Not much to do on it though.

---

### Post by kulturloseramerikaner on 2007-08-08
I have a developer buddy that had nothing but good things to say about it, especially the way it handles files, but the last time he saw it was about 6-7 years ago... Can't vouch for it now.

---

### Post by fistfullofroses on 2007-08-08
Personally, I have used the old school BeOS and Haiku. I prefer Haiku over the original. I tried Zeta once, and did not like it so much.

---

### Post by ezsit on 2007-08-10
Back in 1996 or 1997 I tried BeOS 4.5 and then 5.0. I was very impressed. The stability was great, the system booted in mere seconds, adding apps was super easy (just uncompress the file into the Programs folder), the speed was amazing (my P2 333Mhz just flew compared to Windows and OS/2), devices were auto-configured and hardware detection was very good. It was the first OS I used that booted into a somewhat live mode to do the installation.

Back in the late 90s there was a very active and enthusiastic developer and user community. New apps were being developed and released all the time. Programs like Opera and Gaim were being actively developed on BeOS BEFORE their Windows, Linux, MacOS, and OS/2 counterparts were released.

However, the Be company never made a success out of the OS business. They were sabotaged by Microsoft and Apple and their business dried up. Be Inc. had some success in the embedded market and briefly sold their OS as the basis for Sony's internet surfing device.

Be Inc. started building their own computers in the early 90s. The machines were very ahead of their time. Be Boxes were dual processor, PowerPC. They stopped selling hardware and ported their BeOS to Intel and Mac hardware and sold just the operating system. It was a microkernel design, 64bit journaled filesystem, OpenGL based graphics, multithreaded and mostly POSIX compliant system. BeOS had file indexing and searching built-in. BeOS was very sophisticated for its time.

Since the company went under just as USB and cheap IDE cd burners became available, the OS dated very quickly and hardware support became a real limiting factor.

---

### Post by RAV TUX on 2007-08-11
> **ezsit said:**
> Back in 1996 or 1997 I tried BeOS 4.5 and then 5.0. I was very impressed. The stability was great, the system booted in mere seconds, adding apps was super easy (just uncompress the file into the Programs folder), the speed was amazing (my P2 333Mhz just flew compared to Windows and OS/2), devices were auto-configured and hardware detection was very good. It was the first OS I used that booted into a somewhat live mode to do the installation.

Back in the late 90s there was a very active and enthusiastic developer and user community. New apps were being developed and released all the time. Programs like Opera and Gaim were being actively developed on BeOS BEFORE their Windows, Linux, MacOS, and OS/2 counterparts were released.

However, the Be company never made a success out of the OS business. They were sabotaged by Microsoft and Apple and their business dried up. Be Inc. had some success in the embedded market and briefly sold their OS as the basis for Sony's internet surfing device.

Be Inc. started building their own computers in the early 90s. The machines were very ahead of their time. Be Boxes were dual processor, PowerPC. They stopped selling hardware and ported their BeOS to Intel and Mac hardware and sold just the operating system. It was a microkernel design, 64bit journaled filesystem, OpenGL based graphics, multithreaded and mostly POSIX compliant system. BeOS had file indexing and searching built-in. BeOS was very sophisticated for its time.

Since the company went under just as USB and cheap IDE cd burners became available, the OS dated very quickly and hardware support became a real limiting factor.
Very interesting read.

---

