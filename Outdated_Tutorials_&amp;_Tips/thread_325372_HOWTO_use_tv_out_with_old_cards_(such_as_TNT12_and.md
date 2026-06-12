---
title: "HOWTO use tv out with old cards (such as TNT1/2 and Geforce256DDR)"
date: 2006-12-25
forum: Outdated Tutorials &amp; Tips
---

### Post by adam0509 on 2006-12-25
Hi,

EDIT : **Important note**

I also made my TV-out worked with the **nvtv** tool. (better, cause I get clone, but in 640*480)


**Introduction**

This method is about "how making TVout works" when your card only support 1 display at a time (**NO clone, NO dual display**).

This HOW-TO has been tested for the following card :
- Geforce 256 DDR
- <add your card here>

And should work for :
- TNT
- TNT2
and basically, all cards having TV-OUT and a driver supporting tvout feature.

**What we gonna do**

In this method, we gonna create 2 files :

    * xorg.conf.notv : It's the normal xorg
    * xorg.conf.tv : It's the xorg for the TV

And we gonna make a script to switch between tv-out and normal display.

**1rst : Making TV-out works**

Now **add** these lines to your xorg.conf :

```
sudo gedit /etc/X11/xorg.conf
```

*Device*

```

Section "Device"
        Identifier      "Device1"
        Driver "nvidia"
        Option  "TVOutFormat" "SVIDEO"
        Option  "TVStandard" "PAL-B"
        Option  "ConnectedMonitor" "TV"
EndSection

```

Most important point here is the option "ConnectedMonitor"

*Monitor*

```

Section "Monitor"
        Identifier "Television" #TV
        HorizSync 30-50
        VertRefresh 60
EndSection

```

Vertrefresh to 50 if old PAL-TV, maybe 100 for recent tv that support 100Hz, but not sure.

*Screen*

```

Section "Screen"
        Identifier      "Screen1"
        Device          "Device1"
        Monitor         "Television"
        DefaultDepth    24
        SubSection "Display"
                Depth 24
                Modes "640x480"
        EndSubSection
EndSection

```

Most important here is "Device" same as in device section, and "Monitor" same as...Monitor section ! (Sure you guess it ;) )

You can change depth and résolution if you want.

*Last but not least : Server Layout*

```

Section "ServerLayout"
        Identifier      "Basic Layout"
        Screen          "Screen1"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

Important here is "Screen", same as in the screen section. 

_Remember the previous value of this one_, cause you will have to "sudo nano /etc/X11/xorg.conf" and change the screen value to the default value after testing.

NOW SAVE YOUR XORG AND TEST (CTRL + ALT + BSPACE ++ startx)

**Script to switch**

From this point, you should have get a display on your TV.

So create 2 different files in your home directory

  * xorg.conf.notv : xorg with screen
  * xorg.conf.tv : xorg working with TV

Copy them to /etc/X11/ :

```

sudo cp xorg.conf.notv /etc/X11
sudo cp xorg.conf.tv /etc/X11

```

You now just need a script that we gonna call "nvidia" (still in your home), in where you will add these lines :

```

#!/bin/bash
 
case $1 in
        tv   ) cp /etc/X11/xorg.conf.tv   /etc/X11/xorg.conf ;;
        notv ) cp /etc/X11/xorg.conf.notv /etc/X11/xorg.conf ;;
        *       ) echo 
                  echo "Usage"
                  echo 
                  echo "  tv   - use TV"
                  echo "  notv - use CRT"
                  ;;    
esac


```

okay now you have to make the script executable, via nauthilus/thunar or with command :

```

chmod 755 nvidia

```

and place it in in a executable folder such as :

```

sudo cp nvidia /usr/local/bin

```

**Using the script**

To choose TV, type in a console :

```
nvidia tv
```

Then restart X : CTRL+ALT+BSPACE. Type "startx" if X does not restart.

If all is correct, X should startx on your TV.

To return to the normal display type in a console :

```
nvidia notv
```

Then restart X.

little trick, if you type nvidia :

```
$ nvidia
tv   - use TV
notv - use CRT

```

This is made because of the echo lines contains inside the script.

**Credits :**

HOWTO by me.

Thanks to all french user that are workings such hard to maintain the [french wiki]("http://doc.ubuntu-fr.org") ;)

If you have any suggestion/question, post here.

You are free to copy, redistribute, correct, improve this document, even if you don't quote me in credits.

---

### Post by ^rooker on 2007-04-28
**Suggested Improvements:**
(Tested on Dapper 6.06.1)


**1) When using TV-out that requires switching of xorg.conf, one could use "switchconf":**

- get switchconf: "sudo apt-get install switchconf"
- create 2 directories: 
mkdir /etc/switchconf/normal /etc/switchconf/tvout

- copy the xorg.conf files in the corresponding subdirectories of these 2 folders. You should end up with something like this:
/etc/switchconf/tvout/etc/X11/xorg.conf
/etc/switchconf/normal/etc/X11/xorg.conf

(You can use this to toggle between more configurations, or you could add more config files to switch (see "switchconf" docs for more). I found it cleaner than doing a brute copy)

- Use "switchconf tvout" or "switchconf normal" to toggle between the modes.
(Unfortunately, switching of xorg.conf files requires (a) restart of X-Server and (b) sudo)

- Restart your X-server by pressing Ctrl+Alt+Backspace.


**2) (my favorite) A small script using "nvtv" to toggle tvout:**
NOTE: This does **not** require any modification to your existing xorg.conf, you don't have to sudo anything - and you don't have to restart your X-server.

```
#!/bin/bash
# Description: Toggles TV-Out mode (nvidia cards, only).
# Author: ^Rooker
# Date: 2007-Apr-28
# Based on info from: http://wiki.ubuntuusers.de/NVtv

case "$1" in
on)     echo "Turning TV out $1..."
        xrandr -s 800x600                     # switch X server to 800x600 
        nvtv -r 800,600 -s Huge -X -t       # Turn tv-out (-t) on for 800x600 (-r), X-mode (-X) and overscan "Huge" (-s)
        ;;

off)    echo "Turning TV out $1..."
        nvtv -m                                     # Turn tv-mode off
        sleep 1                                     # Wait a second.
        xrandr -s 0                                # return to default X resolution
        ;;

*)      echo "Syntax: $0 [on|off]"
esac
```


**Short explanation: **
- "xrandr -s 800x600" switches the X-server resolution on the fly to 800x600 (for PAL). For NTSC it should be 640x480 (I guess?).
- nvtv parameter "-s Huge" cuts quite a bit off the edge of the image on the TV. Some might prefer "-s Normal" for less cropping.

---

