---
title: "How to  Run a Command from Command prompt"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by rashidaa on 2013-01-18
I see a 'Run' menu at the start menu at lubuntu desk top. Which can be activated by pressing Alt+F2.
I want to do follwoing:
[LIST=1]
[*]Go To command prompt by Ctr+Alt+F2
[*]Activate 'run' from command prompt
[*]Type xrandr -s 1 at the run command text box 

[/LIST]
All these three step I want to do from Command prompt and not from Terminal.
How is it possible?
my objective is to set screen resolution from command prompt.

---

### Post by pissedoffdude on 2013-01-19
Hi,

It looks like you're confusing the command prompt with the terminal.  In linux, the command line interface is known as the terminal.

Now, based on your previous posts, I'm assuming you want to get to the terminal to run chmod +x .xprofile so as to make it executable

Assuming you want to create the .xprofile script, open the terminal, then type the following:

```
cd ~
rm .xprofile
touch .xprofile
echo xrandr -s 1 > .xprofile
chmod +x .xprofile
```

Reboot or logout and let us know if that worked

---

### Post by rashidaa on 2013-01-19
On rebooting I lose the file.
At present, I am trying lubuntu and boot it from USB, where I can save the file only for the session. On reboot I lose the file. I am unable to save file.
I am not confusing the terminal window and command prompt.
I go to the terminal window by ctrl+Alt+T
where as I go to the Command prompt by 
Ctrl+Alt+F2
At terminal window which I arrive at through Ctrl+Alt+T, I am able to change screen resolution by command 
xrandr -s 1
but at Command prompt which arrive at through Ctrl+Alt+F2, I can not change the screen resolution by typing this command
Why??

---

### Post by GordThompson on 2013-01-19
> **rashidaa said:**
> I go to the terminal window by ctrl+Alt+T
where as I go to the Command prompt by 
Ctrl+Alt+F2
At terminal window which I arrive at through Ctrl+Alt+T, I am able to change screen resolution by command 
xrandr -s 1
but at Command prompt which arrive at through Ctrl+Alt+F2, I can not change the screen resolution by typing this command
Why??
My guess: 

- When you hit [Ctrl-Alt-T] you are launching a new process (a "Terminal" window) within the current X session, which by default runs on virtual terminal #7 (tty7). 

- When you hit [Ctrl-Alt-F2] you are switching to virtual terminal #2 (tty2) and there is no X session running there so `xrandr` doesn't work. 

The following might help explain:

[http://www.tuxfiles.org/linuxhelp/multiple-x.html](http://www.tuxfiles.org/linuxhelp/multiple-x.html)

---

### Post by rashidaa on 2013-01-19
Thank you . This is a great information, I was quite unaware of it. 
Please tell, if there is any method from which we can send command from tty2 to tty7. That is can we manipulate tty7 from tty2.
I think that it should be possible, but what is the method?

---

### Post by Cheesemill on 2013-01-19
You can prepend a command with the DISPLAY environment variable to indicate which display you want it to use. For example...
```
DISPLAY=:0.0 gedit
```Would open gedit on screen 0 on the first X display (usually TTY7).

[http://www.x.org/archive/X11R6.8.1/doc/X.7.html#sect4](http://www.x.org/archive/X11R6.8.1/doc/X.7.html#sect4)

---

### Post by steeldriver on 2013-01-19
or for xrandr specifically you can specify the display via the -d parameter
```
xrandr -d :0 -q
``` is equivalent to
```
DISPLAY=:0 xrandr -q
```

---

