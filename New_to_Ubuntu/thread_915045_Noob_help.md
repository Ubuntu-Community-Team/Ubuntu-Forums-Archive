---
title: "Noob help?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by fahorne on 2008-09-09
[SIZE="3"]Emachine 566i
32mb ram
7.5 gb hd

Installed Xububtu and tried to: sudo gedit /etc/fstab.
It prompts me for pwd (which I give), then "command not found."
What's the deal. That is a valid command. [/SIZE]

---

### Post by anotherdisciple on 2008-09-09
does Xubuntu use Gedit? Try nano

---

### Post by wolfen69 on 2008-09-09
you got xubuntu to load with only 32mb ram? does not sound right. as far as i know, xubuntu does not use gedit. find out what text editor xubuntu uses and try again.

---

### Post by anotherdisciple on 2008-09-09
I read that mousepad is the default editor... try this:

```
sudo mousepad /etc/fstab
```

if that doesn't work...


```
sudo nano /etc/fstab
```

---

### Post by hyper_ch on 2008-09-09
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by billgoldberg on 2008-09-09
> **hyper_ch said:**
> It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

Agreed.

To OP:

Use mousepad instead of gedit.

Or install gedit.

---

### Post by oldos2er on 2008-09-09
> **fahorne said:**
> [SIZE=3]Emachine 566i
32mb ram
7.5 gb hd

Installed Xububtu and tried to: sudo gedit /etc/fstab.
It prompts me for pwd (which I give), then "command not found."
What's the deal. That is a valid command. [/SIZE]

 How on earth did you install Xubuntu with only 32MB RAM?

---

### Post by darrelljon on 2008-09-09
On 32Mb RAM, its likely Xubuntu just ran out of memory before it loaded a graphical desktop environment. Stick to [Slitaz]("http://www.slitaz.org/en/"), [Damn Small Linux]("http://www.damnsmalllinux.org/") or [Puppy Linux]("http://www.puppylinux.org/") instead. Check out the links in my signature too and let us know how you get on.

---

### Post by fahorne on 2008-09-09
[SIZE="2"]Thanks, all. Gedit wasn't in Xubuntu. I installed and it works great.:-D:o:)[/SIZE]

---

