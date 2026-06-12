---
title: "HOWTO: Save 80-100MB RAM in gnome and make boot rapid"
date: 2009-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by stwschool on 2009-06-06
So here's the deal. My computer is a good one. But at times it runs like a slug. Turns out nautilus is the problem. 80-100MB for a file manager/desktop icon manager?

So I tried PCManFM. It looks similar, and does all the same things (see attachment). It used 3mb. Yes, 3mb. You lose previews for pictures and it doesn't do FTP, but I can use other apps for that.

So, if you're brave, roll up.

1. Open the terminal. It's quicker this way, and I can give EXACT instructions.
2. sudo aptitude install pcmanfm
3. Once that's installed type the following:
   sudo nano /usr/share/applications/nautilus-computer.desktop
4. Look for the line beginning Exec= and change it to Exec=pcmanfm /
5. Ctrl + O to save and Ctrl + x to exit.
6. sudo nano /usr/share/applications/nautilus-folder-handler.desktop
7. Look for the line beginning Exec= and change it to Exec=pcmanfm %U
8. Ctrl + O to save and Ctrl + x to exit.
9. gconf-editor
10. Choose apps>nautilus>preferences>show-desktop and take out the tick
11. Close, log out and log back in again.

Should now be lightning fast. Note that if you want desktop icons (not everyone does) open pcmanfm (go places and choose anything) then:
1. Edit -> Preferences -> Desktop -> Tick 'Manage desktop and show file icons'.
I'll leave you to decide whether to let PCManFM handle wallpaper and whether to let the window manager organise your right-click menu.

Enjoy!

---

### Post by frodon on 2009-06-08
If you don't mind please add instructions on how undoing things for those who want to give this a try and undo things later (in case they don't like it).

Thanks for the tutrial.

---

### Post by stwschool on 2009-06-08
No worries, will see what I can sort out tomorrow after work (it's a bit late here right now and my brain's mush).

---

### Post by han87 on 2009-06-08
This is **perfect** for my eee PC.

Went from 180mb usage with nothing open to 130mb.  I still have image preview too, so nothing big lost.  A little faster upon boot too.

What I did in case I need to revert was save the old lines I changed...so I can change right back in a minute if I choose to.

In a folder, go to Edit > Preferences and check the Display image files with supported format as thumbnails.

---

### Post by l-x-l on 2009-06-08
Thanks... don't need this for my laptop as it has plenty of RAM. But for one of my older pcs I was looking to convert to a server it may be perfect.

---

### Post by Hubi17 on 2009-06-09
Hi

this seemed like a nice filemanager, since its not so bloated. however, i had a problem with PCManFM. it would allow me to browse folders, but if i tried to open any type of file, it would not open it. it only briefly showed the name of the window in the taskbar and then it disappeared not opening anything... any ideas what that might be?

---

### Post by han87 on 2009-06-09
> **Hubi17 said:**
> Hi

this seemed like a nice filemanager, since its not so bloated. however, i had a problem with PCManFM. it would allow me to browse folders, but if i tried to open any type of file, it would not open it. it only briefly showed the name of the window in the taskbar and then it disappeared not opening anything... any ideas what that might be?



Open gconf-editor, open up:

desktop > gnome > session > required_components

modify the value "filemanager" to say pcmanfm instead of nautilus.  log out and log on and it will work for you

---

### Post by Hubi17 on 2009-06-09
> **han87 said:**
> Open gconf-editor, open up:

desktop > gnome > session > required_components

modify the value "filemanager" to say pcmanfm instead of nautilus.  log out and log on and it will work for you

thanks for the quick reply!

that fixed it, so thank you for your help too!! ;)

---

### Post by zhurai-tsuki on 2009-06-09
things about this:

- yes it's more light-weight, there are problems with it...

ex:
opening terminal "here" (I'm on GNOME...=> gnome-terminal) tries to run it, but fails and doesn't open a terminal

extract "here" (of archives) same as opening terminal


so, for me, I'm sticking with what I had before o/

---

### Post by han87 on 2009-06-09
> **zhurai-tsuki said:**
> things about this:

- yes it's more light-weight, there are problems with it...

ex:
opening terminal "here" (I'm on GNOME...=> gnome-terminal) tries to run it, but fails and doesn't open a terminal

extract "here" (of archives) same as opening terminal


so, for me, I'm sticking with what I had before o/


Follow my instructions a few posts up and it will solve those problems for you.

---

### Post by zhurai-tsuki on 2009-06-09
> **han87 said:**
> Follow my instructions a few posts up and it will solve those problems for you.

I'll test that later...

hmm... though note:

> Should now be lightning fast. Note that if you want desktop icons (not everyone does) open pcmanfm (go places and choose anything) then:
1. Edit -> Preferences -> Desktop -> Tick 'Manage desktop and show file icons'.
I'll leave you to decide whether to let PCManFM handle wallpaper and whether to let the window manager organise your right-click menu.

about this, apparently, this doesn't work too well with desktop-drapes (wallpaper changer)... as apparently it doesn't let drapes change the wallpaper at all.

---

### Post by milesnapue on 2009-06-10
What should I change my Exec to if at the moment it looks like 
Exec=nautilus --no-desktop computer:

```
[Desktop Entry]
Encoding=UTF-8
Name=Computer
Comment=Browse all local and remote disks and folders accessible from this computer
TryExec=nautilus
Exec=nautilus --no-desktop computer:
Icon=computer
Terminal=false
StartupNotify=true
Type=Application
Categories=GNOME;GTK;Core;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.26.2
X-Ubuntu-Gettext-Domain=nautilus
```

is what the whole file looks like, thanks for your help

---

