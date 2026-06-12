---
title: "Setting up Keyboard shortcuts"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by cheatos on 2012-02-26
Hi,

is there a way to enable keyboard shortcuts in lubuntu (e.g. changin desktops) like in lubuntu?

---

### Post by audiomick on 2012-02-26
I think you made a typo in that post; it doesn't really make sense. Try again, maybe?

---

### Post by cheatos on 2012-02-26
> is there a way to enable keyboard shortcuts in lubuntu (e.g. changin desktops) like in lubuntu? 	

The last one was meant to be ubuntu, sorry and I have seen that changing desktops ist possible, I needed to move a window to the next desktop.

---

### Post by Rodney9 on 2012-02-26
See here - [http://ubuntuforums.org/showthread.php?t=1422861&highlight=lubuntu+shortcuts](http://ubuntuforums.org/showthread.php?t=1422861&highlight=lubuntu+shortcuts)


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by cheatos on 2012-02-26
Thanks for that link, but what is the command for 'move window to desktop on the right/left' ?

---

### Post by cheatos on 2012-02-28
bump

---

### Post by Lalaith on 2012-02-28
I don't know if this is what you are looking for, but I change windows pressing Ctrl+Alt+arrow
(arrow <-- goes to window on the left, 4 ex)

---

### Post by cheatos on 2012-02-28
By standard, Ctrl+Alt+Arrow changes desktops, I want to move one window (i.e. firefox) to the desktop on the right.

---

### Post by Lalaith on 2012-02-29
Oh, right. Then try shift+crtl+alt+arrow.

Is that what you asked for? I found it on the settings --> keyboard --> shortcurts. There are some shortcuts on "Navigation" tab that are not set to any combination as default but you may want to give them a shortcut as well. (like "move window to workspace 1, ...)

hope it helps :)

---

### Post by cheatos on 2012-02-29
Yes, the Shift+Ctrl+Alt+Arrow is the command I'm looking for, but it only works in ubuntu. As I had to switch to lubuntu I'd like to know how I can make a new shortcut (the Ctr+Alt+Shift+Arrow) because by default this shortcut is not enabled in lubuntu.

Hope this is understandable...

---

### Post by Rodney9 on 2012-03-01
You can just roll your mouse wheel when the cursor is over the desktop icons on the panel.

---

### Post by cheatos on 2012-03-01
When I roll my mouse eover the desktop it changes desktops, when I roll my mouse over the application entry in the panel it minimizes the window or restores it. When I roll my mouse over the desktop pager it switches desktops again, so no way of moving the active window from one to another desktop. There has to be a command for it, doesn't someone know it?
Or can somebody look it up in ubuntu in the keyboard configs?

---

### Post by ahning on 2012-03-01
If you would like to have easy to configure and use keyboard shortcuts (keybindings) you can use the openbox window manager or fluxbox which already has many keybindings set up. I use openbox which requires more time to get it working than fluxbox.

I also have mousebindings as well so I can get different menus with the left and right mouse click on screen.

---

### Post by cheatos on 2012-03-01
So, where can I get to the openbox window Manager? I only have an entry for Openbox Configuration Manager and I couldn't find an entry for keyboard or mouse shortcuts (it has a mouse-entry but not for shortcut edititing...)

---

### Post by ahning on 2012-03-01
You can get opnbox by typing after the prompt:
sudo apt-get install openbox

and the same for fluxbox which already has many keyboard short cuts with the first installation:

sudo apt-get install fluxbox

or do both together:

apt-get install fluxbox openbox

When they install you will have a blank screen with drop down menus from the right click of the mouse. You can change the mouse binding or key binding to what ever you want.

---

### Post by cheatos on 2012-03-02
So I found it ut where to change it even without installing anything, itsin the /$HOME/.config/openbox/lxde-rc.xml

There its pretty far to the bottom and by default the movement of windows to another desktop is set with Shift+Alt+Arrow

I'l mark this as solved now, thanks for all your help!

---

