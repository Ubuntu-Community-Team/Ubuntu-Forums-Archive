---
title: "issue with startup command"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by hookitup on 2012-05-18
so i want to run a command when i log in, just to make my life easer, 
i am trying to make guake open 6 new tabs, i know to open a new tab i just type ```
guake --new-tab=1
```
or hit shift-ctrl-t
but i much rather have it automated, 
i put the above command in the "startup application" to see if it would work and it didn't, i tried to make a file in gedit containing ```
guake --new-tab=1

guake --new-tab=1

guake --new-tab=1

guake --new-tab=1

guake --new-tab=1

guake --new-tab=1
```

and place it in startup application, still no luck, i tried that file but with .sh as the file extension and make it executable, still no luck, what can i do to make this work?

---

### Post by anewguy on 2012-05-18
Post back what startup file you are talking about and it's contents.

Also, I know squat about Quake, but since it allows new-tab=1, can you put in something like new-tab=6 and get 6 tabs??

---

### Post by hookitup on 2012-05-18
nahhh the =6 doesnt work and the only thing in my startup applications is guake program, which just starts the program so its available, but i would like to have it run a script or something that after guake is open it opens 6 more tabs, but there is no option for this under preference, so if i run ```
guake --new-tab=1
``` in terminal then it opens a new tab, how can i automate this command to run after guake has ran from startup applications



Thanks.

---

### Post by anewguy on 2012-05-20
Perhaps you should write a simple shell script, something like:

gedit test.sh

Put these lines in the file:

$!/bin/bash
$ guake --new-tab=1
$ guake --new-tab=1
$ guake --new-tab=1
$ guake --new-tab=1
$ guake --new-tab=1
$ guake --new-tab=1

Save the file.

Using "places", right-click and set the file to executable.

Then try this at a terminal:

./test.sh


If that works we can add it to your user startup.

EDIT:  I was able to run the script with no problem - I just don't have Quake so I couldn't test it.  I tried installing Quake (I thought it used to be free years ago, but maybe I'm thinking of a different game) but I have to get a CD from somewhere in order to install data it apparently wants.


Dave ;)

---

### Post by stinkeye on 2012-05-20
Linking this script as the startup command in unity 12.04 works for me.
It needs the first sleep command otherwise it loads before compiz
and I get multiple instances of the indicator icon.
The **cd $HOME** is needed otherwise the terminals open in the directory 
where the script is saved.
The last command, **guake -s0 &**, puts the focus back to the first tab.
```
#!/bin/bash

cd $HOME
sleep 15
guake -n1 &
sleep 3
guake -n1 &
guake -n1 &
guake -n1 &
guake -n1 &
sleep 1
guake -s0 &
```

---

### Post by hookitup on 2012-05-27
thanks for all the replies, i fixed it by doing```
sleep 10; guake --new-tab=1
```

---

