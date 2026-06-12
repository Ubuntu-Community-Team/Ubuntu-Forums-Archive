---
title: "HOWTO: Remove APE tags from MP3 Files"
date: 2008-12-16
forum: Outdated Tutorials &amp; Tips
---

### Post by aheckler on 2008-12-16
Besides the music data itself, MP3 files also include metadata that stores information like the artist, album, and track number. (These are also known as "tags".) This is so that various media players can display this information without having to ask you for it. Sometimes though, different ways of storing these tags (ID3v1, ID3v2, APE, etc.) can conflict, [causing problems]("http://bugzilla.gnome.org/show_bug.cgi?id=362876") in programs like Rhythmbox. Since ID3 is the most common form in which MP3 files store their metadata, it might be a good idea to erase any other tags so as to avoid problems.

[SIZE="2"][COLOR="Red"]**PLEASE NOTE:**[/COLOR][/SIZE] Once you've erased APE tags, there's no way to get them back except for adding them to your files again one at a time. Although the apetag package used in this guide is able to add and modify APE metadata, the author cannot support this process. [COLOR="Red"]**Use with caution**[/COLOR]!

Here's how to get rid of the APE tags in your MP3 files:

[SIZE="4"]**1. Download the "apetag" package**[/SIZE]

[INDENT]Download apetag from [here]("http://rarewares.org/debian/packages/unstable/"). Don't worry about the "i386" part; if you're on a 64-bit system, we'll take care of that shortly.
[/INDENT]
[SIZE="4"]**2. Fulfill dependencies**[/SIZE]
[INDENT]You may need to install libstdc++5 as a dependency. To check if you already have it installed, type this in the terminal:

```
dpkg -s libstdc++5
```

If you see "Package `libstdc++5' is not installed", then run:

```
sudo apt-get install libstdc++5
```

If instead you see a bunch of information, then the libstdc++5 package is already installed.[/INDENT]

[SIZE="4"]**3. Install apetag**[/SIZE]

[INDENT]If you're on a 32-bit system, simply double-clicking the .deb file and then clicking **Install** will install apetag.

However, if you are running on a 64-bit computer, you'll need to force apetag to install itself even though you have the "wrong" architecture. Do that by opening a terminal in the directory where you saved your apetag .deb file and running this command:

```
sudo dpkg --force-architecture -i apetag_*_i386.deb
```

Apetag will install itself and be fully functional. Now we can get to removing those pesky tags.[/INDENT]

[SIZE="4"]**4. Remove APE tags from MP3's**[/SIZE]

[INDENT]To remove APE tags from a single file, run this in terminal:

```
apetag -i [COLOR="Red"]musicfile[/COLOR].mp3 -m overwrite
```

You'll have to replace the red "musicfile" text with the name of your MP3, obviously. Don't forget to enclose the filename in quotes if it contains spaces or other funny characters.

To remove APE tags from all of your MP3's at once, replace the red "music-directory" text with the name of your own music folder, then run this:

```
find [COLOR="Red"]music-directory[/COLOR]/ -iname "*.mp3" -exec apetag -i {} -m overwrite \;
```

This could take a few minutes depending on the size of your MP3 collection, so just sit back and wait a bit. :-)[/INDENT]

==================================================
==================================================

**This tutorial was tested on an Ubuntu 9.04 (64-bit) system.**

I would like to thank **uziel** and **oyejorge** from [this thread]("http://ubuntuforums.org/showthread.php?t=292111") for ideas on how to implement apetag, as well as everyone at Ubuntu Forums for generally being awesome.

---

### Post by madverb on 2009-02-07
There is another option. You can just use pyRenamer along with EasyTAG.
```
sudo apt-get install easytag
sudo apt-get install pyrenamer
```
[LIST=1]
[*]Open pyRenamer
[*]Navigate to the offending directory of mp3s
[*]Select Substitutions from the tabs down the bottom
[*]Tick Replace
[*]Put mp3 in first column and ape in second
[*]Click Rename
[*]Open EasyTAG and delete the offending tags and save all the files
[*]Now you can change the extension back to mp3 with pyRenamer
[/LIST]
Peace out!

---

### Post by 3pleT on 2009-04-24
something's very wrong here. i tried to remove the tags using apetag and now gstreamer/rhythmbox reads them all wrong. it seems to have removed the genre and the last digit of the year. can anyone tell me why this is happening?

---

### Post by madverb on 2009-04-24
See my earlier post...

---

### Post by aheckler on 2009-04-25
**3pleT:** I tested this on Jaunty and Rhythmbox still reads everything OK for me.

---

### Post by binbash on 2009-04-25
Tested with jaunty and it is ok, thanks

---

