---
title: "Zenity and Bash, need help with loop"
date: 2008-10-29
forum: Programming Talk
---

### Post by starcannon on 2008-10-29
Hi everyone, I'm still working on my little script. I discovered Zenity, and am trying to control the message:bubble, I can not figure out how to write a loop that does not continuously create the same bubble over and over and over...

I know enough to understand that its trapped inside the if/then loop, so how do I get it out?

My code so far looks like this:
```

#!/bin/bash

exec 3> >(zenity --notification --listen --window-icon="$HOME/.icons/wow.png")
function bubble_launch
{
echo "message:World of Warcraft Launcher is running." >&3
}
function tooltip_launch
{
echo "tooltip:World of Warcraft Launcher is running." >&3
}

while true
do

if ps aux | egrep "Launcher.exe" | grep -v -q grep
then
    tooltip_launch
    bubble_launch
fi
done

```

---

### Post by starcannon on 2008-10-29
Posting my solution by way of code, maybe it will help someone eventually.
```

#!/bin/bash

bub=0

exec 3> >(zenity --notification --listen --window-icon="$HOME/.icons/wow.png")
function bubble_launch
{
bub=1
echo "message:World of Warcraft Launcher is running." >&3
}
function tooltip_launch
{
echo "tooltip:World of Warcraft Launcher is running." >&3
}

while true
do

if ps aux | egrep "Launcher.exe" | grep -v -q grep;
then
    tooltip_launch
    if [ "$bub" == 0 ];
        then
        bubble_launch
    fi
fi
done

```

---

### Post by starcannon on 2008-10-29
Okay, after messing around with my script for awhile, I find that it is extremely inefficient; that said, I am now in need of a bash mentor, or anyone who can give me some pointers on some do's and don'ts, how to discover more efficient ways of bash scripting, etc...

I will likely move on to python at some point, but would like to at least get a bit of a grip on bash first.

My latest code is causing huge cpu usage (eck! not good!), has a nasty memory leak, and when trying to use it to control metacity and compiz can do some funky things, like creating many instances of compiz and compiz.real.

Okay, thats the stuff I can tell you about with my newbie eys, please show me the err of my ways.

Heres the code:
```

#!/bin/bash

#This script monitors a game running under cedega/wine, in this case World of Warcraft, 
#the goal would be to have this script run metacity when Launcher.exe is running, and to 
#load compiz when WoW.exe is no longer running.

# Environmental Variables
bubl=0
bubg=0
bubn=0
launcher=0
game=0

exec 3> >(zenity --notification --listen --window-icon="$HOME/.cedega/World of Warcraft/icons/World of Warcraft.png")

# Functions
function bubble_null
{
bubn=1
echo "message:No World of Warcraft processes running." >&3
}

function tooltip_null
{
echo "tooltip:No World of Warcraft processes running." >&3
}

function bubble_launch
{
bubl=1
echo "message:World of Warcraft Launcher is running." >&3
}

function tooltip_launch
{
echo "tooltip:World of Warcraft Launcher is running." >&3
}

function bubble_game
{
bubg=1
echo "message:World of Warcraft Game is running." >&3
}

function tooltip_game
{
echo "tooltip:World of Warcraft Game is running." >&3
}

function launcher_check
{
if ps aux | egrep "Launcher.exe" | grep -v -q grep;
then
launcher=1
else
launcher=0
fi
}

function game_check
{
if ps aux | egrep "WoW.exe" | grep -v -q grep;
then
#exec 3> >(metacity --replace)
game=1
else
game=0
#exec 3> >(compiz --replace)
fi
}

# Main
while true
do

launcher_check
game_check
if [ "$launcher" == 1 ];
then
    tooltip_launch
    if [ "$bubl" == 0 ];
        then
        bubble_launch
bubg=0
bubn=0
    fi
elif [ "$game" == 1 ];
then
    tooltip_game
    if [ "$bubg" == 0 ];
        then
        bubble_game
bubl=0
bubn=0
    fi
else
    if [ "$launcher" == 0 ] & [ "$game" == 0 ]
    then
        tooltip_null
        if [ "$bubn" == 0 ];
            then
            bubble_null
bubl=0
bubg=0
        fi
    fi
fi
done

```

---

### Post by ghostdog74 on 2008-10-29
I don't know what you are doing, anyway, if there's absolutely not necessary for zenity, then remove it. Start with pure command line. Also, if you don't want to loop forever, then don't forget to break out of your while loop using break keyword.

---

### Post by starcannon on 2008-10-29
Ghostdog74, thanks for the reply; I have appended the goal of the script in a comment line in the scripts codebox above(i'll include it in this post as well). I would like to find a way to monitor the Launcher.exe and WoW.exe processes without being stuck in the while/do loop. I'm using Zenity to put a wee icon in the system tray to give feedback of what the script is doing. This is more for educational experience than to be any sort of useful tool.
```

#This script monitors a game running under cedega/wine, in this case World of Warcraft, 
#the goal would be to have this script run metacity when Launcher.exe is running, and to 
#load compiz when WoW.exe is no longer running.

```

---

### Post by ghostdog74 on 2008-10-29
if you don't want to use a loop, use a cron job.

---

### Post by geirha on 2008-10-29
You could make a wrapper script that checks every ten seconds if wow is running. Launcher.exe will go into the background and start Wow.exe to run the game, so checking if Wow.exe is running is one way to go. However, if there are updates, it will launch the updater instead so you need to handle those as well. They are all executables inside the same directory, so greping for that directory may be an option. If you've installed it do the default location, that directory would be "World of Warcraft".

```
#!/bin/sh

# Switch to metacity
metacity --replace &

# Run the launcher
WINEPREFIX="$HOME/.wine" wine "C:\\Program Files\\World of Warcraft\\Launcher.exe"

# Wait until no processes match "World of Warcraft"
while ps -ef | grep -q "[W]orld of Warcraft"; do sleep 10; done

# Switch back to compiz
compiz --replace &


```

---

### Post by starcannon on 2008-10-29
@[ghostdog74]("http://ubuntuforums.org/member.php?u=162413")
I've never used cron before, what I've read about it so far, it sounds like it runs jobs on a schedule.

So, can I have a cron job that is constantly watching to see if a process name, say "wineserver" is running?

The trick, and I may be asking to much, is to have realtime monitoring of a process so that as soon as the process exists an action can be taken, all that while not making the cpu run wild...

@[geirha]("http://ubuntuforums.org/member.php?u=243323")
Wow, thanks for the code snippet; it looks similar to what I want; I'll play with that, and get back to you.

---

### Post by unutbu on 2008-10-29
pgrep will return the process ID of wineserver if it is running. It returns an empty string if the process isn't running.

```
pgrep wineserver
```

For example:

```
#!/bin/sh 
retval=$(pgrep wineserver)
if [ -z $retval ]; then
    echo "wineserver is not running";
else
    echo "wineserver is running";
fi
```

---

### Post by starcannon on 2008-10-29
@[unutbu]("http://ubuntuforums.org/member.php?u=518895")

I actually just read about pgrep and was getting ready to write a little trial script. Used yours instead, btw don't forget the quotes around your strings in your if statements ;)

I'm amazed at how fast, and lite it is. Low memory footprint, low cpu usage, and thats while just letting it rapid fire in a while true/do loop.

Excellent thanks again!

I'll keep hammering at this, if I get something I really like I'll be sure to bang a drum!

I've already run through some noob tutes for python, and am seeing that it has a steeper learning curve, but pays out in dividends if I forge on.

---

