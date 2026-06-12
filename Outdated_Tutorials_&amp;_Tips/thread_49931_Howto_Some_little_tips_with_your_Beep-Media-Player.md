---
title: "Howto: Some little tips with your Beep-Media-Player."
date: 2005-07-18
forum: Outdated Tutorials &amp; Tips
---

### Post by JoeyrS on 2005-07-18
This howto shows some application of the plugin bmp-songchange, a port of the old xmms songchange plugin.

Lets go.
Open a terminal session and enter:
```

wget http://joeyrs.altervista.org/bmp-songchange_0.0.1-2_i386.deb
sudo dpkg -i bmp-songchange_0.0.1-2_i386.deb

```

(I've made that package because there is no an official version. That one works fine in Ubuntu and Debian.)
Now the Beep-Media-Player Songchange plugin is installed on our ubuntu, lets configure it.
- Run beep-media-player and select Preferences -> Plugins -> General
- Click in "Song Change 0.0.1" CheckBox (Activate it)
- Click Preferences.

In Song change Command Box type:
```
 echo "Current Song: %s" >~/.bmp/songchange.dat
```
(This outputs the title of your current song in a file.)

In Playlist end Command Box type:
```
echo "" >~/.bmp/songchange.dat
```
(This clear the file if the playlist ends.)

You can optionally include these strings:
        %F     frequency (in hertz)
        %c     number of channels
        %f      filename (full path)
        %l      length (in milliseconds)
        %n     name
        %r      rate (in bits per second)
        %s     name (an alias for %n)
        %t     playlist position (%02d)

From now you'll have the title of the current song in a file (~/.bmp/songchange.dat); how we can use it?

**_XChat:_**
  Want to print in a channel the title of your current song? It's very simple, just type in your current xchat window:
```
  /exec -o cat ~/.bmp/songchange.dat
```

  You can simplify that command in two modes:
  - Adding a button in the userlist panel:
    Type in your current xchat window:
```
 /addbutton SongChange exec -o cat ~/.bmp/songchange.dat
```
  - Making an alias:
    Select Menu -> Settings -> Advanced -> Replace Menu
    Add a new alias typing in name box: song and in command box:
```
exec -o cat ~/.bmp/songchange.dat
```
    Click on Save Button.
    Now you can show your song typing: /song

**_XOSD:_**
XOSD is a simple library to display shaped text on your X display, like a TV on-screen display. You can use it for displaying the title of the current song. Install it by typing: _apt-get install xosd-bin_ or using synaptic.
After the install we can display the song title by using osd_cat command.
Using XOSD (Example):
```
osd_cat -f"-adobe-helvetica-bold-*-*-*-20-*-*-*-*-*-*-*" -s1 -pbottom -o-40 -cgreen -d5 ~/.bmp/songchange.dat
```

Making automatic the OSD SongChange:
Let's return to Beep-Media-Player Preferences and modify:
```
echo "Current Song: %s" >~/.bmp/songchange.dat
``` to:

```
echo "Current Song: %s" >~/.bmp/songchange.dat && osd_cat -f"-adobe-helvetica-bold-*-*-*-20-*-*-*-*-*-*-*" -d5 ~/.bmp/songchange.dat
```
From now osd_cat displays your current song title every time the song changes,
you can refer at [http://ldots.org/xosd-guide/index.html](http://ldots.org/xosd-guide/index.html) for personalizing your OSD Title.
Here is an example of OSD SongChange: [http://img69.imageshack.us/img69/4619/xosd7sl.png](http://img69.imageshack.us/img69/4619/xosd7sl.png)

You can use both of these tips together.
That's all. Hope this are useful, any comment would be appreciated.

---

### Post by MrRoboto on 2005-07-18
nice trick.. thanks!

---

### Post by Sam on 2005-07-19
Thank you for this good tip ! :razz:

---

### Post by JoeyrS on 2005-07-20
Another Tip: 
Want to show the lenght of your current song in minutes and seconds?
I wrote down this simple bash script, it converts from millisec to Minutes:Seconds

```

#!/bin/bash
if [ $# -eq 1 ] ; then
  Lenght="$(echo "scale=2; ($1/1000)/60" | bc)"
  Point=`expr index "$Lenght" .`
  Minutes=`expr substr $Lenght 1 $(( $Point - 1 ))`
  Seconds="$(echo "scale=2; (${Lenght:2}/100)*60" | bc)"
  Point=`expr index "$Seconds" .`
  Seconds=`expr substr $Seconds 1 $(( $Point - 1 ))`
  if [ ${#Minutes} = 1 ] ; then Minutes=0$Minutes ; fi
  if [ ${#Seconds} = 1 ] ; then Seconds=0$Seconds ; fi
  echo $Minutes:$Seconds
fi

```

Copy and paste in a new file (for ex. "converter") , save and make it executable by typing: chmod +x converter.

Than back to beep-media-player's preferences and add to echo: $(/path/to/your/file/converter %l)

The script read the lenght in milliseconds and outputs in [mm:ss]

The final command are like this: (with XOSD)
```

echo "* Now Listening: « %s» [$(/home/joeyrs/converter %l)]" >~/.bmp/songchange.txt && osd_cat -f"-adobe-helvetica-bold-*-*-*-20-*-*-*-*-*-*-*" -s1 -pbottom -o-40 -cgreen -d5 .bmp/songchange.dat

```

Hope this are helpful :)

---

### Post by maruchan on 2005-07-20
This is a pretty cool tip. However, a few questions:

-my OSD shows at the top left, where there's a lot of stuff already - how can I change that?
-how can I change the font size?
-how can I change the font color from red?
-how can I enable the drop shadow?

Thanks!

---

### Post by JoeyrS on 2005-07-20
> **maruchan]This is a pretty cool tip. However, a few questions:

-my OSD shows at the top left, where there's a lot of stuff already - how can I change that?
-how can I change the font size?
-how can I change the font color from red?
-how can I enable the drop shadow?

Thanks![/QUOTE]

**For the position you can use these opt on osd_cat:**
  -A <left/right/center>
  -p <top/middle/bottom>
  -o (This is the offset, use with positive or negative integers)

** Changing Font Size: **
You have two ways for changing the font size:
1) Using a tool like gtkfontsel (sudo apt-get install gtkfontsel) and choosing your own font type and size said:**
> Thanks!
You're welcome :)

