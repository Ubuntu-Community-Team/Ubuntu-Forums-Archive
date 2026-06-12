---
title: "How-to run Multiple (Virtual) X sessions"
date: 2006-10-05
forum: Outdated Tutorials &amp; Tips
---

### Post by bodhi.zazen on 2006-10-05
[size=4]**Bodhi's VirtualX script.[/size]**


This is a bash script which will give you a GUI to start virtual X sessions without going through KDM, GDM, XDM, etc.

[color=blue]This is an adaptation from my work with dual monitors....[/color]

_What is a virtual X session_? Just as you can have multiple terminals (tty1, tty2....,tty6)
You can have multiple instances of X (Ctrl-Alt-F7, Ctrl-Alt-F8, Ctrl-Alt-F9).

_Yes, but doesn't that slow down your computer_? **[color=red]NOT THAT MUCH[/color]**

_Yes, but why you ask_?

Are you the type that runs gnome, but are interested in trying an alternate desktop?

This script allows yo to stay logged in gnome, all applications running, and start a second X session,  say Fluxbox, Openbox, IceWM, or XFCE.

Otherwise you have to log-out, choose a new session in GDM, log in.  This stops all your gnome programs.

With this script you can explore AND keep gnome running as "home base" 

_Features_:[list=number][*]You may select to run fluxbox, gnome, KDE, icewm, openbox, or xfce.[*]NO ADDITIONAL SCRIPTS.[*]To change between X Sessions Ctrl-alt F7 ; Ctrl-Alt-F8 ; Ctrl-Alt-F9, etc.[/list]

That is correct. I consolidated a number of start scripts into this bash script.

The upside is there is now only one configuration file for your virtual X setup and configuration.

The downside is you will need to understand this file if you want to tweak my setup (you know you do....) :twisted:

I tried to comment the script so as to make this as painless as possible.


_Dependencies_:

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

_I advise these packages_:
fbsetbg to set background image (openbox, Fluxbox, IceWM [Although IceWM has themes])
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

[size=2][b]1. Save this script as /usr/bin/virtualX
```
sudo gedit /usr/bin/virtualX
```
Copy and paste this script:[/b][/size]> #!/bin/sh

# Variables
# widowmanager=Desktop/Window manager
# tempfile1=tempfile1

#############################################################################
##             Default Screen                                             ##
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

dialog  --backtitle "Welcome to bodhi's virtual X script" --title "Desktop Environment" --menu "Please select a desktop environment" 13 175 7 \
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
	rm ~/tempfile1 & rm windowmanager
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
		#DISPLAY=:1.0 rox --pinboard=Default &

		exec /usr/bin/startx /usr/bin/fluxbox -- :1 2> /dev/null &
		exit ;;

	gnome)
		# Start xsreensaver & numlockx
		DISPLAY=:2.0 /usr/bin/xscreensaver &
		DISPLAY=:2.0 /usr/bin/numlockx on &

		# PLAY a sound
		# Use a CLI player
		# Example:
		# sleep -3 & mpg321 -a hw:1,0 /path/sound.mp3 &

		# Start Gnome
		/usr/bin/startx /usr/bin/gnome-session -- :2 2> /dev/null &
		exit ;;
		
	kde)
		# Start xsreensaver & numlockx
		DISPLAY=:3.0 /usr/bin/xscreensaver &
		DISPLAY=:3.0 /usr/bin/numlockx on &

		# PLAY a sound
		# Use a CLI player
		# Example:
		# sleep -3 & mpg321 -a hw:1,0 /path/sound.mp3 &

		# Start KDE
		/usr/bin/startx -- :3 2> /dev/null &
		exit ;;
		
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

		# Start IceWM
		exec /usr/bin/startx /usr/bin/icewm-session -- :4 2> /dev/null &
		exit ;;

	openbox)
		# Start xsreensaver & numlockx
		DISPLAY=:5.0 /usr/bin/xscreensaver &
		DISPLAY=:5.0 /usr/bin/numlockx on &

		# To set background image, uncomment the following lines and set the path to an image
		# DISPLAY=:5.0 fbsetbg -f /home/picture.jpg &
		
		# PLAY a sound
		# Use a CLI player
		# Example:
		# sleep -3 & mpg321 -a hw:1,0 /path/sound.mp3 &

		# Start rox Rox does not work so well with Openbox....
		# rox --pinboard=Default &
		
		# Start Openbox
		exec /usr/bin/startx /usr/bin/openbox -- :5 2> /dev/null &
		exit ;;

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

		# Start XFCE
		exec /usr/bin/startx /usr/bin/xfce4-session -- :6 2> /dev/null &
		exit ;;
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

