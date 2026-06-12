---
title: "[SOLVED] i need to know how to edit this"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by bradpurvis on 2008-10-26
/etc/apt/sources.list

please and thank you :)

---

### Post by hictio on 2008-10-26
It is a plain text file, you can eidt with the Text Editor, gedit, the only thing is that it has to be done by the root user.
Open a terminal (Applications -> Accessories -> Teminal), and type:
```

sudo gedit /etc/apt/sources.list

```

It will ask your password.
Save when you are done, and close it.

If, for safe sake, you want to make a copy, before the above, type this on to the terminal:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

```

Note that if you make the copy first, it will ask your password, but if open the file right after, it will not ask your password again, as it stores it for a few minutes.

---

### Post by bradpurvis on 2008-10-26
thank you very much :D

---

### Post by kostkon on 2008-10-26
> **bradpurvis said:**
> thank you very much :D
Graphically you can do it in *System -> Administration -> Software Sources*.

---

### Post by bradpurvis on 2008-10-26
well too late lol. i just installed JAVA.

um how do i mark this as solved?

---

### Post by ukera on 2008-10-26
you can also do:

[PHP]sudo nano /etc/apt/sources.list[/PHP]

or instead of nano, you can ALSO use vi.  (:

-ukera

---

### Post by cyberdork33 on 2008-10-26
> **bradpurvis said:**
> um how do i mark this as solved?

The option is in the thread tools menu at the top of the page.

---

### Post by bapoumba on 2008-10-27
Moved to ABT, and marked as Solved :)

---

