---
title: "I need a BASH/python script written."
date: 2010-05-16
forum: Programming Talk
---

### Post by MetalMusicAddict on 2010-05-16
To anyone who feels kind enough to help a guy out...

I need a script written to go through a dir recursively execute a cmd and name the output file based on the folder it's in, plus one up.

Basically, I have album covers I need to resize (using imagemagick) but rename based on Album/Artist. (just like the dir structure) Resulting files should be put into another dir.

If someone can get me mostly there, I might be able to take it over.

I honestly know what I'm asking. Thanx for any help.

---

### Post by DangerOnTheRanger on 2010-05-16
I could probably do that, but what do you mean by "one up?"

---

### Post by MetalMusicAddict on 2010-05-16
> **DangerOnTheRanger said:**
> I could probably do that, but what do you mean by "one up?"

Meaning, if "FLAC" is where my music is then under that is Artist/Album.

So, now things are /FLAC/Artist/Album/cover.png. The resulting file would be "artist.name-album.name.jpg" Where it would all be lowercase, a dot for spaces and a dash separating artist-album.

I know this is all very specific but the resulting files need to be that way.

---

### Post by DangerOnTheRanger on 2010-05-16
Yeah, I could do that. But it's all really just some bash and sed magic.

---

### Post by MetalMusicAddict on 2010-05-16
> **DangerOnTheRanger said:**
> Yeah, I could do that. But it's all really just some bash and sed magic.

I really didn't think it was *too* crazy, just in my own research, I couldn't get it. :)

---

### Post by hannaman on 2010-05-16
The following would get the filename you want in bash assuming you run this in the directory where the .jpg lives:
```
album=`dirname \`pwd\`` | awk -F/ '{ print tolower($NF) }'`
artist=`dirname \`pwd\`` | awk -F/ '{ name=NF-1; print tolower($name) }'`
mv cover.jpg ${artist}-${album}.jpg
```
Should get you started anyway.

---

### Post by DangerOnTheRanger on 2010-05-16
Rather dense, isn't it?

---

### Post by MetalMusicAddict on 2010-05-16
> **DangerOnTheRanger said:**
> Rather dense, isn't it?

Not sure if that was meant as sarcastic or not. :P

I think part of it for me was getting it to run recursively, as well as where to put my "convert" cmd.

```
#!/bin/bash

for a in *.png
        do

##OUT=`echo "$a" | sed s/"\.png$"/"\.jpg"/g` [SIZE="1"]**(DONT THINK I NEED THIS REALLY)**[/SIZE]

album=`dirname \`pwd\`` | awk -F/ '{ print tolower($NF) }'`
artist=`dirname \`pwd\`` | awk -F/ '{ name=NF-1; print tolower($name) }'`
convert cover.png cover.jpg
mv cover.jpg ${artist}-${album}."$OUT"

done
```

---

### Post by kerry_s on 2010-05-16
"$OUT" should be jpg, if your not using that line.

---

### Post by DaithiF on 2010-05-17
assuming you're starting from a top-level directory (FLAC I think you mentioned), then I would do it something like the below (untested, remove echo statement once its doing what you want):

```
find . -name '*.png' | while read filepath
do
  parent=${filepath%/*}
  grandparent=${parent%/*}
  album=${parent##*/}
  artist=${grandparent##*/}
  echo convert "$filepath" "${artist}-${album}.jpg"
done
```

---

### Post by MetalMusicAddict on 2010-05-30
> **DaithiF said:**
> assuming you're starting from a top-level directory (FLAC I think you mentioned), then I would do it something like the below (untested, remove echo statement once its doing what you want):

Sorry I didn't get back sooner. I went out of town.

YOU ROCK! :)

Works great though now I need to get the outputted files to be all lower case and replace spaces w/underscores. I'll tinker with it myself unless someone is faster than me. :)

Should I try to do it after or before the outputted files?

Thanx again.

---

### Post by saulgoode on 2010-05-30
> **MetalMusicAddict said:**
> ... now I need to get the outputted files to be all lower case and replace spaces w/underscores. I'll tinker with it myself unless someone is faster than me. :)

Your could use the 'tr' command:

```
find . -name '*.png' | while read filepath
do
  parent=${filepath%/*}
  grandparent=${parent%/*}
  album=$(echo ${parent##*/} | tr '[ ][:upper:]' '[_][:lower:]')
  artist=$(echo ${grandparent##*/} | tr '[ ][:upper:]' '[_][:lower:]')
  echo convert "$filepath" "${artist}-${album}.jpg"
done

```

---

### Post by MetalMusicAddict on 2010-05-30
@DaithiF and saulgoode

Thanx so much guys! This will make converting 1000+ album covers of mine MUCH simpler. I belong to another community where we add our self-scanned hi-res album art.

[Album Art Exchange]("www.albumartexchange.com")

I hope others find this script useful.

---

### Post by DaithiF on 2010-05-31
and just for variety, you could also do the lowercasing / space->underscore replacing in sed:
```
album=$(echo ${parent##*/} | sed -r 's/^(.*)$/\L\1/;s/ /_/g'

```

---

