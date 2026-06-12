---
title: "Some quick help with a bash script"
date: 2008-03-26
forum: Programming Talk
---

### Post by picpak on 2008-03-26
Alright, so I use Openbox as my little gaming WM. Not for anything big and fancy, just something to run my old Sega Genesis games in. (plus, I get 3 times as much FPS with it than in Gnome...a no-brainer, right?)

I got tired of always opening a terminal and typing "dgen ROMs/Genesis/etc.etc..." so I wrote myself a script that presents a file open box and runs the selected file with dgen. It runs when I log into Openbox.

[php]#!/bin/sh

romdir=~/ROMs/Genesis/
location=`zenity --file-selection --filename=$romdir --title="Select ROM to run"`

if [ $location ]; then
	dgen "$location"
else
	dgen "$location"
fi[/php]

Now obviously this is some awful quality code, it runs the same thing for then as it does for else. But it does the trick for me.

BUT, what I also want is, when dgen closes, for the script to reload again. Now I imagine that that would mean putting in an if statement that runs `ps aux` and searches to see if dgen is running (or even just see if there was a killall) within the script, but I want to know what would be the best solution. Any help would be appreciated. Thanks in advance!

---

### Post by picpak on 2008-03-26
Well, that was easy.

[php]#!/bin/sh

romdir=~/ROMs/Genesis/
location=`zenity --file-selection --filename=$romdir --title="Select ROM to run"`

if [ -e "$location" ]; then
	dgen "$location"
else
	exit 0
fi

zenity --question --title="Play again?" --text="Would you like to play again?"
	case "$?" in
		1  )  exit 1 ;;
		0  )  ~/bin/dgen.sh ;;
	esac

[/php]

I referred to the scripts at [https://help.ubuntu.com/community/Nautilus_Scripts](https://help.ubuntu.com/community/Nautilus_Scripts) to help me out.

---

