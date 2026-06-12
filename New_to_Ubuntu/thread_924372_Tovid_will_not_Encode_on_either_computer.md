---
title: "Tovid will not Encode on either computer"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by wetinwales on 2008-09-19
Hi All
Using Ubuntu 8.04. (on two separate machines. One desktop dedicated only to Ubuntu and one Laptop dual boot with XPsp3 )
Neither will Encode a .vob file
Installed (I hope) ALL the dependencies listed in the tovid WIKI. Re-installed tovid.
It will not Encode (from a .vob file)

The log gives:-

The following commands will be run:
=========================================
makemenu -noask -quiet -overwrite -pal -dvd -align northwest -font "Helvetica" -fontsize 24 -textcolor "rgb(255,255,255)" -fontdeco '-stroke rgb(0,0,0) -strokewidth 1' -button-font "Helvetica" -button ">" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -button-outline "rgb(140,140,140)" "VTS 01 1.VOB" -out "/tmp/Untitled_menu_1"
------------------------
tovid -quiet -overwrite -pal -dvd -full -quality 8 -in "/media/disk/Fallout Decrypt/VTS_01_1.VOB" -out "/tmp/VTS 01 1.VOB.tovid_encoded" -from-gui -noask
------------------------
makexml -quiet -overwrite -dvd -menu "/tmp/Untitled_menu_1.mpg" "/tmp/VTS 01 1.VOB.tovid_encoded.mpg" -out "/tmp/Untitled_disc"
------------------------
Running command: makemenu -noask -quiet -overwrite -pal -dvd -align northwest -font "Helvetica" -fontsize 24 -textcolor "rgb(255,255,255)" -fontdeco '-stroke rgb(0,0,0) -strokewidth 1' -button-font "Helvetica" -button ">" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" -button-outline "rgb(140,140,140)" "VTS 01 1.VOB" -out "/tmp/Untitled_menu_1"
================================================== =======
mencoder MISSING!

You are missing CORE tovid dependencies! Please install the above MISSING
dependencies and try again. See tovid.wikia.com/wiki/Tovid_dependencies or
tovid.org for help.
================================================== =======
Running command: tovid -quiet -overwrite -pal -dvd -full -quality 8 -in "/media/disk/Fallout Decrypt/VTS_01_1.VOB" -out "/tmp/VTS 01 1.VOB.tovid_encoded" -from-gui -noask
================================================== =======
mencoder MISSING!

You are missing CORE tovid dependencies! Please install the above MISSING
dependencies and try again. See tovid.wikia.com/wiki/Tovid_dependencies or
tovid.org for help.
================================================== =======
Running command: makexml -quiet -overwrite -dvd -menu "/tmp/Untitled_menu_1.mpg" "/tmp/VTS 01 1.VOB.tovid_encoded.mpg" -out "/tmp/Untitled_disc"
================================================== =======
mencoder MISSING!

You are missing CORE tovid dependencies! Please install the above MISSING
dependencies and try again. See tovid.wikia.com/wiki/Tovid_dependencies or
tovid.org for help.
================================================== =======
Can anyone shed light on it for me ???
Daf
wetinwales is online now Report Post   	Edit/Delete Message

---

### Post by LowSky on 2008-09-19
"mencoder MISSING!"
Thats the biggest clue to your problem
this should fix it
```
sudo apt-get install mplayer
```

---

### Post by wetinwales on 2008-09-19
Have the latest mplayer installed according to terminal (I put it in a couple of hours ago)
Now my problem on 'BURN' is SCR running backwards remultiplex input (not exact wording)
Lord knows how I do that. I guess its other language for "...strip off the timecode and re-lay a new one..."
I'm lost now...
Be grateful for any help

---

