---
title: "[Bash] Disable Compiz on Battery or when running specific programs"
date: 2009-07-01
forum: Programming Talk
---

### Post by Shikaku2 on 2009-07-01
Hello all! ):P I'm kind of new to the Ubuntu forums but I made a neat little script.

I posted a thread in the tips and tutorial section as well, but I think I'll make another thread here to also ask for some bash help.

What this script does is disable Compiz when a specific program is running or if you are running off a battery.  It works quite well for me ;) but I want some testers, and suggestions on the finding the programs part.  I think it's correct, but any help is appreciated.

Here is how to work this script, which can also be read if it is run using the -h option or invalid/no options:

> This script allows disabling compiz when: a laptop is running off the battery, and/or when any program from a list of programs is running.
To use, execute this script with one or both of these options (this does not require sudo or root access):
Example (if the script was called autocompiz.sh)

./autocompiz.sh -b -l -s 4

This disables compiz on battery, and disables compiz when any program is running from the list in the file nocompizlist.txt in your home directory (Open places, Home folder, and that is your home directory, or open a terminal and type cd ~), and checks every 4 seconds.

This program only requires -b or -l as an option, but you can use all options.  It is not recommended to use -b if you are not running on a battery at all (i.e, desktop computer).  If the file nocompizlist.txt does not exist in your home directory, it will be created, empty.  If there is an empty list and you use -l the program finding part won't do anything :) The reason I made it this way is that this script allows editing of the program list while running.  Once you add another program it will immediately be in effect when you save the text file.

An example nocompizlist.txt:

wine
pidgin

In short put only the program names by lines, there is no limit to the amount.

It is recommended you put this in the Startup Applications under System, Preferences menu.  Make sure you right click the file, press the Permissions tab and check that it is executable near the bottom and hit ok, then put the location of the script in the command box, and and any options after if desired (remember -b or -l is required).  Then log out and back in to your username.

I tried to make it as user friendly as possible.  Any suggestions for features are welcome as well, including more criteria for disabling Compiz 8)

Also this version is 0.2, the version posted in Tips and Tutorials is 0.1, which had very bad handling of options.  I was hoping the thread would appear already, but I'll post here in the meantime.

---

### Post by Qwertman on 2009-07-29
Sounds cool, but wouldn't this consume battery life and speed as it is an extra process that frequently checks things? If this has a runonce option (rather than running as a daemon) I'd definitely use that. Otherwise I'll give it a shot myself but in the case I fail (I've never really scripted in ubuntu or python for that matter) you may want to consider that function.

---

### Post by piratemurray on 2009-09-06
Hi there I've commented out the section that checks for the optional applications every few seconds. It doesn't seem to have had any negative impact on my laptop so far. I've added my updated verison of the script for all. 

By the way this script is really cool. Exactly what I was looking for!

---

### Post by Sciroccogti on 2010-11-19
Well it does not work on Ubuntu 10.10, I guess this is an old script, to bad its my last gripe I have on Ubuntu. Have to turn off compiz constantly when watching movies or playing games, so I just dont use compiz anymore.

---

