---
title: "Communicating to gnome-terminal through an &amp;amp;quot;executable&amp;amp;quot; python script"
date: 2007-09-28
forum: Programming Talk
---

### Post by 1337455 10534 on 2007-09-28
[/SIZE]
[SIZE="3"]Suppose I want to use my (executable) script to install a package, add a repository, open a restricted file; and I want to use commands such as "sudo apt-get install" and "gksudo gedit "etc/apt/sources.list"" etc..
How do I go about getting my python program to do that? [/SIZE]

If the Ubuntu community is feeling extra nice; how do you create a python script that is run in the terminal, but can run with its own GUI in the terminal?? How would you make it resize the terminal, and give the contents of the terminal a, say, yellow and orange theme??

---

### Post by ryanVickers on 2007-09-28
Does it have to be python, or did you just choose that at random? :p

Because if you were to use BASH commands/scripts, I, and many other people, could help, but you might not find *as much* help with python.

---

### Post by 1337455 10534 on 2007-09-29
Yes, it needs to be python to be cross-platform

---

### Post by ryanVickers on 2007-09-29
Yeah, I would recommend BASH, and I'm only 14 - ckeck out the RAR program I made in my signature! :p

I don't know about a colour scheme, but it can do everything else!

---

### Post by 1337455 10534 on 2007-09-29
Wait, so BASH is a language?? I thought it was a shell..
I know this is probably the wronfgplace to do it, but could you tell me more about your Graphical RAR maker and what a split archive is? I'm interested.

---

### Post by ryanVickers on 2007-09-29
sure.  You know all of the different formats for compressed folder right?  like tar.gz, or .zip for windows?  Well, that's just 2, but rar is just another one of them that happens to be quite feature rich.  Problem is, with all the other formats you install, it gives you a nice tool, but with rar, it just installs a command and no real tool, especially not for making slip archives :)

I always found it a pain to remember all of the switches/options and the format to put it in, so now this script of mine just asks you a bunch of questions and puts the command together for you!  I've tried to include all of the useful features while keeping it relatively simple for inexperiences users.  Oh, and it was developed in about 3 days of actual time :)

oh, forgot a few things :)

Edit: A split archive is just 1 big archive broken into pieces of a certain size automatically, so you don't have to worry about picking the right amount of files or that kind of thing.  You just break it up, move it somewhere, and then when it extracts, it just checks for all the pieces and unzips like it was one archive!

It's not *really* graphical, but it pops up dialogs instead of just text, so that's good enough for me :)

One cool feature I've added recent;y is to check to make sure you've got everyhting installed that it needs on the startup and if you don't have it, it will install it for you (with the root password of course)! :)

Yeah, BASH is just another type of shell, like kshell or that.

---

### Post by 1337455 10534 on 2007-09-29
Does your script give terminal commands? If so, what language did you use??!!

---

### Post by ryanVickers on 2007-09-29
yeah, for the most part, it's just gathering user info, but then at the very end, it runs the command "rar" with all the parameters it's collected along the way :)

That's really all scripts are, just a bunch of commands to run :p

---

### Post by 1337455 10534 on 2007-09-29
?? So you used a scripting language... That magically can run BASH commands? I need to know which one, please!

---

### Post by CptPicard on 2007-09-29
Bash is both a shell and language, because bash is a scriptable shell... it's a bit of a black art though IMO :)

If you've already started with Python, check out the [os module]("http://docs.python.org/lib/module-os.html"), that has functions for running other programs, and I suppose it's sufficient for your needs.

The "GUI-ish thing inside console" sounds like something you might want to use ncurses for... and about the console resizing, I don't think you can do that programmatically without doing some kind of communication between the console process and yours; on KDE I'd refer you to dcop, but no idea about Gnome.

---

### Post by walkerk on 2007-09-29
Use os to do this...
```
#!/usr/bin/python
import os

os.system('ping [www.google.com](www.google.com)')

```

---