rm windowmanager
clear
echo -e '\E[32m'"bodhi.zazen"
tput sgr0
[b]Save and exit gedit.

Now make it executable:[/b]```
sudo chmod a+x /usr/bin/virtualX
```

2. Enable script for use within X.

Note: by default, in Ubuntu you can use this script in tty1
```
Ctrl-alt-F1
login
virtualX
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

[color=red]Now, to run this script, open a terminal and type virtualX.[/color]

3. Shortcut:
Start this script with
```
bash virtualX
```
Watch the capital X at the end.....

4. Add a menu item/launcher/desktop shortcut.
Create a menu item, launcher, or desktop icon.
Name =virtualX
Command= bash virtualX


5. KDE:
This script starts KDE with just startx.

Thus edit your .xinitrc

> #!/bin/sh

#
# ~/.xinitrc
#
# Executed by startx (run your window manager from here)
#

exec startkde 


6. Rox: Rox works well with fluxbox, icewm, xfce. It will allow desktop icons very easily.
See here for configuration:

[[color=blue]Fluxbuntu Rox[/color]](http://community.fluxbuntu.org/index.php?PHPSESSID=85ab217b4a7cd75f8f465236137258ff&topic=78.0)

[[color=blue]Debian Rox[/color]](http://forums.debian.net/viewtopic.php?t=7345&sid=1951ea962cdd2a4f852c8ff87742519b)

Note: Rox does not work so well with openbox.

[size=2][color=blue]Most of all, have fun ![/color][/size]

---

### Post by DJiNN on 2006-10-05
Hi bhodi, thanks for the excellent "HowTo".  It's not running on my system though for some reason. Just exits (Cleanly i might add) both in a terminal window & a tty1 etc......

Also, what i was going to say (but forgot to mention the other day) was that i "Can't" switch back & forth when doing the one line command that we talked about..... when i switch back to my normal session (CTL-ALT-F7) then go back to tty1, it's no longer running as an xsession.

I'll keep playing with this script & see if i can sort out what's wrong. :)

---

### Post by bodhi.zazen on 2006-10-05
> **DJiNN said:**
> Hi bhodi, thanks for the excellent "HowTo".  It's not running on my system though for some reason. Just exits (Cleanly i might add) both in a terminal window & a tty1 etc......

Also, what i was going to say (but forgot to mention the other day) was that i "Can't" switch back & forth when doing the one line command that we talked about..... when i switch back to my normal session (CTL-ALT-F7) then go back to tty1, it's no longer running as an xsession.

I'll keep playing with this script & see if i can sort out what's wrong. :)

Thank you thank you for your response, I will look at the script again tonight.

I ran the script last night before posting but I was not able to replicate your issues (on my Ubuntu box).

When you find the script exits cleanly, is this for all window managers or do some work for you?

Just to ask the obvious, you must have the window manager installed for this script it to launch it (ie this script does not run xfce if xfce is not installed).

Since you have *box do openbox and/or fluxbox work?

As to changing from tty1 to F7 or F8 I could do all this with no problems. I can even close the terminal in which I run the script and the window manager I started with the script continues to run.

At any rate to trouble shoot the script remove the "2> /dev/null" from the end of the line(s) with the relevant window manager(s) and you should then see error messages (as well as other text) in the terminal.

---

### Post by DJiNN on 2006-10-05
> **bodhi.zazen said:**
> Thank you thank you for your response, I will look at the script again tonight.

I ran the script last night before posting but I was not able to replicate your issues (on my Ubuntu box).

Hi bodhi..... just ran the script on my FluxBox (You know, the server install?) and it ran fine, and gave me a choice etc (Which is really cool by the way, well done.... ) So i chose "OpenBox" because i know that i have that installed on this machine. It ran fine, but when i swapped back to CTRL-ALT-F7 then went back to OB again, it had exited, giving the errors as lines 109 & 110 - that i neither have xscreensaver or xnumlock installed. Are these pre-requisites (Do they "Have" to be installed) or is it a choice thing? No worries, because i can install them, it's just that i never really use either, especially the numlock thing. Sad as it may be, i NEVER ever use the keypad on the right of the keyboard.....  for anything! :)

> When you find the script exits cleanly, is this for all window managers or do some work for you?I don't even get that far on the Ubuntu machine..... no choices at all, i just run it & it exits without even bringing up a "Choice" as it were. In fact, the first time that i saw the choices was just now when i ran it on the Flux machine. :)

> Just to ask the obvious, you must have the window manager installed for this script it to launch it (ie this script does not run xfce if xfce is not installed).I can imagine that, that's why i ran OpenBox to try it out on the Flux machine, because it's installed on that machine, but XFCE isn't. 

On the Ubuntu machine, it's actually "Xubuntu" so i don't know if that will make a lot of difference as to how the script works etc, but i would have imagined that if it runs OK on the Server install with Flux, then it would run OK on XFCE.....? (Or is that just "Wishful thinking"? ) :)

> Since you have *box do openbox and/or fluxbox work?OpenBox works fine on the Fluxbox machine (Apart from the fact that it still exits when i come out of it & go back to CTRL-ALT-F7.  On the Ubuntu (Xubuntu) machine, nothing works at all...... I don't even get a screen with choices on it. :)

> As to changing from tty1 to F7 or F8 I could do all this with no problems. I can even close the terminal in which I run the script and the window manager I started with the script continues to run.Hmmm, i've tried it on both machines here & it doesn't do that. I can get it to run on this (Flux) machine, and choose a "VirtualX" environment, but as soon as i exit & go back to it, it's stopped with the screensaver & numlock errors that i mentioned earlier. 

Ah, hold on..... BREAKING NEWS!!! :) Heehee...... i've just checked, and for some reason (On the Flux machine at any rate) it's firing the virtual X's up & it is keeping them there, but i have to get to them by doing CTRL-ALT-F8 or F9 or F10 etc...... it's not putting them on CTRL-ALT-F1, F2 etc. So yes, they're still running but not where i thought they were..... Any ideas?

But nothing works at all on the Xubuntu machine..... YET!! :)

---

### Post by DJiNN on 2006-10-05
Me again..... just been playing around on the Flux machine & this really works well...!! I've currently got Fluxbox (Main X server) running with both OpenBox & IceWM running at the same time.... all in 512mb or RAM on an old PIII 700Mhz machine..... amazing! & all desktops are really responsive & work really well. 

But i still can't get a peep from the main (Xubuntu) machine..... it just won't run the virtualX script either from a terminal or a tty sccreen..... weird.

Anyway, just wanted to let you know..... & say "Thanks" for a great script.  I'll keep on playing & keep you posted with how it goes.

---

### Post by bodhi.zazen on 2006-10-05
> **DJiNN said:**
> Hi bodhi..... just ran the script on my FluxBox (You know, the server install?) and it ran fine, and gave me a choice etc (Which is really cool by the way, well done.... ) So i chose "OpenBox" because i know that i have that installed on this machine. It ran fine, but when i swapped back to CTRL-ALT-F7 then went back to OB again, it had exited, giving the errors as lines 109 & 110 - that i neither have xscreensaver or xnumlock installed. Are these pre-requisites (Do they "Have" to be installed) or is it a choice thing? No worries, because i can install them, it's just that i never really use either, especially the numlock thing. Sad as it may be, i NEVER ever use the keypad on the right of the keyboard.....  for anything! :)

No you do not have to run either xscreensaver or numlock X. You in fact do not need to do anything, all that will happen is that your error messages will persist.

To fix, edit the script and comment out (or delete) the xscreensaver and numlockx lines like this:
```
fluxbox)
# Start xsreensaver & numlockx
# DISPLAY=:1.0 /usr/bin/xscreensaver &
# DISPLAY=:1.0 /usr/bin/numlockx on &

