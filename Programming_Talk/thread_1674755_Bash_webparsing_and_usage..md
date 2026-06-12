---
title: "Bash webparsing and usage."
date: 2011-01-24
forum: Programming Talk
---

### Post by Gosujii-sama on 2011-01-24
I'm relatively new to the bash/web stuff dealing with it from bash. I fully understand socket protocol and web protocol and programing just not bash itself.

Program rundown: basically im creating a bash/sh file to recompile Ghost++ copy it to a directory and NOW i want to add a automatic download for a map file it uses called "DotA" which is commonly known to those that use it.

So far looks like this:

```

#!/bin/bash

ghostdir="/home/*****/ghost/"
ghostmappath=$ghostdir"maps/"
dotacfg=$ghostdir"mapcfgs/dota.cfg"
site="http://www.getdota.com/"
war3mappath="/home/*****/.wine/drive_c/Program Files/Warcraft III/Maps/Download/"

function get_dota {
  wget $site"index.php"
  while read line   
  do   
    if [[ $line == *input_file_name2* ]]; then
      newestdota=$(expr "$line" : '<input type="hidden" name="file_name" value="\([^_]*\)" id="input_file_name2"/>')
    fi
  done <index.php
  sudo rm index.php

  if [ ! -f "$ghostmappath$newestdota" ]; then
    cd $ghostmappath
    echo -n "Downloading new DotA map..."
    wget $site$newestdota
    if [ ! -f "$war3mappath$newestdota" ]; then 
      sudo cp $newestdota $war3mappath$newestdota 
    fi
    echo "Complete!"
    echo -n "Writing cfg file..."
    sudo rm $dotacfg
    echo "map_path = maps\\download\\"$newestdota >> $dotacfg
    echo "map_localpath = "$newestdota >> $dotacfg
    echo "map_type = w3mmd" >> $dotacfg
    echo "map_statsw3mmdcategory = *****" >> $dotacfg
    echo "map_matchmakingcategory = dota_elo" >> $dotacfg
    echo "map_defaulthcl = aremso" >> $dotacfg
    echo "map_defaultplayerscore =" >> $dotacfg
    echo "map_loadingame = 1" >> $dotacfg
    echo "map_observers = 1" >> $dotacfg
    echo "map_speed = 3" >> $dotacfg
    echo "map_visibility = 4" >> $dotacfg
    echo "map_flags = 3" >> $dotacfg
    echo "map_gametype = 1" >> $dotacfg
    echo "Complete!"
  else  
    echo "Dota is up to date!"
  fi
  echo "All DotA maps up to date."
}

function compile_ghost {
  cd $ghostdir
  sudo rm ghost++
  echo "Entering: $ghostdir"
  cd $ghostdir"ghost/"
  if [ -f ghost++ ]; then
    echo "GHost++ Already compiled...removing for rebuild"
    sudo rm ghost++
  fi
  echo "Compiling GHost++"
  make
  echo "Copying new ghost++ to $ghostdir..."
  sudo cp "ghost++" $ghostdir"ghost++"
  cd $ghostdir
  if [ -f ghost++ ]; then
    echo "-Completed Recompile-"
  else
    echo "ERROR: Compilation had an error try again or check files dude!"
    exit
  fi
  cd ~/Desktop
}

function run_ghost {
  compile_ghost
  get_dota
  cd $ghostdir
  ./ghost++
}

while : do
  clear
  echo "Commands: "
  echo "  ghost  cghost  dota  war3"
  echo "  quit"
  echo -n "Jabberwock~> "
  read text
  case $text in
    ghost) run_ghost;;
    war3) ~/wine-war3/wine "C:\Program Files\Warcraft III\Frozen Throne.exe";;
    dota) get_dota;;
    cghost) compile_ghost;;
    quit) break;;
    *) break;;
  esac
done

```

also i know i dont know bash well as everyone else :P so fill in your ideas too if u want. im sure others would benifit from such a script.

if someone knows a way to open a new terminal window and run another cmd in it lemme know im lookin for that now.

---

