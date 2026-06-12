---
title: "need help with bash script to generate nfo files"
date: 2010-05-03
forum: Programming Talk
---

### Post by jurialmunkey on 2010-05-03
Hi all,

I'm trying to write a simple bash script which will generate a text .nfo file from the file names in a directory. Its for my music video library in xbmc. 

Basically I have a bunch of music videos which are named : "Artist - Song.avi"

I need to create an .nfo text file for each with the following in it:
```
<musicvideo>
<title>Song</title>
<artist>Artist</artist>
</musicvideo>
```

So, for example, "Arcade Fire - Laika.avi" will have a file generated called "Arcade Fire - Laika.nfo" with Laika between the title tags and Arcade Fire between the artist tags.

I know this is really easy, but I can't for the life of me figure out exactly how to do it... Help me please!!

---

### Post by Portmanteaufu on 2010-05-03
This should work for all the .avi files in the directory tree. Make sure you have write permissions everywhere, though.

```

#!/bin/bash
find . -name '*.avi' | while read file_name; do
        band_name=`echo $file_name | sed 's/ *-.*$//'` # Get rid of song name
        band_name=`echo $band_name | sed 's/^.*\///'`  # Get rid of file path
        song_name=`echo $file_name | sed 's/^.*- *//'` # Get rid of band name
        song_name=`echo $song_name | sed 's/.avi//'` # Get rid of file extension
        new_file_name=`echo $file_name | sed 's/.avi/.nfo/'` # Make new filename
        echo "Making $new_file_name..."
        echo -en "<musicvideo>\n<title>$song_name</title>\n<artist>$band_name</artist>\n</musicvideo>\n" > "$new_file_name"
done

```

---

### Post by jurialmunkey on 2010-05-03
Thank you. Works perfectly.

---

### Post by umsorg on 2011-01-30
Hi,

I already have the .nfo files, but the name of the file is not correct.

For now I have for example Ubuntu Cartoon - S01E01.avi / Ubuntu Cartoon - S01E01.nfo.

The NFO contains:

```
<episodedetails>
 <title>Ubuntu ABC</title>
 <episode>1</episode>
 <season>1</season>
</episodedetails>
```Problem is that I need to rename every .avi and .nfo so that they include the <title> also. Like this: Ubuntu Cartoon - S01E01 - Ubuntu ABC.avi / Ubuntu Cartoon - S01E01 - Ubuntu ABC.nfo

Is there easy way to do this? I have about 5000 avi/nfo file.

---

### Post by Vaphell on 2011-01-30
```

#!/bin/bash

find . -name '*.nfo' | while read nfo
                       do
                         title=$( grep '<title>' "$nfo" | sed -r 's:.*<title>(.*)</title>.*:\1:g' )
                         name=${nfo%.nfo}
                         newname="$name - $title"
                         mv -v "$name".nfo "$newname".nfo
                         mv -v "$name".avi "$newname".avi
                       done

```

reads the title from <title></title> and appends it to the file name. It doesn't recognize if the title is already included so don't run it many times - each execution will add the title to the name.

test it first on some junk sample to see if it behaves ok, 5k files messed up by some dumb oversight is not something anyone would want to experience and fix.

---

### Post by umsorg on 2011-01-30
Thank You!

---

### Post by umsorg on 2011-02-22
> **Portmanteaufu said:**
> This should work for all the .avi files in the directory tree. Make sure you have write permissions everywhere, though.

```

#!/bin/bash
find . -name '*.avi' | while read file_name; do
        band_name=`echo $file_name | sed 's/ *-.*$//'` # Get rid of song name
        band_name=`echo $band_name | sed 's/^.*\///'`  # Get rid of file path
        song_name=`echo $file_name | sed 's/^.*- *//'` # Get rid of band name
        song_name=`echo $song_name | sed 's/.avi//'` # Get rid of file extension
        new_file_name=`echo $file_name | sed 's/.avi/.nfo/'` # Make new filename
        echo "Making $new_file_name..."
        echo -en "<musicvideo>\n<title>$song_name</title>\n<artist>$band_name</artist>\n</musicvideo>\n" > "$new_file_name"
done

```

I need to create nfo like this:

```

<episodedetails>
<title>Funny episode</title>
<episode>10</episode>
<season>1</season>
</episodedetails>

```File is Ubuntu show - 1x10 - Funny episode.mkv

I don't need 'Ubuntu show' part with the NFO, but everything els. I tried google, but without any luck. Script almost works for me, but I don't know how to use sed to ignore the 'Ubuntu show' and split 1x10 to episode and season.

---

### Post by Vaphell on 2011-02-22
```

#!/bin/bash

name='Ubuntu show - 1x10 - Funny episode.mkv'

echo old name: $name

name=$( echo "$name" | sed -r 's:Ubuntu\sshow\s*-\s*(.*):\1:g' ) # match Ubuntu ... but use only group 1 (first parentheses)
episode=$( echo $name | grep -oE '[0-9]+x[0-9]+' )  # match [digit]x[digit](1-or-more)
s=${episode%x*}  # throw away x and stuff after
e=${episode#*x}  # throw away x and stuff before
echo name: $name  s:$s  e:$e 

```

---

### Post by sisco311 on 2011-02-22
> **umsorg said:**
> I need to create nfo like this:

```

<episodedetails>
<title>Funny episode</title>
<episode>10</episode>
<season>1</season>
</episodedetails>

```File is Ubuntu show - 1x10 - Funny episode.mkv

I don't need 'Ubuntu show' part with the NFO, but everything els. I tried google, but without any luck. Script almost works for me, but I don't know how to use sed to ignore the 'Ubuntu show' and split 1x10 to episode and season.

Try something like:
```

#!/usr/bin/env bash

while IFS= read -rd '' file; do

  filename="${file##*/}"

  title="${filename%\.mkv}"
  title="${title##* - }"

  episode="${filename#* - *x}"
  episode="${episode% - *.mkv}"

  season="${filename#* - }"
  season="${season%x* - *.mkv}"

  cat > "${file%\.mkv}.nfo" <<< \
"<episodedetails>
<title>${title}</title>
<episode>${episode}</episode>
<season>${season}</season>
</episodedetails>"

done < <(find . -name '*.mkv' -print0)

```

---

### Post by Diametric on 2011-02-22
That was a really cool script.  Thanks for the post.

---

### Post by umsorg on 2011-02-22
Thank you :)

---

