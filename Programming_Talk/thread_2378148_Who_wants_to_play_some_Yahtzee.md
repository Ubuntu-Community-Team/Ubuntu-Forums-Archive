---
title: "Who wants to play some Yahtzee?"
date: 2017-11-20
forum: Programming Talk
---

### Post by roxin25 on 2017-11-20
So im trying to create a program that rolls dice, trouble is, i dont know how to properly utilize my checklist output in my roll function. Example output: (1:2:4)

I know this is not the most efficent, proper, or even good looking way to write this- but I have only recently begun learning linux, but in this case, i want to leave this function with 5 varibles loaded into the die

Heres the function:

rolling()
{
#Initial Roll for random numbers 1-6
DIFF=$((6-1+1))
die1=$(($(($RANDOM%DIFF))+1))
[LEFT][COLOR=#222222][FONT=Verdana]die2=$(($(($RANDOM%DIFF))+1))[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]die3=$(($(($RANDOM%DIFF))+1))[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]die4=$(($(($RANDOM%DIFF))+1))[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]die5=$(($(($RANDOM%DIFF))+1))

#Select desired dice to keep
choice=$(zenity --height=250 --list --text "What dice would you like to keep?" 
--checklist --column "Keep?" --column "Dice" FALSE "die1" [LEFT][COLOR=#222222][FONT=Verdana]FALSE "die2"[/FONT][/COLOR][/LEFT]
 [LEFT][COLOR=#222222][FONT=Verdana]FALSE "die3"[/FONT][/COLOR][/LEFT]
 [LEFT][COLOR=#222222][FONT=Verdana]FALSE "die4"[/FONT][/COLOR][/LEFT]
 [LEFT][COLOR=#222222][FONT=Verdana]FALSE "die5"
--separator=":")
echo $choice

#Roll undesired dice again[/FONT][/COLOR][/LEFT]
[/FONT][/COLOR][/LEFT]

#Final roll

}

---

