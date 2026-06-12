---
title: "Keyboard shortcuts in 8.10"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by kernelhaxor on 2008-11-06
I can go to K-Menu->System Settings->Keyboard->Keyboard Shortcuts ..
In there, there are only preconfigured actions and I can edit the buttons for each action but I cannot add my own keyboard shortcut ..
For example, if I wanted to open a console on some key combination, how do I add shortcuts like that?

---

### Post by Denestria on 2008-11-06
Right click on the menu button, select menu editor, pick the program you want then chose the advanced tab, at the bottom is the shortcut option.  *Or try system settings, advanced tab, input actions.
Personally I use the command line a lot so what I do for Konsole is add it to autostart with the --background-mode option then anytime I want a terminal all I have to do is F12 to bring it up or dismiss it.

---

### Post by kernelhaxor on 2008-11-07
> **Denestria said:**
> Right click on the menu button, select menu editor, pick the program you want then chose the advanced tab, at the bottom is the shortcut option.  *Or try system settings, advanced tab, input actions.
Personally I use the command line a lot so what I do for Konsole is add it to autostart with the --background-mode option then anytime I want a terminal all I have to do is F12 to bring it up or dismiss it.

Thanks!  I found it and configured a shortcut but it isn't working?!  Do I have to do a restart?

---

### Post by Denestria on 2008-11-07
Looks like another bug in basic functionality in KDE4.
[http://bugs.kde.org/show_bug.cgi?id=160892](http://bugs.kde.org/show_bug.cgi?id=160892)

I have the unpleasant feeling that I've been tricked into doing alpha testing.

---

