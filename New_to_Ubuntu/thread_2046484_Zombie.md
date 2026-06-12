---
title: "Zombie"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by vasa1 on 2012-08-23
For the last two days even after shutting down the computer and restarting, I'm noticing 1 zombie in top.

My list of processes has this:
```
2883 ?        00:00:00 kworker/1:1
 2896 ?        00:00:00 kworker/1:0
 2899 ?        00:00:00 xfce4-terminal
 2903 ?        00:00:00 xfce4-terminal <defunct>
 2904 pts/1    00:00:00 bash
 2960 pts/1    00:00:00 ps
```

Is it a cause for worry? How do I fix it?

---

### Post by coldcritter64 on 2012-08-23
Zombie process [[COLOR=Blue]-- info link --[/COLOR]]("http://en.wikipedia.org/wiki/Zombie_process")

Basically a zombie is a child process that has "died" but has not been "reaped" by its parent process (that is it still has an entry in the process table). Nothing to worry about.

The link gives some info about removal using the SIGCHLD signal with the kill command manually, though in some cases it may require the parent process shut down as well.

---

### Post by vasa1 on 2012-08-23
Thanks for replying. I just checked and will do so for a few days more. The zombie appears with the xfce terminal and not with the gnome terminal. I'm not a "power user" of the terminal so it really doesn't matter which I use. I started using the xfce terminal just recently.

---

### Post by vasa1 on 2012-08-23
Marking this solved because there's a [bug filed]("https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/996484").

---

### Post by vasa1 on 2012-08-23
I'm not sure if this is of any use, but when I open the xfce terminal and check top, I see one zombie. I quit top and close that terminal. Then, I open the gnome terminal and check top. No zombie.

For ordinary users, is there any real benefit in using one terminal rather than another? In this case, gnome versus xfce?

(I came across [a blog]("https://plus.google.com/117091380454742934025/posts/VjbFCa7X5NJ") in which some guy got quite worked up about the facilities **not** provided by a terminal but then that guy is a dev.)

---

### Post by The Cog on 2012-08-23
I personally prefer gnome-terminal because it supports using the scroll wheel when using man or less. I think it's really a matter of taste - I haven't noticed any really significant differences.

---

### Post by vasa1 on 2012-08-23
> **The Cog said:**
> I personally prefer gnome-terminal because **it supports using the scroll wheel when using man or less**. I think it's really a matter of taste - I haven't noticed any really significant differences.

I hadn't noticed that. Having that feature is quite convenient. I wonder if there's some setting deep down in Xfce's innards that would allow it.

---

