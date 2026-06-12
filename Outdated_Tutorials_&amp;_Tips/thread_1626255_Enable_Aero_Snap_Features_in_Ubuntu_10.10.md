---
title: "Enable Aero Snap Features in Ubuntu 10.10"
date: 2010-11-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Poizhan on 2010-11-20
[Aero Snap Functionality?]("http://wwww.ubuntuforums.org/showpost.php?p=9190800&postcount=45")

Following this tutorial you will be able to implement snap based window resizing which is almost identical to Windows 7's "Aero Snap" feature.

Prerequisites:

- Compiz Fusion Settings Manager
```
sudo apt-get install compizconfig-settings-manager
```
- WMctrl
- Hardware ID number of your pointing device via xinput list
```
xinput list
```

Create the following three files (DON'T FORGET: MOUSE="11" needs to be changed to your mouse's id# in all three files):

compizsnap-left.sh
```
#!/bin/sh
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#

MOUSE="11"

# ----- Don't edit below this line unless you know what you are doing.
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2-10))

echo $WIDTH
TEMPWIDTH=$(($WIDTH-10))
echo $TEMPWIDTH
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
       while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
    do 
        echo 'button pressed'
    done
    
    if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -le 10 ]
    then
        
        wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-10

    else
        echo "exiting without matching"
        exit 1
    fi
else
        echo "exiting because button isnt "
        exit 1
fi
```

compizsnap-right.sh
```
#!/bin/sh
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#

MOUSE="11"

# ----- Don't edit below this line unless you know what you are doing.
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2))

echo $WIDTH
TEMPWIDTH=$(($WIDTH-10))
echo $TEMPWIDTH
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
       while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
    do 
        echo 'button pressed'
    done
    
    if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -ge $TEMPWIDTH ]
    then
        
        wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1

    else
        echo "exiting without matching"
        exit 1
    fi
else
        echo "exiting because button isnt "
        exit 1
fi
```
compizsnap-max.sh
```
#!/bin/sh
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#

MOUSE="11"

# ----- Don't edit below this line unless you know what you are doing.
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
       while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
    do 
        echo 'button pressed'
    done
    if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[1\]=." | sed s/"valuator\[1\]="//)" -le 10 ]
    then
        
        wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz

    else
        echo "exiting without matching"
        exit 1
    fi
else
        echo "exiting because button isnt "
        exit 1
fi
```

Now, Fire up Settings > Preferences > CompizConfig Settings Manager and then select the Commands plugin.

Set Command 0:
```
sh ~/.scripts/compizsnap-left.sh
```

Set Command 1:
```
sh ~/.scripts/compizsnap-right.sh
```

Set Command 2:
```
sh ~/.scripts/compizsnap-max.sh
```

And last of all select the Edge Bindings tab and set the appropriate commands to the appropriate edges. 

Command 0 - Left Edge
Command 1 - Right Edge
Command 2 - Top Edge

---

### Post by colinnc on 2010-11-21
Thanks, works great!

---

### Post by wbar2 on 2010-11-29
The right snap script worked for me, but the left and max scripts did not.

I was able to get the left script to work by modifying the following line from

```
    if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -le 10 ]
```

to

```
    if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -ge $TEMPWIDTH ]
```

I am still not able to get the max script to work.

You should probably also note that wmctrl is a prereq for this tutorial. It was not standard in my Ubuntu 10.10 installation.

---

### Post by Dfairlite on 2010-12-21
I have been trying for hours to get this to work to no avail. I think it has something to do with my inputs
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Logitech USB Receiver                       id=8    [slave  keyboard (3)]

```

I can't get any of the three to work. I've followed the directions VERBATIM!
Thanks for any assistance.

---

### Post by AnankeIs on 2011-01-04
This is just awesome

Personally I found it easier to just combine this with "Grid" the compiz plugin and then use xte to simulate the Grid hotkeys so
```
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1'
```
Becomes
```
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_6' 'keyup Control_L' 'keyup Alt_L
```

I found that this also deals correctly with other width considerations like having docky running in panel mode on the left side of my screen. Grid seems to resize correctly accounting for it's width, whereas the wmctrl doesn't!

This would also get the maximize command to work for those that are having trouble with that one. I haven't tested that since I tend to think the maximize is redundant given that dbl clicking a window does that already

---

### Post by xbaez on 2011-02-06
Hello
I need to go watch the Super Bowl

After 2 hours of trying, I give up

I have Logitech G700 Wireless keyboard

EVERYTHING works, I even customised the scripts in order to write the variables to a log, and they work ok

**HOWEVER, ALL OF THE EDGE BINDINGS IN COMPIZ DO NOT WORK**

So all the scripts are never called

I even tried doing other things, like SHOW DESKTOP, doesn't works either

I have 2 monitors, Nvidia GTX 570 Ti, and nothing is working

Perhaps if I use only one monitor it will works?

EDGE BINDINGS: left, top, right

None of them work 

I appreciate the responses

---

### Post by Tlingit on 2011-02-20
> **xbaez said:**
> Hello
I need to go watch the Super Bowl

After 2 hours of trying, I give up

I have Logitech G700 Wireless keyboard

EVERYTHING works, I even customised the scripts in order to write the variables to a log, and they work ok

**HOWEVER, ALL OF THE EDGE BINDINGS IN COMPIZ DO NOT WORK**

So all the scripts are never called

I even tried doing other things, like SHOW DESKTOP, doesn't works either

I have 2 monitors, Nvidia GTX 570 Ti, and nothing is working

Perhaps if I use only one monitor it will works?

EDGE BINDINGS: left, top, right

None of them work 

I appreciate the responses

Same!

---

### Post by xbaez on 2011-02-20
I fixed by restarting my PC

---

### Post by mikeobeda on 2011-02-21
Where should I save the script files?  I've looked in my root folder and there weren't any hidden .script folders there.

If I make the scripts and put them in a .scripts in my home folder, how would I get them to run?  I wish I knew what the ~/. meant, but I don't know how to ask that question with a google search

---

### Post by plafuro on 2011-03-06
Hi everyone!

As the last script on [this thread]("http://ubuntuforums.org/showthread.php?t=1294661") didn't quite cut it for me (working on several screens here), I made some additions to it (became kind of a monster :P)... Maybe other people find it useful.

**Big Thanks to raving** for giving me a good basis to start from!

@raving: Ich hoffe das ist ok für dich!! Ich wäre auch für Verbesserungen, Kritik und mögliche Zusammenarbeit dankbar!! :)

-----

**BIG BOLD DISCLAIMER: This is my first serious attempt to bash scripting, so it may not be beautiful or structured and MANY things could be done better. Just share your thoughts and we will together improve the script!! Oh, and of course you use it on your own resposibility :)**

So now the script will work on **multiple displays** with multiple screens, and will provide f**eedback to the user** of the future position of the window through compiz's firepaint. It's not the classiest solution to it, but was the first resource i had at hand when building this (if anyone has a suggestion on how to draw rectangles easily from a bash script with no further dependencies, let me know!). You can adjust the effect with ccsm.

At the moment the script is configured so that the upper and left corner of side X react exactly the same as the action for side X itself, and the center of the screen just aborts any operation (you can, however, while you still hold your mouse button, still select a sector of the screen to resize your window). As this is based on raving's code, all areas in the screen could be configured to perform a different action.

**Keeping the name of the script as compizconfig is important!!** As moving the mouse to a different edge of the window could trigger different copies of it, I tried to make the script aware of this fact -**based on the filename**.

TL;DR Some improvements made. Here is the code, hope you enjoy it :P


```

#!/bin/bash
#####################################################################
#
# Based on:
# http://wwww.ubuntuforums.org/showthread.php?t=1294661
# http://linuxundich.de/de/ubuntu/aero-snap-mit-gnome-und-compiz/
#
# Extended by plafuro (ubuntuforums) on 2011/3/6
#	- Now it also works on any screen of any display
#	- Particles used for feedback to the user 
#	  (Needs compiz and firepaint plugin, adjust firepaint settings
#	  for desired effect). A better way of drawing this (i.e. with
#	  primitives) is very welcome!.
#		
######################################################################

## Holding the mouse next to the edge may trigger several copies 
## we will try to avoid that

if [ $(echo `ps -ef |grep -c compizsnap.sh`) -gt 5 ]; then
exit
fi

### Store all pointer devices in an array

DEVICES=`xinput -list | grep "slave  pointer" | grep -iv "virtual" | grep id= | sed 's:.*id=\([0-9]*\).*:\1:' `
DEVICE_ARRAY=($DEVICES)
DX=2
DY=42

### On which screen are we? 
### This will allow the script to work for all screens on the current display

THISSCREEN=$(echo $DISPLAY  | cut -f 2 -d '.')
THISSCREEN=$(($THISSCREEN+1))
XINFOSTR=$(xdpyinfo -display $DISPLAY |grep 'dimensions:' | sed -n ''$THISSCREEN'p')

### General screen information
### Tolerance can be adjusted based on user preference 

WIDTH=$(echo $XINFOSTR | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x')
HEIGHT=$(echo $XINFOSTR | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 2 -d 'x' | cut -f 1 -d p)
WIDTH=$(($WIDTH+1-1))    #Damit Leerzeichen in WIDTH u. HEIGHT wegfallen... Geht bestimmt "schöner"
HEIGHT=$(($HEIGHT+1-1))
HWIDTH=$(($WIDTH/2-$DX))
HHEIGHT=$(($HEIGHT/2-$DY))
VTOLERANCE=$(($HEIGHT/5))
HTOLERANCE=$(($WIDTH/5))
XROOT=$(xwininfo -root | grep id: | awk '{ print $4 }')

### Position of the mouse
SECTOR=0

### Coordenates for effects
Particle1X=0
Particle2X=0
Particle3X=0
Particle4X=0
Particle1Y=0
Particle2Y=0
Particle3Y=0
Particle4Y=0
NEWMOUSEPOSITION=0
OLDMOUSEPOSITION=0


### The tolerance can be adjusted for a better recognition of the
### screen sector. This works well on 1280x1024 and 1920x1080

VTOLERANCE=$(($HEIGHT/5))
HTOLERANCE=$(($WIDTH/5))


##############################################################
### mousePosition
### This will store mouse position in the screen 
### as a sector (upperleft, upperright, top, bottom, etc)
##############################################################

mousePosition(){

    X=$(xdotool getmouselocation | awk '{print $1}' | cut -d : -f 2)
    Y=$(xdotool getmouselocation | awk '{print $2}' | cut -d : -f 2)

    TEMP=0
    #Horizontal
    if [ $X -lt $(($HWIDTH-$HTOLERANCE)) ]; then
        SECTOR=1    					#left
	TEMP=1
    fi

    if [ $X -gt $(($HWIDTH+$HTOLERANCE)) ]; then
        SECTOR=2    					#right
	TEMP=1
    fi

    #Vertikal
    if [ $Y -lt $(($HHEIGHT-$VTOLERANCE)) ]; then
        SECTOR=$((C+3))    				#top
	TEMP=1
    fi 

    if [ $Y -gt $(($HHEIGHT+$VTOLERANCE)) ]; then
        SECTOR=$((C+6))    				#bottom
	TEMP=1
    fi

    if [ $TEMP -lt 1  ];then
	SECTOR=0					#center
    fi

    NEWMOUSEPOSITION=$SECTOR

    case $SECTOR in
    0)  #CENTER
	particlesCenter		;;
    3)  #TOP
	particlesTop		;;   
    1)  #LEFT
	particlesLeft		;;   
    2)  #RIGHT
	particlesRight		;;         
    6)  #BOTTOM
	particlesBottom		;;   
    4)  #UPPERLEFT
	particlesUpperLeft	;;   
    5)  #UPPERRIGHT
	particlesUpperRight     ;;   
    7)  #LOWERLEFT
	particlesLowerLeft      ;;   
    8)  #LOWERRIGHT
	particlesLowerRight     ;;   
    esac

}

