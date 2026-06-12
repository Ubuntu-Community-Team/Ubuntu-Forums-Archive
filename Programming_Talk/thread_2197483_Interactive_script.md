---
title: "Interactive script"
date: 2014-01-04
forum: Programming Talk
---

### Post by vasa1 on 2014-01-04
I have this script, *~/bin/inter-alarm*:

```
#!/usr/bin/env bash

# My first attempt at an interactive alarm

echo "Type in after how many minutes or seconds you want the alarm to sound"

read my_time

sleep "$my_time";

COUNTER=0
    while [ $COUNTER -lt 5 ]; do
       mplayer -really-quiet /usr/share/sounds/freedesktop/stereo/complete.oga
          let COUNTER=COUNTER+1 
    done


```

To run it, I need to 
[LIST]
[*]open a terminal 
[*]specify the time, for example, **15s** 
[*]press enter and 
[*]leave the terminal open till the script completes.
[/LIST]

What I want, but don't know how to do, is this: I want the script to open the terminal by itself (when I double-click the script in my file manager), accept the time I specify and then close the terminal but leave the script running. Is that possible?

---

### Post by DaviesX on 2014-01-04
> I want the script to open the terminal by itself (when I double-click the script in my file manager)
No, I don't think so.

> close the terminal but leave the script running
Yes, linux is multitask. You can change you script to read command parameters instead of asking from stdin. This way you can run your script and send it to background by adding & after the command

---

### Post by trent.josephsen on 2014-01-04
Opening a terminal to get user input is doable, but unnecessarily complicated.

**zenity** is a program designed for doing just this kind of thing. It provides several dialogs that can be used in shell scripts. It is probably already installed. Try replacing "read my_time" with
```
my_time=$(zenity --entry --text="Enter the duration of the alarm:")
```

---

### Post by vasa1 on 2014-01-04
Brilliant. Thank you!

---

