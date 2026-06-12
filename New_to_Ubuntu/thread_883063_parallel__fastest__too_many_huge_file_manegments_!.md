---
title: "parallel??  fastest???  too many /huge file manegments !!!!!"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by just_linux on 2008-08-07
I have a long program that I want to run ( it might takes 1 hr):popcorn:
how can I make it to run in background ?:popcorn:
How can I run the same program parallel ? ( the same program that the same time running 
How can I make it to alert me when it is done?
How can I make it to run program after each other? ( like mkdir test ls ??) 
How can I force my PC to just work on my project and nothing else ( fasterest speed ever?????


Thanks :guitar: 


OH OH I wander about parallel downloading too:
I have too many huge files I need to downalod for the web!!!
So I wanted to write a shell program to do that BUT :popcorn::confused:

WHAT IS THE FASTERST WAY TO GET THOSE HUGE FILES?????
parallel wget? ?? ( how should I do it parallel? ):lolflag:
I heard about AXEL? I have no idea? 

TELL ME more 
Thanks :guitar:

---

### Post by unutbu on 2008-08-07
> how can I make it to run in background ?

If the program is called 'prog', then run
```

nohup prog &

``` The nohup will keep prog from being killed if you close your terminal window or log out. If this is not an issue for you, then you can skip the nohup.
> 
How can I run the same program parallel ? ( the same program that the same time running
```

nohup prog &
nohup prog &
```

This will of course run the same thing twice. It will only do different things if you give it different input. To make one program with different parts running in parallel, you have to design a parallel algorithm and write threaded coded or make use of a parallel library.
> 
How can I make it to alert me when it is done?

You could add a command to the end of your program like this:
```

zenity --info --text 'Prog has finished!'
```

Or, alternatively, use an image viewer program to display an image. For example:

```
gqview --fullscreen the_end.jpg
```

You can add these lines as-is to the end of a shell script. In perl:
```

system("zenity --info --text 'Prog has finished!'");

```
In python:

```
import subprocess
subprocess.call("zenity --info --text 'Prog has finished!'")

```
> 
How can I make it to run program after each other? ( like mkdir test ls ??)

Let's say first program is called prog1 and the second program is called prog2. Then make a script

```
#!/bin/sh
prog1
prog2

```
Call the script dual. Make it executable
```

chmod 755 dual
```

Run it:

```
./dual
```
> 
How can I force my PC to just work on my project and nothing else ( fasterest speed ever?????
```

nuhup nice -20 prog &
```
This gives prog priority over all other processes.

---

### Post by maybeway36 on 2008-08-07
> **just_linux said:**
> How can I make it to run program after each other? ( like mkdir test ls ??) 
Here's what I do:
```
command1 && command2 && command3
```

---

### Post by bodhi.zazen on 2008-08-07
You can also run long, unattended programs in screen.

---

### Post by scorp123 on 2008-08-07
> **maybeway36 said:**
> Here's what I do:
```
command1 && command2 && command3
``` Let me expand on that:

The "&&" makes program run after each other **only if the previous command was successful!**

Example (on a standard Ubuntu system): ```
xterm && xclock && zenity --info --text="All commands have finished."
``` What should happen: a simple terminal window opens. You close it and then a clock appears. You close that one too and then a simple dialogue window appears informing you that all commands have finished.

Let's add a few twists ...

The "||" (double pipe) makes program run** only if the previous command was [B]NOT** successfull![/B] Now use this with the one above and you can construct interesting shell commands :D

Example:  ```
asdfghj || xterm && qwerty || zenity --info --text="Some commands here are not valid\!" 
``` What you should see: The shell should complain that the command "asdfg..." does not exist. Of course it doesn't (at least not 'out of the box'). Because this command finished with an error within the same second a terminal window should have popped open. We told the shell to do that. Because that command was successful ("xterm" should exist 'out of the box') the next command is executed. But because it fails too a dialogue box instead is opened informing you about the illegal command.

The ";" executes commands one after another **regardless** if the previous commands produced an error or not ... Try the commands above, mix it with illegal commands, and you will see the subtle differences.

Combine all three operators ";", "&&" and "||" together and you can do some very interesting things! e.g. execute commands, then regardless if the result was a success or not trigger a backup job, and then depending on the success of other programs do "this" (whatever that might be) or "that".

Hope this was useful ;)

---

### Post by billgoldberg on 2008-08-07
There are some usefull tips here in this post.

Bookmarked for future reference.

---

