---
title: "calling a bash script from quicklist"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-03-07
Hi Everyone,

I have been using [todo.txt ]("http://todotxt.com/")a command line script to write todo lists. 
I'd like to have a launcher in the dock like thing Ubuntu has on the side,so that I can click the icon and have the terminal popup showing the to do list.

Usually, I can do this in the terminal by typing t (the alias to call the script) and typing ls - then I see the list.

I thought it would be cool to just click an icon in the dock thing and have that happen automatically.

I've got the quicklist and I can get it to call a script that almost works.

The problem is that about a nano-second after showing me the list of things I need to do, the terminal window disappears.  Does anyone know how I can make it stay open until I close it?

The script I'm using is very simple:
 
```
#!/bin/bash
terminal 
~/scripts/todo.sh ls 
``` 

Any ideas?
I'd really appreciate some guidance.  This is bugging me :-)

---

### Post by Lisiano on 2013-03-07
The problem is that by default, after a script finishes executing, the terminal will close as there is nothing else to input or output.
One way to stop this behaviour is to modify the Defaul profile in your terminal, for Ubuntu, right-click in the terminal -> Profiles -> Profile Preferences -> When command exits: -> Hold the terminal open. This might not be a good method if you have a habit of exiting terminals by typing exit, as they will no longer close.
Another way is to put this at the very end of the script ```
read -s -n 1
```This will make Bash wait until you press any key before continuing or in this case &#8212; exiting.

---

### Post by GrouchyGaijin on 2013-03-07
Hey thanks!  I really appreciate the help.

As long as I've got your attention, I'd like to ask a couple of follow up questions. :-)

```
#!/bin/bashterminal 
~/scripts/todo.sh ls
read -s -n 1
```

Works pretty well except when it launches at first a terminal window appears with an error message that I can't read because that terminal window closes almost immediately and a second window showing my to do list opens up.

Question 1:  Do you know how I can stop that first terminal window from appearing?
 
Question 2: Is there a way to just keep my to do list window open so that I can issue a command to add a new item to the list, instead of having it close when I press any key?

---

### Post by Lisiano on 2013-03-07
1) Try the first method, it should stop the first one from closing, you can revert the change later.
2) Replace 'read -s -n 1' with 'bash'. This will simply start a new shell.

---

### Post by schragge on 2013-03-07
```
#!/bin/bash
[COLOR=red]terminal [/COLOR]
~/scripts/todo.sh ls
read -s -n 1
```
Sorry, but what does [COLOR=red]the second line[/COLOR] do? Opens an empty terminal window? Why?

---

### Post by GrouchyGaijin on 2013-03-07
> **schragge said:**
> ```
#!/bin/bash
[COLOR=red]terminal [/COLOR]
~/scripts/todo.sh ls
read -s -n 1
```
Sorry, but what does [COLOR=red]the second line[/COLOR] do? Opens an empty terminal window? Why?

Apology accepted.

I'm guessing you realized that terminal isn't needed.
I realized that as well after I ran the script and got an error referencing line two.

I don't know very much about writing scripts and thought that I may need to specifically say somewhere that I want this  to happen in a terminal.  Obviously I was mistaken.

---

### Post by GrouchyGaijin on 2013-03-07
> **Lisiano said:**
> 1) Try the first method, it should stop the first one from closing, you can revert the change later.
2) Replace 'read -s -n 1' with 'bash'. This will simply start a new shell.

Actually, that didn't stop the first window from appearing.
Tip #2 does let me type a command in the same terminal window though. :-)

---

### Post by GrouchyGaijin on 2013-03-07
OK - I got it doing what I wanted.

Here is the ultra basic script that is called from the quicklist.

```
#!/bin/bash~/scripts/todo.sh ls
bash
```

and here is the quicklist

```
[Desktop Entry]Version=1.0
Type=Application
**[COLOR=#ff0000]Terminal=false[/COLOR]**
Exec=gnome-terminal -x /home/grouchygaijin/scripts/todo-list
Name=ToDo.txt
Icon=/home/grouchygaijin/Launcher-Images/todotxt_logo_2012.png
Keywords=Terminal App 
```

In the quicklist the Terminal had been set to TRUE.  I changed that to FALSE and the double terminal window problem stopped.

---