########################################################################
### do_SECTOR
### This function triggers the action corresponding to a certain sector
########################################################################

do_Sector() {

    case $SECTOR in
    0) do_center     ;;
    3) do_top	     ;;   
    1) do_left       ;;
    2) do_right      ;;       
    6) do_bottom     ;;
    4) do_upperleft  ;;
    5) do_upperright ;;
    7) do_lowerleft  ;;
    8) do_lowerright ;;
    esac
}

##########################################################################
### particlesXXX
### Particle positions for the different sectors in the screen/behaviours
##########################################################################

particlesTop(){
	
	#Particle1X=0
	#Particle1Y=0

	#Particle2X=0
	#Particle2Y=$WIDTH

	#Particle3X=0
	#Particle3Y=$HHEIGHT

	#Particle4X=$WIDTH
	#Particle4Y=$HHEIGHT

	particlesFullScreen
}


particlesBottom(){


	Particle1X=0
	Particle1Y=$((HHEIGHT+DY))
	Particle2X=$WIDTH
	Particle2Y=$((HHEIGHT+DY))
	Particle3X=0
	Particle3Y=$HEIGHT
	Particle4X=$WIDTH
	Particle4Y=$HEIGHT

}

particlesLeft(){

	Particle1X=0
	Particle1Y=0

	Particle2X=$HWIDTH
	Particle2Y=0

	Particle3X=0
	Particle3Y=$HEIGHT

	Particle4X=$HWIDTH
	Particle4Y=$HEIGHT


}

