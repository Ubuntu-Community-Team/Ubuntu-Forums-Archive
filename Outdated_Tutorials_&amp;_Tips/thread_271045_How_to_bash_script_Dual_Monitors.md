---
title: "How to bash script Dual Monitors"
date: 2006-10-04
forum: Outdated Tutorials &amp; Tips
---

### Post by bodhi.zazen on 2006-10-04
[size=4]**Bodhi's Dual Monitor script.[/size]**

This is a bash script which will give you a GUI to start your dual monitors.

_Features_:[list=number][*]You may select to run fluxbox, gnome, KDE, icewm, openbox, or xfce with choice of monitor configurations-  twinview, dual monitors, or a single monitor.[*]NO ADDITIONAL SCRIPTS.[*]To change between X Sessions Ctrl-alt F7 ; Ctrl-Alt-F8 ; Ctrl-Alt-F9, etc.[/list]

That is correct. I consolidated several start scripts into this bash script.

The upside is there is now only one configuration file for your dual monitor setup.

The downside is you will need to understand this file if you want to tweak my setup (you know you do....) :twisted:

I tried to comment the script so as to make this as painless as possible.


_Dependencies_:

[size=2]**You must follow this how-to and set-up your xorg.conf first**[/size] [-X

[size=2][[color=blue]Bodhi's Dual Monitor Guide[/color]](http://www.ubuntuforums.org/showthread.php?t=240150)[/size] 

EDIT:
[color=darkblue]Thanks to compwiz18:[/color]
> **compwiz18 said:**
> Howdy.  Just thought that it might be worth noting that on a fresh install, dialog is not installed by default.  I had to run **sudo apt-get install dialog** to make the program run, otherwise it just exits.

_Absolute dependency_:
dialog
```
sudo aptitude update
sudo aptitude install dialog
```

_Consider these packages_:
fbsetbg to set background image (openbox)
numlockx - Turns on number lock (on the number pad)
xscreensaver - Screen saver.

_Options_:
rox (see below)

To play a sound at start of window manager:
Install mpg123 or mpg321

Syntax: mpg321 -a hw:y,z /path_to/sound.mp3
	hw:y,z is your soundcard
	hw:0,1 or hw:1,0 or hw:2,0


[size=2]**CONFIGURATION**[/size]

1. _Revisions to xorg.conf_: If you followed my Dual Monitor How-to, I renamed the server identifications for this script (sorry). #-o

If you have not yet followed my guide, I updated it with this post and you should follow that now before proceeding with this.

This is a small edit.

New server names :
	AKA Identifier in "ServerLayout" sections.
	twinview = TWINVIEW
	dual monitors = DUAL (short for dual monitors, was DUALSCREEN)
	single monitor = FAIL (short for failsafe, was DELL)

```
sudo gedit /etc/X11/xorg.conf
```
make the following chages in the 3 server layout sections:

Twinview:> # **********************************************************************
# ServerLayout sections.
# **********************************************************************

Section "ServerLayout"
**	Identifier	"TWINVIEW"**
	Screen		"twinviewscreen"
	InputDevice	"Mouse1" "CorePointer"
	InputDevice	"Keyboard1" "CoreKeyboard"
Endsection

Dual Monitors:> # **********************************************************************
# ServerLayout sections.
# **********************************************************************

Section "ServerLayout"
**     Identifier      "DUAL"**
     Screen      0  "Screen 0" 0 0
     Screen      1  "Screen 1" LeftOf "Screen 0"
     InputDevice     "Mouse1" "CorePointer"
     InputDevice     "Keyboard1" "CoreKeyboard"
EndSection

Single monitor:> # **********************************************************************
# ServerLayout sections.
# **********************************************************************

Section "ServerLayout"
**	Identifier  "FAIL"**
	Screen      0 "Screen 0"
	InputDevice     "Mouse1" "CorePointer"
	InputDevice     "Keyboard1" "CoreKeyboard"
#	Option      "Offtime" "10"
EndSection

2. The start script is currently set to start Fluxbox Dualscreen as Default.

If you want alternate default settings, edit this line in in the script: O:)

> ###########################################################################
#    Default settings- Edit these lines to configure defult settings     ##
###########################################################################

# Start xsreensaver & numlockx
DISPLAY=:1.0 /usr/bin/xscreensaver &
DISPLAY=:1.0 /usr/bin/numlockx on &

# PLAY a sound
# Use a CLI player 
# Example:
# mpg321 -a hw:1,0 /path/sound.mp3

# Start rox
# rox --pinboard=Default &
# DISPLAY=:1.1 rox --pinboard=Default &

**exec /usr/bin/startx /usr/bin/fluxbox -- :1 -layout DUAL 2> /dev/null &**  <-- Edit this line.

###########################################################################
###########################################################################

Defaults: **My recommendations, if any, in BOLD**

Fluxbox:
> Twinview: exec /usr/bin/startx /usr/bin/fluxbox -- :1 -layout TWINVIEW 2> /dev/null &

**[size=2]Dual: exec /usr/bin/startx /usr/bin/fluxbox -- :1 -layout -- :1 -layout DUAL 2> /dev/null &[/size]**

Fail: exec /usr/bin/startx /usr/bin/fluxbox -- :1 -layout -- :1 -layout FAIL 2> /dev/null &

Gnome:
> Twinview: /usr/bin/startx /usr/bin/gnome-session -- :2 -layout TWINVIEW 2> /dev/null &

Dual: /usr/bin/startx /usr/bin/gnome-session -- :2 -layout DUAL & DISPLAY=:2.1 /usr/bin/gnome-session 2> /dev/null &

Fail: /usr/bin/startx /usr/bin/gnome-session -- :2 -layout FAIL 2> /dev/null &

KDE:
> Twinview: /usr/bin/startx -- :3 -layout TWINVIEW 2> /dev/null &

Dual: /usr/bin/startx -- :3 -layout DUAL 2> /dev/null &

Fail: /usr/bin/startx -- :3 -layout FAIL 2> /dev/null &

IceWM:
> Twinview: exec /usr/bin/startx /usr/bin/icewm-session -- :4 -layout TWINVIEW 2> /dev/null &

**[size=2]Dual: exec /usr/bin/startx /usr/bin/icewm-session -- :4 -layout DUAL & DISPLAY=:4.1 /usr/bin/icewm-session 2> /dev/null &[/size]**

Fail: exec /usr/bin/startx /usr/bin/icewm-session -- :4 -layout FAIL 2> /dev/null &

Openbox:
> Twinview: exec /usr/bin/startx /usr/bin/openbox -- :5 -layout TWINVIEW 2> /dev/null &

**[size=2]Dual: exec /usr/bin/startx /usr/bin/openbox -- :5 -layout DUAL & DISPLAY=:5.1 /usr/bin/openbox 2> /dev/null &[/size]**

Fail: exec /usr/bin/startx /usr/bin/openbox -- :5 -layout FAIL 2> /dev/null &

Xfce:
> **[size=2]Twinview: exec /usr/bin/startx /usr/bin/xfce4-session -- :6 -layout TWINVIEW 2> /dev/null &[/size]**

Dual: exec /usr/bin/startx /usr/bin/xfce4-session -- :6 -layout DUAL 2> /dev/null &

Fail: exec /usr/bin/startx /usr/bin/xfce4-session -- :6 -layout FAIL 2> /dev/null &

[size=2][b]3. Save this script as /usr/bin/dual
```
sudo gedit /usr/bin/dual
```
Copy and paste this script:[/b][/size]> #!/bin/sh

# Variables
# widowmanager=Desktop/Window manager
# monitorcfg = Display configuration AKA Twinview/Dual/Single
# tempfile1=tempfile1
# tempfie2=tempfile2

#############################################################################
##             Default Screens                                             ##
#############################################################################

# GDM starts at boot on screen 0

# Fluxbox = 1
# Gnome = 2
# IceWM = 3
# KDE = 4
# Openbox = 5
# xfce = 6

#############################################################################
##             Select Desktop/Window manager                                  ##
#############################################################################

dialog  --backtitle "Welcome to bodhi's dual monitor script" --title "Desktop Environment" --menu "Please select a desktop environment" 13 175 7 \
        "default" "Default settings" \
        "fluxbox" "Fluxbuntu <http://community.fluxbuntu.org>" \
        "gnome" "Ubuntu" \
        "icewm" "<http://en.wikipedia.org/wiki/IceWM>" \
        "kde" "Kubuntu" \
        "openbox" "<http://www.icculus.org/openbox/2/>" \
        "xfce" "Xubuntu" 2>~/tempfile1

return_value=$?

windowmanager=`cat ~/tempfile1`

case $return_value in
  0)
    if [ "$windowmanager" = default ]
    then
	rm ~/tempfile1 & rm ~/tempfile2 & rm windowmanager
	clear
	echo -e '\E[32m'"bodhi.zazen"
	tput sgr0
