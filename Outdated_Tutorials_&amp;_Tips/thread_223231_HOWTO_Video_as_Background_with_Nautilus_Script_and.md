---
title: "HOWTO: Video as Background with Nautilus Script and XGL"
date: 2006-07-26
forum: Outdated Tutorials &amp; Tips
---

### Post by orgy on 2006-07-26
hi, i've made 2 nautilus scripts so you can run video as background when running XGL/Compiz, 1 to start the video, and 1 to stop it.

What you need:

[LIST]
[*]Install xwinwrap through Synaptic Package Manager.
[*]Install mplayer. You can find the .deb right [HERE]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mplayer&searchon=names&subword=1&version=dapper&release=all") along with its perequisites.
[/LIST]

Open a terminal and do:

```
 gedit ~/.gnome2/nautilus-scripts/xwinwrap 
```

and copy and paste this into the file:
[PHP]
#!/bin/bash
xwinwrap -ni -o 0.6 -fs -s -sp -st -b -nf -- mplayer -wid WID "`echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS`"
[/PHP]

Save and close the file. Then:
```
 chmod 700 ~/.gnome2/nautilus-scripts/xwinwrap 
```

Thats all for the first file. Now the script to stop the movie:

```
 gedit ~/.gnome2/nautilus-scripts/stop-xwinwrap 
```


and copy and paste this into the file:
[PHP]
#!/bin/bash
FILE="`echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS`"
kill "`pgrep -fn $FILE`"
[/PHP]

Save and close the file. Then:
```
 chmod 700 ~/.gnome2/nautilus-scripts/stop-xwinwrap 
```

Now just rightclick any video file then select "Scripts" and then "xwinwrap" or "stop-xwinwrap"

[COLOR="Red"]NOTE: THESE SCRIPTS DONT INCLUDE FILE TYPE VALIDATION, SO JUST BE SURE TO USE THEM ON THE RIGHT VIDEO FILES[/COLOR] ;)

---

### Post by naes on 2006-08-12
Hi

I've extended your script with zenity to give a GUI interface. Hope you like

```
#!/bin/bash
if zenity --question --title="Run movie as desktop background?" --text="This script will allow you to play a movie on the desktop within your XGL environment.\n\nClick the OK button and choose the movie from the file selection."
then
xwinwrap -ni -o 0.6 -fs -s -sp -st -b -nf -- mplayer -wid WID "`zenity --file-selection`"
fi
```

---

### Post by Flipper on 2006-08-12
All Perfect, but how do i stop the script without right clicking the file?
With naes GUI interface, you can select a file :) but to stop , you have to run the stop-xwinwrap from the script-menu that opens when you right click the file that is playing.
Can you update to make the stop script to run from wherever you are?

and how can i make a video "loop" ?

---

### Post by naes on 2006-08-13
To make the movie loop, try adding the -loop <number> (0 means forever) after the mplayer command eg;

```
xwinwrap -ni -o 0.6 -fs -s -sp -st -b -nf -- mplayer -loop 2 -wid WID "`zenity --file-selection`"
```


I've not tried it myself.

Time permitting, I'm hoping to extend the script to allow the user to select a movie (with validation), or a screensaver and the ability to stop same.

---

### Post by Sammi on 2006-08-14
This is fun! :D

---

### Post by dominicguy on 2006-08-14
is it possible to use another player..

ex: totem

---

### Post by el3ktro on 2006-08-22
> **dominicguy said:**
> is it possible to use another player..

ex: totem

I'm afraid not because you need a command line player for this, and mplayer itself is a command line player, Totem comes with a GUI. Please correct me if I'm wrong with that.

Tom

---

### Post by Khuezy on 2007-11-06
How do I make my videos autostart and no sound?
Thanks

---

### Post by rofel on 2007-11-07
Thanks it works perfectly.

---

### Post by Khuezy on 2007-11-08
My video stopped working for some reason

---

### Post by forumkiller on 2007-12-12
mine isnt workin for some reason, does this require a restart or anything?

---

### Post by orgyn on 2007-12-12
do u have mplayer installed? install it if u dont.

hope thats the answer.

---

### Post by forumkiller on 2007-12-12
> **orgyn said:**
> do u have mplayer installed? install it if u dont.

hope thats the answer.

i installed it after, then deleted the scripts and redid everything, still not seeing it in operation.

Are there any other settings i should be looking at?

---

### Post by Georges on 2009-08-09
> **orgy said:**
> 
[LIST]
[*]Install xwinwrap through Synaptic Package Manager.
[/LIST]


There is no such thing like xwinwrap in the ubuntu repositories. But you can get the newest xwinwrap [at tech.shantanugoel.com]("ttp://tech.shantanugoel.com/projects/linux/shantz-xwinwrap")

---

### Post by ngaitanis on 2010-01-17
A bit late on the subject, and maybe wrong, but in order to close the background video from anywhere you can use the following:

[PHP]
#!/bin/bash

kill $(pgrep -fn "mplayer -wid");
[/PHP]

We assume of course that no other instance of mplayer with "-wid" is running at the same time.

---