### Post by 3pleT on 2009-05-02
It's OK now. I did it the easiest way possible:
1. Install Wine (if it's not already installed), download and install mp3tag: [http://www.mp3tag.de/en/download.html](http://www.mp3tag.de/en/download.html)
2. Open mp3tag and open: Tools->Options, Tags->Mpeg, make sure Read->APE is checked and uncheck everything other than APE under Remove.
3. Open the path to your audio collection.
4. Arrange files by "Tag", select all files tagged with APE (they should be somewhere around the top), and remove their tags.

Some files now seem to have tags other than APE or ID3. Rhythmbox still can't modify those.

---

### Post by phlancelot on 2009-07-18
Madverbs solution worked beautifully for me

THANKS!!!

---

### Post by luisg on 2009-11-09
I don't recommend madverb's solution, it cuts a couple of seconds at the end of mp3.

---

### Post by brookie on 2009-12-04
Hello,

I couldn't install the apetag dependency in Karmic.

```
sudo apt-get install libstdc++5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidate
```

So I tried madverb's solution with pyremover/easytag. It worked. Next I did some googling and found this post (see last post by Martin Mai: 

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/127510](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/127510)

Another solution is: 

1. Install exfalso in synaptic. Search for "quodlibet" to find the "quodlibet-plugins" and install them as well. 

2. Open exfalso and click on plugins, enable APEv2 to ID3v2 plugin. Close plugins box.

3. Open music directory that is giving you problems in Rhythmbox. 

4. Highlight all the mp3 files in the lower left corner of exfalso window.

5. Right click on the highlighted files and you will see the "APEv3 to ID3v2" option. Select it from the right click menu and all the files will now have the APE tags gone. 

6. Open up rhythmbox and you can now edit your ID3 tags in there and they will stick without the APE tag overriding your changes. You could also edit the tags in Easytag or exfalso as well. 

Them dang APE tags are gone! Hope this helps some of you other Rhythmbox users. 

Cheers, 
brookie

---

### Post by elraun on 2010-02-28
here's what i did:

[LIST=1]
[*]sudo apt-get install soundconverter
[*]open the problem file or directory in sound converter
[*]save the file as mp3. it must have a new name if you are starting with an mp3 but this process also works for other file types. see the preferences to find out what the new name will be.
[*]you should now be able to edit the files with your music player.
[/LIST]

---

### Post by sgleo87 on 2010-05-01
> **madverb said:**
> There is another option. You can just use pyRenamer along with EasyTAG.
```
sudo apt-get install easytag
sudo apt-get install pyrenamer
```
[LIST=1]
[*]Open pyRenamer
[*]Navigate to the offending directory of mp3s
[*]Select Substitutions from the tabs down the bottom
[*]Tick Replace
[*]Put mp3 in first column and ape in second
[*]Click Rename
[*]Open EasyTAG and delete the offending tags and save all the files
[*]Now you can change the extension back to mp3 with pyRenamer
[/LIST]
Peace out!


Thanks! Worked perfectly for me!

(Tried the solution using Exfalso first, but this did not remove the ape tags.)

---

### Post by nyex on 2010-05-02
Yeah, madverb solution was the only one that did the trick for me. It does seem to cut a few seconds from the end of the mp3, though.

Another solution would be to just use another audio player ;) But Rhythmbox integration with gnome is pretty neat, I think.

---

### Post by jarondl on 2010-09-27
Thanks Brookie! 
That was exactly what I was looking for. 


> Another solution is: 

1. Install exfalso in synaptic. Search for "quodlibet" to find the "quodlibet-plugins" and install them as well. 

2. Open exfalso and click on plugins, enable APEv2 to ID3v2 plugin. Close plugins box.

3. Open music directory that is giving you problems in Rhythmbox. 

4. Highlight all the mp3 files in the lower left corner of exfalso window.

5. Right click on the highlighted files and you will see the "APEv3 to ID3v2" option. Select it from the right click menu and all the files will now have the APE tags gone. 

6. Open up rhythmbox and you can now edit your ID3 tags in there and they will stick without the APE tag overriding your changes. You could also edit the tags in Easytag or exfalso as well. 

Them dang APE tags are gone! Hope this helps some of you other Rhythmbox users. 

Cheers, 
brookie

---

### Post by carandraug on 2010-09-27
Here's a python script to remove the tag from a file.
```

#!/usr/bin/env python
import sys
import mutagen.apev2
for p in sys.argv:
	try:
		mutagen.apev2.delete(p)
	except Exception, e:
		print e

```

You'll need the python mutagen module installed
```

sudo aptitude install python-mutagen

```

If Rhythmbox finds both APE and ID3 tags, it will show the APE tags (or at least it used to). If the ID3 tags are wrong, you won't notice it on Rhythmbox until you remove the the APE tags. If you find that Rhythmbox shows wrong tags after you have removed the APE tags, this is probably the reason.

---

