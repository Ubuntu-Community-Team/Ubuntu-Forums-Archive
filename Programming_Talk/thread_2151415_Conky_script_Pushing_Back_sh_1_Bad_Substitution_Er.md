---
title: "Conky script Pushing Back sh: 1: Bad Substitution Error"
date: 2013-06-04
forum: Programming Talk
---

### Post by Myst1234 on 2013-06-04
Hello everyone,

I've been trying to build a conky for a few days now, and after passing my first few hurdles I am stuck, and have not been able to find some documentation about this, nor a thread for my issue.

when I try to run my conky from the terminal I get a sh: 1: Bad Substitution message. Last night i tried revamping my conky to run with accuweather because I learned that conkyForecast is now a monthly paying subscription, so perhaps that is the issue? Not sure.

Here is my conkyrc

 ```

background no
update_interval 1
total_run_times 0
own_window yes
own_window_transparent yes
own_window_class Conky
own_window_hints undecorate,sticky,skip_pager,skip_taskbar,below
double_buffer yes
no_buffers yes
text_buffer_size 2048
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
use_spacer none
minimum_size 1000 0
alignment top_left
gap_x 12
gap_y 12
uppercase no
use_xft yes
xftfont DejaVu Sans:size=12
xftalpha 0.8
default_color 000

TEXT
${voffset 400}${font DejaVu Sans:size=24}${time %A}, ${time %d} ${time %B} ${time %Y}${font}
${battery_bar 8,720 BAT0}
${voffset -8}${fs_bar 8,720 /}
${voffset -8}${goto 400}${cpubar 8,310 cpu}
${voffset -8}${goto 400}${font saxMono:size=9}${top pid 1}${font DejaVu Sans:size=8}${voffset -1} ${top name 1}${voffset 1}${goto 660}${font saxMono:size=9}${top cpu 1}
${goto 400}${font saxMono:size=9}${top pid 2}${font DejaVu Sans:size=8}${voffset -1} ${top name 2}${voffset 1}${goto 650}${font saxMono:size=9}${top cpu 2}
${goto 400}${font saxMono:size=9}${top pid 3}${font DejaVu Sans:size=8}${voffset -1} ${top name 3}${voffset 1}${goto 640}${font saxMono:size=9}${top cpu 3}
${goto 400}${font saxMono:size=9}${top pid 4}${font DejaVu Sans:size=8}${voffset -1} ${top name 4}${voffset 1}${goto 620}${font saxMono:size=9}${top cpu 4}
${goto 400}${membar 8, 260}
${goto 400}${font saxMono:size=9}${top_mem pid 1}${font DejaVu Sans:size=8}${voffset -1} ${top_mem name 1}${voffset 1}${goto 620}${font saxMono:size=9}${top_mem mem 1}
${goto 400}${font saxMono:size=9}${top_mem pid 2}${font DejaVu Sans:size=8}${voffset -1} ${top_mem name 2}${voffset 1}${goto 630}${font saxMono:size=9}${top_mem mem 2}
${goto 400}${font saxMono:size=9}${top_mem pid 3}${font DejaVu Sans:size=8}${voffset -1} ${top_mem name 3}${voffset 1}${goto 640}${font saxMono:size=9}${top_mem mem 3}
${goto 400}${font saxMono:size=9}${top_mem pid 4}${font DejaVu Sans:size=8}${voffset -1} ${top_mem name 4}${voffset 1}${goto 650}${font saxMono:size=9}${top_mem mem 4}${font}
${voffset -90}${font route3:size=160}${time %l}${font route3:size=100}${voffset -80}${goto 230}${time %M}${font}
${voffset -500}${execpi 360 ${color 48bcff}CHICAGO WEATHER${hr 2}$color${execi 600 bash $Home/1d_accuweather_rss/1d}
${font conkyweather:size=30}${execpi 600  sed -n '2p' $Home/1d_accuweather_rss/weather}${font}${goto 75}${voffset -25}${execpi 600 sed -n '1p' $Home/1d_accuweather_rss/weather|cut -c1-20}
${goto 75}${execpi 600 sed -n '1p' $Home/1d_accuweather_rss/weather|cut -c21-40}
${goto 75}${execpi 600 sed -n '1p' $Home/1d_accuweather_rss/weather|cut -c41-60}

${execi 600  sed -n '3p' $Home/1d_accuweather_rss/weather}
${font conkyweather:size=30}${execpi 600  sed -n '5p' $HOME/1d_accuweather_rss/weather}${font}${goto 75}${voffset -25}${execpi 600 sed -n '4p' $Home/1d_accuweather_rss/weather|cut -c1-20}
${goto 75}${execpi 600 sed -n '4p' $Home/1d_accuweather_rss/weather|cut -c21-40}
${goto 75}${execpi 600 sed -n '4p' $Home/1d_accuweather_rss/weather|cut -c41-60}

${execi 600  sed -n '6p' $Home/1d_accuweather_rss/weather}
${font conkyweather:size=30}${execpi 600  sed -n '8p' $Home/1d_accuweather_rss/weather}${font}${goto 75}${voffset -25}${execpi 600 sed -n '4p' $Home/1d_accuweather_rss/weather|cut -c1-20}
${goto 75}${execpi 600 sed -n '7p' $Home/1d_accuweather_rss/weather|cut -c21-40}
 ${goto 75}${execpi 600 sed -n '7p' $Home/1d_accuweather_rss/weather|cut -c41-60}
```

