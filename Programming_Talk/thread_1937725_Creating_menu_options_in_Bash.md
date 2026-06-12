---
title: "Creating menu options in Bash?"
date: 2012-03-08
forum: Programming Talk
---

### Post by Gogeden on 2012-03-08
Hello, I am the author of the program GISAH that's written in DOS Batch for Windows. My skills with Bash aren't as great as they are with Batch. I wanted to make a Bash version of GISAH for use on GNU/Linux, BSD, etc but one thing is holding me up: Menu choices

In Batch, I used set to forge these, like so:

@echo off

echo I. Analyze all volumes. 
echo II. Defrag Windows Drive 
echo A. Main Menu 
 
set choice= 
set /p choice=  
 
if not '%choice%'=='' set choice=%choice:~0,1% 
if '%choice%'=='1' goto :analyze 
if '%choice%'=='2' GOTO :defrag 
if '%choice%'=='a' GOTO :return 
if '%choice%'=='A' GOTO :return


See, I would first issue the @echo off to prevent the input lines from appearing when ran in the MS-DOS shell. Then use echo to print the available options. Then, in order to make those options function as such, use "set" to create the "choice" variable. I tried simply copying and pasting this into a .sh file and such but I got an error when I ran it in bash.

I've heard of many other commands such as select and case. But they confuse me. Thanks all :)

---

### Post by WthIteh on 2012-03-08
Welcome to the world of bash programming :)
Here is an example trying to do what you explained:

```

#!/bin/bash

function analyze_volumes {
    echo "analyze volume function";
}

function defrag {
    echo "defrag function";
}

function main_menu {
    echo "main menu function";
}

select choice in \
    "Analyze all volumes" \
    "Defrag Windows Drive" \
    "Main Menu" \
    "Exit"
do
    case $choice in
        "Analyze all volumes")
            analyze_volumes;
            ;;
        "Defrag Windows Drive")
            defrag;
            ;;
        "Main Menu")
            main_menu;
            ;;
        "Exit")
            break;
            ;;
        *)
            echo "Please select an option";
            ;;
    esac
done
echo "Finish!"

```You can define functions instead of plain use of goto calls.
You can use "select" with a list of space separated words to select an option.
You can use "case" to  match against patterns.

---

### Post by Gogeden on 2012-03-08
Very cool! I especially liked the sharp there at the end (#). Now I must figure out how to connect multiple scripts. Thanks! Appreciate it. :D

---

### Post by Gogeden on 2012-03-08
It also seems like I have more possibilities with those function commands. Me likey.

---

