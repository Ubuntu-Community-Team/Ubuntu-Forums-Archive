---
title: "[Python] No such file or directory"
date: 2013-07-06
forum: Programming Talk
---

### Post by ki4jgt on 2013-07-06
I'm using a script I wrote in python3.3 a few months back. Now I've installed a fresh copy of Ubuntu and the script won't work. It's a cgi script using OS module. Whenever I run this script either from the server or the command-line I get an error that the directory doesn't exist, even though I simply transfered the htdocs directory EXACTLY AS IT WAS from the server.

```

import os
os.listdir("images")

```

I get an error that the directory or file doesn't exist when I run the script from the terminal.

---

### Post by Cheesehead on 2013-07-06
Either provide the full path to the 'images' directory,
Or cd to the parent directory before launching the python interpreter.

Use the python command 'os.getcwd()' to list the python interpreter's current working directory.
Is it the directory you expect?

---

### Post by ki4jgt on 2013-07-06
I've already tried getcwd(). Doesn't work and I was thinking cwd would present security problems as it's going to show the folder path in the html output.

EDIT:
Sorry, wrong about that but getcwd doesn't work either.

---

### Post by steeldriver on 2013-07-06
what version of Ubuntu did you just install? what is the exact error message? are you sure it's finding the python interpreter itself?

---

### Post by ki4jgt on 2013-07-07
I installed Ubuntu 13.04 which is what version I had with the original files. I just added harddrive encryption. Now, the tools.py file (where I keep the css, header, footer and other things I don't want to code over and over) is calling for a random background image from the "images" folder. The images folder is in the same directory as the files and the name is spelled correctly b/c the site used to work before I reinstalled Ubuntu. Also, I'm using xampp with a link to htdocs on my desktop and htdocs has been made rwx by everyone. Basically that's all I've done. Here's the error message I get when I use this code:
```

import random
import os

random.choice(os.listdir("images"))

```

OSError: [Errno 2] No such file or directory: 'images'

---

### Post by trent.josephsen on 2013-07-07
"getcwd doesn't work" is just about the most useless response you could have given. What do you mean it doesn't work? It's a debugging aid, it doesn't have to do anything but return a string. Add
```
print(os.getcwd())
```
to your file and see what it prints.

---

### Post by ki4jgt on 2013-07-07
Well, getcwd returns the CURRENT WORKING DIRECTORY of the terminal where the script is running. So, if I'm running the terminal in home and execute the script (or my server is) getcwd will look in MY home folder for "images". The server needs to get the absolute path for the file in question. There is a way to do that and I've done it.

EDIT:
Thanks for the help guys.

---

