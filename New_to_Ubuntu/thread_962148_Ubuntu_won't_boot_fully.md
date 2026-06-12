---
title: "Ubuntu won't boot fully"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by rcmcivor on 2008-10-29
I just installed Ubuntu 8.04 a few days ago, my first crack at linux. 

The machine boots to the point of asking my user name and password but doesn't get much farther. I'm left with the blank beige screen and a mouse pointer.

The last thing I was working on was trying to get samba working... which I didn't but I think I was close. The machine seemed to be working fine before I shut it down. Sorry I can't give anymore info.

Any ideas?

---

### Post by Xiong Chiamiov on 2008-10-29
You managed to do something to gnome.  I'd try moving your ~/.gnome2 folder, which will essentially revert all of your gnome settings to the default.  You can then start moving things back if you need to.
```

mv ~/.gnome2 ~/.gnome2.bak

```
then restart.

---

### Post by rcmcivor on 2008-10-29
Okay. How do I get to terminal from where I am?

Also what sort of things would I need to move back? Only thing's I've done so far:
- installed wireless network card driver (using ndiswrapper)
- installed BOINC, which was frozen which is why I rebooted. I'm not sure if it was frozen because of my system because IIRC they had server issues over the last couple days
- Started setting up samba

Thanks

---

### Post by meindian523 on 2008-10-29
Ctrl+Alt+F1 will drop you to a command line.

---

