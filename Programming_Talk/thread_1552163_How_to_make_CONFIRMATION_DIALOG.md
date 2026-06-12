---
title: "How to make CONFIRMATION DIALOG"
date: 2010-08-13
forum: Programming Talk
---

### Post by kurci2 on 2010-08-13
Hi!
I have created some lounchers. Usually for autostarting more programs. I'm wondering if someone can help me with making a CONFIRMATION DIALOG. Like one witch appears when i wanna shut my machine down.
I want to put that script in my other scripts, so when someone starts it, the first thing appearing is the confirmation dialog...
I don't want any more accidentally opned programs.

thanks :KS

---

### Post by surfer on 2010-08-13
```
$ man zenity
```
if you want dialogs from the shell.

for more elaborate widgets you could use python and wxpython.

---

### Post by linux18 on 2010-08-13
sudo apt-get dialog
man dialog

I don't need it, I always start the right program every time no matter what it is :)

---

### Post by kurci2 on 2010-08-13
i have focused on zenity.

i have created louncher:
> zenity --question
sleep 1
gnome-screensaver-command -l
sleep 1
sudo s2disk

problem is ... when zanity shows dialog i can press YES or NO. But no matter witch i press the script runs...

---

### Post by MadCow108 on 2010-08-13
please read the manpage:
man zenity
> 
For example, zenity --question will return either 0 or 1, depending on whether the user pressed OK or Cancel.


the return value of the last command is also saved in the $? variable in bash

```

if zenity --question; then
 echo "yes";
else
  echo "no";
fi

zenity --question
echo "return value was $?"

```

---

### Post by lykeion on 2010-08-13
You need to write a bash script. Maybe something like this (using a zenity list):
[PHP]#!/usr/bin/env bash

CHOICE1=$(zenity --list \
	--height=220 \
	--title="List" \
	--text="Options" \
	--radiolist \
	--column="" --column="Option" \
	FALSE "Shutdown" \
	FALSE "Restart" \
	FALSE "Suspend" \
	TRUE "Hibernate")

case $CHOICE1 in
	"Shutdown")
		echo "shutdown..."
		sudo shutdown -h now
	;;
	"Restart")
		echo "restart..."
		sudo reboot
	;;
	"Suspend")
		echo "suspend..."
		gnome-screensaver-command -l
	;;
	"Hibernate")
		echo "hibernate..."
		sudo s2disk
	;;
esac[/PHP]

Some links of interest:

Nice intro to zenity:
[http://www.blastfromthepast.se/blabbermouth/2009/04/gui-creation-with-zenity/](http://www.blastfromthepast.se/blabbermouth/2009/04/gui-creation-with-zenity/)

Discussion on how to suspend/hibernate from command-line:
[http://ubuntuforums.org/showthread.php?t=813387](http://ubuntuforums.org/showthread.php?t=813387)

Hope this helps...

---

### Post by lykeion on 2010-08-13
> **kurci2 said:**
> i have created louncher

It's called a launcher, not to make fun of you, lounch is something completely different:

[http://www.urbandictionary.com/define.php?term=LOUNCH](http://www.urbandictionary.com/define.php?term=LOUNCH)

---

### Post by kurci2 on 2010-08-13
thansk for help!
this is it:
> #!/bin/bash
zenity --question --title="Lock&Hibernate" --text="Ali ste prepri&#269;ani, da želite zakleniti zaslon ter ra&#269;unalnik postaviti v hibernacijo?"
case $? in
    0)
        gnome-screensaver-command -l
	sleep 1
	sudo s2disk
    ;;
esac

works like ubuntu ... perfecly :P

oh...i apologize for that louncher.

---

