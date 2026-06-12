---
title: "10 ways to improve performance (for beginners)"
date: 2011-02-08
forum: Outdated Tutorials &amp; Tips
---

### Post by birkopf on 2011-02-08
I will be developing this small tutorial with time. If you have a suggestion - send me private message. 

##################################
#** IMPROVING UBUNTU PERFORMANCE** #
##################################


**1. From time to time remove unnecessary files**

In the home folder press "Ctrl + H" which will show you all hidden files. Remove catalogs and files from programs that you are not longer using (for example you were using Gimp, but you removed it months ago). Always remove to bin and leave it for few days just in case. DON'T remove file/folder if you don't know what is. means it's important :-)



**2. Every now and than remove old headers**

First go to Synaptic, Click Reload. Next click Mark all Upgrades. click Apply. After installs are finished you might need to restart.
 
After that run in terminal:
```

uname -a

```
It will return you something like:
```

Linux ubuntu 2.6.35-23-generic

```
This is your current header. Note it carefully! Go to Synaptic. In search window write

header

It will give you currently installed headers. Mark for removal all headers EXCEPT of you current one and last newest header. In this case 2.6.35-23 stays as current and 2.6.35-22 stays as last used before current.  


 
**3. Use cleaning programs**

Programs listed below are popular and remove old, unused, orphaned, leftover files from disk. They are easy to use and should be used with CAUTION and backup! If you have problems operating them - google for manuals.
```
 
- Bleech it 
- Computer Janitor   
- 2click Update
- Gconf Cleaner
- gtkorphan

```

For duplicated files you can use:
```

Binstats
Fdupes
Fslint

```




**4. Tar everything or at least what you can...**

Some people are keeping millions of files like photos, mp3 with random numbers in random places. Sort out your files into main folders like Music, Pictures, Programs, Documents, E-books, etc. Create sub categories in those main folders for example Pictures -> Holiday 2010. Move all your pictures from holiday time into categories like for example June 2010, July 2010. Once all is sorted go into June 2010 where all pictures are, press "Crtl + A" (selects all files in folder). right click on them and choose "Compress". Use tar.gz as it's fastest. Once compressed - remove picture files = you have them in compressed archive. Keeping in archives will limit number of files. Not necessarily for the system (hdd), but when you enter folder which has 29.000 pictures they all start to buffer... When you enter folder which has 1 tar archive it doesn't ;-) Always try to split vast amounts of file into folders which will contain max 200-300 and tar them. Easy to search and un-compress.        




**5. Replace sluggish programs** 

Some default programs after time are not enough. You can replace Firefox with Chromium. Apparently it's faster. My opinion is - it takes less RAM and is as fast as Firefox so I use it... properly configured! 
Replace Rhythmbox with Banshee, Evolution with Claws-Mail. I always replace Brasero with GnomeBaker as the first works on my nerves. Gwibber can be replaced with Hotot which is faster and better and doesn't load with system. If you like them after time - remove default programs.   

Additional - Visit options for most commonly used (by you) programs and look for options to clean cache. Once a month is fine. 




**6. Synaptic**

In synaptic always first click "Reload". On left choose "Status". You will see above it "Not installed (Residual Config)" Once a month go to Residual Config, choose all packages, right click them. Select Mark for Complete Removal and click "Apply" button. 
Synaptic keeps history of installs/uninstalls in case you will need to come back to it. Check the history once a month. If you have installed programs from sources most likely they had dependencies which you installed as well. History in Synaptic will show it all. If you removed programs you can remove dependencies as well. 


I have stopped using terminal and apt-get for cleaning because it doesn't keep history... or it keeps somewhere, but I'm lazy and like visual side by Synaptic. In case you want to use commands, run those ones from time to time:

```

sudo apt-get clean

sudo apt-get autoclean

sudo apt-get autoremove

```




**7. Control startup**

System -> Preferences -> Startup Applications

Un-click everything that you don't want to load at the start of system. For example if your computer doesn't have Bluetooth - un-click it. Button "Close" will remember configuration. The less programs starting with system you have the better, but don't turn off systemic ones. 




**8. Remove programs you will never use**

I know I will never use Remote Desktop Access and for example Games in Ubuntu so the first thing I do after installing fresh system is to remove all I am not interested in.




**9. Remove old e-mails and cahe**

You program probably keeps tons of old emails. Visit all your folders and remove what's unnecessary. Most programs after that should be archived = backup important emails should be done. General rule is to remove all clutter that is old. If it's  likely you'll need it - TAR, Tar and Tar :-D 

Your media player as well as ubuntu keeps in hidden folders in your /home mases of small thumbnails of opened documents like for example pictures, or miniatures of played CD. You can clean that from time to time.  



**10. Re-compress your mp3**

If you have a small disk and have lot's of mp3 they are probably compressed to different standard. You can use programs like "SoundConverter" which will allow you to take you mp3 which is for example 320kbps and re-compress it to 192kbps (standard good quality) or 128kbps (standard medium quality). Remember to use it first as a test. After that you can use it with option "Remove Source File" which is your ultimate goal. To be able to re-compress you mp3 you will need to install "lame" most probably from Medibuntu. Both can be found after net search. SoundConventer has also extensive help.   




**11. System menu**

In you System menu you have few interesting options to optimize memory usage. System -> Preferences -> Appearance will let you turn off additional visual effects, which will slightly improve performance.