# PLAY a sound
# Use a CLI player
# Example:
# sleep -3 & mpg321 -a hw:1,0 /path/sound.mp3 &

# Start rox
#DISPLAY=:1.0 rox --pinboard=Default &

exec /usr/bin/startx /usr/bin/fluxbox -- :1 2> /dev/null &
exit ;; 
```

If you like, you could enable rox while you are there........ I do not recall if you use rox.

> **DJiNN said:**
> I don't even get that far on the Ubuntu machine..... no choices at all, i just run it & it exits without even bringing up a "Choice" as it were. In fact, the first time that i saw the choices was just now when i ran it on the Flux machine.

Not sure what is at issue with xubuntu. I can tell you the script was written for Arch and then adapted to Ubuntu. It does not run (well) on Zenwalk either. Of course, it could be adapted....

> **DJiNN said:**
> Ah, hold on..... BREAKING NEWS!!!  Heehee...... i've just checked, and for some reason (On the Flux machine at any rate) it's firing the virtual X's up & it is keeping them there, but i have to get to them by doing CTRL-ALT-F8 or F9 or F10 etc...... it's not putting them on CTRL-ALT-F1, F2 etc. So yes, they're still running but not where i thought they were..... Any ideas? 

LOL DJiNN :lol: X runs virtual on higher sessions, ie Ctrl-alt-F7, Ctrl-Alt-F8, ... You could change this behavior by editing some system files. If that is what you would like I would need to do a little research on Ubuntu.

> **DJiNN said:**
> Me again..... just been playing around on the Flux machine & this really works well...!! I've currently got Fluxbox (Main X server) running with both OpenBox & IceWM running at the same time.... all in 512mb or RAM on an old PIII 700Mhz machine..... amazing! & all desktops are really responsive & work really well.

:twisted: It is amazing how little this technique saps resources. I have been trying to teach this, but people have been afraid of the configuration files and CLI interface, thus the script.

> **DJiNN said:**
> But i still can't get a peep from the main (Xubuntu) machine..... it just won't run the virtualX script either from a terminal or a tty sccreen..... weird.

Did you enable the script? ```
sudo chmod a+x /usr/bin/virtualX
```

Also, did you try adding my shortcut to your fluxbox menu? It also works like a charm :biggrin: 

8-)

---

### Post by DJiNN on 2006-10-05
> **bodhi.zazen said:**
> No you do not have to run either xscreensaver or numlock X. You in fact do not need to do anything, all that will happen is that your error messages will persist.

To fix, edit the script and comment out (or delete) the xscreensaver and numlockx lines like this:
```
fluxbox)
# Start xsreensaver & numlockx
# DISPLAY=:1.0 /usr/bin/xscreensaver &
# DISPLAY=:1.0 /usr/bin/numlockx on &

