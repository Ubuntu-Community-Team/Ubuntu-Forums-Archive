---
title: "rss feed alarm clock (making mplayer open randbom file from bash)"
date: 2006-07-04
forum: Programming Talk
---

### Post by kthakore on 2006-07-04
hello there I have created a quick hack that plays rss files as sound to wake me up. ALso it plays a music file
here it is:
```
cd /home/admin/Desktop/alarm
rm -rf alarm.txt
echo "good morning , today is" >> alarm.txt
date >> alarm.txt
echo "... The latest top world stories are " >> alarm.txt
perl rss2html.pl http://www.theglobeandmail.com/generated/rss/BN/International.xml >> alarm.txt
echo "That is it.Time to get up!" >> alarm.txt
mplayer music.wav
mplayer music.wav
mplayer music.mp3
festival --tts alarm.txt
rm -rf alarm.txt 

```
does any one know how I can make mplayer play a random music file from a directory, as right now it only plays the file i point it too:

```
mplayer music.mp3
```

thax in advance

---

### Post by kthakore on 2006-07-04
hey admins can u kick this guy off the forums as he is been posting this @#$% all over the forums.

---

### Post by simonn on 2006-07-04
Have a look at [http://linuxgazette.net/issue55/tag/4.html](http://linuxgazette.net/issue55/tag/4.html) for generating random numbers.

You could put all the music files in a directory, then when you want to pick a random file, count all the files and make a list of them. Generate a random number between 1 and the number of files in the list and then get the file name from the list that corresponds to the random number generated.

I'll leave the details to you :).

---

### Post by kthakore on 2006-07-07
Thx for the reply! I came up with a good alarm clock check it out

```
cd /home/admin/Desktop/alarm
rm -rf alarm.txt
echo "good morning , today is" >> alarm.txt
date >> alarm.txt
echo "... The latest top world stories are " >> alarm.txt
perl rss2html.pl http://www.theglobeandmail.com/generated/rss/BN/International.xml >> alarm.txt
echo "That is it. Time to get up!" >> alarm.txt
mplayer music.wav
mplayer music.wav
amarok -a
amarok -t
DATE1a=$(date +%S)
DATE1b=$(date +%M)
DATE1=$[DATE1b*60]
DATE1=$[DATE1 + DATE1a]

DATE2a=$(date +%S)
DATE2b=$(date +%M)
DATE2=$[DATE2b*60]
DATE2=$[DATE2 + DATE2a]

DATE3=$[DATE2 - DATE1]
while [ $DATE3 -lt 30 ]; do
	DATE2a=$(date +%S)
        DATE2b=$(date +%M)
  	DATE2=$[DATE2b*60]
	DATE2=$[DATE2 + DATE2a]

	DATE3=$[DATE2 - DATE1]
done
amarok -t
festival --tts alarm.txt
rm -rf alarm.txt 

```

Yeah my first bash script is done!!! THANX you oguys

---

### Post by hotdoog on 2007-02-26
I found this on [http://www.macosxhints.com/article.php?story=20051108193636341]("http://www.macosxhints.com/article.php?story=20051108193636341")

> #!/bin/bash
#made by rusl modifying file
#from [http://www.macosxhints.com/article.php?story=20051108193636341](http://www.macosxhints.com/article.php?story=20051108193636341)

# File locations
WritingsPath=/home/hotdoog/Desktop/mp3/
TempLog=/tmp/random-alarm-music.log

# Create a temporary logfile of all matches
find $WritingsPath -iregex ".*.mp3" > $TempLog
find $WritingsPath -iregex ".*.ogg" >> $TempLog
find $WritingsPath -iregex ".*.wav" >> $TempLog

# Choose a random line number (any number from 1 to the length of the file)
LowerBound=1
RandomMax=32767
UpperBound=$(cat $TempLog | wc -l)
RandomLine=$(( $LowerBound + ($UpperBound * $RANDOM) / ($RandomMax + 1) ))

# Use sed to grab the random line
Command=$(sed -n "$RandomLine{p;q;}" "$TempLog")

# open the random line in TextEdit
mplayer "$Command"
And I changed the file extensions [mp3 instead of doc]
And the program to mplayer
And of course the paths to suit my own

So it randomly plays any song in the directory.

Seems to work.

Now I want to integrate it with kthakore's code. And then I will put it into Evolution as a wake up alarm. I will report if it works.

---

