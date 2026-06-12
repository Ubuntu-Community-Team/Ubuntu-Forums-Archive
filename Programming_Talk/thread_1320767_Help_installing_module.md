---
title: "Help installing module"
date: 2009-11-09
forum: Programming Talk
---

### Post by jesuisbenjamin on 2009-11-09
Hello there,

I would like to install **pyPdf** (see this [**link**]("http://pybrary.net/pyPdf/")), but i have some troubles. The setup.py file does not help, nor do any of the documents appended.
Can someone help me through?
Thanks

---

### Post by silentrebel on 2009-11-09
I have a feeling you simply copy pyPdf to the location where your other python libraries are...
Then you just use the 'from...import...' phrase to import the libraries and follow the commands in the README to use the functions the whole thing offers...
The setup.py doesn't seem to really setup anything; it just seems to be information about the library and its developer...

---

### Post by silentrebel on 2009-11-09
Actually, extract the archive navigate to *pyPdf-1.12/.* and type ```
 python setup.py
```.
You then get these instructions for use:
> usage: setup.py [global_opts] cmd1 [cmd1_opts] [cmd2 [cmd2_opts] ...]
   or: setup.py --help [cmd1 cmd2 ...]
   or: setup.py --help-commands
   or: setup.py cmd --help


---

