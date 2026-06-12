---
title: "Bash script for converting audio files"
date: 2010-01-12
forum: Programming Talk
---

### Post by Rayve on 2010-01-12
I recently got some iPod Audiobooks on a CD and put them on my computer, but to be able to play them on my mp3 player (not an iPod) I know I need to convert them from .m4b to .mp3.  Here is the script (and where I found it).  It works one at a time (when I use the "single" example, commented out) but running the script (for batches) gives me a Permission Denied error.

Script:
```

#!/bin/bash
# copied from http://intuitivenipple.net/10/converting-mp3s-to-m4b-audiobooks-and-m4b-to-mp3  on 12 Jan 2009
# for single files 
# ffmpeg -i <infile.m4b> -acodec libmp3lame -ar 22050 <outfile.mp3>

# for batch files
for m4b in $(/home/candice/Desktop/AudioBooks_All/*); do ffmpeg -i $m4b -acodec libmp3lame -ar 22050 ${m4b}.mp3; done

```Script in action:
```

candice@candice-desktop:~/Desktop/AudioBooks_All$ /home/candice/Desktop/m4btomp3.sh
/home/candice/Desktop/m4btomp3.sh: line 7: /home/candice/Desktop/AudioBooks_All/01 An Abundance of Katherines.m4b: Permission denied

```The script is 755.  With Google I discovered the issue is not the permissions of the script but that the command called *in* the script doesn't have permission.  How can I give ffmpeg/lame permissions?  Do I need to run it with sudo?

Thanks!

- Rayve

Just in case: running Ubuntu 9.04, mp3 player is the Sansa Fuze.

---

### Post by ssam on 2010-01-12
if you use rhythmbox to copy the files to the mp3 player, it will automatically convert them. (unless it does not know about your player, in which case you can make an .is_audio_player file [http://live.gnome.org/Rhythmbox/FAQ](http://live.gnome.org/Rhythmbox/FAQ) )

---

### Post by ssam on 2010-01-12
the error message is because:
```
$(/home/candice/Desktop/AudioBooks_All/*)
```
is ask it to run every file in that directory, and the files are not executable.

try just
```

for m4b in /home/candice/Desktop/AudioBooks_All/*; do ffmpeg -i $m4b -acodec libmp3lame -ar 22050 ${m4b}.mp3; done

```

the script may still have issues if the files have spaces in their names. there is lots of info around the web, for dealing with this eg [http://www.cyberciti.biz/tips/handling-filenames-with-spaces-in-bash.html](http://www.cyberciti.biz/tips/handling-filenames-with-spaces-in-bash.html)

---

### Post by Rayve on 2010-01-12
ssam,

The other line of code didn't work - now I get:

```

/home/candice/Desktop/AudioBooks_All/02: no such file or directory

```The filenames all have spaces, so I then enclosed the new line in double quotes [oops, read that last line of yours after this! is there something else I should do here?], but now I get this: 

```

Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/candice/Desktop/AudioBooks_All/01 An Abundance of Katherines.m4b':
  Duration: 06:47:58.89, start: 0.000000, bitrate: 33 kb/s
    Stream #0.0(eng): Audio: aac, 22050 Hz, mono, s16
    Stream #0.1(eng): Subtitle: text / 0x74786574
Unable to find a suitable output format for '/home/candice/Desktop/AudioBooks_All/01 Artemis Fowel bk 1.m4b'

```As though it didn't actually go through the encoding process.  

This is what the line looks like now in the script:

```

for m4b in "/home/candice/Desktop/AudioBooks_All/*"; do ffmpeg -i $m4b -acodec libmp3lame -ar 22050 ${m4b}.mp3; done

```Is it not assigning the variable to m4b somehow?  I'm not terribly familiar with for loops yet.

---

### Post by Rayve on 2010-01-12
Okay, so I checked out that site (thanks, ssam!) and here's what I have, minus all my commented stuff:

```

#!/bin/bash
SAVEIFS=$IFS
IFS=$(echo -en "\n\b")
for m4b in /home/candice/Desktop/AudioBooks_All/*; 
do ffmpeg -i $m4b -acodec libmp3lame -ar 22050 ${m4b}.mp3; 
done
IFS=$SAVEIFS

```

And so far it seems to be working.  No errors, at least, and ffmpeg is encoding away!  :)

Thanks so much!

---

