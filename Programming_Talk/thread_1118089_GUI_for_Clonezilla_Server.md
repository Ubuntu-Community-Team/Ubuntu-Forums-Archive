---
title: "GUI for Clonezilla Server"
date: 2009-04-06
forum: Programming Talk
---

### Post by Wickd on 2009-04-06
Hi there

I am not a total noob but ito programming in Linux I am. I would like to develop a Graphical User Interface for the Clonezilla server. This cant be a difficult task, but I need to create and execute a terminal command in the terminal.

For example:

How would I execute the following DRBL command:

/opt/drbl/sbin/drbl-ocs -b -q -j2 -p reboot -z1 -i 0 -l en_US.UTF-8 startdisk save 2009-04-07-00-img sda

This command gives the basic image save command with some extra features.

I would like to use Perl and wxWidgets to do this, but not very familiar with them yet

Thanks for the help

---

### Post by coolaj86 on 2009-04-06
If you know perl then this might interest you.

[http://wxperl.sourceforge.net/documentation.html#Tutorials](http://wxperl.sourceforge.net/documentation.html#Tutorials)

If you don't, I'd suggest using python instead. It seems that many desktop apps are extended with python (rhythmbox, amarok, openoffice, etc). It seems easier to understand than perl, IMHO.

Sorry if that isn't the answer you're looking for, but your question is a bit vague.

---

### Post by Wickd on 2009-04-07
Haha. yeah my terminology sucks at the moment.

So here goes, I want Python to 'access a terminal' and 'type in' a command, like the one above?

Thanks for the help so far

---

### Post by coolaj86 on 2009-04-07
The 'os' module handles system execs. The function you want from that module is 'system()'.

```
#!/usr/bin/python
from os import system
system('echo "hello world"')
```

or 

```
#!/usr/bin/python
import os
os.system('echo "hello shoebox"')
```

---

### Post by Wickd on 2009-04-08
Thanks dude. That hit the spot!!

---

