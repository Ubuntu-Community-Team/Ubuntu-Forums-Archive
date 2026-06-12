---
title: "KDE Wallpaper Scripting?"
date: 2013-04-26
forum: Programming Talk
---

### Post by LoREZ on 2013-04-26
This script randomizes wallpapers on various DEs, but the one thing I can't figure out is how to manipulate the **KDE4** wallpaper.  KDE has no commandline tool for this, but I've seen where one of the developers added the ability for KDE to refresh the wallpaper if the wallpaper image is overwritten.  

What I want to know is exactly where that specific image is stored.  I don't mean the directory *all* of the wallpapers are stored in collectively, but whether KDE is just looking where the original image was found, or if (like Windows) it copies the applied image to a different location with a different name.  They don't make it easy, and all the solutions I've found are cumbersome, when they work at all.  Google and kde.org seem to be dead ends.

[PHP]#!/bin/bash

#!/bin/bash

#rWall was written by Ike Davis (c) 2013, and is licensed under GPL v2.0.
#I hereby poke all users with the "NO warranty, real or implied" stick.
#This script selects a random image from a directory and applies it as a 
#background. It is designed for use with GNOME or Openbox.
#This script requires Feh for use with Openbox.

#declaring variables so users can see what the script involves
declare VERSION      #v1.0 "Homer", v1.5 "Bart", v1.8 "Lisa", v2.0 "Krusty"
declare BGDIR          #result of wallpaper commandline argument test
declare WALLPAPER   #result of randomized image selection
declare INTERVAL      #number of loops
declare SPEED          #loop speed
declare DEFAULT       #default desktop environment
declare USERDIR       #default image directory

VERSION="v2.0 \"Krusty\" (c) 2013, by Ike Davis"

#change this directory to the desired image directory
USERDIR=$HOME/path/to/primary/Wallpapers

#set alternate image directories below, then use option "-d1" or "-d2"
set_d1() {
  BGDIR=$HOME/path/to/secondary/Wallpapers
}

set_d2() {
  BGDIR=$HOME/path/to/tertiary/Wallpapers
}

#options are "set_openbox", "set_gnome2", and "set_gnome3"
DEFAULT=set_gnome3

cd /

#SET DEFAULT DIRECTORY
if [[ -d "$2" ]]; then
    BGDIR="$2"
  elif [[ -d "$1" ]]; then
    BGDIR="$1"
  else
    BGDIR="$USERDIR"
fi



#randomize wallpaper list and select one image.  The point of the script. 
#Alternate method: "$(find ~/Wallpapers -type f | shuf -n1)" or -name "*.jp*g"
random_sort() {
  WALLPAPER=$(find "$BGDIR" -type f -iregex ".*\.\(jpg\|png\|jpeg\)$" \
  | sort --random-sort | head --lines=1)
}

random_sort

#DESKTOP ENVIRONMENT CALLS
set_openbox() {
  #feh --bg-center "$WALLPAPER"
  #feh --bg-scale "$WALLPAPER"
  feh --bg-max "$WALLPAPER"
  #feh --bg-tile "$WALLPAPER"
}

set_gnome2() {
  gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$WALLPAPER"

  #gnome2 options; "none", "wallpaper" (tiled), "centered", "scaled", "stretched"
  gconftool-2 -t str --set /desktop/gnome/background/picture_options "wallpaper"
}

set_gnome3() {
  gsettings set org.gnome.desktop.background picture-uri file://"$WALLPAPER"
}

#HELP
usage() {
  echo " rwall [-h -v -m -ob -g2 -g3 -l] | IMAGE DIRECTORY"
  echo
  echo " --help .................. prints this help"
  echo " -h ...................... prints short help"
  echo " --version, -v ........... prints version number"
  echo " --menu, -m .............. displays an interactive menu"
  echo " --openbox, -ob .......... writes openbox wallpaper (uses Feh)"
  echo " --gnome2, -g2 ........... writes gnome2 wallpaper"
  echo " --gnome3, -g3 ........... writes gnome3 wallpaper"
  echo " --loop, -l .............. loops default desktop environment background"
  echo " --ob-loop, -obl ......... loops openbox background"
  echo " --g2-loop, -g2l ......... loops gnome2 background"
  echo " --g3-loop, -g3l ......... loops gnome3 background"
  echo " --alt-dir1, -d1 ......... use first alternate image directory"
  echo " --alt-dir2, -d2 ......... use second alternate image directory"
  echo
}

