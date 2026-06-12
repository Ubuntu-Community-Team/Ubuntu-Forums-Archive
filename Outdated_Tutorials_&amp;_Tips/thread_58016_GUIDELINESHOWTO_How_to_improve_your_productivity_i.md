---
title: "GUIDELINES/HOWTO: How to improve your productivity in Linux"
date: 2005-08-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Nightblade on 2005-08-18
Hello! This is my first how-to ever, and it's VERY simple. I also realize that 90% will already know this. But it's for the complete newbies, the ones who have switched from Windows.

What I've come to discover is that I personally love simplicity, speed and convenience in my computer. But I also love eye-candy and "bling". So, until now I've always thought "the bigger the better, I have a quick computer, I can afford a HEAVY windowmanager like KDE or GNOME, and it's pretty easy to spiff up to a nice WM (window manager) too.". It was a "sunny" day, I was browsing throught this section of the forum (I LOVE fixing, tweaking and getting new cool stuff working on Linux) to find something new. I came across the "Enlightenment + Gnome" thread. Cool! Tried it out and at last I ended up skipping Gnome totally and going simply for Enlightenment. Enlightenment is really nice, very customizable, easy, fast, and did I mention really fast? It's basicly everything I ever wanted.

LoL that was pretty much my Linux story, dunno why I wrote it. Now to the main-purpose of this thread. To improve your productivity in Linux you have to access stuff quicker. One thing I was tired of when running Windows was browsing that big old start-menu that ALWAYS was big as a tree. So, when I learned to love Gnome I started using alt+F2 (run command). It's really smooth! And quick!

Learn to use the Run Command, it will speed you up.

What many people don't realize is that bash-scripting is one of the MAIN advantages in Linux versus Windows. You can customize to the extent of your frickin mind ;) For example, you run games in cedega? I always entered a terminal, browsed my way to the game folder and ran cedega exe.exe. Now I use:

Run Command: gamename

by a simple script located in /usr/local/bin/gamename

```
#!/bin/sh
# any application specific commands, like the mouse-fix for World of Warcraft, or maybe a xinit for a new x-server.
cedega /path/to/game/exe.exe
```

Simple, quick and productive!

---

### Post by AgenT on 2005-08-18
You can also use "Keyboard Shortcuts" program (under System -> Preferences) to not only find out new shortcuts that you probably were not aware, but also bind new ones (a lot are unused by default).

As far as the run command goes, you can also add the run dialog (or a single line terminal/console, among other things) to your panel for quick access:
Right click on your panel -> Add to Panel.

---

### Post by Lux Perpetua on 2005-08-18
Good idea for a how-to! 

Personally, I find that using the keyboard as much as possible (vs. mouse/touchpad/etc.) increases productivity. Pressing an arbitrary key or combination of 2 keys on the keyboard is faster and easier than maneuvering the mouse pointer to a specific location. I wish there were a "friendlier" keyboard-centric window manager. I've tried wmii and ion...the tiling concept is the right idea, but these WM's are a pain to learn and use.

---

### Post by Nightblade on 2005-08-19
[QUOTE=Lux Perpetua]Good idea for a how-to! 

Personally, I find that using the keyboard as much as possible (vs. mouse/touchpad/etc.) increases productivity. Pressing an arbitrary key or combination of 2 keys on the keyboard is faster and easier than maneuvering the mouse pointer to a specific location. I wish there were a "friendlier" keyboard-centric window manager. I've tried wmii and ion...the tiling concept is the right idea, but these WM's are a pain to learn and use.[/QUOTE]
 If you don't mind configing in the terminal, Enlightenment has some nice features for you. I *THINK* you can customize any shortcut to any key, not sure though. Try it out!

---

### Post by Stormy Eyes on 2005-08-19
[QUOTE=Nightblade]If you don't mind configing in the terminal, Enlightenment has some nice features for you. I *THINK* you can customize any shortcut to any key, not sure though. Try it out![/QUOTE]

You can do the same with Openbox by banging on its XML-format config file.

---

