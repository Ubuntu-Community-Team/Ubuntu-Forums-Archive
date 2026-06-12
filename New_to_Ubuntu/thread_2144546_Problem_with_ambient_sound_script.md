---
title: "Problem with ambient sound script"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by Zukaro on 2013-05-12
This script is called by a crontab every 30 minutes to play sound (the sound files are a little longer than 30 minutes long, which is why if mplayer is running the script waits one minute then calls itself again until it plays).  Everything seems to work perfectly, except around 8am where no sounds will play at all even if I call the script manually.  I'm not sure what the problem is, everything looks functional to me and I see no reason that at 8am it wouldn't work yet at 10am it does.

During the day the script plays a different sound than at night.

```
#!/bin/bash
DAY="/home/zukaro/Sounds/Day/Day.ogg"
NIGHT="/home/zukaro/Sounds/Night/Night.ogg"
TIME="$(date +%H)"
AM="6"
PM="20"

if [[ "$TIME" -le "$PM" ]] && [[ "$TIME" -ge "$AM" ]];
        then
                SELECTED="$DAY"
                        else
                                if [[ "$TIME" -ge "$PM" ]] || [[ "$TIME" -le "$AM" ]];
                                        then
                                                SELECTED="$NIGHT"
                                        fi
        fi

if ps aux | grep "[m]player" > /dev/null
        then
                sleep 60
                /home/zukaro/Scripts/nature.sh
                        else
                                mplayer $SELECTED
        fi
exit

```

---

### Post by Impavidus on 2013-05-13
I can't see why this script wouldn't work at 8 if it works at 9, but I do see there are a few problems with it.

First the small things, that shouldn't effect its usability. The second if statement (to select the night sound) is not needed. This if statement will only be tested if the test for the day sound already returned false and will therefore always return true. The grep with a redirect to /dev/null can be replaced by **grep -q**. Terminal output of mplayer should be suppressed too.

Next the bigger problem: the script will continue running until the sound player terminates after slightly more than 30 minutes. If it's started whilst the sound is still running, the script starts new instances of itself every minute until the sound has terminated, all of them running until the next run of the sound player has terminated. When after 30 minutes cron starts a new instance of the script, these instances are added to the list, creating a longer series of scripts corresponding to the ever longer delay between cron starting the script and the previous run of the sound player finishing. In other words, this script, in combination with cron starting it slightly more frequently than the inverse of the time the sound plays, is a very slow kind of [fork bomb]("http://en.wikipedia.org/wiki/Fork_bomb"). Take the duration of the sound minus 30 minutes, rounded up to the whole minute and that's the number of processes accumulating every 30 minutes. If the sound actually plays for 35 minutes, the fork bomb will kill your system after 4 months.

I would implement the system differently. You can make an infinite loop that tests for the time of day, runs the sound player, waits for it to return and then runs the test again. Start the loop at login. No cron needed. This also eliminates the delay, currently up to one minute, between the sound finishing and the new sound starting.

---

### Post by Zukaro on 2013-05-13
Okay; thanks.  This is what I came up with (it's still not perfect however).  Although this script will restart itself if mplayer is killed, meaning that when I try to reboot my computer (or run my other script which needs to kill mplayer) mplayer will imediatly restart.  Mplayer imediatly restarting causes issues when rebooting the computer (if I need to reboot) as in, it wont.

I do want mplayer to imediatly restart after it's finished playing the sound file but I want it to stop if I send the kill command.

I'm not sure how to get it to do that (pretty new to bash scripting :V).
I wasn't able to figure out how to tell if mplayer had finished or not but I figure that the way I made this would do that anyways, as the loop wont be completed until mplayer has finished running.  I'm not sure how to keep it from running again when I need it to stop running however.


```
#!/bin/bash
DAY="/home/zukaro/Sounds/Day/Day.ogg"
NIGHT="/home/zukaro/Sounds/Night/Night.ogg"
TIME="$(date +%H)"
AM="6"
PM="20"

while true;
do

if [[ "$TIME" -ge "$PM" ]] || [[ "$TIME" -le "$AM" ]];
        then
                SELECTED="$NIGHT"
                        else
                                SELECTED="$DAY"
        fi
mplayer $SELECTED
done
```

---

### Post by Impavidus on 2013-05-13
A few suggestions:
You can put a delay between starting the script and starting the sound, by using sleep before the entering the loop. You could even make that delay dependent on a command line option, so that at reboot it takes a minute before the player starts, but when manually restarting it starts immediately.
Instead of killing mplayer you can kill the script. I think that should terminate mplayer as well, without automatically restarting. You could also look at the return value of mplayer. Maybe it returns >0 when it is killed and 0 when it normally terminates. You could use that difference to determine whether the script should restart mplayer or terminate itself.

---

