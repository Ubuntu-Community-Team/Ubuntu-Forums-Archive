---
title: "Questions (again)"
date: 2008-11-03
forum: Programming Talk
---

### Post by Shippou on 2008-11-03
Hello..

So this is my first thread on the month of November.

I am writing a program that bulk compresses directories. In connection to this, I want to ask the following questions:

1. How do count subdirectories only using native Linux commands as musch as possible? I would really appreciate if the command returns a number as a result.

2. How to determine if a file (sorry, can't think of a term) is a directory or an ordinary file? (This is somewhat to complement #1).

3. How to write an application in Java which supports drag-and-drop?

I think these are the more vital questions as of now.

Also, I am thinking of making the code open-source. Don't get me wrong here, I'm just an ordinary Linux user (though I am a programmer) who wants to return something to the Linux community, even though it is only a simple program.

Please help. And thank you very much. :)

---

### Post by Pro-reason on 2008-11-03
See [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html) for determining whether a file is a directory.

---

### Post by dmizer on 2008-11-03
Moved to programming talk. You should get better help here.

---

### Post by Shippou on 2008-11-03
Thanks for all the help, and sorry for posting in the wrong subforum. :)

Happy November to all! :)

---

### Post by Martin Witte on 2008-11-04
if you want to count subdirectories in a shell you can do it with commands:
```
martin@toshibap200:~$ typeset -i i=0
martin@toshibap200:~$ for d in *; do [[ -d $d ]] && i=$(($i+1)); done
martin@toshibap200:~$ echo $i
18
martin@toshibap200:~$ 

```

---

### Post by Bichromat on 2008-11-04
You didn't say if you want to count them recursively or not, so here are 2 versions:
```

#all subdirectories recursively:
find /path/to/dir -type d | wc -l

#non-recursive (only 1 depth level):
find /path/to/dir -maxdepth 1 -type d | wc -l

```

'find' lists the directories, 'wc -l' counts the lines.

---

### Post by Shippou on 2008-11-12
Hello again...

I have not finished my program yet. I'm tardy, after all.

But then, I am thinking of writing a new very simple program.

What is the command used in restarting the network via the terminal?

Thanks for all the help I received.

EDIT: What I mean is how to manually restart the network when the MAC address is changed, or when you build a bridge.

---

### Post by Shippou on 2008-11-12
Hello...

I have finished writing the small program I mentioned about. It is a GUI MAC address spoofer that might be useful for those who change their MAC addresses.

This is a Java application, and I am publishing the source code. Just compile it using 
```

javac Spoof.java

```

If you don't want to compile it, then you can just download the class file and execute it by 
```

sudo java Spoof <interface>

```

where <interface> is the name of the network interface you want the MAC address changed.

This is required to run as root in order to function properly. Changing the MAC address needs to be done as root in the first place.

The following are required to run the program:
1. Java compiler and/or java interpreter
2. ifconfig (duhh... present always)

The program is used by issuing the command

```

sudo java Spoof
sudo java Spoof <interface>

```

Option 1 is the default: it changes the MAC address of eth0. For changing MAC addresses of other interfaces, use option no. 2. Specify which interface as the parameter of Spoof.

This program and the source code can be freely distributed, used, and modified. 

For suggestions, comments and requests, please feel free to post them here, or e-mail me at [email]ardlexworld_90@yahoo.com[/email]

EDIT: Sorry for the late upload of the source code.

---

