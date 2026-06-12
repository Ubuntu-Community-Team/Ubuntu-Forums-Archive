---
title: "Zenity input to Python"
date: 2006-09-22
forum: Programming Talk
---

### Post by srirammurali on 2006-09-22
hi all, am just beginnin to code in python and am getting some serious trouble when in try to parse the input to a zenity text input box inside a python script. there might be a lotta nooby errors. pls help me out with this code
 
CODE:
import os
name=os.system('zenity --entry --title="Testing from Python Shell" --text="Test Zenity-Python Script"')
print name
 
I entered the string Sriram at the zenity interface and the output from the python shell for the print statement was 0.
 
How am i to proceed to transfer the input value at the zenity interface to the variable inside the python script

---

### Post by Wolki on 2006-09-22
> **srirammurali said:**
> 
import os
name=os.system('zenity --entry --title="Testing from Python Shell" --text="Test Zenity-Python Script"')
print name
 
I entered the string Sriram at the zenity interface and the output from the python shell for the print statement was 0.

os.system returns the exit code of the command, not the output. Use os.popen to get a pipe so you can read the output. See [http://docs.python.org/lib/os-newstreams.html](http://docs.python.org/lib/os-newstreams.html) for more information.

---

### Post by srirammurali on 2006-09-23
thanks a lot for the reply dude.

---

