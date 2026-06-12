---
title: "TIP: a simple concept of launcher"
date: 2006-08-08
forum: Outdated Tutorials &amp; Tips
---

### Post by dragobr on 2006-08-08
First of all, i'd like to apologize for my bad english. Im brazilian and im kind of new here ;) 

Inspired by a windows program called [SlickRun]("http://www.bayden.com/SlickRun/"), I decided to create a "dialog box launcher". I don't like shortcuts, i think they're not pratical. I don't like to memorize hot keys for different apps, either. So i found SlickRun for Windows, a "floating command line" utility that allowed me to open files, programs and websites just typing what I wanted in a box that comes up after pressing a single combination of keys.

Missing this in my openbox (there are some programs and applets that you can use in gnome... but i don't know if you could customize them as much as someone might like to), i decided to try to create something like that using shell script. Im not good at all in this, but I think that i managed to create a script that filled my necessities. For me, this is the best way to get what i want in the screen as fast as i want.

I used, as a "front end", a utility called zenity. In order to open a dialog box in the screen with a text and a text box, you can type this in a terminal:

zenity --title="Launcher" --text="What do you want to open?" --entry

You can keep what is written in the textbox using a variable, like this:

var=`zenity --title="Launcher" --text="What do you want to open?" --entry`

with this, i created a simple script that compares what i type in the textbox and opens the respective program... a little example:

```
#!/bin/sh

output=`zenity --title="Launcher" --text="What do you want to open??" --entry`

if [ $output = "gaim" ]
then
	exec "gaim"
fi
```

After saving this file as "dlauncher" in /usr/bin, making it executable with chmod +x /usr/bin/dlauncher and adding a hotkey (for example, CTRL+Q) for opening it, i was able to just press CTRL+Q and type "gaim" for opening gaim...

A more complex file, with the programs i use more often and some tricks like permiting the launcher to open a web site when you type "www.some-thing.com" or to open a directory after typing "nautilus /some/directory", is attached to this post

I hope this can be useful for someone :D This works great for me...

---

### Post by Tamihania on 2006-08-09
Excellent idea! Thank you :) 

I will try it out soon and perhaps give you some feedback.

tami

---

### Post by moma on 2006-08-09
Good idea,

You can allow user to type only part of the command name.
Examples:
"ga" will start gaim.
"wri" will start OpenOffice writer.

```
case "$output" in 

   gaim|ga*) 
      echo "Starting gaim"
      gaim
     ;;

   wri*)
      echo "Starting writer"
      writer
   ;;

   gi*)
      echo "Starting the gimp"
     gimp
   ;;
 
  fi*)
     echo "Starting firefox"
     firefox

    *) 
     echo "Bad command"
     exit 0
esac
```
Ubuntu has already a "Deskbar" applet that does the same.
Right-mouse-click on the main toolbar panel and "Add to panel..."

---

### Post by crackseller on 2006-08-09
erm Alt+F2 does the job :o

---

### Post by ounn on 2006-08-09
Is something like this thar you are looking for?

[http://developer.imendio.com/projects/gnome-launch-box](http://developer.imendio.com/projects/gnome-launch-box)


ounn

---

### Post by Tomosaur on 2006-08-09
Yeah, maybe I'm missing something. Is this any different to Alt+F2? I can't see any differences in the script.

---

### Post by dragobr on 2006-08-09
you can customize this script to fit your needs... like, with ALT-F2, you can only execute commands that are avaible in the console (at least i think, i dont use gnome), but with this script, you can open a program and pass a lot of parameters to it only typing one word.. and, for example, i think its not possible to open a site just typing the url, just to say an example of what one might do with this script.. (to see others, look at the attached file)

the "Deskbar" is ugly, in my opinion, i dont know if i can customize its commands and it have to stay in the panel... i dont like it very much

and i think it would be better to edit the topic to point something: i use openbox, and yes, i think this script would be more usefull for ppl who dont use gnome :)

edit: thanks for the hint, moma.. ill try that ;)
edit2: i uploaded a screenshot of the script running here on my openbox

---

### Post by Tomosaur on 2006-08-09
You can pass programs paramaters with alt+f2 :/ 

The problem with your script is that you need an if statement for every possible command the user inputs, rather than just saying 'exec "$output"' and letting the shell sort out the errors.

---

### Post by dragobr on 2006-08-09
but if you have a program that you always open it with a lot of parameters, youll always have to type them into alt+f2.. with this script, you can use always just a single word that you choose, this is my point.. this is where the alt+f2 lacks customization

and yes, youll have to create an if for every possibility.. but for me, its not a real problem.. maybe a front end for it might help

---

### Post by Tomosaur on 2006-08-09
Fair enough, I just use a shortcut and stick it on my top panel though :P

---

### Post by dragobr on 2006-08-09
fair enough... :)

what I brought here is just another way that might be better for some ppl.. I don't like shortcuts.. as I said, I don't think they're pratical... I know that for most people, it is.. its just a matter of taste :)

---

### Post by Nate53085 on 2006-08-09
> **dragobr said:**
> but if you have a program that you always open it with a lot of parameters, youll always have to type them into alt+f2.. 


Thats what aliases are for

---

