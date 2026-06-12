---
title: "Make tty console text smaller"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by dannyboy79 on 2012-10-30
I have a Mythbuntu 10.04 running but I disabled the windows manager (to save on resources) and I just run command line only. The text is so large that when I issue a command like 
```
ls -la /dev/disk/by-uuid/
```
I can't read the entire line because the end letter is cut off because the console text is to large. I changed it to 8 from 16 using 
```
dpkg-reconfigure console-setup
``` even but it's still to large. Is there some other solution?

I also tried adding vga=791 after the boot line within menu.lst but I ended up with a garbled screen and I had to remove it as it made nothing come up on the screen.

---

### Post by CharlesA on 2012-10-30
ssh in and do it that way. ;)

---

### Post by dodo3773 on 2012-10-30
This is an old thing and not sure if it still works/is what you're looking for:
```

sudo dpkg-reconfigure console-setup

```

---

### Post by dannyboy79 on 2012-10-30
> **dodo3773 said:**
> This is an old thing and not sure if it still works/is what you're looking for:
```

sudo dpkg-reconfigure console-setup

```
i mispoke orginally, I had already ran that command and set it to 8. I called it console-tools, I meant console-setup. It still is no better using 8 versus 16. Oh well, guess I'll ssh in cause at least that way I can control the text of my terminal emulator whether it's lxterminal or gnome-terminal or whatever.

---

### Post by CharlesA on 2012-10-30
When I booted up my 10.04 box, the resolution of the console was set automatically to the resolution of the monitor. Maybe it doesn't like your video card or something?

---

