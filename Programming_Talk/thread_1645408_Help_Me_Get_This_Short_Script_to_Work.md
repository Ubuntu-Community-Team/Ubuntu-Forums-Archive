---
title: "Help Me Get This Short Script to Work"
date: 2010-12-14
forum: Programming Talk
---

### Post by Stigmata13 on 2010-12-14
Hello. I'm currently using a program to rip radio streams. The player is console-based, but with an extra option it is able to output the stream, and I am able to save the individual songs. This is great, however no album info is written to it. I found this script, but it doesn't seem to work:
```

#!/bin/bash
# filename update_id3
for file in *.mpg3; do
if test "$file" "==" "*.mpg3"; then
        exit 0;
fi
info=${file%.mpg3}
artist=$(echo $info | cut -d';' -f1)
song=$(echo $info | cut -d';' -f2)
album=$(echo $info | cut -d';' -f3)
length=$(echo $info | cut -d';' -f4)
length=`expr $length "/" 1000`
seconds=`mp3info -p "%S" "$file"`
seconds=`expr $seconds + 4`
if test $seconds -gt $length; then
        id3v2 -a "$artist" -t "$song" -A "$album" "$file";
        album=`echo "$album" | sed "s/[^A-Za-z0-9_-]/_/g"`
        song=`echo "$song" | sed "s/[^A-Za-z0-9_-]/_/g"`
        artist=`echo "$artist" | sed "s/[^A-Za-z0-9_-]/_/g"`
        mv "$file" "$artist#$song#.mp3" 
else
        echo "Remove $song from $artist because file length $seconds and id length $length"
        rm "$file";
fi
done

```The script uses the internal players format strings and "dumps" them into the file name. It assumes the input file has a name like such

**Artist Name;Song Name;Album Name;Track Length.mpg3**

Using the "cut" command, it grabs a given field (f1 for the artist, f2 for the song, f3 for the album, and f4 for the track length.) It then uses the"echo" command, and then writes those fields to the corresponding idv3 tag sections.
The script also compares the "track length" (in seconds format, such as 120 for two minutes) to the mp3info track speed of the mp3. If the actual speed is less than the number in the title, it gets deleted. If not, the file gets renamed in a manor like this:

**"$artist#$song#.mp3"** 
But the problem is that when I use the ";" character in file names as it suggests, it causes a strange overflow in the terminal (crashing the program). I've tried substituting both the ";" in the file name and script with other characters such as ":", "-cut-", etc, but it just ends up leaving the .mpg3 file untouched. As far as I'm aware, this script was written for Ubuntu 8.10, which is quite dated. Can anyone help me get this to work under Maverick?

Thanks in advanced.

[B]EDIT: By using escape characters, "\;" instead of just ";" in the script to make the files, I'm able to get the exact output the script calls for. However, the script still doesn't want to do anything, and leaves the .mpg3 files unchanged.

EDIT 2: Okay... turns out the script didn't have proper permissions. The script is running now, and working fine, however the line:

"$artist#$song#.mp3" 
[/B]
[B]Makes me end up with a song with a title such as:

Artist_Name - Song_Name.mp3

Anyone have any ideas how I can go about having spaces instead of underscores? I'm sure it's got to be something in the script above but I'm not sure what. I think it may be a setting in the script that converts the spaces " " to "_", but I'm not sure what I would change to fix that.
[/B]

---

### Post by cariboo on 2010-12-15
A bump for the move.

---

### Post by Crusty Old Fart on 2010-12-16
This might work:

[INDENT]**[COLOR=Red]~~~ Changed lines shown in red in the code box below. ~~~[/COLOR]**[/INDENT]
```
#!/bin/bash
# filename update_id3
for file in *.mpg3; do
if test "$file" "==" "*.mpg3"; then
        exit 0;
fi
info=${file%.mpg3}
artist=$(echo $info | cut -d';' -f1)
song=$(echo $info | cut -d';' -f2)
album=$(echo $info | cut -d';' -f3)
length=$(echo $info | cut -d';' -f4)
length=`expr $length "/" 1000`
seconds=`mp3info -p "%S" "$file"`
seconds=`expr $seconds + 4`
if test $seconds -gt $length; then
        id3v2 -a "$artist" -t "$song" -A "$album" "$file";
        album=`echo "$album" | sed "s/[^A-Za-z0-9_-]/_/g"`
[COLOR=Red][B]        song=`echo "$song" | sed "s/[^A-Za-z0-9_-]/ /g"`
        artist=`echo "$artist" | sed "s/[^A-Za-z0-9_-]/ /g"`[/B][/COLOR]
        mv "$file" "$artist#$song#.mp3" 
else
        echo "Remove $song from $artist because file length $seconds and id length $length"
        rm "$file";
fi
done

```

---

