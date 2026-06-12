---
title: "FAT32 long filenames separated from files"
date: 2009-06-18
forum: Programming Talk
---

### Post by PC-XT on 2009-06-18
I was wondering if there was someone who knew about long filenames on a FAT32 partition and would be able to help me with retrieving them (they have been separated from the file records in several folders due to a power outtage as I stated [here]("http://ubuntuforums.org/showthread.php?t=1191143") and I don't know enough to know how to re-attach them, though I used to work with the old DOS 8.3 filesystem using DEBUG to fix weird issues.

---

### Post by asbuntu on 2009-06-18
FAT32 long filenames are stored in the directory, adjacent to the 8.3 entry for the file.  Not sure, but I think they are stored in unicode.  They have a unique combination of attributes that no file or directory entry would ever have.  There can be one, or more than one (five?) entries, in case the name is longer than 15 characters.

You can fix the entries with debug, but I do not recommend that.  For one, by the time you get to FAT32 (I recall FAT12 and FAT16) the locations of things get complex.  For two, the OS cache's directory entries, and making changes directly will make the directory and the cache inconsistent.  For three, if you are using NT or above, I think the OS prevents direct access to the structure.

My recommendation is to simply rename each file as you want, and then don't use the "older" software that assumably led to the corruption.

Also, take a look at google.  I searched "FAT32 long file name" and got a lot of hits.  The first one I saw was [http://www.pcguide.com/ref/hdd/file/fatLong-c.html](http://www.pcguide.com/ref/hdd/file/fatLong-c.html).

I do recall a Microsoft utility called lfnbk.  You could check that out, but I still think you are playing with fire by doing anything but renaming the file.  Good luck.

---

### Post by PC-XT on 2009-06-19
Thank you. This is the only place I got a reply so far. I think lfnbk is the utility I was thinking of.

I did check Google and found the Microsoft specs for FAT32 long filenames, as well as Wikipedia entry, and the page you gave. I have been planning on renaming via Windows rather than thru debug, as I assumed it had become more complicated, so thank you for confirming this. But I am not sure exactly what some of the names should be, and was hoping to be able to find out by exploring the directory entries. I have downloaded R-Studio, which I am going to try over a network connection, and Drive Explorer 30 day trial in case the first doesn't work. They were both recommended as FAT32 directory entry readers.

As for finding the program that corrupted them, the only things ran since it was started up before the outtage were in this order: Windows Scripting Host (running a short startup script that displays any scandisk file, and renames or deletes it using the file system object (fSys), then checks a network connection using fSys.folderexist function; WinOldApp was not used for this to my knowledge), AOL 9, Outlook Express, Firefox 2, and possibly Java (via Firefox)
These have been running for years with little modification without problems.
After the outtage, scandisk took a long time, and looked stuck at 23%, so I pressed the x key to exit and it showed 80%. I do doubt that scandisk would ruin the long filename entries, and have had it behave that way before when directories are corrupted.
It is hard for me to understand how a power outtage could cause some entries to be invalidated in some folders, without causing more damage. To my knowledge, the only program, beside Windows itself, doing anything with most of the folders which lost names (belonging to programs that weren't running) was ScanDisk.

---

### Post by asbuntu on 2009-06-21
You might want to consider looking around before you start renaming files, now that I think about it.  Best would be to make a true disk copy (BIOS or non-filesystem oriented) so you can start over if needed.  That would minimize the amount of data lost, just in case renaming an entry that is adjacent to an orphaned entry causes that orphan to be deleted.

There are some tools out there, but my only knowledge is from the middle to late 90's.  (PCTools?  Norton?  Central Point?  The like)

If you can build a list of orphans, then apply the logic described in MS's KB, you should be able to come close to what the original 8.3 file name would have been.

Scandisk can supposedly fix things, but I don't know if it is controllable and/or if it just deletes the orphans.  Again, make a BIOS level backup of the partition before starting.

From a technical standpoint, I seem to recall that the reason the long file names stayed associated with the 8.3 name was that no properly operating program would ever rearrange entries, and if it had to insert an entry, it would not insert between the 8.3 name and the long name.  Similarly, the orphaning process seems to be related to a program or OS crashing between updates of the 8.3 name and the long name.  Good luck.

---

### Post by PC-XT on 2009-06-25
Thanks. I have a list of the Windows stuff and some programs like FireFox to rename from another drive. I also thought of using the registry, exporting a list, using FIND to extract the directory I needed (using "\progra" to allow for both short and long names) then deleted all in front of each path using WordPad's replace function (I could've used something with regEx more effeciently, but this worked ok) I then sorted the list (using SORT) and am going through it renaming. If I can rename all the files in a directory, or I figure the names of the other files are not important, I have been renaming them. Scandisk reports these lost long filenames per directory, and I don't think changing one directory affects another. The old long names may still be stored, clogging the directory, and the renames are appended at the end. Perhaps I should have it clean them on the directory before I do the renaming once I know the names. I have tried to rename as little as possible per directory so it won't mess up the others.
R-Studio works as a reader, although it is hard to find a particular directory among the thousands, so it is a last resort.
Thanks for the true disk copy idea.
I have appreciated your replies.
Thanks again. :)

---

### Post by PC-XT on 2009-07-18
It happened again. I had scandisk log this time, and it lists all the lfn directory entries as though they were regular entries, and says it deleted them. It was strange, because I had tested scandisk, and it seemed to be working. I think I was accidentally overriding the ini file during the tests. This info led me to a nearly identical problem at [http://www.computing.net/answers/windows-95/how-do-i-restore-long-file-names/170107.html](http://www.computing.net/answers/windows-95/how-do-i-restore-long-file-names/170107.html)
So I set lfncheck back on, which should stop it from happening.
Still no free solution except by hand-renaming. This time scandisk had run completely because I wasn't there to stop it. I do have an incomplete backup, thankfully, but will need to get Windows working first. :(
I was wondering if anyone had used something mentioned in that discussion like [Disk Investigator]("http://www.snapfiles.com/reviews/Disk_Investigator/diskinvestigator.html") or [Uneraser]("http://www.uneraser.com/longfilenames.htm") or something else to recommend it.

---

### Post by PC-XT on 2009-07-22
I found Disk Investigator to be easiest to use for this problem.
I had to make batch files to rename some files, renaming twice to keep the same DOS name for files that are referenced that way.
Also, reinstalling programs may cause duplicate files, which I'm using CloneSpy to clean.

---