###########################################################################
#    Default settings- Edit these lines to configure defult settings     ##
###########################################################################

# Start xsreensaver & numlockx
DISPLAY=:1.0 /usr/bin/xscreensaver &
DISPLAY=:1.0 /usr/bin/numlockx on &

# PLAY a sound
# Use a CLI player 
# Example:
# mpg321 -a hw:1,0 /path/sound.mp3

# Start rox
# rox --pinboard=Default &
# DISPLAY=:1.1 rox --pinboard=Default &

exec /usr/bin/startx /usr/bin/fluxbox -- :1 -layout DUAL 2> /dev/null &

###########################################################################
###########################################################################
	exit
     fi ;;
  1)
	clear
	echo -e '\E[31m' "Cancel"
	tput sgr0
        sleep 2
	clear
	exit ;;
  255)
	clear
	echo -e '\E[31m' "Esc"
	tput sgr0
        sleep 2
	clear
	exit ;;
esac

#############################################################################
##             Set Display Configuration                                   ##
#############################################################################

dialog --backtitle "Welcome to bodhi's dual monitor script" --menu "Please choose the your desired display" 10 75 5 \
        "Twinview" "One big monitor" \
        "Dual" "Two separate monitors" \
        "Failsafe" "Single monitor" 2>~/tempfile2

