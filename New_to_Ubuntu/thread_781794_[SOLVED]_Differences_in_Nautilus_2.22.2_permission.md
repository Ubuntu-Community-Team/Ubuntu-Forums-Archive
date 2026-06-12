---
title: "[SOLVED] Differences in Nautilus 2.22.2 permissions tab"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by ubername on 2008-05-04
Hi

I have an odd issue:

I have two machines which should be running the same version of Ubuntu (i,e, both are on Hardy Heron and both have the same upgrade strategy / server)

However on one, when I go to the permissions tab of a file in Nautilus (v2.22.2) I get this (sorry don't know how to post it inline).

On the other, also using Nautilus 2.22.2, I get the other screenshot.

Anyone know why / how to make them the same (I prefer the first)

TIA

---

### Post by quirks on 2008-05-04
To make the first view the default, in a terminal type this:
```
gconf-editor
```
Then go to apps -> nautilus -> preferences and check **show_advanced_permissions** in the right pane. Close and open Nautilus again, and there you have it.

I didn't know there was another view before. Thanks for pointing it out; I like the first one better, too.

---

### Post by Oldsoldier2003 on 2008-05-04
> **quirks said:**
> To make the first view the default, in a terminal type this:
```
gconf-editor
```
Then go to apps -> nautilus -> preferences and check **show_advanced_permissions** in the right pane. Close and open Nautilus again, and there you have it.

I didn't know there was another view before. Thanks for pointing it out; I like the first one better, too.

Don't forget that for this to take effect you'll need to:

```
sudo killall nautilus
```

---

### Post by ubername on 2008-05-04
> **quirks said:**
> To make the first view the default, in a terminal type this:
```
gconf-editor
```
Then go to apps -> nautilus -> preferences and check **show_advanced_permissions** in the right pane. Close and open Nautilus again, and there you have it.

I didn't know there was another view before. Thanks for pointing it out; I like the first one better, too.


Thanks so much, worked like a charm

Mods: Please mark this as solved if you can.

---

### Post by lns on 2008-08-20
Nice. I definitely like the previous Permissions tab (rwx style). IMHO all the new one does is (badly) hide the concepts behind rwx, which if you take 5 minutes to learn about it, the knowledge is actually portable (imagine that) to other file managers (not to mention the shell).

Mucho kudos for pointing this alternative out. I'm applying it to all my 8.04.1 servers.

---

