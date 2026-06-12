---
title: "Strange dialog script behavior with gnome-terminal"
date: 2009-09-22
forum: Programming Talk
---

### Post by jakev383 on 2009-09-22
This script works perfectly on my 8.04 machine, but I got a new computer and installed 9.04 on it and it doesn't work the way I want. I created a launcher for this, and exactly the same as the one on my old machine. The menu will come and up and display, but when I select an item the menu closes and nothing else happens. I can run the gnome-terminal command exactly as displayed in the script from a terminal and it works, but I cannot call it from my menu. But it works on my old system. Strange! I was hoping someone here could look at it and see why it may not be working on my 9.04 system.

```

#!/bin/sh
a1_initialization() {

# set a temp file for the working scratch. $$ is the current shell ID.
tempfile=`tempfile 2>/dev/null` || tempfile=/tmp/$me.$$

# make sure the tempfile is deleted when we're done
trap "rm -f $tempfile" 0 1 2 5 15

# define the window title, caption and size attributes
TITLE="SSH Menu"
CAPTION="\
You can use the UP/DOWN arrow keys and enter to select item."
W_HEIGHT=30
W_WIDTH=100
W_MENU_HEIGHT=25
}

a5_process_menu(){

${DIALOG:=Xdialog} --clear \
      --title "$TITLE" \
      --menu "$CAPTION" $W_HEIGHT $W_WIDTH $W_MENU_HEIGHT \
            "Home" "Home Server" \
            "sip1" "SIP Server" 2> $tempfile


case $? in
  0 )
    b55_process_selection
    ;;
  1 )
#   No or Cancel button was pressed
    break
    ;;
  2 )
#   Help button was pressed, if present
    break
    ;;
  3 )
#   Extra button was pressed, if present
    break
    ;;
  -1 )
#   errors occured, or exited via the ESC key
    break
    ;;
  * )
#   undefined return code
    break
    ;;
esac
}

#####################################################################
## process the menu selection
#
b55_process_selection(){

case `cat $tempfile` in
  "Home" )
    command="gnome-terminal -e /home/jake/.bin/homeserver"
    ;;
  "sip1" )
    command="gnome-terminal -e /home/jake/.bin/sip1"
    ;;
  * )
#   shouldn't get here, but break just in case (breaks the loop, actually :) )
    break
    ;;
esac

echo "Issuing command: $command"
$command

echo
echo -n " --- Hit ENTER to return to menu --- "
read
}

#####################################################################
## begin main processing here
#


a1_initialization

while true; do
  a5_process_menu
  break
done

exit 0


```

Thanks in advance!

---

### Post by DaithiF on 2009-09-22
when i try this on my 9.04 the xdialog outputs an error message about failing to load module libcanberra-gtk-module.so before it outputs the menu item that was selected.  if this is the same for you then your case statement won't match the output and no command will get executed.  how about commenting out your trap statement temporarily and inspecting your temp file after the fact to confirm if its the same for you.

as to fixing it, I would probably suggest you convert to using zenity rather than xdialog, but you may prefer to track down whatever dependency issue throws the xdialog error and fix that instead.

---

### Post by jakev383 on 2009-09-23
Well, I whacked something out in Zenity for now, but it's not ideal.
In checking on the bugs for the package, it seems that it is linked to a sound package for some reason (there's a thread in launchpad). Maybe a solution will appear soon. I may try compiling from source as well to see if that clears it up.
Thanks.

---

