---
title: "Python processing and sudo"
date: 2008-07-01
forum: Programming Talk
---

### Post by Flimm on 2008-07-01
I'm in the midst of [refactoring](http://epidermis.tuxfamily.org/?q=node/25) [Epidermis](https://launchpad.net/epidermis), and I'd like to find a better solution to my problem.
Basically, I need to run some python code as root. The way I had been doing it was to use
[php]subprocess.call(["gksu", "--", "asroot.py", commandlinearguments])[/php]
But this approach has multiple limitations:
[LIST][*]I can't share objects between processes and subprocesses
[*]I can't easily track progress from the parent process[/LIST]
If you look at [this code skeleton](http://epidermis.tuxfamily.org/?q=node/25), you'll see where I'll need this functionality: for the install, remove and activate methods.
Here's the activate method's skeleton:
[php]    def activate(self, progressCallback=None, block=True):
        """Applies the pigment to current user, and possibly system-wide
        progressCallback: a function which accepts one argument: progress: a
        float varying between 0.0 and 1.0 . If the function returns True then
        the activation will be aborted
        block: if False, this method will spawn a new thread"""
        pass[/php]
 I would love it if they're was an easy way to run these methods as root, while keeping all their arguments including self intact.
Anyone know of something I could use? All the solutions I've seen so far seem like overkill to me.

---

### Post by Flimm on 2008-07-02
I tried dbus, but I can't get a python app running as root to access the session bus of the user.

---

### Post by pmasiar on 2008-07-02
You may want to ask at python.org mailing list, where **real** experts hang around :-)

---

### Post by kknd on 2008-07-02
You can use local sockets!

---

### Post by Can+~ on 2008-07-02
> **pmasiar said:**
> You may want to ask at python.org mailing list, where **real** experts hang around :-)

There's also a forum:
[http://python-forum.org/pythonforum/index.php](http://python-forum.org/pythonforum/index.php)

---

