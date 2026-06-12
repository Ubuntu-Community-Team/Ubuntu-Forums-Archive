---
title: "brewnix app belongs to root user?"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by bcostlow on 2008-10-21
Help!

(using version ubuntu 8.04)

I installed Brewnix (beer brewing software) on Ubuntu but it isn't in the menu system -- did a search and found it at: usr/local/bin

But clicking the icon doesn't work.  Looking at permissions, it says this program belongs to root, no access to changing permissions.

I've tried logging in as root with default password of root (and ubuntu and as root user with the same pws but that doesn't work either)

How do become root to change permissions?

Bill

---

### Post by Thelasko on 2008-10-21
It should have root permissions.  That isn't your problem.
Try to run the program in the terminal.
Go to [Applications>accessories>terminal]("http://technical-itch.co.uk/wp-content/uploads/2007/09/ubuntu-terminal.png") and type.
```
brewnix
```

---

### Post by bcostlow on 2008-10-21
> **Thelasko said:**
> It should have root permissions.  That isn't your problem.
Try to run the program in the terminal.
Go to [Applications>accessories>terminal]("http://technical-itch.co.uk/wp-content/uploads/2007/09/ubuntu-terminal.png") and type.
```
brewnix
```

solved -- many thanks!

Bill

---

### Post by Thelasko on 2008-10-22
Please go to "thread tools" and mark this thread solved.

---

