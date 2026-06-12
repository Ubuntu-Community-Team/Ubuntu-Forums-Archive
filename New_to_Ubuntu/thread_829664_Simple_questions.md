---
title: "Simple questions"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Jimmy9pints on 2008-06-15
I have been using Ubuntu for a while but there are still some REALLY basic things I don't know. Can you help me out?

Firstly, what is the Linux equivalent of ctrl+alt+del to bring up the task manager?
Sometimes I just need to cancel a program (especially firefox recently) and I don't know how to do this in Linux. Currently I am just reseting my machine because a program has hung. 

Secondly, sometimes, I end up on in a terminal - where I am logged into Ubuntu but there is no graphical desktop...just a cursor. How do I get back into the desktop? Again, I am having to reset my machine to log back into the desktop. 

As you can see, these are super basic questions, so if anyone can point me in the direction of a useful FAQ/tutorial with stuff like this on, please do as I am willing to dedicate time and effort to learning. 

That's it for now. Any help appreciated.

---

### Post by Rocket2DMn on 2008-06-15
> **Jimmy9pints said:**
> I have been using Ubuntu for a while but there are still some REALLY basic things I don't know. Can you help me out?

Firstly, what is the Linux equivalent of ctrl+alt+del to bring up the task manager?
Sometimes I just need to cancel a program (especially firefox recently) and I don't know how to do this in Linux. Currently I am just reseting my machine because a program has hung. 
You can set keyboard shortcuts with Compiz in System->Preferences->Advanced Desktop Effect Settings.  If that isn't there, install the package "compizconfig-settings-manager".  Then go to the General Options plugin, Commands tab.  Expand the Commands and Key Bindings area.  Set a command for "gnome-system-monitor" and Key Binding "<Control<Alt>Delete".
There should be a way to do this for Metacity, too, but it has skipped my mind.

> Secondly, sometimes, I end up on in a terminal - where I am logged into Ubuntu but there is no graphical desktop...just a cursor. How do I get back into the desktop? Again, I am having to reset my machine to log back into the desktop. 
You can get to a TTY by doing CTRL+ALT+F1, login, and run
```
startx
```
or
```
sudo /etc/init.d/gdm start|stop|restart
```

> As you can see, these are super basic questions, so if anyone can point me in the direction of a useful FAQ/tutorial with stuff like this on, please do as I am willing to dedicate time and effort to learning. 

That's it for now. Any help appreciated.
You can always check [https://help.ubuntu.com/](https://help.ubuntu.com/) or [https://help.ubuntu.com/community](https://help.ubuntu.com/community) for help (or google something like "site:help.ubuntu.com keywords"

---

### Post by Malta paul on 2008-06-15
Ctrl>Alt>Backspace will reset like MS ctrl>alt>del.

Check out [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

:)

---

### Post by Rocket2DMn on 2008-06-15
> **Malta paul said:**
> Ctrl>Alt>Backspace will reset like MS ctrl>alt>del.

Check out [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

:)

Yes, CTRL+ALT+BACKSPACE will kill and restart X (the GUI), so you will lose anything else you have open as well.  Remember, you can also open a terminal and kill processes from there.
Something like as follows, you want to kill firefox, so you run
```
killall firefox
```
or
```
ps aux | grep firefox
```
get the process ID (the second column) and kill it by pid:
```
kill -9 <pid>
```

---

### Post by Barriehie on 2008-06-15
About a minute late...

I too have found a need to kill a process and I do this:  I go to a terminal and enter **ps -A**, this will list all of the running process'.  Scroll through the list and when you find the one you want to kill you then enter **kill -9 *pid ***where ***pid ***is the process number found from the **ps -A** command.

Also, this OS has a neat thing called a man page.  You can, at the terminal, enter **man *command*** and the system will display a manual page for it.  Try it out on the ***kill*** and ***ps*** commands.

Barrie

---

### Post by housam on 2008-06-15
Here is the complete ubuntu [[COLOR="Red"]_documents index_[/COLOR]]("https://help.ubuntu.com/community/TitleIndex")

---

### Post by howlingmadhowie on 2008-06-15
if you add the system monitor applet to the taskbar, you can display a list of the running processes by clicking on it.

---

### Post by sam_delta on 2008-06-15
to kill a frozed program/window, press ALT-F2 and type ```
xkill
``` then run it by clicking run, your mouse pointer will become a "cross" you click on the window you want to kill (in this case, just click at firefox window), and it will get force killed

sam

---

### Post by master5o1 on 2008-06-15
The equivilant to the 'task manager' in Windows is probably Gnome System Monitor (command: gnome-system-monitor). It is in System>Administration>System Monitor.

I generally just use alt+F2 to open the run-command dialog and then type gnome-system-monitor. I also have Terminal keyboard shortcut turned on (System>Preferences>Keyboard Shortcuts) to alt+F3.

Ctrl+Alt+Backspace restarts X and returns to the GDM/Login Screen.

If you need to force-quit something then there is a force-quit applet for the gnome panels, and also the command to kill a process is `killall`
(alt+F2 then `killall firefox` will close firefox).

I do think it is possible to set Gnome System Monitor to a keyboard shortcut but I haven't done so because I remember the command. Meh.

---

### Post by niteshifter on 2008-06-15
Hi,

> Firstly, what is the Linux equivalent of ctrl+alt+del to bring up the task manager?

If you mean as a GUI, that would be System Monitor. Menu: System -> Administration -> System Monitor. With this tool, you have what Win's Task Manager presents - and then some. For example to kill off a misbehaving firefox you would start System Monitor, click the Processes tab and look for an entry named firefox (not firefox-bin), then right-click on it and select kill process.

You can also place System Monitor on a GNOME panel (like at the top of your screen): Right-click on the panel, click on Add to Panel, this brings up a dialog. Scroll down to System & Hardware, click on System Monitor, then click on add to panel, click close. You can control where SM's icon sits on the panel by right-click on it, then click Move - as you move your mouse left-right the icon will move. Click when it where you want it, it will then be anchored there.

> Secondly, sometimes, I end up on in a terminal - where I am logged into Ubuntu but there is no graphical desktop...just a cursor. How do I get back into the desktop?
This has me a bit curious: Normally one winds up in a console by pressing Ctrl+Alt+F1 (or F2, F3, F4, F5, F6). You get back to the GUI with Ctrl+Alt+F7. If you're being "dumped" to a console, something is amiss with your system ....

---

