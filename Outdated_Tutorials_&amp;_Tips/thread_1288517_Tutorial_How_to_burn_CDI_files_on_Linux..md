---
title: "Tutorial: How to burn CDI files on Linux."
date: 2009-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by dragos240 on 2009-10-11
This method has worked for me. For this to work you will need 8 Things:

1. A sega dreamcast
2. A blank disk
3. A linux system
4. Cdrecord
5. Cdirip
6. A dreamcast game in CDI format (the way most DC games are formatted in)
7. A working cd-r drive.
8. And a physical computer

Okay, lets start. Make sure you have cdrecord, this is pre-installed on most distros. If it isn't, install it via your local repository. Now, get cdirip from [here]("http://es.geocities.com/dextstuff/cdirip/cdirip06.tgz"). Extract the tar.gz with tar by doing this.

```
tar -xf cdrip06.tgz
```Now that that is done, you need to make cdirip able to execute and also you need to copy it to /usr/bin. Do both by doing this:
```

chmod +x cdirip && cp cdirip /usr/bin
```Okay, now that those are installed, download this script. (thanks to milksheik)

[ATTACH]2147511530[/ATTACH]

Rename this script to burndc-cdi by:

```
mv burndc-cdi.txt burndc.cdi
```After this chmod it:

```
chmod +x burndc-cdi
```edit the file with whatever editor you want, and edit this:

```
    if [ -f $WAVFILE ]; then
        cdrecord dev=ATA:1,0,0 speed=4 -multi -audio $WAVFILE && rm $WAVFILE
    elif [ -f $ISOFILE ]; then
        cdrecord dev=ATA:1,0,0 speed=4 -multi -xa $ISOFILE && rm
```do this, 

```
cdrecord -scanbus
```and look for a result, when you've found it, edit that in. For example, mine is 4,0,0 in this example:

```
~$ cdrecord -scanbus

scsibus4:

4,0,0    400) 'TSSTcorp' 'CD/DVDW TS-H652D' 'GA01' Removable CD-ROM

```and I would change it to this:

```
    if [ -f $WAVFILE ]; then
        cdrecord dev=ATA:4,0,0 speed=4 -multi -audio $WAVFILE && rm $WAVFILE
    elif [ -f $ISOFILE ]; then
        cdrecord dev=ATA:4,0,0 speed=4 -multi -xa $ISOFILE && rm
```Now save the file.

And finally, burn the file onto the disk with:
```
./burndc-cdi DREAMCAST-CDI-FILE
```or

```
bash burndc-cdi DREAMCAST-CDI-FILE
```Replacing DREAMCAST-CDI-FILE with your cdi.

Enjoy!

This is a post I made a few winutes ago at dcemu.

---

### Post by falloutdc on 2010-03-09
This did not work for me running
Karmic 2.6.31-20-generic SMP x86_64 GNU/Linux

