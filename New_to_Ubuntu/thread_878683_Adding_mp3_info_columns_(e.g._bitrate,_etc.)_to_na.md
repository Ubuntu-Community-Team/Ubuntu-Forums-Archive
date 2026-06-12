---
title: "Adding mp3 info columns (e.g. bitrate, etc.) to nautilus list view"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by geb666 on 2008-08-03
Here's a solution I found to a problem some people posted about in [_**these**_]("http://ubuntuforums.org/showthread.php?t=265637") [_**threads**_]("http://ubuntuforums.org/showthread.php?t=547484"), however, I can't seem to reply to those posts so I'm creating this new thread.  First, you need to install python-nautilus and python-mutagen.  You might have to add the python-nautilus library path to the PYTHONPATH variable.  Then create a directory called python-extensions in ~/.nautilus.  Put the script below in that directory in a file called bsc.py or you can download the attachment.  Remember that python uses tabs for defining scope, so if you copy and paste the script below then you'll have to replace the spaces with tabs.  Finally, restart nautilus.  That should do it. :)

P.S.  I took the code from [_**this post**_]("http://www.nabble.com/multimedia-columns-in-list-view-td17791081i20.html") and modified it.


```
import os
import urllib
import nautilus
from mutagen.easyid3 import EasyID3
from mutagen.mp3 import MPEGInfo

class ColumnExtension(nautilus.ColumnProvider, nautilus.InfoProvider):
        def __init__(self):
                pass

        def get_columns(self):
                return (nautilus.Column("NautilusPython::title_column",
                                "title",
                                "Title",
                                "Song title"),
                nautilus.Column("NautilusPython::album_column",
                                "album",
                                "Album",
                                "Album"),
                nautilus.Column("NautilusPython::artist_column",
                                "artist",
                                "Artist",
                                "Artist"),
                nautilus.Column("NautilusPython::bitrate_column",
                                "bitrate",
                                "Bitrate",
                                "Bitrate"),)

        def update_file_info(self, file):
                if file.get_uri_scheme() != 'file':
                        return
                if file.is_mime_type('audio/mpeg'):
                        filename = urllib.unquote(file.get_uri()[7:])
                        audio = EasyID3(filename)

                if (os.path.isfile (filename)):
                        mpfile = open (filename)
                        mpinfo = MPEGInfo (mpfile)
                        br = str(mpinfo.bitrate/1000) + " Kbps"
                else:
                        br = ""

                file.add_string_attribute('title', audio["title"][0])
                file.add_string_attribute('album', audio["album"][0])
                file.add_string_attribute('artist', audio["artist"][0])
                file.add_string_attribute('bitrate', br)
                self.get_columns()
```

---

### Post by Elfy on 2008-08-03
It could be that the original thread is in the archive - perhaps you could link to it so others can see.

Could you also mark the thread as solved - it appeared that the thread was an unanswered support request, thanks.

---

### Post by darrell_123 on 2009-01-20
Geb - worked like a charm.  This was driving me crazy.  Thanks so much for posting it.  The only thing I noticed is it doesn't seem to work on network shared folders.

---

### Post by jmdsdf on 2009-01-30
I love this solution! Thanks guys! It was, however, missing one critical feature for me. It was missing a way to show the ID3 date tag. I've updated the script a bit, and here is my revision:

It would be great if this script were also updated with support for displaying JPEG EXIF shooting data. I, unfortunately, am not a Python wizard.

**UPDATE: **I have tried my best and updated this script with EXIF shooting information! It seems to work okay!

**UPDATE #2: **It now works better! Sometimes mp3 info was there but not getting filled in, also mp3 length support is now added.

**UPDATE #3: **Thanks to SabreWolfy for finding another unhandled exception!

**UPDATE #4: **Thanks to gueba for discovering this script wasn't properly closing file handles until it terminates

**UPDATE #5: **Thanks to Pitxyoki for discovering this script wasn't properly closing file handles if there's an exception

**UPDATE #6 (9/17/2009): **Thanks to enbeto for finding a way to read video information!

**UPDATE #7 (9/23/2009): **This is now in a Debian package for easy installation. I have kept the bsc-v2.py source attached in case anyone wants to review it. This is my first attempt at a Debian package, so please be nice in criticisms!

**UPDATE #8 (9/27/2009): **Updated nautilus-columns to support ID3 tags in FLAC, thanks l-x-l! I can't upload the .deb to this site any more. 

**UPDATE #9 (10/5/2009): **MKV support added. Version bump to 0.01.

**UPDATE #10 (10/6/2009): **postinit script automatically restarts Nautilus so options can be seen without logging in and logging out. Thanks thegutterpoet!

**UPDATE #10 (10/26/2009): **album/date added for FLAC/video. Thanks eldon.t!

**UPDATE #10 (3/3/2010): **wav file support, added sample rate file support thru mutagen and kaa (thanks for the idea N'ko) I cannot upload the .deb to Ubuntu Forums any longer, but hopefully this will get hosted at [https://launchpad.net/~team1](https://launchpad.net/~team1) ASAP.

**UPDATE #11 (4/17/2010): **Track number fix, thanks l-x-l

**UPDATE #12 (1/23/2011): **PDF support and more error handling when importing the libraries, thanks draxus! Included .deb in a zip file for easy installation.

---

### Post by mrucci on 2009-02-02
Can someone help me please?

ID3 tag organization columns are necessary.
I have followed this tutorial and used both provided files, the original and the edited one, neither work for me. I created the directory under /.nautilus, places the file there, and restarted nautilus. nothing happens.
One thing I do not understand is the lin in the instructions stating to change a path in capital letters?

please help the noob!

---

### Post by jerome1232 on 2009-02-02
> **mrucci said:**
> Can someone help me please?

ID3 tag organization columns are necessary.
I have followed this tutorial and used both provided files, the original and the edited one, neither work for me. I created the directory under /.nautilus, places the file there, and restarted nautilus. nothing happens.
One thing I do not understand is the lin in the instructions stating to change a path in capital letters?

please help the noob!

One important detail, did you put it under /.nautilus or ~/.nautilus, they are two very different places on your file system.

---

### Post by jmdsdf on 2009-02-02
mrucci, ensure all the dependencies are present, ensure that the script goes into ~/.nautilus/python-extensions/ or /usr/lib/nautilus/extensions-2.0/python/. Make sure you restart Nautilus (I just run "killall nautilus" from the terminal, or run dialog, i.e. Alt-F2). Then open Nautilus, and under Edit | Preferences | List Columns, you should see the extra columns. I hope this helps!

Btw, I updated the script with some more field I hope these will help everyone with managing photos with meta data. One shortcoming I have noticed is that Nautilus, unlike Windows Explorer, does not remember which folders should have which column headers. Oh well. A small annoyance, but not a critical one.

---

### Post by mrucci on 2009-02-02
Aahh! Thank you so much! It works now! one thing I passed was that there are instructions in the py file. need to read more.

But yes, I think my directory orientation was off.

Thanks for the help everyone, working great now!:D

---

### Post by SpetsnazC4 on 2009-02-04
Thanks for this great post! It's just what I need. Is there a way to view the mp3 track length/duration in a column?

---

### Post by SabreWolfy on 2009-02-05
<Experienced difficulties installing and using the script, but resolved them (my errors). Previous post here deleted.>

---

### Post by jmdsdf on 2009-02-06
SpetsnazC4, done! The length of the mp3 will also be formatted h:mm:ss or m:ss depending on the length of the track. Just re-download the script and restart Nautilus.

---

### Post by SabreWolfy on 2009-02-06
> **jmdsdf said:**
> SpetsnazC4, done! The length of the mp3 will also be formatted h:mm:ss or m:ss depending on the length of the track. Just re-download the script and restart Nautilus.

Great stuff! Thanks very much! I spent the whole of yesterday evening trying to add the duration to your script. I used "from mutagen.mp3 import MP3" and then "MP3.info.length", but for some reason I could not get values to appear in the "length" column which I added. If I placed "length" in the "title" column it worked, so thanks for updating your script.

**Edit:** I notice that the updated script is also doing something which I had problems with yesterday -- it is returning "unknown" for the length of some MP3 files. Right-clicking and selecting "Properties" shows the duration, so the file is not corrupted. All the files showing "unknown" for duration also show "unknown" for Title. "Properties" also shows "Unknown" for title though, so there may be a link -- if there is no title, there is no duration...

---

### Post by jmdsdf on 2009-02-06
I'm glad it's (mostly) working. Did you replace the entire script? Previously, a failure in reading the title/album/genre/track #/etc, would cause the script to throw an exception and abort leaving all the fields showing Unknown. I ran the script on 1000+ mp3s, and it worked for me. With fields that are missing it should show "[N/A]". I've updated the script here again with a couple minor changes for exception handling. If it's still not working, can you run the following script in the terminal on one file that isn't updating and give me the output? Thanks!

```

#!/usr/bin/python
from mutagen.easyid3 import EasyID3
from mutagen.mp3 import MPEGInfo

filename = "/home/your_user_name/Music/your_mp3_that_isnt_working.mp3"
audio = EasyID3(filename)
print audio
mpfile = open (filename)
mpinfo = MPEGInfo (mpfile)
print mpinfo.length
print mpinfo.bitrate

```

---

### Post by SabreWolfy on 2009-02-06
> **jmdsdf said:**
> I'm glad it's (mostly) working. Did you replace the entire script? Previously, a failure in reading the title/album/genre/track #/etc, would cause the script to throw an exception and abort leaving all the fields showing Unknown. I ran the script on 1000+ mp3s, and it worked for me. With fields that are missing it should show "[N/A]". I've updated the script here again with a couple minor changes for exception handling. If it's still not working, can you run the following script in the terminal on one file that isn't updating and give me the output? Thanks!

<snip>

I didn't replace the entire script -- I just added the extra columns to your script. Here is the output from the little test script above:

