---
title: "[SOLVED] Help with script"
date: 2008-02-16
forum: Programming Talk
---

### Post by aidanr on 2008-02-16
I'm writing a small script to go through my music collection and modify the album art to make it look nicer. The first script which focuses on just one file works fine, but when I try to put it in a for loop to go  through my music collection recursively I get the errors below. Any ideas?

[php]#!/bin/bash

convert -size 600x600 xc:none \
	-draw "image over 55,3 540,595 '/mnt/Maxtor/test/Music/ACDC/ACDC Live/CD 2/cover.jpg'" \
	-draw "image over 0,0, 600,600  'case.png'" \
	"/mnt/Maxtor/test/Music/ACDC/ACDC Live/CD 2/cover.jpg"[/php]

[php]#!/bin/bash

for i in `find /mnt/Maxtor/test/Music/ -iname 'cover.jpg'`; do
	
convert -size 600x600 xc:none \
	-draw "image over 55,3 540,595 '$i'" \
	-draw "image over 0,0, 600,600  'case.png'" \
	"$i"

done[/php]

```
command:./convert
convert: unable to open image `/mnt/Maxtor/test/Music/Air/Moon': No such file or directory.
convert: no encode delegate for this image format `/mnt/Maxtor/test/Music/Air/Moon'.
convert: unable to open image `Safari/cover.jpg': No such file or directory.
convert: unable to open image `Safari/cover.jpg': No such file or directory.
convert: unable to open image `/mnt/Maxtor/test/Music/Aerosmith/A': No such file or directory.
convert: no encode delegate for this image format `/mnt/Maxtor/test/Music/Aerosmith/A'.
convert: unable to open image `Little': No such file or directory.
convert: no encode delegate for this image format `Little'.
convert: unable to open image `South': No such file or directory.
convert: no encode delegate for this image format `South'.
convert: unable to open image `Of': No such file or directory.
convert: no encode delegate for this image format `Of'.
convert: unable to open image `Sanity/Disc': No such file or directory.
convert: no encode delegate for this image format `Sanity/Disc'.
convert: unable to open image `1/cover.jpg': No such file or directory.
convert: unable to open image `1/cover.jpg': No such file or directory.
convert: unable to open image `/mnt/Maxtor/test/Music/Aerosmith/A': No such file or directory.
convert: no encode delegate for this image format `/mnt/Maxtor/test/Music/Aerosmith/A'.
convert: unable to open image `Little': No such file or directory.
convert: no encode delegate for this image format `Little'.
convert: unable to open image `South': No such file or directory.
convert: no encode delegate for this image format `South'.
convert: unable to open image `Of': No such file or directory.
convert: no encode delegate for this image format `Of'.
convert: unable to open image `Sanity/Disc': No such file or directory.
convert: no encode delegate for this image format `Sanity/Disc'.
convert: unable to open image `2/cover.jpg': No such file or directory.
convert: unable to open image `2/cover.jpg': No such file or directory.
convert: unable to open image `/mnt/Maxtor/test/Music/ACDC/ACDC': No such file or directory.
convert: no encode delegate for this image format `/mnt/Maxtor/test/Music/ACDC/ACDC'.
convert: unable to open image `Live/CD': No such file or directory.
convert: no encode delegate for this image format `Live/CD'.
convert: unable to open image `2/cover.jpg': No such file or directory.
convert: unable to open image `2/cover.jpg': No such file or directory.
convert: unable to open image `/mnt/Maxtor/test/Music/ACDC/ACDC': No such file or directory.
convert: no encode delegate for this image format `/mnt/Maxtor/test/Music/ACDC/ACDC'.
convert: unable to open image `Live/CD': No such file or directory.
convert: no encode delegate for this image format `Live/CD'.
convert: unable to open image `1/cover.jpg': No such file or directory.
convert: unable to open image `1/cover.jpg': No such file or directory.

```

---

### Post by ghostdog74 on 2008-02-16
that's because your files have white spaces. try not to name your music files with spaces in *nix

try this
```

find /yourpath  -type f -iname  'cover.jpg' | while read -r thefile
do
 convert blah blah "$thefile"
done  

```

---

### Post by aidanr on 2008-02-16
Thanks, that's perfect :)

---

