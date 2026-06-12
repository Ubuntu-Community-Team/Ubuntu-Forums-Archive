---
title: "xgl desktop screensaver script"
date: 2006-06-18
forum: Outdated Tutorials &amp; Tips
---

### Post by enkidu75 on 2006-06-18
Hi all. Here's a little script that will run a specified screensaver as a script on your desktop. If you call it again with the name of a different screensaver, the first one will be killed and the second one started. If you call it again with the name of the same screensaver, the original one will be called.

eg
```

dss atlantis  #runs atlantis on desktop
dss juggler3d #kills atlantis, runs juggler on desktop
dss juggler3d #kill juggler
```
dss plamsa 0.3 #run plasma on desktop at 0.3 opacity

You can assign the script to hotkeys, panel items, etc etc.

Note I think this only works with xgl- I haven't got it going under standard gnome etc.

First up, you'll need xwinwrap:

```
sudo apt-get install xwinwrap
```

Then paste the following into a file and make it executable. I call mine dss for Desktop Screen Saver, and I keep it in /usr/bin

```
#!/bin/bash

# Desktop screen saver flip flopper
# This script runs a screensaver on your desktop,
# and drops the name of the screensaver in a marker file.
# When run a second time, it will kill the screensaver,
# and optionaly start another, if the name of a different screensaver
# is passed as an arg.
# Requires xwinwrap to be installed.


# dir to write marker file to
DIR=~/

#Niceness to run screen saver at. The lower this value, the higher
#priority the screensaver will be. The higher the value, the jerkier
#the screensaver will be, and the less it will intefere with your
#work
NICENESS=13

#directory where your screensavers live
SSDIR=/usr/lib/xscreensaver/
 
if [ -z "$1" ]
then
  echo "Usage: dss <screensaver> <opacity>"
  echo " where <screensaver exists in $SSDIR, and opacity (optional) is between 0.0 and 1.0"
  exit
fi
OPACITY=$2
if [ -z $2 ]
then
  OPACITY=1.0
fi

  
SCREENSAVER=$1

if [ -e $DIR.flipflopmarker ]
then
	#get the name of the currently running desktop screensaver
	#kill it, remove the marker file
	OLDSCREENSAVER=`cat $DIR.flipflopmarker`
	killall `cat $DIR.flipflopmarker` 
	rm $DIR.flipflopmarker
fi
if [ "$SCREENSAVER" != "$OLDSCREENSAVER" ]
then
	#start the screensaver, write the name of it to a file
	nice -n $NICENESS xwinwrap -ni  -o $OPACITY -argb -fs -s -st -sp -b -nf -- $SSDIR$1 -root -window-id WID &
	echo $SCREENSAVER  > $DIR.flipflopmarker
fi
exit
```

---

### Post by Indras on 2006-06-25
Hey, thanks, I've been looking for something like this since I found xwinwrap.

I make it run on login... go to System->Preferences->Sessions, open the Startup Programs tab and hit Add, type in "dss <screensaver>"

Atlantis and GLMatrix are my favorites so far.

I know that xwinwrap has an opacity option (-o) to set these slightly translucent.  Is there a way to set that up with this script?  Plasma would make an awesome background, but since it is a solid color, it covers your desktop icons.

---

### Post by Kratos on 2006-06-27
This is a general xwinwrap question that I figured I would ask here. I run XGL on a TwinView display, and when I use xwinwrap, it focuses to my off-hand monitor (monitor 1). Is there a command argument that will force it to focus on my primary monitor? Or, better yet, span both?

Thanks,

Kratos

---

### Post by enkidu75 on 2006-06-27
[QUOTE=Indras]
I know that xwinwrap has an opacity option (-o) to set these slightly translucent.  Is there a way to set that up with this script?  Plasma would make an awesome background, but since it is a solid color, it covers your desktop icons.[/QUOTE]

I've updated the post to add opacity. Neat- I didn't know you could do that :) My favorite with opacity is plasma, but pong is pretty cute too.

Cheers :)

---

### Post by domino on 2006-06-27
Nice one! I went crazy trying to kill the dss :). Now i'm looking for a screensaver that doesn't take 50% cpu time and looks great. Anyone?

Thanks

---

### Post by risbac on 2006-06-29
Try electricsheep! It's not using a lot of CPU, and it looks nice. My only complain is that I can't slow down the animation enough... I can change the framerate, but then it's not smooth anymore. Would be better to keep the framerate, but slow down the animation.

> his is a general xwinwrap question that I figured I would ask here. I run XGL on a TwinView display, and when I use xwinwrap, it focuses to my off-hand monitor (monitor 1). Is there a command argument that will force it to focus on my primary monitor? Or, better yet, span both?

+1 on this one!

---

### Post by Indras on 2006-06-29
[QUOTE=enkidu75]I've updated the post to add opacity. Neat- I didn't know you could do that :) My favorite with opacity is plasma, but pong is pretty cute too.

Cheers :)[/QUOTE]

Sweet, that's exactly what I was looking for.  TYVM!

---

### Post by deadlychicken22 on 2006-08-10
How do you get it to work with electricsheep? I have installed it from the repositories, but every time I try to direct dss to /usr/bin/electricsheep it doesn't work. I've edited the script to point to that directory but it still doesn't work. What am I doing wrong?

---

