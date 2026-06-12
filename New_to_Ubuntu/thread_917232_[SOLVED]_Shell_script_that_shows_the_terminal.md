---
title: "[SOLVED] Shell script that shows the terminal"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-09-11
I have a script to start recording from my tv card. I need to run the command from a terminal, in order to monitor the recording and also to stop it when I want.

But I want to be able to click a button in the desktop and start recording. So I have created a shell script and saved into ~/bin 

It works, but the problem is that the terminal is not displayed when running the shell script file. Is it possible to write a script in which the terminal is displayed?

---

### Post by NESFreak on 2008-09-11
instead of just running the script try running "gnome-terminal <the script>"

---

### Post by lovinglinux on 2008-09-11
> **NESFreak said:**
> instead of just running the script try running "gnome-terminal <the script>"

Already tried that, but it gives me an error "There was an error creating the child process for this terminal"

---

### Post by Pro-reason on 2008-09-11
You should be able to use “gnome-terminal -e **YOURCOMMANDS**”, but it doesn't work for me.

---

### Post by lovinglinux on 2008-09-11
> **NESFreak said:**
> instead of just running the script try running "gnome-terminal <the script>"

I'm so stupid! I was adding "gnome-terminal" to beginning of the script line instead of creating a launcher with "gnome-terminal -e thenameofthescriptfile".

It works now, thanks.

---