### Post by 1337455 10534 on 2007-09-29
Allright, so I found [http://www.linuxcommand.org/wss0040.php](http://www.linuxcommand.org/wss0040.php) and this has helped explain to me how BASH can be used to script. As far as I can see, it's pretty good. I still don't know how to get fancy text effects to work (even in Python), but that is minor... Using the os mod w/ python seems more appealing since Python can be "executed" and because I reall don't know much about BASH.
So here is how my Python program might look like;
```

#!/usr/bin/env python
import os

print "/name of my project/"
print "Option 1"
print "Option 2"
choice = input("Choose an option: ")
     if choice == 1:
          # i want the terminal to do sudo apt-get update && sudo apt-get upgrade with full permissions
     if choice == 2:
          # likewise, I want sudo apt-get clean && sudo apt-get autoremove

```

The code sucks. I know, I know. I'm using my XP comp rite now and am in a hurry. Tell me how to accomplish the comments!

Btw: dcopserver works in GNOME.

---

### Post by walkerk on 2007-09-29
Like so

[PHP]
#!/usr/bin/env python
import os

print "/name of my project/"
print "Option 1"
print "Option 2"
choice = raw_input("Choose an option: ")
     if choice == 1:
          os.system("sudo apt-get update && sudo apt-get upgrade")
     if choice == 2:
          os.system("sudo apt-get clean && sudo apt-get autoremove")
[/PHP]

---

### Post by ryanVickers on 2007-09-29
> **1337455 10534 said:**
> ?? So you used a scripting language... That magically can run BASH commands? I need to know which one, please!

[SIZE=3][COLOR=Red]**_edit>>> OK, i saw your edit.. that still doesn;t say which language you used. Sorry for being obstinate, bu I really need to know!_**[/COLOR][/SIZE]

Well, I don't really know :).  I just thought it was a shell script, and it was the BASH *type* or something :p

glad someone explained it :p

---

### Post by st14n on 2007-09-29
Not sure what you mean by "Create a color scheme/ GUIish looking thing inside the terminal", but there is a program called zenity ([FONT="Courier New"]sudo aptitude install zenity[/FONT]) which provides simple dialog boxes that may work as a simple GUI. However, not *inside* the terminal. [FONT="Courier New"]man zenity[/FONT] gives you some documentation on available options. 

It may be used as follows:

[PHP]#!/usr/bin/env python

import os, commands

zen = 'zenity --list --radiolist --title "Project title" --column Select --column Options TRUE "Option 1" FALSE "Option 2"'
choice = commands.getoutput(zen)
if choice == "Option 1":
    os.system("sudo apt-get update && sudo apt-get upgrade")
elif choice == "Option 2":
    os.system("sudo apt-get clean && sudo apt-get autoremove")[/PHP]

---

### Post by ryanVickers on 2007-09-29
I said that already (*to some extent* :))

Look at my RAR maker, and you'll get the idea of what he means! :p

---

### Post by 1337455 10534 on 2007-09-29
To ryanVicks: thanks for your RAR maker, is it OSS? I'd LOVE to take a look at your code. And sorry for being sucha total n00b.

To walkerk: you just made my day.

I found a book at the library that explains how to make a GUI w/ pyGTK so that + the os mod i should be rolling.

I will deinately take a look at zenity. To explain what i meant before; anyone try to reconfigure X.org in the terminal? Know how the terminal expands into a square, and it has a grey, blue, and pink color scheme? That is what I want, albeit different colors. Another example, reinstalling Windows XP has the exact same color scheme (but not in a console).

I really love this community!! You guys rock!

---

### Post by 1337455 10534 on 2007-09-29
[email]vminch@gmail.com[/email]

for UMER! news

---

### Post by ryanVickers on 2007-09-29
You know what else is annoying (for junk files :))?  Well, this'll clean 'em up!

