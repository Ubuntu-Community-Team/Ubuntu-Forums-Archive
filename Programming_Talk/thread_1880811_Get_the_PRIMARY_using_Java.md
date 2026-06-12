---
title: "Get the PRIMARY using Java"
date: 2011-11-14
forum: Programming Talk
---

### Post by ingolfured on 2011-11-14
Hey guys, my first thread here,

As some of you know the X11 has something called PRIMARY, SECONDARY and the CLIPBOARD. It's easy to access the clipboard, for instance  through java.awt.datatransfer.Clipboard, but do you guys know any way to get the current PRIMARY by some Java API?

---

### Post by 11jmb on 2011-11-14
Welcome :)

I'm not sure if you're looking for a more system-level solution, but if you are looking to read/copy primary selections from a single program, JTextComponent has a getSelectedText() method.

---

### Post by ingolfured on 2011-11-15
Thanks for the reply. I thought maybe there would be an easy way (method or something) to get to the PRIMARY. What I did (which is an ugly solution) was I changed the program autocutsel to make it write to a .txt file. Then I used java to read back from that file.

If someone has a better solution, I would be delight.

---

### Post by 11jmb on 2011-11-15
You could try using JNI to access the native xlib library.

---

### Post by ingolfured on 2011-12-01
Thanks ! Eventually, that became my solution.

---

