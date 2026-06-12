---
title: "[SOLVED] Task bars gone!?"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Skyker on 2008-10-08
Basically Firefox froze (where you click on it and it shows the top bar, but there is nothing below it), this happened before so I just went to restart the computer since I don't know how to find a ctrl+alt+delete menu like they have in Windows.  I clicked 'quit' on the upper task bar, and nothing happened.  (normally a box full of shut down options comes up)

So I hit the power button on the actual computer, and the box came up and I selected restart.  Well after the restart neither of my task bars (top or bottom) show up.  I even went into settings manager and clicked 'panel' but nothing happened when I clicked it.

Please help me.  Even tho the 'fold up' option is really useful, I'd really like to minimize stuff and reopen it again.  (when I minimize, it disappears completely)

Help!:confused:

---

### Post by airtonix on 2008-10-08
Here is one method that may get you back on your feet: 

the 'alt+ctrl+delete' your referring to is called the taskmanager in windows.
in linux there are many ways to manipulate the running processes, having a gui is one of them...it is found in system -> administration -> system monitor.

to use the console/terminal method : ```
sudo killall app-name
```

to find out what is running : ```
sudo top
```

to access a terminal quickly(this is considered a seperate login session), press ctrl+alt+f1 & log in with your username and password.

once there, type : ```
sudo killall gnome-panel
```

---

### Post by posburn on 2008-10-08
Firefox occasionally does the same thing to me.  When I shade the window or maximize it, it goes into fullscreen mode and the panels (or cairo-dock in my case) disappear.  Usually pressing F11 gets FF out of fullscreen and back to normal.

For your missing panels try this in a terminal:

```
killall xfce4-panel
```

This will kill any screwed-up instances of xfce4-panel after which the process will try to restart itself (hopefully successfully).

If the terminal reports back "no process killed", then just enter

```
xfce4-panel
```

and see if it'll start.

If that works (it does in gnome, but not sure about xfce since I don't use it), but your panels are still gone after a reboot, then you need to add xfce-panel back to your list of services/processes to start upon boot. (though I'm not sure how it would get removed in the first place) 

Hope that helps!

---

### Post by tarps87 on 2008-10-08
To get the panels back try```
xfce4-panel
```
Usually you can't kill the panels, in gnome I had to rename the gnome-panel to stop it running (as I'm using awn)

Edit: sorry wrong environment, this is the on for Xubuntu

---

### Post by chaosdesigner on 2008-10-08
For the FF problem:

Have yout tried just using Alt+F4 to just close the programm?

---

### Post by Skyker on 2008-10-08
```
kimberley@kimber:~$ killall xfce4-panel
xfce4-panel: no process killed
kimberley@kimber:~$ xfce-panel
bash: xfce-panel: command not found
kimberley@kimber:~$ 

```

??

  :)  And no, I don't use alt+F4 ever, so it didn't occur to try it haha.

---

### Post by posburn on 2008-10-08
my bad - i just edited my post above.  It should read:

```
xfce4-panel
```

I forgot the "4" after xfce. (DOH!)  Try that.

---

### Post by Skyker on 2008-10-08
yaaay!  Thanks, now how do Iget them to stay there?  (as in, add them to start up opplications?)

---

### Post by posburn on 2008-10-08
To add xfce4-panel to start-up apps: (again, I *think* - I usu. use gnome) go to:
Applications->Settings->Autostarted Applications->Add
Name: Panel / Command: xfce4-panel

---

### Post by tarps87 on 2008-10-08
If you want to just restart the x-server environment (the GUI) you can use Ctrl+Alt+bckspace
This will take you to the login screen and force any running apps to close

---

### Post by Skyker on 2008-10-08
Umm... when I closed Terminal, the task bars went away again o.O

But I managed to add the panels to the start-up applications.

---

### Post by posburn on 2008-10-08
That's normal - any app started through the terminal will be killed when that terminal session is closed, though I'm surprised xfce4-panel didn't restart itself (gnome-panel does).

Try to restart the X server (CTRL-ALT-backspace) and login again to see if your panels are there.

---

### Post by fooman on 2008-10-08
if you put a "&" after the "xfce4-panel"....it will stick even after you close the terminal.  should look like this:

```
xfce4-panel &
```

---

### Post by posburn on 2008-10-08
Hey thanks fooman - I didn't know about using the "&".  Ya learn something new every day!

---

### Post by Skyker on 2008-10-08
Thanks guys, a restart did it, I just had to hurry off to school and couldn't check this morning.  But they're back now, so all's good :D

---

### Post by zaivala on 2010-09-06
Xubuntu 10.04 on an old Sony Vaio laptop (2001):

My taskbar is there, but it only shows Firefox, Help, and the loaded stuff (right end).  I can't get to my Applications, System, etc.

I used Ctrl-Alt-F1, did the xfce4 command referenced here, and was told that it couldn't load it.

Now what?

---

