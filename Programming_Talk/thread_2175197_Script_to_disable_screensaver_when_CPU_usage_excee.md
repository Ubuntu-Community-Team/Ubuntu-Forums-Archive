---
title: "Script to disable screensaver when CPU usage exceeds a certain percentage ?"
date: 2013-09-18
forum: Programming Talk
---

### Post by vasa1 on 2013-09-18
I have this:
```
#!/usr/bin/env bash

sleep_period=7m #minutes

while true; do
  if [[ $(pidof mplayer | wc -w) -gt 0 ]]; then
    while [[ $(pidof mplayer | wc -w) -gt 0 ]]; do
      xdotool mousemove 0 100
      sleep ${sleep_period}
    done
  else
    sleep ${sleep_period}
  fi
done
```

It works for GNOME Mplayer but I'd like a more general solution.

---

### Post by Crusty Old Fart on 2013-09-18
> **vasa1 said:**
> ...It works for GNOME Mplayer but I'd like a more general solution.

There are several different ways you can capture your CPU usage.
This might help: [http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html](http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html)

---

### Post by pqwoerituytrueiwoq on 2013-09-18
mplayer has this feature built in
to enable it run this:
```
echo 'heartbeat-cmd="xscreensaver-command -deactivate"' >> ~/.mplayer/config
```
i use this for other players like adobe flash
```
#!/bin/bash
me="`dirname $0`/`basename $0`"
#echo $me
if [ "$1" == "--help" ];then
    echo -e "Usage:\n\t`basename $0` [CPU TIMER] | --debug | --help\n\tCPU is the cpu usage usage for flash times 10 to assume video is running\n\tTimer is the amount of time to wait before checking if a video player is running"
    exit
elif [ "$1" == "--debug" ];then
    cpu="20"
    delay="5"
else
    if [ -z "$1" ];then
        cpu="20"
    else
        cpu="$1"
    fi
    if [ -z "$2" ];then
        delay="55"
    else
        delay="$2"
    fi
    if [ "`pgrep -f $me | wc -l`" -gt "2" ]; then
        echo "Already running..."
        exit
    fi
fi
while [ 1 ]; do
#    clear
    chrome="`pgrep -lf chrome | grep ppapi | awk '{print $1}' | paste -sd ','`"
    flash="`pgrep -f flashplayer | paste -sd ','`"
#    echo "chrome=$chrome"
#    echo "flash=$flash"
    if [[ -n "$chrome" || -n "$flash" ]];then
        if [ -n "$chrome" ] && [ -n "$flash" ];then
            flash="$flash,$chrome"
        elif [ -n "$chrome" ];then
            flash="$chrome"
        fi
#        echo "Flash processes: $flash"
        # multiply by 10 to remove decimal in newer versions of top
        flash=`top -bn 1 -p "$flash" | grep $USER | head -1 | awk '{print $9*10}'`
        if [ "$1" == "--debug" ];then
            echo "Flash is using `calc $flash/10`% CPU. Threshold is `calc $cpu/10`%"
        fi
    else
#        echo "No flash running"
        flash="0"
    fi
    if [[ $flash -gt $cpu || -n "`pgrep -f parole`" ]]; then
        xscreensaver-command -deactivate > /dev/null
        if [ `xset -q | grep -ce 'DPMS is Enabled'` -eq 1 ];then
            xset -dpms
            xset dpms
        fi
        echo "Video or flash is running, no screensaver for you"
    fi
    sleep $delay
done
```

---

### Post by vasa1 on 2013-09-18
Thanks for the answers. After a while of no responses here, I cooked up something else, ran into trouble, and posted at unix.stackexchange.com: [Script to prevent screen blanking using &#8220;mouse move&#8221; doesn't work]("http://unix.stackexchange.com/q/91249/15760"). Based on answers there, what I'm using now looks like this:

```
#!/usr/bin/env bash

sleep_period=60s 

while true; do
  if [[ $(top -bn 1 | sed -nrs '8p' | awk '{ print int($9) }') -gt 5 ]]; then 
    while [[ $(top -bn 1 | sed -nrs '8p' | awk '{ print int($9) }') -gt 5 ]]; do
      xset -dpms; xset s off
      xset +dpms; xset s on
      sleep ${sleep_period}
    done
  else
    sleep ${sleep_period}
  fi
done

```
I know the sleep_period is short and the CPU% is low but I'll change those later. And no "mouse move".

---

### Post by Vaphell on 2013-09-19
isn't that if superficial? It's function is performed by the inner while either way
```
while true; do
  while top -bn 1 | awk 'NR==8 { exit !($9>5); }'; do
    xset -dpms; xset s off
    xset +dpms; xset s on
    sleep ${sleep_period}
  done
  sleep ${sleep_period}
done
```
should do roughly the same thing

---

### Post by vasa1 on 2013-09-19
> **Vaphell said:**
> isn't that if superficial? It's function is performed by the inner while either way
...
should do roughly the same thing
I'm just a humble newbie in all this :)

I'll give your script a try. Your previous advice has been very helpful!

---

### Post by Vaphell on 2013-09-19
another attempt, while loop inside while loop still stank ;-)
```
while true; do
  if top -bn 1 | awk 'NR==8 { exit !($9>5); }'; then
    xset -dpms; xset s off
    xset +dpms; xset s on
  fi
  sleep ${sleep_period}
done
```

