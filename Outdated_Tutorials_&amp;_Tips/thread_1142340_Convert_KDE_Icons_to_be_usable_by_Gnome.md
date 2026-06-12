---
title: "Convert KDE Icons to be usable by Gnome"
date: 2009-04-29
forum: Outdated Tutorials &amp; Tips
---

### Post by JuanFM on 2009-04-29
Should you decide to give gnome a try from being a longstanding KDE user, you may notice that many of your desktop icons will a) not work b) have a generic text file icon.  Fixing this is pretty simple:  1. Open shortcut in a text editor  2. Replace "[$e]=$HOME" with /home/yourusername 3. Delete any remaining "[$e]" (should be one next to Exec)  So basically this wraps up to Gnome not recognizing parameters if they have the [$e] attached and $HOME not being interpreted as your home path  Te shortcuts should continue to work as normal in KDE.  Now if anybody knows how to automate this, that would be awesome.

---

