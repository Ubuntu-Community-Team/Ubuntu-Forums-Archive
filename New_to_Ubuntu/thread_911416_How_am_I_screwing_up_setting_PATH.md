---
title: "How am I screwing up setting PATH?"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-09-05
Hi, all:

Here's my problem: X11 is not set in the PATH. I believe that this is the reason I am getting "no protocol specified, cannot open display" error messages in my terminal when using bash. As a result, I cannot open the /.bashrc or /.bash_profile (not that I have figured out yet what I'm supposed to put in there) in either root or username (trying to use gedit with "&" to open in a separate window). When I try to set the PATH, here's what I do:

PATH=$PATH:/usr/bin/X11
export PATH

I've tried this as root and as username, and what happens is that as soon as I exit the terminal or exit root status is this:

root@tarahmarie-desktop:/home/tarahmarie# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/bin/X11
root@tarahmarie-desktop:/home/tarahmarie# exit
exit
tarahmarie@tarahmarie-desktop:~$ su
Password:
root@tarahmarie-desktop:/home/tarahmarie# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

The same thing happens when I try to add /usr/lib/kde4/bin to my path in either root or username. What do I do?

---

### Post by Cypher on 2008-09-05
"Cannot open display" has nothing to do with your PATH.

To set the PATH in a manner that is takes effect in every window opened, you should modify your ~/.bashrc and add the line
```

export PATH=$PATH:<dir>:<dir>:<dir>

```
Where <dir> would be /usr/bin/X11 and /usr/lib/kde4/bin and so on. The .bashrc file will be loaded when you login and will take effect on every Terminal window.

---

### Post by tarahmarie on 2008-09-05
> **Cypher said:**
> "Cannot open display" has nothing to do with your PATH.

To set the PATH in a manner that is takes effect in every window opened, you should modify your ~/.bashrc and add the line
```

export PATH=$PATH:<dir>:<dir>:<dir>

```
Where <dir> would be /usr/bin/X11 and /usr/lib/kde4/bin and so on. The .bashrc file will be loaded when you login and will take effect on every Terminal window.

That fixed it; thanks!

---

