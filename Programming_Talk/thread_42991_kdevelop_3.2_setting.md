---
title: "kdevelop 3.2 setting"
date: 2005-06-20
forum: Programming Talk
---

### Post by oldmarti on 2005-06-20
Hi. I just install kdevelop 3.2 and try compile simple hello world project. All is done, but when I try to start program I receive : "konsole command not found". I try to change in "Configure Kdevelop" Terminal Emulation to gnome-terminal but receive "... invalid argument ...". 
Which packages are required to make Kdevelop happy? I like gnome desktop, and don't want change it to kde. Thanks

---

### Post by somuchfortheafter on 2005-06-20
if you wish to have a better dev app / enviroment you may wish to try ajunta its really good...

---

### Post by Kimm on 2005-06-20
yes Anjuta kicks butt [img]http://ubuntuforums.org/images/smilies/eusa_angel.gif[/img]

but if you want kdevelop you can just do a simple "apt-get install konsole" to get it happy :) I think... xD

---

### Post by oldmarti on 2005-06-21
Thanks. I use anjuta too. But have an old project written with kdevelop. With apt-get install konsole kdevelop work fine (for now ;-))

---

### Post by Kimm on 2005-06-21
I just realized that there is something else you can do, so just apt-get remove that filty konsole now :P

it doesnt involve any installing of anything, just the creation of a link

typ this in console:

> 
sudo link /usr/bin/gnome-terminal /usr/bin/konsole


that should work, I just did the same thing but oposite, I wanted to use xterminal instead of gnome-terminal, but anjuta still refused to use it, so I uninstalled gnome-terminal and did something similar to that above:

> 
sudo link /usr/bin/xterminal /usr/bin/gnome-terminal


if you change your mind, just rm -f /usr/bin/konsole and reinstall konsole ^^

[i]Edit:

Note that I didnt try this with KDevelop, but it should work fine there to[/i]

---

### Post by oldmarti on 2005-06-23
The trick with link don't work ;-))
The problem is that kdevelop start terminal with command:
konsole -e /bin/sh -c './hello ; echo "Press Enter to continue!"; read dummy'
but this command failed when use gnome-terminal insted konsole.
Error; Invalid argument: "./hello echo "Press Enter to continue!"; read dummy"
I think - here is a little difference between konsole and gnome-terminal in parsing input line.

---

### Post by Kimm on 2005-06-23
I supose, but then again I said It might not work :-P

---

