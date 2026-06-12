---
title: "How to start programs after startup."
date: 2007-03-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Max Randor on 2007-03-30
During testing on Ubuntu Edgy when I was working out how to do this the only thing that went wrong was that nothing happened :) , I think Gnome's startup programs utility is capable of withstanding broken scripts.

Sometimes you want programs to be running all the time when your computer is on, but you don't want  them to startup on startup because you want to run the programs that you want to use right away first and then let things like gdesklets and instant messenger clients run.
Now while in Ubuntu there does not seem to be an GUI setup way of doing this it is still very easy.

This will involve writing a very simple script, the second one I ever wrote.
A script is a text file with a .sh extension, it gets executed by bash and so it is like typing lots of commands into the terminal one after the other but much easier.
First open a text editor like gedit.
This is an example of my script, only two lines long
```

sleep 30s; gdesklets &
sleep 30; skype

```
sleep is a program that makes another program start after a certain period of time
The 30 is number of seconds after startup I wanted the gdesklets to startup. The s stands for seconds (you can use m for minutes or h for hours).
The ; is very important, without it it won't work.
Then gdesklets is the program I wanted to run first
If you wanted all your new programs to start one after the other then you don't want to include the next sleep 30s; as this is the time delay AFTER the original time delay.
e.g. gdesklets starts after 30 seconds, skype starts after 60 seconds.

Now when you have finished writing your script you need to save it. I saved mine as late_startup.sh and put it in /home/user/.local/bin/ (because then I would be able to run it from the terminal without having to specify the path.

next, System --> Preferences --> Sessions

click on the Startup Programs tab. You will see all the programs you have starting at startup, press +Add and either use Browse to go and find your script or just type in: /home/user/.local/bin/late_start.sh
Or whatever your path and script is called.
Now your script _should_ run at startup and start your programs after the time period you specified.
Hopefully this will let you open the programs you want to use faster without having to wait for your eye candy and instant messengers to load first.

Note: it may be good practice to write ```
#!/bin/bash
``` at the beginning of your script (not tested) I didn't and it worked so I am not including that in my example.
Enjoy.

---

### Post by siralphred on 2007-10-08
thanks for the guide, used it to delay start my screenlets as compiz needs to be running before screenlets

EDIT: its important to change the scripts permission to "Allow Executing File as Progam" u can do that by right clicking> Properties> Permisions

---

### Post by graingert on 2007-10-25
Is there any way to check if compiz has started then run?

For example a loop around ```
top | grep compiz
```

any thoughts?

---

### Post by Max Randor on 2007-10-25
Probably but I do not yet know enough about linux to be able to do that sorry. Maybe someone else can help though, and if you do find the way please post it or a link to it here. Thank You and good luck.

---

