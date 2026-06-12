---
title: "Gnome Dynamic Icon"
date: 2009-07-11
forum: Outdated Tutorials &amp; Tips
---

### Post by ycar on 2009-07-11
Hi,
The following is just an idea about how to dynamically modify an icon on Gnome Desktop.
The below steps describe a technique used to make an icon to show the minute last digit.
(Ex: if the current time is 18:03, then an icon on the desktop shows image '3' - see attached image).
[COLOR="Red"]This has no useful meaning, but the idea can be used in other applications where an icon should be dynamically changed.[/COLOR]

**1. Background**
The GNOME Icon file (*.desktop) has a format similar to the below one:
```
	#!/usr/bin/env xdg-open
	[Desktop Entry]
	Encoding=UTF-8
	Exec=firefox %u
	Icon=firefox
	Name=Firefox
	...
```
Where "Icon" tag points to a png file in /usr/share/pixmaps (without specifying the extension *.png). 
And "Name" tag is the title displayed below the icon.
The idea is to dynamically modify these two parameters in an Icon file (to dynamically change the image and title).

**2. Create [0-9].png images**
2.1 Create 10 images (48x48/png) with names 0.png, 1.png, 2.png... 9.png; representing numbers from 0 to 9 (each image has a picture of its number).
2.2 Copy all 10 images to /usr/share/pixmaps/

**3. Create template icon**
3.1 Create $HOME/Temp/0.desktop with the following content (the icon will be used as a template for desktop icon instances):
```
	#!/usr/bin/env xdg-open
	[Desktop Entry]
	Encoding=UTF-8
	Icon=0
	Name=0
```

**4. Create script for generating desktop icon instances**
4.1 Create the following script in $/HOME/bin/track_mins.sh (which will generate icon insatnces, based on current time and icon template):
```
	#!/bin/sh
	# Get minutes last digit
	MIN_LAST_DIG=`date '+%M' | sed 's/.//'`
	# Generate a new icon instance (based on icon template and copy it to the desktop, replacing the old instance)
	sed -e "s/Icon=[0-9]/Icon=${MIN_LAST_DIG}/" \
		-e "s/Name=[0-9]/Name=${MIN_LAST_DIG}/" \
		$HOME/Temp/0.desktop > $HOME/Desktop/min.desktop
```

**5. Modify CRONTAB file**
5.1 Modify crontab file to include the above script to be executed every minute.
```
	$ crontab -e
```
5.2 Add the following line to crontab file:
```
	* * * * * $HOME/bin/track_mins.sh
```

Done :). 
Thanks! (+ sorry for my english :) )

---

### Post by jpeddicord on 2009-07-11
Interesting idea. Approved, thank you for your tutorials & tips contribution.

Also, going to throw this out there: instead of modifying the .desktop entry directly for the new icon, it is also possible to point the Icon line to a symlink. You could then change the symlink in the cron script to point to the corresponding icons. Just a thought. :)

Jacob

---

### Post by ycar on 2009-07-12
Thanks Jacob,
Indeed, for some applications a better solution is to use simlink (point to a different *.desktop files already predefined).
However, my point was to show that *.desktop files could be modified dynamically and this is easy to implement with script+sed+cron. There could be applications where this is the only one solution (let's say you want to dynamically change Icon title) :).
Thanks.

---

