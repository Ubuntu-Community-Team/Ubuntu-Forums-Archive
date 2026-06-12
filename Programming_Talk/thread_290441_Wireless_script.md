---
title: "Wireless script"
date: 2006-11-01
forum: Programming Talk
---

### Post by /carlito on 2006-11-01
Hi everyone,

Since i was having troubles using the gui configurations tools in edgy to connect to wireless networks, and since i've always looked for an excuse to practice my scripting skills, i've decided to write a small script to help me setup my connection. 

In my opinion there are still many things that could be improved in this script, so for that i call on you! Please advise me on how i could improve this script and how i can keep the code cleaner. 


This script is the very first one i've ever written, so please be gentle.

```
#!/bin/bash

INTERFACE=ra0  
ROOT_UID=0     # Only users with $UID 0 have root privileges.
E_NOTROOT=67   # Non-root exit error.

if [ "$UID" -ne "$ROOT_UID" ]
then
  echo "Run this script as root!"
  exit $E_NOTROOT
fi  

  echo
  echo "                **************************************"
  echo "                *** Scanning for Wireless Networks ***"
  echo "                **************************************"
  echo
iwlist $INTERFACE scan
  echo

OPTIONS="Rescan Connect Info Test End"
           select opt in $OPTIONS; do
               if [ "$opt" = "Connect" ]; then
                echo "Which network would you like to connect to?"
                read NW
                echo "Please enter the encription code for $NW. (ASCII)"
                read PW
                echo "What security mode yould you like to use fo $NW? (open/restricted/off)"
                read ENC
                iwconfig $INTERFACE essid $NW key s:$PW enc $ENC
                dhclient $INTERFACE
                iwconfig $INTERFACE
                ifconfig $INTERFACE
                ping -I $INTERFACE -c 4 google.be
                echo "Done!"
                exit
               elif [ "$opt" = "Rescan" ]; then
                echo
                echo "          ***************************"
                echo "          *** Rescanning Networks ***"
                echo "          ***************************"
                echo
                iwlist $INTERFACE scan
               elif [ "$opt" = "Info" ]; then
                echo
                iwconfig $INTERFACE
                ifconfig $INTERFACE
                echo
               elif [ "$opt" = "End" ]; then
                echo
                echo " Done!"
                exit
               elif [ "$opt" = "Test" ]; then
                ping -I $INTERFACE -c 4 google.be
               else
                echo "1) Rescan"
                echo "2) Connect"
                echo "3) Info"
                echo "4) Test"
                echo "5) End"
               fi
           done

```

---