---

### Post by maruchan on 2005-07-20
Awesome. Thanks for the help.

---

### Post by Mr. Electric Wizard on 2005-07-21
Sounds pretty cool, can somebody please post a screenshot of this OSD?

---

### Post by JoeyrS on 2005-07-21
[HERE](http://img69.imageshack.us/img69/4619/xosd7sl.png) There is an example of XOSD + SoundChange Plugin.

(Look at the bottom left of the image).

---

### Post by Feanor on 2005-07-29
Very good job JoeyrS!  ;-)

---

### Post by fng on 2005-08-03
great tip
thnx!

---

### Post by dziubek on 2005-10-09
[QUOTE=JoeyrS]bmp-songchange_0.0.1-2_i386.deb

In Song change Command Box type:
```
 echo "Current Song: %s" >~/.bmp/songchange.dat
```
(This outputs the title of your current song in a file.)

You can optionally include these strings:
        %F     frequency (in hertz)
        %c     number of channels
        %f      filename (full path)
        %l      length (in milliseconds)
        %n     name
        %r      rate (in bits per second)
        %s     name (an alias for %n)
        %t     playlist position (%02d)[/QUOTE]

echo "%s" > /home/romek/.musiq

211.113.235.71:8422

 ](*,)

---

### Post by kaamos on 2005-10-10
```

~$ osd_cat -f"-adobe-helvetica-bold-*-*-*-20-*-*-*-*-*-*-*" -s1 -pbottom -o-40 -cgreen -d5 ~/.bmp/songchange.dat
Error initializing osd: Default font not found
~$

```

any ideas?

---

