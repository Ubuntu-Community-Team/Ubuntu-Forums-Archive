---
title: "Quick Question"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Dark006 on 2008-08-01
Hey I was just wondering if there is a way to combine to commands and have the info for both exported to a text file. 

For example, say I wanted to see the result of **lspci** and **lspci -n** in the same info.txt file on my desktop. I've been trying combination's of ```
lspci && lspci -n > ~/Desktop/info.txt
``` but that doesn't seem t work. Anyone know how to do this?

---

### Post by anotherdisciple on 2008-08-01
Just do this...

```
lspci > ~/Desktop/info.txt && lspci -n > ~/Desktop/info.txt
```

---

### Post by anotherdisciple on 2008-08-01
Whoops... my bad... do this instead...
```
lspci > ~/Desktop/info.txt && lspci -n >> ~/Desktop/info.txt
```

1 > will write to the file, but overwrite anything that was previously there... 2 >> will add lines to the file

---

### Post by caljohnsmith on 2008-08-01
Another alternative is to use curly brackets to group your commands:
```
{ lspci && lspci -n; } > ~/Desktop/info.txt
```
:)

---

