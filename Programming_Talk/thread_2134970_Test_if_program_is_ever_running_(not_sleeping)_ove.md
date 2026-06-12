---
title: "Test if program is ever running (not sleeping) over a time period?"
date: 2013-04-12
forum: Programming Talk
---

### Post by Merrattic on 2013-04-12
I promise I have searched on this high and low (not just on ubuntuforums) and can't seem to find an answer. Here is the scenario:

I am using mplayer to run a slideshow of jpg images all day. (Yes I know there is feh and fbi, but this is being done without X against the framebuffer inside gnuscreen, so fbi won't work, and mplayer "does")

Each image is on screen for @ 60 seconds then changes to the next.

Watching htop, mplayer is sleeping (S) for most of the time, then when the time comes to change the image it starts running (R) then goes back to sleep (S).

My problem is that at some point each day (random) mplayer freezes up, and stops changing images, even though it still displays an image on screen. htop reports that mplayer is (S).

**How can I run a monitor like "top" on mplayer for say a two minute period to check if mplayer ever goes to (R) (or has an increase in CPU usage) ?**

I can then script to restart mplayer if no (R) is found.

TIA

---

### Post by ofnuts on 2013-04-12
I think you are tackling the problem from the wrong end. If mplayer is mostly sleeping even if it runs fine you'll have a very hard time differentiating the good sleep from the bad one. 

But unless mplayer has a cache, the most recent last access time in the set of files should regularly change...  If all files are in the same directory, this is the output of:
 ```

stat -c '%X' $dir/* | sort -rn  | head -1

```

---

### Post by Vaphell on 2013-04-12
another way would be to put mplayer in a loop with shorter playlists, even if it fails, next step will fix it.
Btw, why not display images one by one in a loop? Is there a reason why the whole list must be loaded at once?

---

### Post by Merrattic on 2013-04-12
@ ofnuts

I'll give that a try, thanks :)

@ Vaphell

Shorter playlists had crossed my mind, or to run some thing like asciiquarium and weatheraspect every now and then, but as I said in the OP mplayer can freeze at anytime.

Doing image by image in a loop with mplayer seemed a bit overkill at the time (?) and I am guessing I would get a blank screen during each change, but I'll try that too as it would overcome the freezing issue too. Thanks :)


What I am surprised about is that there doesn't appear to be a "constant" / "live" monitoring tool, only ones that look at "now" .....:?

---

### Post by Merrattic on 2013-04-13
@ ofnuts

The commands works, and I can see how I can use it :) but none of the files have an access date that relates to "today". All files are renamed randomly each day to shuffle the display sequence. This is shown in "change", but access time and date remains the date I installed the file, which was weeks ago?

---

### Post by rnerwein on 2013-04-13
hi
whats about a little shell script - show only how to
ps -ef | grep process_to_watch
cd /proc/PID_process_to_watch
in a loop
cat sched > /tmp/is_running1
sleep some_seconds
cat sched > /tmp/is_running2
diff /tmp/is_running1 /tmp/is_running2
if there is no difference - do what you want

ciao

---

### Post by ofnuts on 2013-04-13
> **Merrattic said:**
> @ ofnuts

The commands works, and I can see how I can use it :) but none of the files have an access date that relates to "today". All files are renamed randomly each day to shuffle the display sequence. This is shown in "change", but access time and date remains the date I installed the file, which was weeks ago?

This is on a Linuxish file system  (ext2/3/4, reiserfs)? Or in a filesystem mounted wit the option to not use atime 

What says 'stat' alone on one of these files?

---

### Post by Merrattic on 2013-04-13
I used stat to show me the access times :) It is on a CLI ubuntu built from mini iso - ext4 fs. NO X.

@ Vaphell

my little script to loop mplayer, gives a momentary blink between images though

```
#!/bin/bash

FILES="~/Pictures/*.jpg"

for F in $FILES

do

mplayer -geometry 0:0 mf://"$F" -idle -fixed-vo -vf scale=1024:600 & 
sleep 3
killall -9 mplayer

done
```

Any improvements?

@ rnerwien

It needs to constantly monitor to catch mplayer when/if it starts running...

---

