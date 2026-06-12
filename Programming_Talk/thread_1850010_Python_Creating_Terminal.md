---
title: "Python Creating Terminal"
date: 2011-09-25
forum: Programming Talk
---

### Post by possumkeys on 2011-09-25
[FONT=Georgia]                  I have a script that uses the curses library functions to modify the looks of the gnome-terminal and it is working okay. However, all the scripts required to do this are supposed to be run by the user on a terminal he has created himself so that the terminal is modified.
                  However, I want to create a script that creates its own instance of a terminal, prints stuff to it, and modifies it, without making Ubuntu run the script as "application in terminal".
Any help?
Thanks.  :D
[/FONT]

---

### Post by MG&amp;TL on 2011-09-25
I suppose you could get it to launch its own terminal, in Python I guess that would be something like:

```
import os

os.system("gnome-terminal")
//Customization code goes here.
```

---

### Post by cgroza on 2011-09-25
> **MG&TL said:**
> I suppose you could get it to launch its own terminal, in Python I guess that would be something like:

```
import os

os.system("gnome-terminal")
//Customization code goes here.
```
That won't work. The script will wait until gnome-terminal exits and then it will carry on.
The only way I can think of is to put your script in the .bashrc or similar that is executed when gnome-terminal starts.

---

### Post by MG&amp;TL on 2011-09-25
You could have a look at the way terminator does it:

[https://launchpad.net/terminator]("https://launchpad.net/terminator")

---

### Post by MG&amp;TL on 2011-09-25
I'm not entirely sure if it would work, but I guess you could modify my previous suggestion to :

```
import os

os.system("gnome-terminal &")
```

To run it in the background and thus allow modifications. Not tested.

---

### Post by possumkeys on 2011-09-26
Well, I tried this but it doesn't seem to type to the terminal brought up despite my having its file descriptor. Please check out the code below and help out.
```

#!/usr/bin/env python
import os,sys,subprocess
#start new terminal
proc=subprocess.Popen('gnome-terminal')
#wait till terminal is set up
proc.wait()
#get list of terminals current running
current_terminals=os.listdir('/dev/pts/')
print current_terminals
#get new list of terminals and compare to find which terminal is new
new_terminals=os.listdir('/dev/pts')
for i in new_terminals:
    for y in current_terminals:
        if i==y:
            term=i
print term
fd=open(term,'wr')
fd.write('x\n')

```

---

### Post by MG&amp;TL on 2011-09-26
I did say I hadn't tested it.

Errr...shouldn't the 'get terminals currently running' go BEFORE you open the intended terminal? That way, you would get the right one, right?

---

### Post by possumkeys on 2011-09-26
[FONT=Verdana]```
import os,sys,subprocess,time
#get list of terminals current running
current_terminals=os.listdir('/dev/pts/')
print current_terminals
#start new terminal
proc=subprocess.Popen(['gnome-terminal'])
#wait till terminal is set up
#--------> though i dont really know why proc.wait() doesnt work. Any clue?
time.sleep(1)
#get new list of terminals and compare to find which terminal is new
new_terminals=os.listdir('/dev/pts')
for i in new_terminals:
    if i not in current_terminals:
        term=os.path.join('/dev/pts',i)
fd=open(term,'wr')
x=0
while x<1000000:
    fd.write('This sentence has x as {0}\n'.format(x))
    x=x+1
fd.close()

  
 

```This piece of code actually ran thanks to corrections by [/FONT]MG&TL. Thanks A lot Guys.
Really appreciate it. :D

---

