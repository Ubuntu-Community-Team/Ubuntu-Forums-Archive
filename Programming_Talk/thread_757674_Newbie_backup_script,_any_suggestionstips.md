---
title: "Newbie backup script, any suggestions/tips?"
date: 2008-04-17
forum: Programming Talk
---

### Post by kinson on 2008-04-17
Hi guys, I've been doing a spot of newbie scripting, mainly for backing up my data to my external drive. I don't need to backup the system, just my pictures, songs etc.

Basically this is my goal:
1) backup to my external's path(which I've set to fixed)
2) have a backup and a backup and check option(cause checking takes quite a while, so backup for quickie backups)
3) rename the folder to current date (i.e. Data ddmmyy)

I've been fiddling with it so far, but I think its getting a little too complex for its own good....thus I wanted to get a second opinion, perhaps I might be screwing myself :p

```

#////////////////////GLOBAL VARIABLES/////////////////////////////
sourcePath="/home/kinson/Data/"
destPath="/media/usbdisk/"
fullDestPath="/media/usbdisk/"
folderVar="Data"\ $(date +%d%m%y)



#////////////////////FUNCTIONS/////////////////////////////
showMenu(){
echo "1)Backup (Daily Use)"
echo "2)Backup and Check Differences (Takes a long time)"
echo "3)Quit"
}


backupData(){ #Function to backup the data ONLY, much faster after everything's been backed up once
echo "preparing to backup the data now..."

rsync -av --delete $sourcePath $destPath"/Data\ 280108/" > /home/kinson/Desktop/Backup_Script_Report.log

echo "finished backing up the data..."
}

checkData(){ #Function to check if the data has been backed up, and output to a log file
	echo "Will now proceed to check the differences(hopefully none) in the data..."

	diff -ru /home/kinson/Data/ /media/usbdisk/Data\ 280108/ > /home/kinson/Desktop/compareBackupData.log

	echo "finished checking the data..."
}

thankExit(){ #Function to thank the user, and exit the script
	echo -e "\nThank you for using my backup program."
	echo "The program will now exit...."
	exit
}

checkFolderExist(){#unfinished
	echo "Checking to see if folder exists..."

	if [ -d Data\ ?????? ]; then
		if [ Data\ ?????? != "$folderVar" ]; then
			echo "Renaming existing backup folder to current date...
			mv "$destPath"Data\ ?????? "$fullDestPath"
			echo -e "\nfinished renaming the previous folder"
		fi
	else
		while [ 1 ]
		do
			echo "Folder doesn't exist yet, create?"
			read -p "Do you want to create the folder and continue backup job?(y/n)"	
	
			if [ "$REPLY" = "y" ]; then
				echo "Creating folder for backup"
				break
			elif ["$REPLY" = "n"]; then
				echo "Exiting program..."
				exit		
			else
				echo "Please enter 'y' or 'n'"
			fi
		done
	fi
}

#////////////////MAIN///////////////////////////
#Clear screen and start program
clear

#prepare the fullDestPath variable
#e.g. /media/usbdisk/Data\ 280108/
fullDestPath=$fullDestPath$folderVar

echo "*************************************************"
echo "*                                               *"
echo "*                                               *"
echo "*                                               *"
echo "*    Welcome to Kinson's backup script(v0.1)    *"
echo "*                                               *"
echo "*                                               *"
echo "*                                               *"
echo "*************************************************"
echo $fullDestPath
while [ 1 ]
do #Loop the whole program until exit

	echo -e "Please make a selection:\n"
	showMenu

	read CHOICE
	case "$CHOICE" in
	"1")# Backup (Daily Use)
		backupData
	;;
	"2")#Backup and Check Differences (Takes a long time)"
		backupData
		checkData	
	;;
	"3")#Quit
		thankExit
	;;
	*)
	echo "Please make a valid selection"
	;;
	esac
done

```

Currently I'm finishing up that "checkFolderExist" function...but it seems kinda uneccessary. Since there's only gonna be one Data xxxxxx folder there, but just thought that it'd be a good experience. And to check if "Data ?????" exists by using wildcards seems a little tacky.....any comments would be welcome, cheers :)

Kinson

---

### Post by ghostdog74 on 2008-04-17
try not to name your folders with spaces. Also to reduce the amount of echoes, you can use HERE document.

---

### Post by eldragon on 2008-04-17
is this for scripting practices or you just need a reliable backup system?

if its just a backup system you need. install from the repos rsnapshot (which is a script that implements rsync and incremental backups) and configure that. not that hard, can be automated, and its incremental.

if you are practicing scripting, then forget what i said :D

---

### Post by kinson on 2008-04-18

> is this for scripting practices or you just need a reliable backup system?

Well, both really. I love the idea/practice of scripting to automate tasks, as its a really good concept. Ideally I suppose I just want something that I will setup in a crontab or double-click and run the shell script. Its both for learning and for practical purposes :)

> if its just a backup system you need. install from the repos rsnapshot (which is a script that implements rsync and incremental backups) and configure that. not that hard, can be automated, and its incremental.

I'll take a look at rsnapshot, but what I want is really simple..I just want a copy of my files in my external. which rsync -av --delete seems to do just fine, hehe :)

Perhaps my problem is just that I've made things a little too complicated here...but then again, I want to learn too :)

Cheers,
Kinson

---

### Post by kinson on 2008-04-18
> **ghostdog74 said:**
> try not to name your folders with spaces. Also to reduce the amount of echoes, you can use HERE document.

Noted(regarding the spaces), thanks :)

I tried reading up a little on the here documents, but it seems a little confusing, will need to read it carefully, hehe. thanks for the suggestion :)

---

### Post by ghostdog74 on 2008-04-18
> **kinson said:**
> Noted(regarding the spaces), thanks :)

I tried reading up a little on the here documents, but it seems a little confusing, will need to read it carefully, hehe. thanks for the suggestion :)

not confusing at all. in the script
```

cat << EOF
*********************************
**    My backup script
**    Author: The WHO
******************************** 
EOF


```

---

### Post by eldragon on 2008-04-19
well, rsnapshot is all you are doing apparently.

a) runs from crontab
b) can be run manually
c) uses rsync to copy. 
d) supports incremental backups through ext3 hardlinks (aka, if stuff didnt change, its a hardlink it creates to the backuped file.)


one thing it lacks is the option of sending a mail when everything goes wrong, so that you do get to know when backups fail.

you could add that to your script :D

---

