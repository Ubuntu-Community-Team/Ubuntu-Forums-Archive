---
title: "Finding out if in chroot"
date: 2011-02-21
forum: Programming Talk
---

### Post by slakkie on 2011-02-21
Hello,

I've been trying to figure out what I need to do to check whether I'm in a chrooted environment.

At the moment, my search came up with little results. 

Does anyone have some useful tips for me?

Preferred method is by simple use of shell commands, since I need it for a shell script :)

---

### Post by Arndt on 2011-02-21
> **slakkie said:**
> Hello,

I've been trying to figure out what I need to do to check whether I'm in a chrooted environment.

At the moment, my search came up with little results. 

Does anyone have some useful tips for me?

Preferred method is by simple use of shell commands, since I need it for a shell script :)

You can look at the inode number of root:

```
ls -id /
```

If it isn't 2, then you must be chrooted, I suppose. But the converse doesn't hold, so it's not perfect.

---

### Post by Reiger on 2011-02-21
Heuristic I'd use: see if things are missing or different from what you'd expect in a normal root. E.g. boot images, home directory names, missing mounts for things such as /mnt... You can even cat the history file and look for a chroot command...

---

### Post by slakkie on 2011-02-21
> **Arndt said:**
> You can look at the inode number of root:

```
ls -id /
```

If it isn't 2, then you must be chrooted, I suppose. But the converse doesn't hold, so it's not perfect.

That doesn't really work, for example:

Inside my Ubuntu chroot:

15:33 pts/9 0 wesleys@eniac:/home/wesleys
$ ls -id /
2 /

My Debian (currently running):
15:33 pts/8 0 wesleys@eniac:/home/wesleys
$ ls -id /
2 /

---

### Post by Arndt on 2011-02-21
> **slakkie said:**
> That doesn't really work, for example:

Inside my Ubuntu chroot:

15:33 pts/9 0 wesleys@eniac:/home/wesleys
$ ls -id /
2 /

My Debian (currently running):
15:33 pts/8 0 wesleys@eniac:/home/wesleys
$ ls -id /
2 /

Yes, I did say that the converse doesn't hold.

---

### Post by rnerwein on 2011-02-24
> **Arndt said:**
> Yes, I did say that the converse doesn't hold.
high 
i think your chroot is not the same as the origanal system. why not touch a file in any directory what is not
included in the chroot environment ?
if this file is not present - your desicon.
i know that's not really perferct - may be a hint.

ciao

---

### Post by jbiggs12 on 2011-02-24
When you're chrooting into your environment, change your PS1 environment variable as well to (chroot) + your current PS1 after you've chrooted:

```
export PS1="(chroot) $PS1"
```

That way when you've accidentally gotten out of your chroot, you'll know thanks to the change in your shell prompt.

---

### Post by slakkie on 2011-02-25
For my own systems it is pretty easy to figure out if I'm in a chroot. But on other systems I cannot assume a file is there or not.

---