### Post by Habitual on 2013-04-14
> **Merrattic said:**
> **How can I run a monitor like "top" on mplayer for say a two minute period to check if mplayer ever goes to (R) (or has an increase in CPU usage) ?**[http://collectl.sourceforge.net/](http://collectl.sourceforge.net/) may be useful in this case.
You can actually tell it to run for 12 hours and then play it all back at your convenience. Very clever stuff.

---

### Post by Merrattic on 2013-04-15
Ah, collectl, that's more like it. :D Here is some output on mplayer, you should be able to see when mplayer starts and closes:

```
~$ collectl --procfilt f /usr/bin/mplayer

#<----CPU[HYPER]-----><----------Disks-----------><----------Network---------->
#cpu sys inter  ctxsw KBRead  Reads KBWrit Writes   KBIn  PktIn  KBOut  PktOut 
   1   0   272    408      0      0      0      0      0      0      0       0 
  16   2   531    506      0      0      0      0      0      1      0       2 
   2   0   339    546      0      0      0      0      0      0      0       0 
   9   7   430    821      0      0      0      0      0      0      0       0 
   0   0   227    416      0      0      0      0      0      0      0       0 
   1   0   239    437      0      0      0      0      0      0      0       0 
   0   0   277    525      0      0      0      0      0      0      0       0 
   1   0   564   1078      0      0     16      3      0      0      0       0 
   1   0   256    472      0      0      0      0      0      0      0       0 
   1   0   527    984      4      1      0      0      0      0      0       0 
   4   1   473    806      4      1      0      0      3     10      0       0 
   5   0   457    856      0      0      0      0      0      0      0       0 
  22   4   708    902   2116     28      0      0      0      0      0       0 
   9   1   688   1230      0      0      0      0      0      0      0       0 
   5   1   465    808      0      0      0      0      0      0      0       0 
  26   5  1081   1590      4      1      0      0      0      0      0       0 
   2   0   426    796      0      0      0      0      0      0      0       0 
   9   3  1981   3476     40      8     20      3      0      1      0       0 
  13   6   987   1393      0      0      0      0      0      0      0       0                       << mplayer started up @ here
  26  11   861    792      0      0      0      0      0      0      0       1 
  38  12  1088    870      0      0      0      0      0      0      0       0 
  26  10   915    850      0      0      0      0      0      0      0       0 
#<----CPU[HYPER]-----><----------Disks-----------><----------Network---------->
#cpu sys inter  ctxsw KBRead  Reads KBWrit Writes   KBIn  PktIn  KBOut  PktOut 
  26   9   879    810      0      0      0      0      0      0      0       0 
  34  15  1393   1707      0      0      0      0      0      0      0       0 
  19   3  1572   1556      0      0      0      0      0      0      0       0 
  15   1   866   1123      0      0      0      0      0      0      0       0 
  15   1   727   1037      0      0      0      0      2      5      0       0 
  14   1   758   1139      0      0      0      0      2      5      0       0 
  13   0   707   1044      0      0      0      0      0      0      0       0 
  13   1   752   1147      0      0     16      3      0      0      0       0 
  15   0   774   1104      0      0      0      0      0      0      0       0 
  14   0   715   1025      0      0      0      0      0      0      0       0 
  15   0   801   1183      0      0      0      0      0      1      0       1 
  14   0   749   1129      0      0      0      0      0      0      0       0 
  16   0   789   1141      0      0      0      0      0      0      0       0 
  15   1   731   1055      0      0      0      0      0      0      0       0 
  15   1   784   1143      0      0      0      0      0      0      0       0 
  16   0   777   1148      0      0      0      0      0      0      0       0 
  15   1   756   1033      0      0      0      0      0      0      0       0 
  15   1   793   1134      0      0      0      0      0      0      0       0 
  16   1   857   1231      0      0      0      0      0      0      0       0 
  18   1   971   1455      0      0     12      3      0      0      0       0 
  15   1   825   1164      0      0      0      0      0      0      0       0 
  34  10  1487   2283      0      0      0      0      3     10      0       0 
#<----CPU[HYPER]-----><----------Disks-----------><----------Network---------->
#cpu sys inter  ctxsw KBRead  Reads KBWrit Writes   KBIn  PktIn  KBOut  PktOut 
  19   0   987   1304      0      0      0      0      0      0      0       0 
  15   2   798   1091      0      0      0      0      0      0      0       0 
  15   1   762    959      0      0      0      0      0      0      0       0 
  16   1   763   1088      0      0      0      0      0      0      0       0 
  15   1   735    953      0      0      0      0      0      0      0       0 
  14   1   765   1146      0      0      0      0      0      0      0       0 
  17   0   836   1133      0      0      0      0      0      0      0       0 
  16   1   742   1053      0      0      0      0      0      0      0       0 
  15   0   793   1154      0      0      0      0      0      0      0       0 
  12   0   731   1038      0      0      0      0      0      0      0       0 
  16   1   815   1208      0      0      0      0      0      0      0       0 
  16   1   740   1067      0      0      0      0      0      0      0       0 
  18   1   941   1337      0      0      0      0      0      0      0       0 
  14   2   815   1136      0      0      0      0      0      1      0       1 
   1   0   248    452      0      0      0      0      0      0      0       0                        << mplayer stopped @ here
   1   0   250    424      0      0      0      0      3     11      0       2 
   1   0   287    441      0      0      0      0      0      0      0       0 
   1   0   233    419      0      0      0      0      0      0      0       0 
   1   0   316    516      0      0      0      0      0      0      0       0 
   8   6   434    826      0      0      0      0      0      0      0       0 
   1   0   224    413      0      0      0      0      0      0      0       0 
   0   0   241    439      0      0      0      0      0      0      0       0 
#<----CPU[HYPER]-----><----------Disks-----------><----------Network---------->
#cpu sys inter  ctxsw KBRead  Reads KBWrit Writes   KBIn  PktIn  KBOut  PktOut 
   1   0   224    412      0      0      0      0      0      0      0       0 
   1   0   254    471      0      0      0      0      0      0      0       0 
   0   0   222    408      0      0      0      0      0      0      0       0 
   1   0   242    426      0      0      0      0      0      0      0       0 
   1   0   293    453      0      0      0      0      0      0      0       0 
   1   0   309    577      0      0      0      0      0      0      0       0 
```

Next problem (:)) how to capture a cpu spike as above in a bash script and convert to a variable of "Yes" ??  (am guessing some sed and awk and a greater than comparison?)

