---
title: "Is there a ctrl-alt-del equivalent?"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by Muk on 2012-12-25
so in version 12.10 how do i add the force quit command to my taks bar?

thx for the awesome guide :D

---

### Post by oldos2er on 2012-12-25
Post moved to its own thread.

---

### Post by GameX2 on 2012-12-25
Hi,

You can download the Force Quit application here:
[http://www.omgubuntu.co.uk/2011/10/force-quit-applet-unity-launcher](http://www.omgubuntu.co.uk/2011/10/force-quit-applet-unity-launcher)

There are different way to kill an application in Ubuntu; you can of course open the System Monitor, being gnome-system-monitor in the Terminal, and terminate the process here - its the Task Manager equivalent, on Ubuntu.

You could also open a virtual terminal, if the system stop responding, and you cant open the system monitor or use Force Quit.
To do that, press CTRL-ALT-F1 (Up to CTRL-ALT-F6), which will open a console - to exit the console and return to the graphical user interface, press CTRL-ALT-F7.

You will want to use the skill applicationname to kill an application.  You can also use skill yourname to logoff.  Or you could use :

```
top
```This command display the most demanding processes.  Pressing M will sort the processes and show those who use the most RAM.  You will then want to press K to kill a process.  Next to 'PID to kill' , type the PID listed in the console for the process you want to end.

Or in case your system is not responding at all, try to use the command ALT-PrintScreen-K, which will kill your account (logoff the hard way), and bring you back to the login screen.

---

### Post by MishaX2 on 2012-12-25
A nice utility you could check out is xkill.
Just press alt+f2 and type xkill

Now whatever window you will click, its process will be terminated. But the windows "Task Manager" equivalent is called the System Monitor. Just type type it in the menu.

---

### Post by GameX2 on 2012-12-25
> **MishaX2 said:**
> A nice utility you could check out is xkill.
Just press alt+f2 and type xkill

Now whatever window you will click, its process will be terminated. But the windows "Task Manager" equivalent is called the System Monitor. Just type type it in the menu.

Interesting!

I just can't figure out how to exit xkill when it's started.

---

### Post by MishaX2 on 2012-12-25
> **GameX2 said:**
> Interesting!

I just can't figure out how to exit xkill when it's started.

Right click to exit xkill.

---

### Post by The Cog on 2012-12-25
> **GameX2 said:**
> Or in case your system is not responding at all, try to use the command ALT-PrintScreen-K, which will kill your account (logoff the hard way), and bring you back to the login screen.
That's broken in 12.10. You can add this to /etc/rc.local to fix it again (before the exit line):
```
# Fix broken sysrq
echo 1 > /proc/sys/kernel/sysrq

```

---

### Post by stinkeye on 2012-12-25
Here's how you can add xkill to the launcher in Unity.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=12263542&postcount=4[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12263542&postcount=4")

---

### Post by drpjkurian on 2012-12-25
Hi in Kubuntu, you can access 'System Activity' by ```
Ctrl+ Esc
``` you can select the non responding programme and kill it by hitting 'End process'
See the image

---

