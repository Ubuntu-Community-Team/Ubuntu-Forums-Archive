---
title: "startx script (KDE)"
date: 2006-07-12
forum: Programming Talk
---

### Post by geco on 2006-07-12
Hi all! I hope that's the right place to post...
Anyway I wrote a "silly" bash script to start X server from text login with some options, I thaught that it mitgh be good to share it with ubuntu people.
I'm running Kubuntu 6.06 LTS, so I use KDE tricks... I don't know if my script may be useful for GNOME users...

I simply named it "s" to save time in typing :mrgreen: 

Anyway here is the code:

```

#!/bin/bash

#This script is born to be run under the text login.
#For it to be running correctly you need KDE 3.5.3 with Amarok Player
#and the additional kstart scripts which you can create (see kstart --help
#for more informations).
#For dual layout to work you need to properly edit your /etc/X11/xorg.conf file
#(don't forget to backup the original one!) by adding a ServerLayout section
#named "Dual" and the right Screen, Monitor and Device section for a dual monitor to work
#(you can check it out on the web)
#Feel free to copy, modify and distribute di silly bash script! ;-)

SCRIPTNAME=$(basename $0)
AUTOSTART=$HOME/.kde/Autostart
ARG=""

message ()
{
    echo "$SCRIPTNAME is a script to quickly switch on startx with some preferences"
    echo
    echo "Usage: $SCRIPTNAME [-d] [-w|-a]"
    echo "with no arguments just starts Konsole"
    echo "-w starts Konsole, Mozilla Firefox and Mozilla Thunderbird"
    echo "-a starts Konsole and Amarok Player playing some music"
    echo "-d starts the dual screen mode"
    echo
    exit 0
}

if [ "$#" -lt "3" ]; then
    case "$1" in
        -w)
            if [ "$#" -gt "1" ]; then
                message
            fi
            KSTART=kstart.sh
            ;;
        '')
            if [ "$#" -gt "1" ]; then
                message
            fi
            KSTART=kstart-noweb.sh
            ;;
        -a)
            if [ "$#" -gt "1" ]; then
                message
            fi
            KSTART=kstart-amarok.sh
            ;;
        -d)
            ARG="-- -layout Dual"
            case "$2" in
                -w)
                    KSTART=kstart.sh
                    ;;
                '')
                    KSTART=kstart-noweb.sh
                    ;;
                -a)
                    KSTART=kstart-amarok.sh
                    ;;
                *)
                    message
                    ;;
            esac
            ;;
        *)
            message
            ;;
    esac
else
    message
fi
if [ -e /tmp/.X*-lock ]; then
    echo "An X server is already running, shut it down before running this script."
    exit 0
else
    cd $AUTOSTART
    rm -f *kstart* > /dev/null 2>&1
    cp $HOME/.$KSTART $KSTART > /dev/null 2>&1
    chmod +x $KSTART
    #########DEBUG#######
    #echo "$KSTART"     #
    #echo "startx $ARG" #
    #####################
    startx $ARG
    rm -f *kstart* > /dev/null 2>&1
fi
exit 0

```

Here is my kstart scripts:
-a Option:
```

#!/bin/sh
#type "kstart --help" for more informations
kstart --windowclass "Konsole" --desktop 1 multikonsole > /dev/null 2>&1
kstart --windowclass "Amarok" --desktop 1 amarok > /dev/null 2>&1
sleep 10
dcop amarok playlist clearPlaylist
sleep 1
dcop amarok player enableRandomMode false
sleep 1
dcop amarok playlistbrowser loadPlaylist "50 Random Tracks"
sleep 1
dcop amarok player play

```

-w Option:
```

#!/bin/sh
#script to start commonly used programs in different desktops
#type "kstart --help" for more informations
kstart --windowclass "Konsole" --desktop 1 multikonsole > /dev/null 2>&1
kstart --windowclass "Mozilla-firefox-bin" --desktop 3 mozilla-firefox > /dev/null 2>&1
kstart --windowclass "Mozilla-thunderbird-bin" --desktop 4 --activate mozilla-thunderbird > /dev/null 2>&1
kstart --windowclass "Kopete" --desktop 1 kopete > /dev/null 2>&1

```

"multikonsole" is just a script to run several Konsole sessions using dcop, I slightly modified a script found in KDE help files

```

#!/bin/sh
konsole=$(dcopstart konsole-script)
session=$(dcop $konsole konsole currentSession)
dcop $konsole $session > /dev/null

session=$(dcop $konsole konsole newSession)
dcop $konsole $session > /dev/null

session=$(dcop $konsole konsole newSession)
dcop $konsole $session > /dev/null

session=$(dcop $konsole konsole activateSession session-1)
dcop $konsole $session > /dev/null

```

Any suggestion is welcome! :)

---