return_value=$?

monitorcfg=`cat ~/tempfile2`

case $return_value in
  0)
	rm ~/tempfile1 & rm ~/tempfile2
	clear
	echo -e '\E[32m'"bodhi.zazen"
	tput sgr0

    case $windowmanager in

	fluxbox)
		# Start xsreensaver & numlockx
		DISPLAY=:1.0 /usr/bin/xscreensaver &
		DISPLAY=:1.0 /usr/bin/numlockx on &

		# PLAY a sound
		# Use a CLI player
		# Example:
		# sleep -3 & mpg321 -a hw:1,0 /path/sound.mp3 &

		# Start rox
		# rox --pinboard=Default &
		# DISPLAY=:1.1 rox --pinboard=Default &

		case $monitorcfg in
			Twinview)
				exec /usr/bin/startx /usr/bin/fluxbox -- :1 -layout TWINVIEW 2> /dev/null &
				exit ;;
			Dual)
				exec /usr/bin/startx /usr/bin/fluxbox -- :1 -layout -- :1 -layout DUAL 2> /dev/null &
				exit ;;
			Failsafe)
				exec /usr/bin/startx /usr/bin/fluxbox -- :1 -layout -- :1 -layout FAIL 2> /dev/null &
				exit ;;
		esac ;;

	gnome)
		# Start xsreensaver & numlockx
		DISPLAY=:4.0 /usr/bin/xscreensaver &
		DISPLAY=:4.0 /usr/bin/numlockx on &

		# PLAY a sound
		# Use a CLI player
		# Example:
		# sleep -3 & mpg321 -a hw:1,0 /path/sound.mp3 &

		case $monitorcfg in
			Twinview)
				/usr/bin/startx /usr/bin/gnome-session -- :2 -layout TWINVIEW 2> /dev/null &
				exit ;;
			Dual)
				/usr/bin/startx /usr/bin/gnome-session -- :2 -layout DUAL & DISPLAY=:2.1 /usr/bin/gnome-session 2> /dev/null &
				exit ;;
			Failsafe)
				/usr/bin/startx /usr/bin/gnome-session -- :2 -layout FAIL 2> /dev/null &
				exit ;;
		esac ;;

	kde)
		# Start xsreensaver & numlockx
		DISPLAY=:4.0 /usr/bin/xscreensaver &
		DISPLAY=:4.0 /usr/bin/numlockx on &

		# PLAY a sound
		# Use a CLI player
		# Example:
		# sleep -3 & mpg321 -a hw:1,0 /path/sound.mp3 &

		case $monitorcfg in

			Twinview)
				/usr/bin/startx -- :3 -layout TWINVIEW 2> /dev/null &
				exit ;;
			Dual)
				/usr/bin/startx -- :3 -layout DUAL 2> /dev/null &
				exit ;;
			Failsafe)
				/usr/bin/startx -- :3 -layout FAIL 2> /dev/null &
				exit ;;
		esac ;;

	icewm)
		# Start xsreensaver & numlockx
		DISPLAY=:4.0 /usr/bin/xscreensaver &
		DISPLAY=:4.0 /usr/bin/numlockx on &

		# PLAY a sound
		# Use a CLI player
		# Example:
		# sleep -3 & mpg321 -a hw:1,0 /path/sound.mp3 &		

		# Start rox
		# rox --pinboard=Default &
		# DISPLAY=:4.1 rox --pinboard=Default &

		case $monitorcfg in
			Twinview)
				exec /usr/bin/startx /usr/bin/icewm-session -- :4 -layout TWINVIEW 2> /dev/null &
				exit ;;
			Dual)
				exec /usr/bin/startx /usr/bin/icewm-session -- :4 -layout DUAL & DISPLAY=:4.1 /usr/bin/icewm-session 2> /dev/null &
				exit ;;
			Failsafe)
				exec /usr/bin/startx /usr/bin/icewm-session -- :4 -layout FAIL 2> /dev/null &
				exit ;;
		esac ;;

	openbox)
		# Start xsreensaver & numlockx
		DISPLAY=:5.0 /usr/bin/xscreensaver &
		DISPLAY=:5.0 /usr/bin/numlockx on &

		# To set background image, uncomment the following lines and set the path to an image
		# DISPLAY=:5.0 fbsetbg -f /home/picture.jpg &
		# DISPLAY=:5.1 fbsetbg -f  /home/picture.jpg &

		# PLAY a sound
		# Use a CLI player
		# Example:
		# sleep -3 & mpg321 -a hw:1,0 /path/sound.mp3 &

		# Start rox Rox does not work so well with Openbox....
		# rox --pinboard=Default &
		# DISPLAY=:5.1 rox --pinboard=Default &

		case $monitorcfg in
			Twinview)
				exec /usr/bin/startx /usr/bin/openbox -- :5 -layout TWINVIEW 2> /dev/null &
				exit ;;
			Dual)
				exec /usr/bin/startx /usr/bin/openbox -- :5 -layout DUAL & DISPLAY=:5.1 /usr/bin/openbox 2> /dev/null &
				exit ;;
			Failsafe)
				exec /usr/bin/startx /usr/bin/openbox -- :5 -layout FAIL 2> /dev/null &
				exit ;;
		esac ;;

	xfce)
		# Start xsreensaver & numlockx
		DISPLAY=:6.0 /usr/bin/xscreensaver &
		DISPLAY=:6.0 /usr/bin/numlockx on &

		# PLAY a sound
		# Use a CLI player
		# Example:
		# sleep -3 & mpg321 -a hw:1,0 /path/sound.mp3 &

		# Start rox
		# rox --pinboard=Default &
		# DISPLAY=:6.1 rox --pinboard=Default &

		case $monitorcfg in
			Twinview)
				exec /usr/bin/startx /usr/bin/xfce4-session -- :6 -layout TWINVIEW 2> /dev/null &
				exit ;;
			Dual)
				exec /usr/bin/startx /usr/bin/xfce4-session -- :6 -layout DUAL 2> /dev/null &
				exit ;;
			Failsafe)
				exec /usr/bin/startx /usr/bin/xfce4-session -- :6 -layout FAIL 2> /dev/null &
				exit ;;
		esac ;;

	esac ;;


  1)
	clear
	echo -e '\E[31m' "Cancel"
	tput sgr0
        sleep 2
	clear
	exit ;;
  255)
	clear
	echo -e '\E[31m' "Esc"
	tput sgr0
        sleep 2
	clear
	exit ;;
