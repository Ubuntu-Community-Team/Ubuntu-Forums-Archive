---
title: "New to Ubuntu; Gnome Panel crashing"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Zenmij on 2008-11-27
Hi, I am pretty new to using ubuntu and I have a problem where I have gnome panel lock up so I have to use the power button on my laptop. 

I am still able to interact with the desktop but is there an error log I can post somewhere if it happens again? Or any other solution to restart should the panel lock up again and not be able to access the shut down icon?

Thanks v much

---

### Post by kd420 on 2008-11-27
You can try restarting X, using the shortcut "Ctrl+Alt+Backspace" but it is not guaranteed to work, and not always neccesary. Another way, probably better if it's just the panel acting up, is to switch to a virtual terminal and kill the panel.

Ctrl+Alt+F1 will bring you to the first virtual terminal (F1-F4 usually are available as terminals) and you should be prompted for a username & password. Enter the same username/password as the frozen session and issue the command:

killall gnome-panel

EDIT: You can also do this in a regular terminal, if you are able to access one.

This will kill the panel, and bring it back. You can also use this to kill other things (firefox etc.) but make sure you know what you are killing.

IMPORTANT: To get back to the desktop, hit Ctrl+Alt+F7

On a further note, do you know what's causing the freeze-ups (what were you doing right before it happened)? You shouldn't have to deal with it, it should be fixable.

---

### Post by listener on 2008-11-27
To add to the previous post, I had a similar problem on 8.04 once.  I thought about it (it kept happening every login) decided to start removing applets until I found the culprit.  The first one I tried fixed the problem, and I placed it back, without any negative consequences.  Just something about the installation of that applet on that panel configuration, went wrong.  That could be your problem.  Think about which applet you placed on the panel last.  

good luck

---

### Post by dangyogi on 2009-02-18
This is also happening to me.  It's getting quite bad.

gnome-panel goes into an infinite loop and gradually eats up memory.

Now I'm having to kill it about 20 times to get it to work after it locks up.  About half of the time, it doesn't even display the panel.

It seems that talking to somebody on skype really aggravates the problem.

I'm running ubuntu 8.10 on a laptop.

Let me know if I can get you any information on this or run any tests for you.  I'm a programmer, but not that knowledgeable of X or gnome (old school command line person ;).

---