I got the script from the dcemu.co.uk bbs (Attachement here is down)
[http://paste.ubuntu.com/392182/](http://paste.ubuntu.com/392182/)
[http://pastebin.com/aPX5yR04](http://pastebin.com/aPX5yR04)

also cdirip cannot be downloaded anymore from megagames or authors website.

Waybackarchiv mirror
[http://web.archive.org/web/*/http://...p/cdirip06.tgz]("http://web.archive.org/web/*/http://es.geocities.com/dextstuff/cdirip/cdirip06.tgz")

Filehosting mirrors
[http://www.1filesharing.com/download...7/cdirip06.tgz]("http://www.1filesharing.com/download/SP3XZJZ7/cdirip06.tgz")
[http://www.rapidmirrors.com/files/2WRIKRJE/cdirip06.tgz](http://www.rapidmirrors.com/files/2WRIKRJE/cdirip06.tgz)
[http://www.uploadmirrors.com/downloa...H/cdirip06.tgz]("http://www.uploadmirrors.com/download/KWI2FRKH/cdirip06.tgz")



First you have to change ATA:1,0,0 to /dev/XXX inside the script, else it wont run at all

run **wodim --devices **to find the location of your burner


Now if i run the script 
burndc-cdi /location/of/image.cdi
i get


> Found image file. Opening...
This is a v3 image

Analyzing image...
Found 2 session(s)

Ripping image... (Press Ctrl-C at any time to exit)

Session 1 has 1 track(s)
Creating cuesheet...
Saving  Track:  1  Type: Audio/2352  Size: 302     LBA: 0       [cut: 2] 
                                                          
Session 2 has 0 track(s)
Open session

All done!And thats obviously wrong as he says no session inside track 2.


Running the commands inside the shell

> xxx@ubuntu-desktop:~/Downloads/cdirip06$ cdirip /home/xxx/Downloads/cdirip06/xxx.cdi /home/xxx/Downloads/cdirip06 -cdrecord
CDIrip 0.6 - (C) 2001 by DeXT

Searching file: '/home/xxx/Downloads/cdirip06/bbq-aero.cdi'
Found image file. Opening...
This is a v2 image
Destination path: '/home/xxx/Downloads/cdirip06'

Analyzing image...
Found 2 session(s)

Ripping image... (Press Ctrl-C at any time to exit)

Session 1 has 1 track(s)
Creating cuesheet...
Saving  Track:  1  Type: Audio/2352  Size: 300     LBA: 0       [cut: 2] 
                                                          
Session 2 has 1 track(s)
Saving  Track:  2  Type: Mode2/2336  Size: 341445  LBA: 11700   [cut: 2] [ISO]
                                                          
All done!                      Works

I really would like to burn some homebrew cdi images, but cannot afford to bust anymore cd-r's .If Somebody could take a look at the script burndc-cdi shell script that would be great

---

### Post by dragos240 on 2010-03-10
> **falloutdc said:**
> This did not work for me running
Karmic 2.6.31-20-generic SMP x86_64 GNU/Linux

I got the script from the dcemu.co.uk bbs (Attachement here is down)
[http://paste.ubuntu.com/392182/](http://paste.ubuntu.com/392182/)
[http://pastebin.com/aPX5yR04](http://pastebin.com/aPX5yR04)

also cdirip cannot be downloaded anymore from megagames or authors website.

Waybackarchiv mirror
[http://web.archive.org/web/*/http://...p/cdirip06.tgz]("http://web.archive.org/web/*/http://es.geocities.com/dextstuff/cdirip/cdirip06.tgz")

Filehosting mirrors
[http://www.1filesharing.com/download...7/cdirip06.tgz]("http://www.1filesharing.com/download/SP3XZJZ7/cdirip06.tgz")
[http://www.rapidmirrors.com/files/2WRIKRJE/cdirip06.tgz](http://www.rapidmirrors.com/files/2WRIKRJE/cdirip06.tgz)
[http://www.uploadmirrors.com/downloa...H/cdirip06.tgz]("http://www.uploadmirrors.com/download/KWI2FRKH/cdirip06.tgz")



First you have to change ATA:1,0,0 to /dev/XXX inside the script, else it wont run at all

run **wodim --devices **to find the location of your burner


Now if i run the script 
burndc-cdi /location/of/image.cdi
i get


And thats obviously wrong as he says no session inside track 2.


Running the commands inside the shell

Works

I really would like to burn some homebrew cdi images, but cannot afford to bust anymore cd-r's .If Somebody could take a look at the script burndc-cdi shell script that would be great

Thanks for helping out!

---

### Post by dwangoac on 2010-04-11
I wasn't immediately sure what to do after issuing the cdirip command with the -cdrecord option as that did not immediately burn a disc in my case.  I found a good guide at:

[http://www.1up.com/do/blogEntry?bId=6096531](http://www.1up.com/do/blogEntry?bId=6096531)

In essence, the summary of that guide is get cdirip installed and create a text file with the following contents:


```

#!/usr/bin/bsh

cdirip $1 -iso
cdrecord dev=/dev/cdrw -multi tdata01.iso
cdrecord dev=/dev/cdrw -multi tdata02.iso
rm ./tdata0*.iso

```

This is a very simple script and may not work in all cases but it's a good start.  You may need to replace /dev/cdrw in the script above with the output you get from wodim --devices such as /dev/scd0.  Hopefully this script combined with the information on using cdrip in this thread will work.  Take note that if you execute the commands manually make sure you burn 01.iso before 02.iso or you may have problems.

Hopefully this isn't too terse.  Good luck,

A.C.
******

---

