---
title: "HOWTO: Unmount &amp; eject CD-Rom with a launcher on panel"
date: 2005-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Sam on 2005-07-28
This is annoying to get back to the desktop and right-clic on the CD-Rom icon to eject it. I wrote this script to make it simpler !
[list][*]Create a new file:
```
$ sudo gedit /usr/local/bin/eject_cd
```
[*]Paste the following lines:
```
#! /bin/sh

#
# Try to unmount a CD-Rom device, then eject it.
#

DEVICE="$1"
ZENITY_BIN="/usr/bin/zenity"


#Ctrl-C trapping
trap ctrlc INT
ctrlc()
{
	echo -e "\nAborted by user."
	rm -rf $TMP_DIR
	exit 2
}


#Show a dialog with zenity
#@param  string  The text to display
show_dialog()
{
	if [ "$use_zenity" -gt "0" ] ; then
		zenity --error --title "CD-Rom eject" --info-text "$1"
	fi
}


#Get parameters
if [ "$1" == "-h" ] || [ "$1" == "--help" ] ; then
	echo "Usage: eject_cdrom [-q] DEVICE"
	echo -e "Try to unmount DEVICE then eject it if successful.\n"
	echo "Possible parameters:"
	echo -e "-h, --help\tdisplay this help and exit."
	echo -e "-z, --zenity\tuse zenity to displays errors in dialog windows."
	exit 0
fi

if [ "$1" == "-z" ] || [ "$1" == "--zenity" ] ; then
	if [ ! -x "$ZENITY_BIN" ] ; then
		echo "You must install zenity before that."
		exit 1
	fi
	use_zenity="1"

	device="$2"
else
	use_zenity="0"
	device="$1"
fi


#Device check
#TODO: Check if DEVICE is truly a device.
if [ ! -e "$device" ] ; then
	echo "Parameter DEVICE is not a file."
	exit 1
fi


echo "Trying to eject CD-Rom..."

#Unmount
umount "$device" 2>/dev/null
last_err="$?"

if [ "$last_err" -eq "1" ] ; then
	msg="Cannot unmount device $device (busy)."
	echo "$msg"
	show_dialog "$msg"
	exit 1
fi

#Eject
eject "$device"
last_err="$?"

if [ "$last_err" -ne "0" ] ; then
	msg="Cannot eject device."
	echo "$msg"
	show_dialog "$msg"
	exit 1
fi

exit 0
```
[*]Make the script executable:
```
$ sudo chmod +x /usr/local/bin/eject_cd
```
[*]Create a new launcher on a panel (or wherever you want):
[list][*]Right-clic on the panel
[*]'Add to Panel'
[*]'Custom Application Launcher'
[*]Type this (replace /dev/cdrom with your CD-Rom device):[list][*]Name: Eject CD-Rom
[*]Comment: Unmount and eject the CD-Rom /dev/cdrom
[*]Command: /usr/local/bin/eject_cd -z /dev/cdrom
[*]Icon: /usr/share/icons/gnome/24x24/devices/gnome-dev-removable.png[/list]
[*]Clic 'Close'[/list]
[*]Done !
[/list]

**Note:**
This script uses zenity to display errors. However if you don't want this feature, remove the '-z' parameter.

To install zenity:
```
$ sudo apt-get install zenity
```

---

### Post by rwabel on 2005-07-29
> **Sam]This is annoying to get back to the desktop and right-clic on the CD-Rom icon to eject it. I wrote this script to make it simpler !
[list][*]Create a new file:
```
$ sudo gedit /usr/local/bin/eject_cd
```
[*]Paste the following lines:
```
#! /bin/sh

#
# Try to unmount a CD-Rom device, then eject it.
#

DEVICE="$1"
ZENITY_BIN="/usr/bin/zenity"


#Ctrl-C trapping
trap ctrlc INT
ctrlc()
{
	echo -e "\nAborted by user."
	rm -rf $TMP_DIR
	exit 2
}


#Show a dialog with zenity
#@param  string  The text to display
show_dialog()
{
	if [ "$use_zenity" -gt "0" ]  said:**
>  || [ "$1" == "--help" ] ; then
	echo "Usage: eject_cdrom [-q] DEVICE"
	echo -e "Try to unmount DEVICE then eject it if successful.\n"
	echo "Possible parameters:"
	echo -e "-h, --help\tdisplay this help and exit."
	echo -e "-z, --zenity\tuse zenity to displays errors in dialog windows."
	exit 0
fi

if [ "$1" == "-z" ] || [ "$1" == "--zenity" ] ; then
	if [ ! -x "$ZENITY_BIN" ] ; then
		echo "You must install zenity before that."
		exit 1
	fi
	use_zenity="1"

	device="$2"
else
	use_zenity="0"
	device="$1"
fi


#Device check
#TODO: Check if DEVICE is truly a device.
if [ ! -e "$device" ] ; then
	echo "Parameter DEVICE is not a file."
	exit 1
fi


echo "Trying to eject CD-Rom..."

#Unmount
umount "$device" 2>/dev/null
last_err="$?"

if [ "$last_err" -eq "1" ] ; then
	msg="Cannot unmount device $device (busy)."
	echo "$msg"
	show_dialog "$msg"
	exit 1
fi

#Eject
eject "$device"
last_err="$?"

if [ "$last_err" -ne "0" ] ; then
	msg="Cannot eject device."
	echo "$msg"
	show_dialog "$msg"
	exit 1
fi

exit 0
```
[*]Make the script executable:
```
$ sudo chmod +x /usr/local/bin/eject_cd
```
[*]Create a new launcher on a panel (or wherever you want):
[list][*]Right-clic on the panel
[*]'Add to Panel'
[*]'Custom Application Launcher'
[*]Type this (replace /dev/cdrom with your CD-Rom device):[list][*]Name: Eject CD-Rom
[*]Comment: Unmount and eject the CD-Rom /dev/cdrom
[*]Command: /usr/local/bin/eject_cd -z /dev/cdrom
[*]Icon: /usr/share/icons/gnome/24x24/devices/gnome-dev-removable.png[/list]
[*]Clic 'Close'[/list]
[*]Done !
[/list]

