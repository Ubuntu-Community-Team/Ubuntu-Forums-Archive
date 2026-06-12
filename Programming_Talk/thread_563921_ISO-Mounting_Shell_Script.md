---
title: "ISO-Mounting Shell Script"
date: 2007-09-30
forum: Programming Talk
---

### Post by steevols on 2007-09-30
At the prodding of a buddy, I'm trying to write a GUI-based ISO mounter shell script...

I got it going as far as asking for the file, etc, but when it tries to mount, it needs a su account.

So, my question is, is there a tool to ask for sudo'ing in a dialog box?

```


# Trey and Stephen's ISO Mounter Shell Script
# Requires Zenity for dialog boxes to work.

# Ask for ISO - - -

        FILE=`zenity --file-selection --title="Select a File"`

        case $? in
                 0)
#                       echo "\"$FILE\" selected.";;
			zenity --info --text="\"$FILE\" has been selected.";;
        esac

# Inform that it's been selected.

mount $FILE /home/stephen/Desktop/ISOMount -o loop
        
# zenity --notification --window-icon="info" --text="ISO Mounter Active"



```

---

### Post by Waappu on 2007-09-30
Hi

Here is same kind script that I found

```

#!/bin/bash

foo=`gksudo -u root -k -m "Enter your password for ISO Mounter root access" echo "Do you have root access?"` 

if (mount | grep "$*"); then

	if sudo umount /media/ISO/"$*"; then
		sudo rmdir /media/ISO/"$*";
		zenity --info --title "ISO Mounter" --text "Successfully unmounted /media/ISO/$* !";
		exit 0;
	else
		zenity --error --title "ISO Mounter" --text "Cannot un-mount $* !";
		exit 1;
	fi;

else

	if [ -e /media/ISO/"$*" ]; then
		sudo rmdir /media/ISO/"$*";		
	fi;

	sudo mkdir /media/ISO/"$*";

	if sudo mount -o loop -t iso9660 "$*" /media/ISO/"$*"; then
	        if zenity --question --title "ISO Mounter" --text "$* Successfully Mounted. Open Volume ?";
	        then
	                nautilus /media/ISO/"$*" --no-desktop;
	        fi;
	        exit 0;
	else
	        sudo rmdir /media/ISO/"$*";
	        zenity --error --title "ISO Mounter" --text "Cannot mount $* !";
	        exit 1;
	fi;
fi;

```

---

### Post by dwhitney67 on 2007-09-30
I am not familiar with the GUI aspects you are trying to accomplish, however what is the behaviour when you precede the 'mount' command with a 'sudo'?  In other words:

[FONT="Courier New"]sudo mount -o loop ISOimage destFolder[/FONT]

---

### Post by robert_pectol on 2007-09-30
Another example that might assist you:

[http://rob.pectol.com/myscripts/iso-mounter.sh.txt](http://rob.pectol.com/myscripts/iso-mounter.sh.txt)

Good luck!

---

### Post by ryanVickers on 2007-09-30
> **steevols said:**
> ...
So, my question is, is there a tool to ask for sudo'ing in a dialog box?



gksudo instead of just sudo

---

### Post by Quikee on 2007-09-30
A tip - with [fuseiso]("http://fuse.sourceforge.net/wiki/index.php/FuseIso") (should be in the repository however the version might be old) you don't have to be root to mount iso files.  It even supports other CD/DVD formats.

---

### Post by steevols on 2007-09-30
Thanks for the tips all! If I complete this, I'll post it here, and maybe even try to get it into the main *Buntu apt servers.

---

### Post by ryanVickers on 2007-09-30
> ...and maybe even try to get it into the main *Buntu apt servers.

How exactly do you do this?  I've got a pretty decent script that deserves that I think! (sig.)

---

### Post by steevols on 2007-09-30
I have no idea! But that's never stopped me before...

---