---

### Post by vasa1 on 2013-09-19
> **vasa1 said:**
> 
I'll give your script a try. ...
I tried:
```
#!/usr/bin/env bash

sleep_period=5m 

while true; do
  while top -bn 1 | awk 'NR==8 { exit !($9>8); }'; do
    xset -dpms; xset s off
    xset +dpms; xset s on
    sleep ${sleep_period}
  done
  sleep $
done
```
but I get 
```
[11:02 AM] ~/bin $ vh.sh
sleep: invalid time interval ‘$’
Try 'sleep --help' for more information.
sleep: invalid time interval ‘$’
Try 'sleep --help' for more information.
sleep: invalid time interval ‘$’
Try 'sleep --help' for more information.
...

```

---

### Post by Vaphell on 2013-09-19
obviously i ate {sleep_period}
either way, try newer version without inner loop

---

### Post by vasa1 on 2013-09-19
> **Vaphell said:**
> another attempt, while loop inside while loop still stank ;-)
```
while true; do
  if top -bn 1 | awk 'NR==8 { exit !($9>5); }'; then
    xset -dpms; xset s off
    xset +dpms; xset s on
  fi
  sleep ${sleep_period}
done
```
No error in terminal so far :)

---

### Post by vasa1 on 2013-09-19
> **vasa1 said:**
> No error in terminal so far :)

This works as well:
```
#!/usr/bin/env bash

sleep_period=8m 

while true; do
  if top -bn 1 | awk 'NR==8 { exit !($9>8); }'; then
      xdotool key Shift
  fi
  sleep ${sleep_period}
done
```

---

### Post by vasa1 on 2013-09-20
> **Vaphell said:**
> another attempt, while loop inside while loop still stank ;-)
```
while true; do
  if top -bn 1 | awk 'NR==8 { exit !($9>5); }'; then
    xset -dpms; xset s off
    xset +dpms; xset s on
  fi
  sleep ${sleep_period}
done
```
@Vaphell, could you please clarify how  **[FONT=Courier New]exit !($9>5)[/FONT]** works? Specifically, if **[FONT=Courier New]$9[/FONT]** isn't a pure integer, isn't bash supposed to have trouble with numbers like **[FONT=Courier New]0.03[/FONT]** or **[FONT=Courier New]2.21[/FONT]**, etc? How come something like **[FONT=Courier New]exit !(int($9)>5)[/FONT]** isn't necessary?

---

### Post by Vaphell on 2013-09-20
but it's not bash, it's awk :)
```
if top -bn 1 | [COLOR="#0000CD"]awk 'NR==8 { exit !($9>5); }'[/COLOR]; then 
```
awk is a language too and it's much more powerful when it comes to math and has no trouble with floating point numbers. The whole expression in quotes is simply an inlined mini-program but you can write full blown awk scripts in separate files.

```
$ echo 12.3 | awk '{ print ($1>5); }'
1
$ echo 12.3 | awk '{ print ($1<5); }'
0
```

**$9>5** is a boolean expression that returns 0 for false or 1 for true


exit codes which is what selects the branch of *if then else* are the opposite, success/true is 0, failure/false is non-0

```
if <exit code 0>; then
   this will execute
else
  this won't
fi
if <exit code non-0>; then
  this won't execute
else 
  this will
fi
```

standard conditions in [ ] simply return 0/1 too
```
$ [ 0 = 1 ]; echo $?
1
$ [ 0 = 0 ]; echo $?
0
```
that's why you can plug a command into *if* directly and the if will work, in fact **[** is a command like any other ( /usr/bin/[ ).

if we negate **($9>5)** with **!** we get exit codes returned from awk that do the right thing. You could also write **exit ($9<=5)** (no negation) which would do the same.

---

### Post by vasa1 on 2013-09-20
Thank you for the elaborate explanation. I could see that the code was obviously working but didn't realize that **awk** handled numbers better. I've now got it in my Openbox session autostart.

---

