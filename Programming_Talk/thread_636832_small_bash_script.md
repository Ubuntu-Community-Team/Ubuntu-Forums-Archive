---
title: "small bash script"
date: 2007-12-10
forum: Programming Talk
---

### Post by tashe on 2007-12-10
I need to make a bash script that displays the process name and PID (probably with **ps -o pid,command**) and then store it in a menu
( like **switch-case**). 
In the end the user to choose a number form the menu and the sript to kill the process corresponding to that number in the menu.
I'm confused how to store the command name and PID in a menu and then kill it? I you're kind enough to help me out here  :)
thanks in advance

---

### Post by lvleph on 2007-12-10
Sounds like you are trying to rebuild the top command? Try top in the terminal and see if that is what you were looking for.

---

### Post by geirha on 2007-12-10
A quick and dirty way of doing it with sed and zenity, for the sake of bash scripting:
```
pid=`ps -o pid= -o command= | sed 's/^ *\([0-9]\+\) \(.*\)/\1\n\2/' | zenity --list --column="PID" --column="Command"`
[ "$pid" != "" ] && kill $pid

```

---

### Post by ghostdog74 on 2007-12-10
```

linenum=1
array=
ps -o pid,command | while read line ;
do
    echo "$linenum) $line"
    set -- $line
    echo "$1"
    array[$linenum]=$1
    echo ${array[$linenum]}
    linenum=$(( linenum + 1 ))
done
set --
echo "enter number of the process to kill"
read choice
echo "choice : $choice"
......
#construct kill statement here

```

---

