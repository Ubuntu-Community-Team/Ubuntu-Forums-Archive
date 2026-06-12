---
title: "shell script question"
date: 2010-05-04
forum: Programming Talk
---

### Post by deankovell on 2010-05-04
Edit: I solved the problem. check out the second post if you want to see a sweet script to raise all windows belonging to a program.


This script works, but I'm getting an error that seem bogus. 
```
 rm: cannot remove `/home/mark/scripts/hotkeys/hydrogen/hydrogen.tmp': No such file or directory

``` I'm curious about the error showing up when the file is actually getting deleted as it's suppose to. and  Any other suggestions to clean it up or improve it are welcome; This is my first script that's more that one simple command. 
Anyway,  the point of the script is to start a program with a hotkey and then if the program's already running,  pressing the hot key again raises all windows  belonging to that program to the front. 
```
#!/bin/bash
#This script depends on wmctrl

#Place the name of the program to be controlled after PROGRAM= 
#The second entry should be different only if pidof needs something different than the
#command to start the program 
readonly -p PROGRAM=hydrogen
readonly -p PROGRAMPIDNAME=hydrogen

# got these nexttwo lines from here : http://forums.macosxhints.com/showthread.php?t=73839
# They're suppose to make sure the created files get made in the correct directory
abspath="$(cd "${0%/*}" 2>/dev/null; echo "$PWD"/"${0##*/}")"
path_only=`dirname "$abspath"`

#this line checks if jack's running
if [ "$(pidof jackd)" ] 
then 
    #This line checks if the Program's already running
    if [ "$(pidof $PROGRAMPIDNAME)" ]
    then 
            #This section finds all windows belonging to my program
        # and creates a list of their numerical window ids
        pidof $PROGRAMPIDNAME | perl -pe 's/\s+/\n/g' > $path_only/$PROGRAM.tmp &&
        LIST="$(cat $path_only/$PROGRAM.tmp)"
        wmctrl -lp | grep "$LIST" | perl -pe 's/\s+/\n/g' | grep 0x  > $path_only/$PROGRAM.tmp
        LIST="$(cat $path_only/$PROGRAM.tmp)"
        #This section raises the windows belonging to my program
        for x in $LIST; do
            wmctrl -ia $x &&
            rm $path_only/$PROGRAM.tmp
            done
    else
          $PROGRAM
    
    fi
#This checks to see if the program is already running; if it is then it will go
# ahead and raise the windows belonging to it otherwise exit the script
else    
    if [ "$(pidof $PROGRAMPIDNAME)" ]
      then 
            #This section isolates all windows belonging to my program and raises them
        pidof $PROGRAMPIDNAME | perl -pe 's/\s+/\n/g' > $path_only/$PROGRAM.tmp &&
        LIST="$(cat $path_only/$PROGRAM.tmp)"
        wmctrl -lp | grep "$LIST" | perl -pe 's/\s+/\n/g' | grep 0x  > $path_only/$PROGRAM.tmp
        LIST="$(cat $path_only/$PROGRAM.tmp)"
        #This section raises the windows belonging to my program
        for x in $LIST; do
            wmctrl -ia $x &&
            rm $path_only/$PROGRAM.tmp
            done
    else
      exit
    fi
fi
exit
```

---

### Post by deankovell on 2010-05-04
I redid it much more sensibly, and I'm kinda proud of it, so I'm gonna share the better version. it's for using a hotkey to launch a program, and then raise all of its windows if it's already running. I wrote it for audio programs and it checks to see if jackd is running before it will let you launch the program, but it will still raise the windows if the program's already running but jackd isn't. 

 suggestions for adapting this to another script  for using a hot key combination to cycle through one programs windows like alt-tab does would be much appreciated; it's what I'm working on next.
```

#!/bin/bash
readonly -p PROGRAM=hydrogen
readonly -p PROGRAMPIDNAME=hydrogen
PIDSTUFF=`pidof $PROGRAMPIDNAME | perl -pe 's/\s+/\n/g'`
LIST=`wmctrl -lp | grep $PIDSTUFF | perl -pe 's/\s+/\n/g' | grep 0x`
if [ "$(pidof jackd)" ] 
then 
    if [ "$(pidof $PROGRAMPIDNAME)" ]
    then 
    for x in $LIST; do
        wmctrl -ia $x 
    done
    else
          $PROGRAM
    fi
else    
    if [ "$(pidof $PROGRAMPIDNAME)" ]
      then
      for x in $LIST; do
        wmctrl -ia $x 
    done
    else
      exit
    fi
fi
exit
```

---

