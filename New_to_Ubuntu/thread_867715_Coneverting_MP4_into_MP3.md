---
title: "Coneverting MP4 into MP3"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by K-D on 2008-07-23
Hey guys,

Still new to linux and I was wondering if anyone new of some software that i can convert MP4's into MP3's  I used to use ITUNES which did it automatically but am struggling to find anything for Ubuntu 8.04.

Cheers

---

### Post by Bachstelze on 2008-07-23
ffmpeg can do it. However, I'm not sure about whether the version of it shipped with Ubuntu supports encoding into mp3.

```
sudo apt-get install ffmpeg
ffmpeg -formats | grep mp3
```

What does that give you ?

---

### Post by kevmitch on 2008-07-23
Indeed, this is a problem I have run into myself. I have written the following script that uses mplayer to convert the .mp4 to a .wav and uses lame to compress the wav back to mp3. Of course you have to have both installed. Actually, it will convert pretty much any thing to mp3.
```

#!/bin/sh
for file in $@ ; do
     name=`echo $file | sed -e "s/\....$//g"`
     echo dumping $file to $name.wav
     mplayer -ao pcm:file="$name.wav" "$file"
     echo encoding $name.wav to $name.mp3
     lame --preset standard "$name.wav" "$name.mp3"
     rm "$name.wav"
done

```
I'm a little baffled as to why mencoder won't just make the mp3 itself since it does have built-in support for lame, but I guess that's just how it goes.

If you're interested I also have a perl script that will convert the tags. In fact, the full version of the above script calls it. But I thought I'd try and keep things simple to start out.

---

### Post by Archmage on 2008-07-23
Please keep in mind that each format are a losing codec. If you convert to a second codec you'll have a poorer quality.

---

### Post by kevmitch on 2008-07-23
Oh wow, it looks like ffmpeg will do it direct. With

```
ffmpeg -i $name.m4a -acodec libmp3lame -ab 128 -ac 2 $name.mp3 
```

Unfortunately, it doesn't appear to have any ability to give the "--preset standard" option to lame to get a variable bitrate file, and worse doesn't seem to want to exceed the 128kbps specified by the "-ab"  option above. 
Ffmpeg, does however have the handy option of piping output to stdout. This can in turn, be piped directly to lame where you can give it all the options you want. This also has the advantage that ffmpeg does not need lame support compiled in.

```
ffmpeg -i $name.m4a -ac 2 -f wav - | lame --preset standard - $name.mp3
```

---

### Post by kevmitch on 2008-07-23
So the above script is drastically simplified to 
```

#!/bin/sh
for file in $@ ; do
     name=`echo $file | sed -e "s/\....$//g"`
     ffmpeg -i $fname -ac 2 -f wav - | lame --preset standard - $name.mp3
done

```

---

### Post by kevmitch on 2008-07-23
oops sorry, I've corrected my above commands

---

### Post by K-D on 2008-07-23
> **kevmitch said:**
> So the above script is drastically simplified to 
```

#!/bin/sh
for file in $@ ; do
     name=`echo $file | sed -e "s/\....$//g"`
     ffmpeg -i $fname -ac 2 -f wav - | lame --preset standard - $name.mp3
done

```


Is this written in the terminal?

---

### Post by mjwhitfield on 2008-07-23
> **Archmage said:**
> Please keep in mind that each format are a losing codec. If you convert to a second codec you'll have a poorer quality.+1.  Don't transcode from lossy to lossy formats, you'll make your ears cry.

---

### Post by kevmitch on 2008-07-23
> **K-D said:**
> Is this written in the terminal?
No, sorry, it's a shell script. 

Open up a new next file in /usr/local/bin called mp42mp3

```
gksudo gedit /usr/local/bin/mp42mp3
```

Paste the script into the file and save it. Then you'll have to make it executable:
```
sudo chmod +x /usr/local/bin/mp42mp3
```


then you should be able to run it as a command from any directory (since /usr/local/bin is in your path).

```
mp42mp3 *.mp4
```

In a directory with .mp4 files will create a bunch of converted .mp3 files in that same directory.

---

### Post by Rosicrucian on 2008-07-29
Has anyone had any success with this so far since the last post?

---

### Post by gjoellee on 2008-07-29
you should try ConvertIt....and easy graphical converter which converts many more files then just mp3 and mp4! Read mroe here: [http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

---

### Post by clouserw on 2009-01-26
> **kevmitch said:**
> So the above script is drastically simplified to 
```

#!/bin/sh
for file in $@ ; do
     name=`echo $file | sed -e "s/\....$//g"`
     ffmpeg -i $fname -ac 2 -f wav - | lame --preset standard - $name.mp3
done

```

This script completely ignores quoting and will break on anything with a space or other shell character.  A better script is:

```

#!/bin/sh
for file in "$@" ; do
     name=`echo "$file" | sed -e "s/.mp4$//g"`
     ffmpeg -i "$file" -ac 2 -f wav - | lame --preset standard - "$name.mp3"
done

```

---

### Post by kenai- on 2009-03-30
> **kevmitch said:**
> No, sorry, it's a shell script. 

Open up a new next file in /usr/local/bin called mp42mp3

```
gksudo gedit /usr/local/bin/mp42mp3
```

Paste the script into the file and save it. Then you'll have to make it executable:
```
sudo chmod +x /usr/local/bin/mp42mp3
```


then you should be able to run it as a command from any directory (since /usr/local/bin is in your path).

```
mp42mp3 *.mp4
```

In a directory with .mp4 files will create a bunch of converted .mp3 files in that same directory.

Thanks a bunch Kev! That Shell script worked **perfectly**. :D

---

### Post by MrWES on 2009-03-30
Kind of after the fact; but I believe WinFF will convert mp4 to mp3.

[http://winff.org/html/]("http://winff.org/html/")

Bill

---

