---
title: "[NAUTILUS SCRIPT] : Verify/Repair an archive with a GUI (using par2 files)"
date: 2007-03-27
forum: Outdated Tutorials &amp; Tips
---

### Post by frodon on 2007-03-27
This script i wrote and called **Par2-Tool** allow you to verify or/and repair an archive with a .par2 file within 3clicks.

**_[SIZE="3"]Introduction :[/SIZE]_**

I always used par2 directly for this purpose till now but it's command line only and it's sometimes boring and not quick to type all these command lines even if they are simple. In addition the goal is to allow someone without any terminal knowledge to easily verify/repair the archive.

This script will use par2 to verify and repair the archive, if you don't have any ".par2" files with your archive then you can't use this method to verify and repair it.

**_[SIZE="3"]Installation :[/SIZE]_**

First you need par2 and zenity to run this script properly : ```
sudo apt-get install par2 zenity
```
Then create the Par2-Tool file : ```
gedit .gnome2/nautilus-scripts/Par2-Tool
```And edit it like that :
```
#!/bin/bash

# Function to test if it's a par2 file
is_par2 ()
{
	file -b "$1" | grep -i 'par2' || echo $1 | grep -i '\.par2$'
}


#### If no file selected, report error ###
if [ $# -eq 0 ]; then
        zenity --error --title="Warning" --text="No files selected"
        exit 1
fi

# if wrong file type selected
if !(is_par2 "$1")
then
	zenity --error --title="Warning" --text="File type not suported"
        exit 1
fi

# Dialog box to choose verify or repair
Action=`zenity --list --title="Par2-Tool" --radiolist --column="Check" --column="Action" "" "Verify" "" "Repair"`

if [ "$Action" = "Verify" ] 
then
	(result=`par2 v "$1" | grep -i "repair is"`
	zenity --info --title "Par2-Tool" --text "Result of the verify : 
	$result"
	) | zenity  --progress --title "Par2-Tool" --text "Verify on going ..." --auto-close --percentage=0
fi


if  [ "$Action" = "Repair" ]
then
	(result2=`par2 r "$1" | grep -i "complete"`
	zenity --info --title "Par2-Tool" --text "Result of the verify : 
	$result2"
	) | zenity  --progress --title "Par2-Tool" --text "Repair on going ..." --auto-close --percentage=0
fi
```Then don't forget to give it execute rights : ```
chmod +x .gnome2/nautilus-scripts/Par2-Tool
```

That's all for the install

**_[SIZE="3"]Usage :[/SIZE]_**

Open nautilus and go to the folder where your archive is then just right click on the .par2 file you have with the archive and you will see **Par2-Tool** in the "script" section, just click Par2-Tool now and follow the GUI messages ;)


This script can surely be improved so feel free to commit improvements and i will put them in this post.
Hope it's useful for some of you.

---

### Post by stuples on 2007-04-01
I've followed the install steps and everythings there and complete. I don't understand how you're ment to use it, what's the "script" section?

---

### Post by frodon on 2007-04-01
You just need to right click on your .par2 file and choose the Par2-Tool script, i took a screenshot to ilustrate this (i will add it to the guide as well) :
[IMG]http://frodubuntu.free.fr/ubuntu/Par2-Tool.png[/IMG]

---

### Post by DC@DR on 2007-04-01
It's handy, thanks frodon! :-)

---

### Post by stuples on 2007-04-01
Awesome it's working! I think I must have had a nautilus window open on another desktop. Nice script. Thanks frodon

---

