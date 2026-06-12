---
title: "No borders in text boxes - Firefox3"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by BoyBlunder on 2008-08-26
It seems like I've lost the borders on any text-entry box on Firefox (see attachment). Does anyone have a fix for this??

---

### Post by starcannon on 2008-08-26
Restart Compiz, 

Alt-F2
```
compiz --replace
```

or from terminal

```
compiz --replace &
```

A great utility that lets you do this quickly is Compiz Fusion Icon; you can install it by:

```

sudo apt-get install fusion-icon

```

Add it to session manager and it will be there every boot, for now just open it from Applications-->System Tools-->Compiz Fusion Icon

It will now be a little icon on one of your gnome-panels, r-click it and choose Reload Window Manager.

---

### Post by BoyBlunder on 2008-08-26
> **starcannon said:**
> Restart Compiz.

I've restarted the machine multiple times -- isn't that the equivalent?

---

### Post by Rome.konig on 2008-08-26
do you have emerald? what do you use?

---

### Post by BoyBlunder on 2008-08-26
> **Rome.konig said:**
> do you have emerald? what do you use?

I have Emerald and Compiz-fusion.

---

### Post by starcannon on 2008-08-26
Use Compiz Fusion Icon, it is how I deal with compiz and emerald when they do that, look at my earlier post for directions, I updated it.

---

### Post by BoyBlunder on 2008-08-26
> **starcannon said:**
> Use Compiz Fusion Icon, it is how I deal with compiz and emerald when they do that, look at my earlier post for directions, I updated it.

I installed the icon, I don't think it has anything to do with compiz. I can change the visual effects to none and still have no border in the text box show up on Firefox.

I had the issue months ago with the WINDOW borders w/ compiz, which is why I don't think that has anything to do with the TEXT boxes (see my attached image; there's nothing laying out where to type to the right of Username and password).

---

### Post by damis648 on 2008-08-26
Try selecting a different GTK theme, this might be a bug in your GTK theme.

---

### Post by BoyBlunder on 2008-08-26
> **damis648 said:**
> Try selecting a different GTK theme, this might be a bug in your GTK theme.

I've tried multiple themes :(

edit: I am downloading Opera now to see if it affects that as well.

edit2: Installed Opera. Text boxes have borders in it, still not in Firefox.

---

### Post by BoyBlunder on 2008-09-08
Still don't have the resolution to this -- any ideas?

---

