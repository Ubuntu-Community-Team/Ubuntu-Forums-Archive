---
title: "Run a sudo terminal command from the Ubuntu Menu."
date: 2008-07-22
forum: New to Ubuntu
---

### Post by fraser-08 on 2008-07-22
Hi all,

Basically I have a command that I would like to run when I click on an icon on the ubuntu menu.

I have right clicked the ubuntu menu and selected Edit menu, navigated to where i wanted the icon (Other > bluetooth PAN connections) and entered the following:
Type: Application In Terminal (I have tried Application)
Name: Connect to Fraser's K850i
Command: sudo pand -c 00:1E:45:B8:FB:5B   (this is the command i would like to run)


Thanks in Advance and i hope you understand what i am trying to do.

---

### Post by freak42 on 2008-07-22
> **fraser-08 said:**
> 
Command: sudo pand -c 00:1E:45:B8:FB:5B   (this is the command i would like to run)

Thanks in Advance and i hope you understand what i am trying to do.

Hi, instead of sudo use gksudo (your command here),
it will open a gui window where you can enter your root password.
hth

---

### Post by Rui Pais on 2008-07-22
> **fraser-08 said:**
> ...
Command: sudo pand -c 00:1E:45:B8:FB:5B   (this is the command i would like to run)


Thanks in Advance and i hope you understand what i am trying to do.

Hi,
just replace the sudo by gksudo

hth

---

### Post by fraser-08 on 2008-07-23
Hi there, I've tried what you said but it doesn't seem to work. It flashes up a window (i persume it is a terminal window) but it quickly disappears. It's too fast to see/read it.
I've tried changing the type to application, but it did not work.

Thanks in advanced. Fraser

---

### Post by Heinzelotto on 2008-07-23
try
xterm -e "sudo pand -c 00:1E:45:B8:FB:5B; sleep 10"
this will open a terminal in which your command is being executed. Then it will wait 10 seconds before it closes. you can make it close instantly by pressing ctrl+c (this will kill the sleep-command).

---

### Post by fraser-08 on 2008-07-23
> **Heinzelotto said:**
> try
xterm -e "sudo pand -c 00:1E:45:B8:FB:5B; sleep 10"
this will open a terminal in which your command is being executed. Then it will wait 10 seconds before it closes. you can make it close instantly by pressing ctrl+c (this will kill the sleep-command).

Thank you, I think that has solved the problem. I ran it there but i didnt have my mobile with me so it couldnt connect but it looked like it worked. Well it opened a terminal window and asked for the root password. (2 terminal windows actually, one was white with nothing in it.)
When i did Control C to break the operation, both windows closed so i dont really care. :lolflag:

Thanks everyone, and I'll get back to you all tomorrow to tell you if it worked or not. 


Fraser

---

### Post by Rui Pais on 2008-08-02
> **fraser-08 said:**
> Thank you, I think that has solved the problem. I ran it there but i didnt have my mobile with me so it couldnt connect but it looked like it worked. Well it opened a terminal window and asked for the root password. (2 terminal windows actually, one was white with nothing in it.)
When i did Control C to break the operation, both windows closed so i dont really care. :lolflag:

Thanks everyone, and I'll get back to you all tomorrow to tell you if it worked or not. 


Fraser

Hi, sorry this late answer been away for a while :) 
Great to know you seems to workaround your issue.

The problem with the suggested replacing of sudo by gksudo is that gksudo only apply to first command (pand) after gksudo. All the rest, in this case "-c 00:1E:45:B8:FB:5B; sleep 10" is ignored.
So the correct solution its to replace the sudo command line by:
```
gksudo "pand -c 00:1E:45:B8:FB:5B; sleep 10"
```
all inside quotes it's passed to gksudo.

---

