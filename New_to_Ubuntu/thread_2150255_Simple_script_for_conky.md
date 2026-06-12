---
title: "Simple script for conky"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by Grubbie on 2013-05-31
Hello out there!

I recently setup a new server and noticed that my Conky displayed correctly when accessing the server from my iPad using xrdp, but when accessing it from the local terminal, the display was badly jumbled. This is because my local display (monitor) is a 1920 x 1080 display size, where my remote using the iPad is set to 1024 x 768.

I looked through the forums for a solution, but was not able to find anything relating to my situation. So After a bit of head scratching, I ended up writing a bash script that determines which display is being used, and then applies the appropriate Conkyrc file for that display.

Here is the code I came up with:

```

if [ $DISPLAY  != :0 ]
   then
       conky -c /path/to/your/conkyrc/for/remote/display
   else
       conky -c /path/to/your/conkyrc/for/local/display
fi

```

Keep in mind this works specifically where a single local display is used, and a single type of remote display is used. It would require a few more lines of code for different arrangements. My remote access uses Display :10.0 and above (basically anything BUT Display :0).

I hope this is helpful to somebody!

Grubbie :cool:

---

### Post by HiImTye on 2013-06-01
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
here's what I use
tconk.sh
```
cd $HOME
#!/bin/bash
# load our settings
. $HOME/Launchers/.tconk-settings-general
# create and link our temp folder
$HOME/Launchers/.tconk-scripts-linkTmpFiles.sh

# enable Conky
STARTCONKY=no        # Set to anything other than 'yes' to stop conky from
             # loading

# load our startup programs
if [ -f $HOME/Launchers/.tconk-extras-startupTasks.sh ]; then
 $HOME/Launchers/.tconk-extras-startupTasks.sh &
fi

# if we were given additional arguments, sleep for 25 seconds.
 # this is useful, if we are running this at startup we can simply call it with:
 # /path/to/script.sh 1
 # and it will give the window manager time to load, without delaying the script when we manually run it
if [ -n "$1" ]; then
 sleep 25
fi
# kill any existing conky instances, if there are any
if ps -e | grep conky; then
 killall conky
fi
DIMENSIONS="$(xrandr --current|sed -n 's/.*current[ ]\([0-9]*\) x \([0-9]*\),.*/\1x\2/p')"

# our list of dimensions. to add more, add another one (i.e. OPTION3="800x600") and then copy the entire
 # section that is indicated below and paste it directly above where it says to below. once you have done
 # that, change the values to what you want them to be. they should be as follows:
 # t<arg>_a = alignment: top/bottom/middle_left/right/middle *or* two letter abbreviation (i.e tr for top_right)
 # t<arg>_x = x offset (-90, 90, etc)
 # t<arg>_y = y offset
OPTION1="1920x1080"
OPTION2="1360x768"
if [ "$DIMENSIONS" = "$OPTION1" ]; then
 ttime_a=br
 ttime_x=175
 ttime_y=0
 tmemory_a=bl
 tmemory_x=0
 tmemory_y=0
 tnetdown_a=bl
 tnetdown_x=0
 tnetdown_y=258
 tnetup_a=br
 tnetup_x=0
 tnetup_y=304
 tcpu_a=br
 tcpu_x=0
 tcpu_y=0
 tdeluge_a=tr
 tdeluge_x=0
 tdeluge_y=0
 tmpd_a=br
 tmpd_x=418
 tmpd_y=0
# --- copy from here --- #
elif [ "$DIMENSIONS" = "$OPTION2" ]; then
 ttime_a=bm
 ttime_x=0
 ttime_y=0
 tmemory_a=bl
 tmemory_x=40
 tmemory_y=0
 tnetdown_a=bl
 tnetdown_x=250
 tnetdown_y=0
 tnetup_a=br
 tnetup_x=250
 tnetup_y=0
 tcpu_a=br
 tcpu_x=40
 tcpu_y=0
 tdeluge_a=tr
 tdeluge_x=280
 tdeluge_y=20
 tmpd_a=tr
 tmpd_x=40
 tmpd_y=20
# --- to here --- #

# --- paste above this line and change "$OPTION2" to the OPTION# that you added above --- #
else
 echo "no settings specified for the range dimensions=$DIMENSIONS"
 DIMENSIONS='$(zenity --list --radiolist --text "Settings not found for range $DIMENSIONS" --column "" --column "Choose" FALSE $OPTION1 TRUE $OPTION2)'
 if [ "$DIMENSIONS" = "" ]; then
  echo user hit \'Cancel\'
  exit
 fi
fi

 # *** Conky windows ***
if [ "$STARTCONKY" = "yes" ]; then
 # system monitors
 conky -a $ttime_a    -x $ttime_x     -y $ttime_y    -c$HOME/Launchers/.tconk-config-time & # clock, update notification, etc
 conky -a $tmemory_a  -x $tmemory_x   -y $tmemory_y  -c$HOME/Launchers/.tconk-config-memory & # file system & ram usage, top processes by memory, disk io, etc
 conky -a $tnetdown_a -x $tnetdown_x  -y $tnetdown_y -c$HOME/Launchers/.tconk-config-netdown & # total download rate, download connections
 conky -a $tnetup_a   -x $tnetup_x    -y $tnetup_y   -c$HOME/Launchers/.tconk-config-netup & # total upload rate, upload connections
 conky -a $tcpu_a     -x $tcpu_x      -y $tcpu_y     -c$HOME/Launchers/.tconk-config-cpu & # uptime, top processes by CPU, GPU temp, etc
 # application monitors
 conky -a $tdeluge_a  -x $tdeluge_x   -y $tdeluge_y  -c$HOME/Launchers/.tconk-config-deluge & # currently downloading torrents, download/upload rate, ETA, etc
 conky -a $tmpd_a     -x $tmpd_x      -y $tmpd_y     -c$HOME/Launchers/.tconk-config-mpd & # currently MPD state, playing song, album art, progress, etc
fi

# give conky enough time to run scripts, if run in a terminal, before we exit.
 # all conky windows will redraw once the exit is issued, so they will initialize twice.
# if we don't do this and we select 'run in terminal' then conky windows that haven't finished processing
 # their initial scripts will close before they finish and not stay open. increase if when running from
 # a terminal, windows fail to load on time.
sleep 8
# finally, exit
exit


```

---

### Post by Grubbie on 2013-06-03
Thanks for that, HilmTye. That's quite an extensive script!

---

### Post by HiImTye on 2013-06-11
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
you're welcome! I really should post my updated conky setup. maybe in a couple of months when I'm no longer running it headless

---

