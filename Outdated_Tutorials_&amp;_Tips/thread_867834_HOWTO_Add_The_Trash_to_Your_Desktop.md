---
title: "HOWTO: Add The Trash to Your Desktop"
date: 2008-07-23
forum: Outdated Tutorials &amp; Tips
---

### Post by collinp on 2008-07-23
If you are a new person to linux, just coming from Windows or if you want the trash applet on your desktop, then you will like this thread. This is on how to add the trash icon to your Ubuntu desktop:


[LIST]
[*]Run in terminal: gconf-editor
[*]enter your password into the "Password For...." area
[*]Navigate apps \ nautilus \ desktop
[*]On the right side, you will see an option named "trash_icon_visible"
[*]Check the box next to the above said option
[*]exit out of gconf-editor
[/LIST]
Thats it, you should now see a big bin on your desktop, similar to the gnome-panel applet icon. I am sure this will help anyone transition from Windows to Ubuntu.

[B][SIZE=3]To Reverse:

[/SIZE][/B][SIZE=3][SIZE=2]Repeat the first 3 steps listed above, uncheck the box next to "trash_icon_visible", then exit out.[/SIZE]
[/SIZE]

---

### Post by collinp on 2008-07-23
Bump.

---

### Post by mad_golfer on 2008-07-23
Thxs this helped me. 


- Anthony
[Found a great deal on PC Magazines]("http://www.magazinesusa.com/pc-magazine-subscription.cfm") :lolflag::guitar::):KS

---

### Post by Drizzel on 2008-07-24
Hmmm.. Didnt work for me. No trash icon on my desktop :confused:

I'm on Ubuntu Hardy btw.

---

### Post by Drizzel on 2008-07-24
This totally doesnt work. Is there any other way to get the trash bin on the desktop?

---

### Post by jpeddicord on 2008-07-24
You don't want the sudo prefix. Just
```
gconf-editor
```

Otherwise it will only apply to the inaccessible root account.

---

### Post by Rocket2DMn on 2008-07-24
You aren't supposed to use sudo with gconf-editor.  Try it just running
```
gconf-editor
```

---

### Post by collinp on 2008-07-24
sadly, i just noticed that.

---

### Post by collinp on 2008-08-02
Bump.

---

### Post by mssever on 2008-08-02
> **Hellow said:**
> exit out of gconf-editor, remember to save your work before you leave

[snip]

Repeat the first 3 steps listed above, uncheck the box next to "trash_icon_visible", then exit out, and remember to save.gconf-editor has no save command, because all changes are automatically saved immediately. Telling people to save risks potentially confusing people when they can't find a save command.

---

### Post by collinp on 2008-08-02
> **mssever said:**
> gconf-editor has no save command, because all changes are automatically saved immediately. Telling people to save risks potentially confusing people when they can't find a save command.

Ah, just now noticed that. Its been a while since i have been in gconf-editor.

---

