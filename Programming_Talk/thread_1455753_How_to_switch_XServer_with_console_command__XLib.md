---
title: "How to switch XServer with console command / XLib ?"
date: 2010-04-16
forum: Programming Talk
---

### Post by scrawl on 2010-04-16
Hi,

In my program, I would like to switch to another XServer, for example switch to Display :1 . I tried emulating the Keyboard commands (Ctrl+Alt+F8) with xautomation, but that doesnt seem to work, I guess these commands are caught somewhere else so I cant emulate them.

So is there any other way to switch to another XServer in my program? Maybe directly via XLib?

---

### Post by falconindy on 2010-04-16
Look at XOpenDisplay(3).

---

### Post by scrawl on 2010-04-16
Well, I can use this function and it doesnt give an error. But nothing happens. Do I need to activate it somehow?

---

### Post by cdekter on 2010-04-17
What you are trying to do is switch to a different TTY. This in fact has nothing to do with X. It's handled in the kernel, so unless the kernel exposes some kind of API for it, you're out of luck.

---

### Post by scrawl on 2010-04-17
I dont want to switch to another TTY. I want to switch to another running XServer. And it has to be possible, because the fast-user-switcher-applet does this too when switching users. I looked at the source, but its Greek to me.

---