particlesRight(){


	Particle1X=$HWIDTH
	Particle1Y=0

	Particle2X=$WIDTH
	Particle2Y=0

	Particle3X=$HWIDTH
	Particle4X=$WIDTH
	Particle3Y=$HEIGHT
	Particle4Y=$HEIGHT

}

particlesUpperRight(){

particlesRight

}

particlesUpperLeft(){

particlesLeft

}


particlesLowerRight(){

particlesRight

}

particlesLowerLeft(){

particlesLeft

}

particlesFullScreen(){


	Particle1X=0
	Particle1Y=0

	Particle2X=$WIDTH
	Particle2Y=0

	Particle3X=0
	Particle4X=$WIDTH
	Particle3Y=$HEIGHT
	Particle4Y=$HEIGHT

}

particlesCenter(){

clearParticles
	Particle1X=0
	Particle1Y=0
	Particle2X=0
	Particle2Y=0
	Particle3X=0
	Particle4X=0
	Particle3Y=0
	Particle4Y=0

}

###############################################################
### do_XXX
### Actions for the different sectors in the screen/behaviours
###############################################################


do_top(){

#wmctrl -r :ACTIVE: -b remove,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$WIDTH,$HHEIGHT
do_FullScreen
}

do_bottom(){
wmctrl -r :ACTIVE: -b remove,maximized_vert & wmctrl -r :ACTIVE: -e 0,0,$((HHEIGHT+DY)),$WIDTH,$HHEIGHT

}

