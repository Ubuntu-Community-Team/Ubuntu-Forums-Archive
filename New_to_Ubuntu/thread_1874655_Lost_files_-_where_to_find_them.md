---
title: "Lost files - where to find them?"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by zcacogp on 2011-11-03
Hello, 

I have just tried playing around with Enlightenment, and was wondering why my drives which are usually available in Unity weren't on the desktop. I found them under 'root' and dragged and dropped them onto the desktop. 

It seemed to start copying the entire contents of the drives to the desktop, but failed when it got to 'Lost and Found'. I cancelled the processed, but have now discovered that I seem to have lost some things from those drives. 

Enlightenment doesn't seem to have a trash bin of any kind, and I don't know where to find the things which I seem to have lost. Where should I start looking? 

(Yes, I know this sounds like a very stupid question, and I think I have just done something enormously dumb ... and would really value any help you can give - thanks!) 


Oli.

---

### Post by zcacogp on 2011-11-03
Update: I have run Nautilus from the terminal in Enlightenment and looked in the rubbish bin there, and the lost items aren't in there. 

Thanks, in advance, for any help. 


Oli.

---

### Post by decoherence on 2011-11-03
If the drive is not the one that contains your home folder (where you desktop folder lives), then it will copy the data. If the drive is the same one that contains your home it will try to move the files and fail on a permission denied error when trying to move a system file you can't erase (unless it asked for a password and you gave it one, in which case it might've created some kind of interdimensional rip in the spacetime continuum.)

I'm not really sure. Hard to say for certain without testing for myself which I'm kind of reluctant to do

Your best bet would be to go back to Unity and try to recover from there.

If you know how to use the command line, that would be the best place to see what's going on, but it's hard to give directions without knowing more about your system (how many drives, which did you copy, what was the directory structure before, what's missing, etc.)

Drives are typically mounted in /media.

Also, as you've discovered, Enlightenment works pretty differently than the desktop environments you typically see on Ubuntu (XFCE, KDE, GNOME). Have a look at this: [http://en.wikibooks.org/wiki/The_Unofficial_Enlightenment_User's_Manual](http://en.wikibooks.org/wiki/The_Unofficial_Enlightenment_User's_Manual)

---

### Post by zcacogp on 2011-11-03
Decoherence, 

Thanks for your answer. I feel like a complete numpty (hence my posting the Q in Absolute Beginner Talk) as I have been using Ubuntu for a while and make a mistake like this ... 

The machine has four drives. (Actually they are all partitions on the same HDD, but I'm guessing that's immaterial). There is the system drive (ext4), Ianthe (ext4), Helena (ext4) and Pharmacy (ntfs). 

I'm used to Gnome, and don't like Unity (I chose to use Gnome in 11.04) so thought I'd give Enlightenment a try in 11.10. Installed it, logged into it, looked for my usual drives (Ianthe, Helena and Pharmacy) and could only find them in "Root" (it seemed to open a file manager of sorts, and I could navigate down to /media), and thought I would drag them from there to the desktop. Simple left-click drag and drop, and it errored on "Lost and Found". It was only later that I noticed that some directories were missing from the drives in question, and am assuming this is when they went astray. 

Having done some googling I have found some file recovery tools (photorec), and am using them and they seem to be getting most of the lost files back, but not all of them. And the metadata is all awry, and the directory structure is lost. So, a Class 1 nuisance, but not the end of the world. 

Is there any way of getting them *ALL *back, *WITH* the Metadata *AND *directory structure? Or should I be grateful for what I have managed to recover? 

Thanks - again - for your reply. 


Oli.

---

### Post by WasMeHere on 2011-11-03
Hi Oli,

I have not used Enlightenment, but since you left-dragged-and-dropped your folders, I would also assume it had copied (not moved) the files across partitions (as *decoherence* did). Anyway, there is a fair chance that what was moved from the old place should be found in the new place. ***Can you identify the desktop of Enlightenment?*** I mean its name in the file structure. Maybe the same as that of Unity, so that you can open a terminal window and change directory.
```
cd ~/Desktop
``` with UPPERCASE D. Then list the files with **ls** or **ls -l**

You can also use **find** to look for a file with a known name (or known extension).
```
sudo find / -name 'this-file-name.ext'   # or
sudo find / -name '*.jpg'
```
Otherwise, if your files were deleted without being transferred, PhotoRec is a good tool, but not convenient for a large number of files.

Have fun finding out :-)
Olle

---

### Post by zcacogp on 2011-11-04
Chaps, 

Thanks for the answers. I think I have most of the data back. In fact, pretty much all of it - much of it was on a backup I made, but not a complete backup unfortunately. PhotoRec was good at getting the rest, but messy - I have lost a lot of metadata, and the original filenames, but those may be recoverable from the EXIF data. 

