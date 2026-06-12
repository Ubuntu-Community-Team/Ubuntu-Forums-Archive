---
title: "Script to Copy files from Recursive Directories..."
date: 2007-04-20
forum: Programming Talk
---

### Post by xMemphisx on 2007-04-20
Alright, basically all of my music is setup in folders (probably like everyone else's)... Artist Name/Album/Track# Song Title

Anyways, i have a Creative Zen, and i've got Gnomad 2 setup, but you can't just drag and drop your entire Music folder and get it to import all of your songs that lie in that directory... so i was trying to write a simple batch script that would go through my directory, and copy all of my .mp3 files to a single temporary folder somewhere else. 

This is what i tried, but it was no good (obviously)... but i'm not really sure what else to try...
cp "/home/****/Documents/Tunes/Tracks/*/*.mp3" "/home/****/Documents/Temp to Zen/"

Anyone have any ideas? (or know how to get gnomad working the way it hsould be?) Thanks in advance.

---

### Post by Swab on 2007-04-20
try something like this...

```

find /path/to/mp3s -name \*.mp3 -exec cp {} /path/to/new/folder \;

```

man find  for more info..

---

### Post by bashologist on 2007-04-20
To copy all files with a ".mp3" extention to another directory you might wanna try this:
```
[COLOR="Gray"]# Check to make sure the command looks right.[/COLOR]
find /path/to/music -iname '*.mp3'
[COLOR="Gray"]# Make sure to have a "/" at the end of "directory" or it will copy all files into just one file named "directory".[/COLOR]
find /path/to/music -iname '*.mp3' -exec cp {} /new/directory/ \;
```

---

### Post by xMemphisx on 2007-04-20
I got it figured out. I feel stupid.

Thanks guys

---

### Post by Ceezey77 on 2008-11-01
Swab:

Got a bit ahead of myself and ran the script to move some RAW image files out of a photo directory.  (Obviously changed the *.mp3 extension to my required format)

Neglecting the fact that some of the image files in the source directory may be named the same (I've got a backup if I screw anything up anyway) I ran the script and am currently watching it move hundreds of files happily.

(Thank you) :KS

As far as I can see, if the script does copy an image to the target directory that already has the same name, it simply renames it <image>a.{extension} and then <image>b.{extension} - 

(As a noob) I'm wondering if this is default behaviour and whether this can be defined / altered.

Windows convert used to files being named file, file(1), file(2)

---

### Post by ankursethi on 2008-11-01
I remember doing this with Python once. I've lost that script now, but I remember it was about 15 or 20 lines of code. Of course, I'd have written it differently now, but even then it would weigh in at around 10 lines of code.

I seriously need to learn how to use the shell.

---

### Post by carltonnotthedoorman on 2008-11-14
Hey, I'm having a similar problem, but the script above is only copying the files to one directory and not recreating the directory structure. Is there something I need to add to the script?

---

### Post by geirha on 2008-11-14
Use the --parents option to cp (read the man-page)

```
cd /path/to/music
find . -name "*.mp3" -exec cp -v --parents {} /new/directory \;

```

---

### Post by zeezam on 2008-11-29
I'm curious if it's possible to find several file types.
Trying to make a unrar and delete script for my downloaded files.

Now I make **find -name *.nfo -exec rm -fv {} \;** for every filetype.

---

### Post by geirha on 2008-11-29
> **zeezam said:**
> I'm curious if it's possible to find several file types.
Trying to make a unrar and delete script for my downloaded files.

Now I make **find -name *.nfo -exec rm -fv {} \;** for every filetype.

You have logical or (-o). You must group them inside \( and \) or else the -exec will only run on the last filetype.
```
find \( -name "*.nfo" -o -name "*.foo" -o -name "*.bar" \) -exec echo rm {} \;
```

Btw, instead of «-exec rm ...» you can use «-delete»

EDIT: Oh and you can also match by regex:

```
find -regex ".*\.\(nfo\|foo\|bar\)"
```

---

### Post by unutbu on 2008-11-29
```
find . \( -name '*.nfu' -o -name '*.txt' \) -exec rm -fv {} \;
```

This will remove all files that end in .nfu or .txt.
You can add more extensions similarly.

---

### Post by zeezam on 2008-12-21
> **unutbu said:**
> ```
find . \( -name '*.nfu' -o -name '*.txt' \) -exec rm -fv {} \;
```

This will remove all files that end in .nfu or .txt.
You can add more extensions similarly.

Nice, works like a charm!

---

