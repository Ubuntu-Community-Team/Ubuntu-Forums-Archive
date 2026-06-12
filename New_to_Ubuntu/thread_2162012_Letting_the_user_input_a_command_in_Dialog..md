---
title: "Letting the user input a command in Dialog."
date: 2013-07-12
forum: New to Ubuntu
---

### Post by VonNnoV on 2013-07-12
Hi!
Im doing a project for class in which i have to create a menu system that does several things. Im using dialog so if anyone could help me in that format, twould be awesome.
For one of them I have to let the user schedule a task. So i guess it would go some things like:
Hi user, what command would you like to schedule?
(The user inputs a command here)
What time would you like that executed?
(User imputs a time here)
Command has been scheduled. Thank you.

Something like that... and thats for a one time job...
I also need one for a repeating job if possible.

This is what i have so far:

```
#!/bin/bash
# Store menu options selected by the user
INPUT=/tmp/menu.sh.$$
 
# Storage file for displaying cal and date command output
OUTPUT=/tmp/output.sh.$$
 
# get text editor or fall back to vi_editor
vi_editor=${EDITOR-vi}
 
# trap and delete temp files
trap "rm $OUTPUT; rm $INPUT; exit" SIGHUP SIGINT SIGTERM
 
#
# Purpose - display output using msgbox 
#  $1 -> set msgbox height
#  $2 -> set msgbox width
#  $3 -> set msgbox title
#
function display_output(){
    local h=${1-10}            # box height default 15
    local w=${2-41}         # box width default 41
    local t=${3-Output}     # box title 
    dialog --backtitle "Brought to you by Von Vanta" --title "${t}" --clear --msgbox "$(<$OUTPUT)" ${h} ${w}
}
#
# Purpose - display current system date & time
#
function show_date(){
    echo "Today is $(date) @ $(hostname -f)." >$OUTPUT
    display_output 6 60 "Date and Time"
}
#
# Purpose - display a calendar
#
function show_calendar(){
    cal >$OUTPUT
    display_output 13 25 "Calendar"
}
#
#Purpose Remove .gz
#
function Rmgz(){
    echo "You have just removed all .gz log files. $(rm *.gz)" >$OUTPUT
    display_output 5 45 "Remove .gz files. <Are you sure?>"
}
# Purpose - Schedule
##########################################
#


# Purpose - Schedule2
##########################################

#
# Purpose - Compare
##########################################

#
# Purpose - Find Largest file
function Large(){
    echo "The largest file in your system is currently 
    $(du -h | sort -n -r | tail -n 1)" >$OUTPUT
    display_output 15 50 "Largest file on your system. <That's a big file!>"
}

#
# Purpose - display Disk usage
#
function show_du(){
    echo "Your disc usage is $(du -h)" >$OUTPUT
    display_output 14 60 "Your disk usage..<Got enough?>"
}

#
# Print
#
function print(){
    echo "Here are the last 20 lines of the dmesg command. 
    $(dmesg |tail -n 20)" >$OUTPUT
    display_output 18 70 "Print: dmesg command....<You're welcome>"
}

######################################################################################
#Change Ownership of a file#
######################################################################################
function chown1(){
    echo "$(./chown1)" >$OUTPUT
    display_output 4 70 "The file you have selected has been chOWNED!"
}
##########################################################################################################
#
# set infinite loop
#
while true
do
 

### display main menu ###
dialog --clear  --help-button --backtitle "+++++++++++++++Welcome to my FinalProject+++++++++++++++" \
--title "[ The Main Menu.... Ahhhh Yeeeaaaaa.... ]" \
--menu "What do you want to do? (Can't move? Arrow keys smartass.)" 15 50 4 \
Date/time "Displays date and time" \
Calendar "Displays a calendar" \
Rmgz "Removes all .gz log files" \
Schedule "Schedule a one-time job" \
Schedule2 "Schedule a repeating job" \
Compare "Compares 2 files" \
Largest "Determines folder with Lgest usage" \
DiskSpace "Determines disk space available" \
Print "Print last 20 lines of the dmesg command" \
CHown "Change ownership of a file or directory" \
Exit "Exit to the shell" 2>"${INPUT}"
 
menuitem=$(<"${INPUT}")
 
 
# make decsion 
case $menuitem in
    Date/time) show_date;;
    Calendar) show_calendar;;
    Rmgz) Rmgz;;
    Schedule) echo;;
    Schedule2) echo;;
    Compare) echo;;
    Largest) Large;;
    DiskSpace)  show_du;;
    Print) print;;
    CHown) chown1;;
    Exit) echo "Thank you. Have a nice day!"; break;;
esac
 
done
 
# if temp files found, delete em
[ -f $OUTPUT ] && rm $OUTPUT
[ -f $INPUT ] && rm $INPUT
```

---

### Post by VonNnoV on 2013-07-17
im trying to create a script using dialog in which i have a menu box appear asking for a command from the user then take whatever that command is and then ask him for a time in which he wants the command executed.
ive trying to get this for days for all i get is a blue screen. i think somethings completely messed up with my script so something from scratch would help.
Thanks in advance!

---

### Post by coffeecat on 2013-07-18
Threads merged. Please do not post separate threads about the same question. This dilutes community effort.

Also, [please note]("http://ubuntuforums.org/showthread.php?t=2158945"): 

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. 

Since you have made a start, I'll leave the thread open, but please note that people will only be able to give you pointers, not write your code for you.

---

