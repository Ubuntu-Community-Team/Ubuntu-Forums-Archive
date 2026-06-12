---
title: "Adding ID3 tags to mp3s"
date: 2007-01-24
forum: Programming Talk
---

### Post by Swab on 2007-01-24
I stupidly managed to rip a few hundred mp3s without ID3 tags.  I know I can use the id3v2 utility to add tags, but how would I go about scripting the whole process?

Luckily the mp3s are in a tree like so:  artist/album/track number - track name.mp3 

I know it must be possible to automate the creation of the tags, I just can't figure out how to loop through the directory tree and set the needed variables to plug into id3v2... any ideas?

---

### Post by Swab on 2007-01-24
for artist in `ls`
do
        echo "$artist"
done

I tried the above in the top level directory, just to see if it can pick out the artist names... the problem is I just end up with a list of individual words.. for example if i had two directories called "pearl jam" and "talking heads" I get a list like:

pearl
jam
talking
heads

Not really useful for setting a variable...

---

### Post by stoffe on 2007-01-25
Try

[FONT="Courier New"]for artist in *[/FONT]

instead. You'll still have to parse the filenames though, when you get there. It's probably easier to do in a script language like ruby or python, or you could use some tool, like EasyTag (it's in the repos).

---

### Post by duff on 2007-01-25
Some quick tips:

use **find** instead of **ls**.  such as

```
find /my/music/directory -name '*.mp3' |
while read x; do
   echo $x
done
```

use **readlink -f** to get the full path of a file

use **basename** and **dirname** to break apart full paths.

So something like (untested code):
```
find $1 -name '*.mp3' | 
while read x; do
   P=$(readlink -f $x)
   SONG=$(basename $P .mp3)
   P=$(dirname $P)
   ALBUM=$(basename $P)
   P=$(dirname $P)
   ARTIST=$(basename $P)
   TITLE=${SONG:5}  # remove first 4 char; ie. "04 - "
   TRACK=${SONG:0:2}  # just the first 2 chars
done
```

---

### Post by duff on 2007-01-25
^^ and you're going to have to add some double quotes in the above code to make sure spaces are preserved.

---

### Post by Swab on 2007-01-25
Thanks for the help guys.  Much appreciated.

---

### Post by Relain on 2007-01-25
use easytag!

---