```

Traceback (most recent call last):
  File "test.py", line 6, in <module>
    audio = EasyID3(filename)
  File "/usr/lib/python2.5/site-packages/mutagen/easyid3.py", line 56, in __init__
    self.load(filename)
  File "/usr/lib/python2.5/site-packages/mutagen/id3.py", line 113, in load
    self.__load_header()
  File "/usr/lib/python2.5/site-packages/mutagen/id3.py", line 211, in __load_header
    raise ID3NoHeaderError("'%s' doesn't start with an ID3 tag" % fn)
mutagen.id3.ID3NoHeaderError: '024.mp3' doesn't start with an ID3 tag

```

Seems that some "bad" MP3 files do not have ID3 tags. I've previously extracted duration at the command line with:

```

mp3info -p "%03m:%02s\t%f\n" 024.mp3

```

which returns

```

031:44  024.mp3

```

Thanks!

---

### Post by jmdsdf on 2009-02-06
I'm sorry, it appears that the bug isn't in my script, rather in it's Python's Mutagen module (or even further upstream from there?). My only suggestion is to file a bug against Mutagen to see if their developers can update it. Hopefully the long try/except list in handling ID3 tags allows the script to fill in what it can find while disregarding the above errors.

---

### Post by SabreWolfy on 2009-02-06
> **jmdsdf said:**
> I'm sorry, it appears that the bug isn't in my script, rather in it's Python's Mutagen module (or even further upstream from there?). My only suggestion is to file a bug against Mutagen to see if their developers can update it. Hopefully the long try/except list in handling ID3 tags allows the script to fill in what it can find while disregarding the above errors.

Although I guess it could be argued that Mutagen is working correctly and is throwing an exception when it is asked to provide ID3 tag information from a file which does not have an ID3 tag in it.

**[COLOR="Blue"]I've modified the script[/COLOR]** (file attachment at the end of this message) to show the duration for all MP3 files, even those without an ID3 tag. I used "from mutagen.mp3 import MP3" and then used "MP3.info.length" which is independent of the ID3 tag. I placed this code earlier in the program, as it will not execute later on if the file does not have an ID3 tag.

I've also applied a consistent formatting of hh:mm:ss to the length so that the file list can be correctly sorted by length.

I've also trapped for the absence of the ID3 tag so that the "[n/a]" text now correctly appears for files without an ID3 tag.

Thanks for your work on this script though -- I'm now really happy that I can see the length of all my files and sort by length as well!

---

### Post by jmdsdf on 2009-02-06
SabreWolfy, sorry! I misunderstood. I thought it was throwing an exception when there was ID3 information (but say, not in the title). I now see what you're talking about, and will shortly modify the version I have posted as well. (including your updates for the consistent hh:mm:ss)

---

### Post by jh0n on 2009-02-07
thanks a MILLION!

---

### Post by SpetsnazC4 on 2009-02-08
> **jmdsdf said:**
> SpetsnazC4, done! The length of the mp3 will also be formatted h:mm:ss or m:ss depending on the length of the track. Just re-download the script and restart Nautilus.

w00t, thanks :D

---

### Post by doug1212 on 2009-02-08
Cool, don't suppose any pythoneers fancy adding ogg/flac vorbis comment info to the columns ;)
Doug.

---

### Post by jmdsdf on 2009-02-10
Unfortunately, I don't use ogg or flac. Are yours tagged with ID3v2 or APE?

---

### Post by renato1976 on 2009-02-11
Excellent script! 
However I can't do what I need to...
My Music folder has the following structure: 
27 folders (0-9, A...Z), in each Letter folder one folder for each artist, inside the artist folder one folder per album. 
How do I apply recursively the "visible columns" option? I can't possibly set it by hand for each album folder (63Gb of music = countless album folders). Any idea?

---

### Post by SabreWolfy on 2009-02-11
> **renato1976 said:**
> Excellent script! 
However I can't do what I need to...
My Music folder has the following structure: 
27 folders (0-9, A...Z), in each Letter folder one folder for each artist, inside the artist folder one folder per album. 
How do I apply recursively the "visible columns" option? I can't possibly set it by hand for each album folder (63Gb of music = countless album folders). Any idea?

If you are in List mode in Nautilus, each subfolder should appear in the list and you can click on the small black triangle to expand that folder in the current list. All the files in that folder will then be shown, with the current column selection.

---

### Post by renato1976 on 2009-02-11
Thanks SabreWolfy!

However, this method is quite time consuming. It would be ok if I had to do it once and for all, but since I constantly add new artist & album folders  I'd have to select for each new folder the visible columns-option...
Isn't there any one-click way to set the option automagically for all the subfolders in a folder?

---

### Post by jmdsdf on 2009-02-11
Does anyone know how to find bitrate, length and video size for an AVI/MP4/WMV using Python? I tried Mutagen's MPEGInfo class, and although the results sometimes give the right results for length and bitrate, often they are wrong.

---

### Post by t3dium on 2009-03-02
Thanks for this script, works great and was just what I needed.

> **renato1976 said:**
> 
However, this method is quite time consuming. It would be ok if I had to do it once and for all, but since I constantly add new artist & album folders  I'd have to select for each new folder the visible columns-option...
Isn't there any one-click way to set the option automagically for all the subfolders in a folder?

You can do this by going to System -> Preferences -> File Management -> List Columns.
It could be that File Management is not listed under your preferences, but you can then add it under System -> Preferences -> Main Menu.

---

### Post by renato1976 on 2009-03-04
Thank you so much t3dium!! It's exactly what I needed :)

---

### Post by blau2009 on 2009-03-24
I have used this script [http://ubuntuforums.org/showpost.php?p=6689895&postcount=16](http://ubuntuforums.org/showpost.php?p=6689895&postcount=16) and copied it into /usr/lib/nautilus/extensions-2.0/python as bsc.py and into ~/.nautilus/python-extensions as bsc.py. I then run sudo killall nautilus. When I restart Nautilus, I don't have the column options there.

What am I doing wrong?

Do I need to set the pythonpath variable? I've found instructions on how to do this on bash and how to script it so it's set on login. Do I need to follow these instructions?

EDIT: Solved, needed to install the python-pyexiv2 package and to chmod a+x the .py file in ~/.nautilus/python-extensions

Should have actually read the script :)

---

