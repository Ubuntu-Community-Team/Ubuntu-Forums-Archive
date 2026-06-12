---
title: "Easy Pivot - semi-auto pivot rotation"
date: 2009-12-16
forum: Outdated Tutorials &amp; Tips
---

### Post by GrizzlyBear on 2009-12-16
Hi. I have pivot in Gateway monitor, but didn't know how to run it on.
So, after searching and trying, here i gave You my first tutorial - pivot "how to".
This tutorial is based on my kubuntu 9.10 with KDE4 with Nvidia card, and works fine. Hope, that will works everywhere else.

Let's start:

**//First step:**
You have to edit, the xorg.conf, of course after installng nvidia driver.
```
sudo kate /etc/fstab/xorg-conf
```

In Device (or Screen) section insert line:
```
Option          "RandRRotation" "on"
```

device or screen section - i gave You two options, because, after reading some posts, sometimes
when line "option" is in device section it doesn't work, so the "screen" section is the answer.
(i have it in "device" section).

**//Second step:**
You have to make 4 scripts.
Easy way. Make folder, and in it make 4 files (text files with kate/gedit/nano, whatever).
Name those files.
For example i have
pivotleft, pivotright, pivotnormal, pivotinverted

Here's the important thing:
Those names will be the names of a command, so name it as better as You like.
For example: pivoton (for turning screen left), pivotoff (for turning screen to normal position).

**//Third step:**

edit those files:
(in my example)

file: pivotleft

```
#!/bin/bash 
xrandr --orientation left
```

file: pivotright

```
#!/bin/bash 
xrandr --orientation right
```

file: pivotnormal

```
#!/bin/bash 
xrandr --orientation normal
```

file: pivotinverted

```
#!/bin/bash 
xrandr --orientation inverted
```

of course save all files

**//Fourth step**

copy those files to /usr/bin (with sudo)

for example:
go to the catalog where you are in console or with dolphin, hit F4 and the console will popup.
Write line
```
sudo cp pivotleft /usr/bin
```

the same step for the rest of files

**//fifth step**

chmod +x on those files

go to the /usr/bin
and with the console write line:
```
sudo chmod +x pivotleft
```

the same step for the rest of files

**//sixth step**

All Done  :mrgreen: 

-------------------------------------------
now just hit alt+f2 and try it.
Just write:
pivotleft, pivotright, pivotnormal, pivotinverted
and hit enter.

Screen will be rotating  :D 

/Best Regards
GrizzlyBear

p.s. Many thanks to my friend Tomek for helping me with the script, and many others, who write posts about the "option" section in xorg.conf file.

---

### Post by De4dSpace on 2010-01-10
Can it be a toggle script, so you can make a single panel button launcher that could cycle through the orientations.  Why didn't you just make a keyboard shortcut?  I too want a simple way to rotate, but using two separate keyboard shortcuts is annoying.

All I wanna do is toggle between "xrandr -o normal" & "xrandr -o right"  Any suggestions?

Edit: Here is one script to go between two orientations.

#/bin/bash

x=`cat /home/greezy/Scripts/Pivot.log`

if [ $x -eq "0" ];then
xrandr -o right
echo "1" > /home/greezy/Scripts/Pivot.log
else
xrandr -o normal
echo "0" > /home/greezy/Scripts/Pivot.log
fi

Thanx to [http://filmsbykris.com/](http://filmsbykris.com/)

---

### Post by Johannes Eva on 2011-01-12
> **De4dSpace said:**
> 
#/bin/bash

x=`cat /home/greezy/Scripts/Pivot.log`

if [ $x -eq "0" ];then
xrandr -o right
echo "1" > /home/greezy/Scripts/Pivot.log
else
xrandr -o normal
echo "0" > /home/greezy/Scripts/Pivot.log
fi

Thanx to [http://filmsbykris.com/](http://filmsbykris.com/)

Now that's excellent :D

I did write an introduction to this subject, but didn't go that far!

_**[Ubuntu & NVIDIA: external monitor, rotation, ...]("http://www.johannes-eva.net/ubuntu-linux-external-monitor-nvidia- rotate")**_

Tank you De4dSpace!

---

