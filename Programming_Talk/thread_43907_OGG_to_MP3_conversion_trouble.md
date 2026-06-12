---
title: "OGG to MP3 conversion trouble"
date: 2005-06-23
forum: Programming Talk
---

### Post by pdpi on 2005-06-23
I'm having a bit of trouble doing a nice bash script to convert an ogg album into mp3 (the iPod demands...). I'd rather not use one of those nifty ogg2mp3 converters, as the shell practice would do me some good :)

this is what it looks like thus far:
```
for SONG in 1*.ogg; do ogg123 $SONG -d wav -f - | lame -q2 -b160 --id3v2-only --ta The\ Doors --tl Legacy:\ The\ Very\ Best\ Of\ Disc\ 1 --tt \"`(echo $SONG|sed s/[0-9]*-the_doors_//| sed s/-xmr.ogg//)|sed s/_/" "/g`\" - `echo $SONG |sed s/\.ogg/\.mp3/`;done
```

as far as I can tell, this is getting borked in the bit that sets the id3 tag for the title:

```

--tt \"`(echo $SONG|sed s/[0-9]*-the_doors_//| sed s/-xmr.ogg//)|sed s/_/" "/g`\"

```

lame says this:
```

lame: excess arg 110-the_doors_people_are_strange-xmr.mp3ut Buffer 100.0%

```


the files are named like so (first digit is the disc number):
```

213-the_doors_the_changeling-xmr.ogg

```
so you can understand the sort of manipulation I'm trying to pull off. Can anyone help?

---

