---
title: "tar --exclude [bash]"
date: 2011-05-31
forum: Programming Talk
---

### Post by 23Andrew on 2011-05-31
I'm making a backup script in bash. And I've just been testing it out, and with all of the encryption and compression, it becomes very slow, so I've decided to exclude some things.

The first few lines of code go like this [Using different folder names for security]:
[PHP]#! /bin/bash
FILES="Music"
EXCLUDE="*.mp3"
echo Compressing files...
mkdir Backup
tar -pvczf Backup/Backup.tar.gz --exclude=$EXCLUDE $FILES > log.txt
echo Done.
[/PHP]

This works.

If I change the third line to:
[PHP]EXCLUDE="Music/SomeRandomArtist/*"[/PHP]

This works.

However, if I try to combine the two, like:
[PHP]EXCLUDE="*.mp3 Music/SomeRandomArtist/*"[/PHP]

This DOESN'T work, and ends up excluding nothing. 

I've tried delimiting the things with commas instead of spaces, and still no more luck.

Heh, I've tried a lot of things, there's no point mentioning them all.

Google was no help, so I'm hoping you could give me a hand.

Thanks in advance.

---

### Post by papibe on 2011-05-31
I believe --exclude only can handle one expression. But nothing stops you to using several excludes. For example:
```
...
EXCLUDE1="Music/SomeRandomArtist/*" 
EXCLUDE2="*.mp3"
tar -pvczf Backup/Backup.tar.gz --exclude=$EXCLUDE1 --exclude=$EXCLUDE2 $FILES > log.txt
...
```

Good Luck!

---

### Post by 23Andrew on 2011-05-31
> **papibe said:**
> I believe --exclude only can handle one expression. But nothing stops you to using several excludes. For example:
```
...
```

Good Luck!

I'll try that, and thanks.

EDIT:
I tried:
[php]FILES="Music"
EXCLUDE0="*.mp3"
EXCLUDE1="Music/SomeRandomArtist/*"
EXCLUDE2="Music/SomeRandomArtist/"
echo Compressing files...
mkdir Backup
tar -pvczf Backup/Backup.tar.gz --exclude=$EXCLUDE0 --exclude=$EXCLUDE1 --exclude=$EXCLUDE2 $FILES > log.txt
echo Done.[/php]

Interestingly, it worked, however, the directory "Music/SomeRandomArtist/" was still archived, however non of it's contents were.

EDIT2: Removed the final forward slash, on "Music/SomeRandomArtist/" and all is dandy.

---

### Post by papibe on 2011-05-31
Glad to hear that.

If you have more patterns, files, and directories to exclude, is going to be a kind of inconvenience to have all those --exclude statements. Ahother alternative is to put all your excludes in a file:

```
$ cat all_my_excludes.txt
*.mp3
Music/SomeRandomArtist/*
Music/SomeRandomArtist
```
And then use -X option. Something like:
```
...
$ tar tar -pvczf Backup/Backup.tar.gz -X all_my_excludes.txt
...
```
Regards.

---

### Post by dwhitney67 on 2011-05-31
> **papibe said:**
> Glad to hear that.

If you have more patterns, files, and directories to exclude, is going to be a kind of inconvenience to have all those --exclude statements. Ahother alternative is to put all your excludes in a file:

```
$ cat all_my_excludes.txt
*.mp3
Music/SomeRandomArtist/*
Music/SomeRandomArtist
```
And then use -X option. Something like:
```
...
$ tar tar -pvczf Backup/Backup.tar.gz -X all_my_excludes.txt
...
```
Regards.

This is exactly what I was going to suggest; at my office we have a script that does something similar to the following:
```

#!/bin/bash

TMPFILE="/tmp/exclude.lst"

EXCLUDE=`find . \( -wholename './Music/SomeRandomArtist/*.mp3' -print \) -o \
                \( -wholename './Music/SomeRandomArtist2/*.mp3' -print \) -o \
                \( -wholename ./this_script -print \) -o \
                \( -wholename './*.tgz' -print \) > $TMPFILE`

tar czvfX tarball.tgz $TMPFILE .

unlink $TMPFILE

```

---

