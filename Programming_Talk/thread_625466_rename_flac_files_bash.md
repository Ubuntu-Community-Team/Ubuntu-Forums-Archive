---
title: "rename flac files bash"
date: 2007-11-28
forum: Programming Talk
---

### Post by whazooo on 2007-11-28
Hello.
Im trying to make a script that will
take the tag headers from a flac file
put them in a txt file
and then rename the flac file from the tag info created in the newly made file

this is what I have so far

rename.sh

```

#!/bin/bash
for file in *.flac ; do
metaflac $file --export-tags-to=/tmp/tmp.txt
done

```

This reads the metadata and dumps it into a file in the tmp directory

The original files look like this:
01_-_Track_1.flac

the dumped file looks like this:
```

ALBUM=Self Esteem
ARTIST=The Offspring
COMPOSER=The Offspring
DESCRIPTION=
DISCID=0912a612
GENRE=Just Plain Wierd
MUSICBRAINZ_DISCID=o33.enTD6BY0zF2.Wn..dIpgsFI-
TITLE=Self Esteem
TRACKNUMBER=1
TRACKTOTAL=18

```
I would like to use sed to grab the title and artist info and rename the file as such:
Offspring_Self_Esteem.flac

Can anybody point me in the general direction?
thanks!

---

### Post by Trumpen on 2007-11-28
What about something like this:

```
#!/bin/bash
for file in *.flac ; do
           metaflac $file --export-tags-to=/tmp/tmp.txt
           part1=$(awk '{FS="="} /ARTIST/{print $2}' /tmp/tmp.txt |sed 's/ /_/g')
           part2=$(awk '{FS="="} /TITLE/{print $2}' /tmp/tmp.txt |sed 's/ /_/g')
           mv $file ${part1}_$part2.flac
done
```

Hope this helps!

---

### Post by whazooo on 2007-11-28
> **Trumpen said:**
> What about something like this:!

Excellent! Thank you..
works perfectly.

I added this to get rid of the tmp/tmp.txt
to make way if adding more than one flac file to be processed.
```
#!/bin/bash 
for file in *.flac ; do
          metaflac $file --export-tags-to=tmp/tmp.txt
           part1=$(awk '{FS="="} /ARTIST/{print $2}' tmp/tmp.txt |sed 's/ /_/g')
           part2=$(awk '{FS="="} /TITLE/{print $2}' tmp/tmp.txt |sed 's/ /_/g')
           mv $file ${part1}_$part2.flac
 mv tmp/tmp.txt tmp/${part1}_$part2.txt
done
```

Now I'm going to try to add some error handling in case the file cant be read,
the tmp file couldn't be wrote to, if the tmp/tmp.txt file already exists etc.... 

I'll repost it here so others might use it if needed..
Thanks again!!!

---

### Post by LemursDontExist on 2009-03-09
I found the script here immensely useful.  Thank you!  I needed something a little fancier, so in case its useful to anyone else, here's what I came up with.

```
#!/bin/bash
find "${1%/}" -type f -a -name '*.flac' | while read filename ; do
	metaflac "$filename" --export-tags-to=/tmp/tmp.txt
	album=$(awk 'BEGIN {FS="="; IGNORECASE=1} /^ALBUM/{print $2}' /tmp/tmp.txt | sed 's/\//-/g')
	artist=$(awk 'BEGIN {FS="="; IGNORECASE=1} /^ARTIST/{print $2}' /tmp/tmp.txt | sed 's/\//-/g')
	title=$(awk 'BEGIN {FS="="; IGNORECASE=1} /^TITLE/{print $2}' /tmp/tmp.txt | sed 's/\//-/g')
	tracknumber=$(awk 'BEGIN {FS="="; IGNORECASE=1} /^TRACKNUMBER/{print $2}' /tmp/tmp.txt | sed 's/\//-/g')
	mkdir -p /mnt/foto/Music/"$album"
	mv "$filename" "${2%/}/${album}/$tracknumber - $artist - ${title}.flac"
done
```

It takes a source folder and destination folder as arguments and sorts things into album/track - artist - title.  It also deals with some potential problems.  Should be easy to modify if you want a different filename/directory.

---

