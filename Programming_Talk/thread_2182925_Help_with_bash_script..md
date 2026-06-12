---
title: "Help with bash script."
date: 2013-10-23
forum: Programming Talk
---

### Post by stinkeye on 2013-10-23
I have a simple bash script to capture the screen with avconv....
```
#!/bin/bash

NOW=$(date +"%Y-%m-%d-%H:%M:%S")

avconv -f x11grab -r 24 -s 1024x768 -i :0.0+0,0 -c:v libx264 -pix_fmt yuv420p -profile:v high -preset medium -crf 22 ~/Videos/screens/$NOW.mp4
notify-send -u critical -i /home/glen/Pictures/ScreenRecorder.png "Screen Recording" "Finished"
```
I also have a countdown timer script that writes to a **~/tmp/countdown** file 
every second to give the current countdown status in the form of HH:MM:SS
eg when finished file shows....
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **cat ~/tmp/countdown**
00:00:00
```

So what I want to do is send the exit command once **cat ~/tmp/countdown** = 00:00:00
I've had a go at creating some sort of while loop using **[ $timer != "00:00:00" ]** but
I'm just a hobbyist bash scripter and can't get anything to work.
The basic command I want is to start the timer and run the screen recording but with a timer condition...
```
/home/glen/scripts/countdown.sh 00:00:25 & gnome-terminal --window-with-profile=avconv-Term --hide-menubar --geometry 106x12+365-16 -e /home/glen/scripts/screenrecord.sh"
```

I know there is an option for avconv for duration.....**-timelimit** ,but as the terminal output says
> Estimating duration from bitrate, this may be inaccurate
...-timelimit 25 gives me varying times of around 10 to 15 seconds and the saved video is unplayable.

So I think I need to exit the script with the equivalent of pressing ctl+c with the terminal focused.

---

### Post by Vaphell on 2013-10-23
so you want the countdown script to run out, exit and then recording should start?
If so, you need double & there (&&) which means run the latter if the former ended with success, single & means pushing command it follows to background and running next one in parallel, it's like an asynchronous ; 
You don't need tmp file, if you properly queue these scripts the second one will run only after the first exits.

---

### Post by stinkeye on 2013-10-23
> **Vaphell said:**
> so you want the countdown script to run out, exit and then recording should start?
If so, you need double & there (&&) which means run the latter if the former ended with success, single & means pushing command it follows to background and running next one in parallel, it's like an asynchronous ; 
You don't need tmp file, if you properly queue these scripts the second one will run only after the first exits.

Ah it's ok, thanks.

I can start both avconv and a 25 second countdown with....
```
#!/bin/bash

#NOW=$(date +"%b-%d-%y-%H:%M")
NOW=$(date +"%Y-%m-%d-%H:%M:%S")

gnome-terminal --window-with-profile=avconv-Term --hide-menubar --geometry 106x12+365-16 -x avconv -f x11grab -r 24 -s 1024x768 -i :0.0+0,0 -c:v libx264 -pix_fmt yuv420p -profile:v high -preset medium -crf 22 ~/Videos/screens/$NOW.mp4 & 
/home/glen/scripts/countdown.sh 00:00:25 
```

I was using wmctrl and xdotool to send ctr+c to the terminal when the countdown reached 00:00:00, because I thought doing anything else would wreck the recording.
Turns out I can just use **killall avconv**

```
#!/bin/bash
#
# countdown script 
# usage example: countdown.sh 00:10:00
# starts a 10min countdown and write the status to $COUNTDOWNFILE 
# (where conky is listening and displays the content in this setup)
#
# timer for teh perfect pizza
# 

  IFS=:
  OUTPUTFILE=$HOME/tmp/countdown
  COUNTDOWNSOUND=$HOME/Sounds/bell.wav
  COUNTDOWNSOUND2=$HOME/Sounds/complete.mp3
  
  time=$1
  if [ -z "$1" ]; then
    time=$(zenity --entry --text "How long? HH:MM:SS" --entry-text "00:00:00" --title "zeh countdowwn");
  fi

 
 
  if [ -n "$time" ] && [ "$time" != "00:00:00" ]; then
    set -- $time
    secs=$(( ${1#0} * 3600 + ${2#0} * 60 + ${3#0} ))
    while [ $secs -gt 0 ]
    do
      sleep 1 &
      printf "%02d:%02d:%02d\n" $((secs/3600)) $(( (secs/60)%60)) $((secs%60)) > $OUTPUTFILE
      secs=$(( $secs - 1 ))
      wait
    done
    echo "00:00:00" > $OUTPUTFILE

## Turn off screen record if running ##
	if pgrep avconv; then 
		play -q $COUNTDOWNSOUND2 &
		#wmctrl -a avconv-Term && sleep 1 && xdotool key ctrl+c
		[COLOR="#FF8C00"]killall avconv[/COLOR]
	else 
		play -q $COUNTDOWNSOUND 
	fi

    #notify-send -u critical -i ~/Pictures/Bell.png "Screen Recording" "Finished" &
    
  rm $OUTPUTFILE  
  echo
  fi
```

This all works but what I was looking for was a command to do the equivalent of ctrl+c in a script.

---

### Post by Lars Noodén on 2013-10-23
> **stinkeye said:**
> This all works but what I was looking for was a command to do the equivalent of ctrl+c in a script.

ctrl-c is [SIGINT](http://manpages.ubuntu.com/manpages/raring/en/man7/signal.7.html) or #2.  So any of the kill utilities can send SIGINT to avconv or your script.  In addition to [killall](http://manpages.ubuntu.com/manpages/raring/en/man1/killall.1.html) another program which can kill by name or pattern is [pkill](http://manpages.ubuntu.com/manpages/raring/en/man1/pkill.1.html).  

```
pkill --signal SIGINT -x avconv

```

Sometimes different programs trap certain signals and do something special instead of quitting.  One of the common ones for daemons is for SIGHUP to initiate a reload of the configuration file.

---

### Post by stinkeye on 2013-10-23
> **Lars Noodén said:**
> ctrl-c is [SIGINT](http://manpages.ubuntu.com/manpages/raring/en/man7/signal.7.html) or #2.  So any of the kill utilities can send SIGINT to avconv or your script.  In addition to [killall](http://manpages.ubuntu.com/manpages/raring/en/man1/killall.1.html) another program which can kill by name or pattern is [pkill](http://manpages.ubuntu.com/manpages/raring/en/man1/pkill.1.html).  

```
pkill --signal SIGINT -x avconv

```

Sometimes different programs trap certain signals and do something special instead of quitting.  One of the common ones for daemons is for SIGHUP to initial a reload of the configuration file.

Thanks Lars Noodén, just my amateur knowledge where I thought running kill  was the same as closing the 
terminal window.
The killalll command works fine for this script.

PS This is all copy and paste stuff so don't get any idea I actually know what I'm doing. :confused: :P

---

