---
title: "Script to arrange connected monitors"
date: 2013-07-02
forum: Programming Talk
---

### Post by halfvulcan on 2013-07-02
Update: added some comments to the script. The script now edits the panel with "widthtype=pixel" so you don't even have to change that setting in your panel.
This is the first bash script I've posted online.  I use LXDE as my desktop environment on a cheap laptop.  I like to connect to external monitors and TVs for playing movies or at home docked for two displays on which I can be doing different tasks. 

PROBLEM: The LXDE desktop arranges icons (unless you micromanage at a per-icon level) so that icons are starting in the upper left, in columns, ending in the lower right. Since the desktop spans both monitors, if you have one monitor logically arranged above the other, then you'll see about half the icons on the top monitor and half on the bottom.  Not acceptable.
WORKAROUND: Always have xrandr arrange them left and right of each other.  this way, so long as you don't have more than an entire desktop full of files/icons, they'll all be on one screen. It's a good enough solution for me.
PROBLEM: If you have the montior with less vertical pixels on the left side (usually the built-in display on a laptop will be less vertical pixels than an external monitor plugged in), you end up missing some of the screen on the left monitor, because the screen must be a perfect rectangle, even if your monitors can't fill it.
WORKAROUND: Put the monitor with most vertical pixels always on the left side.  The left is the side with the icons, so this is logically the most important monitor in the arrangement, and the one we should also make sure the panel is on.
PROBLEM: The panel in its normal configuration wants to span both monitors. Stupid, stupid, STUPID.  Not only does it look bad, but as mentioned earlier, we may not be even able to see the part of the screen on one of the monitors that that part of the panel is on.
WORKAROUND: Made my script manage and reset the panel so it appears on the left monitor only, sized to the exact width of the left monitor.

The following script can be put into the /usr/local/bin folder if you like.  Don't forget to make it executable.  You can edit your /home/$USER/.config/openbox/lxde-rc.xml (carefully, make a backup of it if it's your first time) and insert hotkeys to toggle the script for easy monitor arrangement. 

I give this script freely.  Free as in "use it, change it, post your improvements wherever you like, use it as a defensive weapon, smoke it, give it to minors, whatever".  It's a copy, so you steal nothing from me by using it, obviously. But I'll stop my "Richard Stallman" rant before it starts.  Initially, I based this script on someone else's (much more limited script).  I'll see if I can find out where I found that. I believe about the only thing that's still identifiable is just the "$xset" variable.  Disclaimer: This is just a bash script meant to bridge a functionality gap I found, created by an amateur.  No warrantees, no guarantees, no liability.  Use and modify at your own risk. 

I'm already thinking of things that others will have trouble with using this script.  It might disappear your panel if something goes very wrong.  I haven't seen it happen with this version of the script, but, if it does, open a folder or create a new folder on the desktop and open it, browse to /home/user/.config/lxpanel/LXDE/panels and open open panel with your text editor.  There will or should be a line that starts with "width=".  Make sure it has a number , so "width=800" for instance.  Also, make sure your panel is configured for width in pixels, not percent, before using this script.

This script assumes a bunch of things, though I tried to at least make it universal for detecting output names.  It assumes:
You're using LXDE
You have a maximum of two monitors.
you have the pgrep command in your system.
Your system uses the LXDE panel with panel profile name "LXDE"
Your system uses the LXDE desktop with desktop profile name "LXDE"
Your panel settings are for width in pixels, not percent.  You can check this by rightclicking panel, choose "panel settings"..
You don't have pcmanfm desktop process on a restarting loop like I do (it occasionally crashes and I like it to snap back into existence, so I have it on an endless restart loop in a bash script).  If you have such a setup, just comment out that line in the script where it restarts the desktop, just before the exit line.


