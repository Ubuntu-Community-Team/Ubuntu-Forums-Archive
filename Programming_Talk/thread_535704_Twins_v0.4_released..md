---
title: "Twins v0.4 released."
date: 2007-08-26
forum: Programming Talk
---

### Post by SOULRiDER on 2007-08-26
Here is the latest version of my program. Im still planning on adding more options in the future but for now this is it.

Description:
Twins is a program that scans directories looking for identical files and lists them for their easy identification. Twins was written in python. Latest version is 0.4

Changes since last version:
> new in 0.4
FIXED: A file would appear to be a duplicate when it was scanned and then re-scanned if being pointed by one or more symlinks.
FIXED: Bug where the program kept scanning the same directories in an endless loop.

Usage:
```
twins [options] [target directory]
 OPTIONS:
        -s, --slent                 Do not be verbose, only show final report.
        -r, --recursive             Be recursive, enter subdirectories.
        -h, --include-hidden        Scan hidden files, if recursive will scan hidden directories.
        -l, --follow-links          Follow symlinks.
```

I hope everyone likes it and finds it useful. If you have any comments please let me know here or by e-mail. My address is located in the source of the program.


Also, if someone is familiar with making deb packages i would like to ask for their help so I can easily distribute this and eventually if possible get it in the repos.

---

### Post by Note360 on 2007-08-26
ooh... looks cool. looks cool I need soemthign to scan for duplicate songs for me, but thats more of an id3 thing

One mroe suggestion. It would be cool if you did something liek modularize it and seperate the single executables up. Alot of people prefer this method.

---

### Post by compwiz18 on 2007-09-01
Looks great!

I'm trying it now on my external drive.  I know it has a lot of duplicates on it...

Thanks!

I can make a deb for it, if you would like.  Just post a reply and I'll get to it.

---

### Post by compwiz18 on 2007-09-02
```

Traceback (most recent call last):
  File "twins.py", line 158, in <module>
    findDupes(parameters[-1])
  File "twins.py", line 72, in findDupes
    findDupes(fullPath)
  File "twins.py", line 72, in findDupes
    findDupes(fullPath)
  File "twins.py", line 48, in findDupes
    for element in dircache.listdir(path):
  File "/usr/lib/python2.5/dircache.py", line 27, in listdir
    list = os.listdir(path)
OSError: [Errno 13] Permission denied: '/media/external-1/backups/files/lost+found'

```

When it hits a folder it doesn't have permissions for, it dies, taking all the collected MD5 sums with it...

---

### Post by SOULRiDER on 2007-09-02
Ok, i think ive fixed it. I still havnt really read about handling errors so i will probably have to improve it int he future, but this should do it for now.

Also, a deb would be great but I will im trying to modularize the program now so i will be releasing a new version later. Thanks for trying it out, i really apreciate it!!

---

### Post by compwiz18 on 2007-09-02
Cool.

If you want me to make a deb of it when you release the new version, just stick a post on this thread.

---

### Post by SOULRiDER on 2007-09-02
I will, thanks man! :)

---

### Post by erfahren on 2007-09-02
Ran it on my /home directory and saw how much of a pack-rat I am! 

it would be cool if something like this could eventually be incorporated with a program (command line or GUI) with the ability to find and remove those hidden backup files (ending with ~) and clear out the ~/.thumbnails directory.

works well though. thanks!

---

### Post by Harpoon on 2007-09-02
This is a much need tool, and thank you for the good work.
 
I used it for a quick check on a small directory (no hidden files/permission problems) and  it worked as advertised.

Ran it against a larger directory using -r (with lots of dupes) and it worked a hitch.

Just for "fun" I ran it against my /etc directory (figured there would be few dupes, but at least some other potential problems) and got:

hashing output interspersed with a few messages similar to this one:
Error opening file for reading: [Errno 13] Permission denied: '/etc/apt/trustdb.gpg' - Skipping

it continues to scan.  Great.

Then the fatal:
Hashing /etc/cups/raw.types...
         ...done hashing. MD5Sum is: 8d45496cddd485f6d9a894321fcd4028 

Traceback (most recent call last):
  File "twins", line 158, in <module>
    findDupes(parameters[-1])
  File "twins", line 72, in findDupes
    findDupes(fullPath)
  File "twins", line 72, in findDupes
    findDupes(fullPath)
  File "twins", line 48, in findDupes
    for element in dircache.listdir(path):
  File "/usr/lib/python2.5/dircache.py", line 27, in listdir
    list = os.listdir(path)
OSError: [Errno 13] Permission denied: '/etc/cups/ssl'

and it terminates.  I don't know if it found any dupes (doubt it).

Hope this is useful to you.   I've been away from programming way too long to offer fix suggestions.

---

### Post by Note360 on 2007-09-02
I think I can handle the error if you want... It shouldnt be that hard just a simple try except OSError

---

### Post by compwiz18 on 2007-09-02
> **Harpoon said:**
> 
....cut....
it continues to scan.  Great.

Then the fatal:
Hashing /etc/cups/raw.types...
         ...done hashing. MD5Sum is: 8d45496cddd485f6d9a894321fcd4028 

--- removed error code ---

and it terminates.  I don't know if it found any dupes (doubt it).

Hope this is useful to you.   I've been away from programming way too long to offer fix suggestions.

