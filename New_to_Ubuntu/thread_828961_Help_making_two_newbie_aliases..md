---
title: "Help making two newbie aliases."
date: 2008-06-14
forum: New to Ubuntu
---

### Post by fredscripts on 2008-06-14
Hi!!!


I'm trying to get comfortable using terminal so I wanna make some basic stuff trough it.

1)  Some kind of "trash" program, that sends the files passed by argument to the Trash. Kind of an alias to run:

```
mv myfile ~/.local/share/Trash/files
```

So I could run:
```

trash myfile
```

And then acts like if I had removed with GUI Gnome right button and remove.

2) An easy one alias called "emptytrash" to empty the trash by terminal, seems something like an alias to the command:

```
rm -r ~/.local/share/Trash/files/*
```


So, it has been a long time since I did an alias, I remember I had to edit some ~/.bashrc file and add like "alias=command" stuff. Anyone could help me with those little aliases? (the fist one as it seems to take arguments maybe could be better a bash script, but I don't know too much about them, so a little guide on that would be appreciated)

Thank you very much in advance!!!

---

### Post by Gannon8 on 2008-06-14
Most of the time if you want to remove a file in the terminal, you would use rm anyway.

I guess the trash command is a shortcut though, if you want a backup.

---

### Post by fredscripts on 2008-06-14
Thanks for answering!!!

Yep I know about rm command, but as it removes the file completely from the file system, I would like to have a "trash" command which just move its to the trash.

Anyone can help me with the steps to get those aliases?

Thanks in advance!

---

### Post by fredscripts on 2008-06-14
No one? :(

At least if you could tell me if the correct process to make an alias is adding to ~/.bashrc a line like

alias=command_here

and if the commands I've posted are the correct for my purposes I'd be very grateful.

Thanks in advance!!

---

### Post by fredscripts on 2008-06-14
OK!! I've got it :)

for the first part I just did a simple python script:
```

#!/usr/bin/python
import os
import sys


for file in sys.argv[1:]:
	os.system("mv "+file+" ~/.local/share/Trash/files/")

```

saved as "mtrash" and then put in in the path with adding this line to ~/.bashrc file:

```
export PATH=$PATH:~/pathscripts/
```

Assuming you have chmod a+x mtrash and you have it on the directory ~/pathscripts


For the second part I just did an alias, adding this line to ~/.bashrc file:

```
alias emptrash='rm -r ~/.local/share/Trash/files/*'
```

So I can use the mtrash like if I did right-click and Move to trash in a GUI, and emptrash to empty the trash.

I think this is a good exercise to feel comfortable with terminal and learning basic things like adding your programs to the path, making aliases, and basic scripts, so I hope someone likes it :)

---

### Post by the_doc on 2008-06-14
I do!

---

