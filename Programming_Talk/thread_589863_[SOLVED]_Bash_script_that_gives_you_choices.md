---
title: "[SOLVED] Bash script that gives you choices"
date: 2007-10-24
forum: Programming Talk
---

### Post by Walter_Crankite on 2007-10-24
I wrote a few scripts. Tiny ones but repeating tasks. 
I now have written a little script that lets me choose which script I want to run. 
I use the OPTIONS syntax that gives you choices. 
But you can only use one word to describe the option. 

OPTIONS="Perm Rsync"
can not be 
OPTIONS="Set correct permissions Rsyncing several folders"

Because that gives you 6 choices instead of 2. 
Is there another way to do this?
 

Script used: 

#!/bin/bash
#
OPTIONS="Perm Rsync"
select opt in $OPTIONS; do
     if [ "$opt" = "Perm" ]; then
     bash script1.sh
     exit
  
     elif [ "$opt" = "Rsync" ]; then
     bash script2.sh
     exit
 
     else
     echo bad option!
fi
done


Thx all,
Wouter
:-({|=

---

### Post by jharbert on 2007-11-09
The Linux command pages give good information on scripting.  I think this is what you're looking for.
[http://www.linuxcommand.org/wss0130.php]("http://www.linuxcommand.org/wss0130.php")

---

### Post by brad.m.sims on 2007-11-09
> **Walter_Crankite said:**
> 
Because that gives you 6 choices instead of 2. 
Is there another way to do this?


I cheat <G>

I do something like Options="Do_this_action Do_this_one_instead"

---

### Post by Walter_Crankite on 2007-11-20
thx guys

---

### Post by volanin on 2007-11-20
```
OPTIONS[1]="First Option"
OPTIONS[2]="Second Option"
OPTIONS[3]="Third Option"

select OPT in ${OPTIONS[@]}; do
...
```

---

### Post by Walter_Crankite on 2007-11-24
thx man
nice

---

### Post by Walter_Crankite on 2007-12-30
Thx to hxxp://grover.open2space.com/node/115
You can make the options as long as you want.

#!/bin/bash

showMenu () {
echo "1) bob"
echo "2) amy"
echo "3) quit"
}

while [ 1 ]
do
showMenu
read CHOICE
case "$CHOICE" in
"1")
echo "Bob was here"
;;
"2")
echo "Amy was here"
;;
"3")
exit
;;
esac
done

---

