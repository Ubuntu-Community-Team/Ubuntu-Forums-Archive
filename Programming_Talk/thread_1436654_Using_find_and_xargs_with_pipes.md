---
title: "Using find and xargs with pipes"
date: 2010-03-22
forum: Programming Talk
---

### Post by FakeOutdoorsman on 2010-03-22
I'm trying to convert Nikon NEF images to jpg.  Usually I use find and xargs for batch processes like this for example:
```
find . -name "*.flac" -exec basename \{\} .flac \; | xargs -i ffmpeg -i \{\}.flac -acodec libvorbis -aq 3 \{\}.ogg
```
However, my latest attempt is giving me no output because I can't seem to get xargs to work with pipes.  An individual set of commands works:
```
dcraw -w -c MEY_7046.NEF | convert - -resize 25% MEY_7046.jpg
exiftool -overwrite_original -TagsFromFile MEY_7046.NEF MEY_7046.jpg
dcraw -z MEY_7046.jpg
```
A nice set of commands, but not yet practical for converting a DVD with multiple directories.  My truncated find-isized version does nothing:
```
find . -name "*.NEF" -exec basename \{\} .NEF \; | xargs -i dcraw -w -c \{\}.NEF | convert - -resize 25% \{\}.jpg
```
Any ideas of where I'm going wrong?

---

### Post by diesch on 2010-03-23
That pipes the output of all the dcraw runs together into one convert call.

Try
```
find . -name "*.NEF" -exec basename \{\} .NEF \; | xargs -i sh -c 'dcraw -w -c $0.NEF | convert - -resize 25% $0.jpg' {}
```

---

### Post by boardhead on 2010-03-23
You can skip the "dcraw -z" command by using "exiftool -tagsfromfile %d%f.NEF -all '-filemodifydate<createdate' ...".

---

### Post by FakeOutdoorsman on 2010-03-23
> **diesch said:**
> That pipes the output of all the dcraw runs together into one convert call.

Try
```
find . -name "*.NEF" -exec basename \{\} .NEF \; | xargs -i sh -c 'dcraw -w -c $0.NEF | convert - -resize 25% $0.jpg' {}
```

Excellent.  That worked perfectly.  Thanks.

> **boardhead said:**
> You can skip the "dcraw -z" command by using "exiftool -tagsfromfile %d%f.NEF -all '-filemodifydate<createdate' ...".

Interesting, although I decided *exiftool* and *dcraw -z* commands were unnecessary this time.

---

### Post by Brimfulof2 on 2011-02-22
I think what you've got here could be just what I'm looking for, but I'm really new to *nix, Ubuntu and command-line stuff so I want to check.
 
If I understand correctly:
 
This command searches through a directory and sub-directories, finding any files with the NEF extension and converts them to JPG (at 25% reduction).
 
So does this replace the NEF files with JPGs or just add the JPGs?
Do I need to download any repositories before running this command?
 
Thanks in advance for your help.

---

