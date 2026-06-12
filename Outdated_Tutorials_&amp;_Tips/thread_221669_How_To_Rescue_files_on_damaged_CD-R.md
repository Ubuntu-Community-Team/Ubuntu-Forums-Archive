---
title: "How To: Rescue files on damaged CD-R"
date: 2006-07-23
forum: Outdated Tutorials &amp; Tips
---

### Post by dimeotane on 2006-07-23
Do you have a damaged CD-R of files that you haven't thrown out because you hope to rescue something from it?  Perhaps it's gotten scratched or has dozens of little  oxidized pinholes in the top foil?  

I've found that Ubuntu does a pretty darn good job recovering files.  I had a 5 year old well used CD-R full of precious mp3 albums, I hoped to salvage something before throwing it out.  On both Ubuntu and XP the CD-R was openable and the file directory showed the contents fine, but most of the files wouldn't drag and drop to copy off the CD.  XP gave a "Data Error: Cyclic redundancy check"  On both XP and Ubuntu, the CDROM drive caused the PC to freeze and crashed explorer and also Gnome! You've already cleaned the CD, and done CD repair wax , but no luck. 

I learned that data recovery from a CD-R does take quite some time running on your PC, so if you can live without recovering your files, you may want to not bother.  It's not too hard to do though, and you can still some other things on you PC while it runs. 

Option 1: use dd to make an ISO image of the CD-R, but continue running even if it encounters errors and to fill the error with zeros. This method worked alright. Some of my albums have perfect audio playback while others skip a bit in the song.  I was impressed with how many files were recovered in a few hours (>60megs)!  In the terminal enter : (My CDROM drive is /dev/hdc for some reason ). Enter this and go sleep for the night:
$ dd if=/dev/hdc of=cdr-backup1.iso conv=noerror,sync 

Option 2: gnu ddrescue is designed to work differently than making an ISO with dd.  It creates a log file so you can resume or make a second attempt at a later time because it creates a log file of it's progress. It can copy backwards too, and fill in missing data later.  I let this run all night on my CD-R and recovered over 100megs of intact files. I've resumed my recovery tonight and gained another 13megs in the past hour. I think the files recovered in this manner are higher quality. 

in the terminal install ddrescue:
$ sudo apt-get install gddrescue
run this ddrescue command and go catch some ZZZzzz's
$ sudo ddrescue -v /dev/hdc cdr-backup2.iso ddrescue.log

After you've made an ISO file in your home folder, right click and you can start extracting files.  If they're not fully recovered you may find that they are of a very small file size and file type is not identified; I send those to the trash (I'm sure hard core hackers can use a hex editor and a toothpick to recover fragments: you go tiger! I couldn't be bothered)   

Maybe the hackers can give some advice here on how to use fsck to repair a file system in the ISO thats not intact... is there some way of doing $ fsck.iso9660 or something? 


Some side notes of interest: 
In comparison, on XP I tried a freeware program to make an ISO of a CD, "LCISOCreator"; which didn't work for more than 3 seconds before a CRC error came up and halted. I'm sure there's plenty of commercial apps that can do a better job for $100. 

A couple other data recovery apps in Ubuntu I came across that might be of interest are: 
Testdisk (with photorec):

"TestDisk checks the partition and boot sectors of your disks. It is very useful in recovering lost partitions. PhotoRec is file data recovery software designed to recover lost media files from digital camera memory or even Hard Disks.

---

### Post by foxy123 on 2006-12-14
A small correction for this howto. You should run

```
sudo apt-get install gddrescue
``` If you use the commend from the howto you install dd_rescue, which is a slightly different programme.

---