this is my 1d accuweather script

 ```
#!/bin/bash

#function: test_image
test_image () {
    case $1 in
     1|01)
       echo a
     ;;
     2|02)
       echo b
     ;;
     3|03)
       echo c
     ;;
     4|04)
       echo c
     ;;
     5|05)
       echo c
     ;;
     6|06)
       echo d
     ;;
     7|07)
       echo e
     ;;
     8|08)
       echo e
     ;;
     11)
       echo 0
     ;;
     12)
       echo h
     ;;
     13|14)
       echo g
     ;;
     15)
       echo l
     ;;
     16|17)
       echo k
     ;;
     18|26)
       echo i
     ;;
     19)
       echo p
     ;;
     20|21|23)
       echo o
     ;;
     22)
       echo r
     ;;
     24|31)
       echo E
     ;;
     25)
       echo u
     ;;
     29)
       echo v
     ;;
     30)
       echo 5
     ;;
     32)
       echo 6
     ;;
     33)
       echo A
     ;;
     34|36|37)
       echo B
     ;;
     35|38)
       echo C
     ;;
     39|40)
       echo G
     ;;
     41|42)
       echo K
     ;;
     43|44)
       echo O
     ;;
    esac
} 

#put your accuweather rss address here
address="http://rss.accuweather.com/rss/liveweather_rss.asp?locCode=%2060510"

killall wget
wget -O $Home/1d_accuweather_rss/weather_raw $address


if [[ -s $Home/1d_accuweather_rss/weather_raw ]]; then

    egrep 'Currently|Forecast<\/title>|_31x31.gif' $Home/1d_accuweather_rss/weather_raw > $Home/1d_accuweather_rss/weather
    sed -i '/AccuWeather\|Currently in/d' $Home/1d_accuweather_rss/weather
    sed -i -e 's/^[ \t]*//g' -e 's/<title>\|<\/title>\|<description>\|<\/description>//g' $Home/1d_accuweather_rss/weather
    sed -i -e 's/&lt;img src="/\n/g' $Home/1d_accuweather_rss/weather
    sed -i '/^$/d' $Home/1d_accuweather_rss/weather
    sed -i -e 's/_31x31.*$//g' -e 's/^.*\/icons\///g' $Home/1d_accuweather_rss/weather
    sed -i -e '1s/.$//' -e '3s/.$//' -e '6s/.$//' $Home/1d_accuweather_rss/weather
    for (( i=2; i<=8; i+=3 ))
        do
            im=$(sed -n ${i}p $Home/1d_accuweather_rss/weather)
            sed -i $i"s/^.*$/$(test_image $im)/" $Home/1d_accuweather_rss/weather
        done

 fi
```

