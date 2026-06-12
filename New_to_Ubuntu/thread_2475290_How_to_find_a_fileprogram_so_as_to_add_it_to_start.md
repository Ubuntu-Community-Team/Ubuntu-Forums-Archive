---
title: "How to find a file/program so as to add it to startup items"
date: 2022-05-21
forum: New to Ubuntu
---

### Post by jonfisher on 2022-05-21
What would one do or type into terminal to find a program/file so as to be able to add it to startup applications.
For example, I'd like to add the Weather app/program to startup applications...

p.s. Where do most programs/apps go when they are installed - into which folder or path?

---

### Post by TheFu on 2022-05-21
Multiple ways.

If there is a menu entry for the program, then there is a .desktop file for it somewhere.  Inside that .desktop file, there's an **Exec=** line.  That's the command run.

If the program is currently running, you can see the name almost always in the process table.  There are many ways to get a list of those things. top, htop, ps are the normal commands.  On my system, right now, there 642 items in the process table.  top and htop show the processes using the most CPU, so if I want to see a specific program in the list, I'll cause it to use CPU and it will jump to the displayed "top" processes, where I can see the name in the right column.  With that name or partial name, I can ask for the full process table using 
```
ps aux |grep -i {partial name}
```

I have an alias for ps with a grep ... psg:
```
$ psg alarm
tf       12719 12702  0 May14 ?        00:53:05 /usr/bin/alarm-clock-applet
```

There's also the built-in pgrep, 
```
$ pgrep  alarm
12719

$ pgrep  -a alarm
12719 /usr/bin/alarm-clock-applet
```
It has some options.

Now I have a program file name and can use any tool that looks for locations on the system for that program name.  I'd use **locate** first, because it is the fastest and anything on the system since over a day will be found.  Locate isn't installed by default. The package name has changed names over the decades for some reason. I think **mlocate** is the current package.

So, if I had an automatic startup capability on my system, I'd use /usr/bin/alarm-clock-applet in that.  I actually have a custom startup script that only gets run under specific situations. It starts about 15 terminals and places them in specific locations, minimizes some, starts gnubiff and ... the alarm-clock tool. I have an issue losing track of time at the computer. ;)

---

### Post by ajgreeny on 2022-05-21
The command ```
which <application>
``` may also be helpful to you but it is necessary to get the application name absolutely correct or it will show nothing.

EG, command ***which firefox ***shows output of ***/usr/bin/firefox***

---