```

#!/bin/bash
echo
echo "=============================================="
echo "=     Will now display all useless files     ="
echo "=============================================="
echo
find $HOME -name "*~"
find $HOME -name "Desktop.ini"
find $HOME -name "Thumbs.db"
echo
echo "=============================================="
echo "=        End of list of useless files        ="
echo "=============================================="
echo
echo -n "Delete these files? (y/n): "
read sure
if [ $sure == "y" ]
then
find $HOME -name "*~" -print0|xargs -0 /bin/rm -f
find $HOME -name "Desktop.ini" -print0|xargs -0 /bin/rm -f
find $HOME -name "Thumbs.db" -print0|xargs -0 /bin/rm -f
sudo deborphan | xargs sudo apt-get -y remove --purge
sudo apt-get autoremove
sudo localepurge
echo
echo "=============================================="
echo "=     Answer is yes - Files were deleted     ="
echo "=============================================="
echo
elif [ $sure == "n" ]
then
echo
echo "=============================================="
echo "=      Script aborted - Files were kept      ="
echo "=============================================="
echo
else
echo
echo "=============================================="
echo "=   Not a proper answer! - Files were kept   ="
echo "=============================================="
echo
fi

```

---

### Post by 1337455 10534 on 2007-09-29
Are those useless?

---

### Post by ryanVickers on 2007-09-29
yesh, pretty much!  the thumbs and desktop things are windows junk, and the "~" on the end files are just useless old copies of files :)

the other stuff that it doesn't chow or ask about it packages/dependencies that were removed but not completely, or are useless (unused dependencies).

---

### Post by walkerk on 2007-09-29
another prompt method instead of echo + read

```
read -p "What is your question? " answer;

print $answer
```

---

### Post by ryanVickers on 2007-09-29
ok, that might come in very handy (somewhere else though... :p)

---

### Post by walkerk on 2007-09-29
> **walkerk said:**
> another prompt method instead of echo + read

```
read -p "What is your question? " answer;

print $answer
```

> **ryanVickers said:**
> ok, that might come in very handy (somewhere else though... :p)

lol.. that was after your bash post :P

<back to python mode> :P

---

### Post by ryanVickers on 2007-09-29
:???::-k:-s

---

### Post by walkerk on 2007-09-29
> **ryanVickers said:**
> :???::-k:-s

right. because that doesn't make sense. enough forum for one weekend.

---

### Post by ryanVickers on 2007-09-29
still don't get what your trying to say! :p

---

### Post by st14n on 2007-09-30
> **ryanVickers said:**
> yesh, pretty much!  the thumbs and desktop things are windows junk, and the "~" on the end files are just useless old copies of files :)

I agree on the windows junk, but the backup files have saved me several times.  However, I find it ugly it have them scattered all over the file tree, so instead I save them in one specific backup folder. In Emacs, which I use, this is pretty simple to do, but I don't know with other editors. For instance, one time I did [FONT="Courier New"]rm *[/FONT] in the wrong directory. (Stupid, i know.) No problem since the backups were in another directory. :) But if you find them useless, feel free to delete them of course.

I know this is not the topic of the thread. Only thought I should mention it...

---

### Post by ryanVickers on 2007-10-07
But they don't even save a copy of what you just did, they save a copy of how it was *before* the save!  I just don't trust them - If I wanted a backup, I'd do it manually :)

---

### Post by 1337455 10534 on 2007-10-15
Will the os.system command work while dealing with rpm, pacman etc.? How about in different desktop environments (KDE, GNOME, Fluxbox, Xfce)?

---

### Post by ryanVickers on 2007-10-15
I never thoughs about that before - adding support for distros other than ubuntu/debian is a great idea, and I think if it has repos, and a command for them, like ubuntu (apt-get install...), then it should work fine!  As for other Desktop environments, Xfce, KDE, and Gnome are a go for sure - I cna't think of a single reason why it wouldn't work with one of them unless your using DE specific tools (like zenity ;) (but it auto-installs it if necessary :)))

---

### Post by 1337455 10534 on 2007-10-15
Thank you very much for a quick reply ryan.
Yea, it changed names, again, when my dad got ahlod of it.
It is now iLinux, and I am working on support for Fedora, RedHat, openSUSE, Ubuntu(s), Puppy, Arch, Mandriva, and DSL :). It'll take a while.

No GUI tho.

P.S: Love the new avatar. Where do you guys get those???

---

### Post by ryanVickers on 2007-10-15
avatar: tux.crystalxp.net

"changed names": ?!? ;)

Quick reply: yeah, I track these things and have a response in about 10 minutes unless solar flare radiation is intercepting my internet connection, or I'm at school :p

---

