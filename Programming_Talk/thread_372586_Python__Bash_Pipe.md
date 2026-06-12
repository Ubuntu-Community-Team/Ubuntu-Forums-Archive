---
title: "Python / Bash Pipe"
date: 2007-02-28
forum: Programming Talk
---

### Post by thomasaaron on 2007-02-28
Hey, guys.

I'd like be able to make a python/Tk text widget *seem* like a terminal emulator.

I need it to be able to perform two functions:

1. It has to display the results of a bash script running in the background in the text widget. This much I've figured out a way to do. I just have the bash script output to a file and then read the file into the text widget.

2. This is what I'm unsure of. I also need for it to be intereactive. For example, if the bash script requests user input (i.e. echo What is your name?; read name), this should be done through the text widget as well. In the OS module there are pipe / popen methods. But those don't seem to be what I need.  How would you go about creating an interactive environment with BASH using a Python widget?

Thanks,
Tom

---

### Post by Tomosaur on 2007-02-28
You can just use system calls, and provide the command as an ordinary string. You'll need to figure out how you want the output to be formatted, however, since the os.popen() method returns a file object rather than a string or an array.

```

#!/usr/bin/python2.4
import os

for line in os.popen("ls").readlines():
        print line

```

^^ Performs the 'ls' command and then prints the output.

---

### Post by thomasaaron on 2007-02-28
OK, that is a much smarter way for handling commands that generate an output than what I've been using. I'll definitely incorporate it.

But what about commands that request an input. For example: os.popen("read name")
How can I deal with that?

Thanks,
Tom

---

### Post by christhemonkey on 2007-02-28
You can use the pexpect module and start a new bash process.

Something like this:
```
#!/usr/bin/env python
import pexpect

pexpect.run('ls -la')
# Run ls -la in the same way as os.popen command.

child = pexpect.spawn('/bin/bash')
# Starts a new bash process
child.interact()
#Gives user the interaction of the new process
```

EDIT: See here for more documentation on it:
[http://pexpect.sourceforge.net/pexpect.html](http://pexpect.sourceforge.net/pexpect.html)

---

### Post by Tomosaur on 2007-02-28
EDIT: ^^christhemonkey's solution is better

---