---

### Post by Vaphell on 2013-06-04
could you change [quote] tags to [code] ? thanks.

shouldn't $HOME be all caps?

---

### Post by Myst1234 on 2013-06-04
Sorry, code tags wrapped.

I wasn't sure if HOME should be caps since my home dir is not. But I will try and report back

---

### Post by Myst1234 on 2013-06-04
I capitalized HOME and got the same exact error

---

### Post by Vaphell on 2013-06-04
```
TEXT
${voffset 400}${font DejaVu Sans:size=24}${time %A}, ${time %d} ${time %B} ${time %Y}${font}
${battery_bar 8,720 BAT0}
${voffset -8}${fs_bar 8,720 /}
${voffset -8}${goto 400}${cpubar 8,310 cpu}
${voffset -8}${goto 400}${font saxMono:size=9}${top pid 1}${font DejaVu Sans:size=8}${voffset -1} ${top name 1}${voffset 1}${goto 660}${font saxMono:size=9}${top cpu 1}
${goto 400}${font saxMono:size=9}${top pid 2}${font DejaVu Sans:size=8}${voffset -1} ${top name 2}${voffset 1}${goto 650}${font saxMono:size=9}${top cpu 2}
${goto 400}${font saxMono:size=9}${top pid 3}${font DejaVu Sans:size=8}${voffset -1} ${top name 3}${voffset 1}${goto 640}${font saxMono:size=9}${top cpu 3}
${goto 400}${font saxMono:size=9}${top pid 4}${font DejaVu Sans:size=8}${voffset -1} ${top name 4}${voffset 1}${goto 620}${font saxMono:size=9}${top cpu 4}
${goto 400}${membar 8, 260}
${goto 400}${font saxMono:size=9}${top_mem pid 1}${font DejaVu Sans:size=8}${voffset -1} ${top_mem name 1}${voffset 1}${goto 620}${font saxMono:size=9}${top_mem mem 1}
${goto 400}${font saxMono:size=9}${top_mem pid 2}${font DejaVu Sans:size=8}${voffset -1} ${top_mem name 2}${voffset 1}${goto 630}${font saxMono:size=9}${top_mem mem 2}
${goto 400}${font saxMono:size=9}${top_mem pid 3}${font DejaVu Sans:size=8}${voffset -1} ${top_mem name 3}${voffset 1}${goto 640}${font saxMono:size=9}${top_mem mem 3}
${goto 400}${font saxMono:size=9}${top_mem pid 4}${font DejaVu Sans:size=8}${voffset -1} ${top_mem name 4}${voffset 1}${goto 650}${font saxMono:size=9}${top_mem mem 4}${font}
${voffset -90}${font route3:size=160}${time %l}${font route3:size=100}${voffset -80}${goto 230}${time %M}${font}
${voffset -500}[COLOR="#FF0000"]${execpi 360 [/COLOR]${color 48bcff}CHICAGO WEATHER${hr 2}$color${execi 600 bash $Home/1d_accuweather_rss/1d}
${font conkyweather:size=30}${execpi 600  sed -n '2p' $Home/1d_accuweather_rss/weather}${font}${goto 75}${voffset -25}${execpi 600 sed -n '1p' $Home/1d_accuweather_rss/weather|cut -c1-20}
${goto 75}${execpi 600 sed -n '1p' $Home/1d_accuweather_rss/weather|cut -c21-40}
${goto 75}${execpi 600 sed -n '1p' $Home/1d_accuweather_rss/weather|cut -c41-60}
```
this can't be right

---

### Post by Myst1234 on 2013-06-04
Why? 