**Note:**
This script uses zenity to display errors. However if you don't want this feature, remove the '-z' parameter.

To install zenity:
```
$ sudo apt-get install zenity
```
 sweet, thanks

---

### Post by f76 on 2005-07-29
How about adding a few lines in the script to temporarily turn of Nautilus annoying automatic file updating feature that hogs the mount while ejecting? 
That would maybe be a usefull allbeit dirty feature.

Ill try your script tonight!/thnx

---

### Post by rwabel on 2005-07-29
[QUOTE=f76]How about adding a few lines in the script to temporarily turn of Nautilus annoying automatic file updating feature that hogs the mount while ejecting? 
That would maybe be a usefull allbeit dirty feature.

Ill try your script tonight!/thnx[/QUOTE]
 didn't know about the automatic file updating.. does it from time to time check the cd if files have been changed? that would be stupid, but explain why sometimes it takes longer to eject

---

### Post by f76 on 2005-07-29
Yes sir. According to some threads it also explains why i cant eject CDs after viewing them(or the properties) in nautilus. 
Nautilus somehow falls in love with my cd and wont let her go..  [-X    Or maybe thats the famd-- i dont know really.

---

### Post by ritger on 2005-07-29
With me it's gam_server that loves the cd's (and some of the harddrives too). You could fix this by doing a killall -9 gam_server in the script, before the unmount. It instantly respawns, but lets go of the mounted drives (the icon stays on the desktop though, go figure).

---

### Post by gammyhand on 2005-08-22
[QUOTE=ritger]With me it's gam_server that loves the cd's (and some of the harddrives too). You could fix this by doing a killall -9 gam_server in the script, before the unmount. It instantly respawns, but lets go of the mounted drives (the icon stays on the desktop though, go figure).[/QUOTE]
 It won't let me save the eject_cd file.

---

### Post by marion on 2005-08-29
Thanks for the script.  I was having issue with ejecting the DVD from xine, and now I just close xine and use your script.  

Thanks much.

---

### Post by DemiUrge8 on 2005-08-30
Is there any way to make the script load the cd tray if you press it again?

---

### Post by Sam on 2005-08-30
[QUOTE=DemiUrge8]Is there any way to make the script load the cd tray if you press it again?[/QUOTE]
It would be a bit complicated. The 'eject -t' command which closes de cd tray exits with the same status if it closes the tray or if it's already closed. So it won't be easy to detect which action to perform (open or close)...

But you can put an another launcher beside to do this !

---

### Post by hubbadub on 2005-10-20
Thanks, worked like a charm for me

---

### Post by blue_chili on 2006-09-15
Fantastic! Worked first time.

---

### Post by naborcoj on 2007-06-17
Thanks. It's helped me a lot!
But I had to adjust some things on this script to make it run error free on my system. Maybe it's related to the version of bash and zenity, as my pc runs Ubuntu 7.04 Feisty.
What I had to change:

1. zenity syntax

```

*Original code:*
zenity --error --title "CD-Rom eject" --info-text "$1"

*Changed code:*
zenity --error --title="CD-Rom eject" --text="$1"

```

2. bash test syntax (it didn't work with ==, but just with a single =)

```

*Original code:*
if [ "$1" == "-h" ] || [ "$1" == "--help" ] ; then

*Changed code:*
if [ "$1" = "-h" ] || [ "$1" = "--help" ] ; then

```

```

*Original code:*
if [ "$1" == "-z" ] || [ "$1" == "--zenity" ] ; then

*Changed code:*
if [ "$1" = "-z" ] || [ "$1" = "--zenity" ] ; then

```

I found this script on [https://help.ubuntu.com/community/EjectCDLauncher](https://help.ubuntu.com/community/EjectCDLauncher) but was unable to report those suggestion there. If you can, please include those changes there, so it can be used by others. It took me some time checking the script until I found what to do.

Thanks again!

---

### Post by vbmds on 2007-07-18
Sorry to say that it did not work for me with my laptop. It did unmount but did not eject. I also did not get any zenity notification(s) either.

---

### Post by gregorvm on 2009-12-26
Thank you, it made  eject-button on my dell studio-xps really work. Before it only functioned if the disk was unmounted already. 

Gregor
Ubuntu Studio on Dell Studio-xps

---