---

### Post by Bodsda on 2013-04-15
Assuming the output is delivered line by line, you can pipe to awk to get just the first column
```

command | awk '{print $1}'

```
Store the output, or run your comparison directly against that in the if clause.

Bodsda

---

### Post by Habitual on 2013-04-16
interactive mode is cool, but turn on collection for the I/O

[URL="http://collectl.sourceforge.net/ProcessIOStats.html"]http://collectl.sourceforge.net/ProcessIOStats.html
[/URL]

---

### Post by Merrattic on 2013-04-17
Hmmmm finding collectl too complicated to get to the info I want and to script it all in. Also running mplayer in a loop is causing script std output to break through the image on the terminal (despite my efforts to silence terminal output with "> /dev/null 2>&1" and other such switches) :(

Will perhaps look at a crontab job which simply restarts every hour or so, and put up with a blank screen for a minute or so (image random renaming mostly)

Thanks for all the help though, and collectl is a cool cli tool :)

---

### Post by Habitual on 2013-04-18
> **Merrattic said:**
> Hmmmm finding collectl too complicated to get to the info I want and to script it all in. Also running mplayer in a loop is causing script std output to break through the image on the terminal (despite my efforts to silence terminal output with "> /dev/null 2>&1" and other such switches) :(

Will perhaps look at a crontab job which simply restarts every hour or so, and put up with a blank screen for a minute or so (image random renaming mostly)

Thanks for all the help though, and collectl is a cool cli tool :)

You are correct, whatever you seem to be doing with "mplayer in loops" and redirects, AND cron won't be solved by using collectl.
But I'm certain you'll figure it out.

Don't thank me, next time I need to use collectl, I am calling on you.

Good Luck.

---

### Post by Merrattic on 2013-05-08
Revisited this issue and eventually came up with a small bash script using **top** to capture a "running" (as opposed to sleeping) process:

```
#!/bin/bash

while :         # infinite loop until condition satisfied
do
if top -bcn 1 | grep "mplayer" | grep "R"; then
# "Do Something"
break
fi
done
```

Needs more work to do what I want but just showing the basics for now ;)

EDIT

Final script in place:

```
#!/bin/bash

if top -d 1 -bcn 180 | grep "mplayer" | grep "R"; then
echo "Running"
else
echo passwd | sudo -S shutdown -r now
fi
```

and a crontab job:

```
*/10 * * * * /home/dpf/running.sh
```

The "180" means that top will look every second for 3 minutes. If it can grep an "R" in that time (images currently on screen for @ 2.5 mins) then all is OK, if it can't then it restarts the PC (lazy I know, will work on better solution, but it reboots so quickly, it makes not much difference). The crontab runs every 10 minutes. Only problem I have spotted is that sometimes mplayer doesn't move from S to R when it changes pictures (or this hapens so fast I don't see it or top doesn't capture it. top allows fractions of seconds so adjusting the runtime might sort this out. Would be easier if I could figure out a way to capture CPU % from top instead of S & R.....

**[EDIT]**

Neater solution without having to reboot:

```
#!/bin/bash

if top -d 1 -bcn 180 | grep "mplayer" | grep "R"; then
echo "Running"
else
screen -X quit #(stops gnu-screen)
echo passwd | sudo -S openvt -f -c 1 ./myscript.sh  #(restarts script on actual physical display)
fi
```

[http://ubuntuforums.org/showthread.php?t=2144422&p=12644806#post12644806](http://ubuntuforums.org/showthread.php?t=2144422&p=12644806#post12644806)

---

