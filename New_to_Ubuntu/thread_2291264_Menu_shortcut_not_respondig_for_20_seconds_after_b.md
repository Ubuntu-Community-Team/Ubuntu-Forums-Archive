---
title: "Menu shortcut not respondig for 20 seconds after boot"
date: 2015-08-18
forum: New to Ubuntu
---

### Post by geranimo on 2015-08-18
Hello, I configured the menu with a keyboard shortcut, but it takes 20 seconds after boot until I can use the shortcut. I have to click on the menu if I want to use it. I don't know why it is happening since I just reinstalled xubuntu because my linux broke for an unknown reason.

Do somebody have an idea?

(no shortcut works finally, but all of them start working 20 seconds after boot)

---

### Post by eyal-ez on 2015-10-07
Getting the exact same behavior on: 3.13.0-65-generic #106-Ubuntu SMP Fri Oct 2 22:08:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linuxrunning xubuntu desktop

---

### Post by Toz on 2015-10-07
For the keyboard shortcuts to work in Xfce, the xfsettingsd daemon needs to start up. It is possible that it is taking it that long to start up. Are you using an older system that takes a while to start? Do you have a lot of autostart applications?

One thing (aside from limiting the number of startup applications) that you can do to speed up Xfce start time is to clear out the sessions cache. To do so:
[LIST=1]
[*]Log out of your graphical session
[*]Press Ctrl+Alt+F1 to go to a text console
[*]Log in to the text console
[*]Issue the following commands:
```
cd .cache
rm -rf sessions
```
[*]Press Ctrl+Alt+F7 to return the graphical console
[*]Log in and see if its any better
[/LIST]

Note: When you clear your sessions cache, you remove any applications that you may have set to autostart via the "Save session for future logins" option available when logging out or via the Settings Manager > Session and Startup > General tab > Automatically save session on logout.

---

