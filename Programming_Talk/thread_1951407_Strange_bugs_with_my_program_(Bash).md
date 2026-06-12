---
title: "Strange bugs with my program (Bash)"
date: 2012-04-02
forum: Programming Talk
---

### Post by Gogeden on 2012-04-02
I'm having two strange bugs with my program I wrote in Bash. I'll start the program, call another script, then return to the first script and for some weird reason the first script will display the correct text but have the corresponding options (If I press 1 it'll do what ever 1 corresponds with in the previous script) of the previous script I launched. That's the first bug. The second is that I get this error when trying to launch script 2:

> ./misc/clean.sh: line 31: syntax error: unexpected end of file

I'm still learning Bash and I've been stumped on this problem for weeks. Here's the two scripts:

Script 1:

```
#!/bin/bash

clear



echo "GISAH on"; uname -o

# =============================================

function  clean_hdd {
    ./misc/clean.sh;
}

function self-clean {
    ./misc/self_clean.sh;
}

function  exit {
    break;
}

select choice in \
    "Clean Hard-disk" \
    "Self-Cleaning" \
    "Power Menu" \
    "Exit"
do
    case $choice in
        "Clean Hard-disk")
            clean_hdd;
            ;;
        "Self-Cleaning")
            self-clean;
            ;;
        "Power Menu")
            main_menu;
            ;;
        "Exit")
            break;
    exit
            ;;
        *)
            echo "Please select an option";
            ;;
    esac
done
```
========================================================
Script 2:
========================================================
```
#! /bin/bash

clear

function  firefox {
    echo "firefox";
}

function main {
    


select choice in \
    "Firefox" \
    "Main Menu"
    
do
    case $choice in
        "Firefox")
            rm -r ~/.mozilla/firefox/*.default/Cache/; 
    cd ~/.mozilla/firefox/*.default/;
    mkdir ./Cache;
            ;;
    "Main Menu")
    cd ~/Desktop/GISAH_BASH/;
    ./GISAH.sh
;;
    esac
done


```

Here's how to reproduce the bug, save and name that first script "GISAH.sh" (Name of my program) and then chmod +x it, then launch it. Press 1 to call the second script. You'll get that second error I mentioned. If anyone can fix that let me know I'd appreciate it. I had it fixed once but then I screwed something up while diagnosing the first problem I mentioned. Then, when that script gets launched, go back to the previous menu by pressing 2.

Really need the help. Thanks! :D

---

### Post by CynicRus on 2012-04-02
./misc/clean.sh: line 31: syntax error: unexpected end of file - You forgot to close the bracket-)

As for the rest - it is believed that the whole problem because - what do you use the script with the parameter 2. And your first script waits for the end of the second, because the management passed to him.

If you want to run scripts from the keyboard, I think - need to use &#1099;&#1075;&#1080;scripts invoked without a parameter, clearly defining their functionality.

---

### Post by ofnuts on 2012-04-02
There is not matching closing  brace for
```

function main {

```However, this is bash and not C, you don't define main, bash will run the code which is not inside a function definition..

---

### Post by Gogeden on 2012-04-03
> **CynicRus said:**
> ./misc/clean.sh: line 31: syntax error: unexpected end of file - You forgot to close the bracket-)

As for the rest - it is believed that the whole problem because - what do you use the script with the parameter 2. And your first script waits for the end of the second, because the management passed to him.

If you want to run scripts from the keyboard, I think - need to use &#1099;&#1075;&#1080;scripts invoked without a parameter, clearly defining their functionality.


Thanks for the help on the first problem to both of you :)

Now, would you happen to know of a way to stop that second script when I pull up the main menu? What is that bitnscripts? o_O Thanks :D

---

### Post by CynicRus on 2012-04-03
bitnscript - subscript-)

So, why you use 2 script? You can complete you task with 1 script. Bash have procedure, you can write some procedure, and call this procedure after key press. But, if you want use two scripts with parameter - do not use the same variables in two script.

---

### Post by Gogeden on 2012-04-05
> **CynicRus said:**
> bitnscript - subscript-)

So, why you use 2 script? You can complete you task with 1 script. Bash have procedure, you can write some procedure, and call this procedure after key press. But, if you want use two scripts with parameter - do not use the same variables in two script.

I carried the habit over from DOS Batch. I'm the author of the program GISAH and having multiple scripts like that helped with debugging ten-fold. I'll put it all in 1 and report back. Thanks! :)

Freedomftfw! :lolflag:

---

