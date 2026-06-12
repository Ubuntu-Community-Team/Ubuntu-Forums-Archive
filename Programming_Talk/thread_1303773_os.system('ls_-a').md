---
title: "os.system('ls -a')"
date: 2009-10-28
forum: Programming Talk
---

### Post by jesuisbenjamin on 2009-10-28
Hello there,

i am new to programming and am beginning with Python. Now i am playing around with some scripts to practice and learn along.

I wanted to run a simple command
```
os.system('ls -a')
```
The funny thing is that when i run ls -a manually in the shell i get the 'coloured' version where eg. folders are in blue font, whereas when i run the same command from my script there are no colours/legend.

I guess this leads me to ask three questions:
[LIST]
[*]How come it doesn't show colours whilst using the script?
[*](Assuming it is due to the module: ) Is there an alternative to os.system() to execute shell command-lines?
[*]How can i find out what module i should use when i just have an idea of what i want to do? For example: suppose i want a module to search for files, how can i come to know there is a module for this and what its name would be?
[/LIST]

Thanks

---

### Post by Arndt on 2009-10-28
> **jesuisbenjamin said:**
> Hello there,

i am new to programming and am beginning with Python. Now i am playing around with some scripts to practice and learn along.

I wanted to run a simple command
```
os.system('ls -a')
```
The funny thing is that when i run ls -a manually in the shell i get the 'coloured' version where eg. folders are in blue font, whereas when i run the same command from my script there are no colours/legend.

I guess this leads me to ask three questions:
[LIST]
[*]How come it doesn't show colours whilst using the script?
[*](Assuming it is due to the module: ) Is there an alternative to os.system() to execute shell command-lines?
[*]How can i find out what module i should use when i just have an idea of what i want to do? For example: suppose i want a module to search for files, how can i come to know there is a module for this and what its name would be?
[/LIST]

Thanks

You can force coloring by using "ls --color".

'ls' detects whether stdout is a terminal, so for example "ls > filelist" also doesn't color. Apparently python does something so that the output from os.system isn't identical to stdout.

---

### Post by NovaAesa on 2009-10-28
Also in your terminal, there is a chance that you have an alias so that when you type in 'ls' it actually is converted to 'ls -color'. I don't think python would pick these aliases up. This could have something to do with it, I'm not 100% sure, but it's something for you to look into.

---

### Post by Arndt on 2009-10-28
> **NovaAesa said:**
> Also in your terminal, there is a chance that you have an alias so that when you type in 'ls' it actually is converted to 'ls -color'. I don't think python would pick these aliases up. This could have something to do with it, I'm not 100% sure, but it's something for you to look into.

Yes, that's the case for me anyway (not that I chose it to be that way). What I said about detecting a terminal doesn't apply, sorry.

---

### Post by geirha on 2009-10-28
> **jesuisbenjamin said:**
> 
Assuming it is due to the module: ) Is there an alternative to os.system() to execute shell command-lines?

The subprocess module allows you to run processes and to send and read data from them. ```
help('subprocess')
```

> **jesuisbenjamin said:**
> 
How can i find out what module i should use when i just have an idea of what i want to do? For example: suppose i want a module to search for files, how can i come to know there is a module for this and what its name would be?


Well, there's the library reference [http://docs.python.org/library/index.html](http://docs.python.org/library/index.html). You can also search modules (and their descriptions) from the python interactive shell
```
help('modules searchterm')
```
In the case of an ls-equivalent, see os.listdir() «help('os.listdir')»

---

### Post by ghostdog74 on 2009-10-28
use Python's own directory listing function instead of calling ls from your script. Make your script portable.

---

### Post by lukeiamyourfather on 2009-10-28
My guess is the Python interpreter doesn't care what colour the output is. Why not just use this instead.

```

import os
myDir = "/usr"
fileList = os.listdir(myDir)
for file in fileList:
     print file

```

Do whatever you want with the list of files, organise it, filter it, etc. Don't get hung up on the specifics like the colour of the text from the terminal because it doesn't really matter. Cheers!

---

### Post by Martin Witte on 2009-10-28
The system command doesn´t execute the alias but the actual ls command as found in the path. Example below shows an alias isn't found by os.system

```
martin@toshibap200:~$ alias p=ls
martin@toshibap200:~$ python
Python 2.6.4rc2 (r264rc2:75497, Oct 20 2009, 02:55:11) 
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import os
>>> os.system('p')
sh: p: not found
32512
>>> 

```

---

### Post by Martin Witte on 2009-10-28
> **Arndt said:**
> Yes, that's the case for me anyway (not that I chose it to be that way). What I said about detecting a terminal doesn't apply, sorry.

This is set in [~/.bashrc]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_01.html#sect_03_01_02_04") in your home directory in a default ubuntu user setup

---

