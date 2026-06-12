---
title: "Command New Tab Terminal"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by TzaB on 2008-07-25
Hello all, i am trying to find how i can open a new tab at a terminal window.

Basically, i want to find a solution to write a shell script that will open up a new tab in terminal and then run a command on the new tab.

I searched at Google and i used "man gnome-terminal".
From the manual i tried the command "--tab-with-profile" and also other commands that was listed, but i am not able to find the solution.

If you can help, please post a reply. 
Thanks

---

### Post by gimlithedwarf on 2008-07-25
you can add a launcher to the top panel or to the desktop that runs a script in a terminal and you could probably set up the gnome preferences to run it on a hotkey as well. Hope that helps

Gimli

---

### Post by bab1 on 2008-07-25
Are you trying to run a script in the background?  If so, run the script and add a " &" (no qoutes) at the end.

---

### Post by faytaliti on 2008-07-25
Try Terminator, it allows you to have multiple tabs in a gnome-terminal window. It is available in the Ubuntu repository. :popcorn:

---

### Post by TzaB on 2008-07-25
Thanks for your replies. 

But i am trying to do the following:

I want to write a script that will open a new tab at terminal and return what a log file has on it.
After this, a new tab will open and will return what another log file has on it .

For example

tail -f name.log (and this appearing to a tab)
tail -f name1.log (and this appearing to another tab)

---

### Post by run1206 on 2008-07-25
i use the default Gnome terminal (i setup the Keyboard Shortcuts from Preferences and did Alt+F11 to start a terminal)
and do Ctrl+Shift+T and i get a new tab in my terminal (and Ctrl+Shift+W to close a tab). 
not too sure how to do scripts, so i wouldn't be any help with the log part though, sorry :(

---

### Post by DGortze380 on 2008-07-25
> **TzaB said:**
> Hello all, i am trying to find how i can open a new tab at a terminal window.

Basically, i want to find a solution to write a shell script that will open up a new tab in terminal and then run a command on the new tab.

I searched at Google and i used "man gnome-terminal".
From the manual i tried the command "--tab-with-profile" and also other commands that was listed, but i am not able to find the solution.

If you can help, please post a reply. 
Thanks

If you right click on the script you have the option to "run in terminal". Just make sure you put a read statement or something at the end of the script so that it doesn't close the terminal until you hit enter.

---

