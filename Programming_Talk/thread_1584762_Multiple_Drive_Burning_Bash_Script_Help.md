---
title: "Multiple Drive Burning Bash Script Help"
date: 2010-09-29
forum: Programming Talk
---

### Post by tmckellar on 2010-09-29
Hello all, I've been working on a project for about a week and I've hit a wall with part of it. I have a bash script that allows me to burn a CD on multiple drives at once. The script itself works great as is but I'm looking to add a little idiot proofing to it. This is it at the current stage of development which will get cleaned up before it gets put into use.

```
#!/bin/bash

tempwav=${1%.*}.wav

newwav=${1%.*}-burn.wav

val=$(($2-1))

IFS=$'\n'

if [ "${1/*.}" == "flac" ]
then
	if file -b "$1" | grep -i 'mono'
	then
		flac --decode $1
		sox  $tempwav -c 2 $newwav
		rm $tempwav
	elif file -b "$1" | grep -i 'stereo'
	then
		flac --decode $1
		mv $tempwav $newwav
	fi
elif [ "${1/*.}" == "mp3" ]
then
	if file -b "$1" | grep -i 'monaural'
	then
		lame --decode $1 $tempwav
		sox  $tempwav -c 2 $newwav
		rm $tempwav
	elif file -b "$1" | grep -i 'stereo'
	then
		lame --decode $1 $newwav
	fi
elif [ "${1/*.}" == "ogg" ]
then
	if file -b "$1" | grep -i 'mono'
	then
		oggdec $1 
		sox  $tempwav -c 2 $newwav
		rm $tempwav
	elif file -b "$1" | grep -i 'stereo'
	then
		oggdec $1
		mv $tempwav $newwav
	fi
fi

for i in $(seq 0 $val)
do
	if [ ! -f "$newwav" ]
	then
	exit 0
	else
	cdrecord -eject dev=/dev/scd$i -audio -tao -pad $newwav | tee >(zenity --progress --pulsate --text "Burning $1 to CD") >burn.txt &
	sleep 2
	fi
done
#rm $newwav
```

I've made another script that acts as a gui for it but it basically works like this in a terminal, $1 being the file and $2 being the number of copies inside the script.

```
audiomultiburn.sh 13-ReYourBrains.flac 2
```

Here's the trouble I've ran into. The purpose of this is to burn audio CD's after a church service. We might make 4 CD's of 4 different services at once. I'd like to be able to check if a drive is busy burning a CD already and skip to the next available drive. I've got it kind of working where if the first drive is busy it will skip to the next one but if drive 2 is busy then it errors out. This is what I'm using currently in a separate script to test this functionality.

```
#!/bin/bash

val=$(($1-1))

for i in $(seq 0 $val)
do
	if ! cdrecord --inq dev=/dev/scd$i &> /dev/null
	then
		echo "$i cannot be accessed by cdrecord. Continuing without it."
		echo "$(($i+1)) being used instead" &
	fi
done
```

Any suggestions would be greatly appreciated.

---

### Post by tmckellar on 2010-10-14
Anybody have any ideas here? At all?

---

