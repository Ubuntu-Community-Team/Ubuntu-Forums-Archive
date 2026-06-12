---
title: "alt f2 does seem to run command"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by rccharles on 2013-04-15
I'm running 2011 - 10.  I'm running the default desktop.  It's the Mac OS X like icons on the left. 


I read somewhere about alt f2.  alt f2 does bring up a command prompt.  I entered terminal.  I see icons for terminal, top, and screen shot.

I tired clicking on terminal.  I pressed enter.  Screen disappeared, but I didn't get into terminal.  :(

How do i run a command from alt f2?

What's the easiest way to get to terminal?

Robert

---

### Post by r-senior on 2013-04-15
You have three choices:

1. Alt-F2 and type "gnome-terminal" (literal command)
2. Super (Windows) key and type "terminal" (intelligent search for programs)
3. Ctrl-Alt-T (shortcut for terminal)

Once the terminal is running, you can right click on the icon in the launcher (the icons on the left) and "Lock to Launcher". The icon then remains when the terminal is closed and you can click on it to run the terminal again.

Alt-F2 runs an arbitrary command. If an icon with gears on it appears in the Dash (the overlay that shows icons), it doesn't mean that there is a program associated with that command, it just means it will run it as if you typed that command at the command line. That's what I mean by literal command above. To do the sort of program search that you appear to be trying to do, the Super key is the one you want.

---

### Post by rccharles on 2013-04-16
Thanks.

What icons I see below are some type of search ressults from the characters I type in?  As many searches do, I get mostly lame answers. What is it searching for?  The results are not all commands?  What is the point?  I mean I get the screen shot icon.  When I click, I get a screen shot.

Now that I think of it, what type of commands can I enter?  top didn't seem to to anything.

---

### Post by deadflowr on 2013-04-17
Run command is really an erroneous name, as it doesn't run command line commands, but launches programs with whatever variable you want , or can set.

It should really be called execute program.

So, lets say you want to open a program, like gedit, and you want to open a certain file.
Normally, you could open gedit then click open and find the file.
Open up the home folder and find the file and open it in gedit.
Open up a terminal and post gedit filename.

But with run command, you can do this without opening any secondary program, as the gedit filename will simply open up gedit at that file.
Whatever options are available depend on the program.
I usually open the terminal and run a quick programname --help to see the various options I can set for that program. Such as opening firefox on a certain page which is not my home page.

---