#LOOP WALLPAPER
loop() {
  printf "Enter the number of loops, or press Enter for a continuous loop: " 
  read INTERVAL
  printf "How fast should the background swap (in seconds)?: " 
  read SPEED
  echo
  
  #default background swap speed
  if [[ -z $SPEED ]]; then
    SPEED=3
  fi

  if [[ -z $INTERVAL ]]; then
    echo "Press Ctrl+C to cancel the loop."
    echo
    while [[ true ]]; do
      random_sort
      $DEFAULT
      sleep $SPEED
    done
  else
    echo "You have chosen to loop the background $INTERVAL times."
    echo "Press Ctrl+C to cancel the loop, or wait for the count to reach 0."
    echo
    echo "$(($INTERVAL - 1)) changes left."; echo
    while [[ $INTERVAL > 0 ]]; do
      random_sort
      $DEFAULT
      sleep $SPEED
      let --INTERVAL
      if [[ $INTERVAL > 1 ]]; then
        echo "$(($INTERVAL - 1)) changes left."; echo
      elif [[ $INTERVAL == 1 ]]; then
        echo "Last change complete."; echo
      else
        echo "There are no changes left. Goodbye."; echo; exit 0
      fi
    done
  fi
}

loop_openbox() {
  if [[ $DEFAULT != set_openbox ]]; then 
    $DEFAULT=set_openbox
  fi
  loop
}

loop_gnome2() {
  if [[ $DEFAULT != set_gnome2 ]]; then 
    $DEFAULT=set_gnome2
  fi
  loop
}

loop_gnome3() {
  if [[ $DEFAULT != set_gnome3 ]]; then 
    $DEFAULT=set_gnome3
  fi
  loop
}

#MENU
menu() {
  echo "Thank you for using rWall! Please choose an option."
  echo
  # add menu items here
  SELECTION="Gnome2 Gnome3 Openbox loop randomize help quit"

  select options in $SELECTION; do
    random_sort
    # each condition matches on menu item
    if [ "$options" = "Gnome2" ]; then
        echo "You have chosen $options."
        set_gnome2

    elif [ "$options" = "Gnome3" ]; then
        echo "You have chosen $options."
        set_gnome3

    elif [ "$options" = "Openbox" ]; then
        echo "You have chosen $options."
        set_openbox

    elif [ "$options" = "loop" ]; then
        echo "You have chosen $options."
        loop

    elif [ "$options" = "randomize" ]; then
        echo "You have chosen $options."
        random_sort

    elif [ "$options" = "help" ]; then
        echo "You have chosen $options."
        echo
        usage
        
    elif [ "$options" = "quit" ]; then
        echo "You have chosen to $options."
        echo
        exit 0
    else
        clear;
        echo "Please choose a valid option."
    fi
  done
}


#COMMANDLINE OPTIONS
if [[ -d $2 ]] || [[ -z $2 ]]; then
  case $1 in 
    "-h"                 ) echo "rwall [-h -v -m -ob -g2 -g3 -l] | IMAGE DIRECTORY";;
    "--help"             ) usage;;
    "--version" | "-v"   ) echo "$VERSION";;
    "--gnome2" | "-g2"   ) set_gnome2;;
    "--gnome3" | "-g3"   ) set_gnome3;;
    "--openbox" | "-ob"  ) set_openbox;;
    "--menu" | "-m"      ) menu;;
    "--loop" | "-l"      ) loop;;
    "--ob-loop" | "-obl" ) loop_openbox;;
    "--g2-loop" | "-g2l" ) loop_gnome2;;
    "--g3-loop" | "-g3l" ) loop_gnome3;;
    "--alt-dir1" | "-d1" ) set_d1 ; random_sort ; $DEFAULT;;
    "--alt-dir2" | "-d2" ) set_d2 ; random_sort ; $DEFAULT;;
    "$BGDIR"             ) $DEFAULT;;
    ""                   ) $DEFAULT;;
    "--redpill"          ) echo "Why oh why didn't I take the BLUE pill?";;
    "--bluepill"         ) echo "Never send a human to do a machine's job.";;
    *                    ) echo "\"$1\" is invalid. Type \"rwall --help.\""
  esac
else
  echo "You entered an invalid option.  Type \"rwall --help\" for help."
fi

exit 0[/PHP]

---

### Post by LoREZ on 2013-04-27
Bump. :)

---

