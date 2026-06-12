---
title: "power-up &amp; run"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Clive McCarthy on 2008-06-15
I'm developing an OpenGL program in C that I want to run as soon as the computer is powered up. It's a semi-embedded application: no keyboard, no mouse, just a power button.

How do I get Ubuntu to immediately, on power-up, (with no log-on) run a script or an application?

Similarly, I need Ubuntu to close down nicely when the power button is pushed again, no asking if I want to hibernate or anything else...

How can I do this?
:popcorn:

---

### Post by sam_delta on 2008-06-15
add the path to your application to the file "/etc/rc.local"
example, if your file is in your desktop, open the file /etc/rc.local and type
"/home/username/Desktop/myprogram"

make sure  your program is executable

it will not run exactly when you turn on the pc (i duno if thats possible) but it will run at a lower runlevel, it will run before the xserver is started (before login, at boot time)

sam

---

### Post by sdennie on 2008-06-15
You can set a user to auto-login using System->Administration->Login Window and looking at the Security tab.  To autorun something in that users login, look at System->Preferences->Sessions.  To change the behavior of the power button, hit Alt-F2 and type gconf-editor.  Navigate to /apps/gnome-power-manager/buttons and click on power.  Look in the bottom right and it will tell you the available options for what happens when you push the power button (it sounds like in your case, you will just want to double click on power and change it to shutdown).

---

### Post by aktiwers on 2008-06-15
Okay I don't know how to do this, but maybe you could disable any GUI (gnome, kde, etc..) or uninstall them, so that you boot directly to terminal. Then make it autologin and then run your app from rc.local like Sam_delta said.

I think being in terminal mode, the powerbotten will just shut down the system with no userinput if I remember correct.

---

### Post by Clive McCarthy on 2008-06-18
Your advice here has been very helpful. My next system issue is to figure out how to invoke fullscreen mode from _within_ my program?

I found advice about manually doing what I want by using: 
system>preferences>keyboard short cuts>window management>toggle fullscreen mode
Which does what I need. :)

I need to unleash my OpenGL/glut program from the fenestration's mullions. A system call to the window manager is probably what I need...

---

### Post by sdennie on 2008-06-18
You should be able to do this with wmctrl:

```

sudo apt-get install wmctrl

```

Then, to set a window to fullscreen:

```

wmctrl -c "Exact Title of the Window" -b add,fullscreen

```

---

### Post by Clive McCarthy on 2008-06-18
My, oh, my. I do like having this level of control!

---

### Post by Clive McCarthy on 2008-06-19
An addedum for folks who might want to do the same thing:

In my C program I used the following:

[B][INDENT]glutFullScreen();
system("wmctrl -r\"name of window\" -b add,fullscreen,skip_taskbar");[/INDENT][/B]

which works like a charm. This is a pseudo GlutGameMode for Ubuntu & OpenGL/glut

:guitar:

---

