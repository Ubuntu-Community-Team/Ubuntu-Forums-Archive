---
title: "I have too many x-manager/de"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by il_maniscalco on 2012-01-26
Ok, I installed ubuntu and I like it.
But I didn't like unity, so I installed gnome, or xubuntu I can't remember, or both.
after that I found at login, the gnome session, a gnome 2d session, a xfce session, two xubuntu sessions, and now I wanted to try (with no success as I couldn't right click to the menu) fluxbox, so I have all those plus unity and unity 2d.

I think it's too much, and want to put some ordering in my graphic environments.

At the moment, I'd like to try fluxbox, and perhaps enlightment (i don't know if it's still maintained) or, I'd like something better than xfce that seems too "cold" for me, I don't like it too much.

please can you advise me on:

1) how to uninstall what in excess
2) what to keep
3) if I can cleaning my system in order to make at least one desktop environment / window manager to work fully and properly (I don't know but I feel something is wrong at the moment and my failure using fluxbox shows it)
4) what environment/manager (what's the difference by the way) could I try? I'm looking for a fast one, but with elegant themes and nice fonts and colors. I'm aware every de/wm have themes, but where to find them and how to install them.

ps: fluxbox didn't find my chromium in the menu (until the menu appeared), why?

---

### Post by mcduck on 2012-01-27
1. I'd use Synaptic PAckage Manager, but feel free to use Software Cetner or apt-get if you want. Just uninstall all the packages you *know* to be related to a certain desktop environment, and afterwards run "sudo apt-get autoremove" and any remaining packages should be automatically removed.

2. Of course keep the one(s) you actually like. ;)

3. I can't see any way how having multiple desktop environments/window managers installed could cause any problems, so there's probably some other reason if things aren't working for you...

4. Window Manager is basically just the program that draws program window son the display and allows you to move them around, minimize them and so on. Although many window managers contain at least some basic functionality that allows you to start programs etc.

A Desktop Environment contains a lot more, they come with all kinds of background services, automatic tools that handle all kinds of things for you (mounting removable drives, drag&dropping things between programs, sound, network connections and so on), and a collection of applications specifically designed to work together and with the desktop environment. 

For example Gnome comes with it's own user interface toolkit (GTK), web browser, office applications, calculator, terminal emulator, all the configuration tools, and so on. While Openbox only gives you black screen with a right-click menu to start your programs and the ability to run graphical applciations inside windows, without any configuration tools or anything included unless you install them yourself...

It's quite ahrd to recommend anyhting based on looks, wat looks good depends on who's looking... ;) And stuff like fonts and how the applications themselves look like depends on the toolkit used by the application (GTK or QT, usually), not on the DE/WM you are using.

However if you want to try something fast, then Openbox is of course always worth a try.

What comes to getting themes, try gnome-look.org (for Gnome), kde-look.org (for KDE), xfce-look.org (for XFCE4) or box-look.org (for fluxbox, openbox and all the other more minimalistic window managers).

For applications it depends on the toolkit the app in question uses, but you'll find GTK themes from gnome-look.org and xfce-look.org, and QT thems from kde-look.org.

...and there are some themes available in Ubuntu's repositories as well...

---

### Post by il_maniscalco on 2012-01-29
Thank you I really appreciated it.

---

