---
title: "Programming; List all files, change drive&amp;folder, delete that file list?"
date: 2013-07-15
forum: Programming Talk
---

### Post by CaptBry on 2013-07-15
This is Copy reversal across folders job. 
For a 'dumb' stereo, I had to manually extract the 10GB of music files from their respective folders and dump them all into the first level on a USB drive. The 'dumb' stereo can't parse folders in Play mode.

This might be a good Python project - but I haven't programmed since my Atari 800....

Its; Search one folder for "all Files" and store the file names.
The move to a different drive (USB Drive in this case) and Delete those files from the 'target' drive (USB).

Neat & sweet, yes?

Or is there a program or sequence which can already do this?

Essentially a reversal of a copy error....Must be in Unix somewhere?...I ain't the FIRST! LoL

Thanks!

---

### Post by Vaphell on 2013-07-16
i can't figure out from your description what you need, 'moving to USB and deleting stuff from the *target* USB' doesn't match any definition of 'crystal clear' i know of :-)

---

### Post by ofnuts on 2013-07-16
If there is no white space in your file names: 

```

find source_root_dir -name '*.mp3' -exec mv {} target_dir \;

```

Or the more efficient (all files moved in one call to "mv"):

```

find source_root_dir -name '*.mp3' -exec mv -t target_dir {}\+

```

If your source only contains music files just get rid of the whoe tree:

```

rm -rf source_root_dir

```

If there are white space in your fle names, something along these lines (untested):
```

find . -name '*.mp3' -print0 | xargs -0 mv -t target_dir

```

---

### Post by CaptBry on 2013-07-16
Thanks, OFNUTS!

I looked up the --help pages on find,rm, and mv.

The fragment, | xarg parses the print0 of the filenames into the rm function?

Do I translate the steps correctly:
find the all the filenames to be deleted and store them in a file called, source_root_dir

then remove those files names; rm -rf source_root_dir while in the directory where the files need to be removed from (target directory)

Would this work:

find *.mp3 > Delete_List.txt
move to the target directory & drive
copy Delete_List into that folder.
then; rm | Delete_List.txt

I think that last line isn't parsing the text list properly...

Thanks for your help and stuff :)

---

### Post by ofnuts on 2013-07-16
No, the filenames are not stored anywhere. *source_root_dir is* the top directory with your music. It's optional in ***find*** if *source_root_dir *is your current directory when you start. All these commands are various ways to do more or less the same thing. From top to bottom, in slow motion:

1) list all mp3 files under the *source_root_dir directory* and move them one by one to *target_dir* (assumes no spaces in filenames)
2) list all mp3 files under the *source_root_dir* directory and move them all together to *target_dir* (assumes no spaces in filenames)
3) delete all mp3 files under the *source_root_dir *directory  (use only after 1,2 or 4 have run and you are happy with the result...)
4) same as 2) but will handle properly the "difficult" names (spaces, etc)

Each line is a complete command, there is strictly no "list" file produced on disk; everything is done "on the fly", because the *"-exec"* parameter in ***find*** makes it execute commands on each file that matches, and ***xargs*** reads from stdin (here, a pipe ('|') with the output of ***find***) a list of items to use as arguments in a command (here, ***mv***).

Welcome to the power of the command line :)

.

---

### Post by CaptBry on 2013-07-16
Excellent slow motion explanation!

It all worked; THANKS

plus I learned -exec and xargs (some features) ; very powerful commend line stuff.

command line syntax still gets me...practice....

Cheers!

Follow up for others :
I used Pyrenamer to change spaces to underscores.
Then eliminated ' marks and brackets ()
These messup the rm function

These filenames changes must be done in the original folder(artist in this case) and the giant one (all mp3s in the base folder of the USB drive - IDENTACALLY for the filesnames to be the same.
Then I used 
ls > killfile.txt in the Artists' folder
copied that into the USB drive's main folder
the used:
cat killfile.txt | xargs > rm
that will read the text file into the rm (remove) function, which will kill 'em all.
Artist deleted from the USB, yay.

---

