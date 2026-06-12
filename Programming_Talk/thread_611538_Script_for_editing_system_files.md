---
title: "Script for editing system files"
date: 2007-11-13
forum: Programming Talk
---

### Post by ncwilde43 on 2007-11-13
Hello,

As a beginner, I decided to dab around in bash scripting and thought I'd write a simple script that opens the sources.list, menu.lst, fstab and xorg.conf files for easy edit.  Please take a look at the script and let me know if there is anything else you want me to add or edit.  I really need the practice!

```

#!/bin/bash

#DECLARE COMMAND FOR PREFERRED EDITOR
	#I.E. 
		#GNOME EDITOR, 	EDITCMD="gedit"
		#BLUEFISH, 	EDITCMD="bluefish"
EDITCMD="gedit"

#DECLARE DEB SOURCE VARIABLES
SOURCE="sources.list"				#ZENITY WINDOW, COLUMN 2 DISPLAY VARIABLE 
SOURCEDIR="/etc/apt/sources.list"		#DIRECTORY SOURCES.LIST IS LOCATED
SOURCEDESC="APT Sources List"			#DESCRIPTION OF SOURCES.LIST

#DECLARE GRUB EDIT VARIABLES
GRUB="menu.lst"					#ZENITY WINDOW, COLUMN 2 DISPLAY VARIABLE
GRUBDIR="/boot/grub/menu.lst"			#DIRECTORY MENU.LIST IS LOCATED
GRUBDESC="Grub Boot Menu List"			#DESCRIPTION OF MENU.LST

#DECLARE XORG VARIABLES
XORG="xorg.conf"				#ZENITY WINDOW, COLUMN 2 DISPLAY VARIABLE
XORGDIR="/etc/X11/xorg.conf"			#DIRECTORY XORG.CONFIG IS LOCATED
XORGDESC="Xorg Configuration File"		#DESCRIPTION OF XORG.CONF

#DECLARE FSTAB VARIABLES
FSTAB="fstab"					#ZENITY WINDOW, COLUMN 2 DISPLAY VARIABLE
FSTABDIR="/etc/fstab"				#DIRECTORY FSTAB IS LOCATED
FSTABDESC="File Systems Table"			#DESCRIPTION OF FSTAB FILE

#START ZENITY WINDOW LIST
ans=$(zenity  \
	--list  \
	--title="Edit System Files" \
	--text "Pick which file to edit:" \
	--radiolist  \
	--height=240 \
	--width=310 \
	--column "Pick" \
	--column "File" \
	--column "Description" \
	TRUE "$SOURCE" "$SOURCEDESC"\
	FALSE "$GRUB" "$GRUBDESC" \
	FALSE "$XORG" "$XORGDESC"\
	FALSE "$FSTAB" "$FSTABDESC");

#CASE STATEMENT
case "$ans" in
	$SOURCE)
		gksudo $EDITCMD $SOURCEDIR
		;;
	$GRUB)
		gksudo $EDITCMD $GRUBDIR
		;;
	$XORG)
		gksudo $EDITCMD $XORGDIR
		;;
	$FSTAB)
		gksudo $EDITCMD $FSTABDIR
		;;
esac

```

---

### Post by erfahren on 2007-12-04
that script is actually pretty nifty. I like it. The menu is nice. Instead of typing in "sudo gedit */this/that/andthe.other*" you just need to launch the script.

I actually found this post when I was going to post my little script I made. I made it just to back up the configuration files I usually edit after a fresh install. I oftentimes forget to back them up before I go and edit them. It's not nearly as nice as the one above, but it's functional and works for me.

```

#!/bin/bash

sysfile1=/etc/fstab
sysfile2=/etc/X11/xorg.conf
sysfile3=/etc/default/acpi-support
sysfile4=/etc/network/interfaces
sysfile5=/etc/apt/sources.list
sysfile6=/boot/grub/menu.lst

if [ -f "$sysfile1" ]; then
    sudo cp $sysfile1 $sysfile1'_backup-fresh'
    echo "backup of $sysfile1 created successfully!"
else
    echo "$sysfile1 not found. No backup created."
fi

if [ -f "$sysfile2" ]; then
    sudo cp $sysfile2 $sysfile2'_backup-fresh'
    echo "backup of $sysfile2 created successfully!"
else
    echo "$sysfile2 not found. No backup created."
fi

if [ -f "$sysfile3" ]; then
    sudo cp $sysfile3 $sysfile3'_backup-fresh'
    echo "backup of $sysfile3 created successfully!"
else
    echo "$sysfile3 not found. No backup created."
fi

if [ -f "$sysfile4" ]; then
    sudo cp $sysfile4 $sysfile4'_backup-fresh'
    echo "backup of $sysfile4 created successfully!"
else
    echo "$sysfile4 not found. No backup created."
fi

if [ -f "$sysfile5" ]; then
    sudo cp $sysfile5 $sysfile5'_backup-fresh'
    echo "backup of $sysfile5 created successfully!"
else
    echo "$sysfile5 not found. No backup created."
fi

if [ -f "$sysfile6" ]; then
    sudo cp $sysfile6 $sysfile6'_backup-fresh'
    echo "backup of $sysfile6 created successfully!"
else
    echo "$sysfile6 not found. No backup created."
fi

exit 0

```
note to newbies: you can make a directory named "bin" in your home folder ( /home/*username*/bin ) for scripts. Bash will look there when you type in the name of the script at the command line. 

to make a script in there executable, do: chmod +x ~/bin/*name-of-script*
(no sudo needed)

In Ubuntu, its set up by default to look there (in the ~/.profile - it's a hidden file in your home directory)
for more info on all that see:
[http://www.linuxcommand.org/wss0010.php](http://www.linuxcommand.org/wss0010.php)
[http://ubuntuforums.org/showthread.php?t=363796](http://ubuntuforums.org/showthread.php?t=363796)

---

### Post by Majorix on 2007-12-04
Why did you choose bash scripting? Python can do that and more.
[www.python.org](www.python.org)

---

### Post by ncwilde43 on 2007-12-04
> **erfahren said:**
> 
note to newbies: you can make a directory named "bin" in your home folder ( /home/*username*/bin ) for scripts. Bash will look there when you type in the name of the script at the command line. 
In Ubuntu, its set up by default to look there (in the ~/.profile - it's a hidden file in your home directory)
for more info on all that see:
[http://www.linuxcommand.org/wss0010.php](http://www.linuxcommand.org/wss0010.php)
[http://ubuntuforums.org/showthread.php?t=363796](http://ubuntuforums.org/showthread.php?t=363796)

Thanks for the tips!

> **Majorix said:**
> Why did you choose bash scripting? Python can do that and more.
[www.python.org]("http://www.python.org")

I used bash script because of my familiarity with the language and lack of knowledge on object oriented languages.  Python seems like a fairly simple language so maybe I'll try replicating the script using it.

---

### Post by Wybiral on 2007-12-04
> **ncwilde43 said:**
> I used bash script because of my familiarity with the language and lack of knowledge on object oriented languages.  Python seems like a fairly simple language so maybe I'll try replicating the script using it.

Actually, you don't really have to understand OOP for Python, it's entirely capable of OOP, functional, and procedural. The big thing about Python, however, is namespaces. But that's pretty easy to get used to.

---

