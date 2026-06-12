---
title: "Now what?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Maximusmaximus on 2008-11-18
hello all,

today i downloaded tee worlds a small 2d game and i have no idea how to load it. i have some basic understanding of compiling but i could not find a configure file. i also have python installed and i am fairly sure i have to use that to compile/install the program. i have tryed to learn python commands but none of it really makes sense to me so if anyone could explaine that that would be awesome

[http://www.teeworlds.com/?page=downloads&id=2152](http://www.teeworlds.com/?page=downloads&id=2152)

thanks to all who can help

---

### Post by taurus on 2008-11-18
Seems like you just download, unpack, and run it.  Assuming you've saved it to ~/Desktop and you downloaded the x86 version.  Open a terminal and run

```
cd ~/Desktop
tar xvzf teeworlds-0.4.3-linux_x86.tar.gz
cd teeworlds-0.4.3-linux_x86
./teeworlds
```

---

### Post by tjwoosta on 2008-11-18
> hello all,

today i downloaded tee worlds a small 2d game and i have no idea how to load it. i have some basic understanding of compiling but i could not find a configure file. i also have python installed and i am fairly sure i have to use that to compile/install the program. i have tryed to learn python commands but none of it really makes sense to me so if anyone could explaine that that would be awesome

[http://www.teeworlds.com/?page=downloads&id=2152](http://www.teeworlds.com/?page=downloads&id=2152)

thanks to all who can help

your over-complicating the situation

there is no installing neccesary, just extract and play

simply download the linux_x86 version  (or x86-64 if you have 64bit)

then extract the .tar.gz wherever you want

then open the extracted folder and double click the file that says "teeworlds"

---

### Post by Maximusmaximus on 2008-11-19
> **tjwoosta said:**
> your over-complicating the situation

there is no installing neccesary, just extract and play

simply download the linux_x86 version  (or x86-64 if you have 64bit)

then extract the .tar.gz wherever you want

then open the extracted folder and double click the file that says "teeworlds"

when i double click on teeworlds nothing happens

---

### Post by tjwoosta on 2008-11-19
? 

strange..

it works for me..

what if you use the command line like taurus suggested?

---

### Post by bergersau on 2008-11-19
You probably need to make the file executable.

Either use the command
```
chmod +x *filename*
```
from a terminal.

Or right click on the file and find the tab with the permissions, click on executable and apply or close the dialogue.

Then you should be able to execute it.

---

