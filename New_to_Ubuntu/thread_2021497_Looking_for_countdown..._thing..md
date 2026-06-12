---
title: "Looking for countdown... thing."
date: 2012-07-09
forum: New to Ubuntu
---

### Post by HeartAttack on 2012-07-09
Allow me to elaborate.
My dad asked me whether there was a program that would show him, on his desktop if possible, just how long it is yet until April 2031, the month he may finally retire. Since this seems to me like a relatively simple program (I guess I could do it myself, if I knew the proper language) I am fairly certain it does exist somewhere, but as of now I was unable to find anything that would be of actual use.

---

### Post by AlbertJB on 2012-07-09
Could you try this screenlet? It's implemented in GTK 2.x and I see you use Ubuntu 10.04. I can't test it since I use Ubuntu 12.04 (GTK 3.X). I am also interested in this feature.

[http://gnome-look.org/content/show.php/Improved+Countdown+screenlet?content=140959](http://gnome-look.org/content/show.php/Improved+Countdown+screenlet?content=140959)


I've been searching in Google and I've seen that there're iphone ([http://www.timeanddate.com/countdown/create](http://www.timeanddate.com/countdown/create)) and android apps ([https://play.google.com/store/apps/details?id=smsr.com.cw](https://play.google.com/store/apps/details?id=smsr.com.cw)) to do that, but not an easy one for Ubuntu...

---

### Post by HeartAttack on 2012-07-09
Works for me. Though my dad does NOT use Lucid, I think he's on 11.04 right now. Well, can't hurt to try now, can it?

---

### Post by GreatDanton on 2012-07-09
No, you can always change it back to previous state. But I am pretty sure it will work.

Regards.

---

### Post by AlbertJB on 2012-07-09
It won't work in my case (Ubuntu 12.04) :(

What might I have done wrong?

---

### Post by stinkeye on 2012-07-09
You can use a script with conky to display a countdown.

Install conky and you may need to install libdate-manip-perl
```
sudo apt-get install conky-all libdate-manip-perl
```

Save this as **howlong.pl** in your home folder.
After saving, right click on the file
**Properties > Permissions**
and mark as executable.
```
#!/usr/bin/perl
#Script Name: howLong.pl
#Author: Nathan Handler <nhandler @ubuntu.com>
 
use strict;
use warnings;
use Date::Manip;
 
my $target=$ARGV[0] || "[COLOR="Red"]April 1, 2031[/COLOR]";
my $delta = DateCalc(ParseDate("now"),ParseDate($target),1);
 
$delta=~s/^[+-]//;
my($y,$m,$w,$d,$h,$min,$s) = split(/:/,$delta,7);

$y = sprintf("%02d", $y);
$m = sprintf("%02d", $m);
$w = sprintf("%02d", $w);
$d = sprintf("%02d", $d);
$h = sprintf("%02d", $h);
$min = sprintf("%02d", $min);
$s = sprintf("%02d", $s);
 
print $y . "y " if($y>0);
print $m . "m " if($m>0);
print $w . "w " if($w>0);
print $d . "d " if($d>0);
#print "$h:$min:$s" if($h>0||$min>0||$s>0);</nhandler>
```


Save this as **.conkyrc** in your home folder.(Include the preceding dot when saving.)
```
double_buffer yes
background no
no_buffers yes
draw_outline no
draw_shades no
update_interval 30
out_to_console no
out_to_stderr no

# Window Placement & Size
alignment br
own_window yes
own_window_type normal
own_window_transparent no
own_window_argb_visual yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour 000000

gap_x 0
gap_y 0
minimum_size 
maximum_width 

#Text Formatting
use_xft yes
xftfont Ubuntu Mono:size=13


TEXT
${pre_exec ~/howLong.pl}
```

To test, open a terminal and run
```
conky
```

Add to startup applications using
```
conky -p 10
```

---

### Post by GreatDanton on 2012-07-09
@Stinkeye what does this -p 10 in your attachments. Is this delay?

---

### Post by stinkeye on 2012-07-09
> **GreatDanton said:**
> @Stinkeye what does this -p 10 in your attachments. Is this delay?
Yesiree.
Delays the start of conky 10 secs so as it doesn't load before the window manager.

---

### Post by josephmills on 2012-07-09
**EDITING DONT USE YET**

if you would like here is a bash script 
```

#!/usr/bin/env bash 
##sanity check 
if 
[ "$#" -lt "2" ] ; then         
echo "Incorrect usage ! Example:"         
echo './countdown -d  "April 1, 2031 00:00"'         
echo 'or'         
echo './countdown -m  90'         
exit 1 
fi 
##setting up the varibles for 1
now=`date +%s` 
if [ "$1" = "-d" ] ; then         
until=`date -d "$2" +%s`         
sec_rem=`expr $until - $now`         
echo "-d"
## is the time allready done ?          
if [ $sec_rem -lt 1 ]; then                 
echo "$2 is already history !"         
fi fi 
if [ "$1" = "-m" ] ; then         
until=`expr 60 \* $2`         
until=`expr $until + $now`         
sec_rem=`expr $until - $now`         
echo "-m"         
if [ $sec_rem -lt 1 ]; then                 
echo "$2 is already history !"         
fi fi 
##start the loop 
while [ $sec_rem -gt 0 ]; do         
clear         
date         
let sec_rem=$sec_rem-1         
interval=$sec_rem         
seconds=`expr $interval % 60`         
interval=`expr $interval - $seconds`         
minutes=`expr $interval % 3600 / 60`         
interval=`expr $interval - $minutes`         
hours=`expr $interval % 86400 / 3600`         
interval=`expr $interval - $hours`         
days=`expr $interval % 86400000 / 86400`         
interval=`expr $interval - $hours`         
## Add the function to print to screen
function toscreen(){
echo "----------------------------"         
echo "I got me the Goal in"         
echo "----------------------------"         
echo "Days:    " $days         
echo "Hours:   " $hours         
echo "Minutes: " $minutes         
echo "Seconds: " $seconds         
sleep 1
}
toscreen
done


```

I will try to make gui for it.

---

### Post by HeartAttack on 2012-07-09
Uhm, yeah. Alright. For me it is solved, the screenlet worked for my dad, all is fine. So there's that. Though that conky script does look a hell of a lot more elegant a solution I must say. I may try that for a Wacken countdown. Bit more reasonable than 19 years if you ask me.

---

### Post by josephmills on 2012-07-09
ok here you go 

you can either download the debian file here 
[http://bazaar.launchpad.net/~josephjamesmills/+junk/countdownret/download/josephjamesmills%40gmail.com-20120709212800-quif8d5zi5szxy7b/countdownret_0.0.11_-20120709212716-k9egl27bkd7sm4qt-5/countdownret_0.0.1-1_all.deb](http://bazaar.launchpad.net/~josephjamesmills/+junk/countdownret/download/josephjamesmills%40gmail.com-20120709212800-quif8d5zi5szxy7b/countdownret_0.0.11_-20120709212716-k9egl27bkd7sm4qt-5/countdownret_0.0.1-1_all.deb)

Or you can add my repo 
```
sudo add-apt-repository ppa:josephjamesmills/beta
```
then 
```
sudo apt-get update
```
then 
```
sudo apt-get install countdownret
```

It will be in the menu

Hope this helps

The package is for Lucid

**edit**
I am going to play around with this add years ect so best to add repo and get automatic updates ;)

---

