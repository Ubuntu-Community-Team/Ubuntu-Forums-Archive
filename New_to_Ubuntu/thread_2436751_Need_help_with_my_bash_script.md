---
title: "Need help with my bash script"
date: 2020-02-12
forum: New to Ubuntu
---

### Post by coley9225 on 2020-02-12
I'm new to linux so please keep that in mind. I'm trying to make a bash script to enable/disable my touchpad. I found some but they aren't working on my system, so I'm trying to modify to my them work on my machine. I know "synclient touchpadoff=1" will disable the touchpad( but not click for some reason), and of course "=0" will enable it. My bash script will work fine, turn on touchpad and return touchpad on message, but try to disable and it still enable touchpad and return touchpad on. What am I doing wrong.
My script:

#!/bin/bash

#Toggle touchpad on/off with keyboard input

echo "Do you want touchpad on?"
echo "Answer y or n"
    read answer
if answer=y
    then synclient touchpadoff=0
    echo "touchpad on"
else
     synclient touchpadoff=1
    echo "touchpad off"
fi

My only other option would be to mod the start up to disable at boot, then keyboard shortcut to terminal and enable touchpad if mouse fails or not available. The ultimate goal is to make a keyboard shortcut with onscreen output showing touchpad on or off, but thats a project for another day. Any help would be GREATLY appreciated. Thanks

---

### Post by kevdog on 2020-02-12
Hmmm not exactly the way I would write your script however consider this

```
#!/usr/bin/env bash

...
...
...
answer=${answer^^}
if [ ${answer} = 'Y' ]; then
   $(synclient touchpadoff=0)
   echo "Touchpad on"
else
    $(synclient touchpadoff = 1
    echo "Touchpad off"
fi
```

---

### Post by Holger_Gehrke on 2020-02-12
A bit of explanation: 
'if' executes a list of commands ending in a semicolon (and followed by 'then'). If that list succeeds (read: the last command returns an exit status of 0) the list after 'then' is executed otherwise a list after 'else' -  if one exists - will be. 
The 'answer=y' you have in your script is a simple assignment and will always succeed. Because of that, the code after 'then' always will be called. 
So you should be running 'test' (see 'man test') or '[' or use a conditional expression enclosed in '[[ ... ]]'. Also when doing a comparison you want to substitute the variable for its value by prefixing the variable name with a '$' (putting it in braces like kevdog does is not strictly necessary here, but there are situations where you need to do that and it doesn't hurt).
Since 'test' and '[' expect the expression to be made up of several separate words, there need to be spaces around the comparison operator (and after the '[' and before the ']' - I mention this because forgetting the spaces is my mistake of choice). 
The line 'answer=${answer^^}' in kevdog's script is what's called a 'Parameter Substitution'; this one will change the case of all letters in answer to upper case. Adding another line with the substitution 'answer=${answer:0:1}' will shorten answer to just its first character (so 'y', 'yes', 'yeah' and 'yup' would all work ...).

Holger

---

### Post by kevdog on 2020-02-12
> **Holger_Gehrke said:**
> A bit of explanation: 
'if' executes a list of commands ending in a semicolon (and followed by 'then'). If that list succeeds (read: the last command returns an exit status of 0) the list after 'then' is executed otherwise a list after 'else' -  if one exists - will be. 
The 'answer=y' you have in your script is a simple assignment and will always succeed. Because of that, the code after 'then' always will be called. 
So you should be running 'test' (see 'man test') or '[' or use a conditional expression enclosed in '[[ ... ]]'. Also when doing a comparison you want to substitute the variable for its value by prefixing the variable name with a '$' (putting it in braces like kevdog does is not strictly necessary here, but there are situations where you need to do that and it doesn't hurt).
Since 'test' and '[' expect the expression to be made up of several separate words, there need to be spaces around the comparison operator (and after the '[' and before the ']' - I mention this because forgetting the spaces is my mistake of choice). 
The line 'answer=${answer^^}' in kevdog's script is what's called a 'Parameter Substitution'; this one will change the case of all letters in answer to upper case. Adding another line with the substitution 'answer=${answer:0:1}' will shorten answer to just its first character (so 'y', 'yes', 'yeah' and 'yup' would all work ...).

Holger

Nice explanation.  I wish someone was as helpful with me when I was learning how to use shell scripts (and I'm still learning).

---

### Post by coley9225 on 2020-02-13
YEAH!! I had to fiddle with it a little, to get around a couple of error messages, but the script now works perfect. 

#!/bin/bash

#Toggle touchpad on/off with keyboard input

echo  "Do you want touchpad on?"
echo   "answer Y/N"
    read answer
     answer=${answer^^}
if  [[  ${answer} = 'Y' ]] ;
    then $(synclient touchpadoff=0)
    echo "touchpad on"
else
    $( synclient touchpadoff=1)
    echo "touchpad off"
fi
 I would like to thank kevdog for giving me the modified script, and holger_gehrke for the great explanation.  I hope to get explanations like that whenever I need help, as it not only gets my problem fixed, but also helps me understand and learn. If I wanted the easy way all the time I would look for GUI solution. I will mark the post solved. Thanks again for the quick response and the great help.

---

