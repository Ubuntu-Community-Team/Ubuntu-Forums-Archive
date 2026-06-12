---
title: "[SOLVED] How do you start a Guest session in Xubuntu 8.10?"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by jis on 2008-11-02
In Ubuntu Gnome it can be done in the exit menu in upper-right corner...

---

### Post by overdrank on 2008-11-02
> **jis said:**
> In Ubuntu Gnome it can be done in the exit menu in upper-right corner...

Hi and it has been awhile since I have use xfce but I believe you should have a similar option when logging off.

---

### Post by jis on 2008-11-02
Well it doesn't (or I have been blind again).

---

### Post by schweerelos on 2008-11-16
I don't know if the original poster still cares -- but I'll post the answer just in case someone else has the same question and comes across this thread.

You'll have to install the package **gdm-guest-session**.
[LIST]
[*]In a terminal: ```
sudo aptitude update && sudo aptitude install gdm-guest-session
```
[*]Or use the package manager to find and install the package.
[/LIST]

You can then run ```
/usr/share/gdm/guest-session/guest-session-launch
``` in a terminal to start a guest session.

If you want to start guest sessions from a button in the panel, you can add a "Launcher" applet to the panel and set its "Command" to ```
/usr/share/gdm/guest-session/guest-session-launch
```

Alternatively to all this, you can just install the package **fast-user-switch-applet** and add it to the panel (you probably have to add an "XfApplet" to the panel and then add the fast user switch one to that). The drawback is that this way, a lot of gnome packages will also be installed on your system.

---

### Post by jis on 2008-11-18
Thanks. Can you start a guest session from GDM?

---

### Post by jis on 2008-11-29
schweerelos, the method you gave did not work: I got screen locked (by gnome-screensaver) and only thing I could do was to give my password to continue.

---

### Post by schweerelos on 2008-11-29
jis, sorry to hear this didn't work for you.

Let me try to understand what is going wrong for you.

So you installed the gdm-guest-session package, right? And then what? Did you run /usr/share/gdm/guest-session/guest-session-launch? Or did you add the launcher to the panel and try that? Or did you go the alternative route and installed fast-user-switch-applet?

Try running /usr/share/gdm/guest-session/guest-session-launch from a terminal to see if there are any error messages shown in the terminal window after you've unlocked the screen saver.

And I don't think this works directly from gdm -- it doesn't seem to fit the idea behind the guest sessions, from what I can see from [this discussion]("http://ubuntuforums.org/showthread.php?p=5904109").

---

### Post by jis on 2008-11-30
I tried running /usr/share/gdm/guest-session/guest-session-launch in another Xubuntu 8.10 computer and it worked fine. I'll try with the problem computer again later.

---

### Post by jis on 2008-12-01
I tried the script again and it works fine now.

---

### Post by m_l17 on 2008-12-07
Works for me too and Thanks schweerelos :D Please jis mark this as Solved.

---

### Post by jis on 2009-01-07
It does not work for me anymore; see [another thread]("http://ubuntuforums.org/showthread.php?p=6513343").

---

