---
title: "CD/DVD Drive help"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Norst on 2008-05-17
Now CD/DVD drives have been able to close themselves forever. Yet it has never been used by GUI’s. You can right click on a CD/DVD ROM device in Windows, KDE, Gnome and select that the device eject, but you never get the option to inject (close the tray). Instead you must do it physically. You’d think this would be a pretty cool accessibility feature. If I have difficulty putting a CD/DVD in the drive, then how in hell am I going to hit that tiny little button on the drive. Rather I must push on the tray to get it to close. This is a self preservation feature of a CD/DVD drive, not a way to close the tray. I see a lot of people do this, it’s bad. You can slip the tray off it’s little plastic gears, or even snap a few teeth off it. Been there. It would be better to have the option of closing the tray from the right-click menu.

If someone knows how to add a rick click menu to a device that can do this please point me in the right direction.

I can do it with the command line
Code:

eject -t [DriveName]

but I have 3 CD/DVD drives so having to type it out each time would be a pain.

---

### Post by nowshining on 2008-05-17
there is a way on the forums if u search to use F1-f12 to close/open trays.

---

### Post by Norst on 2008-05-19
Thanks, I'll check that out

---

### Post by nowshining on 2008-05-20
have u found the post?

---

### Post by kingvirendra on 2008-09-02
> **Norst said:**
> Now CD/DVD drives have been able to close themselves forever. Yet it has never been used by GUI’s. You can right click on a CD/DVD ROM device in Windows, KDE, Gnome and select that the device eject, but you never get the option to inject (close the tray). Instead you must do it physically. You’d think this would be a pretty cool accessibility feature. If I have difficulty putting a CD/DVD in the drive, then how in hell am I going to hit that tiny little button on the drive. Rather I must push on the tray to get it to close. This is a self preservation feature of a CD/DVD drive, not a way to close the tray. I see a lot of people do this, it’s bad. You can slip the tray off it’s little plastic gears, or even snap a few teeth off it. Been there. It would be better to have the option of closing the tray from the right-click menu.

If someone knows how to add a rick click menu to a device that can do this please point me in the right direction.

I can do it with the command line
Code:

eject -t [DriveName]

but I have 3 CD/DVD drives so having to type it out each time would be a pain.
-Virendra Negi

---

### Post by 3rdalbum on 2008-09-02
If you run Compiz, go into Advanced Desktop Effects Settings, click General Options and go to the Commands tab. In the Commands box, type your "eject" command into one of the Command Line fields. Go to the Keybindings box and set a keyboard shortcut (say, F12). Repeat for as many optical drives as you have.

There is a similar method involving gconf-editor, if you are using the Metacity window manager (the normal Gnome one).

Incidentally, I've never had any trouble when pushing the tray in. In a quick survey, my Pioneer burner takes more pushing but feels like a solidly-built drive; my Samsung feels flimsier but only needs a slight nudge.

---

### Post by kaibob on 2008-09-02
Earlier today, the eject command was updated so that the -T option now works as a toggle to open a CD drive when it's closed and close it when open. As a result, the following simple command will open and close a CD drive:

```
eject -T
```

With multiple CD drives, you have to add an identifier for each drive. In my case, the top CD drive is scd0, so I use the following:

```
eject -T /dev/scd0
```

I don't know of any way to assign this to the right click menu, but it's just as easy to assign it to a key or key combination.

---

