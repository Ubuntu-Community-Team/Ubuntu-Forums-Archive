---
title: "How to program a count down and timer stopwatch in bash script?"
date: 2010-08-24
forum: Programming Talk
---

### Post by honeybear on 2010-08-24
Hello,

For cooking I would need a console countdown and also a stopwatch.

How can we make that?

---

### Post by Neezer on 2010-08-24
> **honeybear said:**
> Hello,

For cooking I would need a console countdown and also a stopwatch.

How can we make that?

I'm not on my ubuntu laptop right now...I'm at work. But I would look in synaptic. This sounds like it is very common and already around. I looked up alarm clock a few days ago and got one...I seem to recall that there was a "timer" option in there as well.

Before going through the trouble of writing a script, make sure the problem hasn't already been solved. 

Unless the exercise is to write a script just for that in order to practice....in which case, asking and getting the answer isn't going to help you learn anymore than google....

hope that helps and good luck.

---

### Post by DaithiF on 2010-08-24
toy bash alias:
```
alias stopwatch='since=$(date +%s);watch -tn 1 eval "echo \$((\$(date +%s) - $since))"'

```
ctrl-c to exit

---

### Post by honeybear on 2010-08-24
here it is, thanks

```
printf "Countdown, how much seconds :> "
read seconds
since=$(date +%s);watch -tn 1 eval "echo \$(($seconds-\$(date +%s)+$since))"
```

---

### Post by juancarlospaco on 2010-08-24
sleep ?

---

### Post by honeybear on 2010-08-25
> **juancarlospaco said:**
> sleep ?

```
while  ; done
``` could be useful

---

### Post by honeybear on 2010-08-25
> **honeybear said:**
> here it is, thanks

```
printf "Countdown, how much seconds :> "
read seconds
since=$(date +%s);watch -tn 1 eval "echo \$(($seconds-\$(date +%s)+$since))"
```

the problem is that this script does not stop when reached zero value

---

### Post by honeybear on 2010-09-07
I still have to finish it when it comes to 0 in countdown ... it is not so easy man :'(

---

### Post by DaithiF on 2010-09-07
> **honeybear said:**
> I still have to finish it when it comes to 0 in countdown ... it is not so easy man :'(

heres a countdown function for your bashrc:
```
function countdown() {
    [[ -z $1 ]] && seconds=60 || seconds=$1
    since=$(date +%s)
    remaining=$seconds
    while (( remaining >= 0 ))
    do 
        printf "\r%-10d" $remaining
        sleep 0.5
        remaining=$(( seconds - $(date +%s) + since ))
    done
}

```

---

### Post by geirha on 2010-09-07
I came up with a similar approach, but using the special SECONDS variable instead of date.
```

countdown () 
{ 
    if (($# != 1)) || [[ $1 = *[![:digit:]]* ]]; then
        echo "Usage: countdown seconds";
        return;
    fi;
    local t=$1 remaining=$1;
    SECONDS=0;
    while sleep .2; do
        printf '\r%3d seconds remaining' "$remaining";
        if (( (remaining=t-SECONDS) <= 0 )); then
            printf '\r%3d seconds remaining\n' 0;
            paplay /usr/share/sounds/ubuntu/stereo/phone-outgoing-busy.ogg;
            break;
        fi;
    done
}

```

---

### Post by brent7890 on 2011-06-08
It doesn't have to be this complicated at all guys, I know this is past the date of the original poster, but seriously, it's this easy:

timer=60
until [ "$timer" = 0 ]
do
clear
echo "$timer"
timer=`expr $timer - 1`
sleep 1
done
THEN ENTER AFTER WHATEVER COMMANDS

---

### Post by DaithiF on 2011-06-09
> **brent7890 said:**
> It doesn't have to be this complicated at all guys, I know this is past the date of the original poster, but seriously, it's this easy:

Hi, the reason for the more complicated approaches above was to make them slightly more accurate.  doing stuff and sleeping for 1 second  each time x 60 is going to take longer than 60 seconds.  quick test of your script on my system -- 61.5 seconds for a 60second countdown.  Over 120 seconds it took 122.7.  Probably not a big deal, but don't blame us if you burn the soup! :)

---