And 

What would be right?

---

### Post by Vaphell on 2013-06-05
you tell me. It's not closed which is a syntax error that does who knows what to the end result and it lacks actual content to execpi - in other places *${exexpi}* looks like this *${execpi 600  sed -n '2p' $Home/1d_accuweather_rss/weather}* and here it ends with the interval.

---

### Post by stylintile on 2013-06-06
Hello Vaphell,
     Myst1234 is totally correct.  In that line;

```
${voffset -500}[COLOR=#FF0000]${execpi 360 [/COLOR]${color 48bcff}CHICAGO WEATHER${hr 2}$color${execi 600 bash $Home/1d_accuweather_rss/1d}
```

the execpi 360 is supposed to parse a command every 360 conky updates, but there is no command to parse.  If you look at the last object on that line, you can see the bash command following the execi and interval.

I would try removing the;

```
[COLOR=#FF0000]${execpi 360[/COLOR]
```

then try running from terminal again and see what errors come up.

Hope this helps

---

### Post by Myst1234 on 2013-06-06
Oh ok, I see now. I'm new to the conky world, and have been trying to piece things together.

I will report back after the change, thanks

---

### Post by epicoder on 2013-06-08
Your Accuweather script seems to be reacting to the exclamation point in your hash bang, hence the "Bad substitution" error. I have no clue why it's doing that or how to fix it. Check for non-printable characters, maybe?

---

### Post by Myst1234 on 2013-06-08
Hey guys, sorry for the delayed response, have not had a chance to work on this conky til now.

 I removed the suggested section and it did fix it. However I am now getting this - 

```
wget: no process found
--2013-06-08 12:46:49--  http://rss.accuweather.com/rss/liveweather_rss.asp?locCode=60510
Resolving rss.accuweather.com (rss.accuweather.com)... 174.35.30.135, 174.35.30.201
Connecting to rss.accuweather.com (rss.accuweather.com)|174.35.30.135|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2789 (2.7K) [text/xml]
Saving to: `/home/r/1d_accuweather_rss/weather_raw'

100%[======================================>] 2,789       --.-K/s   in 0.001s  

2013-06-08 12:46:49 (2.56 MB/s) - `/home/r/1d_accuweather_rss/weather_raw' saved [2789/2789]

sed: can't read /1d_accuweather_rss/weather: No such file or directory
sed: can't read /1d_accuweather_rss/weather: No such file or directory
sed: can't read /1d_accuweather_rss/weather: No such file or directory

```

Everything looks good until the end. I looked inside the 1d_accuwether_rss folder and there is indeed a weather file, but obviously it's not being picked up.
This leaves the first part running fine, but no weather data, not even pretend weather data, and the xml file reports everything fine as well.

---

### Post by steeldriver on 2013-06-08
looks like you still have $Home in place of $HOME in your 'sed' expressions - $Home is expanding to nothing so instead of **/home/r**/1d_accuwether_rss/weather its is trying to find /1d_accuwether_rss/weather - try

```

echo $HOME
echo $Home

```

see the difference?

---

### Post by stylintile on 2013-06-08
Hello again,
     I'm assuming you are using Teo's scripts from here;

