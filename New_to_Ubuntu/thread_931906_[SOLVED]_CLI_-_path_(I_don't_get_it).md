---
title: "[SOLVED] CLI - path (I don't get it)"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by adamogardner on 2008-09-27
I've read about path multiple times but it doesn't make sense to me.  I think of path as a narrow route to be traveled in either direction. But Linux is like a tree. So if there is a 'path' as I describe, what is the significance of it?  why have it? and what sort of things woould I want to set to it? I don't get it at all.

---

### Post by jrothwell97 on 2008-09-27
Think of it as the path you take up the branches (folders) of the tree to access the fruits (files) on the branches.

---

### Post by hubie on 2008-09-27
It is a list of places that the OS looks when you type in a command, so if you type [FONT="Fixedsys"]ls[/FONT], linux looks in all the directories in your $PATH variable until it finds it (/bin/ls for me).  If it doesn't find it, then it gives you a "can't find" type of error.  It stops looking when it finds the first instance of it.

If you want to see what is in your path, type
```
$echo $PATH
```

What you might want to do with it is, for instance, if you have your own program you want to run from any directory, you can add the location of its directory to your $PATH variable, so instead of having to type in [FONT="Georgia"]/home/me/myprograms/myspecialprog[/FONT], you can just type [FONT="Georgia"]myspecialprog[/FONT] provided [FONT="Georgia"]/home/me/myprograms[/FONT] is added to your $PATH.

By the way, Windows has a PATH of sorts as well.  If you right-click on "My Computer", select [FONT="Fixedsys"]Properties --> Advanced --> Environment Variables[/FONT] you'll see what your Windows path is.

---

### Post by adamogardner on 2008-09-27
> **jrothwell97 said:**
> Think of it as the path you take up the branches (folders) of the tree to access the fruits (files) on the branches.

ok so the 'path' changes with each ...'venture?'  That is something if not more confusing.what's the point of moving something to your path?

---

### Post by Sorivenul on 2008-09-27
This explaination is probably the best concept and explaination of PATH as I've found:
[http://www.faqs.org/docs/Linux-mini/Path.html]("http://www.faqs.org/docs/Linux-mini/Path.html")
In short, the PATH does run both ways.  You input a command, which goes out in search of an executable, if it finds one, it returns to you in the form of an application or script running.  Hope this helps!

---

### Post by gossrock on 2008-09-27
Path can refer to more than one thing.  In a specific instance of a file you can say "the path to the file is /home/username/filename"  The path (your "narrow route to be traveled") starts from the root of the filesystem (also known as "/") and ends at the name of the file.

It can alson refer to the PATH enviroment variable. (you can read what is in it by typing echo $PATH) that this is where the computer looks for the comands that you want to execute.

mine reads:
/home/myunsername/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

so if I type a command like "ls" it will first look in "/home/myunsername/bin" if the command is not there (and it is not) it will look in "/usr/local/sbin" (and it is not there either) then it will look in the next ... and the next ... untill it finds it in "/bin" 

if there where multiple programs with the same name then the one that gets executed is the one that is found first in the list.

---

### Post by jpeddicord on 2008-09-27
A path (lowercase) is usually just a directory on your filesystem. /home/user/documents is a path. /share/dev/script.py is a path. Anything that can be typed in like that is a path.

The PATH (commonly uppercase) is an environment variable that tells the system where it can run programs from without having to type in the full path. The PATH can have multiple directories in it, each separated by a colon:

```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

Using the above PATH, if you were to type in "firefox", the system would first look for /usr/local/sbin/firefox. Then /usr/local/bin/firefox. Then /usr/sbin/firefox. It would eventually find it at /usr/bin/firefox.

You can add directories to the PATH simply by changing the variable in your shell prompt:

```
export PATH="/home/user/myapps:$PATH"
```

would result in a PATH of:

```
/home/user/myapps:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

Meaning that /home/user/myapps would be searched in first for any runnable applications. To make a PATH environment variable persistent after multiple Bash sessions or a system restart, add an export line like above to the end of your ~/.bashrc.

---

### Post by adamogardner on 2008-09-27
This has been excellent advice.  I am confused about the rest of the directories that are neglected by the search or executable or whatever it is that ae not in the path.  Why are they omitted, what do they contain? obviously not executables, correct?

---

### Post by jpeddicord on 2008-09-27
> **adamogardner said:**
> What am I looking at here? I don't see my /home/myname@.  

adamogardner@CRONUS:~$ $echo $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory
adamogardner@CRONUS:~$

Take out the $:
```
echo $PATH
```

---

### Post by hubie on 2008-09-27
Sorry, I put the $ before echo to represent the command prompt.

---

### Post by adamogardner on 2008-09-27
> **hubie said:**
> Sorry, I put the $ before echo to represent the command prompt.
 
oh well it still worked, duh I should have figured that.  WHat is the significance of the '$' before PATH?

---

### Post by jpeddicord on 2008-09-27
> **adamogardner said:**
> oh well it still worked, duh I should have figured that.  WHat is the significance of the '$' before PATH?

It tells the shell you're looking for an environment variable. Otherwise, "echo PATH" would just show the word "PATH" for its output.

You can see all of your current environment variables with the `env` command.

---

### Post by gossrock on 2008-09-27
> **adamogardner said:**
> I am confused about the rest of the directories that are neglected by the search or executable or whatever it is that ae not in the path.  Why are they omitted, what do they contain? obviously not executables, correct?

It is not so much that the rest are omitted as it is that they are not included.  The only directories that are in the PATH are where you want the system to look for the standard executables, that is, executables that you don't want to be bothered with typing out the path to.  so if PATH was set to nothing you would have to write out "/bin/ls" to execute the ls command.  this could get annoying.  You can run executables that are not in the PATH by simply typing out the path to that executable.

---

### Post by RequinB4 on 2008-09-27
Put it this way - if you didn't have a "exculsionary" PATH, then the "executor" program would have to search the name of every file in every directory on your entire system!

In fact, that's another purpose of the PATH - it says what ORDER to look in.  If you have two files of the same name in different directories, then this way you run the file in whichever directory comes first in the PATH.

There are a LOT of directories not in the path and these contain basically everything else related to a computer - since everything in linux is a file.  This is your pictures, video, office documents, but also libraries(that executables reference when they need to call a function), splash pictures, temporary directories, any mounted devices you have and all of files THEY have, any UNMOUNTED devices in /dev, configuration text files that determine program settings, etc.

---

### Post by adamogardner on 2008-09-28
I totally get it.  Thankyou for making this so clear.

---