```

#!/bin/bash
xstatus=`xrandr -q`
outputs=$(echo "$xstatus" | grep "connect" | sed -e "s/ .*//" | sed ':a;N;$!ba;s/\n/ /g' )
connectedoutputs="$(echo "$xstatus" | grep " connected" | sed -e "s/ connected.*//" | sed ':a;N;$!ba;s/\n/ /g')"

#Let's see what monitors are connected.
connectednumber=0
monitor1=""
monitor2=""
screenwidth=0
screenheight=0

for connectedoutput in $connectedoutputs; do
	#count and label outputs
	connectednumber=$(($connectednumber + 1))
	eval monitor${connectednumber}="$connectedoutput"
	
	defaultres=$(echo "$xstatus" | grep -A 100 "$connectedoutput"  | sed -e "s/.*$connectedoutput connected.*//"  | sed ':a;N;$!ba;s/\n/ /g' | sed -e "s/connect.*//" | grep -w "[0-9]*x[0-9]* *[0-9]*.[0-9]*.+" |  sed -e "s/[0-9]*[[:punct:]][0-9]*.+.*//" | sed "s/[ \t][ \t]*//g" )
	if [ "$defaultres" = "" ] ; then 
		defaultres="$modelinename"
	fi

	defaultwidth=$(echo "$defaultres" | sed -e "s/x[0-9]*//g")
	defaultheight=$(echo "$defaultres" | sed -e "s/[0-9]*x//g")
	if [ "$defaultwidth" -ge "$screenwidth" ] ; then
		screenwidth="$defaultwidth"
	fi
	if [ "$defaultheight" -ge "$screenheight" ] ; then
		screenheight="$defaultheight"
		leftmonitor="$connectedoutput"
	fi

	eval mon${connectednumber}res="$defaultres"
	resolutions=$(echo "$xstatus" | sed -e "s/    .*//" | sed -e "s/_.*//" | sed -e 's|["'\'']||g' | sed -e "s/[a-z]* connect.*//" | sed -e "s/Screen.*//" | sed ':a;N;$!ba;s/\n/ /g' | sed "s/[ \t][ \t]*/ /g" | sed -e "s/.*$connectedoutput //" | sed -e "s/ [A-Z][A-Z]*[0-9].*//")
			
done
		
echo "The number of connected monitors is $connectednumber."
echo "monitor1 is $monitor1 with default resolution of $mon1res"
echo "monitor2 is $monitor2 with default resolution of $mon2res"


# assign the monitors as monitor1 and monitor2
if [ "$connectednumber" = "2" ] ; then
	if [ "$leftmonitor" = "$monitor2" ] ; then
		leftmonres="$mon2res"
		rightmonitor="$monitor1"
		rightmonres="$mon1res"
	else
		leftmonres="$mon1res"
		rightmonitor="monitor2"
		rightmonres="$mon2res"
	fi
fi


#A very sloppy attempt to identify disconnected monitors. I got it working and never bothered making it "look" nicer.
disconnectedoutputs=""				
for output in $outputs ; do
	disconnected="yes"
	for connectedoutput in $connectedoutputs; do
		if [ "$output" = "$connectedoutput" ] ; then
			disconnected="no"
		fi
	done
	if [ "$disconnected" = "yes" ] ; then
		disconnectedoutputs="$disconnectedoutputs $output"
	fi
done				
disconnectedoutputs=$(echo "$disconnectedoutputs" | sed "s/[ \t][ \t]*//")					
echo "disconnectedouputs are $disconnectedoutputs"


#Turn off each disconnected output, thereby also forcing the screen size to react accordingly
for disconnectedoutput in $disconnectedoutputs ; do
	xrandr --output $disconnectedoutput --off
done
	

	
#arrange the monitors, tallest on the left
if [ "$connectednumber" = "2" ] ; then
	xrandr --dpi 96 --output $leftmonitor --mode $leftmonres --pos 0x0 --panning 0x0 --output $rightmonitor --mode $rightmonres --right-of $leftmonitor --panning 0x0
else
	xrandr --dpi 96 --output $monitor1 --mode $mon1res --pos 0x0 --panning 0x0
fi


#edit the lxpanel panel so that it will only span the left monitor.
perl -pi -e "s/width=.*/width=$screenwidth/g" ~/.config/lxpanel/LXDE/panels/panel
perl -pi -e "s/widthtype=.*/widthtype=pixel/g" ~/.config/lxpanel/LXDE/panels/panel

#Identify the pcmanfm desktop process that displays the icons and wallpaper.
desktopprocess="pcmanfm --profile LXDE --desktop"
desktoppid=$(pgrep -f "$desktopprocess")

#sleeping for a moment, maybe not necessary, trying to avoid problems with slow computers and restarting lxpanel too soon after editing panel file.
#I have reason to believe it may be necessary, but my past problems may have been caused by something else.
sleep 1

#restarting lxpanel and desktop
lxpanelctl restart
kill $desktoppid&
$desktopprocess		
exit

```

