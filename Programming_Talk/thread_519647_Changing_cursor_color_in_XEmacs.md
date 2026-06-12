---
title: "Changing cursor color in XEmacs"
date: 2007-08-07
forum: Programming Talk
---

### Post by swarog on 2007-08-07
Seems like it is not possible through GUI menu, so I guess there must be some kind of variable, but I don't know which one and where it has to be written. I want to change it to black instead of red.

---

### Post by Rocket2DMn on 2007-08-07
w00t for emacs!
The config file for emacs is in your home directory:
```
emacs ~/.emacs
```
and the line to add should be:
```
set-cursor-color "black"
```
Then close out emacs and open it again.
Give it a try and let me know, I'm not in front of my linux laptop to test it out.

---

### Post by swarog on 2007-08-07
Ok. I tried to put that line (I guess it must be written with braces?) in my config file and then when I start xemacs it says this:
> (1) (initialization/error) An error has occurred while loading /home/alex/.emacs:

Symbol's function definition is void: set-cursor-colo

To ensure normal operation, you should investigate the cause of the error
in your initialization file and remove it.  Use the `-debug-init' option
to XEmacs to view a complete error backtrace..
I tried also to put set-cursor-color on M-x while running xemacs but it didn't help too. It turned out I can't execute set-background-color in xemacs as well.
On the other hand set-background-color works in regular emacs and set-cursor-color just doesn't make any effect and runs silently without any errors there.

---

### Post by Rocket2DMn on 2007-08-07
Your quote says "Symbol's function definition is void: set-cursor-colo", did you type it in wrong?  Also, is there a .xemacs file that Xemacs reads rather than .emacs?

It looks like there is a command line option to change the color of the cursor, but this doesn't help if you run Xemacs from the GUI unless you modify the command that the icon gives (right click and hit Properties):
```
xemacs -cr color
```

I looked up some of the man pages and google searched - there are descriptions on how to set the cursor color to be whatever color you want by default.  It is difficult to repeat them here as the explanations can be a little long and cryptic, but I'll try.

One way requires adding this to a specific file:
```
*cursorColor:    black
```
The resource listed the file as .../app-defaults/Emacs but that doesn't mean too much (you can search for the file)

or you can add ```
emacs*cursorColor:	black
``` to your .Xdefaults file.
If you take this approach (which I suggest), you will have to run 
```
source .Xdefaults
``` or may have to restart the X-server.  You can restart the X-server by saving any open files and hitting CTRL+ALT+BACKSPACE

---

### Post by swarog on 2007-08-08
Thank you for your reply. I tried methods you proposed, but unfortunately they don't work for my system. But I have managed to change the color by running customize-face RET text-cursor command with its appropriate option setting. Still this doesn't affect GNU emacs behavior but I don't use it, besides its default coloring scheme suits me very well.

---

