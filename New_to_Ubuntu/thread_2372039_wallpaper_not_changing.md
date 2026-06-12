---
title: "wallpaper not changing"
date: 2017-09-20
forum: New to Ubuntu
---

### Post by pagno2 on 2017-09-20
Ubuntu 16.04.3
Appearence - Pictures and folders - Upload some 20 photos in order to have them automatically changing. That doesn't happen. The first photo becomes the desktop.
Wallch installed and uninstalled as not working.
Does anybody have a solution?
GA

---

### Post by again? on 2017-09-20
You can try [Variety]("http://peterlevi.com/variety/").
If you want something lighter you can use a bash script.
Save as **wallpaperChanger** and make executable.
```
#!/bin/bash

#modified by Ruja
#original script by kennethadammiller
#http://ubuntuforums.org/showthread.php?t=1378108

#option "t" sets the timeout time between changing wallpapers in secs
#option "s" sets the setting for when the image is applied as wallpaper
#after these options, place the locations for each of your folders that you
#want to be scanned for wallpapers to be cycled through


#  Add a task to "Startup Applications" with the command:
#  /path/to/wallpaperChanger -t 3600 -s stretched "/path/to/wallpapers/folder1" "/path/to/wallpapers/folder2" "/path/to/wallpapers/folder3"
#   ...

#if launched with -t 0, changes wallpaper once, then exits

#my example: /home/glen/scripts/wallpaperChanger -t 300 -s stretched "/home/glen/Pictures/wallpaper"
a=1
b=1

while getopts ":t:s:" opt;      #get the command line arguments so that 
do                              #it can set the amount of time to sleep for
  case $opt in
        t)
        time=$OPTARG
        a=0
        ;;
        s)
        setting=$OPTARG
        b=0
        ;;
  esac
done

if [ $a = 0 ];  #so yea i guess i couldn't figure out how to get it to work 
  then          #in the opt-while loop above. oh well. it works now.
  shift 2
fi
if [ $b = 0 ];
  then
  shift 2
fi

time=${time:=3600}              #set time to default if the user didn't specify
setting=${setting:=stretch}     #set setting to default of stretched if user doesn't specify
newline='
'                               #$newline variable is easier :)

##change to each of the directories that contain wallpapers
#and add what's in those directories 
##to a newline delimited list
wallpapers=""
while [ "$1" != "" ];
do
	cd "$1"
		for var in {*.jpg,*.png,*.JPG,*.PNG}     #match jpg and png extensions
		do
			if [ -f "$1/$var" ] && [ -r "$1/$var" ];
			then
				if [ "$var" != '*.jpg' ] && #if there is no match for the file type 
				   [ "$var" != '*.png' ] && #in the directory, skip it so that it doesn't
				   [ "$var" != '*.JPG' ] && #cause problems when it goes to change to them
				   [ "$var" != '*.PNG' ];
				then
					wallpapers="$wallpapers$1/$var$newline"
				fi
			fi
		done
	shift
done
count=$(echo "$wallpapers" | wc -l)
#finished adding wallpapers up into newline delimited variable

#get a random $current to select from $wallpapers
repeat=1
while [ $repeat = 1 ];
do
	current=$(($RANDOM % $count)) #random number between 0 and $count-1
	if [ $current -gt 0 ];        #number cannot be 0, if it is just try again
	then
		tempwallpaper="$(echo "$wallpapers" | head -n $current | tail -n 1)"
		gsettings set org.gnome.desktop.background picture-uri file://"$tempwallpaper"
		
		if [ $time != 0 ];
		then
			sleep $time
		else
			repeat=0
		fi
	fi
done
#end
```
Read start of script for how to use.
eg: command to run wallpaperChanger, changing desktop background every 5mins(300 secs)
```
/path/to/wallpaperChanger -t 300 "/path/to/picture/folder"
```
Use your paths.

---

### Post by Impavidus on 2017-09-21
Variety can be installed from the repositories and I read it should work fine.

I made my own bash script to switch wallpapers. On Xubuntu 17.04 the command to set one is```
xfconf-query -c xfce4-desktop -p /backdrop/screen0/monitor0/workspace0/last-image -s "/path/to/file"
```The details often change a bit, I had to modify my script after most upgrades in recent years. It downloads images from different urls depending on time of day, so I wanted some flexibility.

Instead of making a script that sleeps for several minutes before switching the wallpaper again, it may be better to have a script that only switches the wallpaper once and is repeatedly called by cron.

---

### Post by pagno2 on 2017-09-21
Installed Variety from repository.
Nice settings. Seems to be working properly.
Thanks

---