---

### Post by Vaphell on 2013-07-03
1st part in a much prettier form using arrays. Monitors should be sorted according to H in descending order right off the bat
```
#!/bin/bash

while read cout res
do
  coutputs+=( "$cout" )
  coutres+=( "$res" )
done < <( xrandr -q | awk '/connected/{ co=$1; } /[*]/{ print co, $1; }' | sort -t 'x' -k2nr )

dcoutputs=( $( xrandr -q | awk '/disconnected/{ print $1; }' ) )


echo "connected monitors: ${#coutputs[@]}"
for i in "${!coutputs[@]}"
do
  echo "* monitor #$i: ${coutputs[i]}, resolution: ${coutres[i]} (width: ${coutres[i]%x*}, height: ${coutres[i]#*x})"
done

echo "disconnected outputs: ${#dcoutputs[@]}"
for dc in "${dcoutputs[@]}"
do
  echo "* $dc"
done
```

if you explain what's up exactly with the second part i'd prettify that too.

---

### Post by halfvulcan on 2013-07-06
I tested what you posted and it works as posted. I especially like the sorting of the monitors into order right at the beginning. Very nice and thanks.  By the way, to those noobier than me, you must start these scripts using bash, not sh, unless you move it into your execution path and make it executable, in which case you can just type in the script filename. 

I have a mental block on arrays, but I'll get better with them.  I've added comments into the script to hopefully give you what you need to do more.  I think about all that's left of the script after identifying the monitors is positioning them, tall monitor left, using the xrandr command after making sure to turn off any that are disconnected, just in case xrandr still has them active.  Then, editing the "width=" line in the lxpanel panel file to be the width of the tallest monitor, which is now arranged on the left.  Then tell lxpanel to restart.  Also, to force the background wallpaper to rearrange itself (because it tends not to), kill the pcmanfm desktop process ""pcmanfm --profile LXDE --desktop" and restart it.

By the way, the command I use 
perl -pi -e "s/width=.*/width=$screenwidth/g" ~/.config/lxpanel/LXDE/panels/panel
to edit the panel, may or not be the best way to do it.  I mainly did that because somebody somewhere online recommended that above other methods as being either more efficient or more reliable/less error prone, or something.

Before too long, I'll go ahead and put your changes into the original script above maybe.  I'll maybe post the "before" and "after"  to show what a difference "prettification" can make.  I almost hate to mention it, but I have a much more complex version of this script that I was afraid to post because it does what this script does and much more, but it has bugs.  I figured I'd post this because I knew this is less likely to cause lots of problems for people who try it.  My other script launches a complete zenity menu letting you choose what kind of arrangement you prefer (single LVDS, single VGA, right and left, or panning clones) and what resolutions you'd like for each monitor.  But yeah, the feature-filled you make something, the more error-checking you must have, to make sure the script is responding appropriately to situations as they're changing.  I just barely kept my sanity after racking my brain for over a week on the big script, but it sort of works. I may post it, but it might be confusing to post it also in this same thread.

---

### Post by Vaphell on 2013-07-07
arrays are nice because they have similar level of rocksolidness shell globs have. Once you populate them with elements you don't have to rely on IFS to cut unquoted variable for you, which can give unexpected results if you heavily play with IFS. Also they eliminate most needs for eval and eval usually means bad approach.
Bash also supports associative arrays where elements are indexed by strings. I initially wanted to use them to have *resolution[monitor_name]=1920x1080* but once i had the eureka moment and got the idea to sort monitors preemptively i had to abandon them. The only way to guarantee initial order is integer indexed array.

---

