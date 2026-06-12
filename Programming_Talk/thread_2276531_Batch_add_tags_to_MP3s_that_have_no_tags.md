---
title: "Batch add tags to MP3s that have no tags"
date: 2015-05-03
forum: Programming Talk
---

### Post by GrouchyGaijin on 2015-05-03
Hi Guys,

Background:  I listen to a podcast before I go to bed. The podcast is called Darkness Radio and is actually a comedy program that is nominally about ghosts.  When gPodder downloads the MP3 files, they are not tagged.  That is, the album, artist, title and track number tags are missing.  The Darkness Radio dudes are "too busy" to add tags.

Each file is named as in the example below:
```
darknessradio040215_9p_0_1428028158.mp3
```
The 040215 is the date of the broadcast and the _9p_ is the hour (the 9:00 hour or hour 1 of a 3 hour show)

Until now, I have been using Rhythmbox to tag and sync the fies to my Sony Walkman MP3 player.
In an effort to speed up the tagging process I have been playing with eyeD3 [http://eyed3.nicfit.net/](http://eyed3.nicfit.net/) .  The idea is I could run a script and have the files tagged automatically.

Running the command:
```
 eyeD3 -a "Darkness Radio" -A "April 21 - DR" -t Hour * 
```
will tag each MP3 in the directory with the artist tag Darkness Radio, the album tag April 21 - DR and the track title Hour
eyeD3 supports ```
 -n  
``` for track number.

I have two questions:
1.  Could anyone explain to me what I should do to have the script read the first part of the file name:
```
 darknessradio040215 
``` and change that into a date for example ```
 April 21 - DR 
```

and 

2.  How I can have the script read the time part of the file name which is either ```
_9p_
``` ```
 _10p_
``` or ```
_11p_
``` and then create the title tags of ```
Hour 1
``` ```
 Hour 2 
``` or ```
 Hour 3 
``` as well as the track number tags ```
 1 
``` ```
 2 
``` or ```
 3 
```

---

### Post by steeldriver on 2015-05-03
So it's really a question about extracting substrings from a filename then? you seem to have the actual tagging figured out

You can do stuff like that either using standard text utilities (sed, awk, perl, cut...) or using the shell's own built-in capabilities - see [http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion](http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion)

e.g. given

```

$ f=darknessradio040215_9p_0_1428028158.mp3 

```
split the name into an array separated by underscores
```

$ IFSold="$IFS"
$ IFS=_ ; a=( ${f%.*} )
$ IFS="$IFS_old"

```
result
```

$ echo "${a[0]}"
darknessradio040215
$ 
$ echo "${a[1]}"
9p

```

remove the leading 'darknessradio' substring and/or the trailing 'p' 
```

$ echo "${a[0]#darknessradio}"
040215
$ 
$ echo "${a[1]%p}"
9

```

convert date string to formatted date (NOTE: the result will depend on your system's locale)
```

$ date '+%b %d' --date="${a[0]#darknessradio}"
Feb 15

```

If you actually need to do arithmetic on the date/time (for example if the recordings can span a midnight boundary) then you might be better off using a language that provides datetime modules such as python or perl.

---

### Post by tgalati4 on 2015-05-03
*easytag* has some smart tagging features.  You can set up how to parse the track title and it will automatically fill in the ID3 tags.  It's not a batch file, but a semi-automatic process and works pretty well if the track titles have consistent names.

---

### Post by GrouchyGaijin on 2015-05-03
> **steeldriver said:**
> So it's really a question about extracting substrings from a filename then? you seem to have the actual tagging figured out

You can do stuff like that either using standard text utilities (sed, awk, perl, cut...) or using the shell's own built-in capabilities - see [http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion](http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion)

e.g. given

```

$ f=darknessradio040215_9p_0_1428028158.mp3 

```



Thank you,  Yes I guess it is really a question about extracting substrings from a file name.
I guess the part I do not understand is how to make a script run on each file in a directory and automatically assign values based on parts of each individual file's name.

Specifically, after downloading the MP3s I have a directory with, for example:
```

darknessradio040215_9p_0_1428028158.mp3
darknessradio040215_10p_0_1428028562.mp3
darknessradio040215_11p_0_1428028992.mp3

```

What I am hoping to do is have the script pull out
```
040215
``` from each file and save it as a variable to use in tagging (-A April 2)
Then pull the ```
_9p_
``` and save it as a variable to use with the first track (-t Hour 1) and as a variable to be used with the track number (-n 1).
If the file had ```
_10p_
``` the tags would be -t Hour 2 and -n 2
If the file had ```
_11p_
``` that would be saved as a variable for -t Hour 3 and -n3

Does that make sense?

Basically, I want to be able to download the day's broadcast and have the files tagged with:
The album name Date
The track tag Hour plus 1, Hour 2 or Hour 3 (although 9p, 10p and 11p would be fine)
The track number 1, 2 or 3

---

### Post by Vaphell on 2015-05-03
```
$ IFSold="$IFS"
$ IFS=_ ; a=( ${f%.*} )
$ IFS="$IFS_old"
```

this one is kinda oldschool and arguably ugly, given it requires a global change of IFS affecting so many things.
in bash you can use read for that

```
$ f=darknessradio040215_9p_0_1428028158.mp3
$ IFS=_ read -ra a <<< "${f%.*}"
$ printf '%s\n' "${a[@]}"
darknessradio040215
9p
0
1428028158
```

no global IFS change. Obviously with read you could also read chunks directly into vars.
```
IFS=_ fullname part leftover <<< "${f.%}"
name=${fullname:0:${#fullname}-6}
timestamp=${fullname:${#fullname}-6}
```

---

### Post by Vaphell on 2015-05-03
given that i am a no-life...


```
#!/bin/bash

part_offset=

while read -rd $'\0' fpath
do
    file=${fpath#./}
    IFS=_ read -r fullname part _ <<< "${file%.*}"
    len=${#fullname}
    name=${fullname:0:len-6}

    timestamp=${fullname:len-6}
    ts_m=${timestamp:0:2}
    ts_d=${timestamp:2:2}
    ts_y=${timestamp:4:2}
    day=$( LANG=C date -d "$ts_m/$ts_d/$ts_y" '+%B %d' )
    
    part=${part%p}
    [[ -z $part_offset ]] && part_offset=$(( part-1 ))
    part=$(( part-part_offset ))
    echo "file: $file"
    echo "   name: $name"
    echo "   date: $day"
    echo "   part: $part"
    echo
done < <( find . -iname '*.mp3' -print0 | sort -z -t _ -k1 -Vk2n )
```

out:
```
file: darknessradio040215_9p_0_1428028158.mp3
   name: darknessradio
   date: April 02
   part: 1

file: darknessradio040215_10p_0_1428028562.mp3
   name: darknessradio
   date: April 02
   part: 2

file: darknessradio040215_11p_0_1428028992.mp3
   name: darknessradio
   date: April 02
   part: 3
```

---

### Post by GrouchyGaijin on 2015-05-03
You Sir are my god!  I think I owe you close to a case of beer if you ever come to Sweden!

---

### Post by Vaphell on 2015-05-03
maybe someday... ;-)


i forgot about a very convenient [[ =~ ]] so the alternative to *read* and trimming by hand would be

```
regex='^(.*)([0-9]{2})([0-9]{2})([0-9]{2})_([0-9]+)p_.*$'

while read ...
do
    ...
    [[ $file =~ $regex ]]
    name=${BASH_REMATCH[1]}
    ts_m=${BASH_REMATCH[2]}
    ts_d=${BASH_REMATCH[3]}   
    ts_y=${BASH_REMATCH[4]}
    part=${BASH_REMATCH[5]}

    ...
done < <( ... )
```

---

