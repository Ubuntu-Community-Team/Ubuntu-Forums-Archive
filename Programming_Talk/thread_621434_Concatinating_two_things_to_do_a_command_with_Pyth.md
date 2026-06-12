---
title: "Concatinating two things to do a command with Python"
date: 2007-11-23
forum: Programming Talk
---

### Post by Sayers on 2007-11-23
```

#The commands import allows the use of linux commands, making this a frontend program
import commands

def setup():
	centDir = raw_input("Where did you install cent, the defualt is ~/Centrifuge >")
	centDirCommand = "cd " +centDir
	commands.getoutput(centDirCommand)
	commands.getoutput('mkdir hi')
setup()

```

Currently it will mkdir in the location of the .py not where I ask it to, being ~/Centrifuge

---

### Post by LaRoza on 2007-11-23
Did you try the OS module?

[http://docs.python.org/lib/os-file-dir.html](http://docs.python.org/lib/os-file-dir.html)

It has these functions.

---

### Post by Sayers on 2007-11-23
Thanks! That plus a bit of guess work has solved my problem for now, next how can I return to something after I have finished, instead of closing the application. Example

def hi()
     print "hi"

and instead of the application ending it goes to the main menu I made, would I def the menu so I can call it over?

---

### Post by LaRoza on 2007-11-23
> **Sayers said:**
> Thanks! That plus a bit of guess work has solved my problem for now, next how can I return to something after I have finished, instead of closing the application. Example

def hi()
     print "hi"

and instead of the application ending it goes to the main menu I made, would I def the menu so I can call it over?

Use a loop, and use "if"s and "break"s.

---

