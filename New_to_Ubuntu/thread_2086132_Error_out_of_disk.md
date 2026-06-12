---
title: "Error: out of disk"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by Paper Pusher on 2012-11-19
I did something really stupid.  I saved some files and I ran out of disk space.  I can no longer boot my system.  Instead I get the prompt "grub rescue."  I do not need the extra files taking up disk space.

How do I delete the extra files?

When I boot off the CD, the GUI shows me the extra files but will not let me delete them.  When I get into the command line prompt via the terminal,  I can't get to the boot disk in order to delete the files.

Help!  What do I do to delete the files eating up the disk?

---

### Post by Bucky Ball on 2012-11-19
While booting from the CD, open a terminal and:

```
sudo nautilus
```

That will open the file manager as root. Be careful. ONLY delete the files you want gone. 

While you're there, as you need to expand/shrink partitions by booting from the CD (the partitions in question need to be unmounted), you could give yourself some extra space.

---

### Post by Wim Sturkenboom on 2012-11-20
Because it is in a graphical environment, rather use
```

gksudo nautilus

```
;)

---

### Post by Bucky Ball on 2012-11-20
> **Wim Sturkenboom said:**
> Because it is in a graphical environment, rather use
```

gksudo nautilus

```
;)

+1. Indeedy. Thanks, my mistake. ;)

---

### Post by newb85 on 2012-11-20
> **Wim Sturkenboom said:**
> Because it is in a graphical environment, rather use
```

gksudo nautilus

```
;)

This is something I've never understood.  In my experience, 
```
sudo nautilus
```
works just fine, with the difference being that with sudo I enter my password in the terminal, and with gksudo I enter it in a little GUI-esque box comes up.  Is there a difference beyond that?

---

### Post by Bucky Ball on 2012-11-20
A ton of info on the differences out there ... here's a sample:

[http://askubuntu.com/questions/11760/what-is-the-difference-between-gksudo-nautilus-and-sudo-nautilus](http://askubuntu.com/questions/11760/what-is-the-difference-between-gksudo-nautilus-and-sudo-nautilus)

[http://superuser.com/questions/202676/sudo-vs-gksudo-difference](http://superuser.com/questions/202676/sudo-vs-gksudo-difference)

---

### Post by newb85 on 2012-11-20
Thanks!  I guess I've been lucky...

---

