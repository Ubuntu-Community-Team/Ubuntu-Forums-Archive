---
title: "Music folder library cleanup bash script"
date: 2011-04-04
forum: Outdated Tutorials &amp; Tips
---

### Post by diddyb on 2011-04-04
Hey everyone,

If you have your music organized in folders by artist, when you delete music from Rhythmbox or most music players, the folder is never deleted.  If you delete lots of artists through your music player, your library will be full of empty folders.  By empty, I mean no music in them.

So I made a bash script which removes all those folders for you.  Right now, the script will remove all folders which do not contain mp3s or m4as, however simple modification can extend it to look for other media types also.

Simply put the script in your music library folder and run.  You might wanna run it more then once too.  I recommend looking at the script code before you run it though to make sure you are using it correctly.  USE AT YOUR OWN RISK.

```

#!/bin/bash
echo
echo "Written by Brian L Dombrowski, feel free to distribute"
echo
echo "This script removes all folders in the current directory,"
echo "which don't have music files, hence \"cleans up\""
echo
echo "are you sure you want to clean your folders? yes/no"
read VERIFY
if [ "$VERIFY" != "yes" ]; then
	echo "	exiting..."
	sleep 1
	exit
fi



function cleanup {
	echo "Cleaning up dead folders..."
	IFS=',';  # token seperator

	for token in $( ls -m | sed 's/, /,/g' ); do

		cd $token 2> /dev/null
		if [ $? = "0" ]; then
			#check if folder contains mp3s
			FILES=$(ls -R | grep .mp3)
			if [ "$FILES" != "" ]; then
				#folder contains mp3s
				cd ..
				continue
			fi
			#check if folder contains m4as
			FILES=$(ls -R | grep .m4a)
			if [ "$FILES" != "" ]; then
				#folder contains m4as
				cd ..
				continue
			fi

			#folder doesn't contain relevant files
			echo "Deleting $token with files:"
			ls -R
			echo
			cd ..
			rm -rf $token
		fi
	done
}

cleanup
echo
echo "Press enter to exit"
read VERIFY


```

---

