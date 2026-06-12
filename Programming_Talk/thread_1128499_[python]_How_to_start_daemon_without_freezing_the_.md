---
title: "[python] How to start daemon without freezing the rest of the program?"
date: 2009-04-17
forum: Programming Talk
---

### Post by days_of_ruin on 2009-04-17
My code checks for a dbus server and if its not there it needs to start it.
Question is, how do I start an external program without tying up my program?
Threads? I'm hoping there is a simpler way.

---

### Post by conehead77 on 2009-04-17
Im far from a Python expert, but i **think** i know what you need...
This is a code snippet from a script i recently made:
```

import subprocess as sub

p = sub.Popen(['/bin/bash', '-c', 
               "/home/user/script.sh "], 
               stdout=sub.PIPE, 
               stderr=sub.STDOUT)

```

script.sh is executed with bash in a subprocess. Hope this helps.

---

### Post by s1ightcrazed on 2009-04-17
You could do it with a separate thread, but that would not really be the best way to go about it. Conehead has the right idea, just make sure that whatever you're running 'let's go' of the terminal when it's done, so that your python script can pick up the return code and move on. I think subprocess is overkill for what you need; if you're talking about just spawning a daemon and not needing to do anything with stdout or stderr, or using process control, then os.system will do fine. 

```
import os

my_daemon='/etc/init.d/myservice start'

return_code=os.system(my_daemon)
```

or, if you're just starting a binary:

```
import os

my_binary='/path/to/binary &'

return_code=os.system(my_binary)
```

cheers,

---

### Post by days_of_ruin on 2009-04-21
Okay my programs design has changed and what I need to do now is
start a daemon for each instance (window) of this program and kill it when
the program is closed.

---

### Post by imdano on 2009-04-21
You could hang on to the pid of the process you spawn and use an [atexit](http://docs.python.org/library/atexit.html) callback to send it a SIGTERM when your main program is exiting.  If you're using Python 2.6 you can hang on to the Popen object and call the .terminate() method on it, otherwise you can just keep the pid and use os.kill().

---

### Post by KyleBrandt on 2009-04-22
> **s1ightcrazed said:**
> 


```
for beer in $(ls /home/fridge); do

    drink $beer

done
```



Better not to use ls here.  It will get confused with beers that have two words ( a space) , such as 'bud light', causing you to spill beer all over yourself.  Instead use:

```

for beer in /home/fridge/*; do
    drink "$beer"
done

```

---

### Post by imdano on 2009-04-22
> **imdano said:**
> You could hang on to the pid of the process you spawn and use an [atexit](http://docs.python.org/library/atexit.html) callback to send it a SIGTERM when your main program is exiting.  If you're using Python 2.6 you can hang on to the Popen object and call the .terminate() method on it, otherwise you can just keep the pid and use os.kill().I should add that this approach won't actually make the processes you spawn real daemons.  They'll be child processes of your main program.  To truly daemonize them you'd have to add "daemonizing" code to the processes you're spawning (see [here](http://code.activestate.com/recipes/278731/) for a very well-documented example of how to do this in Python).

---

### Post by days_of_ruin on 2009-04-23
> **imdano said:**
> I should add that this approach won't actually make the processes you spawn real daemons.  They'll be child processes of your main program.  To truly daemonize them you'd have to add "daemonizing" code to the processes you're spawning (see [here](http://code.activestate.com/recipes/278731/) for a very well-documented example of how to do this in Python).

Yes I realized that any process I started from my program weren't showing
up in 'ps -A'. Thanks for the info.

---

