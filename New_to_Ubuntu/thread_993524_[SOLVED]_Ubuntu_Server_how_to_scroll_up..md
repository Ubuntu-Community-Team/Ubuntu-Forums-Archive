---
title: "[SOLVED] Ubuntu Server how to scroll up."
date: 2008-11-25
forum: New to Ubuntu
---

### Post by toolfan2k4 on 2008-11-25
Hello all, I am using ubuntu server. When I run the dmesg command to find my flash drive it fills the screen more then once. The result is that I can only see the last set of lines of output. How do I scroll up? Or is there a command to make it not scroll down until I hit the space bar like in M$DOS? Any help is appreciated and I am sorry for the poor explanation.:(

---

### Post by solitaire on 2008-11-25
All you need to do is press the "Shift key" and "Page Up" to scroll up...

---

### Post by diablo75 on 2008-11-25
```
dmesg |more
```

---

### Post by snova on 2008-11-25
A plain old console (Ctrl-Alt-F1, etc.) doesn't have scrolling that I know of. Pipe the output through less, or more.

---

### Post by handydan918 on 2008-11-25
> **diablo75 said:**
> ```
dmesg |more
```

Last time I checked, scrolling back was exactly one of the functions that made "less" more than "more".

---

### Post by scorp123 on 2008-11-26
> **snova said:**
> A plain old console (Ctrl-Alt-F1, etc.) doesn't have scrolling that I know of. Shift+PageUp :)

---

### Post by ilrudie on 2008-11-26
> **handydan918 said:**
> Last time I checked, scrolling back was exactly one of the functions that made "less" more than "more".

When using more you can "scroll" up by pressing the b key.
Also Shift+PageUp works but only scrolls a small amount on my system (a few screens).

---

### Post by snova on 2008-11-26
> **scorp123 said:**
> Shift+PageUp :)

Neat! I'll remember that.

---

### Post by toolfan2k4 on 2008-11-28
OK thanks everyone! I cant use regular terminal because im using server which as far as I know of is command line only unless you install gnome. At any rate the more command was what I was looking for thanks everyone for the input.

---

