---
title: "List title name of processes"
date: 2013-04-11
forum: Programming Talk
---

### Post by PlasticoBolha on 2013-04-11
Hi all.
I'm a bit new in programming in Java but I'm learning. I'm making a program, and I need to list all processes names and PID.

I could print here the code but theres no need. The key line of the program is ' [COLOR=#333333][FONT=lucida grande]Runtime.getRuntime().exec("ps") '.[/FONT][/COLOR]
[COLOR=#F0F0F0][FONT=Lucida Grande]
[/FONT][/COLOR]That means that is like I write "ps" in the terminal window and then I work with the results. The output that I got with "ps" is:

```

[COLOR=#333333][FONT=lucida grande]PID   TTY  TIME       CMD                
1312 ?      00:00:01 gnome-session
1351 ?      00:00:00 dbus-launch
1362 ?      00:00:00 dbus-daemon
[/FONT][/COLOR][COLOR=#333333][FONT=lucida grande](...)
[/FONT][/COLOR]
```[COLOR=#333333][FONT=lucida grande]

[/FONT][/COLOR]Now that's good but it's not enough. I need a new colum that presents the name that is written in the title bar. For example now I'm in google chrome writing this post. I need to list something like this:

```

[COLOR=#333333][FONT=lucida grande]PID   TTY  TIME       CMD                 (something)
1312 ?      00:00:01 chrome             General Help - Post New Thread - Google Chrome
(...)
[/FONT][/COLOR]
```[COLOR=#333333][FONT=lucida grande]
[/FONT][/COLOR]
Is it possible?

---

### Post by brainwash on 2013-04-11
One possible solution (joining tables):
```
brainwash@local:~$ sudo apt-get install wmctrl
[sudo] password for brainwash:
...
brainwash@local:~$ wmctrl -l -p
0x04a00523  0 7318   local [ubuntu] List title name of processes' - Reply to Topic - Mozilla Firefox
brainwash@local:~$ pgrep firefox
7318
```
More information about the command-line tool wmctrl:
```
man wmctrl
```

---

### Post by PlasticoBolha on 2013-04-11
Thank you! That's enough for me :)

---

### Post by rnerwein on 2013-04-12
> **PlasticoBolha said:**
> Hi all.
I'm a bit new in programming in Java but I'm learning. I'm making a program, and I need to list all processes names and PID.

I could print here the code but theres no need. The key line of the program is ' [COLOR=#333333][FONT=lucida grande]Runtime.getRuntime().exec("ps") '.[/FONT][/COLOR]
[COLOR=#F0F0F0][FONT=Lucida Grande]
[/FONT][/COLOR]That means that is like I write "ps" in the terminal window and then I work with the results. The output that I got with "ps" is:

```

[COLOR=#333333][FONT=lucida grande]PID   TTY  TIME       CMD                
1312 ?      00:00:01 gnome-session
1351 ?      00:00:00 dbus-launch
1362 ?      00:00:00 dbus-daemon
[/FONT][/COLOR][COLOR=#333333][FONT=lucida grande](...)
[/FONT][/COLOR]
```[COLOR=#333333][FONT=lucida grande]
[/FONT][/COLOR]Now that's good but it's not enough. I need a new colum that presents the name that is written in the title bar. For example now I'm in google chrome writing this post. I need to list something like this:

```

[COLOR=#333333][FONT=lucida grande]PID   TTY  TIME       CMD                 (something)
1312 ?      00:00:01 chrome             General Help - Post New Thread - Google Chrome
(...)
[/FONT][/COLOR]
```[COLOR=#333333][FONT=lucida grande]
[/FONT][/COLOR]
Is it possible?

[COLOR=#333333][FONT=lucida grande]hi
mostely you ain't need to install new software. just have a look at the manual pages. here ps.
enlarge your terminal window and type (you ain't need the sudo): ps aux (i think this is what you want) ;-)
ciao[/FONT][/COLOR]

---

### Post by ronald577 on 2013-04-12
Thanks for the code.

---

### Post by PlasticoBolha on 2013-04-12
Well, I've looked up and I didnt find anywhere in the documentation of "ps" and in the internet... I need the name in the bar, not the name of the process...

---

### Post by oldos2er on 2013-04-12
Moved to Programming Talk.

---

### Post by Vaphell on 2013-04-12
ps definitely won't tell you window titles, window manager knows these things and you can probe it it via mentioned already *wmctrl*

---

### Post by PlasticoBolha on 2013-04-12
Well, if someone got a sugestion to do that without installing anything new please feel free to tell me :) For now I'm satisfied. Thank you all.

---

