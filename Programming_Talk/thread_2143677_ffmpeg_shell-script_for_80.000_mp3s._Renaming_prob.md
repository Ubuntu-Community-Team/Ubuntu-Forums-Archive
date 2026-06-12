---
title: "ffmpeg shell-script for 80.000 mp3s. Renaming problems"
date: 2013-05-09
forum: Programming Talk
---

### Post by UnknownFrequency on 2013-05-09
Hi there.

I need to crop 80.000 mp3 files into 30sec sequences.

```

FILES="/Music/*"
for f in $FILES
do
    echo "Processing $f"
    crop="_crop"
    ffmpeg -i "$f" -vn -acodec copy -ss 00:00:00 -t 00:00:30 "$f$crop"
done

```

$crop ofcause get appended after .mp3
I can't seem to figure out how to do it? 
Maybe any other suggestions, that eg. could improve speed etc?
Thank you!

---

### Post by papibe on 2013-05-09
Hi UnknownFrequency.

You can use bash's parameter substitution to get rid of the mp3 extension:
```
$ var=song.mp3
$ newvar="${var%%.mp3}"
$ echo "$newvar"
song
```
where ${var%%.mp3} takes var and trim the '.mp3' from the end of the file. With that in mind you could rewrite your script to something like:
```
#!/bin/bash
FILES="/Music/*"
CROP="_crop"

for file in $FILES
do
    echo "Processing $file"
    newfile="${file%%.mp3}$CROP.mp3"
    **echo** ffmpeg -i "$file" -vn -acodec copy -ss 00:00:00 -t 00:00:30 "$newfile"
done
```
Note that I'm echoing the command instead of actually executing it, so you can debug it and remove it when you feel it running as it should.

Now, there's the slight case that some filenames may content characters that might the above code don't work properly (specially if they are brought from Windows for instance). So just to be extra safe, I'd use this other structure:
```
#!/bin/bash
FILES_DIR="/path/to/Music/"
CROP_STR="_crop"

while IFS= read -d $'\0' -r file
do
    echo "Processing $file"
    newfile="${file%%.mp3}$CROP_STR.mp3"
    **echo** ffmpeg -i "$file" -vn -acodec copy -ss 00:00:00 -t 00:00:30 "$newfile"
done< <(find "$FILES_DIR" -type f -iname '*.mp3' -print0)

```
Note that this even would go recursively over your directory in contrast with just one level of the 'for' loop. Again remove the echo when you won't to do the actual conversion.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Vaphell on 2013-05-09
how much time does a single file take? The script is as simple as it gets, i doubt you can make it noticeably faster. You could throw echo away. Most likely you are limited by the hard drive - 80k files 5MB a pop means reading 400GB of data and assuming 1M of output a pop, writing 80GB. That's a lot.

you can throw echo away to shave off few milliseconds, or make it print at greater intervals, eg counter every 1000 files.
Put crop outside the loop, you repeat the crop=_crop assignment for each file which is not needed given it never changes.
also i don't like the loop definition too much
i'd write it like this
```
music='/Music'
for f in "$music"/*
do
  ffmpeg -i "$f" -vn -acodec copy -ss 00:00:00 -t 00:00:30 "${f%.*}_crop.mp3"
done
```

edit: pabibe's version is more flexible (allows for recursion)

---

### Post by ajgreeny on 2013-05-09
There may be some good reason for using ffmpeg, or should that now be avconv, but either way it could be worth looking at the **mp3splt** package which can split mp3 files without decoding and then re-encoding, so there is no loss of quality.  I use it for single files quite a lot, but have never needed to batch split files in the way you are asking about, though it seems as if it could be done using the -t option on all the mp3 files in a folder, and also I assume recursively.

---

### Post by UnknownFrequency on 2013-05-09
[**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747"): Is there a loss of quality using ffmpeg?

But the mp3splt looks like it does the job as well. 
Thanks to all. It's nice to learn!

---

### Post by ajgreeny on 2013-05-10
> **UnknownFrequency said:**
> [**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747"): Is there a loss of quality using ffmpeg?

But the mp3splt looks like it does the job as well. 
Thanks to all. It's nice to learn!
I'm not totally sure about your ffmpeg quality query, but I thought ffmpeg decoded and then encoded again when it acted on any files in that way; I could well be wrong of course, so wait for more answers from people who know a lot more than I do.

mp3splt is, nevertheless a very useful utility, along with mp3wrap and mp3gain, all of which I use and find worth adding to any OS of mine.

---

### Post by FakeOutdoorsman on 2013-05-10
> **UnknownFrequency said:**
> Is there a loss of quality using ffmpeg?

No, if you copy the audio stream with **-acodec copy** or **-c:a copy**.
Yes, if you re-encode to a lossy format.

---

### Post by ajgreeny on 2013-05-11
> **FakeOutdoorsman said:**
> No, if you copy the audio stream with **-acodec copy** or **-c:a copy**.
Yes, if you re-encode to a lossy format.
So if you split an mp3 into 30 second separate mp3 files does that count as re-encoding or not?

---

### Post by FakeOutdoorsman on 2013-05-11
> **ajgreeny said:**
> So if you split an mp3 into 30 second separate mp3 files does that count as re-encoding or not?

I should have clarified my last post, but the answer is "it depends...". If you do not [stream copy](http://ffmpeg.org/ffmpeg.html#Stream-copy) with **-c:a copy** then ffmpeg will re-encode by default. If you include **-c:a copy** then ffmpeg will demux and mux the section without encoding.

---

### Post by ajgreeny on 2013-05-12
OK, thanks for that, FakeOutdoorsman.

It seems so much easier to use mp3splt to me, but as I said, there may be good reasons for the OP wanting to use ffmpeg.

---