# PLAY a sound
# Use a CLI player
# Example:
# sleep -3 & mpg321 -a hw:1,0 /path/sound.mp3 &

# Start rox
#DISPLAY=:1.0 rox --pinboard=Default &

exec /usr/bin/startx /usr/bin/fluxbox -- :1 2> /dev/null &
exit ;; 
```If you like, you could enable rox while you are there........ I do not recall if you use rox.

I do use Rox (& also Thunar quite a bit at the moment) & i have already commented out the screensaver etc on every line..... The script actually "Runs" but just exits straight away & doesn't do anything.  

One thing that did happen, was when i commented out the lines with sccreensaver etc, it started throwing up a "bad token" error, somewhere around line 90.... icewm)      I looked but i still can't find anything that's obvious. 

> Not sure what is at issue with xubuntu. I can tell you the script was written for Arch and then adapted to Ubuntu. It does not run on Zenwalk either.

hmmm, it's strange that it should work on Ubuntu but not on Xubuntu isn't it? There could be something missing perhaps.... I'm not running Zen at the moment as you know, but once i learn a bit more about this script & what each line means & does (I know some but not all,.... yet) then i'll perhaps re-do a version for Zen...... just to try it out more than anything else. :)  

> LOL DJiNN :lol: X runs virtual on higher sessions, ie Ctrl-alt-F7, Ctrl-Alt-F8, ... You could change this behavior by editing some system files. If that is what you would like I would need to do a little research on Ubuntu.

LOL!! It's very strange how it does it..... (Well, to me anyway) ... so i effectively have all of my tty screens (1-6) and then my virtualX's are running on 8,9,10 etc..... with, of course, CTRL-ALT-F7 bringing my main desktop & environment back.  

I don't actually mind it at all..... just strange that it happens that way. :)

> :twisted: It is amazing how little this technique saps resources. I have bee trying to teach this, but people have been afraid of the configuration files and CLI interface, thus the script.

This is one of the things that amazes me, and also one of it's strengths i think. This script, with time & development, could turn out to be a really beneficial little tool. (That's a subtle hint to keep on working on it by the way....) ;) :D

> Did you enable the script? ```
sudo chmod a+x /usr/bin/virtualX
```Also, did you try adding my shortcut to your fluxbox menu? It also works like a charm :biggrin: 

I did enable the script and it works fine on the Flux system, but still nothing on this one (Xubuntu). It runs..... but just exits straight away.  

I shall keep going though....... i really love the ability to be able to run several X's at once..... & would even consider doing another server install just to get the ability on this machine as well.

---

### Post by DJiNN on 2006-10-05
Another update..... :)

It seems that using the CLI command ```
/usr/bin/startx /usr/bin/openbox -- :2 
``` as you told me earlier, does work on the xUbuntu system, but as on the other system, it puts the virtualX on CTRL-ALT-F8/F9 etc. It doesn't touch tty 1 or 2 etc. 

So now i can swap between these virtual X's, but they're just in a different place to where i was previously looking.

I personally think this  is a great step forward for me, for while it may not be working quite as it should, at least it "IS" working & i can do what i set out to do, which is run several Virtual X environments at the same time. 

Now i've just got to find out...A:) why it's doing this (ie: using different  screens to the ones that it's supposed to be using) and B:) how i can get the script working on the xUbuntu machine.

It's all good fun though...... :)

---

### Post by compwiz18 on 2006-10-05
Howdy.  Just thought that it might be worth noting that on a fresh install, dialog is not installed by default.  I had to run **sudo apt-get install dialog** to make the program run, otherwise it just exits.

---

### Post by DJiNN on 2006-10-05
> **compwiz18 said:**
> Howdy.  Just thought that it might be worth noting that on a fresh install, dialog is not installed by default.  I had to run **sudo apt-get install dialog** to make the program run, otherwise it just exits.

THAT'S IT!!! :)  Thanks ever so much for that....... It now works perfectly on both machines. I don't think i would have found that one, for sure. :)

I have 3 different VX's running on this machine, and i'm just about to go to tty1 & run it from there.... just to see what happens. :)

Thanks once again..... You've saved me many hours of trial & error, with the emphasis on "error". :)

---

### Post by Witty Name on 2006-10-11
"**Widow**manager", you say?

---

### Post by bodhi.zazen on 2006-10-11
This how-to has been added to the Ubuntu wiki:

[[color=navy]Virtual X[/color]](http://doc.gwos.org/index.php/VirtualX)

---

### Post by bodhi.zazen on 2006-10-11
> **Witty Name said:**
> "**Widow**manager", you say?

Before I do the work, is that a request to add WM2 to the script?

[wm2](http://www.all-day-breakfast.com/wm2/)

If that is the case, I would be happy to modify the script.

---

### Post by Angry penguin on 2007-02-27
I got the virtualX script to work. If I run it from the terminal it starts the xsession then immediately exits, if I start it from the tty1 it starts the xsession and gives me a desktop where my cursor is an "X". Any Idea what happened?

I was hoping that I could use this new xsession to run some games. How do I get the script to launch my game when I choose, for example xfce?

---

### Post by bodhi.zazen on 2007-02-27
> **Angry penguin said:**
> I got the virtualX script to work. If I run it from the terminal it starts the xsession then immediately exits, if I start it from the tty1 it starts the xsession and gives me a desktop where my cursor is an "X". Any Idea what happened?

I was hoping that I could use this new xsession to run some games. How do I get the script to launch my game when I choose, for example xfce?

I am not sure as I do not game much ...

perhaps I can help ...

Can you tell me please, 

1. What command are you starting X with. The gray screen with a black X is, well X.

2. To start your game, what command do you use in a terminal ?

As you can see, to stat a window manager we use :

/usr/bin/startx /usr/bin/openbox -- :2

To start your game we may need to try :

/usr/bin/startx <command for game> --:1 or some such, I am not sure :?

---

### Post by Angry penguin on 2007-02-28
1. I just entered the virtual terminal and typed "vitrualX" and it started the new xserver.

2. I use: a script which calls out some options for doom and points to the doom wad. I am playing doomsday.

I tried using the /usr/bin/startx line with the path to game as you suggested and I got this error:

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

---

### Post by bodhi.zazen on 2007-02-28
FYI : Each X session must be on it's own virtual session ...

So the first session is logically called (numbered) ... 0 and is on Ctrl-Alt-F7

The second is numbered ... 1 and is on Ctrl-Alt-F8

And on up to the 6th session, numbered 5 of course, on Ctrl-Alt-F12

===========

 > Server is already active for display 0Means you tried to start a new session on the first terminal (Ctrl-Alt-F7).

So you need to increase the number at the end of the command ...

/usr/bin/startx <command to start game> **-- :2**

/usr/bin/startx <command to start game> **-- :3**

Now, if that fails, well then I would just run 2 gnome sessions, one on Ctrl-Alt-F7

And the other on Ctrl-Alt-F8

Then launch the game from the second session on Ctrl-alt-F8

You can Ctrl-Alt-F7 to return to your first gnome session.

HTH ~~ Are you "less angry penguin" yet, you know that is the first step to recovery from years of $M brain washing ...

Perhaps you will become Pondering Penguin, then happy penguin, and perhaps ever the hacking penguin :twisted:

:lolflag:

---

### Post by Sammi on 2007-06-07
I can only seem to get this to work if I use sudo to launch virtualX. That can't be right...

Does it have something to do with my user not having sufficient rights to start X sessions? Where can I change that?

EDIT: Ok I was trying to log in to Gnome and I think it just wasn't happy with the same user logging in twice, as creating a new user and logging into a virtual terminal (say tty1) with it and then launching Gnome with virtualX worked fine.

Downloading Xubuntu in Synaptic right now to see how it does...

---

### Post by mon^rch on 2008-06-22
fbsetbg is no longer in the repos... what do I do? :(

---

### Post by Sammi on 2008-06-22
-

---

### Post by nick_h on 2008-06-22
> fbsetbg is no longer in the repos... what do I do?
fbsetbg is in the fluxbox package.

---

### Post by mon^rch on 2008-06-26
doh
ty

---

### Post by mon^rch on 2008-06-26
I get the following error when trying to start now:
-e \E[32mbodhi.zazen
what's wrong?

---

### Post by mon^rch on 2008-06-26
nvmnd... problem fixed. thank you for the excellent script

GS

---

### Post by bodhi.zazen on 2008-06-26
> **mon^rch said:**
> nvmnd... problem fixed. thank you for the excellent script

GS

You are most welcome, glad you enjoyed it. I am sure you can adapt it for a variety of needs ...

ssh -X comes to mind.

---

### Post by mon^rch on 2008-06-26
no doubt, eh?!?!?!?! you rock brother!

Greg Starr

---

### Post by mon^rch on 2008-07-18
hey, is it possible to edit the script to add like (if I wanted) 15 different X sessions? ie: KDE4, blackbox etc...

and if so, how?

---

### Post by bodhi.zazen on 2008-07-18
> **mon^rch said:**
> hey, is it possible to edit the script to add like (if I wanted) 15 different X sessions? ie: KDE4, blackbox etc...

and if so, how?

15 :lolflag:

well, first you are limited to 6 by the default settings.

Other then that go for it :)

X sessions are numbered starting with 0

startx -- :0

then comes 1 , 2 , 3 ... up to 14

so

startx /path/window_mananger_1 -- :0
startx /path/window_manager_2 -- :1
...
startx /path/window_manager_15 -- :14

Now you can number your x sessions any way you wish (yo do not need to start with 0 and go to 14), up to 99

---

### Post by mon^rch on 2008-07-19
thanks, much appreciated

---

### Post by unutbu on 2008-08-22
bodhi.zazen, thanks for the VirtualX script!
I'm running into a problem, however.

When I run it from the gnome session (and select gnome), the screen goes black for a moment, and then I'm popped back to the gnome session.

When I run it from tty1 (and select gnome), I get the grey mosaic pattern and the X cursor. No usual gnome session. None of the mouse buttons do anything. I pressed Ctrl-Alt-Backspace, and was sent back to tty1.

Okay, confession #1: I use fvwm as my window manager instead of metacity. 

Confession #2: I don't have xscreensaver or numlockx installed, so I commented out those lines.

Here is the slight change I made to the script:
```