do_right(){
wmctrl -r :ACTIVE: -b remove,maximized_horz & wmctrl -r :ACTIVE: -b add,maximized_vert & wmctrl -r :ACTIVE: -e 0,$((HWIDTH+DX)),0,$HWIDTH,0

}


do_left(){

wmctrl -r :ACTIVE: -b remove,maximized_horz & wmctrl -r :ACTIVE: -b add,maximized_vert & wmctrl -r :ACTIVE: -e 0,0,0,$HWIDTH,0

}


do_upperleft(){

do_left

}


do_lowerleft(){

do_left

}


do_upperright(){

do_right

}


do_lowerright(){

do_right

}

do_center(){

clearParticles

}

do_FullScreen(){

wmctrl -r :ACTIVE: -b add,maximized_vert & wmctrl -r :ACTIVE: -b add,maximized_horz

}

####################################################################
### createXXX and clearParticles
### These funcions are meant for section previsualisation purposes,
### not really needed, but wanted to give the user some feedback 
### on what will happen if mouse button is released
####################################################################

createSingleParticle(){

dbus-send --type=method_call --dest=org.freedesktop.compiz/org/freedesktop/compiz/dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/firepaint/allscreens/add_particle org.freedesktop.compiz.activate string:'root' int32:$XROOT string:'x' double:$1 string:'y' double:$2

}

createParticles(){

## For the sake of performance we will avoid drawing along the x axis 
## if the line to draw is at the very top or the very bottom

if [ $Particle1Y -gt 0 ]; then
createParticleLineX $Particle1X $Particle2X $Particle1Y 
fi

if [ $Particle3Y -lt $HEIGHT ]; then
createParticleLineX $Particle3X $Particle4X $Particle3Y 
fi

createParticleLineY $Particle2Y $Particle3Y $Particle2X 
createParticleLineY $Particle1Y $Particle3Y $Particle1X

}

createParticleLineY(){

for (( i=$1; i<$2; i=$i+40 )) 
do

createSingleParticle $3 $i

done

}

createParticleLineX(){


for (( i=$1; i<$2; i=$i+40)) 
do

createSingleParticle $i $3

done

}

clearParticles(){

dbus-send --type=method_call --dest=org.freedesktop.compiz/org/freedesktop/compiz/dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/firepaint/allscreens/clear_key org.freedesktop.compiz.activate string:'root' int32:$XROOT

}

##############################################################
### "Main" process
##############################################################

#Ermittlem, ob Button gedrückt ist || Check for button being pressed down
DOWN=0
for i in ${!DEVICE_ARRAY[@]}
do
    if [ `xinput --query-state ${DEVICE_ARRAY[i]} | grep down` ]; then
        DOWN=1
    fi
done

## Button gerückt?  || Is the button pressed?
if  [ $DOWN -gt 0 ]; then

    mousePosition
    createParticles
    OLDMOUSEPOSITION=$NEWMOUSEPOSITION			    ## Before starting the loop, save current mouse position

    ## Prüfe solange, bis Button losgelassen wurde... || Wait until button is released
    
    while [ $DOWN -gt 0 ]    
    do 

	mousePosition 					    ## Store mouse position

	if [ $NEWMOUSEPOSITION != $OLDMOUSEPOSITION ]; then ## If the mouse has moved, clear and redraw
	   clearParticles
	   createParticles	
	fi
	
        
	OLDMOUSEPOSITION=$NEWMOUSEPOSITION
        DOWN=0

        for i in ${!DEVICE_ARRAY[@]}
        do
            if [ `xinput --query-state ${DEVICE_ARRAY[i]} | grep down` ];then
                DOWN=1
		
            fi
        done

    done   
    ## ...dann nehme Aktionen vor.  || When the mouse is released, clear and resize the window
    clearParticles
    do_Sector
fi

```

---

### Post by JBauerIV on 2011-04-25
@plafuro

How do you install and use your script?

---

