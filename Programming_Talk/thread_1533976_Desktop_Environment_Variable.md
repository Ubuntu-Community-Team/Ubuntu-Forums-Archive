---
title: "Desktop Environment Variable?"
date: 2010-07-18
forum: Programming Talk
---

### Post by lkjoel on 2010-07-18
Are there any Desktop Environment Variables?
So I could type something like:
```
echo $DE
*GNOME*
```
Or are there any commands?
Thanks in advance!

---

### Post by trent.josephsen on 2010-07-18
Well, what if you're running GNOME's settings daemon, KDE's panel, XFCE's desktop manager, and Openbox as a window manager?

```
echo $DE
FrankenDesktop
```

---

### Post by lkjoel on 2010-07-18
> **trent.josephsen said:**
> Well, what if you're running GNOME's settings daemon, KDE's panel, XFCE's desktop manager, and Openbox as a window manager?

```
echo $DE
FrankenDesktop
```
I meant what it was logged into.
And I know that the $DE variable is probably not existing.

---

### Post by Dayofswords on 2010-07-18
```
echo $DESKTOP_SESSION
gnome

```

this maybe?

doesnt work with in  CTRL+ALT+F1,F2 and such

---

### Post by lkjoel on 2010-07-18
Thank you!
This will help LinuxEssentials, and another thread I'm helping out on.

---

### Post by trent.josephsen on 2010-07-18
> **lkjoel said:**
> I meant what it was logged into.
Point being that you can run all of those at once.  Arguably it is even in the Unix tradition to combine tools like this (panel, desktop, file manager, window manager, settings manager, office suite, and browser all from different sources).  What's more, you could start all of these with a GNOME session (I think... I'd have to fiddle with it to be sure) and start it from a neutral login manager like SLIM.  It's not any particular DE; rather, it's a mishmash of tools that combine to create a DE.  Then what do you do?

What I'm getting at here is that what it means to be running some particular DE isn't really well-defined.  DEs are collections of tools that can be mixed and matched:  settings manager, window manager, file manager, terminal, login manager, screensaver daemon, panel, dock...  the possibilities for combination are impractically numerous.  "gnome" or "kde" just doesn't cut it.  How do *you* define what it means to be running GNOME?

---

### Post by lkjoel on 2010-07-18
> **trent.josephsen said:**
> How do *you* define what it means to be running GNOME?
Running Nautilus with gnome-panel with gnome window manager and gnome desktop manager.
I get what you mean, but all that I am looking for is what the user logged into.
LinuxEssentials will not care about having the xfce4-panel, nautilus and the kde window manager, but all that it will care is if the user was logged into gnome.
But would the variable know that the user logged into SLIM?

---

### Post by nvteighen on 2010-07-19
See this post by me: [http://ubuntuforums.org/showpost.php?p=9607968&postcount=11](http://ubuntuforums.org/showpost.php?p=9607968&postcount=11)

This is really an issue that should be addressed by someone somehow. I don't know, maybe the X.org guys or someone. We need a way to trivially know what DE is running, in the sense of "library preference". For me, running GNOME or Xfce is to run a GTK+ based DE; GNUStep, a GNUStep based DE; KDE, a Qt one.

---

### Post by trent.josephsen on 2010-07-19
> **lkjoel said:**
> Running Nautilus with gnome-panel with gnome window manager and gnome desktop manager.
I get what you mean, but all that I am looking for is what the user logged into.
LinuxEssentials will not care about having the xfce4-panel, nautilus and the kde window manager, but all that it will care is if the user was logged into gnome.
But would the variable know that the user logged into SLIM?

No.  SLIM is just the login screen.  Ubuntu uses GDM, or used to.  KDM and XDM are other options.

What do you mean by "what the user logged into"?  How would you define what I log in to if I'm using such a mishmash of various tools?  

I agree with nvteighen that there's a need for some way to determine library preference, but in general, I don't think it's a good idea for programs to make assumptions about what environment they're running under.  Tell me, what will you do with the information if $DESKTOP_SESSION contains "gnome"?  What if it contains "kde"?  (And what will you do if, as in my case, it's empty?)

---

### Post by lkjoel on 2010-07-19
So what I get is that it is nearly impossible to know what DE the user is using right?
They should make it much easier!

---

### Post by lkjoel on 2010-07-20
I finally found (with the help of nvteighen's post) how to do it.
I made a shell script that will detect the DE.
Check DEtools.tar.gz
The one to use for applications is showde.
To use it, you can do this:
```
chmod +x showde
showde
echo $?
```
It will show you a number:
1=KDE/QT
2=GNOME/XFCE/XORG
3=CLI/PURE

And thanks to all of you for trying to help!

---