[http://ubuntuforums.org/showpost.php?p=3295106&postcount=5](http://ubuntuforums.org/showpost.php?p=3295106&postcount=5)

the attachment on that post has the fix, I believe

---

### Post by Harpoon on 2007-09-02
Compwiz:  I thunk I got the right one, but I guess I picked up the pre-fix tar by accident or neglect.  The errors do not appear with the newest version (suggest changing or deleting the link in the earlier post?)

Every day I wonder if I could be more stupid.  I guess this answers that question

Thanks a bunch for the pointer.

---

### Post by SOULRiDER on 2007-09-02
Thanks a lot to everyone that tries it out. Right now im trying to split it into module sbut since I still havnt learned much about design im doing it the way i think is best (which is probably not :P)

Ill post it as soon as its done. Thanks again for everyones support!

---

### Post by Palmyra on 2007-09-02
I need something similar to this.  I have two separate directories, and I want to ensure that both directories are identical.  I would like the application to check directory #1 for the mdsum, and then check directory #2.  After that, it should compare the mdsums of all the files in both directory #1 and directory #2, and make sure that both directories are identical.  

The point of this is that I am moving the contents of directory #1 over to #2, but I don't have the time to ensure that everything was moved over correctly.  Therefore, the application should make sure the move was done properly by checking mdsums.

Also, could someone make a .DEB of Twins, please?

OP, can you please create a website (on Sourceforge or elsewhere) for Twins so I can track its progress?

---

### Post by Georges on 2007-09-07
for syncing 2 directories use unison
```

sudo apt-get install unison unison-gui
unison-gui

```
by default unison does not sync owner, mode and times. You need to tell it to do so.

for finding duplicates... there are already many utilities.
e.g:
[http://www.pixelbeat.org/fslint/](http://www.pixelbeat.org/fslint/)

It is in active development so you may want to install the .deb from that site (because it has some bugs fixed) instead of from the ubuntu repository:
```

sudo apt-get install fslint
fslint-gui

```
the gui just calls the command line utility findup
It my be interesting to compare your code with fslint (it has some python in there)

Rule: before starting a project, ask google, or even apt
```

apt-cache search duplicate

```
> 
fdupes - Identifies duplicate files within given directories
findimagedupes - Finds visually similar or duplicate images
fslint - A toolkit to fix various problems with filesystems' data.
gtkpod - manage songs and playlists on an Apple iPod
komparator - directories comparator for KDE
mirrordir - duplicate a directory by making a minimal set of changes
perforate - Utilities to save disk space


---

### Post by Acglaphotis on 2007-09-09
deb for twins:

[http://www.mediafire.com/?1xmvjy9thxd](http://www.mediafire.com/?1xmvjy9thxd)

---

### Post by SOULRiDER on 2007-09-10
Thanks a lot for making a deb package. I dont have much time to work ont he new version but its almost done :)

I will test it when I boot into Ubuntu.

---

### Post by bsharp on 2007-09-13
This is genius....I don't have a need for it on Ubuntu right now, but I will test it anyway and hope something like this will come along for Windows (that's where all my junk is :P)

---

### Post by erfahren on 2007-09-13
> **bsharp said:**
> This is genius....I don't have a need for it on Ubuntu right now, but I will test it anyway and hope something like this will come along for Windows (that's where all my junk is :P)
for WinXP there's [Find Duplicates.NET](http://www.pcworld.com/downloads/file/fid,64306-order,1-page,1/description.html?tk=nl_hsxdwn), a freeware stand-alone app. I'm sure there are other more comprehensive ones available (freeware even), see DupKiller and Duplicate Cleaner here: [http://www.majorgeeks.com/downloads12.html](http://www.majorgeeks.com/downloads12.html)

---

### Post by SOULRiDER on 2007-09-13
My program is written in python so it WILL work on windows but im not sure of how it will react with things like symlinks. Also, you can just mount your windows partition and use it :P

---

### Post by Awalton on 2007-09-13
Well, like what's already been noted, there are a ton of apps that already exist to do this, but if you want to keep going, hell why not, it's good experience either way.

A big suggestion would be not to hash the whole file unless you need to. Hashes take a while to run, especially across larger files, and it's more advantageous to scan more files than to scan whole files on the first pass. I had to write a similar program in C a long time ago, and I just opened the file, hashed the first 8K and stuck that in the hash table. If there were any collisions, at that point you do the whole hash check just to be sure. Most files (images, songs, etc) will show a delta in the first two blocks. The only ones that won't are files such as source code, where the full-file hash check will catch them. It should shave quite a bit of time off the current run-time of the script. You could go with an adjustable block-size too to tune your hash performance.

I'd write the patch for you but Python is Greek to me.

---

### Post by Palmyra on 2007-09-15
> **Georges said:**
> for syncing 2 directories use unison
```

sudo apt-get install unison unison-gui
unison-gui

```
by default unison does not sync owner, mode and times. You need to tell it to do so.

I am not trying to sync directories.  I want to know if two directories are already identical, and if they are, I can delete one of the two.  Syncing means that you are intentionally trying to make them identical.  It appears I have download the same folders multiple times, and if Twins could find out that I have the same folder on my computer on different locations, that'd be great.

> 
for finding duplicates... there are already many utilities.
e.g:
[http://www.pixelbeat.org/fslint/](http://www.pixelbeat.org/fslint/)



Methods used to identify duplicate files are probably not as good as using md5 to see if they are truly identical.  More importantly, when moving files, it is good to check md5 to see if the moved file is identical to the original file (since all sorts of things can happen during the move).

The idea is not to find duplicates, but to ensure file integrity.  

Also, FSLint does not have an ideal graphic user interface.

---

