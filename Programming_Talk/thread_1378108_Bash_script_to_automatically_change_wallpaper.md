---
title: "Bash script to automatically change wallpaper"
date: 2010-01-11
forum: Programming Talk
---

### Post by kennethadammiller on 2010-01-11
I've made this. It works completely. It adds the same capability to ubuntu as what windows has

just read the first 20 lines script, it's more than enough to start using it right away

---

### Post by kennethadammiller on 2010-01-11
[http://pastebin.com/f1032ac65](http://pastebin.com/f1032ac65)

sorry, silly me. forgot to add that :)

---

### Post by kennethadammiller on 2010-01-11
and oh yea, there's this

i posted this as well
you guys might take a look.
[http://brainstorm.ubuntu.com/idea/23291/](http://brainstorm.ubuntu.com/idea/23291/)

---

### Post by kennethadammiller on 2010-01-11
nevermind guys. someone just told me about the application drapes. oh well. this was a pretty cool script. worked really well

---

### Post by Potters Son on 2010-01-11
Great idea. Now, if only there was a way to stream Rhythmbox's visualization or a screensaver as the desktop background. *sigh*

---

### Post by kennethadammiller on 2010-01-14
There is. You just have too look around. In fact, i've seen youtube videos where the desktop background is a video. you have to configure xwinwrap to do it; 

only thing is it's not practical. It's not commonly implemented (therefore buggy) and it consumes more cpu doing something that's not productive.

[http://www.youtube.com/watch?v=BhyoCHoXioc](http://www.youtube.com/watch?v=BhyoCHoXioc)

---

### Post by richardjennings on 2010-01-14
dude i want flying through the sky as my background.

how do i do it *arggggggghhhh*

---

### Post by richardjennings on 2010-01-14
[http://tech.shantanugoel.com/resources/downloads/shantz-xwinwrap.zip](http://tech.shantanugoel.com/resources/downloads/shantz-xwinwrap.zip)

gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false

xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet movie.mpg

and its working yay :)

---

### Post by richardjennings on 2010-01-14
incidently, by setting:

gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop true

I have a clickable desktop icons and video!

---

### Post by Matt_Johnson on 2010-01-14
awesome :)

---

### Post by Ruja on 2012-05-14
I modified this script to work with my Ubuntu 11.10 installation, with Gnome Shell 3.2 and works perfectly. I made the wallpapers keep changing randomly. I post the code in case it is useful for someone.

I saved the code to ~/.wallpaperChanger, then opened "Startup Applications" and added a task with the command:

/home/userName/.wallpaperChanger -t 3600 -s stretched "/path/to/wallpapers"

*EDIT: If launched with -t 0, changes wallpaper once, then exits.*

```
#!/bin/bash

#modified by Ruja
#original script by kennethadammiller
#http://ubuntuforums.org/showthread.php?t=1378108

#option "t" sets the timeout time between changing wallpapers
#option "s" sets the setting for when the image is applied as wallpaper
#after these options, place the locations for each of your folders that you
#want to be scanned for wallpapers to be cycled through

#you can save the code to ~/.wallpaperChanger, then open
#"Startup Applications" and add a task with the command:
#
#  /home/userName/.wallpaperChanger -t 3600 -s stretched "/path/to/wallpapers1"
#  "/path/to/wallpapers2" "/path/to/wallpapers3" ...

#if launched with -t 0, changes wallpaper once, then exits

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

---

### Post by ravisghosh on 2012-08-18
Wonderful! This works 100% in 12.04. I tried other scripts that didn't do anything.

---

### Post by ravisghosh on 2012-09-19
Hey Ruja,

This script works perfectly with Unity on Ubuntu 12.04. However, if you are on XFCE, it doesn't work. Could you please help.

---

### Post by Ruja on 2012-10-04
Hey, try changing the line starting with [FONT="Courier New"]gsettings[/FONT] (near the end) to this:

```
xfconf-query -c xfce4-desktop -p /backdrop/screen0/monitor0/image-path -s "$tempwallpaper"
```

You can test this command directly in terminal, replace [FONT="Courier New"]"$tempwallpaper"[/FONT] with the path of some image. Tell me if this worked for you.

---

### Post by Berundo on 2012-10-14
Very useful scripts, thanks guys :)

---

