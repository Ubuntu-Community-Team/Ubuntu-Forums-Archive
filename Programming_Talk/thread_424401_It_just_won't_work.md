---
title: "It just won't work"
date: 2007-04-26
forum: Programming Talk
---

### Post by allyourzigg on 2007-04-26
I'm unsure whether or not this should be here or in general but I have a small script that is designed to play a song (in this case reveille) at a certain time (thanks cron) to wake me up. The problem is that it will work fine when I run the script manually for testing but when cron attempts to run it I hear no sound and do not wake up.
the only thing that appears to not be working is the sound because the volume does change and go back. The commands each work individually in cron.

```
#!/bin/bash

VOL="40"
SND_FILE="/root/sound/reveille.mp3"

if [ "$UID" = '0' ]
then
	#Check volume and push it to variable
	CUR_VOL=`amixer -c 0 | grep Mono\: | cut -d [ -f 1 | cut -c 18-19`

	#Set New volume so I don't get scared out of bed	
	amixer -c 0 set PCM $VOL\%

	#Play file
	mpg321 $SND_FILE

	#Set Volume back to original level
	amixer -c 0 set PCM $CUR_VOL\%
	exit 0
else
	echo "You are not root! Please become root to run this script"
	exit 67
fi

```

---

### Post by allyourzigg on 2007-04-26
I FIXED IT! :KS :KS 

It seems that mpg321 didn't detect that esd was running correctly and attempted to play using alsa but esd blocked the sound card and no sound came out. Adding the -o esd option fixed it, I also added -q so it wouldn't gum up the syslog with as much output

```
#!/bin/bash

VOL="40"
SND_FILE="/root/sound/reveille.mp3"

if [ "$UID" = '0' ]
then
	#Check volume and push it to variable
	CUR_VOL=`amixer -c 0 | grep Mono\: | cut -d [ -f 1 | cut -c 18-19`

	#Set New volume so I don't get scared out of bed	
	amixer -c 0 set PCM $VOL\%

	#Play file
	mpg321 -q -o esd $SND_FILE

	#Set Volume back to original level
	amixer -c 0 set PCM $CUR_VOL\%
	exit 0
else
	echo "You are not root! Please become root to run this script"
	exit 67
fi
```

---

