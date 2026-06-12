---
title: "Gnome panel problem"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by blueshead on 2012-02-19
It's Mardi Gras.. It's my bday..Copious amounts of beer..

Don't know how I did this before I passed out on the floor..But is there anyway to get the panel back up to the top? lol

It's as you can see..It's stuck in the middle of my screen.. :P

And yes.. I went to panel properties and selected top..It don't budge..It laughs at me.. 

Is there a key command so I can drag it?  It's sneering at me now!

[IMG]http://i260.photobucket.com/albums/ii38/blueshead_bucket/Screenshot-02192012-062945AM.png[/IMG]

---

### Post by Frogs Hair on 2012-02-19
Not sure what you did , but try the following .```
rm -rfv $HOME/.gconf/apps/panel
```

---

### Post by blueshead on 2012-02-19
> **Frogs Hair said:**
> Not sure what you did , but try the following .```
rm -rfv $HOME/.gconf/apps/panel
```


Hey frogs.. I fixed it.. not sure how I did it..I kept clicking move left, right,top,bottom.. and rebooted.. and ITS back..

I have no idea why it worked.. but I'm happy now..

Thank you for answering my post,though.. :KS

---

### Post by spillage2 on 2012-02-19
When you have got it sorted run the .sh below and back it up. If it happens again just run and restore...
Just save as panel_restore.sh..

```

#!/bin/sh
#
# GNOME Panel Save / Restore
# Writen by PhrankDaChicken
#
# http://ubuntu.online02.com
#
#
# Updated to add restore defaults by jimjimovich
# http://www.starryhope.com
#
#


DIR=$(pwd)
TITLE="PanelRestore"

Main () {
    CHOICE=$(zenity --list --title "$TITLE" --hide-column 1 --text "What do you want to do?" --column "" --column "" \
"0" "Save Panel Settings" \
"1" "Restore Panel Settings" \
"2" "Restore Default Panel Settings")
    if [ $CHOICE = 0 ]; then
        Panel_Save
    fi
    if [ $CHOICE = 1 ]; then
        Panel_Restore
    fi
    if [ $CHOICE = 2 ]; then
        Panel_Defaults
    fi    
}

Panel_Restore () {
    FILE=$(zenity --title "$TITLE: Open File" --file-selection --file-filter "*.xml" )
    if [ -n "$FILE" ]; then 
        gconftool-2 --load "$FILE"
        killall gnome-panel
    fi
    Main
}

Panel_Save () {
    FILE=$(zenity --title "$TITLE: Save File" --file-selection --save --confirm-overwrite --filename "Gnome_Panel.xml" --file-filter "*.xml" )
    if [ -n "$FILE" ]; then 
        EXT=$(echo "$FILE" | grep "xml")
        if [ "$EXT" = "" ]; then
            FILE="$FILE.xml"
        fi
        gconftool-2 --dump /apps/panel > $FILE
        zenity --info --title "$TITLE: File Saved" --text "File saved as: \n $FILE"
    fi
    Main
}

Panel_Defaults () {
    zenity --question --text="Are you sure you want to restore the default top and bottom panels?"
    gconftool-2 --recursive-unset /apps/panel
    rm -rf ~/.gconf/apps/panel
    pkill gnome-panel
    exit
}

Main

# END OF Script

```

Spill.

---

### Post by blueshead on 2012-02-19
> **spillage2 said:**
> When you have got it sorted run the .sh below and back it up. If it happens again just run and restore...
Just save as panel_restore.sh..

```

#!/bin/sh
#
# GNOME Panel Save / Restore
# Writen by PhrankDaChicken
#
# http://ubuntu.online02.com
#
#
# Updated to add restore defaults by jimjimovich
# http://www.starryhope.com
#
#


DIR=$(pwd)
TITLE="PanelRestore"

Main () {
    CHOICE=$(zenity --list --title "$TITLE" --hide-column 1 --text "What do you want to do?" --column "" --column "" \
"0" "Save Panel Settings" \
"1" "Restore Panel Settings" \
"2" "Restore Default Panel Settings")
    if [ $CHOICE = 0 ]; then
        Panel_Save
    fi
    if [ $CHOICE = 1 ]; then
        Panel_Restore
    fi
    if [ $CHOICE = 2 ]; then
        Panel_Defaults
    fi    
}

Panel_Restore () {
    FILE=$(zenity --title "$TITLE: Open File" --file-selection --file-filter "*.xml" )
    if [ -n "$FILE" ]; then 
        gconftool-2 --load "$FILE"
        killall gnome-panel
    fi
    Main
}

Panel_Save () {
    FILE=$(zenity --title "$TITLE: Save File" --file-selection --save --confirm-overwrite --filename "Gnome_Panel.xml" --file-filter "*.xml" )
    if [ -n "$FILE" ]; then 
        EXT=$(echo "$FILE" | grep "xml")
        if [ "$EXT" = "" ]; then
            FILE="$FILE.xml"
        fi
        gconftool-2 --dump /apps/panel > $FILE
        zenity --info --title "$TITLE: File Saved" --text "File saved as: \n $FILE"
    fi
    Main
}

Panel_Defaults () {
    zenity --question --text="Are you sure you want to restore the default top and bottom panels?"
    gconftool-2 --recursive-unset /apps/panel
    rm -rf ~/.gconf/apps/panel
    pkill gnome-panel
    exit
}

Main

# END OF Script

```

Spill.



This sounds great. But I'm only into Ubuntu for 4 months..(OSX user)

How do I save this as a script..sh?

Ahh I copied n pasta it in text edit and saved as  .sh  It shows up as a script now.. Will that be O.K? It looks very similer to Applescripts

And thank you very much for the help!

---

### Post by spillage2 on 2012-02-19
yep that should do it. like i said get it all back to how it was then you can change things around see what you think and if your not happy run the script to take it back to normal.

i have my two panels at the bottom of my page both transparent. the upper one has my icons bit like a dock panel and my running programs show below.

did try a proper dock programme but didn't like any that much..

spill.

---

### Post by Frogs Hair on 2012-02-19
> **blueshead said:**
> Hey frogs.. I fixed it.. not sure how I did it..I kept clicking move left, right,top,bottom.. and rebooted.. and ITS back..

I have no idea why it worked.. but I'm happy now..

Thank you for answering my post,though.. :KS

Glad it's working .:o

---

### Post by blueshead on 2012-02-19
> **spillage2 said:**
> yep that should do it. like i said get it all back to how it was then you can change things around see what you think and if your not happy run the script to take it back to normal.

i have my two panels at the bottom of my page both transparent. the upper one has my icons bit like a dock panel and my running programs show below.

did try a proper dock programme but didn't like any that much..

spill.

Ya  being an OSX user.. I've tried the different dock apps for Ubuntu.. Did not like any of them..

I've been very happy with the panel and the very few apps I need in them..

All good now!

And thank you very much for the script!

---

