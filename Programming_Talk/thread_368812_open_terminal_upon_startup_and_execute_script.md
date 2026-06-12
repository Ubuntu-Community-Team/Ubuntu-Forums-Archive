---
title: "open terminal upon startup and execute script"
date: 2007-02-23
forum: Programming Talk
---

### Post by gtratter on 2007-02-23
Hello folks;

Since I am a NooB I start with simply things - or so I think. I made a simple shell script called *myscript*. When I execute it from the command line I get something like this:

```
gt@gt-laptop:~$ myscript


Greetings! Say, you are looking mighty sharp on this fine Friday!

Just so you don't get confused, today's date is 02/23/07

You were most recently working on testx.txt.

Your shell is /bin/bash 

You are in directory /home/gt 

Your current file system looks like this: 
 Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4             37358288   4787628  31052520  14% / 

OK, time to get to work now! 

gt@gt-laptop:~$ 

```

That is all working fine - next I thought - how cool would it be upon starting up to open a terminal window automatically and execute the script. I thought that something as simple as
```
gnome-terminal --execute myscript
```
would do the trick.  I was trying this with putting this line into *System - Preferences - Session - Startup Programs*. I am thinking it should work because *gnome-terminal* is a program and the *--execute myscript* would be the instruction to the program.

Where am I wrong here?

---

### Post by kerry_s on 2007-02-23
Try> gnome-terminal -x myscript
or try xterm
xterm -e myscript

---

### Post by gtratter on 2007-02-23
**kerry_s**

thanks - I should have said in my original post that I tried that. The result is the same - I get a short flash of a terminal window and that is it - very puzzling!:?:

---

### Post by 23meg on 2007-02-23
In the "Title and Command" tab of your gnome-terminal profile settings, choose "Hold the terminal open" in the "When command exits" combo box.

---

### Post by kerry_s on 2007-02-23
There should be a hold command, try reading the man pages.

---

### Post by gtratter on 2007-02-24
> **23meg said:**
> In the "Title and Command" tab of your gnome-terminal profile settings, choose "Hold the terminal open" in the "When command exits" combo box.

THAT did the trick - now I am being greeted with my personal logon when I start-up - I know its korny but, heck but these are my first baby steps......

[I]
Greetings! Say, Gerhard - you are looking mighty sharp on this fine Friday!

Just so you don't mix up your dates, today is 02/23/07

You are in directory /home/gt and you were most recently working on Images/.

Your shell is /bin/bash and the available WiFi connection is innsbruck 

Your current file system looks like this: 
 Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4             37358288   4787368  31052780  14% / 

If you don't have the time to look out the window - here is the weather: 
 City: Los Angeles, CA (90049)
    Temp:         51F
    Cond:          Clear
    Wind:          11mph (NNW)
    Tomorrow:  48F to 67F
    Forecast:     Sunny 

[/I]

Just in case there are other who are just starting to learn about scripts here is the shell script which creates the above output:

```
 
#! /bin/sh
#       this is my first shell script
#
echo "\n"
echo "Greetings! \c"
echo "Say, Gerhard - you are looking mighty sharp on this fine `date +%A`!\n"
echo "Just so you don't mix up your dates, today is `date +%D`\n"
echo "You are in directory `pwd` and you were most recently working on `ls -1Fc ~/ | head -1`.\n"
echo "Your shell is `echo $SHELL` and the available WiFi connection is `/home/gt/Scripts/./wifi.sh` \n"
echo "Your current file system looks like this: \n `df -k /home` \n"
echo "If you don't have the time to look out the window - here is the weather: \n `/home/gt/Scripts/./weather.sh 90049` \n"



```

---

### Post by Emmtor on 2010-06-05
I had the exact same problem with gtratter! thanks for posting!

---

### Post by switchrodeo720 on 2010-06-19
I have also had the desire to run a command/script/nautilus-script and have the gnome-terminal window stay up longer. My solution was to wrap the script/command in a 'while true; do' loop, which has it's own advantages over holding open the terminal window using the settings mentioned above. 

I recently wrote a script to display my file system information and provide me with the option to refresh the results. Here is the final code:

```
#!/bin/sh

while true
do

	echo "File system usage:"
	echo "Filesystem\t      Size  Used Avail Use% Mount Point"
		df -h | egrep "^/dev"
	echo
	echo "Enter [q] to exit or [r] to refresh:\c"
	read status
	if [ $status = "q" ]
	then
		exit 0
	elif [ $status = "r" ]
	then
		clear
	fi
done
```

This can be called from the command line, from a keyboard shortcut or from a nautilus script. If launching from a keyboard shortcut, use a command like this:

```
gnome-terminal -x sh /path/to/file/script.sh
```

---

