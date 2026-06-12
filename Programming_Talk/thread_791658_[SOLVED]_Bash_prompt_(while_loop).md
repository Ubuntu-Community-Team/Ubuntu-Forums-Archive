---
title: "[SOLVED] Bash prompt (while loop)"
date: 2008-05-12
forum: Programming Talk
---

### Post by Dr Small on 2008-05-12
I have been trying to design a simple prompt (nothing very spectacular) that will run input as commands from variables I set in the script.

Example,
```
OPEN='ged $1'

while true; do	
	echo -n "prompt> "
	read command
	"$command"
done
```

the variable OPEN I wish to act as a command, so when I run it in my prompt, it executes the value of the variable, but so far I have not had any luck at this.

So if I run the script, it ouputs:
```
prompt> 
```

And then I would type:
```
prompt> OPEN /path/to/file.txt
```

And it would execute the OPEN variable, and run my command. Any way to do this?

Dr Small

---

### Post by dtmilano on 2008-05-12
This will work with your example, but I don't see the point:

> #! /bin/bash

alias OPEN='ged'

while true; do	
	echo -n "prompt> "
	read command
	eval $command
done

---

### Post by Dr Small on 2008-05-12
That does the same identical thing as before.
```
prompt> OPEN /path/to/file.txt
/home/drsmall/bin/prompt: line 11: OPEN: command not found
```

---

### Post by nick_h on 2008-05-12
By default alias expansion is only enabled for interactive shells.

To get it working, add the line
```
shopt -s expand_aliases
```
to the script dtmilano posted.

---

### Post by Dr Small on 2008-05-12
Thanks, that did the trick :)

---

