---
title: "Reverting to Default Panels"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by LittleLORDevil on 2008-04-24
I severely messed up my GNOME panels messing around with a fresh install of Hardy.  Is there a command to revert to the default?

---

### Post by mmb1 on 2008-04-24
I'm not aware of a command, but is bad enough to where you can't reconstruct them with right-clicking and creating new ones?

---

### Post by LittleLORDevil on 2008-04-24
I guess not its just that there are things hiding all over the place and moving themselves](*,)

---

### Post by grannyw on 2008-04-24
its really strange man that u cant figure it out

---

### Post by mmb1 on 2008-04-24
can you post a screenshot, please?

---

### Post by LittleLORDevil on 2008-04-24
I just decided I am going to do a reinstall I think I messed up some files when I was messing with window managers and theme managers.

---

### Post by mmb1 on 2008-04-24
That sounds a bit drastic, sorry that i was unable to help.  Good luck with your reinstall!

---

### Post by LaRoza on 2008-04-24
> **LittleLORDevil said:**
> I severely messed up my GNOME panels messing around with a fresh install of Hardy.  Is there a command to revert to the default?

Delete the configuration directory. 

```

rm -rf .gconf 

```

Log out (press Ctrl + Alt + Backspace)

---

### Post by LittleLORDevil on 2008-04-24
Thanks I will keep this in mind for the next time I mess up things :)

---

### Post by oldjudithp on 2008-07-02
> **LaRoza said:**
> Delete the configuration directory. 

```

rm -rf .gconf 

```

Log out (press Ctrl + Alt + Backspace)

I tried this without success, but my "mess up" may have been different!
Playing around with the panel I deleted the texts "Applications" etc and now have reinstalled applets (icons) without visible text descriptions as when first installed.
How do I get back and revert to the original installed panel in Ubuntu Hardy?

---

### Post by chrisccoulson on 2008-07-02
> **LaRoza said:**
> Delete the configuration directory. 

```

rm -rf .gconf 

```

Log out (press Ctrl + Alt + Backspace)

Thats very drastic LaRoza. A slight;y more sane way would perhaps be to do something like:
```
gconftool-2 --recursive-unset /apps/panel
```
That would keep all the other preferences in GConf intact

---

### Post by markbuntu on 2008-07-02
The easiest way is to log out and log back in in anything but the previous session. This will reset your session to the original gnome or xfce configuration script.

The way gdm (the log in manager) works is to load your previous session by default but you can curcumvent that in the login screen. The little icon on the bottom left includes options for doing so.

---