### Post by TNBY963 on 2006-08-11
Thanks a lot! This runs just great.
Everyday I am amazed at what Ubuntu can do It seems like the sky is the limit.

The only downside of this is that it's very cpu intensive. But that has nothing to do with this great guide.

---

### Post by Sam on 2006-08-11
Thanks for the tip ! That's a great way of impressing your non-UNIX friends !!

---

### Post by Lunar_Lamp on 2006-08-17
Try 'dss tangram' - it looks fantastic!

---

### Post by Attila_fdd on 2006-11-19
hello i have a little problem with this script...
it runs perfectly but i have to launch it 2 times, why?
the first time it says "no processes are terminated" (or something similar) and the second time it runs. I would like to put on session to have this script loaded on session boot, but for the problem above it doesnt work. Any suggestion?

i use it on ubuntu dapper with xgl and beryl

---

### Post by qsuc on 2006-12-27
I'm not able to install xwinwrap - apt-get and Synaptic can't find it. Universe and Multiverse repositories are enabled. Any ideas?

---

### Post by JayRoe on 2007-01-07
> **qsuc said:**
> I'm not able to install xwinwrap - apt-get and Synaptic can't find it. Universe and Multiverse repositories are enabled. Any ideas?

I have the same problem.

---

### Post by speckman on 2007-03-30
i've been using polytopes for a couple years with X, or whatever is standard.  with my graphics card, it doesn't take any cpu time (unless it displays the biggest object).

i think the way i do it, i just run nautilus with --no-desktop and run the screensaver as -root.  i have an icon on my taskbar for a special nautilus so it doesnt try to redisplay the desktop.
(i attached a screenshot that i took a while back, a couple ubuntus ago.  you can see the low cpu usage :))

sure is a good way to impress people :)  
"wow what's that?"  "oh yeah, 4d object in my background..."


another thing i wanna do is, once i figure out this 3d desktop stuff, (i'm pretty clueless when it comes to most of this), pipe all output to a filter.  this filter keeps track of a 2d array of "liquid".  10 years ago i wrote an asm program that simulated raindrops falling down a window.  it's pretty easy once you get the rules right.  it's not like i used physics or anything, i just made up rules until i got it right.  you just treat this array as height values and use it as a lens.  diffract the screen behind it.  like i said, i just had to get the rules right.

anyway, it looked pretty cool.  raindrops falling down your screen.  it wouldnt take much cpu at all now.  it'd be neat to have a window in which you could change the drop size, liquid type, speed, etc.

actually, i hope someone else does this :P

---

### Post by soulbreak on 2007-09-13
For whatever reason when I run dss, xwinwrap overlaps everything on the screen.  I can still interact with the terminal I just can't see it.  Just the screensaver.

---

### Post by unlucky.break on 2007-10-19
Hi, long time reader of these forums, first time posting...

I can't seem to get this to work.  I've got** /usr/bin/** as my location for the dss file and as the location of my screensaver.

I run **dss electricsheep** and get:
     electricsheep: no process killed
     rm: remove write-protected regular file `/usr/bin.flipflopmarker'?  *enter* y
     rm: cannot remove `/usr/bin.flipflopmarker': Permission denied
SO...
I run "***sudo* dss electricsheep**" and get:
     electricsheep: no process killed
I run again, and get:
     bad option: -root, try --help
     /usr/bin/electricsheep died, exit status 1

 when I do "**whereis electricsheep**"  I get:
     /usr/bin/electricsheep
     /usr/X11R6/bin/electricsheep      --this links back to dir bin 
     /usr/bin/X11/electricsheep
     /usr/share/electricsheep
     /usr/share/man/man1/electricsheep.1.gz

I try changing the screensaver loacation in the **dss** script to **/usr/bin/X11/** and get the same result as if the location was **/usr/bin/**

I change the screensaver location in the **dss** script to **/usr/share/**
I run **sudo dss electricsheep** and get:
     electricsheep: no process killed
I run again, and get:
     /usr/share/electricsheep: Permission denied
     /usr/share/electricsheep died, exit status 2

But it's ***also*** in **/usr/share/applications/screensavers/** as: **electricsheep.desktop**.  I look at **that** file's properties, and see the options: **--root 1 --zoom 1**  I am not permitted to change these.  And I haven't explored how to do so.

I change the screensaver location in the **dss** script to **/usr/share/applications/screensavers/**
I run **sudo dss electricsheep.desktop** and get:
     electricsheep.desktop: no process killed
I run again, and get:
     /usr/share/applications/screensavers/electricsheep.desktop: 2: [Desktop: not found
     /usr/share/applications/screensavers/electricsheep.desktop: 5: Sheep: not found
     /usr/share/applications/screensavers/electricsheep.desktop: 7: --root: not found
     /usr/share/applications/screensavers/electricsheep.desktop died, exit status 0

I'm running Ubuntu Feisty Fawn, KDE desktop,  GeForce 6200 , TV-out as my second display
I'm not sure what further info I can provide that would be useful.
Any help is appreciated.

---

### Post by briandotcom0 on 2008-04-24
this is just what I am looking for, but I tried "sudo apt-get install xwinwrap" and it gave me a "E: Couldn't find package xwinwrap". I googled xwinwrap, but i couldn not find a way to get it. anyone know how to get xwinwrap?

---

### Post by briandotcom0 on 2008-04-24
to change permissions: "sudo chown <userName> <fileName>"

---

