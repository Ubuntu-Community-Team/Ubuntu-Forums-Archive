---
title: "division in a bash script"
date: 2014-04-05
forum: Programming Talk
---

### Post by GrouchyGaijin on 2014-04-05
Hello Gurus,

I'm trying to write a bash script that will let me put in hours and minutes and convert that into a decimal.
Example: 3:35 into [COLOR=#000000][FONT=Verdana] 3.58

I am using M for the minutes.

The problem I am having is when I try to divide the result of M *60 by 3600.
I get 0 instead of [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]0.58
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
Could someone give me a clue on what I am doing wrong?

[/FONT][/COLOR][B][COLOR=#ff0000][FONT=Verdana]UPDATE
[/FONT][/COLOR][/B][COLOR=#000000][FONT=Verdana]
I found that I can get the decimal with:
[/FONT][/COLOR]```
echo "scale=2; $mul / 3600" | bc

```
[COLOR=#000000][FONT=Verdana]but I do not know how to set the resulting decimal as a variable so I can use it later on.
[/FONT][/COLOR]

---

### Post by Vaphell on 2014-04-05
capture it with $( ), just like any other output

```
$ dec=$( bc <<< "scale=2; 5440/3600" )
$ echo $dec
1.51
```

in pure bash it's not that hard either

```
$ IFS=: read h m <<< "1:31"
$ printf '%d.%02d\n' $h $((100*m/60))
1.51
$ printf **-v dec** '%d.%02d\n' $h $((100*m/60))
$ echo $dec
1.51
```
it always rounds down, no idea if it's a problem and it appears the bc does that too. It could be fixed with some additional math.


btw, why did you go as deep as seconds if the resolution you use is in minutes? hh:mm:ss is ok too?

```
$ IFS=: read h m s <<< "1:31:15"
$ printf '%d.%02d\n' $h $((100*(m*60+s)/3600))
1.52
```

I manage the remainder by hand and right off the bat i move from 0.xx to xx (multiplication by 100) which will prevent rounding down to 0.
If you want to use integer arithmetic to fake this kind of calculations, you always have to stack multiplication first, and do division at the end. Integer division truncates the reminder so you can't use it early, or your calc will be imprecise or outright useless. If you do 1/2*a*b*c you get 0 from 1/2, and then 0*a=0, 0*b=0, 0*c=0. a*b*c/2 is the correct way.

---

### Post by GrouchyGaijin on 2014-04-05
Thanks man,
Once again you have helped make life easier.
The monthly time sheets will go a tad quicker now - LOL
As to why I went as deep as seconds - it was a copy and paste thing.

---

### Post by Vaphell on 2014-04-05
just for kicks i whipped up a bash only script that calcs truncated and rounded version with dec precision of 1+
It's down to seconds but works just fine if you omit s.

```
#!/bin/bash

hr=$1
prec=${2:-2}
printf -v p "1%0${prec}d" 0

IFS=: read h m s <<< "$hr"
h=$(( 10#$h ))
m=$(( 10#$m ))
s=$(( 10#$s ))

mm=$((p*(m*60+s)/3600))
printf -v trunc "%d.%0${prec}d" $h $mm

hh=$(( h+(p*10*(m*60+s)/3600+5)/10/p ))
mm=$(( (p*10*(m*60+s)/3600+5)/10%p ))
printf -v round "%d.%0${prec}d" $hh $mm

printf '%s => %s / %s\n' "$hr" "$trunc" "$round"

```


```
$ for h in 04:{08..59..17}; do ./hr2frac.sh "$h" 1; done
04:08 => 4.1 / 4.1
04:25 => 4.4 / 4.4
04:42 => 4.7 / 4.7
04:59 => 4.9 / 5.0
$ for h in 04:{08..59..17}; do ./hr2frac.sh "$h" 2; done
04:08 => 4.13 / 4.13
04:25 => 4.41 / 4.42
04:42 => 4.70 / 4.70
04:59 => 4.98 / 4.98
$ for h in 04:{08..59..17}; do ./hr2frac.sh "$h" 3; done
04:08 => 4.133 / 4.133
04:25 => 4.416 / 4.417
04:42 => 4.700 / 4.700
04:59 => 4.983 / 4.983
$ for h in 04:{08..59..17}; do ./hr2frac.sh "$h" 4; done
04:08 => 4.1333 / 4.1333
04:25 => 4.4166 / 4.4167
04:42 => 4.7000 / 4.7000
04:59 => 4.9833 / 4.9833
```

---

### Post by GrouchyGaijin on 2014-04-05
Thanks man,
By the way I use your weather script on just about a daily basis.

---

### Post by Vaphell on 2014-04-05
:-) i thought about upgrading it few times, but i haven't been able to overcome the inertia of my laziness yet.

---

### Post by GrouchyGaijin on 2014-04-06
OK being never completely satisfied I started playing with the script and have one that almost works.
(or works most of the time, that is)

```

#!/bin/bash
echo "This script is for hours and wages. "
read -p "Enter the number of hours: " H
read -p "Enter the number of minutes: " M 
mul=$(($M * 60))
dec=$( bc <<< "scale=2; $mul/3600" )
echo $H hours $M minutes in decimal form is $H$dec
Time=$H$dec
Gross=$( bc <<< "$Time * 176.00" )
echo "The gross salary is: $Gross SEK"
Tax=$( bc <<< "$Gross * 0.30") 
Net=$( bc <<< "$Gross - $Tax")
echo "The net salary is: $Net SEK"


```

The above works as long as I do not put in an hour and zero minutes.
If I enter 1:00
I get an answer that has an extra zero.
That is 176.00 becomes 1760.00

Where is the mistake?

---

### Post by Vaphell on 2014-04-06
calculation spits out 0 and you get 10 instead of 1.0

```
echo $H hours $M minutes in decimal form is [COLOR="#FF0000"]$H$dec[/COLOR]
Time=[COLOR="#FF0000"]$H$dec[/COLOR]
```

instead of playing by hand with H and M separately

```
Time=$( bc <<< "scale=2; ($H*60+$M)/60" )
Time=$( bc <<< "scale=2; $H+$M/60" )

```

no idea how much of a difference it makes but you might be losing precision.

```
t=(H*60+M)/60
salary=t*hourly_rate
```
is not exactly the same as
```
salary=hourly_rate*(H*60+M)/60
```
if t step is lossy.

are 2 reads better than 1 supporting h:m format? and i'd parametrize hrly_rate and tax_rate :-)

PS. Hourly rate of 170SEK?! Holy balls batman! >_< (and i assume it's a janitor level wage ;-) )

---

### Post by GrouchyGaijin on 2014-04-06
Yeah Janitor's helper

Thanks man!
(Dude if you leave Poland, with your skills you could make a ton of money.)

---

