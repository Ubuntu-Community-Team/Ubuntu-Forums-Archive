---
title: "Shell script with user interaction"
date: 2011-08-18
forum: Programming Talk
---

### Post by Majere79 on 2011-08-18
I am trying to get a program running that will present the user with a list of items in the shell window.  The user can then use the arrow up/down keys to select an item (denoted by highlighting) and then take an action when pressing the enter key.  I am a complete novice to programming so I don't know if this can even be done with a shell script.  If that is true, then please recommend alternatives.

---

### Post by Bachstelze on 2011-08-18
You need a real language like Python or C, and the ncurses library.

---

### Post by Majere79 on 2011-08-18
Alright, I will look into maybe using Python.  I will have to read some tutorials on it.

---

### Post by dethorpe on 2011-08-23
Not quite what you are after, but could consider the bash "select" built-in command to display a menu with numbers, user then type the number of the option they want and press enter to take the action.
 
e.g: can get something like this:
 
> 
[FONT=Arial][FONT=Arial]Select your terminal type:[/FONT]
[FONT=Arial]1) Givalt GL35a[/FONT]
[FONT=Arial]2) Tsoris T-2000[/FONT]
[FONT=Arial]3) Shande 531[/FONT]
[FONT=Arial]4) Vey VT99[/FONT]
[FONT=Arial]terminal?[/FONT]
[/FONT]
 
Can google for more info, example link: [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_06.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_06.html)

---

### Post by cgroza on 2011-08-23
Bash has a " select in " construct: 

```

select $opt in "Opt1" "Opt2"
do

echo $opt

done


```

---

### Post by bumble-b on 2011-08-23
You can try *dialog* program. [http://linuxgazette.net/101/sunil.html](http://linuxgazette.net/101/sunil.html)

---

### Post by Habitual on 2011-08-23
This is a snippet from another c-li program I wrote.
CAUTION: This needs help but does present a dialog of sorts to the user to select one of the terminals you showed us.

```

menu_items=(
    "Givalt GL35a" "Tsoris T-2000" "Shande 531" "Vey VT99" "Other"
    )
 
PS3="Select Terminal:"
select s in "${menu_items[@]}"; do
    if [[ -z "$s" ]]
    then
        echo "Option $REPLY is invalid - Please select a number from 1 to ${#menu_items[@]}"
    else
        terminal_selection=${items_period[$REPLY-1]}
        break
    fi
done
launch terminal program here ...  "$terminal_selection" ...
exit 0

```

---

### Post by JupiterV2 on 2011-08-23
I think what you might want is [zenity]("http://library.gnome.org/users/zenity/stable/"). Zenity pops up GTK+ styled dialogues from a bash script for user interaction. You'd probably be interested the list dialog.

---

### Post by Habitual on 2011-08-23
or yad. :)

---

