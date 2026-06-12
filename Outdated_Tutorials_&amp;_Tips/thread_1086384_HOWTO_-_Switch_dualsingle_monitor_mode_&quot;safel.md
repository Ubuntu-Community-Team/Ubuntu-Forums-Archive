---
title: "HOWTO - Switch dual/single monitor mode &quot;safely&quot; with script"
date: 2009-03-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Sam Lars on 2009-03-04
I've been using a second monitor with my laptop at home for a little bit now, but only the laptop's screen everywhere else I go.  It's gotten a bit old to have to switch between the settings in gnome-display-properties, and I ran into some other annoyances along the way.
I decided to write a script that would take care of all the work for me.
There are some things in here specific to my setup that you should change if you want to use this for yourself.
I'll note the things that require attention, and post the script at the bottom.

```
killall ...
```
These are three programs that I find I need to restart when my screen resolution changes.  I want them all aligned to the bottom of my screen, but when I put the second monitor on top, they end up in the wrong place.
They are started again at the end of the script.  If you don't have these programs or have others you would like to restart, place them in these places.

```
nohup metacity --replace & sleep 5
```
I've noticed that when switching resolution with Compiz running, it sometimes crashes X and returns me to my login screen.  I lose everything I had open.  Not fun.
So I switch to Metacity for the resolution change, which has worked great for me.
The nohup shouldn't be necessary here, but it just lets it know that if this script exits, it shouldn't kill Metacity (I've been stuck without a window manager too many times...).  It's more important when the programs that were killed in the previous part are restarted at the end of the script.
The & tells the script to move on and not wait until the previous command exits.
I have it sleep 5 seconds to wait for Metacity to come up and get settled in before I throw the next part at it.

```
export season=`xrandr | grep VGA | cut -c16-19`
if [ "$season" == 'norm' ]; then
```
This is some code specific to my setup.  Basically what it is doing is switching modes.  This is so it knows whether it is set up with a second monitor or not and switches it off or on accordingly.  Maybe there's a better way to do this, but this is how I did it.
A couple things to note:
The command xrandr will tell you what your current display settings are.  The first command is taking the info from where it says "VGA."  This is my second monitor connection.  You should look at the output of your xrandr to see what it calls your second monitor.
The other thing is where it is cutting.  You should run the command
```
xrandr | grep VGA | cut -c16-19
```
to see what it outputs for you.  You can adjust the numbers at the end to tell it what part to look at.  The if statement should then be told to look for what that output is when the second monitor is not set up.  So when my second monitor is not active, that command will return "norm."  You should change yours accordingly.

```
xrandr --output VGA --mode 1280x1024 --above LVDS --pos 800x0
```
This is the command that tells the second monitor what to do.
The VGA is the name of my second monitor.  This comes from xrandr.  It should be the same in the second command, which switches the monitor off.
The 1280x1024 is the resolution for it.
The "above" tells the second monitor to be above LVDS (name of my laptop's screen, from xrandr).  Other options are "right-of," "left-of," and "below."
The 800x0 tells it to be 800 up.  I'm not sure this is necessary given the "above" part, but it doesn't seem to hurt.  800 is just the vertical resolution of my laptop screen (1280x800).

```
gconftool-2 -s -t int /apps/avant-window-navigator/monitor_height 1824
```
Another thing that needs changed is AWN's location.  To keep it at the bottom of the screen, I have to change this value.
The first command, 1824 (800 + 1024), puts it at the bottom of the two monitors together.  The second one in the script, 800, puts it at the bottom of my laptop screen.
If you have your monitors set up differently, you may not need this, or may want to set the monitor_xoffset value instead.




```
#!/bin/bash
#set -x
echo " * Killing conky"
killall conky
echo " * Killing stalonetray"
killall stalonetray
echo " * Killing awn"
killall awn
#echo " * metacity --replace"
#nohup metacity --replace > /dev/null & sleep 5
#gnome-display-properties; sleep 1
echo " * Determining time and season..."
export season=`xrandr | grep VGA | cut -c16-19`
echo " * The season is" $season
echo " * Setting screen resolution"
if [ "$season" == '280x' ]; then
echo " * Going home"
xrandr --output VGA --off
gconftool-2 -s -t int /apps/avant-window-navigator/monitor_height 800
else
echo " * Going big"
xrandr --output VGA --mode 1280x1024 --above LVDS --pos 800x0
gconftool-2 -s -t int /apps/avant-window-navigator/monitor_height 1824
fi
#echo " * compiz --replace"
#nohup compiz --replace > /dev/null & sleep 5
sleep 2
echo " * Starting stalonetray"
nohup stalonetray > /dev/null &
echo " * Starting awn"
nohup avant-window-navigator > /dev/null &
echo " * Starting conky"
nohup conky > /dev/null &
```

---

### Post by pendlaren on 2009-09-18
Hi,

Thanks for posting this info - I've been doing this switching manually for a too long time now!

I don't run any of your three apps, neither compiz, so I thought just running this simple script should work?

```

#!/bin/bash
export season=`xrandr | grep VGA | cut -c18-21`
echo " * The season is" $season
if [ "$season" == 'norm' ]; then
        echo " * Going big"
        xrandr --output VGA --mode 1680x1050 --left-of LVDS --pos 0x1680
else
        echo " * Going home"
        xrandr --output VGA --off
fi
echo " * metacity --replace"
nohup metacity --replace & sleep 5

```

Running this does not affect the display settings, as far as I can see, except some blinking when metacity replaces itself, I guess. The output I get is:
```

 * The season is 680x
 * Going home
 * metacity --replace
nohup: appending output to `nohup.out'

```

running xrandr shows that both VGA and LVDS is still active:
```

Screen 0: minimum 320 x 200, current 3080 x 1050, maximum 3080 x 1050
VGA-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 433mm x 271mm
LVDS connected 1400x1050+1680+0 (normal left inverted right x axis y axis) 287mm x 215mm
DVI-0 disconnected (normal left inverted right x axis y axis)

```

Also tried replacing with compiz in last line, but still keeps dual screen setting.

Any ideas?

---

### Post by Sam Lars on 2009-09-18
First of all, you may not have to run the Metacity command... I think I was just doing that because Compiz didn't like resolution changes.

Also, I think I changed my script a little since I posted it here... so I'm changing that in the original post. I'm not sure how much it would change what you're trying to do, though.

I would suggest looking at the xrandr command that it's running. First, try changing the name to VGA-0 instead of just VGA. You can just run that command to make sure it works.

---

### Post by pendlaren on 2009-09-21
> **Sam Lars said:**
> I would suggest looking at the xrandr command that it's running. First, try changing the name to VGA-0 instead of just VGA. You can just run that command to make sure it works.

ah... simple as that! :)

I didn't notice the difference in my xrandr output, and thought the xrandr command did some settings and then metacity "applied" it.

Thanks a lot for your help - this will save me time and frustration!

---

