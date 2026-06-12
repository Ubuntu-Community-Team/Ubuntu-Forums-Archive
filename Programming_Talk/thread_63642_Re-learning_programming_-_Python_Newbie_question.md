---
title: "Re-learning programming - Python Newbie question"
date: 2005-09-08
forum: Programming Talk
---

### Post by Electrobes on 2005-09-08
Hi everyone I just got back into the computing fun and recently installed Ubuntu onto a Linux only computer. I am looking forward to playing with programming and decided to try Python. I have coded in C, some C++, and a little in JAVA a few years back. I am new to both Linux and Python. I am slightly confused as to what editor I should use... for Python. Any suggestions. 

Also if it is suggested I download something, how do I get it installed via the command line (something new to me). I have used sudo apt-get install before... but I am guessing that was with already included items.. not items downloaded. Thank you!

I did try to install idle... using sudo apt-get install idle but I got this instead...

Reading package lists... Done
Building dependency tree... Done
Package idle is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package idle has no installation candidate

I am not sure what it means... but I thought IDLE was an editor plus I also thought it came included with Ubuntu.. guess I was wrong?

---

### Post by Electrobes on 2005-09-08
I forgot to mention that I did run simple things with Python like the print Hello World using the command line. But when I copied (typing in myself) an example I could not use the command line at all easily, but if I copy and pasted onto the command line, it worked just fine. SHould I be using an editor, or do most people use this method? thanks again

---

### Post by Electrobes on 2005-09-08
okay I found gedit, and got it up, but I am not sure how to get it to highlight as I write code. I also do not know how to run it after the code is written? I'll keep looking but if anyone uses gedit or knows how to get a body of code to run using gedit I would love to hear from you :)

---

### Post by Electrobes on 2005-09-08
okay for those of you who are new, here's some news as I go learning some new things about Linux and programming in Python. I got gedit to work (highlighting syntax). If you run gedit, its in the preferences, but I found that whatever you are writing, the file has to be saved as .py (for python). I am still not sure if executing the code this way is correct:

1. write code out under a .py file
2. complete whatever code you are writing,
3. save file
4. Copy the contents fo the file and paste it onto the terminal (after you've opened python on the terminal)
5. hit enter and the code runs. 

The reason I am not sure if I am doing this right is because I figure there is another, and easier way to execute the code after finsihing it on gedit editor. If someone knows this and I still haven't responded please tell me, I would appreciate that. Oh well back to learning python. By the way I like this tutorial so far... a byte of python. its very helpful and a good way to start thus far.

---

### Post by ow50 on 2005-09-08
To run the code easier:

A1. Have your file start with "#!/usr/bin/env python". That should be the first line. This is the unix style way where that first line tells how the code should be run.
A2. Make sure the file has execute permissions. Right click in Nautilus or use command "chmod" in the terminal.
A3. Run the file with "./yourfile.py".

or

B1. Use command "python yourfile.py".

The usefulness of the python console is mostly limited to testing one-liners of code.

---

### Post by Electrobes on 2005-09-08
a couple of fustrating things. First I created a file Program 1.py I now want to remove it but if I type rm Program 1.py I get this:

christian@ubuntu:~$ rm Program 1.py
rm: cannot remove `Program': No such file or directory
rm: cannot remove `1.py': No such file or directory

Obviously the space is causing trouble for the command to work. How do I remove this file?? 

I believe this also may be causing the trouble when I try to run the Program 1.py file via the terminal. I get this: The first line shows the files (I somehow created two, and I have no idea how that happened...)

Desktop  Program 1.py  Program 1.py~
christian@ubuntu:~$ python Program 1.py
python: can't open file 'Program': [Errno 2] No such file or directory
christian@ubuntu:~$


Thank you in advance for your help.. I understand how it can be answering newb questions....

---

### Post by Electrobes on 2005-09-08
AHA! I got it removed.. I put a ' on either side of the program name and it worked! And guess what else? I also got it to run the program too! Muwahahaha! Thanks again

---

### Post by jobezone on 2005-09-08
If you start typing the first letters of your file, and press **TAB**, it will be completed for you (or will show multiple filenames which begin with those letters). This also works with commands.

You can handle that file (and other files with spaces in their names) in the terminal by using **Program\ 1.py** or **"Program 1.py"**.

---

### Post by wtd on 2005-09-08
From the sounds of it, learning some basic *nix commandline skills would be an excellent use of your time.

---

### Post by Electrobes on 2005-09-08
yeah you're right. Its the programming thats forcing me to learn and use the commands though.. so everytime I find something out that blows me away ti sticks with me.. you know what I mean? I love surprises and in this hobby (well, hobby for me anyway) I think its awesome when stuff like that happens, especially before I get into the good stuff :)

---

### Post by Mike Buksas on 2005-09-11
[QUOTE=Electrobes]a couple of fustrating things. First I created a file Program 1.py I now want to remove it but if I type rm Program 1.py I get this:

christian@ubuntu:~$ rm Program 1.py
rm: cannot remove `Program': No such file or directory
rm: cannot remove `1.py': No such file or directory

Obviously the space is causing trouble for the command to work. How do I remove this file?? 

I believe this also may be causing the trouble when I try to run the Program 1.py file via the terminal. I get this: The first line shows the files (I somehow created two, and I have no idea how that happened...)

Desktop  Program 1.py  Program 1.py~
christian@ubuntu:~$ python Program 1.py
python: can't open file 'Program': [Errno 2] No such file or directory
christian@ubuntu:~$


Thank you in advance for your help.. I understand how it can be answering newb questions....[/QUOTE]

Put a backslash '\' in front of the empty space: ```
rm Program\ 1,py
```, or wrap the name in quotes: ```
rm "Program 1.py"
```

Although the Unix shells can handle spaces in filenames, for the reason that you just discovered, it's often better to leave them out and stick with names like Program1.py instead. At least if you're going to be using the command line.

As far as getting IDLE is concerned: have you added the universe repositorities? The unofficial Ubuntu starter guide has the low-down on that [here](http://ubuntuguide.org). 

I still like emacs with python-mode for working in python. It fontifies (colors) python keywords and coments, does indentation for you and will run the python intrepreter in a buffer window. It's a little on the sparse and unfriendly side, but with some hacking and patience, you can get it to do whatever you want.

---