### Post by gueba on 2009-04-15
First of all, thank you for this useful script. We discussed it on the german ubuntu-forum [http://forum.ubuntuusers.de/topic/suche-nautilus-plug-in-fuer-mehr-infos/#post-1921263]("http://forum.ubuntuusers.de/topic/suche-nautilus-plug-in-fuer-mehr-infos/#post-1921263") and found a problem using external drives. After viewing *.mp3 files in nautilus with extra columns enabled, you can not umount the drive unless you kill nautilus. The user Plippo found out that these mp3s are opened but not closed properly and found this solution, which works for us: just insert ```
mpfile.close()
```
around line 150:
```

       mp3length = "%02i:%02i:%02i" % ((int(mpinfo.length/3600)), (int(mpinfo.length/60%60)), (int(mpinfo.length%60)))
	file.add_string_attribute('length', mp3length)
	mpfile.close()
except:
	file.add_string_attribute('bitrate', "[n/a]")
	file.add_string_attribute('length', "[n/a]")
```

btw: is it possible to show the id3-tag version (ID3v1, ID3v2.3 etc.)?

---

### Post by SabreWolfy on 2009-04-18
> **gueba said:**
> 
...
The user Plippo found out that these mp3s are opened but not closed properly and found this solution, which works for us
...


Thanks for telling us about this. I've made the change to my script. No idea about the ID3 tag versions without researching it. I've just looked at the mutagen MP3 class briefly and I don't see anything about ID3 tag versions.

Edit: There seems to be some discussion of this [here]("http://code.google.com/p/quodlibet/wiki/Mutagen"). Not sure if it is helpful. I found that page by searching Google for "mutagen mp3 id3 tag version".

---

### Post by Pitxyoki on 2009-06-18
Hi,
I have been using this extension for some time now.

When I started using it, I noticed that the bitrate is not correct for some files and discovered that the reason for that lies in the way the mutagen mp3 class reports an mp3's bitrate.
Apparently, if an mp3 file has a Xing header, and it is a VBR file, the mp3 class calculates the average bitrate for that file and outputs that average as it's bitrate.

I just modified the mp3 class so that it shows 'VBR' for this kind of files.
```
$ diff /usr/share/pyshared/mutagen/mp3.py .nautilus/python-extensions/mymp3.py
201a202
>                 self.isVBR = True
210a212,215
>         try:
>             self.isVBR
>             self.bitrate = "VBR"
>         except: pass

```

Also, you were closing the mp3 files, but not if an exception occurred:
```
$ diff -w bsc-v2-ubuntuforums.py .nautilus/python-extensions/bsc-v2-mine.py
26c26
< from mutagen.mp3 import MPEGInfo
---
> from mymp3 import MPEGInfo
92a93
> 			
148c149,154
< 				file.add_string_attribute('bitrate', str(mpinfo.bitrate/1000) + " Kbps")
---
> 				#print "Detected mp3 with bitrate " + str(mpinfo.bitrate) + ": " + filename
> 				if mpinfo.bitrate == "VBR":
> 					br = mpinfo.bitrate
> 				else:
> 					br = str(mpinfo.bitrate/1000) + " Kbps"
> 				file.add_string_attribute('bitrate', br)
156a163,166
> 				try:
> 					mpfile.close()
> 				except:	pass
> 

```

Finally, I'm getting an 'unknown' string for all bookmarked directories. If I refresh the folder, the 'unknown' string disappears, and the columns for that directory show as they should. Does anyone have a clue on how to solve this?

---

### Post by Keith_Beef on 2009-07-05
Thanks for taking the time to write and troubleshoot this. I've been looking for a way to display image data read from EXIF tags for a while.

This doesn't work quite right for me, and also I've noticed a curious difference between the dates in EXIF tags and in Nautilus.

First problem, is that I must have missed some detail in the installation of the script...

I installed the libraries:

```
sudo apt-get install python-nautilus python-mutagen python-pyexiv2
```

I downloaded the script and stored it in the ~/.nautilus/python-extensions directory.

I set PYTHONPATH to what I think it should be (but maybe this is wrong):

```
export PYTHONPATH=/usr/lib/nautilus-python
```

I killed and restarted Nautilus:

```
killall nautilus
nautilus &
```

Now, when I open a folder with all these photos, I can add columns to the view, but the columns remain empty.

Biggest part of this problem, though, is that when I right-click on an image file and look at properties, Nautilus just bombs out...

Second problem, is that I've got a stack of pictures taken last weekend, yet the times I get back are different depending on how I view them...

So, if I look using exiftime, I see something like this:
```
exiftime IMG_0132.JPG 
Image Created: 2009:07:04 16:39:56
Image Generated: 2009:07:04 16:39:56
Image Digitized: 2009:07:04 16:39:56
```

If I right-click and look at properties, I see Date Taken: 2009:07:04: 16:39:56, which matches.

Yet in the Nautilus window, for Date Modified, I see Sat 04 Jul 2009 12:39:56 EDT.

My camera, a Canon A610, was set to the local (EDT) time while taking the pictures. The hardware clock is set to UTC and the time is set correctly for EDT. I don't understand what Nautilus is doing to end up with this 4 hour difference...


K.

---

### Post by Arkitekt on 2009-09-02
how would I go about adding a Track # column to this script?

---

### Post by jmdsdf on 2009-09-02
Arkitekt, check again, there is a track number listed on my version. It is just called "Track" under Edit | Preferences | List columns | Track.

Keith_Beef, don't use "Date Modified", use "EXIF Dateshot". Again, make sure you're looking at my version. Running "export PYTHONPATH=/usr/lib/nautilus-python" isn't necessary, I'm not sure what that does. Did you make the script executable? i.e., run chmod a+x ~/.nautilus/python-extensions/bsc-v2.py ?

Pitxyoki, you have come up with a cool solution to the VBR problem. I wish that could go upstream, or you can find out a different way to detect VBR files that don't require patching the Python libraries.

---

### Post by Arkitekt on 2009-09-03
Ahh thanks, found it :) this script is great. wish there was a way to only set a folder and all of its subfolders to certain columns instead of either doing everyone that is in list view or each folder individually

---

### Post by MoonRocketZero on 2009-09-03
Not being able to see mp3 info has been bugging the heck out of me, I figured someone here had to have sloved this and a quick search gave me this thread and what seems like a perfect solution so far.

Followed the directions and  this seems to be just what I was looking for, thanks a lot :D

---

### Post by joedaman1999 on 2009-09-07
Thanks for the great script and easy instructions!!!!! Works great!:P

---

### Post by ENigma885 on 2009-09-11
_[SIZE="5"]To sum up the whole thing[/SIZE]_ (Updated to script UPDATE #11 (4/17/2010) as published by jmdsdf in post #4) 

**01** - Download the script from [[COLOR="Blue"]HERE[/COLOR]]("http://www.2shared.com/file/uzJh9_u_/bsc-v2.html") to ur desktop
**02** - Install the needed dependencies (make sure [COLOR="Red"]universe source[/COLOR] is enabled "*System>Administration>Software Sources>Ubuntu Software* tab")
```
sudo apt-get install python-nautilus python-mutagen python-pyexiv2

```
**03** - Make a directory in ur [COLOR="Red"]home/.nautilus[/COLOR] named "[COLOR="Red"]python-extensions[/COLOR]" (if done graphically, hit *ctrl+H *to view hidden folders in ur home directory)
```
mkdir ~/.nautilus/python-extensions
```
**04** - Copy the script to it (again, if done graphically, hit ctrl+H to view hidden folders in ur home directory)
```

cd Desktop
cp bsc-v2.py ~/.nautilus/python-extensions

```
**05** - Make the script executable
```
chmod a+x ~/.nautilus/python-extensions/bsc-v2.py
```
**06** - Close all Nautilus windows
```
killall nautilus
```
**07** - Relaunch Nautilus

And here's a screenshot of how it looks like 
[[IMG]http://img27.imageshack.us/img27/1262/mp3tags.th.png[/IMG]](http://img27.imageshack.us/i/mp3tags.png/)

---

### Post by enbeto on 2009-09-13
Hi all!
Really really nice script, it made my life much better!
I added some functionality for video files. It just shows the length of the video in the same Length column of mp3 files. I'm adding the script below in case someone is interested in. Hope not destroyed anything you did, my experience in python is really poor... However, I tried it and worked...

```

#!/usr/bin/python
# this script can installed to the current user account by running the following commands:

# sudo apt-get install python-nautilus python-mutagen python-pyexiv2 
#sudo apt-get install python-kaa-metadata
# mkdir ~/.nautilus/python-extensions
# cp bsc-v2.py ~/.nautilus/python-extensions
# chmod a+x ~/.nautilus/python-extensions/bsc-v2.py

# alternatively, you may be able to place the script in:
# /usr/lib/nautilus/extensions-2.0/python/

# change log:
# jmdsdf: version 2 adds extra ID3 and EXIF tag support
# jmdsdf: added better error handling for ID3 tags, added mp3 length support, distinguished
#         between exif image size and true image size
# SabreWolfy: set consistent hh:mm:ss format, fixed bug with no ID3 information 
#             throwing an unhandled exception
# jmdsdf: fixed closing file handles with mpinfo (thanks gueba)
# jmdsdf: fixed closing file handles when there's an exception (thanks Pitxyoki)
 
import os
import urllib
import nautilus
# for id3 support
from mutagen.easyid3 import EasyID3
from mutagen.mp3 import MPEGInfo
# for exif support
import pyexiv2

# for reading image dimensions
import Image

#for reading video length
import kaa.metadata #It also gives mp3 support I think

class ColumnExtension(nautilus.ColumnProvider, nautilus.InfoProvider):
    def __init__(self):
        pass

    def get_columns(self):
        return (
            # id3 support
            nautilus.Column("NautilusPython::title_column",
                "title",
                "Title",
                "Song title"),
            nautilus.Column("NautilusPython::artist_column",
                "artist",
                "Artist",
                "Artist"),
            nautilus.Column("NautilusPython::album_column",
                "album",
                "Album",
                "Album"),
            nautilus.Column("NautilusPython::tracknumber_column",
                "tracknumber",
                "Track",
                "Track number"),
            nautilus.Column("NautilusPython::genre_column",
                "genre",
                "Genre",
                "Genre"),
            nautilus.Column("NautilusPython::date_column",
                "date",
                "Date",
                "Date"),
            nautilus.Column("NautilusPython::bitrate_column",
                "bitrate",
                "Bitrate",
                "Audio Bitrate in kilo bits per second"),
            nautilus.Column("NautilusPython::length_column",
                "length",
                "Length",
                "Length of audio"),
            # exif support
            nautilus.Column("NautilusPython::exif_datetime_original_column",
                "exif_datetime_original",
                "EXIF Dateshot ",
                "Get the photo capture date from EXIF data"),
            nautilus.Column("NautilusPython::exif_software_column",
                "exif_software",
                "EXIF Software",
                "EXIF - software used to save image"),
            nautilus.Column("NautilusPython::exif_flash_column",
                "exif_flash",
                "EXIF flash",
                "EXIF - flash mode"),
            nautilus.Column("NautilusPython::exif_pixeldimensions_column",
                "exif_pixeldimensions",
                "EXIF Image Size",
                "EXIF Image size - pixel dimensions"),
            nautilus.Column("NautilusPython::pixeldimensions_column",
                "pixeldimensions",
                "Image Size",
                "Image size - pixel dimensions"),  
        )

    def update_file_info(self, file):
        if file.get_uri_scheme() != 'file':
            return

        filename = urllib.unquote(file.get_uri()[7:])
        
        # video handling
        if file.is_mime_type('video/x-msvideo'):
            viinfo=kaa.metadata.parse(filename)
            vilength = "%02i:%02i:%02i" % ((int(viinfo.length/3600)), (int(viinfo.length/60%60)), (int(viinfo.length%60)))
            file.add_string_attribute('length',vilength)    
        else:
            pass
        
        # mp3 handling
        if file.is_mime_type('audio/mpeg'):
            # attempt to read ID3 tag
            try:
                audio = EasyID3(filename)
                # sometimes the audio variable will not have one of these items defined, that's why
                # there is this long try / except attempt
                try:
                    file.add_string_attribute('title', audio["title"][0])
                except:
                    file.add_string_attribute('title', "[n/a]")
                try:
                    file.add_string_attribute('album', audio["album"][0])
                except:
                    file.add_string_attribute('album', "[n/a]")
                try:
                    file.add_string_attribute('artist', audio["artist"][0])
                except:
                    file.add_string_attribute('artist', "[n/a]")
                try:
                    file.add_string_attribute('tracknumber', audio["tracknumber"][0])
                except:
                    file.add_string_attribute('tracknumber', "[n/a]")
                try:
                    file.add_string_attribute('genre', audio["genre"][0])
                except:
                    file.add_string_attribute('genre', "[n/a]")
                try:
                    file.add_string_attribute('date', audio["date"][0])
                except:
                    file.add_string_attribute('date', "[n/a]")
            except:
                # [SabreWolfy] some files have no ID3 tag and will throw this exception:
                file.add_string_attribute('title', "[no ID3]")
                file.add_string_attribute('album', "[no ID3]")
                file.add_string_attribute('artist', "[no ID3]")
                file.add_string_attribute('tracknumber', "[no ID3]")
                file.add_string_attribute('genre', "[no ID3]")
                file.add_string_attribute('date', "[no ID3]")
                
            # try to read MP3 information (bitrate, length)
            try:
                mpfile = open (filename)
                mpinfo = MPEGInfo (mpfile)
                file.add_string_attribute('bitrate', str(mpinfo.bitrate/1000) + " Kbps")
                # [SabreWolfy] added consistent formatting of times in format hh:mm:ss
                # [SabreWolfy[ to allow for correct column sorting by length
                mp3length = "%02i:%02i:%02i" % ((int(mpinfo.length/3600)), (int(mpinfo.length/60%60)), (int(mpinfo.length%60)))
                mpfile.close()
                file.add_string_attribute('length', mp3length)
            except:
                file.add_string_attribute('bitrate', "[n/a]")
                file.add_string_attribute('length', "[n/a]")
                try:
                    mpfile.close()
                except:    pass

        else:
            # not a song
            file.add_string_attribute('title', '')
            file.add_string_attribute('album', '')
            file.add_string_attribute('artist', '')
            file.add_string_attribute('tracknumber', '')
            file.add_string_attribute('genre', '')
            file.add_string_attribute('date', '')
            file.add_string_attribute('bitrate', '')
            if file.is_mime_type('video/x-msvideo'):
                pass
            else:
                file.add_string_attribute('length', '')
        
        # image handling
        if file.is_mime_type('image/jpeg') or file.is_mime_type('image/png') or file.is_mime_type('image/gif') or file.is_mime_type('image/bmp'):
            # EXIF handling routines
            try:
                img = pyexiv2.Image(filename)
                img.readMetadata()
                file.add_string_attribute('exif_datetime_original',str(img['Exif.Photo.DateTimeOriginal']))
                file.add_string_attribute('exif_software',str(img['Exif.Image.Software']))
                file.add_string_attribute('exif_flash',str(img['Exif.Photo.Flash']))
                file.add_string_attribute('exif_pixeldimensions',str(img['Exif.Photo.PixelXDimension'])+'x'+str(img['Exif.Photo.PixelYDimension']))
            except:
                # no exif data?
                file.add_string_attribute('exif_datetime_original',"")
                file.add_string_attribute('exif_software',"")
                file.add_string_attribute('exif_flash',"")
                file.add_string_attribute('exif_pixeldimensions',"")
            # try read image info directly
            try:
                im = Image.open(filename)
                file.add_string_attribute('pixeldimensions',str(im.size[0])+'x'+str(im.size[1]))
            except:
                file.add_string_attribute('pixeldimensions',"[image read error]")
        else:
            # not an image
            file.add_string_attribute('exif_datetime_original', '')
            file.add_string_attribute('exif_software', '')
            file.add_string_attribute('exif_flash', '')
            file.add_string_attribute('exif_pixeldimensions', '')
            file.add_string_attribute('pixeldimensions', '')
        
        self.get_columns()

```

---

### Post by jmdsdf on 2009-09-17
Awesome work enbeto! I've improved it a bit, I'll modify my first post. By the way, your Python coding looks great! Then again, I'm a novice as well. :)

---

### Post by jmdsdf on 2009-09-23
ENigma885, nice work by the way. It has made me realize installing this script requires too much thought. I've updated this whole process into a Debian package for easier installation.

---

### Post by jrbray on 2009-09-24
The fields work in Column Mode for me, but if I try to modify the Display/Icon Captions, I get the new field names, but the contents remain as 'unknown' when I switch to Icon view. Does that work for you?

---

### Post by jmdsdf on 2009-09-24
I'm sorry, I'm a bit confused in the problem. Are you saying that you see the columns in "List View", but if you rename the file the column goes to "Unknown" for the fields? I just tried that, and it doesn't happen for me. I can also switch between "List View", "Compact View" and "Icon View" with no problems. The fields do show up briefly as "Unknown", but get filled in.

---

### Post by SabreWolfy on 2009-09-27
> **jmdsdf said:**
> ENigma885, nice work by the way. It has made me realize installing this script requires too much thought. I've updated this whole process into a Debian package for easier installation.

Thanks! I installed your Debian package after ensuring all dependencies were met and everything works fine.

However: the Python nautilus module seems to be absent:

```

Traceback (most recent call last):
  File ".../.nautilus/python-extensions/bsc-v2.py", line 20, in <module>
    import nautilus
ImportError: No module named nautilus

```

But it *is* installed:

```

$ dpkg -l python-nautilus
...
ii  python-nautilus
...

```

If I open the Python interpreter and enter "import nautilus" I still get the same error as above ... ? How does the script run if this module is missing?

---

### Post by l-x-l on 2009-09-27
Worked for me but no FLAC support?

---

### Post by jmdsdf on 2009-09-27
SabreWolfy, it appears as if you have an old version installed in your user folder. Run "rm ~/.nautilus/python-extensions/bsc-v2.py". The package installs the script to /usr/lib/nautilus/extensions-2.0/python/bsc-v2.py

l-x-l, I have added FLAC support for ID3 tags and updated the package. Sadly, the audio length isn't recognized.

---

### Post by SabreWolfy on 2009-09-28
> **jmdsdf said:**
> SabreWolfy, it appears as if you have an old version installed in your user folder. Run "rm ~/.nautilus/python-extensions/bsc-v2.py". The package installs the script to /usr/lib/nautilus/extensions-2.0/python/bsc-v2.py


Yes, that was the problem initially (hence the paste of that code above; I subsequently edited the post).

After deleting that old version, the script in the location installed by the Debian package works and I can see length of tracks, etc. but if I open Python and try "import nautilus", it still gives an error. Just wondering how it works if it can't find the module.

---

### Post by thegutterpoet on 2009-10-05
> **jmdsdf said:**
> ENigma885, nice work by the way. It has made me realize installing this script requires too much thought. I've updated this whole process into a Debian package for easier installation.

I have been trying all sorts of codes and scripts all run in the terminal to get my folder views showing artists or albums or durations...but to no avail.

Where is this debian package you mention here mate??? And will it give me what I need??? as in artist, or album columns in the list view????

---

### Post by ENigma885 on 2009-10-05
> **thegutterpoet said:**
> I have been trying all sorts of codes and scripts all run in the terminal to get my folder views showing artists or albums or durations...but to no avail.

Where is this debian package you mention here mate??? And will it give me what I need??? as in artist, or album columns in the list view????
Check post #4 in the 1st page
or dl the deb from [here]("http://ubuntuforums.org/attachment.php?attachmentid=130866&d=1254759323")

---

### Post by thegutterpoet on 2009-10-05
**I have installed the deb package...[B]but** can see NO artist or duration options in the nautilus preferences for column lists...do I need to restart??? or switch them on through some other method???[/B]

---

### Post by ENigma885 on 2009-10-05
Seems like there's something wrong with ur FF file handling configuration. 
Anyway, save the deb to ur desktop and double click it from there not through FF.

---

### Post by thegutterpoet on 2009-10-05
I also tried running the commands in the text file...

but these two didnt work...

**cp bsc-v2.py ~/.nautilus/python-extensions**

gave me a response of :
**cp: cannot stat `bsc-v2.py': No such file or directory**

and **chmod a+x ~/.nautilus/python-extensions/bsc-v2.py**

gave me : **chmod: cannot access `/home/raphael/.nautilus/python-extensions/bsc-v2.py': No such file or directory**

---

### Post by thegutterpoet on 2009-10-05
Well I got the file installed...but now need to know how to use it!

Is there a setting I need to change to tell the folder view to show the columns I desire? As 'artist' and 'duration' have not appeared in View/Visible Columns...

---

### Post by ENigma885 on 2009-10-05
Open a Nautilus window and
Edit (menu, top left)>> Preferences>> List Columns (tab, 4th from left) 
Then check or uncheck the columns u need.
See attached screenshot!

**Important:-
After u install the deb file or manually the script, u have to restart Nautilus. Better to logout and back in again or restart ur system.

---

### Post by thegutterpoet on 2009-10-05
Cheers Enigma. I should have restarted before panicking and pleading for more help...Logging out and in has given me what I was seeking. So thanks for the help, have a wicked day, or night, wherever you are...

---

### Post by eldon.t on 2009-10-23
hi,

very nice nautilus addon script.
Unfortunately it damages lists response time on large directories, so be aware of that before using it.

i had to remove the video part to skip tag parsing on video files, i also took the chance to migrate all "audio" tags to using kaa.metadata only, it should not improve performance much or reduce the memory footprint but well the less imports you make the better in my opinion, so here's my "audio only" script part :

```
		if file.is_mime_type('audio/mpeg') | file.is_mime_type('audio/x-flac'):
			try:
				info=kaa.metadata.parse(filename)
				try: file.add_string_attribute('length',"%02i:%02i:%02i" % ((int(info.length/3600)), (int(info.length/60%60)), (int(info.length%60))))
				except: file.add_string_attribute('length','-')
				try: file.add_string_attribute('bitrate',str(int(info.bitrate)))
				except: file.add_string_attribute('bitrate','-')
				try: file.add_string_attribute('title', info.title)
				except: file.add_string_attribute('title', '-')
				try: file.add_string_attribute('album', info.album)
				except: file.add_string_attribute('album', '-')
				try: file.add_string_attribute('artist', info.artist)
				except: file.add_string_attribute('artist', '-')
				try: file.add_string_attribute('genre', info.genre)
				except: file.add_string_attribute('genre', '-')
				try: file.add_string_attribute('tracknumber',info.trackno)
				except: file.add_string_attribute('tracknumber', '-')
				try: file.add_string_attribute('date',info.userdate)
				except: file.add_string_attribute('date', '-')				
			except:
				file.add_string_attribute('length','-')
				file.add_string_attribute('bitrate','-')
				file.add_string_attribute('title','-')
				file.add_string_attribute('artist','-')
				file.add_string_attribute('genre','-')
				file.add_string_attribute('tracknumber','-')
				file.add_string_attribute('date','-')
```

don't forget you can remove/comment the two import lines from the current script :

```
#from mutagen.easyid3 import EasyID3
#from mutagen.mp3 import MPEGInfo
```

you can still use the exif part if you want.

it has worked so far for all my flac / mp3 files

thx to the original poster for his work

---

### Post by wii552 on 2009-10-23
waht theme is that? (i love it!)

---

### Post by jmdsdf on 2009-10-24
eldon.t: unfortunately kaa-metadata doesn't show full date information (it shows "2009" instead of "2009-10-24") and the bitrate functionality seems broken. Also, another problem is that "album" doesn't seem to be in KaaMetadata: [http://doc.freevo.org/2.0/SourceDoc/KaaMetadata](http://doc.freevo.org/2.0/SourceDoc/KaaMetadata)

Thanks very much for reminding me that I forgot to add the date field for video!

---

### Post by irish66 on 2009-10-25
thank you very much

---

### Post by eldon.t on 2009-10-26
> **jmdsdf said:**
> eldon.t: unfortunately kaa-metadata doesn't show full date information (it shows "2009" instead of "2009-10-24") and the bitrate functionality seems broken. Also, another problem is that "album" doesn't seem to be in KaaMetadata

i forgot the album data in my script so i fixed my post above and you will get the album tag too.

Don't look too closely at the freevo documentation it seems quite out of date.

the ubuntu python-kaa-metadata provides a sample script to display the parsed data "mminfo", you can see all the parsed tags kaa managed to get using that script and more with the debug command : "mminfo -d 2 file.mp3"

the date problem can be fixed too, it looks like the problem is there's no standardized date format for id3 date tags so end users have to "guess" the date format in that tag, here the devs decided to try and parse the date and return a numeric value, aka a year in format "YYYY".

that can actually be fixed in one line by forcing the return of the raw date format inserted in the mp3 tag as you will see it in the debug info of mminfo.

the fix below will return a string instead of an integer so that could prove hazardous for some scripts but not in our case :

-- Edited wth a better cleaner hack -- no change to eyeD3 but only to kaa audio/mp3.py

you simply have to change the following thing :

in /usr/share/pyshared/kaa/metadata/audio/mp3.py aroud line 164 :

replace :
```
                if id3.tag.getYear():
                    self.userdate = id3.tag.getYear()
```
with :
```
                if id3.tag.getYear():
		    dateFrame = id3.tag.getDate()
        	    if dateFrame:
                    	self.userdate = dateFrame[0].getDate();
```


As a reference here's the original code of the previous hack is proposed, if you need to revert :
in /usr/share/pyshared/kaa/metadata/audio/eyeD3/frames.py aroud line 796 :
```
   def getYear(self):
      if self.date:
         return self.__padDateField(self.date[0], 4);
      else:
         return None;
```

a better solution would be to add an additional entry in the AUDIOCORE array in audio/core.py that would return the raw date as a string, but that requires a larger, but easy enough, fix.

It should only impact mp3 parsing, and i've noticed that the flac dates are returned correctly.

As for the bitrate problem i think i've noticed some mp3 without bitrate info but it only appears on a very small number of my files and i haven't investigated that..

---

### Post by Pitxyoki on 2009-10-26
> **eldon.t said:**
> As for the bitrate problem i think i've noticed some mp3 without bitrate info but it only appears on a very small number of my files and i haven't investigated that..

Hi,
This also happens with the mutagen classes in some rare occasions.
By the way, what does kaa show for variable bitrate files? The average bitrate or "VBR"?

---

### Post by jmdsdf on 2009-10-26
Thanks eldon.t! I'm glad the album field is there, I've updated my package with that.

It looks like the getDate() function is already in /usr/share/pyshared/kaa/metadata/audio/mp3.py but it just doesn't fill out a field when parsing. Is there other way to access this function or the variable that contains the full date data? I could fork the python-kaa-metadata package... better yet, maybe you could ask for that functionality to be included upstream? In the mean time I'll keep using the python-mutagen package. I hate pulling functionality from the script. When I was downloading podcasts, this ability to differentiate by days was invaluable.

---

### Post by eldon.t on 2009-10-27
> **Pitxyoki said:**
> Hi,
This also happens with the mutagen classes in some rare occasions.
By the way, what does kaa show for variable bitrate files? The average bitrate or "VBR"?

Kaa shows an average bitrate.

As for the missing bitrates i've identified one source for this bug which is when the mp3 has a thumbnail tag in it, then the bitrate is never found. I do have a few other mp3 files with missing "kaa bitrates" but haven't checked them out.


[QUOTE=jmdsdf]It looks like the getDate() function is already in /usr/share/pyshared/kaa/metadata/audio/mp3.py but it just doesn't fill out a field when parsing. Is there other way to access this function or the variable that contains the full date data? I could fork the python-kaa-metadata package...[/QUOTE]

i don't see that getDate() function or call in audio/mp3.py, but i have updated to the latest (karmic) packages which correspond to the current up to date versions of this lib.

Anyways from what i've seen in my rapid overview of the code, mp3 parsing is mainly done by a third party lib "eyeD3" and most of the data manipulation is done there, so i'm not sure it's quite a kaa-metadata problem.

I have fixed my previous date hack to only modify audio/mp3.py, the previous hack was a bit too ugly to be left around :)

So yes this hack could be proposed to kaa-metadata although according to their "known bug" comment in the current version, they may see that as a step back, but i don't really know if that date is really the raw date or a parsed and formated date.

---

### Post by jrbray on 2009-11-28
> **jmdsdf said:**
> I'm sorry, I'm a bit confused in the problem. Are you saying that you see the columns in "List View", but if you rename the file the column goes to "Unknown" for the fields? I just tried that, and it doesn't happen for me. I can also switch between "List View", "Compact View" and "Icon View" with no problems. The fields do show up briefly as "Unknown", but get filled in.

My problem is the latter, information is show in the icon view, but the captions remain Unknown. (Sorry for the tardy reply, got distracted)

---

### Post by jmdsdf on 2009-12-03
jrbray, the captions shouldn't be shown in Icon view. However, I may still be confused about your problem--perhaps a screenshot would help me understand?

---

### Post by jrbray on 2009-12-24
Here is my screenshot showing the different effects of icon and list mode

Sorry about the slow response, not at the appropriate machine much now.

---

### Post by jmdsdf on 2009-12-27
Cool! I didn't even know there was an option in Nautilus under Edit | Preferences | Display | Icon Captions. It doesn't work for me here either and I don't know why. Anyone else?

---

### Post by glaubersm on 2009-12-29
Hello
Does anyone know where I can find a script that shows details of video files such as resolution and duration, for example?

---

### Post by go_beep_yourself on 2010-01-20
[https://launchpad.net/~team1](https://launchpad.net/~team1)

I've created this for those who would like to see this project further and for a place to put the deb packages.

---

### Post by N'ko on 2010-03-18
I need to see the Sample Rate in Nautilus.  Can anyone help me add a Sample Rate column to the script.

Thanks
N'ko

---

### Post by go_beep_yourself on 2010-03-18
Would someone make the initial commit to the Bazzar source code repository to get this application going? I created the repository and right now, any member can commit to it. It uses the bzr command. Some people are asking me how to contribute their work language translations. Right now anybody can commit. I may later change that to have a separate branch for patches to be committed that can merge into the main development branch.

---

### Post by jmdsdf on 2010-03-28
N'ko, I added Sample Rate to the extension. go_beep_yourself, I'd love to know how to commit with bzr (and how to build with dpkg-buildpackage so I can upload to a PPA). Sorry, I'm really still very new with this kind of thing. I used dh_make, but for some reason it's not including the one file I need to install. Oh well, I'm sure I'll figure it out in time. I built the deb again, but can't figure out how to upload to the team1 repo or push to a PPA. Hmm.

---

### Post by N'ko on 2010-04-02
> **jmdsdf said:**
> N'ko, I added Sample Rate to the extension. go_beep_yourself, I'd love to know how to commit with bzr (and how to build with dpkg-buildpackage so I can upload to a PPA). Sorry, I'm really still very new with this kind of thing. I used dh_make, but for some reason it's not including the one file I need to install. Oh well, I'm sure I'll figure it out in time. I built the deb again, but can't figure out how to upload to the team1 repo or push to a PPA. Hmm.

jmdsdf,

Thanks for the added Sample Rate support, it should be a big help.  We need to be able to see Sample Rate of Audio files before mass importing into Rivendell (radio automation).

One problem, I downloaded the newest version of the script today and it does not work for me.  The version I have from October 26, 2009 works fine but the new one, I am not able to select any new columns.  I am running Karmic.

Any help would be great

---

### Post by N'ko on 2010-04-03
> **N'ko said:**
> jmdsdf,

Thanks for the added Sample Rate support, it should be a big help.  We need to be able to see Sample Rate of Audio files before mass importing into Rivendell (radio automation).

One problem, I downloaded the newest version of the script today and it does not work for me.  The version I have from October 26, 2009 works fine but the new one, I am not able to select any new columns.  I am running Karmic.

Any help would be great

Opps! I didn't give the script permission to execute!  It is working great for me now.  Thanks again for the great script.

N'ko

---

### Post by l-x-l on 2010-04-10
Hello all... I just updated to the newest script. But I can't seem to get Genre, Track & Bitrate info for my FLAC files to appear. Wondering if anyone may have a quick answer. Thx.



Edit: Ok after some tinkering I was able to get fix my FLAC's missing track number by changing the following in the script from:
```

				try: file.add_string_attribute('track',info.trackno)
				except: file.add_string_attribute('track', '[n/a]')
```

to
```

				try: file.add_string_attribute('tracknumber',info.trackno)
				except: file.add_string_attribute('tracknumber', '[n/a]')
```


I was also able to fix my genre issues by going into /usr/share/pyshared/kaa/metadata/audio/flac.py and adding the following to the 'map' section:

```
u'GENRE': 'genre',
```


The FLAC bitrate issue still alludes me. Anyone know where can I find documentation on this stuff??

---

### Post by go_beep_yourself on 2010-04-13
The Launchpad project created for this has modify/upload new revision for any user that subscribes to Launchpad, so please upload the code, debs, translations, and modifications to the version control system they are using called Bazaar. 

[http://wiki.showmedo.com/index.php/Using_Launchpad_and_Bazaar](http://wiki.showmedo.com/index.php/Using_Launchpad_and_Bazaar)

---

### Post by jmdsdf on 2010-04-17
Thanks l-x-l, I'll fix that track number bug on my side as well.

---

### Post by tsixlas on 2010-05-03
worked like a charm in ubuntu 10.04. Very helpful script

---

### Post by wishingstar on 2010-05-21
Hi,

I just installed this script, gave it permission to execute (under  ~/.nautilus), when i run the command:

```
killall nautilus && nautilus
```

I get the following error:

```
Traceback (most recent call last):
  File "/home/yazan/.nautilus/python-extensions/bsc-v2.py", line 37, in  <module>
    import pyexiv2
ImportError: No module named pyexiv2
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net  usershare' returned error 255: net usershare: cannot open usershare  directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```

Please help!

---

### Post by mixmastamyk on 2010-05-22
> **geb666 said:**
> 
Remember that python uses tabs for defining scope, so if you copy and paste the script below then you'll have to replace the spaces with tabs.


A small correction, this isn't quite true.  Python doesn't care if you use tabs or spaces, just that each indentation level is consistent with the others.

---

### Post by ENigma885 on 2010-05-22
> **wishingstar said:**
> 
I get the following error:

```
Traceback (most recent call last):
  File "/home/yazan/.nautilus/python-extensions/bsc-v2.py", line 37, in  <module>
    import pyexiv2
ImportError: No module named pyexiv2
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net  usershare' returned error 255: net usershare: cannot open usershare  directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```

Please help!

Make sure that all dependencies are installed.
```
sudo apt-get install python-nautilus python-mutagen python-pyexiv2
```

**For a step by step installation, please refer to [COLOR="Red"]post #38[/COLOR] in this thread. (I will try to keep the script updated according to post #4 by jmdsdf until the deb packages are up to the Launchpad page)

---

### Post by UberStudent on 2010-05-27
Has anyone tailored this to work in only select folders?

---

### Post by SabreWolfy on 2010-05-28
Nautilus remembers the list/icon view per folder AFAIK. I therefore presume you mean that folder A shows list view without the extension whereas folder B shows list view with the extension? That would have to be specified in Nautilus, although in list view the extension would also be executed, so it would then have to suppress the additional columns. This is becoming quite complicated. I'm still surprised that this is not available by default in Nautilus. The equivalent application in a very popular commercial operating system allows for easy selection of a huge number of fields, including page number, word count, track length, title, etc.

---

### Post by UberStudent on 2010-05-28
Yes, you presume correctly. 

And I, too, am surprised this function has not been standard in Nautilus for years.  :-?

---

### Post by jmdsdf on 2010-05-30
Sorry if I sidetrack this discussion, but does anyone know of a script like this for KDE's Dolphin file manager?

---

### Post by brevardo on 2010-06-07
Figured it out!!! It is awesome!

---

### Post by therealbrewer on 2010-06-08
Can the script be adjusted so that I can sort by track number and not get this:

1
10
11
12
2
3
4
.
.
.

---

### Post by nosehat on 2010-06-16
Thanks for the awesome script!  This definitely makes Nautilus more usable for me.

For anyone having trouble getting this to work:

I spent a while trying different things to get this to work before I realized that **the full list of the dependencies is in the comments in the python file**:

```
sudo apt-get install python-nautilus python-mutagen python-pyexiv2 python-kaa-metadata
```

---

### Post by artemyv on 2010-06-26
> **go_beep_yourself said:**
> Would someone make the initial commit to the Bazzar source code repository to get this application going? I created the repository and right now, any member can commit to it. It uses the bzr command. Some people are asking me how to contribute their work language translations. Right now anybody can commit. I may later change that to have a separate branch for patches to be committed that can merge into the main development branch.


OK - I have played a little with bzr - and have uploaded the script from post 4 as revision 1

(version from UPLOAD 11)

As a revision 2 I have uploaded my tinkered version as suggestion:
1. Added format column for mp3 files like "Mpeg1 Layer3" (since I have several files in Mpeg1 layer1 format and want to distinguish them easily)
2. changes the adding of ID3 attributes code to use loops
3. replaced try/except approach for the loop with using if audio.has_key(x) checks
4. since the list has 9 keys and current version handles only 6 of them - I have added 3 more columns - as they go for free now (not that I'm thinking they are of any use really)

---

### Post by artemyv on 2010-06-26
> **therealbrewer said:**
> Can the script be adjusted so that I can sort by track number and not get this:

1
10
11
12
2
3
4
.
.
.

I have uploaded to bzr (at revision 4) the quick fix for this. (I modified only mp3 part - but it easily could be propagated to other file types as well). I'm adding space before single-digit track-numbers. This fixes the sorting order for me.

---

### Post by ricothebrol on 2010-07-05
Hi,

I'm pretty new to the Ubuntu/Linux environment, so please excuse me in advance if my question is stupid !

My problem is that I managed to have a display of the new optional columns (artist, album, ...) but when I check the boxes nothing happens ! I tried in both menus, "view" and "edit".

I ran the following command :
sudo apt-get install python-nautilus python-mutagen python-pyexiv2  python-kaa-metadata

I also have copied the      [bsc-v2.py]("http://ubuntuforums.org/attachment.php?attachmentid=153614&d=1271562286") file in those locations :
/home/julie/.nautilus/python-extensions
and
/usr/lib/nautilus/extensions-2.0/python

I must have done something wrong, but I have no idea what that could be (my total lack of knowledge concerning Ubuntu doesn't help...:redface:)

Thanx in advance.

Best regards.

---

### Post by artemyv on 2010-07-05
> **ricothebrol said:**
> Hi,

My problem is that I managed to have a display of the new optional columns (artist, album, ...) but when I check the boxes nothing happens ! I tried in both menus, "view" and "edit".


This sounds really strange to me - if you see new columns in the column list - it means that the script was working.

Are you sure you are using the list view in the nautilus? (Ctrl+2 or View -> List)
Columns should be added in this view only...

Could you add the "old" columns that are available without the script?

---

### Post by ricothebrol on 2010-07-06
Hi, 

Thanx for your answer !

Yes, when I chech/uncheck "file name" or "file type" (mine is in french so those translations might not be accurate) they appear/disappear, but that doesn't work for all the "new" columns.

I'm using Ubuntu 10.04.

---

### Post by ricothebrol on 2010-07-06
Might help : the Nautilus version I'm using is 2.30.1 (I didn't change it in any way)

---

### Post by artemyv on 2010-07-06
> **ricothebrol said:**
> Might help : the Nautilus version I'm using is 2.30.1 (I didn't change it in any way)

I'm using same version. And am here out of ideas... Hope somebody more expirienced with python could help...

Have you tried to change order of columns? Move say Bitrate column to be just after the Name?

---

### Post by ricothebrol on 2010-07-06
Hi ! I finally got it to work, with some help from a friend : the problemn was that the file was installed in two locations (/home/julie/.nautilus/python-extensions and /usr/lib/nautilus/extensions-2.0/python). I erased it in the second one and that was it !
Thanx anyway for getting interrested in my problem !
Best regards.
Eric

---

### Post by artemyv on 2010-07-07
glad it is working. Good luck.

As I said earlier  - slightly updated version of the script is posted here: [https://code.launchpad.net/~team1](https://code.launchpad.net/~team1)

---

### Post by pyrokamileon on 2010-07-21
I couldn't get this to work for me, I'm running Debian Lenny and my installed Nautilus version is 2.20.  I tried putting the file in a couple different locations, only one location at a time (and I did chmod a+x it) and then I'd logout/login and I still would only have the usual column offerings.  my extensions directory is a 1.0 by the way, that's where Synaptic put my clamscan.py so I figured that would be a good place for bsc-v2.py but it didn't work there either...  does anyone know how to make it work in Debian?

---

### Post by Milind on 2010-07-21
I can't get this to work. I followed the instructions in post #38 on page 4 of this thread. I now have files bsc-v2.py & bsc-v2.pyc in the python-extensions subfolder in .nautilus. I've killed and restarted Nautilus, logged out and logged back in but there are no new columns in the list in the 'Preferences -> List Columns'. Any suggestions ? If I can't get this to work I would at least like to know how to reverse the changes I've made to my system. Thanks in advance.

---

### Post by miscontime on 2010-07-23
hello,

I have a problem with the bsc-v2, it would be great if you could help me!!
after a few first problems I read the whole thread and made the script run (on 10.04). as I registered that the columns have to be activated every time I started nautilus (is that a bug?) I tried to find the fault and cleared the python-extensions folder, then rebooted and looked to the usr/lib/nautilus/extension-2.0 folder - maybe I could have installed it in this folder too. so there I found a bsc.pyc file which I deleted. after that I tried to install it again, exactly in the way it is described in post 38 on page 4. unfortunately the installed prog didn't work out, the columns don't even show up in the Edit | Preferences | List columns window. 
Thanks for all hints!

---

### Post by miscontime on 2010-07-24
I found the solution! Sorry for the post above, the problem was missing python-kaa-metadata because of stupid apt-get autoremove. Thanks a lot for the script!!!

---

### Post by MichaelGld on 2010-07-24
How do you do this part of the instructions?




[SIZE=4][B]> **geb666 said:**
> ...  You might have to add the python-nautilus library path to the PYTHONPATH variable. 
[/B][/SIZE]> **geb666 said:**
>  



```
import os
import urllib
import nautilus
from mutagen.easyid3 import EasyID3
from mutagen.mp3 import MPEGInfo

class ColumnExtension(nautilus.ColumnProvider, nautilus.InfoProvider):
        def __init__(self):
                pass

        def get_columns(self):
                return (nautilus.Column("NautilusPython::title_column",
                                "title",
                                "Title",
                                "Song title"),
                nautilus.Column("NautilusPython::album_column",
                                "album",
                                "Album",
                                "Album"),
                nautilus.Column("NautilusPython::artist_column",
                                "artist",
                                "Artist",
                                "Artist"),
                nautilus.Column("NautilusPython::bitrate_column",
                                "bitrate",
                                "Bitrate",
                                "Bitrate"),)

        def update_file_info(self, file):
                if file.get_uri_scheme() != 'file':
                        return
                if file.is_mime_type('audio/mpeg'):
                        filename = urllib.unquote(file.get_uri()[7:])
                        audio = EasyID3(filename)

                if (os.path.isfile (filename)):
                        mpfile = open (filename)
                        mpinfo = MPEGInfo (mpfile)
                        br = str(mpinfo.bitrate/1000) + " Kbps"
                else:
                        br = ""

                file.add_string_attribute('title', audio["title"][0])
                file.add_string_attribute('album', audio["album"][0])
                file.add_string_attribute('artist', audio["artist"][0])
                file.add_string_attribute('bitrate', br)
                self.get_columns()
```

---

### Post by /bee/ on 2010-08-04
I wouldn't get into that until you follow the directions in post #38:

[http://ubuntuforums.org/showpost.php?p=7931669&postcount=38](http://ubuntuforums.org/showpost.php?p=7931669&postcount=38)

Thank you guys for your work on this, it had been killing me.  Any word on if V0-V9 VBR will ever get some love?

---

### Post by SabreWolfy on 2010-08-18
Where can I find the Debian package?

---

### Post by SabreWolfy on 2010-08-18
> **miscontime said:**
> I found the solution! Sorry for the post above, the problem was missing python-kaa-metadata because of stupid apt-get autoremove. Thanks a lot for the script!!!

Confirmed. I followed the instructions in Post #38, but the plugin did not work until I installed python-kaa-metadata; this should be added to Post #38.

---

### Post by normanp on 2010-10-10
Is his all in a deb package now? If so where can it be obtained?
Thanks

---

### Post by suoko on 2010-10-14
ouch, can't find the deb on ppa team1 !
by the way, i tried the manual procedure on maverick with no success.
any hints ?
i need it to copy scattered mp3s to phone since rhythmbox copy is unable to paste in nautilus and my microsd doesn't show up in rhythmbox folders

---

### Post by mastermindg on 2010-11-09
Check out this post, it has the deb file:

[Link]("http://www.webupd8.org/2010/01/mp3-and-flac-metadata-information-id3.html")

---

### Post by tg3793 on 2010-11-19
I often wonder about duplication of efforts. And in the interest of pointing friends of mine to the best solution, could someone tell me if they have tried both the solution in this thread and also the solution on [this site]("http://www.webupd8.org/2010/10/music-and-exif-metadata-information-in.html"). I would like to know the pros and cons of each solution ... again, only if you happen to have tried the other one as well.

The link above mentions a download called "nautilus-columns" which I went ahead and  implemented on my own machine and am now recommended to others as well. And just in case that site ever goes away I've also [copied the story here]("http://techsupporttv.wordpress.com/2010/11/17/add-mp3-wav-and-exif-columns-to-your-nautilus-view/")  (and given full credit to the originator).

Thanks and I hope to continue to give back to this community. Although I've been dabbling in Linux off and on for years, it wasn't until this past month that I jumped neck deep into the Ubuntu :-)

---

### Post by Micha401 on 2011-01-02
Just stumbled upon and installed. Works like a charm in Maverick amd64.
Thank you!

---

### Post by DraXus on 2011-01-05
Hello!

I've modified the script to add support for PDFs. You can take a look here: [http://pastebin.com/WxspTtvL](http://pastebin.com/WxspTtvL)

Thank you!

Edit: you will need pyPdf lib (python-pypdf package)

---

### Post by Jack Brown on 2011-01-11
Yep new year and it still works! :)

For people who skipped everything up to this post, just download the **python script on post #4** (page1) by jmdsdf, instructions inside.  (adds column fields to nautilus for mp3, photos, videos) and extendable for others.

(basically install dependencies, put the python in specific folder, change permissions, restart nautilus)

Great job guys, what a team Effort.

---

### Post by marco_ask on 2011-01-15
Hi,
I've installed the latest script, but I can't see some other EXIF info for jpg file. I mean, I would ask if there is a way to show also other exif information like **Exposure Time**, **Aperture**, etc. etc.
TIA
I'm going crazy trying to view this info!

---

### Post by SabreWolfy on 2011-01-16
> **marco_ask said:**
> Hi,
I've installed the latest script, but I can't see some other EXIF info for jpg file. I mean, I would ask if there is a way to show also other exif information like **Exposure Time**, **Aperture**, etc. etc.
TIA
I'm going crazy trying to view this info!

I assisted briefly with this plugin many months ago, with displaying some of the audio data. If the data you require is stored in the file and is available via whichever Python module is extracting these data from the file, it should be easy to add to the code to display what you want.

---

### Post by marco_ask on 2011-01-19
> **SabreWolfy said:**
> I assisted briefly with this plugin many months ago, with displaying some of the audio data. If the data you require is stored in the file and is available via whichever Python module is extracting these data from the file, it should be easy to add to the code to display what you want.
These attributes are specific for jpg file.
My goal was to order some file in a folder by these attribute.
I achieved my goal with a simple program called "MaPiVi".
Thanks anyway for your interest

---

### Post by marco_ask on 2011-01-19
> **SabreWolfy said:**
> I assisted briefly with this plugin many months ago, with displaying some of the audio data. If the data you require is stored in the file and is available via whichever Python module is extracting these data from the file, it should be easy to add to the code to display what you want.
These attributes are specific for jpg file.
My goal was to order some file in a folder by these attribute.
I achieved my goal with a simple program called "MaPiVi".
Thanks anyway for your interest

---

### Post by marco_ask on 2011-01-19
> **SabreWolfy said:**
> I assisted briefly with this plugin many months ago, with displaying some of the audio data. If the data you require is stored in the file and is available via whichever Python module is extracting these data from the file, it should be easy to add to the code to display what you want.
These attributes are specific for jpg file.
My goal was to order some file in a folder by these attribute.
I achieved my goal with a simple program called "MaPiVi".
Thanks anyway for your interest

---

### Post by jmdsdf on 2011-01-23
Thanks DraXus. I've updated my original post with your PDF support and expanded the error handling routines when importing the libraries with your idea. I've also found that I can throw the deb into a zip and have it available for download. I also saw Artemy's branch, and pulled the MPEG format and track formatting (but not the rest). I'll update the download here at some point in the future.

[http://ubuntuforums.org/showthread.php?p=6643803](http://ubuntuforums.org/showthread.php?p=6643803)

For some reason, importing the PIL Image library is throwing an error when I run it from Nautilus (but works fine from other Python scripts). If anyone knows of a solution or sees this bug as well, please post.

> **DraXus said:**
> Hello! I've modified the script to add support for PDFs. You can take a look here: [http://pastebin.com/WxspTtvL](http://pastebin.com/WxspTtvL)

---

### Post by caprilo on 2011-01-27
Its works for mp3's. Is there any way to adapt this script to include ogg and flac?

---

### Post by SabreWolfy on 2011-02-09
> **caprilo said:**
> Its works for mp3's. Is there any way to adapt this script to include ogg and flac?

The python-mutagen module which is used supports other formats, so it should be possible.

---

### Post by craigmcfly on 2011-06-19
Are there any plans to update the script for nautilus 3? It's a great plugin and it would be fantastic if it could continue in 3.

---

### Post by SuperGrouper on 2011-09-08
This script is wonderful- exactly what I needed!  Thanks. :D

---

### Post by kinggo on 2011-11-20
> **craigmcfly said:**
> Are there any plans to update the script for nautilus 3? It's a great plugin and it would be fantastic if it could continue in 3.
+1 for this
I really miss this :(

---

### Post by fullscr33n on 2011-11-20
+1 

yeah this would be great to have

---

### Post by starplex on 2011-11-28
+1
Keep going back to windows just for this feature (Total Commander Ultima Prime displays metadata)

---

### Post by starplex on 2011-12-14
I rewrote part of the script for Ubuntu 11.10. Displays bitrate, length and some chosen ID3 tags (artist, album, track name) ONLY for MP3 and FLAC(WAV). Works like a charm in Nautilus 3. You'll need python-mutagen & python-kaa-metadata. I use [http://www.giuspen.com/nautilus-pyextensions/](http://www.giuspen.com/nautilus-pyextensions/) to manage nautilus python scripts.

I will try to add the other stuff from the original script.

This is my first every python script/program so be gentle :)

---

### Post by e-i-k-e on 2012-01-02
> **starplex said:**
> I rewrote part of the script for Ubuntu 11.10. Displays bitrate, length and some chosen ID3 tags (artist, album, track name) ONLY for MP3 and FLAC(WAV). Works like a charm in Nautilus 3. You'll need python-mutagen & python-kaa-metadata. I use [http://www.giuspen.com/nautilus-pyextensions/](http://www.giuspen.com/nautilus-pyextensions/) to manage nautilus python scripts.

I will try to add the other stuff from the original script.

This is my first every python script/program so be gentle :)

i'm using nautilus 3.2.1 with ubuntu 11.10 64bit. your version doesn't work for me. i'm unable to start nautilus and this is the error:


```
TypeError: metaclass conflict: the metaclass of a derived class must be a (non-strict) subclass of the metaclasses of all its bases
Speicherzugriffsfehler
```

Speicherzugrifffehler should be something like "segmentation fault" in english.



edit @ Mo 2. Jan 17:36:13 CET 2012:
running the script alone produces this error:
```
python bsc-v2.py
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
```

---

### Post by tjajab on 2012-01-15
Seems to be python-kaa-metadata that is the problem. I do not know much about python, but part of the problem is explained here: [http://blog.rabbitvcs.org/archives/312](http://blog.rabbitvcs.org/archives/312)

For now, it should work with mp3 if you comment out the kaa import and the whole flac part (I've attached such a version).

python-mutagen has support for flac, ogg, wav etc, so I guess it should work to use that instead.

**Complete instructions for Ubuntu 11.10 (only mp3 support):**
Create folders so that the path ~/.local/share/nautilus-python/extensions exists.
Place the (updated) script there.
Install python-nautilus and python-mutagen:
```
sudo apt-get install python-nautilus python-mutagen
```

Good luck.

---

### Post by lcreed on 2012-01-17
I'm trying to cheat and get some kind of system where my ratings stick between iTunes and some media player in Ubuntu 11.10.  Right now I rate the songs on the ipod, syne to iTunes and then modify the "Sort Composer" field with a number corresponding to the number of stars.  Now I'm trying to figure out a way to view that Sort Composer field in uBuntu so I can rate the songs in Banshee or whatever and it will hopefully write to the ID3 tag.  Presumably the other media players won't recognize these ratings.

Anyone know of a way to do what I want to do or how to mod this script so that it includes a "Sort Composer" column which for all I know is iTunes specific?

---

### Post by e-i-k-e on 2012-01-21
@tjajab: your version fits my needs. thank you so much!

---

### Post by dez93_2000 on 2012-04-17
@tjajab - shame there's a button to report abuse but not one to report "user is awesome". Thanks for this, *finally* looking how I want it to!

---

### Post by ElijahLynn on 2012-05-04
With the help of Trism in #ubuntu on Freenode I updated V5 ([http://bazaar.launchpad.net/~team1/+junk/devel/revision/5](http://bazaar.launchpad.net/~team1/+junk/devel/revision/5)) of the script on Launchpad to support 12.04 and Nautilus 3.4.1. I have a LP account but don't know how to commit it to [https://code.launchpad.net/~team1/+junk/devel](https://code.launchpad.net/~team1/+junk/devel), if someone can that would be great.

See attached, oh btw the new location for the file should be ./local/share/nautilus-python/extensions, I changed the documentation to reflect this.

---

### Post by nodjoim on 2012-06-02
"You might have to add the python-nautilus library path to the PYTHONPATH variable"

How do I do that?

---

### Post by SabreWolfy on 2012-06-02
> **nodjoim said:**
> "You might have to add the python-nautilus library path to the PYTHONPATH variable"

How do I do that?

Look [here]("https://www.google.com/search?q=add+to+pythonpath+variable") or [here]("http://stackoverflow.com/questions/3402168/permanently-add-a-directory-to-pythonpath") as a starting point.

---

### Post by nodjoim on 2012-06-02
This works! Thanks!

---

### Post by cehlgn on 2012-06-07
Added in MP4, M4A - ALAC Apple Lossless file support.

[http://bazaar.launchpad.net/~team1/+junk/devel/download/grnsrv%40rocketmail.com-20120607181124-91s44i0a322kpk3p/bscv2.py-20100626134041-qcgfprsb49x7mnzd-1/bsc-v2.py]("http://bazaar.launchpad.net/%7Eteam1/+junk/devel/download/grnsrv%40rocketmail.com-20120607181124-91s44i0a322kpk3p/bscv2.py-20100626134041-qcgfprsb49x7mnzd-1/bsc-v2.py")

---

### Post by Luke3535 on 2012-07-09
Hi,
I'm an Ubuntu beginner, and I would appreciate some kind help getting this solution to work. It's just what I need to view programs for an Internet radio station that I'm working on.

When I download the zip file from post #4, extract the deb file, and double click on it, I get:

[INDENT]Package Installer - nautilus-columns[/INDENT]
[INDENT]Error: Wrong architecture 'amd64'[/INDENT]

What do I need to do to install this?

I believe that I have a 32 bit installation, based on some Googling I did last week.

Thanks,

Luke

---

### Post by ElijahLynn on 2012-07-11
> **Luke3535 said:**
> Hi,
I'm an Ubuntu beginner, and I would appreciate some kind help getting this solution to work. It's just what I need to view programs for an Internet radio station that I'm working on.

When I download the zip file from post #4, extract the deb file, and double click on it, I get:

[INDENT]Package Installer - nautilus-columns[/INDENT]
[INDENT]Error: Wrong architecture 'amd64'[/INDENT]

What do I need to do to install this?

I believe that I have a 32 bit installation, based on some Googling I did last week.

Thanks,

Luke

Luke,

I feel you! Assuming you are using latest Ubuntu and Nautilus:

First you need to download the file from #132 or #136, then place it in the ~/.local/share/nautilus-python/extensions folder. ~ means your home folder then within the home folder you want to find the .local folder, it is hidden by default, you can show hidden files with ctrl+h. Then navigate to the folder and place the file there. If the folder path stops at some point you will need to manually create the folders and nautilus will know to look there, it is built in.

Then to test it open a terminal and type "killall nautilus" and then super+1 to relaunch nautilus.

It is worth noting that this extension is super bloated and makes nautilus take 5 seconds to boot up, but it is just once so it should be okay. I am in the process of stripping out everything I don't need so it is fast, it bugs me.

---

### Post by altoaguila on 2013-04-07
I agree, a really useful extension for sorting out all those podcasts where you don't know which is which! Bravo, but it does slow Nautilus launch, why is it not part of Nautilus I wonder....??

---

### Post by jimingkui on 2013-04-11
How to get it work in Ubuntu 13.04 with Nautilus 3.6.x?. I installed python-nautilus, python-mutagen python-pyexiv2 python-kaa-metadata.  Downloaded and put the script under ~/.local/share/nautilus-python/extensions/, and gave the executable permission. But there's no change in Nautilus Preferences -> List Columns after restart Nautilus.

Does the script work with Nautilus 3.6.x or higher?

Thanks!

---

### Post by hg088 on 2013-05-22
> **jimingkui said:**
> How to get it work in Ubuntu 13.04 with Nautilus 3.6.x?. I installed python-nautilus, python-mutagen python-pyexiv2 python-kaa-metadata.  Downloaded and put the script under ~/.local/share/nautilus-python/extensions/, and gave the executable permission. But there's no change in Nautilus Preferences -> List Columns after restart Nautilus.

Does the script work with Nautilus 3.6.x or higher?

Thanks!

Bump anyone?

---

### Post by mc4man on 2013-05-23
> **hg088 said:**
> Bump anyone?
Last I tried some nautilus-python extensions in 13.04, nautilus-python itself showed issue, so none would run of those attempted. (inc. [the example extensions ]("https://bugs.launchpad.net/ubuntu/+source/nautilus-python/+bug/1141063")in the package.
(it was a while ago that tried..

---

### Post by hg088 on 2013-05-23
> **mc4man said:**
> Last I tried some nautilus-python extensions in 13.04, nautilus-python itself showed issue, so none would run of those attempted. (inc. [the example extensions ]("https://bugs.launchpad.net/ubuntu/+source/nautilus-python/+bug/1141063")in the package.
(it was a while ago that tried..
Mm ye you're right, and apparently it's a confirmed bug and all: [https://bugs.launchpad.net/arronax/+bug/1174109](https://bugs.launchpad.net/arronax/+bug/1174109)

---

### Post by mc4man on 2013-05-26
upstream bug - 
[https://bugzilla.gnome.org/show_bug.cgi?id=698214](https://bugzilla.gnome.org/show_bug.cgi?id=698214) 
LP- [https://bugs.launchpad.net/ubuntu/+source/nautilus-python/+bug/1170017](https://bugs.launchpad.net/ubuntu/+source/nautilus-python/+bug/1170017)


Checking the filelist in the 32 bit libpython2.7 shows this so 32 bit may also be affected - 
/usr/lib/i386-linux-gnu/libpython2.7.so.1.0

---

### Post by mc4man on 2013-05-29
Well a fix was applied in 13.10 that fixes amd64 installs but some tests here show i386 also affected. 
 Suggestions to ck. that[ in the report were ignored]("https://bugs.launchpad.net/ubuntu/+source/nautilus-python/+bug/1170017") so went ahead & modified my orig. patch to allow  extensions to load for both archs in 13.04 & placed in a ppa. (amd64 done,  i386 queued
[https://launchpad.net/~mc3man/+archive/n-p-testfix](https://launchpad.net/~mc3man/+archive/n-p-testfix)

---

### Post by benawhile on 2013-08-14
Hi
I successfully added the columns nautilus extension according to the 12.04 webupd8 page. Now I have an "artist" column for my mp3s, which helps quite a lot. But what I really want is to display the "comments" column. I use this to insert my own date code, the date I created the mp3, (I create a lot of mp3 in Audacity) and it makes sorting easier. I used this column in windows all the time. Does anyone know if I can get Nautilus to display the "comments" column?

I have Ubuntu 12.04

---

### Post by alan-pater on 2013-11-28
Is bsc-v2.py still actively working on? I installed the version  packaged on [WebUpd8]("http://www.webupd8.org/2012/05/add-pdf-audio-and-exif-metadata-to.html") and it is working as expected. My problem is that I  am looking to add DwC metadata support and am not sure how to go about  doing that. 

One problem is that exiv2 does not support DwC.  Exiftool does but it looks difficult (at least for me!) to change bsc-v2.py to use  exiftool. 
PyExifTool is available here: [http://smarnach.github.io/pyexiftool/ ]("http://smarnach.github.io/pyexiftool/")

Could anyone provide some hints on using pyexiftool in bsc-v2.py?

Note: Darwin Core (DwC) is a XMP metadata standard used for sharing biodiversity information. I am working on getting this added to various tools to allow researchers in the field to easily add and edit DwC metadata to their images, such as those captured with camera traps.

---

