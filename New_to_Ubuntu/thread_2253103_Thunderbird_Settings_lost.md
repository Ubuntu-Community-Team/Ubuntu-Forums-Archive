---
title: "Thunderbird Settings lost"
date: 2014-11-17
forum: New to Ubuntu
---

### Post by RayArdia on 2014-11-17
I reinstalled Ubuntu 14.04, having saved my complete Home folder to a separate HDD. I now find that I can't get Thunderbird to access my two email accounts . How do I recover the settings like Username (I forgot what I used) and Password?

---

### Post by coffeecat on 2014-11-17
Did you copy your saved home folder back to the re-installed system? If you didn't, when you first opened Thunderbird, it would have created the folder ~/.thunderbird with nothing much in it. That is, a hidden folder called .thunderbird in your home folder in the new system. Unless you have done something else, all your saved emails, settings, etc, will be in the hidden .thunderbird folder in your home folder in the separate HD.

If my assumptions are correct, you need to replace the .thunderbird folder and contents in your new home with what is archived in the separate HD.

---

### Post by RayArdia on 2014-11-17
The copy of Home on my external HDD doesn't seem to contain ANY hidden files. Can I use a command in terminal to check this as I find it very strange indeed.

---

### Post by coffeecat on 2014-11-17
It would be odd for a copy of the whole of your home folder to exclude the hidden files and folders, because even Microsoft filesystems such as NTFS and FAT32 will cope with them. 

You could cd to the home folder on the external HD and run this command:

```
ls .*
```

But be sure you're in the correct folder. Did you set up the same path - /home/yourname - as in an Ubuntu system - or did you simply copy everything in /home/username to a differently named folder in the external HD? Not that it makes any difference, but what is the filesystem on the external HD?

---

### Post by RayArdia on 2014-11-17
> **coffeecat said:**
> It would be odd for a copy of the whole of your home folder to exclude the hidden files and folders, because even Microsoft filesystems such as NTFS and FAT32 will cope with them. 

You could cd to the home folder on the external HD and run this command:

```
ls .*
```

But be sure you're in the correct folder. Did you set up the same path - /home/yourname - as in an Ubuntu system - or did you simply copy everything in /home/username to a differently named folder in the external HD? Not that it makes any difference, but what is the filesystem on the external HD?

I simply copied /Home/ray to a newly-named folder 'Copy of Home as at 14 Nov 2014"
File System on Seagate HDD is HPFS/NTFS
Re:- "You could cd to the home folder on the external HD and run this command:"
Output:-
ray@ray-Aspire-5735:~$ cd /media/ray/"Seagate Expansion Drive"/"Copy of Home as at 14 Nov 2014"
ray@ray-Aspire-5735:/media/ray/Seagate Expansion Drive/Copy of Home as at 14 Nov 2014$ ls .*
.:
BSA M20 Military Version_files
BSA M20 Military Version.html
cups-1.7.3
Desktop
Downloads
Early Lighfoot - Sunday Concert
Family Tree 1_2014-09-27.gpkg.media
firefox
Firefox_wallpaper.png
guayadeque
hp-check.log
hplip-3.10.9
iTunes
Jigsaw etc.dxf
John Denver
Keepass Database.kdb
Link to Calibre Library
Link to Diagrams Sketches etc
Link to Genealogy Research Documents, Photos etc
Link to Hobbies
Link to Music
Link to Pictures
lshw.txt
Marks Events.odt
Marriage Marks-Wadham Oct-Dec 1867.odt
MobiMetaEditor
Mounting and Permissions.odt
NIS Vocabulary - Beginners 1-8.odt
NIS Vocabulary.odt
Pillar Drill mods.dxf
QBT Downloads
qcad-3.4.6-linux-x86_32
recovered_jpegs
Screenshot from 2014-05-16 22:11:00.png
shotwell-0.8.1
Silverside.odt
Soluciones NIS Int.odt
troubleshoot.txt
Two M10 nuts .skb
Two M10 nuts .skp
usr
Videos
WD&RA letter to Santander 28 Jul 2014.odt

..:
Backup 26 Mar 2014                        Photos for Sorting
Calibre Library                           Pictures
Copy of Home as at 14 Nov 2014            Programs Downloaded
Diagrams Sketches etc                     QBT Downloads
documents                                 RAY-PC
Genealogy Research Documents, Photos etc  Recipes
Hobbies                                   recovered_jpegs
Link to Calibre Library                   $RECYCLE.BIN
Linux                                     Seagate
MediaID.bin                               System Volume Information
Music                                     User, Workshop & Service Manuals 
ray@ray-Aspire-5735:/media/ray/Seagate Expansion Drive/Copy of Home as at 14 Nov 2014$ 
 I don't see any .files, so presume something has gone wrong. I'm not sure what the entry just before Backup 26 Mar 2014  ( ..: ) means; is it significant?

---

### Post by lisati on 2014-11-17
How did you copy your files to your backup drive? If you were using a file browser, opened the folder, and copied from there, hidden files would be easily missed by the copy if you hadn't chosen the relevant option to view hidden files.

---

### Post by RayArdia on 2014-11-17
That's just what I did - I had no idea that any files could be missed out of the Copy - Paste, seems like I'm stuffed!
BTW is there any significance in the ( .: ) ?

---

### Post by lisati on 2014-11-17
> **RayArdia said:**
> 
BTW is there any significance in the ( .: ) ?

A period in a filename has different meanings according to the context. Towards the end of a filename, it's commonly used as a separator for the file type/file extension. At the start of the filename, it's used to signal that the file is hidden in Ubuntu.

There are commonly two special filenames in Windows and *nix. "." is a kind of shorthand for the current directory, and ".." refers to one level up in the file directory structure.

---

### Post by RayArdia on 2014-11-17
> **lisati said:**
> A period in a filename has different meanings according to the context. Towards the end of a filename, it's commonly used as a separator for the file type/file extension. At the start of the filename, it's used to signal that the file is hidden in Ubuntu.
Understood, no problems with that.

There are commonly two special filenames in Windows and *nix. "." is a kind of shorthand for the current directory, and ".." refers to one level up in the file directory structure.

That's understood too, but what is the significance of the two, one on top of the other in that   'ls .*'   sequence above?

---

### Post by lisati on 2014-11-17
> **RayArdia said:**
> That's understood too, but what is the significance of the two, one on top of the other in that   'ls .*'   sequence above?

My bad: I misinterpreted your question as relating to one line with "." followed by ".." on the next. Now that I've taken another look, I must confess to not being sure....... :(

---