% diff ~/bin/virtualX-orig /usr/local/bin/virtualX
64,65c64,65
< 		DISPLAY=:2.0 /usr/bin/xscreensaver &
< 		DISPLAY=:2.0 /usr/bin/numlockx on &
---
> #		DISPLAY=:2.0 /usr/bin/xscreensaver &
> #		DISPLAY=:2.0 /usr/bin/numlockx on &
73c73
< 		/usr/bin/startx /usr/bin/gnome-session -- :2 2> /dev/null &
---
> 		/usr/bin/startx /usr/bin/gnome-session -- :2 2> $HOME/.virtualX-errors &
```

And here is what I found in .virtualX-errors:
```

xauth:  creating new authority file /home/shark/.serverauth.8154
xauth:  error in locking authority file /home/shark/.Xauthority
xauth:  error in locking authority file /home/shark/.Xauthority
xauth:  error in locking authority file /home/shark/.Xauthority
xauth:  error in locking authority file /home/shark/.Xauthority

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux tack 2.6.22-14-generic #1 SMP Tue Feb 12 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.2.log", Time: Fri Aug 22 2008
(==) Using config file: "/etc/X11/xorg.conf"

(II) Module already built-in
AUDIT: Fri Aug 22 2008: 8172 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified




...
The same error repeated every two seconds
...