I don't know where the data went to. That is perhaps the most worrying thing. It isn't (and wasn't) on the desktop, and isn't in any of the .trash folders anywhere. I can't find it with a search and it seems to have just gone. The HDD it was on is new (within the last 6 weeks), and replaced an old and failing one. I am starting to wonder whether the old HDD really was failing or whether the PSU is actually causing problems, and have ordered a replacement one of those as well. 

Many thanks for your help in getting the data back. It's appreciated. I guess the worrying aspect is how long it will stay back for. Now that is genuinely concerning ... 


Oli.

---

### Post by WasMeHere on 2011-11-04
Hi again Oli,

I'm glad you have most of your data restored: Another confirmation that it is good to backup your data. And PhotoRec could help finding the rest of your files. Congratulations :-)

Do you have any particular reason to suspect the power supply unit? Or that it is a hardware problem?

If I were you I would not rely on Enlightenment but it could be some other problem. Do you use the ***ext4*** file system? It is very fast partly because there is a long latency before it writes (temporary stuff) to the disk (syncing). This might be the cause of your problem. ***Ext3*** is very well tested and I think it is safer, when there are problems (interruptions of different kinds, system crashes, power-down events etc). It could also be some bug of the bleeding edge Ubuntu 11.10.

Anyway, if you feel that your problem is solved, please mark this thread SOLVED

Good luck with your data in the future
Olle

---

### Post by zcacogp on 2011-11-05
Olle, 

Thanks for your answer. I have now recovered almost all of what I lost. Photorec did the job of finding the lost photographs well. It changed the filenames, and amended a lot of file metadata, but I discovered a tool called renrot which allowed me to copy a lot of the data out of the EXIF data to the filename, so the photos can now be displayed in the order in which they were taken - which is very helpful. 

Why do I think it was a hardware problem? Well the machine had a problem with the HDD a couple of months ago; I moved up from a small IDE HDD to a larger SATA HDD, for more space, and the new SATA drive produced a lot of SMART errors after a few weeks. So I replaced it with another (new) SATA drive, which is the one I am using. However now that I have lost data from it I wonder whether it is a hardware problem, and whether the PSU is producing spikes (or worse). Anyway, I installed a new PSU this morning so will see how we get on. 

Yes, I use EXT4 for all my Ubuntu file systems. Your point is interesting - thanks. 

Out of interest, why would you not rely on Enlightenment? From what I have seen, I quite like it - I think I like it more than Unity (which I really don't like at all.) 

I'll mark this thread as SOLVED, but would be interested in your thoughts on the above ... thanks! 


Oli.

---

### Post by WasMeHere on 2011-11-06
> **zcacogp said:**
> Olle, 

... a tool called renrot which allowed me to copy a lot of the data out of the EXIF data to the filename ...
Interesting, thanks for sharing!
> 
Why do I think it was a hardware problem? Well the machine had a problem with the HDD a couple of months ago; I moved up from a small IDE HDD to a larger SATA HDD, for more space, and the new SATA drive produced a lot of SMART errors after a few weeks. So I replaced it with another (new) SATA drive, which is the one I am using. However now that I have lost data from it I wonder whether it is a hardware problem, and whether the PSU is producing spikes (or worse). Anyway, I installed a new PSU this morning so will see how we get on. 
 
I see, you may me right, but if you have seen no read/write errors on the new HDD, I don't think so.
> 
Yes, I use EXT4 for all my Ubuntu file systems. Your point is interesting - thanks. 

Out of interest, why would you not rely on Enlightenment? From what I have seen, I quite like it - I think I like it more than Unity (which I really don't like at all.) 

I'll mark this thread as SOLVED, but would be interested in your thoughts on the above ... thanks! 


Oli.

The reason I would not rely on it is that the files disappeared, that they were deleted from the old place before they were safely copied to the new place. Of course, it might be unfair to blame Enlightenment, but I don't know it, while I think I know the other tools that you were using. But if you like Enlightenment and are used to it, so that you know what happens, then it is OK.

Olle

---

### Post by zcacogp on 2011-11-06
Olle, 

Thanks. Yes, renrot saved my bacon. More details about it are here: 

[http://freecode.com/projects/renrot](http://freecode.com/projects/renrot)

The reason for losing the data I guess will always remain unknown; it could be something amiss with Enlightenment, it could be a mistake I made while using Enlightenment, it could be the PSU causing the drive to behave oddly. I guess I'll believe any of them, but having changed the PSU I have counted that one out of future problems. 

I think I will use Enlightenment ... cautiously! I do like it, and I don't like Unity ... but I will take (and keep) meticulous back-ups of stuff, should it happen again. 

Thanks again for your help. 


Oli.

---

