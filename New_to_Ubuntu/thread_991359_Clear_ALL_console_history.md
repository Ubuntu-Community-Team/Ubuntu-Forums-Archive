---
title: "Clear ALL console history"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Racecar56 on 2008-11-23
I want to clear the thing where you press up and it gives you the previous command you did, because it gets annoying sometimes, how do I do that? Typing 'clear' (without quotes) in the console only clears the text but it does not clear what I am talking about (the up thing).

---

### Post by binbash on 2008-11-23
rm .bash_history

---

### Post by philinux on 2008-11-23
It's stored in this file
/home/username/.bash_history

I find it very useful since in gedit you can search the file.

---

### Post by Racecar56 on 2008-11-23
WOOT!
Will it also delete the history auto of the CTRL+ALT+F* thing too? I would think so...

---