..
AUDIT: Fri Aug 22 2008: 8172 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


.FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

giving up.

xinit:  unable to connect to X server

xinit:  No such process (errno 3):  unexpected signal 15.
xauth:  error in locking authority file /home/shark/.Xauthority

```
I have installed dialog, and have edited /etc/X11/Xwrapper.config per your instructions.
Any idea where I'm going wrong?

---

### Post by lswb on 2008-08-22
If you go to Main Menu/System/Admin/Login Window/General, and uncheck "Disable multiple logins for a single user", then you do NOT have to log out or stop any running X programs to login in again with a different window manager, or even the same window manager. Just open the regular logout window, select switch user, select the window manager session you want from the login option menu, then login again using your usual name and password. You can then switch between sessions (and ttys) with the Ctrl-Alt-Fx keys.

---

### Post by Xepra on 2008-10-02
Wow this is functionality that I was blissfully ignorant of up until today.

I actually came across it while trying to run a remote desktop manager locally...

ie  ctrl-alt-f2, log in to that terminal, type  xinit -- :1, then run ssh -XC user@server, type password, then run gnome-session (or startkde or whatever).   This will bring up the entire remote desktop :).  You can do something similar with Xming in windows.


I think many people search for this functionality, but it never seems to be brought up in the discussions regarding Remote Desktop, VNC, NX, RDP, etc.


I also found this script interesting:

[http://ubuntuforums.org/showthread.php?t=552805&page=2](http://ubuntuforums.org/showthread.php?t=552805&page=2)

Although I don't think I have much use for it on a daily basis, maybe some of you will.


Mainly I am posting to as a question though.  Is there a program that runs an entire X server in a window in linux?  Something like Xming does for windows...  Basically can I start a windowed 800x600 pixel X session in an already running gnome environment, and then start programs in that?

---

### Post by bodhi.zazen on 2008-10-02
Yes ..

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948")

---

### Post by Xepra on 2008-10-08
> **bodhi.zazen said:**
> Yes ..

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948")

Perfect =), just what I wanted.

I am actually surprised that this doesn't come up more on the rather common "why doesn't ubuntu support rdp" threads where the reply is usually use vnc, try the beta xrdp, or just tunnel X.  All good suggestions, but this is probably a more useful/appropriate reply (although it is probably good for them to try the other options since this method has a lot of overhead...).

Is it possible to port an existing X session to a different terminal, either local or remote?  Either that or use something like nohup to have the session not close and resume it later?  For that matter can you do it with an arbitrary ssh X tunnel?  Or even cooler, can you use something like screen to replicate the sessions across multiple terminals?

Well I guess you could just use VNC to solve that last one...  but I still feel that there is a gap left between VNC and full X session forwarding.  Basically I still have not across a good way to resume local sessions remotely, or exit remote sessions without killing them and resuming them later.  There are workarounds for most of this, but none that I have found are secure and relatively easy to use/intuitive.

---

### Post by Augustino on 2008-11-17
When I run virtualX after of select gnome say me

/usr/bin/virtualX: 159: /usr/bin/xscreensaver: not found
/usr/bin/virtualX: 159: /usr/bin/numlockx: not found

and I can not use multiseat

What Should I do? :confused: :(

Best regards

---

### Post by bodhi.zazen on 2008-11-17
> **Augustino said:**
> When I run virtualX after of select gnome say me

/usr/bin/virtualX: 159: /usr/bin/xscreensaver: not found
/usr/bin/virtualX: 159: /usr/bin/numlockx: not found

and I can not use multiseat

What Should I do? :confused: :(

Best regards

First, this is not a script for multiseating.

Second, you can either comment out the lines on xscreensaver and numlockx or install those two apps if you wish to use them.

---

### Post by newbuntuxx on 2008-11-24
Hey bodhi,

I was wondering if you or anyone else tried your script on 8.10?

thanks

---

### Post by bodhi.zazen on 2008-11-24
Yes it has been run on 8.10

You need to have all the various window managers installed if you want to use them and it helps if you understand what the script is doing (which is why I posted the description / explanations).

---

### Post by -random on 2009-02-08
Thanks a mil Zazen !

I use this to switch between DotA and browsing.. :popcorn: :p;):o:D;);)

:KS

---

### Post by bodhi.zazen on 2009-02-09
> **-random said:**
> Thanks a mil Zazen !

I use this to switch between DotA and browsing.. :popcorn: :p;):o:D;);)

:KS

You are most welcome , glad you found this information helpful.

---

### Post by say2sky on 2011-05-13
Very helpful. thanks!

Now I hope one step further in virtual X to run windows manager from a different partition.

I have two partition one for booting system, the other for new version ubuntu. I need new version gnome/kde session can be show at booting system's virtual X.

Because X must be started by root, startkde need to be started by normal user. I have tried this.

DISPLAY=:1.0 
X :1&
sudo chroot /media/sda3 su  username -c "/usr/bin/startkde"

It works but when switching back and forth again, system stop there no response.

---

### Post by say2sky on 2011-05-13
Have tried all these

/usr/bin/startx /usr/bin/startkde -- :1 2> /dev/null &
/usr/bin/xinit /usr/bin/startkde -- :1 2> /dev/null &

not work. Suggestions are greatly appreciated.

---

### Post by bodhi.zazen on 2011-05-13
> **say2sky said:**
> Have tried all these

/usr/bin/startx /usr/bin/startkde -- :1 2> /dev/null &
/usr/bin/xinit /usr/bin/startkde -- :1 2> /dev/null &

not work. Suggestions are greatly appreciated.

Start a thread in general help and be sure to include a description of the problem and any error messages you are getting.

---

