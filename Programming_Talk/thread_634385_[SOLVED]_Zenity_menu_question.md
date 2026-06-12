---
title: "[SOLVED] Zenity menu question"
date: 2007-12-07
forum: Programming Talk
---

### Post by mdpalow on 2007-12-07
Hi Everyone,

I've got a shell script using Zenity.

I have a main menu using:

choice="$(zenity --width=585 --height=490 --list  --column "test"  \

After a menu option is selected and it does what it's suppose to do, it exits the script.

I added a 'bash Menu' to the end of a task so it brings up the menu again.

However, I have a menu within a menu and don't want to use the 'bash' command to bring up the MAIN menu, I want it to bring up the menu I was just in because there are other options in this menu that I may want to do.

The way it is right now, I perform an option and am then taken back to main menu where I have to then go back into the 2nd menu to do another task.

How can I have the second menu come up again when I'm finished doing one task, so I can do another task within that menu.

Sure hope this makes sense...

Thanks in advance..

---

### Post by geirha on 2007-12-07
I think I understand part of it, but it's hard to suggest anything without knowing what the code looks like. Could you post a small script showing the undesired behavior?

From what I think I understand though, it sounds like you want to have a while-loop showing the second zenity-list until a special "done" choice is selected? or perhaps you want to add --checklist or --multiple to the zenity-command so you can select several choices from that list?

---

### Post by mdpalow on 2007-12-07
Thanks for the reply.

I was thinking the same thing about having the ability to select multiple things at once that would be done.

However, right now I would like to see if I can get the original idea working and then look into that.

I've attached a test file you can use to see my dilemma .

Always have to go back to main menu. Would like to be able to stay in second menu until I want to leave.

Thanks..

EDIT::::   Ha, just saw it was you 'geirha' !!  That's good news for me. :)  Thanks for being there AGAIN...

---

### Post by geirha on 2007-12-07
I've added some while-loops to it which I think should give the desired results. "while true" is generally an infinite loop, but the keyword "break" will exit the loop.
```
#!/bin/bash

while true; do
  choice="$(zenity --width=200 --height=150 --list --column "" --title="test" \
  "Go to next menu" \
  "Exit ")"

  case "${choice}" in
    "Go to next menu" )
      while true; do
        choice2="$(zenity --width=200 --height=150 --list --column "" --title="test" \
        "Do Something" \
        "Do Something Else " \
        "Back")"

        case "${choice2}" in
          "Do Something" )
            echo "hello"
          ;;
          "Do Something Else " )
            echo "hello"
          ;;
          *)
            break
          ;;
        esac
      done
    ;;
    *)
      break
    ;;
  esac
done
```

Nice to be of assistance again, mdpalow :)

---

### Post by mdpalow on 2007-12-07
you know geirha... that couldn't have been a better answer! :)

My brain is a little tired from work and you providing the solution like that is a nice relief.

I'll start a direct deposit to your bank shortly. ;)

thanks very much...

---

### Post by inukaze on 2011-09-12
Thank you for Your Help , thanks to your script i completed one , with the follow lines :

```
#!/bin/bash

# Scripts for Japanese Support was Downloaded From : http://www.esdebian.org/foro/45378/how-tobeta-dojin-games-linux-koumajo-densetsu-bunny-must-dye-chelsea-and-the-seven-demons

# Go to the Game Directory
Game_Path=${0%/*}
cd "$Game_Path" && cd ..
export WINEPREFIX="$PWD/wine"
export WINEDEBUG="-all"
echo ""
echo ""
echo "If the Game dont start , you need Run $Game_Path/Linux_Japanese_Support.sh for Run Game Properly"

while true; do
  menu_launch="$(zenity  --width 309 --height 240 --list --radiolist  --column "Choose" --column "Option" TRUE "Play Game" FALSE "Launch Game Config" FALSE "Launch Controller Config" FALSE "Exit")"
         if [ "$menu_launch" = "Exit" ]; then
          echo done
          exit
         elif [ "$menu_launch" = "Play Game" ]; then
		`wine "Koumajou.exe" $@`
	 elif [ "$menu_launch" = "Launch Game Config" ]; then
		`wine "config.exe" $@`
	 elif [ "$menu_launch" = "Launch Controller Config" ]; then
		`wine "keyconfig.exe" $@`
         else
          clear
          echo Invalid option
         fi
done
```

Its for a Wine , to run With Wine , also as know : Tohouvania 1

---