[https://bbs.archlinux.org/viewtopic.php?id=139962](https://bbs.archlinux.org/viewtopic.php?id=139962)

If so, you may want to download the files again. Since there was one error already, there could possibly be others (especially if you copied and pasted from someone else's script).  Or at least compare your file with Teo's original file.  It's been awhile since I used his scripts, but I do remember that I had to create a few of the empty text files because, for some reason, the scripts didn't do it automatically.

Hmm, I just remembered that I also had to change all of the file paths, with search and replace in gedit, from Teo's file path to mine.  Also the ~/ shortcut didn't work either,  I had to put in the entire file path.

Just some things to check, I don't know if that is the problem with yours or not.

edit-- steeldriver posted as I was typing, and that could very well be the problem also.

---

### Post by Myst1234 on 2013-06-09
> **steeldriver said:**
> looks like you still have $Home in place of $HOME in your 'sed' expressions - $Home is expanding to nothing so instead of **/home/r**/1d_accuwether_rss/weather its is trying to find /1d_accuwether_rss/weather - try

```

echo $HOME
echo $Home

```

see the difference?

This made a huge difference!

---

### Post by Myst1234 on 2013-06-09
> **stylintile said:**
> Hello again,
      I'm assuming you are using Teo's scripts from here.

I was an you were right, I needed to double and triple check the scripts

---

### Post by Myst1234 on 2013-06-09
Ok so final thing - 

Thanks for the help everyone, I've got it working so far. Last thing is the weather script should be 3 days (including the current day) but it is only showing 2 including the current. Where did I mess up on that?

This is my current conky

```

background no
update_interval 1
total_run_times 0
own_window yes
own_window_transparent yes
own_window_class Conky
own_window_hints undecorate,sticky,skip_pager,skip_taskbar,below
double_buffer yes
no_buffers yes
text_buffer_size 2048
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
use_spacer none
minimum_size 1000 0
alignment top_left
gap_x 12
gap_y 12
uppercase no
use_xft yes
xftfont DejaVu Sans:size=12
xftalpha 0.8
default_color 000

TEXT
${color 48bcff}Chicago Weather ${hr 2}$color${execi 600 bash $HOME/1d_accuweather_rss/1d}
${font conkyweather:size=30}${execpi 600  sed -n '2p' $HOME/1d_accuweather_rss/weather}${font}${goto 75}${voffset -25}${execpi 600 sed -n '1p' $HOME/1d_accuweather_rss/weather|cut -c1-20}
${goto 75}${execpi 600 sed -n '1p' $HOME/1d_accuweather_rss/weather|cut -c21-40}
${goto 75}${execpi 600 sed -n '1p' $HOME/1d_accuweather_rss/weather|cut -c41-60}

${execi 600  sed -n '3p' $HOME/1d_accuweather_rss/weather}
${font conkyweather:size=30}${execpi 600  sed -n '5p' $HOME/1d_accuweather_rss/weather}${font}${goto 75}${voffset -25}${execpi 600 sed -n '4p' $HOME/1d_accuweather_rss/weather|cut -c1-20}
${goto 75}${execpi 600 sed -n '4p' $HOME/1d_accuweather_rss/weather|cut -c21-40}
${goto 75}${execpi 600 sed -n '4p' $HOME/1d_accuweather_rss/weather|cut -c41-60}

${execi 600  sed -n '6p' $HOME/1d_accuweather_rss/weather}
${font conkyweather:size=30}${execpi 600  sed -n '8p' $HOME/1d_accuweather_rss/weather}${font}${goto 75}${voffset -25}${execpi 600 sed -n '4p' $HOME/1d_accuweather_rss/weather|cut -c1-20}
${goto 75}${execpi 600 sed -n '7p' $HOME/1d_accuweather_rss/weather|cut -c21-40}
${goto 75}${execpi 600 sed -n '7p' $HOME/1d_accuweather_rss/weather|cut -c41-60}

${voffset 200}${font DejaVu Sans:size=24}${time %A}, ${time %d} ${time %B} ${time %Y}${font}
${battery_bar 8,720 BAT0}
${voffset -8}${fs_bar 8,720 /}
${voffset -8}${goto 400}${cpubar 8,310 cpu}
${voffset -8}${goto 400}${font saxMono:size=9}${top pid 1}${font DejaVu Sans:size=8}${voffset -1} ${top name 1}${voffset 1}${goto 660}${font saxMono:size=9}${top cpu 1}
${goto 400}${font saxMono:size=9}${top pid 2}${font DejaVu Sans:size=8}${voffset -1} ${top name 2}${voffset 1}${goto 650}${font saxMono:size=9}${top cpu 2}
${goto 400}${font saxMono:size=9}${top pid 3}${font DejaVu Sans:size=8}${voffset -1} ${top name 3}${voffset 1}${goto 640}${font saxMono:size=9}${top cpu 3}
${goto 400}${font saxMono:size=9}${top pid 4}${font DejaVu Sans:size=8}${voffset -1} ${top name 4}${voffset 1}${goto 620}${font saxMono:size=9}${top cpu 4}
${goto 400}${membar 8, 260}
${goto 400}${font saxMono:size=9}${top_mem pid 1}${font DejaVu Sans:size=8}${voffset -1} ${top_mem name 1}${voffset 1}${goto 620}${font saxMono:size=9}${top_mem mem 1}
${goto 400}${font saxMono:size=9}${top_mem pid 2}${font DejaVu Sans:size=8}${voffset -1} ${top_mem name 2}${voffset 1}${goto 630}${font saxMono:size=9}${top_mem mem 2}
${goto 400}${font saxMono:size=9}${top_mem pid 3}${font DejaVu Sans:size=8}${voffset -1} ${top_mem name 3}${voffset 1}${goto 640}${font saxMono:size=9}${top_mem mem 3}
${goto 400}${font saxMono:size=9}${top_mem pid 4}${font DejaVu Sans:size=8}${voffset -1} ${top_mem name 4}${voffset 1}${goto 650}${font saxMono:size=9}${top_mem mem 4}${font}
${voffset -90}${font route3:size=160}${time %l}${font route3:size=100}${voffset -80}${goto 230}${time %M}${font}
```

and the current weather script 
```
#!/bin/bash

#function: test_image
test_image () {
    case $1 in
     1|01)
       echo a
     ;;
     2|02)
       echo b
     ;;
     3|03)
       echo c
     ;;
     4|04)
       echo c
     ;;
     5|05)
       echo c
     ;;
     6|06)
       echo d
     ;;
     7|07)
       echo e
     ;;
     8|08)
       echo e
     ;;
     11)
       echo 0
     ;;
     12)
       echo h
     ;;
     13|14)
       echo g
     ;;
     15)
       echo l
     ;;
     16|17)
       echo k
     ;;
     18|26)
       echo i
     ;;
     19)
       echo p
     ;;
     20|21|23)
       echo o
     ;;
     22)
       echo r
     ;;
     24|31)
       echo E
     ;;
     25)
       echo u
     ;;
     29)
       echo v
     ;;
     30)
       echo 5
     ;;
     32)
       echo 6
     ;;
     33)
       echo A
     ;;
     34|36|37)
       echo B
     ;;
     35|38)
       echo C
     ;;
     39|40)
       echo G
     ;;
     41|42)
       echo K
     ;;
     43|44)
       echo O
     ;;
    esac
} 

#put your accuweather rss address here
address="http://rss.accuweather.com/rss/liveweather_rss.asp?locCode=60510"

killall wget
wget -O $HOME/1d_accuweather_rss/weather_raw $address


if [[ -s $HOME/1d_accuweather_rss/weather_raw ]]; then

    egrep 'Currently|Forecast<\/title>|_31x31.gif' $HOME/1d_accuweather_rss/weather_raw > $HOME/1d_accuweather_rss/weather
    sed -i '/AccuWeather\|Currently in/d' $HOME/1d_accuweather_rss/weather
    sed -i -e 's/^[ \t]*//g' -e 's/<title>\|<\/title>\|<description>\|<\/description>//g' $HOME/1d_accuweather_rss/weather
    sed -i -e 's/&lt;img src="/\n/g' $HOME/1d_accuweather_rss/weather
    sed -i '/^$/d' $HOME/1d_accuweather_rss/weather
    sed -i -e 's/_31x31.*$//g' -e 's/^.*\/icons\///g' $HOME/1d_accuweather_rss/weather
    sed -i -e '1s/.$//' -e '3s/.$//' -e '6s/.$//' $HOME/1d_accuweather_rss/weather
    for (( i=2; i<=8; i+=3 ))
        do
            im=$(sed -n ${i}p $HOME/1d_accuweather_rss/weather)
            sed -i $i"s/^.*$/$(test_image $im)/" $HOME/1d_accuweather_rss/weather
        done

fi
```

 everything above has been edited with you guys help, and is currently what is working minus the 3rd day in the forecast.


p.s. anyone interested in using the script above feel free. The setup is as follows - 

create a Conky dir in your home dir
in the conky dir create a file called conkymain and copy and paste the first script into it
create a 1d_accuweather_rss dir in your home dir 
in the 1d_accuweather_rss dir create a file called 1d, copy and paste the second script into it
run your conky with ```
conky -c ~/Conky/conkymain
```

---

### Post by stylintile on 2013-06-10
Hi again,
     Sorry for not getting back sooner.  Check the file at;
HOME/1d_accuweather_rss/weather

and compare it to the accuweather extended forecast page.  Find the lines that match the third day forecast.  If I'm correct then the first four lines under TEXT in your rc file are
for current conditions, the second four lines are for the first day, and the third four are for the second day.  Which means you don't have the third day in there.  If the file follows
the pattern for line numbers, the it should be on lines 9,10 and 11.  If that matches then you need to add;

```

${execi 600  sed -n '9p' $HOME/1d_accuweather_rss/weather} 
${font conkyweather:size=30}${execpi 600  sed -n '11p' $HOME/1d_accuweather_rss/weather}${font}${goto 75}${voffset -25}${execpi 600 sed -n '4p' $HOME/1d_accuweather_rss/weather|cut -c1-20}
${goto 75}${execpi 600 sed -n '10p' $HOME/1d_accuweather_rss/weather|cut -c21-40} 
${goto 75}${execpi 600 sed -n '10p' $HOME/1d_accuweather_rss/weather|cut -c41-60} 
```

after the third weather section in your rc.  If those lines don't match, then change the;

```
'10p'
```

to whichever line numbers you need.  For example:

```
sed -n '9p'
```

is telling conky to read line 9 of that file, and the:

```
cut -c41-60
```

is telling it to only display the 41st through the 60th characters in that line.

I have to go to work now, but post back if you have any questions/problems and attach a screenshot of your weather section and I will do my best to help when I get home.  Good luck

---

### Post by Myst1234 on 2013-06-10
Sorry I'm a bit confused, I understand the code better now, but where am I looking for the correlation?

In the weather file, it is nothing but the output of the 1d executable file. Which I assume the conky reads and displays. Not sure where I'm looking for the lines that would or wouldn't display a third day.

---

### Post by stylintile on 2013-06-10
Okay, I tried to download the scripts from the link above, but got a 404 error.  So, if you could start your conky and then copy the weather file at HOME/1d_accuweather_rss/weather and paste it here, I'll see if it will do what you want

---

### Post by Myst1234 on 2013-06-11
This is the HOME/1d_accuweather_rss/weather file

```
Currently: Cloudy: 76F 
e
6/10/2013 Forecast
High: 77 F Low: 59 F Clouds breaking for some sun 
c
6/11/2013 Forecast
High: 85 F Low: 66 F Partly sunny and warmer 
c
```

 I figured this was the file the conky was displaying, because it changes each day the 1d file is executed. I suppose it could change each time it is run, if the weather from accuweather were to change.

EDIT: I just ran it again and it changed ever so slightly

```
Currently: Clear: 68F 
A
6/10/2013 Forecast
High: 77 F Low: 59 F Clouds and limited sun 
d
6/11/2013 Forecast
High: 85 F Low: 66 F Partly sunny and warmer 
c
```

---

### Post by Vaphell on 2013-06-11
your conky shows current + 2 forecasts alright but this part is borked

```
${execi 600  sed -n '3p' $HOME/1d_accuweather_rss/weather}
${font conkyweather:size=30}${execpi 600  sed -n '5p' $HOME/1d_accuweather_rss/weather}
${font}${goto 75}${voffset -25}${execpi 600 sed -n [COLOR="#0000FF"]'4p'[/COLOR] $HOME/1d_accuweather_rss/weather|cut -c1-20}
${goto 75}${execpi 600 sed -n '4p' $HOME/1d_accuweather_rss/weather|cut -c21-40}
${goto 75}${execpi 600 sed -n '4p' $HOME/1d_accuweather_rss/weather|cut -c41-60}

${execi 600  sed -n '6p' $HOME/1d_accuweather_rss/weather}
${font conkyweather:size=30}${execpi 600  sed -n '8p' $HOME/1d_accuweather_rss/weather}
${font}${goto 75}${voffset -25}${execpi 600 sed -n [COLOR="#FF0000"]'4p'[/COLOR] $HOME/1d_accuweather_rss/weather|cut -c1-20}
${goto 75}${execpi 600 sed -n '7p' $HOME/1d_accuweather_rss/weather|cut -c21-40}
${goto 75}${execpi 600 sed -n '7p' $HOME/1d_accuweather_rss/weather|cut -c41-60}
```

---

### Post by stylintile on 2013-06-11
Hi again,
     I just realized that I got your names mixed up in an earlier reply.  I'm sorry for that. :oops:

I just checked the rss page that the script is pulling information, and it only shows current conditions, todays forecast, and tomorrows forecast.  So getting another day from that script/feed will not be possible.  Also, vaphell is correct
as usual, those lines in the rc should read like this:
```

${color 48bcff}Chicago Weather ${hr 2}$color${execi 600 bash $HOME/1d_accuweather_rss/1d}
${font conkyweather:size=30}${execpi 600  sed -n '2p' $HOME/1d_accuweather_rss/weather}${font}${goto 75}${voffset -25}${execpi 600 sed -n '1p' $HOME/1d_accuweather_rss/weather|cut -c1-20}
${goto 75}${execpi 600 sed -n '1p' $HOME/1d_accuweather_rss/weather|cut -c21-40}
${goto 75}${execpi 600 sed -n '1p' $HOME/1d_accuweather_rss/weather|cut -c41-60}

${execi 600  sed -n '3p' $HOME/1d_accuweather_rss/weather}
${font conkyweather:size=30}${execpi 600  sed -n '5p' $HOME/1d_accuweather_rss/weather}${font}${goto 75}${voffset -25}${execpi 600 sed -n '4p' $HOME/1d_accuweather_rss/weather|cut -c1-20}
${goto 75}${execpi 600 sed -n '4p' $HOME/1d_accuweather_rss/weather|cut -c21-40}
${goto 75}${execpi 600 sed -n '4p' $HOME/1d_accuweather_rss/weather|cut -c41-60}

${execi 600  sed -n '6p' $HOME/1d_accuweather_rss/weather}
${font conkyweather:size=30}${execpi 600  sed -n '8p' $HOME/1d_accuweather_rss/weather}${font}${goto 75}${voffset -25}${execpi 600 sed -n '8p' $HOME/1d_accuweather_rss/weather|cut -c1-20}
${goto 75}${execpi 600 sed -n '7p' $HOME/1d_accuweather_rss/weather|cut -c21-40}
${goto 75}${execpi 600 sed -n '7p' $HOME/1d_accuweather_rss/weather|cut -c41-60} 
```

The way yours is now is repeating todays conditions in tomorrows forecast.  If you really want more forecast days you may want to look at mrpeachy's v9000 weather scripts here:

[http://crunchbang.org/forums/viewtopic.php?id=16100](http://crunchbang.org/forums/viewtopic.php?id=16100)

That's what I actually use now.  It was easier for me customize the layout and number of days.  You can have whatever you want, from current conditions only, up to current, today and nine more days.

Hope this helps

---