**12. Removed**

As few more experienced users pointed out - this point was not necessary.   



[B]Rest will come... 

REMEMBER that you are cleaning your computer at your own responsibility and if you don't know what you are doing - DON'T DO IT[/B] ):P

---

### Post by Zuben El Genubi on 2011-02-08
Looks good. Now is there a sticky anywhere defining terms? An Android forum has a list "What are they talking about" for new users. That would be what I'm looking for.
Thanks

---

### Post by dino99 on 2011-02-08
you might post on the good subforum, not here

---

### Post by mcduck on 2011-02-08
Nice guide, although only steps 5 & 7 (and perhaps 3, depends on what exactly you do with those tools) have any effect on *performance*, the rest will just free some hard drive space... ;)

Good tips for new users anyway. :)

---

### Post by Bucky Ball on 2011-02-08
Mods, should be in 'tutorials' forum as is a 'how to'. 

Compressing audio files is really not a goer for anyone who bothers to have audio files better than 192kbps. Between 320-192kbps there is an audible difference. 320-128 very. I wouldn't go there and stick to FLAC when possible. But that's me.

In point 2, could you not also remove the previous images?

Point 3, maybe also consider:

```
sudo apt-get clean
sudo apt-get autoclean
```

Point 4; as your images are probably already compressed, when compressed further (having yet more air squeezed out) would this not effect quality when recompressed? The information would have been squeezed out ... the same may apply to audio. Curious if that is the case.

;)

---

### Post by mcduck on 2011-02-08
> **Bucky Ball said:**
> 
Point 4; as your images are probably already compressed, when compressed further (having yet more air squeezed out) would this not effect quality when recompressed? The information would have been squeezed out ... the same may apply to audio. Curious if that is the case.

;)
Zip, gzip and similar are lossless compression formats (how could you zip actual data files and programs if they weren't... :D)

On the other hand most people have JPG photos, which are already compressed, so there's hardly any data zipping could squeeze out of them. Actually in worst case your JPG images end taking *more* space in archive format...

Compressed data doesn't compress well. Especially if the original compression is already more efficient than what a lossless compression can be. So in the same way gzipping movie files, compressed audio formats and other such things is usually just a waste of time.

---

### Post by Bucky Ball on 2011-02-08
> **mcduck said:**
> Zip, gzip and similar are lossless compression formats (how could you zip actual data files and programs if they weren't... :D)

Not referring to data files and programs. Thanks for the other info. ;)

---

### Post by cascade9 on 2011-02-08
If you really want to speed up ubuntu then a minimal install then adding whatever DE you want is the way to go IMO (but that might not be for beginners, depends on the person). Moving to Xfce4, lxde or openbox would give also give you a major performance increase over standard ubuntu, with virtually no effort. 

Also, make sure that your install is as close to the 1st sector of the HDD as possible. HDDs are faster at the begining of the drive, slower toward the end of the drive. 

> **Bucky Ball said:**
> Compressing audio files is really not a goer for anyone who bothers to have audio files better than 192kbps. Between 320-192kbps there is an audible difference. 320-128 very. I wouldn't go there and stick to FLAC when possible. But that's me.

+1. IIRC .flac used about the same amount of CPU power to decode as MP3. (depending on your decoder, media player and the MP3 options.) . 

> **mcduck said:**
> Nice guide, although only steps 5 & 7 (and perhaps 3, depends on what exactly you do with those tools) have any effect on *performance*, the rest will just free some hard drive space... ;)

Good tips for new users anyway. :)

+1 . Also +1 on your post on data compression ;)

---

### Post by vanadium on 2011-02-08
Indeed, few of these are performance tips indeed. Most of them will allow you to reclaim a few GB disk space. Usually, this is not an issue, however.


3. Use cleaning programs probably is nice for a Windows machine. We fleed away from these for some reasons. The only benefit is, again, a bit of disk space, but left in the hands of beginning users, these programs might break some applications.

5. Replace sluggish programs: This will be useful and noticeable for slower machines. But then, consistency requires you to also switch gnome or KDE for lighter desktops.

8. Remove programs you will never use: not an ideal tip for beginners, because it will remove the ubuntu-desktop metapackage. Not sure it this is a major problem, but at least it may disturb distro-upgrading.

10. Re-compress your mp3
The tip to re-compress mp3's indeed should be removed all together, because it is bad advice. Transcoding lossy audio files to the same lossy format will cause further quality loss. The only valid option to improve space efficiency is to rerip and encode with settings that meet the required quality and are space efficient.

Storage space for audio, however, is not an issue. Ripping to flac is indeed the better option, after which the audio can be transcoded if needed to take on the road.

12. is written in a rather convoluted way for beginners. I don't follow (but then, I might be a beginner).

---

### Post by mcduck on 2011-02-08
> **vanadium said:**
> 
12. is written in a rather convoluted way for beginners. I don't follow (but then, I might be a beginner).
Actually it's just nonsense. 

Having swap space available doesn't mean that it would be used. The kernel will use swap if it needs to, not just because it's there. :D

So larger swap partition will, at worst, waste a bit of your hard drive space.

---

### Post by gordintoronto on 2011-02-08
I also disagree with #10 and #12.

Then again, I rip CDs to flac format so there is no loss of quality.

---

