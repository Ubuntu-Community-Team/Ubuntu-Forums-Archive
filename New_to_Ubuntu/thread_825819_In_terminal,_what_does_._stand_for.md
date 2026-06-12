---
title: "In terminal, what does ./ stand for?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by diablo75 on 2008-06-11
I'm wanting to write something about the commands used in terminal on my blog, but I'm looking for a little background about this guy:

./(commandname)

For instance, when you cd into a folder containing something you want to execute, you have to type ./nameoffile instead of nameoffile.  I'm just looking for a little background behind the syntax and why it's like that.

I guess another way of asking this is:  What does the period represent, and what does the forward-slash represent?

---

### Post by Joeb454 on 2008-06-11
In the way you are mentioning - ./command

./ means the current directory

Though . can also signal a hidden file as well as the current directory

---

### Post by Kebabman on 2008-06-11
./ is the path to the current directory. If you do a ls -al in any directory you will see at the top : 

drwxr-xr-x 70 keba keba    4096 2008-06-11 14:57 .
drwxr-xr-x  4 root root    4096 2008-03-12 13:48 ..

or similar.

. is the current directory, and .. is the directory immediately above it in the directory structure. You have to specify the path to a file in order to execute it unless it can be found via your PATH environment variable. Hence the ./

Hope that explains it enough.

---

### Post by _sphinx_ on 2008-06-11
[dot] is a bash command that takes filename as its first argument and read and execute whatever is written in the file. 
you can read
```
man .
```

---

### Post by Golem XIV on 2008-06-11
The period means "this directory" and the slash is the directory delimiter.  So running **./cmdname** in a terminal would run the  command **cmdname** from the current directory.

The reason for this is that Linux will look for commands in the $PATH variable, where the directory paths for the usual commands are being stored.  If your command has the same name, it could happen that a different command with the same name is executed instead.  The period-slash ensures that you actually run the command that you want.

There are other shortcuts, like two periods for the directory above the current one (parent directory), the ~ that means your home directory, etc.

---

### Post by KingTermite on 2008-06-11
> **Kebabman said:**
> ./ is the path to the current directory. If you do a ls -al in any directory you will see at the top : 

drwxr-xr-x 70 keba keba    4096 2008-06-11 14:57 .
drwxr-xr-x  4 root root    4096 2008-03-12 13:48 ..

or similar.

. is the current directory, and .. is the directory immediately below it in the directory structure. You have to specify the path to a file in order to execute it unless it can be found via your PATH environment variable. Hence the ./

Hope that explains it enough.

Good explanation. Let me expand on one point.

The reason you often have to put the "./" in front of your command is because whatever directory you are in is not part of the search path (e.g. the PATH variable). 

If you have whatever directory part of the search path, you don't have to type "./" in front of the command because its found via the search path. A little trick I did was to put "." in my PATH variable so whatever directory I'm in is automatically searched and I don't have to use "./" wherever I am.

---

### Post by diablo75 on 2008-06-11
So, would it be possible to type **../filename** so as to run something from the parent directory?

Also, can someone explain the PATH variable and where it is configured?

---

### Post by _sphinx_ on 2008-06-11
Yes.

---

### Post by Joeb454 on 2008-06-11
Yes totally possible, I've done it a few times myself (it saves on the "cd" commands :p)

---

### Post by KingTermite on 2008-06-11
> **diablo75 said:**
> So, would it be possible to type **../filename** so as to run something from the parent directory?

Also, can someone explain the PATH variable and where it is configured?

Yes, you could run a file in the parent directory that way.

The PATH variable is the "search path". It is the list of directories searched to run a command when you try to type one at the command line. It is searched "in order" the directories are listed.

The variable is set by default when you log in (not sure where), but you can add/modify it in your .bashrc file as you can modify any environment variable. I added "." to be the first directory looked in like this line in my .bashrc:

```
PATH=.:$PATH
```

[http://www.troubleshooters.com/linux/prepostpath.htm](http://www.troubleshooters.com/linux/prepostpath.htm)

---

### Post by diablo75 on 2008-06-11
> **KingTermite said:**
> 
```
PATH=.:$PATH
```


Does this allow you to then not type ./ if you want to run a file from the current directory?

---

### Post by decoherence on 2008-06-11
For people think about putting their current directory in $PATH, please read the following, taken from the bash cookbook preview available from Safari Books Online

[http://my.safaribooksonline.com/0596526784/adding_the_current_directory_to_the_path](http://my.safaribooksonline.com/0596526784/adding_the_current_directory_to_the_path)

> As you know, the shell searches the directories listed in $PATH when you enter a command name without a path. The reason not to add . is the same reason not to allow world-writable directories in your $PATH.

Say you are in /tmp and have . as the first thing in your $PATH. If you type ls and there happens to be a file called /tmp/ls, you will run that file instead of the /bin/ls you meant to run. Now what? Well, it depends. It's possible (even likely given the name) that /tmp/ls is a malicious script, and if you have just run it as root there is no telling what it could do, up to and including deleting itself when it's finished to remove the evidence.

So what if you put it last? Well, have you ever typed mc instead of mv? We have. So unless Midnight Commander is installed on your system, you could accidentally run ./mc when you meant /bin/mv, with the same results as above.

In other words, it's not a great idea to do this and it's a REALLY bad idea to do it if you're using sudo. Some might say this is paranoia, but when dealing with computer security, paranoia is the correct policy imho.

---

### Post by KingTermite on 2008-06-11
> **diablo75 said:**
> Does this allow you to then not type ./ if you want to run a file from the current directory?

yes, that is correct.

decoherence makes a good point though; although I don't think it will sway me as of yet. YMMV. I don't download things constantly, and 90% of what I download is from the repository or trusted sources, so I'm not worried about a malicious script.

---

