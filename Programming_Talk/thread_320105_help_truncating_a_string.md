---
title: "help truncating a string"
date: 2006-12-16
forum: Programming Talk
---

### Post by pickarooney on 2006-12-16
Can anyone help me with a command to cut a trailing space of a string?
It's for a tagging script that reads filenames in the format **singer - songname.mp3**, I want to read the two elements into variables. With bash I can just echo the filename and cut into two fields with the - as delimiter, but that leaves me with a trailing and a leading space.

There's probably some awk or sed command that does this.

---

### Post by Ramses de Norre on 2006-12-16
Remove all whitespace: ```
echo string|sed 's/[[:space:]]//g'
```
Leading and trealing whitespace: ```
echo string|sed 's/^[[:space]]//g' && echo string|sed 's/[[:space]]$//g'
```

Test these before you really use them please, I just wrote these down in a few minutes.

---

### Post by pickarooney on 2006-12-16
I'm getting an unterminated `s' command error.

---

### Post by pickarooney on 2006-12-16
OK, got it.
```

#!/bin/bash

if [ $# -lt 1 ]; then
  echo ""
  echo "Usage: makeid3 <track>"
  exit
fi

filename=$1

album=`basename "$PWD"`
echo album = $album
artist=`echo "$filename"|cut -f1 -d-|sed 's/ *$//'`
echo artist = $artist
song=`echo "$filename"|cut -f2 -d-|sed 's/^ *//'`
echo song = $song

if [ $album == "Music" ]
then
   album=Unknown
fi

id3ed -s "$song" -n "$artist" -a "$album" -q "$filename"

```

---

