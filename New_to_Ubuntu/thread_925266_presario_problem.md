---
title: "presario problem"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by ecuadorche on 2008-09-20
i have a compaq presario pc 

full name is compaq presario sr1630nx

now i have a dual boot off separate hard drives both the installs start up fine 

my problem comes when i try to login to ubuntu.
i put my username and password in and it will go to the desktop
it will show me the background but nothing else and if i right click or do anything with my keyboard it will just take me back to my login screen 

i have no problem reintalling since its in a separate drive from my xp install but im afraid the issue is going to repeat any help would be appreciated

ask me for more specifics if neeeded

---

### Post by ecuadorche on 2008-09-20
sorry to purpsely bump this
thread

but the manner of my question is urgent and i would like to get this pc up and running before monady

---

### Post by GepettoBR on 2008-09-20
Well, you haven't provided much information. Is this happening right after installation, or did you recently install/update anything?

Try this: from the login screen, press ctrl+alt+f1. This will take you to a text-based prompt. Try to login. If you can login, type the following command: ```
/etc/init.d/gdm restart
``` Then press ctrl+alt+f7 to return to the login screen and login normally. Now, if your problem repeats itself, you can go back to tty1 (using ctrl+alt+f1) and see if there are any error messages.

P.S. If the command above does not work, add the word "sudo" before it. This will make Ubuntu ask for your password, you can go ahead and type it.

---

### Post by ecuadorche on 2008-09-20
i just installed the newwest ubuntu
installation went fine 
my problem is when i turn on my computer i can type my name and password and it looks like the desktop is loading but if i do anything the computer will just go back to the login screen 

nothing happens is like a redundant login or something like that

---

### Post by GepettoBR on 2008-09-20
And no error messages showed up?

---

### Post by ecuadorche on 2008-09-20
yeah it gave me no errors 
just a mouse and the ubuntu background and when i did anything its just went back to the login screen

i would like for this computer to run ubuntu

---

### Post by GepettoBR on 2008-09-20
Okay, try this: Log into the command-line mode and type "sudo dpkg reconfigure -phigh xserver-xorg".

---

### Post by ecuadorche on 2008-09-22
when i typed that it gave me this 

type dpkg fro help about installing and deinstalling package
use dselet or aptitude for user friendly package management
type dpkg i hel for a list dpkg debug flag values
type dpkg force help for a list of forcing options 
type dpkg deb help for hel a bout manipelatin .deb files 
type dpkg license for copyright license and lack of warranty

options marked* produce a lot of output pipe it thorugh less or more 


more or less thats what it gave me what should i do with this

---

### Post by ecuadorche on 2008-09-22
i would appreciate anyones help

---

### Post by GepettoBR on 2008-09-22
Another solution is removing your xorg.conf file, and see if the newly generated one works. This can backfire, though, so instead of moving it, we'll rename it. Type this into your command line: 
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
If it does not work, you'll want to undo it. Type this:
```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
There may be other solutions, but this is the last I can think of, short of reinstalling GDM ("sudo apt-get purge gdm && sudo apt-get install gdm" in the command line) and reinstalling Ubuntu altogether. I'm sorry I couldn't be more helpful, but hopefully the xorg.conf trick will do the trick.

---

