---
title: "HOWTO: toggle xwinwrap with script"
date: 2007-03-23
forum: Outdated Tutorials &amp; Tips
---

### Post by muguwmp67 on 2007-03-23
[B][SIZE="4"]You can find instructions on building xwinwrap [here]("http://ubuntuforums.org/showthread.php?t=146533")
[/SIZE][/B]

I've written a script that will
[LIST]
[*]remove the current background and start xwinwrap, if xwinwrap is not running
[*]restore the current background and kill xwinwrap, if xwinwrap is running
[/LIST]

I use this script as a launcher on my gnome panel, so I can toggle my background between a wallpaper and xwinwrap.  The script is currently hard coded to run the electricsheep screensaver hack.  If you use xwinwrap, You can modify the script for whatever your preferred hack is by editing the xwinwrap_string.

```
#!/bin/bash
#
# xwinset.sh version 1.0
# Created: 3/23/07 by mugwump67
#
# This script will:
#    turn on xwinwrap if it is off and set background option to 'none'
#    turn off xwinwrap if it is on and set background option to stretched
#
# future enhancements
#	Currently only switches between none and stretched
#		- better to save all current background settings to config file and restore from there
#	Add right-click integration with nautilus (i.e. click mpeg/hack to set)
#	
#---------------------------
# outline:
#---------------------------

#   If xwinwrap is running, 
# 	shut off xwinwrap
#	set background option to stretched
# 	If xwinwrap is off
#		If current background is not "none"
#			set current background to "none"
#		start xwinwrap
# --------------------------

xwinwrap_string="nice -n 15 xwinwrap -ni -o 0.11 -fs -s -sp -st -b -nf -- /usr/bin/electricsheep --root 1 --nick mugwump67 --zoom 1 --max-megabytes 5000  -window-id WID"

# if xwinwrap is running, 	
if [ -n "$(ps  | grep xwinwrap)" ]
	then
	# shut off xwinwrap, set backgound option to 'stretched'
		killall xwinwrap
		gconftool-2 --type string -s /desktop/gnome/background/picture_options stretched

else
# xwinwrap is off
# 		save current background option to 'none'
# 	start xwinwrap
	gconftool-2 --type string -s /desktop/gnome/background/picture_options none
	$xwinwrap_string &
fi

```

This is the first significant shell script that I've ever written, and its missing a few things because I couldn't figure out how to do them yet (these are listed in future enhancements).  Nonetheless, I hope others find it useful

---

### Post by wconstantine on 2007-04-29
Great job! I got some problems though. I can't make xwinwrap play videos as background without sound properly (I know it's not your scripts fault ;) ). The problem is that the background image still remains, or atleast the main colour. I use gnome, know any way to set it to transparent or just completely turn it off?

---

### Post by muguwmp67 on 2007-04-30
Here's my example xwinwrap string:

```
nice -n 15 xwinwrap -ni -o 0.11 -fs -s -sp -st -b -nf -- /usr/bin/electricsheep --root 1 --nick mugwump67 --zoom 1 --max-megabytes 5000  -window-id WID"
```

the -o 0.11 parameter controls the transparency of xwinwrap.  The lower it is, the more transparent xwinwrap is.

After a lot of experimentation, due to an obsessive/compulsive nature, I found for me that a background color of G66, R66 and B67 on the color chooser worked best for me with the 0.11 transparency. I was looking for a subtle moving color image in the background,   Be aware that as you make it more opaque, you will begin to fade the icons on your desktop, if any.

Obviously your preferences will be different, but I found that it took tweaking of both the opacity then the background color to get things they way I wanted.

Using the script will cause the background image to be replaced by whatever the *desktop colo*r setting is for the* selected background image*.

---

### Post by the8thstar on 2007-05-01
Ther's no xwinwrap file in my OS, nor in the repos. Where do you find it?

---

### Post by muguwmp67 on 2007-05-01
I'm not ready to write a new howto on xwinwrap installation yet, but I added a couple of links at the top for more information.

---

### Post by wconstantine on 2007-05-01
> **muguwmp67 said:**
> Here's my example xwinwrap string:

```
nice -n 15 xwinwrap -ni -o 0.11 -fs -s -sp -st -b -nf -- /usr/bin/electricsheep --root 1 --nick mugwump67 --zoom 1 --max-megabytes 5000  -window-id WID"
```

the -o 0.11 parameter controls the transparency of xwinwrap.  The lower it is, the more transparent xwinwrap is.

After a lot of experimentation, due to an obsessive/compulsive nature, I found for me that a background color of G66, R66 and B67 on the color chooser worked best for me with the 0.11 transparency. I was looking for a subtle moving color image in the background,   Be aware that as you make it more opaque, you will begin to fade the icons on your desktop, if any.

Obviously your preferences will be different, but I found that it took tweaking of both the opacity then the background color to get things they way I wanted.

Using the script will cause the background image to be replaced by whatever the *desktop colo*r setting is for the* selected background image*.

So -o 1.00 is totally overwriting the desktop background? =) I found out that if you add the -nosound string to the mplayer string you don't need to have any sound in the video background! =D

---

### Post by muguwmp67 on 2007-05-01
Yup, 1.00 is full opacity.  The nosound thing is good to know.

---

### Post by the8thstar on 2007-05-04
So... where do we gownload this xwinwrap guys?

---

### Post by castoroil97 on 2007-06-18
Thanks, I had wondered how that guy on you tube did it.

