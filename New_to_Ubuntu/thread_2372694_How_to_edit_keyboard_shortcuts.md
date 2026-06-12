---
title: "How to edit keyboard shortcuts"
date: 2017-09-28
forum: New to Ubuntu
---

### Post by johnnoberries on 2017-09-28
Hi, I'm trying to move from Windows to Ubuntu, but I'm having a lot of problems with how to configure keyboard shortcuts. For example, the default text editor gedit, doesn't seem to have any options for changing its keyboard shortcut settings. Are these specific to gedit, or inherited from somewhere else, eg unity? I've found these pages
[URL="https://superuser.com/questions/174267/can-you-do-keyboard-shortcuts-in-gedit"]https://superuser.com/questions/174267/can-you-do-keyboard-shortcuts-in-gedit
[/URL][https://askubuntu.com/questions/638018/custom-keyboard-shortcuts-in-gedit-3-10-on-ubuntu-14-04](https://askubuntu.com/questions/638018/custom-keyboard-shortcuts-in-gedit-3-10-on-ubuntu-14-04)
[https://askubuntu.com/questions/452386/how-to-change-keyboard-shortcuts](https://askubuntu.com/questions/452386/how-to-change-keyboard-shortcuts)
[https://askubuntu.com/questions/223986/custom-keyboard-shortcuts-in-gedit](https://askubuntu.com/questions/223986/custom-keyboard-shortcuts-in-gedit)

but none of the suggested approaches work. Is there any documentation about how keyboard shortcuts, or gedit, works? I'm on ubuntu 16.04 LTS

---

### Post by TheFu on 2017-09-28
For how GUI things work on Unix-like systems, you have to understand the overall architecture of X/Windows. It is build on layers of layers of layers. 

It is too complex to explain here, but in general, the current "widget" has the first opportunity to handle any event.  If it doesn't handle it, then the parent "widget" gets the event and has an opportunity to handle it.  That happens up the widget chains --> application --> Window Manager --> X11 --> login --> console line until someone along the way knows how to handle the input.  At any level, the type of input can be completely captured or not.  Depends on how the programmer(s) wrote it.

Different window managers have different ways to handle these things.  The same for different Desktop Environments - so posting both of those items with the question is helpful. 

I don't use gedit or Unity, so it might choose to block all higher inputs or it might pass them through.  IDK.

As with almost all programs on a Linux system, if you don't find the information you want in the manpage (man gedit), or the project documentation [https://wiki.gnome.org/Apps/Gedit](https://wiki.gnome.org/Apps/Gedit) , then their is always to source code.  

You can also send commands into a specific window using external tools like **xdotool**.  I use this to have program launchers from my window manager, openbox.  It replaces having any needs for menus.  Unity is probably different.  I find Unity weird, but luckily in a few weeks it won't be the default on Ubuntu anymore.  Gnome will be.

[https://help.ubuntu.com/community/KeyboardShortcuts](https://help.ubuntu.com/community/KeyboardShortcuts) - points to xbindkeys, xbindkeys-config, and some other tools.

I realize this isn't directly helpful, but hopefully it will help you to find a solution.  The wikipedia article on X/Windows will explain it better, probably.

From - John Bigboote

---

### Post by Bucky Ball on 2017-09-28
* Update: Before reading the rest of this post, maybe I'm wrong and maybe it's easy. I'm not using Ubuntu, so please [ _try this_]("https://help.ubuntu.com/stable/ubuntu-help/keyboard-shortcuts-set.html") and let us know. 

In older releases, it appears to have been System -> Preferences -> Keyboard Shortcuts. You could also have a look there, if it still exists. I have been [hunting here]("https://duckduckgo.com/?q=ubuntu+create+keyboard+shortcut"). ;)
___

Welcome. Creating keyboard shortcuts in Ubuntu appears to be unnecessarily convoluted and complicated from what I've seen online. One of the reasons I've used Xubuntu for years is the fact that it is very easy to customise; adding keyboard shortcuts takes seconds. To create one, 'Keyboard> Application Shortcuts> Add'. You type the name of the app you want to launch and the key combo to launch it. Done.

I spent five minutes looking for info on how to create a custom keyboard shortcut on Ubuntu to open a specific app to see if I could help you, but no luck. You can use default keyboard shortcuts, create launchers easy enough, but ... Hope someone else knows the quick way to create custom keyboard shortcuts and good luck! Curious to know if an easy way exists. :)

---

### Post by vasa1 on 2017-09-28
> **johnnoberries said:**
> Hi, I'm trying to move from Windows to Ubuntu, but I'm having a lot of problems with how to configure keyboard shortcuts. For example, the default text editor gedit, doesn't seem to have any options for changing its keyboard shortcut settings. ...
Can you provide specific instances of what you want to change to what?

---

