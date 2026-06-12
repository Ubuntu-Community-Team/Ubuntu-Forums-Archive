---
title: "[bash] Current time to degrees for clock wallpaper"
date: 2009-11-08
forum: Programming Talk
---

### Post by relst-nl on 2009-11-08
I'm trying to make a script which transforms the current time into a clock image. 
I'm doing it with imagemagick and bash. What I already have is a script which makes the clock from out nothing:
[http://raymii.org/test/clock.sh](http://raymii.org/test/clock.sh)
(It looks like: [http://raymii.org/test/clock.png](http://raymii.org/test/clock.png) )
But now the time has to be shown with hands. 
What I was thinking is to call the script from a crontab every minute.
It then takes the current time with the date command, strips it so that the HHSS is left (with sed maybe). Then it makes a line with convert that is in the angle it should according to the current time(The Minute hand) and it does that also for the hour hand. Then it composites it all together. 

I have a center dot, and the hands should come out of it. In the script I'm using percentages because the plan is to make it work at 1280x1024 and 1920x1280. 

But the whole date to hand conversion part is to difficult for me. I totally do not know how to do that. 

My bash skills are limited, and what I have can probably be done better, so i'd love some tips and suggestions. Espicially for the time to hand part.

---

### Post by geirha on 2009-11-08
```
read hour minute < <(date "+%H %M")
```
That'll read in the current hour and minute into those two variables, in bash (not sh).

To calculate the coordinates for the lines, you'll need sine and cosine. Bash can't do such arithmetic, so you'll need an external program that can. Awk is one possibility.

```

awk "-vradius=100" "-vhour=$hour" 'BEGIN {printf "%.0f", radius*cos(3.14*(hour%12)/6)}'

```

As for your current code, use lowercase variable names unless you intend to export the variables. This helps avoid accidentally overwriting special shell variables or environment variables. 

Also:
```

RESOLUTION1="1280"
RESOLUTION2="1024"
KUT1="$RESOLUTION1 x $RESOLUTION2" 
RESOLUTION=`echo $KUT1 | sed 's/ //g'`

# Can be done with
resolution1="1280"
resolution2="1024"
resolution="${resolution1}x${resolution2}"

```

And:
```
let CLOCKSIZE1=$RESOLUTION1/4
```
is correct, but I find using the POSIX $(( )) or the bash (( )) prettier:
```

clocksize1=$((resolution1/4))
# or
((clocksize1=resolution1/4))

```

---

### Post by relst-nl on 2009-11-08
A friend of mine who is much better in maths then me said to me, convert the minutes to degrees, and then make an hand which rotates that amount of degrees. That was a good idea, so now I have this:

```
TIJD1=$(date +%M)

let TIJD=$TIJD1*6
```and for the hours:

```

UUR=$(date +%l)
UUR=`echo $UUR | sed 's/ //g'`
let UUR2=$UUR*30
echo TIJD 0
echo $TIJD1
echo TIJD 1
echo $UUR2
#Check if it is past a quater/half/three-quarter hour, if so, move the hour hand a little further. 
case $TIJD1 in
00 | 01 | 02 | 03 | 04 | 05 | 06 | 07 | 08 | 09 | 10 | 11 | 12 | 13 | 14 | 15) 
    let UUR2=$UUR2+0;;
16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 | 25 | 26 | 27 | 28 | 29 | 30)
    let UUR2=$UUR2+7;;
31 | 32 | 33 | 34 | 35 | 36 | 37 | 38 | 39 | 40 | 41 | 42 | 43 | 44 | 45)
    let UUR2=$UUR2+15;;
46 | 47 | 48 | 49 | 50 | 51 | 52 | 53 | 54 | 55 | 56 | 57 | 58 | 59)
    let UUR2=$UUR2+22;;
*)
echo TIME ERRORS;
esac
echo TIJD 2
echo $UUR2

```If I do not do that case thing the hour hand will jump from hour to hour and not incremental, that looks weird...

And then it does this with the arrow: ```
convert lijnm.png -matte \( +clone -background none -rotate $TIJD \)  -gravity center  -compose Src -composite  lijntrans.png
```and then it sticks it all together:
```
 composite lijntrans.png clock.png clock.png
```And I've changed the case to lower, and the removing of spaces also. 

Uploaded the new version: [http://raymii.org/test/clock.sh](http://raymii.org/test/clock.sh)

Thanks :)

---

