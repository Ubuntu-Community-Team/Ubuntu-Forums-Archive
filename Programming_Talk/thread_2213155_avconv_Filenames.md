---
title: "avconv Filenames"
date: 2014-03-25
forum: Programming Talk
---

### Post by ryan-peter-t on 2014-03-25
Hello there, 
I'm having a problem with avconv.

I run the following code:

for file in '/home/ryan/Videos/MusicVideos/'*;
do
avconv -i $file -f mp3 -vn -ab 192k '/home/ryan/Music/'$file;
done

Unfortunately it reports back that it cant find any of the given files.
I believe one problem to be that the filenames has spaces in them, as when it states that it cant find the file. It only shows the part until the first space.

eg.
Filename = 'hello world'
It will state that it couldn't find the file 'hello'

Any help as to why this is would be greatly appreciates.
Kind Regards
Ryan

---

### Post by sisco311 on 2014-03-25
Hi, ryan-peter-t and welcome to the forums!

Thread moved to the **Programming Talk**.

---

### Post by sisco311 on 2014-03-25
You should double quote every expansion and everything that could contain a special character, eg. "$file", "$@", "$(command)"

Also in  your code $file will expand to the full path to the file names:

```

cd /home/ryan/Videos/MusicVideos/ || exit 1
shopt -s nullglob
for file in ./*
do
    avconv -i "$file" -f mp3 -vn -ab 192k /home/ryan/Music/"$file"
do

```

See: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes) and BashPitfalls (link in my signature).

---

### Post by ryan-peter-t on 2014-03-25
Many thanks sisco311.
And sorry I put the post in the wrong area.

Kind Regards
Ryan

---

### Post by sisco311 on 2014-03-25
You are welcome!

---

### Post by andrew.46 on 2014-03-26
Instead of specifying a bitrate (and thus using CBR encoding) you could try vbr with:

```

-qscale:a 2 

```

All the gory details here:

Encoding VBR (Variable Bit Rate) mp3 audio
[http://trac.ffmpeg.org/wiki/Encoding%20VBR%20%28Variable%20Bit%20Rate%29%20mp3%20audio](http://trac.ffmpeg.org/wiki/Encoding%20VBR%20%28Variable%20Bit%20Rate%29%20mp3%20audio)

---