esac
rm windowmanager & rm monitorcfg
clear
echo -e '\E[32m'"bodhi.zazen"
tput sgr0
[b]Save and exit gedit.

Now make it executable:[/b]```
sudo chmod a+x /usr/bin/dual
```

3. Enable script for use within X.

Note: by default, in Ubuntu you can use this script in tty1
```
Ctrl-alt-F1
login
dual
```

To enable this script for use within an X session (gnome):
```
sudo gedit /etc/X11/Xwrapper.config
```
Change:> allowed_users=console
To:```
allowed_users=anybody
```

[Documentation](http://www.fifi.org/cgi-bin/man2html/usr/share/man/man5/Xwrapper.config.5.gz)

After this edit you can use this script from tty1 or in a terminal in gnome (or any window manager).

[color=red]Now, to run this script, open a terminal and type dual.[/color]

4. Shortcut:
Start this script with
```
bash dual
```

5. Add a menu item/launcher/desktop shortcut.
Create a menu item, launcher, or desktop icon.
Name =Dual
Command= bash dual


6. KDE:
This script starts KDE with just startx.

Thus edit your .xinitrc

> #!/bin/sh

#
# ~/.xinitrc
#
# Executed by startx (run your window manager from here)
#

exec startkde 


7. Log out works with dual monitors, at times, from only one of the two screens. If it hangs with both screens (rare) use Ctrl-Alt-Backspace.


8. Rox:Rox works well with fluxbox, icewm, xfce. It will allow desktop icons very easily.
See here for configuration:

[[color=blue]Fluxbuntu Rox[/color]](http://community.fluxbuntu.org/index.php?PHPSESSID=85ab217b4a7cd75f8f465236137258ff&topic=78.0)

[[color=blue]Debian Rox[/color]](http://forums.debian.net/viewtopic.php?t=7345&sid=1951ea962cdd2a4f852c8ff87742519b)

Note: Rox does not work so well with openbox.

---

