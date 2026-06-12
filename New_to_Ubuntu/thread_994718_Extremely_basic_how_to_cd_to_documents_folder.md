---
title: "Extremely basic: how to cd to documents folder"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Motion_Noob on 2008-11-27
I have a terminal window open, and I want to unzip and untar a file that I've put in a folder named "driver" here: 

john/documents/driver 

I believe I first have to change to that directory.

But all of these commands give the same result of "No such file or directory" :

john@john-ubuntu:~$ cd /home/john/documents
john@john-ubuntu:~$ cd /john/documents
john@john-ubuntu:~$ cd /documents

What in the world am I missing?! Thank you in advance.

---

### Post by Waappu on 2008-11-27
Hi

Terminal is case sensitive. So check if some of folder names contain actually capital letters

---

### Post by Liviu-Theodor on 2008-11-27
You can verify what folders you have with the [FONT="Courier New"]ls[/FONT] command. If you want to see also hidden files, the command is [FONT="Courier New"]ls -a[/FONT]. This is given in the terminal.

---

### Post by OutOfReach on 2008-11-27
Right the terminal is case sensitive so you would have to enter it like this:
```

cd /home/me/Documents/

```

---

### Post by Motion_Noob on 2008-11-27
Yes! That was it! Thank you. Case sensitivity. (was so frustrated at something so simple.)

Now that I'm in the Documents directory, I want to change into a subdirectory there named "webcamdriver" (all small letters.)

At the john@john-ubuntu:~/Documents$  prompt, I type:

cd /webcamdriver

And I get the "No such file or directory" message again.

cd /Documents/webcamdriver   also gives the "No such file or directory" message.

---

### Post by Waappu on 2008-11-27
```
cd ~/Documents/webcamdriver
```

or when you are in Documents folder do not put slah before```
cd webcamdriver
```

---

### Post by Dedoimedo on 2008-11-27
Hello,

If you're inside the home directory, that you do not need the preceeding slash ...

Only:

```
cd webcamdriver
```

You see the slash indicates you go back to root  of the filesystem (/)and then search for your desired directory there. This is the absolute path. When you use cd without the slash, you use relative paths to the current directory.

Dedoimedo

---

### Post by prshah on 2008-11-27
> **Motion_Noob said:**
> 
john@john-ubuntu:~$ cd /home/john/documents
john@john-ubuntu:~$ cd /john/documents
john@john-ubuntu:~$ cd /documents


Tab completion will save you a lot of grief in the Terminal. Enter part of the directory name, and then press [Tab]. If the computer finds a match, it will automatically fill it in. If you press [Tab] twice in sucession, it will show you a list of matches, and you can fill in a further character or two, and continue to use Tab completion to fill in the rest.

Incidentally, tab completion works for more than just cd; if you use modprobe, it will tab complete module names instead of filenames and so on.

---

### Post by Waappu on 2008-11-27
Hi

BTW you could also check e.g. man pages to read information about commands
[http://www.ss64.com/bash/cd.html](http://www.ss64.com/bash/cd.html)

```
man cd
```

---

### Post by Motion_Noob on 2008-11-27
That was it. Omitting the slash worked perfectly. Thank you everyone!:)

---

