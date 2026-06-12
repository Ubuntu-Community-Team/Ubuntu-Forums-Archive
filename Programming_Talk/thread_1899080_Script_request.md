---
title: "Script request"
date: 2011-12-22
forum: Programming Talk
---

### Post by tiger63 on 2011-12-22
I'd like a script that I could start at boot that will automatically start 2 particular conkys whenever I start my music player and shut down these same 2 conkys whenever I shut down my music player.  I have virtually zero scripting knowledge.  

I'm running Xubuntu 11.10, though I somehow doubt that matters for this.

I hope this is the right section to request such a script.

---

### Post by Vaphell on 2011-12-22
care to describe how you run those 2 conkys? i have it roughly working but could use some details to nail things down.

---

### Post by tiger63 on 2011-12-22
Well, I'm not sure what you're asking.  Right now, I don't run them...I've only tested them.  They are basically rc files that each call templates, each of which calls a different python script, one retrieves song/artist/album info, the other retrieves album cover art and displays it.  I have them in separate conkys because I want to do the bg's for each in completely different ways.  Would you like to see the files?

BTW, the music player I'm using is Deadbeef, if that makes a difference.

---

### Post by Vaphell on 2011-12-22
I wrote a script that runs stuff when a given app is present in the list of processes and kills that stuff when that app disappears from the list. The only missing part is the stuff itself.
I am asking what are the exact commands you use to run/test these conky configs. My conky works with the default config but I would like to know how to achieve more advanced setup like running 2 configs at once or whatever so I can incorporate it into my script.

edit: ok, i figured it out

```
#!/bin/bash

cfg1=$HOME/cfg1
cfg2=$HOME/cfg2
player=audacious2
interval=3

while true
do
  if(( $( ps u -C $player | wc -l ) > 1 ))
  then
    echo $player is running
    if(( $( ps u -C conky | wc -l ) == 1 ))
    then
      echo starting conky
      conky -c "$cfg1" &
      conky -c "$cfg2" &
    else
      echo conky running already
    fi
  else
    if(( $( ps u -C conky | wc -l ) > 1 ))
    then
      echo $player is not running, killing conky
      killall conky
    else
      echo $player is not running
    fi
  fi
  sleep $interval
done
```

modify variables at the top to suit your needs. Half the script are echo commands so it's easy to test what happens when the player appears/disappears

---

### Post by tiger63 on 2011-12-23
Hey Vaphell,

Thanks a ton for taking the time to work on this.  The script works as advertised, however, there is a problem.

I should have mentioned that I want to run 3 conkys in total and that I only want the 2 specific conkys called by the script to be killed when I shut down the music player.  As it is now, this script shuts down all my conkys.

I know, my fault for not mentioning that earlier.  Is there any way to achieve this?  I call the main conky (conkymainrc) from a script at startup and want it to run indefinitely.  Then I'd like the other conkys (conkydbrc and conkydb1rc) to be called with the startup of deadbeef and dismissed with the shutdown of deadbeef.  I imagine it would be quite a bit more complicated...like getting the PID's of the two specific conkys and only killing those (but again, you'd know more about this than I).

Again, I'm sorry I wasn't clearer.

---

### Post by Vaphell on 2011-12-23
```
#!/bin/bash

cfg[0]=$HOME/cfg1
cfg[1]=$HOME/cfg2
player=audacious2
interval=3

pid=()

echo "conky configs to run: ${#cfg[@]}"
for c in ${cfg[@]}
do
  echo $c
done
echo -------------------------

while true
do
  if (( $( ps u -C $player | wc -l ) > 1 ))
  then
    echo $player is running
    if (( ${#pid[@]} == 0 ))
    then
      echo "starting conky"
      for(( i=0; i<${#cfg[@]}; i++ ))
      do
        conky -c "${cfg[i]}" &
        pid[$i]=$!
        echo "cfg #$((i+1)): ${cfg[i]} (${pid[i]})"
      done
    else
      echo "conky running already"
    fi
  else
    if(( ${#pid[@]} > 0 ))
    then
      echo "$player is not running, killing conky (${pid[@]})"
      for p in ${pid[@]}
      do
        kill $p
      done
      pid=()
    else
      echo "$player is not running"
    fi
  fi
  sleep $interval
done
```
i decided to use an array which means you are not limited to a fixed number of cfg files. Adding more cfg[*i*]=... will expand the list.

---

### Post by tiger63 on 2011-12-23
Brilliant, Vaphell!  Thanks a ton!

---

### Post by tiger63 on 2011-12-24
Vaphell,

Thought you'd like to see the fruits of your labor ;)

The top left conky is ever present; the one below it and the album art at top right appear and disappear with the start and shutdown of Deadbeef :)

Again, many thanks!

[[IMG]http://img3.imageshack.us/img3/9427/screenshot1224201112313.png[/IMG]](http://imageshack.us/photo/my-images/3/screenshot1224201112313.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by Vaphell on 2011-12-24
nifty :)

---

