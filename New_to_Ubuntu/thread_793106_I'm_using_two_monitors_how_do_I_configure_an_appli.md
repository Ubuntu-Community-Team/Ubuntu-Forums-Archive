---
title: "I'm using two monitors how do I configure an application to launch on my 2nd monitor?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by energy. on 2008-05-13
I'm using twinview and my card is nvidia, if that helps.  right now all of my applications load on the primary display.  I'd like firefox to load on the secondary display when I click its shortcut.

---

### Post by rockerphil on 2008-05-13
i'm not too sure how your WM works, but i know with my WM (Fluxbox) i can right click on the top bar of a window and have it "remember" the dimensions and position of a particular application window, so what *I* would do is position your FireFox window on your 2nd monitor then set it to remember the position, thus launching on the secondary monitor every time afterwards

---

### Post by Nythain on 2008-05-13
from what i've researched, this really varies from window manager to window manager and app to app...
unfortunately, i've found gnome/metacity particularly lacking in this and many other dual monitor departments...

sometimes an app will have a command line option to set teh screen, sometimes teh window manager will, and some window managers are pretty good at remember those things, like fluxbox... kde's kstart could probably do it via command line launch but i dont know if/what metacity can do

---

### Post by PinkFloyd102489 on 2008-05-13
I dont know if this will work or not, it should work, based on what Ive seen. When executing some programs from the command line, you have to specify the display, like :0.

So browse to /usr/share/applications and find the .desktop file of the application you're wanting. Open the file as root (or sudo) and find the line that begins with Exec. For example, the line in the Firefox file should say "firefox %u" or something similar.

Now here's the part that "should" work. Put DISPLAY=:X in front of the application name, X being the number of the display. The main monitor is 0 and the second monitor is usually 1. So for example, Firefox's Exec line should look like this:

```
Exec=DISPLAY=:0 firefox %u
```

Then just do this for other applications you want and change the display number for which monitor you want. Like I said, I dont know for sure that this should work, but theoretically it should. Let me know if it does. :)

---

### Post by lazyart on 2008-05-13
Devil's Pie @ [http://burtonini.com/blog/computers/devilspie](http://burtonini.com/blog/computers/devilspie) could help here.

---

### Post by energy. on 2008-05-13
> **PinkFloyd102489 said:**
> I dont know if this will work or not, it should work, based on what Ive seen. When executing some programs from the command line, you have to specify the display, like :0.

So browse to /usr/share/applications and find the .desktop file of the application you're wanting. Open the file as root (or sudo) and find the line that begins with Exec. For example, the line in the Firefox file should say "firefox %u" or something similar.

Now here's the part that "should" work. Put DISPLAY=:X in front of the application name, X being the number of the display. The main monitor is 0 and the second monitor is usually 1. So for example, Firefox's Exec line should look like this:

```
Exec=DISPLAY=:0 firefox %u
```

Then just do this for other applications you want and change the display number for which monitor you want. Like I said, I dont know for sure that this should work, but theoretically it should. Let me know if it does. :)

I changed that line to 

```
Exec=DISPLAY=:1 firefox %u
```

and when I try to open firefox by using the link that is under the applications tab on the gnome panel I get this error 

```
Failed to execute child process "DISPLAY=:1" (No such file or directory)
```

:confused:

---

### Post by PinkFloyd102489 on 2008-05-13
Try "export DISPLAY:X && firefox %u".

---

