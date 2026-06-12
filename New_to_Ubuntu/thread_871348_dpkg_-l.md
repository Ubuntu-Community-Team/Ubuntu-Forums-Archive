---
title: "dpkg -l"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-26
I am trying to view the list of all my installed packages.  "the book" said use the dpkg -l command I did this and it prints out in alphabetical form but starts at the letter "l" with, 
"ii  libxosd2       2.2.14-1.4     X On-Screen Display library - runtime"
I'm sure I have more packages than this.  What's going on?

---

### Post by Oldsoldier2003 on 2008-07-26
Try sending the output to a file, you are probably overflowing the text buffer of your terminal.
```

dpkg -l > installed_software.txt
```

---

### Post by adamogardner on 2008-07-26
that did the trick!  what is this ">" supposed to do?  how do I know when to use it?  Thanks for the tip.

---

### Post by scragar on 2008-07-26
you can also pipe it to less(using the pipe and the command less(shift+backslash for pipe btw))```
dpkg -l | less
```
arrows to scroll, q to exit.

the > sends the output of a command to somewhere else, normaly a file, but it can also be used for a few other things like sending the error output(2 outputs, error and standard) to the normal output.


Incase your looking for a standard rule, the pipe is used to send to commands(like less, more or sort)), while the > is used for files and a few other misc purposes. Go for pipe if your ever unsure, no chance of dodge text files being made then.

---

### Post by ad_267 on 2008-07-26
Or try this "dpkg -l | less"

This sends the output of dpkg -l into the program less which is for viewing text files or input and allows you to scroll with the arrow keys. You press q to quit.

The ">" means send the output to a file. "|" is a pipe that sends the output of one program as the input to another.

Edit: Damn beaten to it.

---

### Post by Oldsoldier2003 on 2008-07-26
The advantage of sending the output to a text file is you can load that file back into dpkg and install the packages. (For example: on another computer or the same computer after an clean reinstall)

---

### Post by adamogardner on 2008-07-26
how do you do that, oldsoldier?

---

### Post by Oldsoldier2003 on 2008-07-26
> **adamogardner said:**
> how do you do that, oldsoldier?

Actually it uses another dpkg flag. 

to save the list:
```
dpkg --get-selections > installed_software.txt
```

to reload the software:
```
sudo dpkg --set-selections < installed_software.txt
```

---

### Post by SOULRiDER on 2008-07-26
> **adamogardner said:**
> that did the trick!  what is this ">" supposed to do?  how do I know when to use it?  Thanks for the tip.

The ">" throws the output to a file. Mind you, this creates a new file and writes the output there.
If you decide to use ">>" it will append the output to the file you want.

---

### Post by adamogardner on 2008-07-26
thanks   you the man.

---