Thanks!

---

### Post by overdrank on 2007-07-15
> **muguwmp67 said:**
> [B][SIZE="4"]Xwinwrap is available in some [3rd-party repositories,]("http://3v1n0.tuxfamily.org/") or you can find instructions on building it [here]("http://ubuntuforums.org/showthread.php?t=146533")
[/SIZE][/B]

I've written a script that will
[LIST]
[*]remove the current background and start xwinwrap, if xwinwrap is not running
[*]restore the current background and kill xwinwrap, if xwinwrap is running
[/LIST]

I use this script as a launcher on my gnome panel, so I can toggle my background between a wallpaper and xwinwrap.  The script is currently hard coded to run the electricsheep screensaver hack.  If you use xwinwrap, You can modify the script for whatever your preferred hack is by editing the xwinwrap_string.

```
#!/bin/bash
#
# xwinset.sh version 1.0
# Created: 3/23/07 by mugwump67
#
# This script will:
#    turn on xwinwrap if it is off and set background option to 'none'
#    turn off xwinwrap if it is on and set background option to stretched
#
# future enhancements
#	Currently only switches between none and stretched
#		- better to save all current background settings to config file and restore from there
#	Add right-click integration with nautilus (i.e. click mpeg/hack to set)
#	
#---------------------------
# outline:
#---------------------------

#   If xwinwrap is running, 
# 	shut off xwinwrap
#	set background option to stretched
# 	If xwinwrap is off
#		If current background is not "none"
#			set current background to "none"
#		start xwinwrap
# --------------------------

xwinwrap_string="nice -n 15 xwinwrap -ni -o 0.11 -fs -s -sp -st -b -nf -- /usr/bin/electricsheep --root 1 --nick mugwump67 --zoom 1 --max-megabytes 5000  -window-id WID"

# if xwinwrap is running, 	
if [ -n "$(ps  | grep xwinwrap)" ]
	then
	# shut off xwinwrap, set backgound option to 'stretched'
		killall xwinwrap
		gconftool-2 --type string -s /desktop/gnome/background/picture_options stretched

else
# xwinwrap is off
# 		save current background option to 'none'
# 	start xwinwrap
	gconftool-2 --type string -s /desktop/gnome/background/picture_options none
	$xwinwrap_string &
fi

```

This is the first significant shell script that I've ever written, and its missing a few things because I couldn't figure out how to do them yet (these are listed in future enhancements).  Nonetheless, I hope others find it useful

Thanks, works like a charm! :KS

---

### Post by kahrytan on 2007-09-27
ADMIN: make this posting as BROKEN. Tuxfamily package for xwinwrap is broken and will break apt-get

---

### Post by muguwmp67 on 2007-09-27
Edited to remove link to 3rd party repos.  I cannot imagine how building from source would break apt-get.

---

### Post by kahrytan on 2007-09-27
Actually, it was my fault it broke apt-get. I moved the deb file mid-install.

---

### Post by Flynn555 on 2008-02-22
this is my command....

xwinwrap -ni -argb -fs -s -st -sp -a -nf -- /usr/lib/xscreensaver/glmatrix -root -window-id WID

for some reason im getting this "Error: Unsupported depth 0... exiting"
any thoughts?? help?

---

### Post by muguwmp67 on 2008-02-22
That command string works for me.  

From the error message, I suspect that you are having a driver issue with your graphics card.  There are many threads available on the forums to help you with getting 3d acceleration working on various cards.

---

### Post by Flynn555 on 2008-02-22
i have compiz...all the advanced effects work fine. (cube/wooble windows, ect)  why would those work?

---

### Post by muguwmp67 on 2008-02-22
Honestly, I don't know.  I'm still using edgy, so I don't have compiz installed.  If compiz is working, then I would expect that your 3d acceleration is working too.  

I haven't been 'under the hood' with my Ubuntu installation in over a year now.  I wish I could help more, but I wouldn't even know where to begin looking.

---

### Post by Flynn555 on 2008-02-29
ok for some reason it works with my other screensavers...just not the matrix..

but its covering up all my windows.  and it only appears on one workspace. 

any ideas?

---

### Post by SurferGTO on 2008-03-01
is it possible to use videos ie wmv/mpg's as the backgrounds with this code? how would i go about doing that?

---

### Post by Flynn555 on 2008-03-27
i finally got mine to work...still needs some work though...i covers all the icons but not the windows and the dock so i guess thats all that matters....

whever i dont add the -o option it covers everything windows and all, but when i do add it the video is really chopped up accross the desktop only showing through on certain parts.  oh and how do you set you background color?

> **SurferGTO said:**
> is it possible to use videos ie wmv/mpg's as the backgrounds with this code? how would i go about doing that?

oh and you can play a video  by doing this...

nice -n 15 xwinwrap -ni -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet YOURMOVIE.avi 

--dont know if mplayer supports wmv or mpg but im shure you can find a plugin if it dosent

---

### Post by markp1989 on 2008-05-04
i have a similar script that just disables xwinwrap, or enables it . but it doesnt do any of the other stuff, like changing your wallpaper etc

```
#!/bin/bash

# click to start, click to stop

if pidof xwinwrap | grep [0-9] > /dev/null
then
exec killall xwinwrap
else
exec xwinwrap -ni -argb -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/matrixview -window-id WID &
fi
```

i have a few similar scripts to this that i use to start or stop conky, and another that does teh same to folding at home.

---

